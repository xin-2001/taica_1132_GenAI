# 作業十一
113-2 TAICA_生成式AI：文字與圖像生成的原理與實務

## 主題:Fooocus圖像生成
- 程式碼請參閱：[程式碼](113_2GenAI_HW11.ipynb)

說明
1. 設想一個應用情境，並使用 Fooocus 生成圖像。
  > (應用情境可能是：社群平台用圖、簡報圖、網站視覺元素、個人品牌圖像等。)
2. 請至少生成3組圖像，同一張圖的輸入/輸出視為一組。
  > 輸入：為每張圖撰寫簡短說明，例如：使用到 Fooocus 的哪些功能。(prompt 設定、Style、Inpaint、Canny 等）
  > 輸出：生成的圖。
3. 請簡要整理你這份作業的創作流程(文字敘述或流程圖均可)，讓助教/老師能了解你從靈感、設定、試圖改善到輸出圖片的步驟。
4. 整體使用心得分享。
5. 其餘延伸由同學自由發揮。

### 結果展現
1. 僅prompt:A shiba inu slumped over a desk full of computers and coffee cups, exhausted but cute.
   > ![image.png](result/result-1.png)
2. 勾選Input image>Upscale or Variation，並選擇Vary (Strong)
   - Prompt:A shiba inu slumped over a desk full of computers and coffee cups, exhausted but cute.
   > ![image.png](result/result-2.png)
3. 勾選Input image>Upscale or Variation，並選擇Vary (Subtle)
   - Prompt:A shiba inu slumped over a desk full of computers and coffee cups, exhausted but cute.
   > ![image.png](result/result-3.png)
4. 勾選Input image>Image Prompt(無勾選Advanced)
   - Prompt:A shiba inu slumped over a desk full of computers and coffee cups, exhausted but cute.
   > ![image.png](result/result-4.png)
5. 勾選Input image>Image Prompt(勾選Advanced)
   - Prompt:A shiba inu slumped over a desk full of computers and coffee cups, exhausted but cute.
   - 將兩張圖片Weight設置為0.8
   > ![image.png](result/result-5.png)
6. 勾選Input image>Upscale or Variation，並選擇Vary (Subtle)
   - Prompt:A shiba inu slumped over a desk full of computers and coffee cups, exhausted but cute.
   - 將左圖片Weight設置為1，右圖Weight設置為1.2。
   > ![image.png](result/result-6.png)
7. 勾選Input image>Upscale or Variation，並選擇Vary (Subtle)
   - 經過圖片生成的prompt=closed mouth, closed eyes, cup, no humans, animal, phone, sleeping, cellphone, smartphone, desk, dog, mug, pen, computer, disposable cup, pencil, animal focus, monitor, coffee, keyboard \(computer\), mouse \(computer\), coffee cup, eraser, shiba inu.
   > ![image.png](result/result-7.png)
8. 勾選Advanced>setting
   - Performance選擇Quality
   - 設置Negative Prompt
   - 設置Aspect Ratios為1:1
   > ![image.png](result/result-8.png)

#### 心得分享


