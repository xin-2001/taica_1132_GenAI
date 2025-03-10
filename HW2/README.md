# HW2
## 主題:打造類神經網路
程式碼請參閱：[程式碼](113_2GenAI_HW2.ipynb)

1. 使用==4層隱藏層==，分別為20、50、40、20神經元。
2. 檢視資料
   - x_train.shape 檢視變數大小
   - x_train[8740] 查看目前數據內容
3. 標準化
   - x_train.reshape(60000, 784)/255
     > 將數據除255標準化，重新更變長度為784
4. 建立模型
   - model = Sequential()
     > Sequential 模型是一種線性模型，由按順序堆疊的層組成。這意味著每一層的輸出都成為下一層的輸入。這是一種建立神經網路的簡單而通用的方法。
5. 加入隱藏層
   - model.add(Dense(N1, input_dim=784, activation='relu'))
      > Dense() 是 Keras 中密集層的類別。units：層中神經元的數量。input_dim：輸入資料的維度。activation：激活函數。
      > 其他激活函數：sigmoid、tanh、softmax等
      > softmax:將輸入值轉換成概率分布，常用於多分類問題。
6. 配置訓練參數
   - model.compile() 方法用於配置模型的訓練方式。
   - loss：損失函數。
     > ==categorical_crossentropy==:用於多類別分類問題的常見損失函數。
   - optimizer：優化器。
     > ==Adam(learning_rate=0.001)==:用於更新模型的權重以最小化損失函數。
     > 學習率通常在 0.001 到 0.1 之間
7. 訓練模型
   - model.fit(x_train, y_train, batch_size=100, epochs=10)
     > batch_size：批次大小。表示每次迭代中使用的訓練樣本數量(100)。批次大小會影響訓練速度和記憶體使用量。
     > epochs：訓練週期數。表示模型將在整個訓練資料集上迭代 10 次。週期數會影響模型的訓練程度和性能。
8. 使用測試資料測試
   - loss, acc = model.evaluate(x_test, y_test)
     > ==accuracy: 0.9427== ; ==loss: 0.1913==
   - score = model.evaluate(x_test, y_test)
     > ==loss==: 0.1589910238981247
     > ==正確率==: 0.9531000256538391
9. 使用Gradio測試
   - ![image](https://github.com/user-attachments/assets/2a9655cb-b846-41b0-8009-cc8aec604f9a)
   - ![image](https://github.com/user-attachments/assets/e3c3a00b-c1b2-48eb-bdf9-068a190923e9)


