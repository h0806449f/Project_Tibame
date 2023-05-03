測試模型一
1. 使用 VGG16 測試模型能否分辨兩位不同Vtuber
2. 資料來源 : Youtube -> OpenCV
3. 圖片大小 : 500 * 500
4. 小結 :   
    - 背景因素影響過大 -> 模型將白色背景當作 A_Vtuber 的特徵 / 將黑色背景當作 B_Vtuber 的特徵
    - Vtuber 在 500 * 500 的圖片中 僅占圖片區域 1/4 -> 可縮小圖片

![Image text](https://github.com/h0806449f/Project_Tibame/blob/main/%E7%AC%AC%E4%B8%80%E6%AC%A1.png)
