# Capstone-Project
## 主題
人臉之風格轉換
## 目標

## 操作方式
- input : 原始影片 
- output : 風格轉換之新影片 
## 過程 
1. 切割 : 將影片一幀一幀的切成多張image(.png檔)
2. 標記 : 利用Facial Landmarks，於image之原始人臉上標記出68個點
3. 校正 : 將image中68個點對齊至正中心，並進行裁切
4. 風格主換 : 利用DualStyleGan將原始人臉進行風格轉換，產生出新的人臉
5. 合成 : 合成多張風格轉換後之image，由此產生新的影片
## 遇到困難

## 解決問題
