# 作業八
113-2 TAICA_生成式AI：文字與圖像生成的原理與實務

## 主題:使用aisuite使用多LLM的應用
- 程式碼請參閱：
  1. 使用aisuite同時利用多個LLM：[程式碼1](113_2GenAI_HW8.ipynb)
  2. 群組發言小幫手(Reflection)：[程式碼2](113_2GenAI_HW8_a.ipynb)
  3. 柴語生成器(CoT)：[程式碼3](113_2GenAI_HW8_c.ipynb)

說明
- 參考老師【Demo07a】或【Demo07c】程式碼，修改成自己的樣子。
- (Planning模式) 思考一下自己的原始任務是什麼，並想一下怎麼去計劃自己的二階段推理過程。
- (Reflection模式) 思考一下自己的原始任務是什麼，並想一下怎麼去安排Reflection的任務設計。
- Gradio展示。

### 使用aisuite同時利用多個LLM
#### aisuite
- aisuite 允許您輕鬆地在不同的 LLM 之間切換，而無需更改程式碼。
- 它支援多個 LLM 供應商，包括 OpenAI、Mistral、Groq 和 Google。
- aisuite 提供了一個簡單的界面，用於與 LLM 互動，例如傳送提示和接收回應。
#### 同時使用2個模型
1. 模型1
   - provider1 = "groq"
   - model1 = "gemma2-9b-it"
2. 模型2
   - provider2="groq"
   - model2="llama3-70b-8192"
3. 使用同一組system
   - system = "請把使用者寫的事, 轉換成一種生動有趣的文案, 可以幽默一點, 請用台灣習慣的中文回應。"
