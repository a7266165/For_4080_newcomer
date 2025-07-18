# For_4080_newcomer

給專題生的程式入門指南

各位同學好，這份文件旨在指引此前未接觸過程式撰寫的各位，希望能為各位打下一個相對良好的基礎。  
by 莊淯任

## 目錄

- [新手的起點：Vibe-coding](#新手的起點vibe-coding)
- [實用工具](#實用工具)
- [入門範例](#入門範例)

---

## 新手的起點：Vibe-coding

我是大四即將畢業才開始大量撰寫程式，此前和絕大多數的各位一樣，只有大一在課堂上學過一些很基本的程式撰寫。

在基本功如此薄弱的前提下，我在實驗室的這兩年接觸過腦波訊號、機器視覺、肝癌存活分析與阿茲海默預測，並一定程度地掌握其中核心。  
能做到這點，主因我擅於仰賴GPT解決我不太清楚如何下手的問題，並從中學習。

所以，我會建議剛開始學怎麼寫程式的各位，先不要在乎什麼程式語法、架構、類別抽象化等等的coding細節，  
而是先從比較宏觀的「不拖泥帶水地精確描述任務」開始，或者說「下一個好的prompt」。

順帶一提，這份文件使用claude排版，整個過程我給它的幾個主要prompt是：

> **(1)** 「幫我把anaconda下載方式這個doc文件的內容轉換成github易讀的版面」

> **(2)** 可以幫我把插圖用連結的方式放到對應的部份嗎？資料夾結構可以擺成這樣

```
conda
├──   figures
└──  README.md
```

> **(3)** 再來是把git.docx這個文件的內容轉換成github易讀的版面

> **(4)** 最後想請你試著統合剩下三份文件有關poetry安裝的部份，如果有遇到問題我們可以一起討論

最後再進行一些微調，就變成各位看到的樣子了

### Prompt 範例

我以EEG訊號作為一個例子，訊號通常都一定會做頻譜分析，那如果我想要依靠GPT協助我做頻譜分析，可以怎麼下prompt呢？

可以參考以下六個描述(prompt)：

> **(1)** 我現在要對一段EEG訊號進行頻譜分析，請幫我撰寫程式碼。

> **(2)** 我現在要對一段EEG訊號進行頻譜分析，請幫我撰寫python程式碼。

> **(3)** 我現在要對一段EEG訊號進行頻譜分析，它的格式是.edf檔，請幫我撰寫python程式碼。

> **(4)** 我現在要對一段EEG訊號進行頻譜分析，主要觀察delta, theta, alpha, Beta1, Beta2, Beta3, gamma七個頻帶，它的格式是.edf檔，請幫我撰寫python程式碼。

> **(5)** 我現在要對一段EEG訊號進行頻譜分析，它有五個頻道(Fpz、Fz、Cz、Pz、Oz)，主要觀察delta, theta, alpha, Beta1, Beta2, Beta3, gamma七個頻帶，它的格式是.edf檔，請幫我撰寫python程式碼。

> **(6)** 我現在要對一段EEG訊號進行頻譜分析，它有五個頻道(Fpz、Fz、Cz、Pz、Oz)，主要觀察delta, theta, alpha, Beta1, Beta2, Beta3, gamma七個頻帶，它的格式是.edf檔，請幫我撰寫python程式碼，分析每個頻帶的能量並繪製成圖。

相信各位從這六個prompt已經可以稍微感受到什麼是"精確"。
我會說，模糊的prompt並不是錯的prompt，只是當你輸入的prompt越模糊，LLM產出的內容就越可能偏離你想要的結果，而這是工程上不想看到的。

講完精確，接著要講"拖泥帶水"。  
我們在描述一件事的時候，很常把一句話拆成三句話，或者重覆的內容說好幾次：

> **(4)\*** 我現在要對一段EEG訊號進行頻譜分析，分析時採用傅立葉轉換，以傅立葉轉換觀察delta, theta, alpha, Beta1, Beta2, Beta3, gamma七個頻帶，它的格式是.edf檔，請幫我撰寫python程式碼進行傅立葉轉換分析。

像這個句子裡，傅立葉轉換重覆出現多次，它就會佔用你輸入的token，也會影響LLM的產出，在使用時就要盡量避免。

### 成長路徑

對各位而言：
1. **首先要做到的就是ctrl+c & ctrl+v**，把LLM寫好的程式碼原封不動的放到編譯器裡並成功執行產生結果
2. **再來就是試著去瞭解這些程式在做什麼**，同時慢慢增加程式的主控權
3. **最後則是作為一個reviewer**，根據LLM提供的程式碼做二次加工；  
   **以及作為一個架構規劃者/驗收者**，準備好程式整體架構後交由LLM實行細節

---

## 實用工具

###  [VS Code](https://code.visualstudio.com/)
我自己習慣使用的IDE是VScode，這部份大家選自己喜歡的就好

###  [Anaconda/mini-conda](./conda/README.md)
當一台電腦有多人使用，或者一個人同時管理多個project/repo，每個人使用的函式庫就很容易互相衝突。比方說A用的機器學習函式庫是torch/cpu/python3.8，B用的是torch/GPU-cuda124/python3.11，C用的是tensorflow/GPU-cuda116/python3.9，這些python版本/函式庫之間的衝突會讓這三個人完全做不了事。

而conda能讓使用者在電腦創建無數個獨立的程式執行環境，避免不同project/repo的衝突。

**[詳細安裝教學](./conda/README.md)**

###  [Poetry](./poetry/README.md)
即使是同一個project/repo，當它成長到一定規模時，自己的函式庫之間也可能會互相衝突。在我過往經驗，使用pip安裝函式庫，很常發生可以正常安裝函式庫，但執行時卻回報錯誤。

而poetry能協助你管理一個環境裡的函式庫之間的版本依賴關係。如果A函式庫需要<=3.0.0的numpy，B函式庫需要>=4.0.0的numpy，那poetry就會告訴你這個問題並不安裝它。

**[詳細使用指南](./poetry/README.md)**

### [Git](./git/README.md)
在多人合作的repo中，同一份程式碼A改了某部份，B改了另一部份，但A不知道B改了哪裡，B也不知道改了哪裡。甚至連大家手上的程式是不是同一份都不確定。

為了避免這個問題，有人利用雲端建了一套程式管理系統，就叫作git。
- 對個人而言，它可以讓你快速同步不同電腦間的程式碼
- 對團隊而言，它能避免多人分工時的程式衝突/重工問題

**[Git 與 GitHub 設定教學](./git/README.md)**

### 具體實例
- [HCC Survival Analysis](https://github.com/a7266165/HCC_Survival_Analysis)
- [AD-Sensor-Project](https://github.com/a7266165/AD-Sensor-Project)

---

## 入門範例

### 鐵達尼號存活分析（待補）
_即將推出..._

### MNIST資料集手寫數字 0-9分類（待補）
_即將推出..._

---

以上，希望能給大家一些幫助~

## 誌謝

感謝以下同學貢獻（按姓氏筆劃排序）：
- 林宥辰
- 徐維鴻
- 黃彥銘

## 授權條款
本專案採用 MIT License 進行授權 - 詳見 [LICENSE](./LICENSE) 檔案。
