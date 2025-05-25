# 作業十二
113-2 TAICA_生成式AI：文字與圖像生成的原理與實務

## 期末專案發想

說明
1. 藉由此份作業來幫助同學提早對期末專案進行發想，以及讓助教們有提早引導同學的機會。
2. 寫下你預期的期末專案樣子。
3. 已經開始動工的同學，可以附上連結或截圖。

### 研究方向
- 主題:LLM角色與提問模式分析——以Gemini與Llama3為例
- 說明:本研究以 Google Gemini-2.5-flash 作為被提問的 LLM，Groq Llama3-70b-8192 作為提問的 LLM，透過不同角色設定，觀察其在資訊科學問題上的提問模式與互動方式。本研究以序列分析方法，探索不同角色設定如何影響提問過程，並評估模型間的提問策略是否能有效改善問題解決的效率。

### 研究工具
1. 對話生成工具
   - 使用Colab做為開發工具
   - 被提問LLM：Google Gemini-2.5-flash
   - 提問LLM：Groq Llama3-70b-8192
     - 設計14個角色設定。
   - 每個對話17輪(被提問LLM與提問LLM來回為一輪)。
   - 對話完畢後輸出為CSV檔。
   - [程式碼](https://github.com/xin-2001/taica_1132_GenAI/blob/7a65b351b1623e7f18a84a4f8b5fcaf9bc93f8d8/Final_Project/Dialogue_Generation.ipynb)
2. 將對話編碼
   - 開發一電腦科學的對話類別編碼。
   - 使用Google AI Studio 輔助編碼。
3. 序列分析
   - 使用[布丁布丁吃甚麼?](https://blog.pulipuli.info/2010/12/sequential-analysis-tool.html)分析結果。
  