4. 設置生成函數```two_post```
```python
def two_post(prompt):
    # 機器人A
    response1 = reply(prompt, system,
              provider = provider1,
              model = model1
              )

    # 機器人B
    response2 = reply(prompt, system,
              provider = provider2,
              model = model2
              )

    return response1, response2
```
#### 結果展現
> ![image.png](https://github.com/xin-2001/taica_1132_GenAI/blob/main/HW8/hw8-1.png?raw=true)
> ![image.png](https://github.com/xin-2001/taica_1132_GenAI/blob/main/HW8/hw8-2.png?raw=true)
> ![image.png](https://github.com/xin-2001/taica_1132_GenAI/blob/main/HW8/hw8-3.png?raw=true)


### 群組發言小幫手(Reflection)
#### Reflection (反思)
- Reflection (反思) 是一種讓 AI 代理能夠 檢視自身行為並根據回饋進行調整 的機制。它模擬了人類反思自身行為，從經驗中學習並改進的過程。
- Reflection 模式通常涉及兩個或多個 AI 代理，協同工作以完成任務。其中一個代理負責生成內容或執行任務，另一個代理則負責檢視和評估第一個代理的產出，並提供改進建議。
- Reflection 的優點
  - 提高輸出品質: 通過反思和改進，AI 代理可以產出更準確、更自然、更符合預期的結果。
  - 促進學習: Reflection 模式鼓勵 AI 代理從錯誤中學習，並隨著時間推移不斷提升自身能力。
  - 增強協作: 多個代理之間的協作和回饋，可以促進知識共享和共同進步。
#### 程式實作
1. 使用者輸入要傳達的內容
2. model_writer 生成第一版文本（正式、禮貌、通順）
   - provider_writer = "groq"
   - model_writer="gemma2-9b-it"
   - system_writer = "你是一位群組發言小幫手，擅長把使用者寫的內容，轉換成正式、禮貌、通順的發言內容，用於之事項傳遞或請求，並適當加入emoji，使語氣更自然親切。請用台灣習慣的中文回應。"
3. model_reviewer 檢查內容是否夠自然、口語化，並提供具體修改建議
   - provider_reviewer = "groq"
   - model_reviewer = "llama3-70b-8192"
   - system_reviewer = "你是一位文案潤稿專家，請針對以下貼文給出具體修改建議。檢查檢查文案是否足夠正式、表達得自然、口語化，同時保留其禮貌和通順性，使其更貼近一般社群媒體的語境。並提醒使用台灣用語。請用台灣習慣的中文回應。"
4. model_writer 根據建議產出第二版
   > 設置函數```reflect_post```。
   ```python
   def reflect_post(prompt):
    # Step 1: Writer 初稿
    first_version = reply(system_writer, prompt,
                          provider=provider_writer,
                          model=model_writer
                          )

    # Step 2: Reviewer 給建議
    suggestion = reply(system_reviewer, first_version,
                       provider=provider_reviewer,
                       model=model_reviewer
                       )

    # Step 3: Writer 再寫一次（根據建議）
    second_prompt = f"這是我剛剛寫的文案：\n{first_version}\n\n這是修改建議：\n{suggestion}\n\n請根據這些建議，幫我改得更生活化、更自然。"
    second_version = reply(system_writer, second_prompt,
                           provider=provider_writer,
                           model=model_reviewer
                           )

    return first_version, suggestion, second_version
   ```
5. 結果展現
   > ![image.png](https://github.com/xin-2001/taica_1132_GenAI/blob/main/HW8/8a-1.png?raw=true)

### 柴語生成器(CoT)
#### Chain-of-Thought（CoT）
Chain-of-Thought (CoT) 推理是一種用於提升大型語言模型 (LLM) 解決複雜推理問題能力的技術。核心概念是模仿人類的思考過程。當人類面對一個複雜問題時，我們通常會將其分解成一系列的步驟，逐步推理，最終得出答案。CoT 便是引導 LLM 模仿這種逐步推理的過程。
- 運作方式
  1. 問題分解： 將一個複雜問題拆解成多個更容易處理的子問題。
  2. 逐步推理： 引導 LLM 對每個子問題進行推理，並生成中間步驟的答案。
  3. 答案整合： 將所有中間步驟的答案組合起來，形成最終的答案。
- 優點
  - 提升推理能力： CoT 可以幫助 LLM 更好地理解問題，並進行更深層次的推理。
  - 提高準確性： 透過逐步推理，CoT 可以減少 LLM 出現錯誤的可能性。
  - 增強可解釋性： CoT 可以讓 LLM 的推理過程更加透明，更容易理解。
#### 程式實作
1. 第一階段（思考階段）：請 LLM 思考五種「為什麼看待事情的樂觀角度」的原因。
   - provider_planner = "groq"
   - model_planner="gemma2-9b-it"
   - system_planner = "你是一隻活潑的柴犬, 擅長將倒楣的小事轉化為樂觀的觀點。請針對使用者的事件，思考出五種『看待事情的樂觀面向』, 列出條列式清單。用第一人稱思考也可以。請用台灣習慣的中文回應"
2. 第二階段（產文階段）：從這五個原因中挑出最有趣的一個，寫成社群發文（柴語風格 + 第一人稱 + emoji + "汪！" 結尾）
   - provider_writer = "groq"
   - model_writer = "llama3-70b-8192"
   - system_writer = "用柴犬的視角來回應使用者的問題，充滿樂觀、友善又有點調皮的語氣。你說話的方式就像一隻熱情、愛玩的柴犬，總是能用單純卻溫暖的方式解釋事情，並以「汪！」結尾，讓人會心一笑，適時加入 emoji。請用台灣習慣的中文回應"
3. 設置```happy_post```函數
   ```python
   def happy_post(prompt):
    # Step 1: CoT - 思考五種樂觀角度
    planning_prompt = f"使用者說：{prompt}。請幫我想五種樂觀的角度，用中文呈現。"
    happy_reasons = reply(system_planner, planning_prompt,
                          provider = provider_planner,
                          model = model_planner
                          )

    # Step 2: 選出最有趣一項，寫成貼文
    generation_prompt = f"這是我想到的五個理由：\n{happy_reasons}\n\n請從中選出一個最有趣的理由，然後根據它寫一段中文柴語發文。"
    happy_post = reply(system_writer, generation_prompt,
                       provider = provider_writer,
                       model = model_writer
                       )

    return happy_reasons, happy_post
   ```
#### 結果展現
> ![image.png](https://github.com/xin-2001/taica_1132_GenAI/blob/main/HW8/hw8c-3.png?raw=true)
> ![image.png](https://github.com/xin-2001/taica_1132_GenAI/blob/main/HW8/hw8c-4.png?raw=true)
