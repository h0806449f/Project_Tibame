(中 Chinese/ 英 English)

# 專案名稱 : 宅經濟 - 虛擬偶像辨識
# 專案目的 :   
讓使用者透過 AI 模型, 與展覽場地中的人形立牌 或 二次創作的商品, 進行互動
# 技術概要 : 
    1. 前端 : LineBOT, 網頁, APP(Android only)
    2. 後端 : 地端server
    3. AI model : CNN ResNet 101 v2
                  YOLO v8
                  
# AI model 訓練過程
# 第一次模型建立
1. 蒐集資料 : 
    - 使用技術 : OpenCV (使用OpenCV 擷取Youtube上的直播影像)
    - Vtuber : 2 位
2. 模型 : 
    仿製少層的 VGG16
3. 問題點 :  
    - 背景因素影響過大 -> AI model 以背景為判斷基準, 非人物
    - ![Image text](https://github.com/h0806449f/Project_Tibame/blob/main/%E7%AC%AC%E4%B8%80%E6%AC%A1.png)

# 第二次模型建立
1. 優化想法 : 
    - 擷取的圖片, 需要更集中在人物面部特徵
    - 完全去除背景
2. 蒐集資料 : 
    - 使用技術 : OpenCV, SAM (SAM是Meta團隊於 2023.4月 發表的新技術 : https://segment-anything.com/)
    - Vtuber : 6 位
3. 模型 : 
    - VGG16
4. 問題點 : 
    - AI model 訓練完成, 但是, 用於辨識 人形立牌 或 二次創作的商品 時, 效果不好  
    (a. 訓練資料與真實場景, 差異過大)
    - Vtuber數量增加, 特徵容易重複, 需要截取更多特徵  
    (a. 增加模型深度 b. 更換深度更深的模型)

# 第三次模型建立
1. 優化想法 : 
    - 在訓練資料中, 直接加入 人形立牌 或 二次創作的商品 等圖片
    - 使用 ResNet 101 v2 模型
2. 蒐集資料 : 
    - 使用技術 : OpenCV, SAM, 現實照片
    - Vtuber : 6 位
3. 模型 : 
    - ResNet 50 v2
    - ResNet 101 v2

# CNN 成果
第三次模型, 於訓練過程 真實場景 辨識效果良好, 將此模型部署  
為了進一步提升互動性 -> 額外增加另一種模型

# AI model - YOLO v8  
YOLO v8 : https://github.com/ultralytics/ultralytics  
CNN 於辨識單一目標的圖像時, 效果良好。  
但使用者如同時拍攝多的人形立牌, 多個商品, CNN 較不適用 ; 且 CNN 無法用於影像識別。  
所以額外學習 PyTorch 以了解 YOLO v8 如何建立與運作。

1. 蒐集資料 : 直接使用 人形立牌 或 二次創作的商品 等圖片
2. 標記資料 : 
    - API : https://hub.ultralytics.com/
3. 模型成果影片 : 
    - https://www.youtube.com/playlist?list=PLjW4Ibuk2-7BTD_uz0qU2fADAdJYOdUiN

# YOLO 成果  
相較於YOLO v7, YOLO v8 在多目標圖像辨識, 即時影像辨識 都取得較好的成果。  
但受限於專案時間, 沒有部署YOLO系列模型, 僅展示成果影片。  

# 後記
- CNN 模型反應時間, 會影響使用者體驗
- 深度學習領域 PyTorch 使用者較多 -> 加強PyTorch 並練習建立模型
- 多目標任務 -> YOLO 表現良好
- PyTorch 有其他類型的深度學習模型 可額外加強
====================================================================================================  

# Project name : Vtuber Identify AI
# Purpose :   
Allow user interacts with Vtuber's life-sized cardboardcut-out or Vtuber's product.
# Tech : 
    1. front-end : LineBOT, 網頁, APP(Android only)
    2. back-end : local server
    3. AI model : CNN ResNet 101 v2
                  YOLO v8
                  
# AI model training record
# First time
1. collecting data : 
    - tech : OpenCV (collecting images from Vtuber's stream on youtube)
    - Vtuber : 2 
2. model : 
    - VGG16
3. result (problems) :  
    - AI model focus on background too much 
    - ![Image text](https://github.com/h0806449f/Project_Tibame/blob/main/%E7%AC%AC%E4%B8%80%E6%AC%A1.png)

# Second time
1. how to optimize : 
    - OpenCV : when collecting images, focus on Vtuber's facial features (less background)
    - SAM : Image matting (Meta issue this API in 2023.4  https://segment-anything.com/)
2. collecting data : 
    - tech : OpenCV, SAM
    - Vtuber : 6 
3. model : 
    - VGG16
4. result (problems) : 
    - AI model can identify training data ; can not identify Vtuber's life-sized cardboardcut-out or Vtuber's product.  
    (a. huge different between training data and real target)
    - Vtuber increase from 2 to 6, AI need to capture more features
    (a. increase more layer)  
    (b. use another model)

# Third time
1. how to optimize : 
    - training data : put some Vtuber's life-sized cardboardcut-out or Vtuber's product into training data
    - model : ResNet
2. collecting data : 
    - tech : OpenCV, SAM
    - Vtuber : 6
3. model : 
    - ResNet 50 v2
    - ResNet 101 v2

# CNN result
ResNet 101 v2 has better result and accuracy.  
But, if we want to achieve : multiple targets identify or real time identify, we need other model.

# AI model - YOLO v8  
YOLO v8 : https://github.com/ultralytics/ultralytics  
Since YOLO v8 was based on PyTorch, self learn some PyTorch for better understanding YOLO v8.

1. collecting data : Vtuber's life-sized cardboardcut-out or Vtuber's product into training data
2. labeling data : 
    - API : https://hub.ultralytics.com/
3. YOLO v8 result : 
    - https://www.youtube.com/playlist?list=PLjW4Ibuk2-7BTD_uz0qU2fADAdJYOdUiN

# YOLO result  
v8 has better result than v7, but project time limit was close, we did not deploy YOLO.


