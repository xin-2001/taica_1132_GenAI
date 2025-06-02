# 期末專案
113-2 TAICA_生成式AI：文字與圖像生成的原理與實務

說明
1. 介紹你使用的模型。
2. 說明你在這次專案想達成的目的。
3. 以文字+截圖的方式來呈現專案重點（包括調整、引導的過程）。
4. 專案最終成果。

特別注意：
> - 圖片生成類，除了附上生成後的原圖，還需連同操作介面中的小圖畫面，佐證是從特定模型中所生成。
> - 文字生成類，除了附上生成出來的文字，也還截取包括操作介面中的文字畫面。

繳交方式
1、以 Colab 實作的附上 Colab 連結。且附上重點的截圖。
2、非 Colab 實作，但能產生連結來展現實作結果的，請附上該連結與重點的截圖。
3、無法產生實作連結的其它生成模型，請搭配文字與該模型操作過程中的截圖。

## 介紹
- 主題:LLM角色與提問模式分析——以Gemini與Llama3為例
- 說明:本研究以 Google Gemini-2.5-flash 作為被提問的 LLM，Groq Llama3-70b-8192 作為提問的 LLM，透過不同角色設定，觀察其在資訊科學問題上的提問模式與互動方式。本研究以序列分析方法，探索不同角色設定如何影響提問過程，並評估模型間的提問策略是否能有效改善問題解決的效率。

## 研究設計
1. 對話生成工具
   - 使用Colab做為開發工具
   - 被提問LLM模型：Google Gemini-2.5-flash
   - 提問LLM模型：Groq Llama3-70b-8192
     - 設計14個角色設定。
   - 每個對話17輪(被提問LLM與提問LLM來回為一輪)。
   - 對話完畢後輸出為CSV檔。
   - [對話生成程式碼](https://github.com/xin-2001/taica_1132_GenAI/blob/7a65b351b1623e7f18a84a4f8b5fcaf9bc93f8d8/Final_Project/Dialogue_Generation.ipynb)
   - 對話生成紀錄：[原始對話資料](原始對話資料)。
2. 編碼
   - 開發一電腦科學的對話類別編碼。[編碼表](編碼表.md)
   - 使用Google AI Studio 輔助編碼。[編碼結果](編碼結果)
3. 分析
   - 序列分析:使用[布丁布丁吃甚麼?](https://blog.pulipuli.info/2010/12/sequential-analysis-tool.html)。
   - 滯後序列分析:使用[滯後序列分析計算器Lag Sequential Analysis](https://pulipulichen.github.io/HTML-Lag-Sequential-Analysis/)。
## 結果
### 十四個角色個案序列分析


### 滯後序列分析


### 綜合討論


## 討論
