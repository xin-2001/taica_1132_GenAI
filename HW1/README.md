# HW1

## 主題：使用Python繪製神奇寶貝球
- 文件說明請參閱：[文件說明PDF](HW1_ntnu_61308006E.pdf)
- 程式碼請參閱：[程式碼](113_2GenAI_HW1.ipynb)

### 說明
參考[網路資源](https://www.desmos.com/calculator/dpceohzm5o?lang=zh-TW)，找到使用函數製作的卡通圖案，將函式使用python呈現，並在置圖時加入參數增加其美觀，例如：線的粗細、填充的顏色等，以及匯入中文字體使其可以在圖表中呈現中文字。
這些函數組合成的結果會是一顆神奇寶貝球，除了是神奇寶貝球的圖案外，我還額外設置了a、b兩個參數，透過調整a、b參數，可以使神奇寶貝球呈現不同的視角。
- 中文字體
  1. 載入字體
     > ```!wget -O LXGWWenKaiMonoTC-Regular.ttf "https://github.com/lxgw/LxgwWenkaiTC/raw/main/fonts/TTF/LXGWWenKaiMonoTC-Regular.ttf"```
  2. 設定字體
     > ![image](https://github.com/user-attachments/assets/dccec26c-35e9-450b-98fe-5a05e604231d)
- 數學式
  1. $x^{2}+y^{2}-1=0$
  2. ![image](https://github.com/user-attachments/assets/9602f72f-8a5c-4187-b620-8b2261cd7266)
  3. ![image](https://github.com/user-attachments/assets/5be17c55-bd9c-4ab7-8dbc-aefe46896815)
  4. ![image](https://github.com/user-attachments/assets/5cd04e8a-becb-432d-a41c-fca3df15e8ee)
  5. ![image](https://github.com/user-attachments/assets/854739ea-03a3-4a53-b29b-745e6b07c2c8)

- 著色面積
1. ![image](https://github.com/user-attachments/assets/d82c6f8f-9f2b-4c4f-a583-4d894a939750)

- 可變變數
  > 透過調整a、b參數改變呈現角度
  1. $-0.5 < a < 0.5$
  2. $-0.5 < b < 0.5$


### 成果
- 在a設置為0.01，且b設置為0.03時，神奇寶貝球呈現如下
  > ![image](https://github.com/user-attachments/assets/833ed5b7-0da4-4864-b1f3-eaa629c57c66)
- 在a設置為0.24，且b設置為0.13時，神奇寶貝球呈現如下
  > ![image](https://github.com/user-attachments/assets/f5b3b743-785d-4d2f-a97e-3caafb69bfd1)
