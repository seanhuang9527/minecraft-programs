# 挖沙子機器人進階版

[返回程式資料庫](../README.md) · [麥塊程式首頁](../../README.md)

重複挖沙流程並移動到下一個位置，擴大採集範圍。

- 分類：自動化開採技術
- 程式概念：函數、迴圈
- 難度：中階
- [教學影片](https://www.youtube.com/watch?v=N1fw4wxvzAA)
- 聊天指令：`3`

## 準備

準備連續的沙地，Agent 從沙地上方開始，前方至少保留六格採集範圍。

## MakeCode Python

```python
def on_on_chat():
    for index in range(2):
        for index2 in range(3):
            agent.destroy(DOWN)
            agent.move(DOWN, 1)
        for index3 in range(3):
            agent.destroy(FORWARD)
            agent.destroy(BACK)
            agent.destroy(LEFT)
            agent.destroy(RIGHT)
            agent.collect_all()
        agent.move(UP, 3)
        agent.move(FORWARD, 3)
player.on_chat("3", on_on_chat)
```

## 程式截圖

![既有教學程式截圖](../../batch-e-desert-wilderness/images/sand-miner-advanced.png)

## 測試與活動

觀察兩輪採集後 Agent 是否回到地表；用採集的沙子製作染色玻璃。

## 課程回饋

親愛的家長您好
今天的麥塊主題是挖沙子機器人 進階版

進入麥塊世界後，孩子們將使用指令編寫程式
控制機器人來自動收集沙子方塊

指令內容包含：
破壞前、破壞後、破壞左、破壞右、破壞下
移動下、移動上
迴圈 等程式邏輯完成基礎挖沙機器人

之後利用巢狀迴圈的概念
讓小朋友思考
如何在一條路上執行挖沙機器人
並擴大挖沙的範圍

透過這些程式碼
孩子們能讓機器人自動破壞周圍沙子方塊
並將收集到的材料帶回家中
最後用熔爐 做成玻璃
之後收集染料 製作成顏色不同的玻璃

所有孩子都表現得非常棒
順利完成了今天的挑戰任務！

> 依既有教學資料整理；本次尚未重新驗證 MakeCode 積木轉換與 Minecraft Education 實機執行。
