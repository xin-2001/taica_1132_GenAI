# HW1

## 主題：使用Python繪製神奇寶貝球
- 文件說明請參閱：[文件說明PDF](HW1_ntnu_61308006E.pdf)
- 程式碼請參閱：[程式碼](113_2GenAI_HW1.ipynb)

### 說明
參考[網路資源](https://www.desmos.com/calculator/dpceohzm5o?lang=zh-TW)，找到使用函數製作的卡通圖案，將函式使用python呈現，並在置圖時加入參數增加其美觀，例如：線的粗細、填充的顏色等，以及匯入中文字體使其可以在圖表中呈現中文字。
這些函數組合成的結果會是一顆神奇寶貝球，除了是神奇寶貝球的圖案外，我還額外設置了a、b兩個參數，透過調整a、b參數，可以使神奇寶貝球呈現不同的視角。
- 中文字體
  1. 載入字體
     > !wget -O LXGWWenKaiMonoTC-Regular.ttf "https://github.com/lxgw/LxgwWenkaiTC/raw/main/fonts/TTF/LXGWWenKaiMonoTC-Regular.ttf"
  2. 設定字體
     > ![image](https://github.com/user-attachments/assets/dccec26c-35e9-450b-98fe-5a05e604231d)
- 數學式
  1. $x^{2}+y^{2}-1=0$
  2. $ \left(\left(x-\sin\left(a\pi\right)\cos\left(b\pi\right)\right)^{2}+\left(y-\sin\left(b\pi\right)\right)^{2}+\left(\sqrt{1-x^{2}-y^{2}}-\sqrt{1-\sin\left(a\pi\right)^{2}\cos\left(b\pi\right)^{2}-\sin\left(b\pi\right)^{2}}\right)^{2}-0.1\right)\sqrt{\cos\left(a\pi\right)}=0 $
  3. $\left(\left(x-\sin\left(a\pi\right)\cos\left(b\pi-0.5\pi\right)\right)^{2}+\left(y-\sin\left(b\pi-0.5\pi\right)\right)^{2}+\left(\frac{\operatorname{abs}\left(\cos\left(a\pi\right)\cos\left(b\pi-0.5\pi\right)\right)}{\cos\left(a\pi\right)\cos\left(b\pi-0.5\pi\right)}\sqrt{1-x^{2}-y^{2}}-\sqrt{\left(1-\sin\left(a\pi\right)^{2}\cos\left(b\pi-0.5\pi\right)^{2}-\sin\left(b\pi-0.5\pi\right)^{2}\right)}\right)^{2}-2\right)\sqrt{\left(\left(x-\sin\left(a\pi\right)\cos\left(b\pi\right)\right)^{2}+\left(y-\sin\left(b\pi\right)\right)^{2}+\left(\sqrt{1-x^{2}-y^{2}}-\sqrt{1-\sin\left(a\pi\right)^{2}\cos\left(b\pi\right)^{2}-\sin\left(b\pi\right)^{2}}\right)^{2}-0.1\right)}=0$
  4. $\left(\left(x-\sin\left(a\pi\right)\cos\left(b\pi-0.5\pi\right)\right)^{2}+\left(y-\sin\left(b\pi-0.5\pi\right)\right)^{2}+\left(\frac{\operatorname{abs}\left(\cos\left(a\pi\right)\cos\left(b\pi-0.5\pi\right)\right)}{\cos\left(a\pi\right)\cos\left(b\pi-0.5\pi\right)}\sqrt{1-x^{2}-y^{2}}-\sqrt{\left(1-\sin\left(a\pi\right)^{2}\cos\left(b\pi-0.5\pi\right)^{2}-\sin\left(b\pi-0.5\pi\right)^{2}\right)}\right)^{2}-2\right)\sqrt{-\cos a\pi}\sqrt{-\left(\left(x-\sin\left(a\pi\right)\cos\left(b\pi\right)\right)^{2}+\left(y-\sin\left(b\pi\right)\right)^{2}+\left(\sqrt{1-x^{2}-y^{2}}-\sqrt{1-\sin\left(a\pi\right)^{2}\cos\left(b\pi\right)^{2}-\sin\left(b\pi\right)^{2}}\right)^{2}-0.1\right)}=0$
  5. $\left(\left(x-\sin\left(a\pi\right)\cos\left(b\pi\right)\right)^{2}+\left(y-\sin\left(b\pi\right)\right)^{2}+\left(\sqrt{1-x^{2}-y^{2}}-\sqrt{1-\sin\left(a\pi\right)^{2}\cos\left(b\pi\right)^{2}-\sin\left(b\pi\right)^{2}}\right)^{2}-0.05\right)\sqrt{\cos a\pi}=0$

- 著色面積
1. $\left(\left(x-\sin\left(a\pi\right)\cos\left(b\pi-0.5\pi\right)\right)^{2}+\left(y-\sin\left(b\pi-0.5\pi\right)\right)^{2}+\left(\frac{\operatorname{abs}\left(\cos\left(a\pi\right)\cos\left(b\pi-0.5\pi\right)\right)}{\cos\left(a\pi\right)\cos\left(b\pi-0.5\pi\right)}\sqrt{1-x^{2}-y^{2}}-\sqrt{\left(1-\sin\left(a\pi\right)^{2}\cos\left(b\pi-0.5\pi\right)^{2}-\sin\left(b\pi-0.5\pi\right)^{2}\right)}\right)^{2}-2\right)\sqrt{\left(\left(x-\sin\left(a\pi\right)\cos\left(b\pi\right)\right)^{2}+\left(y-\sin\left(b\pi\right)\right)^{2}+\left(\sqrt{1-x^{2}-y^{2}}-\sqrt{1-\sin\left(a\pi\right)^{2}\cos\left(b\pi\right)^{2}-\sin\left(b\pi\right)^{2}}\right)^{2}-0.1\right)}>0$

- 可變變數
  > 透過調整a、b參數改變呈現角度
  1. $-0.5 < a < 0.5$
  2. $-0.5 < b < 0.5$


### 成果
- 在a設置為0.01，且b設置為0.03時，神奇寶貝球呈現如下
  > ![image](https://github.com/user-attachments/assets/833ed5b7-0da4-4864-b1f3-eaa629c57c66)
- 在a設置為0.24，且b設置為0.13時，神奇寶貝球呈現如下
  > ![image](https://github.com/user-attachments/assets/f5b3b743-785d-4d2f-a97e-3caafb69bfd1)
