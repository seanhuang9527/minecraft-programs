# 狗狗的家

[返回程式資料庫](../README.md) · [麥塊程式首頁](../../README.md)

讓 Agent 繞行蓋牆，再鋪設屋頂。

- 分類：基礎與建築
- 程式概念：迴圈
- 難度：初階
- [教學影片](https://www.youtube.com/watch?v=xEo8KkJk6AY)
- 聊天指令：`2`、`1`、`4`、`3`

## 準備

第 1 格準備牆面方塊，第 2 格放至少 49 個屋頂方塊。牆面放置次數超過單格 64 個容量，先以小規模測試並安排補料，確認選取欄位不會用盡。

## MakeCode Python

```python
def on_on_chat():
    agent.turn(LEFT_TURN)
player.on_chat("2", on_on_chat)

def on_on_chat2():
    agent.teleport_to_player()
player.on_chat("1", on_on_chat2)

def on_on_chat3():
    agent.set_slot(1)
    for index in range(4):
        for index2 in range(4):
            for index3 in range(6):
                agent.move(FORWARD, 1)
                agent.place(BACK)
            agent.turn(RIGHT_TURN)
        agent.move(BACK, 1)
        agent.place(FORWARD)
        agent.move(UP, 1)
        agent.move(FORWARD, 1)
        agent.move(LEFT, 1)
    agent.move(UP, 1)
    agent.move(BACK, 1)
    agent.set_slot(2)
    for index4 in range(7):
        for index5 in range(7):
            agent.move(FORWARD, 1)
            agent.place(DOWN)
        agent.move(BACK, 7)
        agent.move(RIGHT, 1)
player.on_chat("4", on_on_chat3)

def on_on_chat4():
    agent.move(FORWARD, 1)
player.on_chat("3", on_on_chat4)
```

## 測試與活動

輸入 1 召回、2 左轉、3 前進調整起點，4 建造。確認牆面和屋頂完整後，手動開門窗，帶狼進屋；缺料時先補料再測試。

> 依既有教學資料整理；本次尚未重新驗證 MakeCode 積木轉換與 Minecraft Education 實機執行。
