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
    - 使用技術 : OpenCV
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
    - 使用技術 : OpenCV, SAM
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

# 成果
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
