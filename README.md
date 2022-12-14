# Capstone-Project
## 主題
影片人臉風格轉換研究

## 作者
郭珈源, 范姜晴, 黃竑翔 

## 動機
透過各式風格替user轉換人臉，讓user也能身歷其境，成為動畫、漫畫、電影中的人物

## 目標
研究影片人臉風格轉換，比較目前發表的影像生成、風格轉換技術，研究其中原理、架構並設計實驗，追求高解析度、content image與style image融合恰當、風格控制彈性、影片細節連續的風格轉換

## 操作方式
- input : 原始影片 
- output : 風格轉換之新影片 

## 過程 
1. 切割 : 將影片一幀一幀的切成多張content image(.png檔)
2. 標記 : 利用Facial Landmarks，於image之原始人臉上標記出68個點
3. 校正 : 將image中68個點對齊至正中心，並進行face alignment
4. 風格樣本 : 抓取user想要的style image
5. 風格轉換 : 利用DualStyleGan將原始人臉進行style transfer，產生出新的人臉
6. 合成 : 合成多張風格轉換後之image，由此產生新影片

![dualstylegan1](https://user-images.githubusercontent.com/56677419/202916259-3f48cdca-bad7-4181-bbf8-38dd79451376.jpg)


## 遇到困難
合成新影片後，人物頭髮及背景部分，明顯出現不連續問題，使影片效果不佳。

(左方為input，右上方為校正後的影片，會發現人臉已置中於畫面，右下方為風格轉換後的影片，會發現頭髮及衣服明顯不連續)

https://user-images.githubusercontent.com/56677419/202915859-a43c396a-c7ec-4f29-b4c3-e0ac80fd2f91.mp4

https://user-images.githubusercontent.com/56677419/202916046-c0016383-8ac7-425d-a08f-29fc6690ebd7.mp4

## 解決方法
1. 嘗試利用Optical Flow一一對應前後image之差別，藉此使image串接時能更順暢
2. 透過Vtoonify之encoder，加強對影片中人臉的捕捉，完全改善人臉部連續問題

https://user-images.githubusercontent.com/56677419/202966063-e188f568-11b2-4377-ba3a-2a5d12971189.mp4

https://user-images.githubusercontent.com/56677419/202966196-1da2ef27-4043-4238-9444-2563c2447e9b.mp4

## DualStyleGan與Vtoonify差異
- DualStyleGan接收照片後需重新校正，將人臉置中face alignment才能進行風格轉換，因此影片中頭髮或衣服的晃動會使其看起來不連續，因此只適合做單張照片的人臉風格轉換。
- Vtoonify結合了Image-to-Image Translation-based framework及StyleGAN-based framework各自的優點並改良，捕捉人臉的準確度提高，不需對齊人臉即可進行風格轉換，影片效果大幅進步，因此適合做影片的人臉風格轉換。


## 運用技術
- Faceial Landmarks 68 points
- Image-to-Image Translation
- Pixel2Style2Pixel
- DualStyleGan
- Vtoonify
- StyleGAN

## 參考資料
- [CVPR 2022] Pastiche Master: Exemplar-Based High-Resolution Portrait Style Transfer
- [Yang et al. 2022] VToonify: Controllable High-Resolution Portrait Video Style Transfer
