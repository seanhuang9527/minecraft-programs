# 炸彈超人

[返回程式資料庫](../README.md) · [麥塊程式首頁](../../README.md)

用 Agent 鋪設兩層平台，搭配基岩、紅石火把與 TNT 設計遊戲。

- 分類：基礎與建築
- 程式概念：迴圈、巢狀迴圈
- 難度：初階
- [教學影片](https://youtu.be/ZXCQpmKxAsM)
- 聊天指令：`2`、`1`、`3`

## 準備

第 1 格放至少 20 個基岩，第 2 格放至少 20 個 TNT。老師安排獨立測試場並設定爆炸規則；紅石火把由老師或玩家手動放置。

## MakeCode Python

```python
def on_on_chat():
    agent.set_slot(1)
    agent.move(UP, 1)
    for index in range(4):
        for index2 in range(5):
            agent.place(DOWN)
            agent.move(FORWARD, 1)
        agent.move(BACK, 5)
        agent.move(RIGHT, 1)
player.on_chat("2", on_on_chat)

def on_on_chat2():
    agent.teleport_to_player()
player.on_chat("1", on_on_chat2)

def on_on_chat3():
    agent.set_slot(2)
    agent.move(UP, 2)
    for index3 in range(4):
        for index4 in range(5):
            agent.place(DOWN)
            agent.move(FORWARD, 1)
        agent.move(BACK, 5)
        agent.move(RIGHT, 1)
player.on_chat("3", on_on_chat3)
```

## 測試與活動

在固定起點輸入 1 召回、2 鋪基岩。回到同一起點再次輸入 1，再輸入 3 鋪 TNT。確認兩層對齊後，利用紅石火把測試爆炸與基岩保護效果。

> 依既有教學資料整理；本次尚未重新驗證 MakeCode 積木轉換與 Minecraft Education 實機執行。
