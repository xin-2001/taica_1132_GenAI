# 作業三
113-2 TAICA_生成式AI：文字與圖像生成的原理與實務
[TOC]

## 主題二:GAN原理
研究GAN背後原理，試著用自己的方式解釋Cross Entropy、KL divergence。 (延伸內容：實際計算、比較兩者的效果、程式實驗、使用情境等等)

繳交方式：
- 寫明是主題幾。
- colab連結(請記得將共用權限打開)or附上pdf檔。
- 請在重點處以 MarkDown 註明，並且貼上重點截圖。
- 也可以自行增加內容。
---
### GAN原理
GAN 的核心思想是生成器 (Generator) 和 判別器 (Discriminator) 之間的對抗。
可以將生成器比擬為駭客，而鑑別器比擬為防火牆或檢測系統。
- 生成器（Generator）是駭客:目的是製造假的數據（例如假身份）並混入真實數據庫，讓它看起來毫無破綻。
- 鑑別器（Discriminator）是防火牆或檢測系統:它的任務是分辨哪些數據是真實的，哪些是駭客生成的假數據。

對抗過程：

- 駭客（生成器）不斷提升技能，製造出看似更真實的假數據。
- 防火牆（鑑別器）也不斷升級，學習如何更準確地識別假數據。

最終目標：駭客的假數據高超到連最強的防火牆都無法辨別真假。

在 GAN 中，判別器和生成器分別使用 Cross Entropy 和 KL Divergence 作為損失函數，通過最小化這些損失函數，它們可以互相競爭，最終生成逼真的數據。

### Cross Entropy(交叉熵/ㄕㄤ)
Cross Entropy 是駭客的測試結果

Cross Entropy 就像駭客完成一次進攻後，得到一份“測試報告”，告訴他：
> 進攻得多成功，還有多少次被防火牆識破。
> - 這個數值越小，表示駭客的技能越高（生成器變強）
> - 數值越大，表示駭客還需要改進。

在 GAN 中，判別器的目標是用最少的字數來描述真實數據和生成數據之間的差異。交叉熵越低，表示判別器越能準確地區分真實數據和生成數據。


### KL divergence
KL 散度是駭客的“偽裝指數”

KL 散度可以用來衡量駭客偽裝的假數據跟真實數據有多相似：
- 如果 KL 散度很小，表示駭客的假數據已經幾乎和真實數據一樣了，超級擬真。
- 如果 KL 散度很大，表示假數據的漏洞還多，防火牆很容易發現。

在 GAN 中，生成器的目標是讓自己生成的數據的描述方式儘可能接近真實數據的描述方式。KL 散度越低，表示生成數據越逼真。

:::warning
- Cross Entropy： 用來衡量描述一件事情所需要的字數，越低越好。
- KL Divergence： 用來衡量兩個描述方式之間的差異，越低越好。
:::


### 實際操作
#### 計算
- Cross Entropy公式:
  > $H(P, Q) = - Σ P(x) * log(Q(x))$
  > - $𝑝(x)$:真實分布
  > - $q(x)$:預測分布
  > - $−log𝑞(𝑥)$:預測錯誤的成本越高，懲罰越大
- KL divergence公式:
  >  $D_KL(P || Q) = Σ P(x) * log(P(x) / Q(x))$
  > - $𝑝(x)$:真實分布
  > - $q(x)$:預測分布
  > - 越接近 $0$，表示兩個分布越相似。
- Cross Entropy與KL divergence的關係
  > $H(p, q) = H(p) + D_{KL}(p \| q)$
  > 
  > Cross Entropy 可以視為包含 KL Divergence 的部分，因此兩者緊密相關。

#### 比較效果與應用場景
- Cross Entropy 的應用:
  - 分類問題： 交叉熵損失函數經常用於深度學習（例如神經網絡）中的分類問題。它用來衡量模型的預測（q）與真實標籤（p）之間的差異，值越小，模型越準確。
  - 二元分類 (Binary Classification): 常與 Sigmoid 函數配合。
  - 多類別分類 (Multi-Class Classification): 通常與 Softmax 一起使用。

- KL Divergence 的應用:
  - 生成模型： 如變分自編碼器（VAE），使用 KL Divergence 測量生成分布與目標分布的差異。
  - 機率分布的比較： 用於檢測兩個分布是否相似，例如自然語言處理中的語言建模。

#### 程式實驗: Python 範例
程式碼:[程式碼3-2](113_2GenAI_HW3_2.ipynb)
```python!
import numpy as np
from scipy.stats import entropy

# 真實分布 (p) 和 預測分布 (q)
p = np.array([0.4, 0.6])
q = np.array([0.3, 0.7])

# 計算 Cross Entropy
cross_entropy = -np.sum(p * np.log(q))
print(f"Cross Entropy: {cross_entropy}")

# 計算 KL Divergence
kl_divergence = np.sum(p * np.log(p / q))
print(f"KL Divergence: {kl_divergence}")

# 驗證關係: H(p, q) = H(p) + D_{KL}(p || q)
entropy_p = -np.sum(p * np.log(p))  # p 的熵
print(f"Entropy of p: {entropy_p}")
print(f"H(p, q) = {entropy_p + kl_divergence}")
```
- 成果
  > ![image](https://hackmd.io/_uploads/Syhccvbnyx.png)
  > 
  > 從結果來看可以明顯看出Cross Entropy 包含 KL Divergence


