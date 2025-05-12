# 作業十
113-2 TAICA_生成式AI：文字與圖像生成的原理與實務

## 主題:diffusers套件圖像生成
- 程式碼請參閱：[程式碼1](113_2GenAI_HW10.ipynb)、[程式碼2](113_2GenAI_HW10_g.ipynb)

說明
- 選定一個合適的模型，試著生出各種圖片。
- 修改prompt，甚至可以推薦prompts給使用者。
- 其餘延伸由同學自由發揮。
- 模型也可以至https://civitai.com/models搜尋，找到心儀的模型後再到hugging face中搜尋。(找不到或許在hugging face上沒有)

### 模型選用
使用```ashiqabdulkhader/shiba-dog```，[來源](https://huggingface.co/ashiqabdulkhader/shiba-dog)。

### 測試prompt
- 使用[程式碼1](113_2GenAI_HW10.ipynb)
#### 基本生圖
- ```pipe = StableDiffusionPipeline.from_pretrained(model_name, torch_dtype=torch.float16, use_auth_token=True).to("cuda")```:建立 Stable Diffusion 模型的 pipeline。
- ```Random seed``` 是一個用於初始化隨機數生成器的數值。當你設定一個特定的 random seed 時，每次執行程式碼都會產生相同的隨機數序列，進而產生相同的圖像。如果沒有設定 random seed，每次執行程式碼都會產生不同的噪訊，進而產生不同的圖像。
- pipe(...): 這是呼叫 Stable Diffusion pipeline 的方法，用於執行圖像生成。pipeline 會根據提供的參數生成圖像。
  - prompt=prompt: 指定生成圖像的提示文字，這裡使用 prompt 變數的值作為提示。
  - height=height: 指定生成圖像的高度，這裡使用 height 變數的值作為高度。
  - width=width: 指定生成圖像的寬度，這裡使用 width 變數的值作為寬度。
  - num_inference_steps=num_inference_steps: 指定生成圖像的推理步數，這裡使用 num_inference_steps 變數的值作為推理步數。推理步數越多，生成的圖像質量越高，但生成時間也會越長。
  - guidance_scale=guidance_scale: 指定生成圖像的指引強度，這裡使用 guidance_scale 變數的值作為指引強度。指引強度越高，生成的圖像越符合提示文字，但生成的多樣性也會降低。
  - generator=generator: 指定生成圖像的隨機數生成器，這裡使用 generator 變數的值作為隨機數生成器。這可以確保每次執行程式碼時都能生成相同的圖像。
  - .images[0]: 從 pipeline 的輸出中獲取生成的圖像。images 是一個包含生成圖像的列表，[0] 表示獲取列表中的第一張圖像。
#### Negative Prompt
- Negative Prompt 是一種用於排除或抑制圖像中特定元素或特徵的技術。它與一般的 Prompt 相反，一般的 Prompt 是用來引導模型生成你想要的內容，而 Negative Prompt 則是告訴模型你不想要出現的內容。
- Negative Prompt 的作用:
  - 提升圖像品質： 透過排除常見的圖像瑕疵，例如模糊、顆粒感、變形等，Negative Prompt 可以提升生成圖像的整體品質。
  - 控制圖像內容： Negative Prompt 可以用於排除特定元素或特徵，例如特定的人物、物件、顏色等，讓生成的圖像更符合你的需求。
  - 提升生成效率： 透過限制模型的生成方向，Negative Prompt 可以減少模型生成不需要內容的可能性，進而提升生成效率。
- 缺點
  - 它只能減少特定元素或特徵出現的可能性，並不能完全保證它們不會出現。
  - 過度使用 Negative Prompt 可能會降低生成的多樣性： 如果你的 Negative Prompt 太過嚴格，可能會限制模型的生成空間，導致生成的圖像缺乏變化。
#### 最佳化prompt
- enhanced_prompt 是基於原始 prompt 進行優化後的提示詞，目的是為了生成更高品質、更符合預期的圖像。
- 作用:
  - masterpiece: 指示模型生成具有傑作級品質的圖像。
  - ultra high quality: 指示模型生成具有超高解析度和細節的圖像。
  - intricate skin details: 指示模型關注皮膚細節，生成更逼真的動物毛髮和皮膚紋理。
  - cinematic lighting: 指示模型使用電影級的燈光效果，提升圖像的藝術性和氛圍感。
#### 更換的排程器
- 將 Stable Diffusion pipeline (pipe) 中的 scheduler 替換成 UniPCMultistepScheduler。
- Scheduler 在 Stable Diffusion 中扮演著重要的角色，它負責控制圖像生成過程中的去噪步驟。不同的 scheduler 會使用不同的演算法和策略來控制去噪過程，進而影響生成圖像的品質和風格。
- UniPCMultistepScheduler 是一種高效能的 scheduler，它可以生成更高品質的圖像，並且比其他一些 scheduler 更快。
- pipe.scheduler: 這是 Stable Diffusion pipeline 中的 scheduler 屬性，用於存取和設定 pipeline 使用的 scheduler。
- UniPCMultistepScheduler.from_config(...): 這是 UniPCMultistepScheduler 類別的一個方法，用於從配置資訊建立一個新的 UniPCMultistepScheduler 物件。
- pipe.scheduler.config: 這是 pipeline 中當前 scheduler 的配置資訊。透過將當前 scheduler 的配置資訊傳遞給 UniPCMultistepScheduler.from_config 方法，可以確保新的 UniPCMultistepScheduler 使用與當前 scheduler 相同的配置。
### 製作成視覺化界面
使用[程式碼2](113_2GenAI_HW10_g.ipynb)
- 使用Gradio呈現
> [!image.png](hw10-11.png)

### 結果展現
1. Three dogs playing in the square, one of which is a Shiba Inu.
   > [!image.png](hw10-1.png)
   > [!image.png](hw10-2.png)
   > [!image.png](hw10-3.png)
2. Shiba Inu sitting in front of the computer and working.
   > [!image.png](hw10-4.png)
   > [!image.png](hw10-5.png)
   > [!image.png](hw10-6.png)
3. Shiba Inu running in the rain.
   > [!image.png](hw10-7.png)
   > [!image.png](hw10-8.png)
   > [!image.png](hw10-9.png)
   > [!image.png](hw10-10.png)
