# 挖沙子機器人

[返回程式資料庫](../README.md) · [麥塊程式首頁](../../README.md)

讓 Agent 下挖後清除四周沙子並收集。

- 分類：自動化開採技術
- 程式概念：迴圈
- 難度：初階
- [教學影片](https://youtu.be/N1fw4wxvzAA?list=PL3600H0DVFhSzXec8B_GPnGsuRxV6wqmv)
- 聊天指令：`3`

## 準備

在至少三格深的沙地上放置 Agent，確認物品欄有空位。

## MakeCode Python

```python
def on_on_chat():
    for index in range(3):
        agent.destroy(DOWN)
        agent.move(DOWN, 1)
    for index2 in range(3):
        agent.destroy(FORWARD)
        agent.destroy(BACK)
        agent.destroy(LEFT)
        agent.destroy(RIGHT)
        agent.collect_all()
player.on_chat("3", on_on_chat)
```

## 程式截圖

![既有教學程式截圖](../../batch-e-desert-wilderness/images/sand-miner-basic-01.png)

![既有教學程式截圖](../../batch-e-desert-wilderness/images/sand-miner-basic-02.png)

## 測試與活動

檢查 Agent 物品欄是否取得沙子；將沙子燒成玻璃，建造玻璃窗。

## 課程回饋

親愛的家長您好 今天的主題是挖沙子機器人

首先進入麥塊世界，孩子們將使用指令編寫程式
控制機器人來自動收集沙子方塊
指令內容包含：
破壞前、破壞後、破壞左、破壞右、破壞下
移動下、移動上
迴圈 等程式邏輯

透過這些程式碼
孩子們能讓機器人自動破壞周圍沙子方塊
並將收集到的材料帶回「家中」
最後用玻璃方塊建造空中的橋樑！

所有孩子都表現得非常棒
順利完成了今天的挑戰任務！

> 依既有教學資料整理；本次尚未重新驗證 MakeCode 積木轉換與 Minecraft Education 實機執行。
