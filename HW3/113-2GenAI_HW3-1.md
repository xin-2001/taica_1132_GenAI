# 作業三
113-2 TAICA_生成式AI：文字與圖像生成的原理與實務
[TOC]

## 主題一:GAN模型生圖
找一個GAN模型來實際操作，並且試著多生幾張圖片。(上課沒說過的也可以)

繳交方式：
- 寫明是主題幾。
- 附上該模型來源(連結)，並簡單介紹這個模型。
- 同主題多生成幾張，並且附上輸入/輸出圖。(最多五組)
- 比較看看，為什麼現在較沒有人在使用GAN來生圖？
- 可以自行增加其他內容。

(為了助教們批改作業時閱讀順利，請將同一組輸入/輸出合併在一起為一張圖片)

### 模型1
來源:[This Person Does Not Exist](https://thispersondoesnotexist.com/)

說明:是一個利用生成對抗網絡（GAN）技術創建的專案，它能生成看似真實的人臉圖片，而這些人實際上並不存在。在網站上，每次刷新頁面時，會利用 GAN 的演算法生成一張全新的人臉。模型的原理是通過訓練神經網絡學習大量的真實人臉圖片，然後利用這些數據來創建全新的、完全虛構的圖像。
- ![2](https://hackmd.io/_uploads/rJlhVqgn1e.jpg)

  > <img src=https://hackmd.io/_uploads/rkU04cl31g.png width=50% />
  > <img src=https://hackmd.io/_uploads/HJhRE9lnye.png width=50% />
  > 
  > 模型很不穩定，下載會用演算法再生成一張新的，因此網頁看到的並非下載下來的。

### 模型2
來源:[edges2shoes](https://affinelayer.com/pixsrv/)

說明:Edges2Shoes 是一個基於 Pix2Pix 技術的模型，專門用於圖像到圖像的轉換。這個模型的核心是條件生成對抗網絡（Conditional GAN），它能夠將手繪的鞋子輪廓（edges）轉換成真實感十足的鞋子圖片。Pix2Pix 的工作原理是通過學習輸入圖像（例如輪廓）與目標圖像（例如真實鞋子）之間的映射關係，並同時學習一個損失函數來優化這種映射。這使得模型能夠生成高質量的圖像，並應用於多種圖像轉換任務，例如從素描生成照片、圖像著色等。
- <img src=https://hackmd.io/_uploads/ryGtnEZ3Jx.png width=40% /> <img src=https://hackmd.io/_uploads/Hk902V-21e.png width=40% />
- <img src=https://hackmd.io/_uploads/HyFJ6VWnJx.png width=40% /> <img src=https://hackmd.io/_uploads/ByhD6E-2yg.png width=40% />
- <img src=https://hackmd.io/_uploads/Sy1Fa4-nke.png width=40% />

### 模型3
來源:[AI生成GAN生圖模型](113_2GenAI_HW3_1.ipynb)

說明:使用Gemini生成GAN生圖程式碼，透過生成對抗網路 (GAN) 的深度學習模型來生成手寫數字圖像。
- <img src=https://hackmd.io/_uploads/r1vUaLZn1l.png width=40% /> <img src=https://hackmd.io/_uploads/ry1DpLZhJg.png width=40% />
- <img src=https://hackmd.io/_uploads/BJ9PaU-hke.png width=40% /> <img src=https://hackmd.io/_uploads/SJr_a8bhye.png width=40% />
- <img src=https://hackmd.io/_uploads/HkC56Ub2kx.png width=40% /> 
> 
> 需要花費大量時間訓練，且其很不穩定，可能一下很好，下一次就很不好。

### 討論
1. 為什麼現在較沒有人在使用GAN來生圖？

   儘管 GAN 在圖像生成領域取得了顯著的成果，並曾是生成圖像的首選方法，但近年來，它的流行度有所下降，主要原因如下：
- 訓練不穩定： GAN 的訓練過程非常不穩定，容易出現模式崩潰 (mode collapse)、梯度消失 (vanishing gradients) 等問題，導致生成結果不理想。
- 難以控制： GAN 的生成結果難以精確控制，例如難以指定生成圖像的特定屬性或風格。
- 生成品質： 雖然 GAN 可以生成逼真的圖像，但在某些情況下，生成的圖像仍然存在瑕疵或不自然之處，例如圖像模糊、細節缺失等。
- 新方法的出現： 近年來，出現了許多新的圖像生成方法，例如擴散模型 (Diffusion Models)、變分自編碼器 (Variational Autoencoders, VAEs) 等，這些方法在某些方面比 GAN 更有優勢，例如訓練更穩定、生成品質更高、更易於控制等。
- 擴散模型 (Diffusion Models) 的崛起：擴散模型是一種基於馬爾可夫鏈的生成模型，它通過逐步添加高斯雜訊將數據轉換為純雜訊，然後學習逆轉這個過程來生成新的數據。擴散模型在圖像生成方面取得了令人矚目的成果，其生成品質通常優於 GAN，並且訓練過程更穩定。因此，擴散模型逐漸成為圖像生成領域的主流方法之一。

雖然 GAN 在圖像生成領域做出了重要貢獻，但由於其訓練不穩定、難以控制、生成品質等問題，以及新方法的出現，它的流行度有所下降。擴散模型等新方法在許多方面都比 GAN 更有優勢，因此逐漸成為研究者和開發者的首選。
