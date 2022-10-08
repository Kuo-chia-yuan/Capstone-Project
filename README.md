# Capstone-Project
## 主題
人臉之風格轉換

## 作者
郭珈源 范姜晴 黃竑翔 

## 動機
透過各式風格為user轉換人臉，讓user也能身歷其境，成為動畫、漫畫、電影中的人物

## 目標
產生自然流暢且獨特的風格轉換影片

## 操作方式
- input : 原始影片 
- output : 風格轉換之新影片 

## 過程 
1. 切割 : 將影片一幀一幀的切成多張image(.png檔)
2. 標記 : 利用Facial Landmarks，於image之原始人臉上標記出68個點
3. 校正 : 將image中68個點對齊至正中心，並進行裁切
4. 風格樣本 : 抓取user想要的風格樣本
5. 風格主換 : 利用DualStyleGan將原始人臉進行風格轉換，產生出新的人臉
6. 合成 : 合成多張風格轉換後之image，由此產生新影片

## 遇到困難
合成新影片後，人物頭髮及背景部分，稍顯不連續，使影片效果不佳

## 解決問題
利用Optical Flow一一對應前後image之差別，藉此使image串接時能更順暢

## 運用技術
- Faceial Landmarks 68 points
- DualStyleGan
- Optical Flow
