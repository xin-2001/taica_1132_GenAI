# 作業八
113-2 TAICA_生成式AI：文字與圖像生成的原理與實務

## 主題:使用aisuite使用多LLM的應用
- 程式碼請參閱：
  1. 使用aisuite同時利用多個LLM：[程式碼1](113_2GenAI_HW8.ipynb)
  2. 群組發言小幫手：[程式碼2](113_2GenAI_HW8_a.ipynb)
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


### 群組發言小幫手


### 柴語生成器(CoT)
