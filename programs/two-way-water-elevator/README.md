# 雙向水電梯

[返回麥塊程式首頁](../../README.md)

一次建出上升與下降兩座水電梯：靈魂砂負責上升，岩漿塊負責下降。

- 程式概念：迴圈、方向
- 難度：中階
- 啟動指令：在聊天室輸入 `4`
- [教學影片](https://youtu.be/ofTe7Mz7J1g)

## 準備

1. 第 1 格放電梯外框方塊，第 2 格放入口或邊框方塊。
2. 第 3 格放靈魂砂，第 4 格放岩漿塊。
3. 將 Agent 放在第一座電梯底部，面向預定的電梯正面。
4. 程式完成後為兩座電梯加水，並用海帶把水柱轉成水源。

## MakeCode Python

```python
def on_on_chat():
    for index in range(5):
        agent.set_slot(1)
        agent.place(FORWARD)
        agent.place(LEFT)
        agent.place(RIGHT)
        agent.move(BACK, 1)
        agent.place(LEFT)
        agent.place(RIGHT)
        agent.move(FORWARD, 1)
        agent.move(UP, 1)
    for index2 in range(2):
        agent.turn(LEFT_TURN)
    agent.move(DOWN, 1)
    for index3 in range(3):
        agent.place(FORWARD)
        agent.move(DOWN, 1)
    agent.set_slot(2)
    agent.move(FORWARD, 1)
    agent.place(LEFT)
    agent.move(DOWN, 1)
    agent.place(LEFT)
    for index4 in range(2):
        agent.turn(LEFT_TURN)
    agent.move(FORWARD, 1)
    agent.destroy(DOWN)
    agent.set_slot(3)
    agent.place(DOWN)
    agent.move(UP, 5)
    agent.move(FORWARD, 3)
    agent.move(DOWN, 5)
    for index5 in range(2):
        agent.turn(LEFT_TURN)
    for index6 in range(5):
        agent.set_slot(1)
        agent.place(FORWARD)
        agent.place(LEFT)
        agent.place(RIGHT)
        agent.move(BACK, 1)
        agent.place(LEFT)
        agent.place(RIGHT)
        agent.move(FORWARD, 1)
        agent.move(UP, 1)
    for index7 in range(2):
        agent.turn(LEFT_TURN)
    agent.move(DOWN, 1)
    for index8 in range(3):
        agent.place(FORWARD)
        agent.move(DOWN, 1)
    agent.set_slot(2)
    agent.move(FORWARD, 1)
    agent.place(LEFT)
    agent.move(DOWN, 1)
    agent.place(LEFT)
    for index9 in range(2):
        agent.turn(LEFT_TURN)
    agent.move(FORWARD, 1)
    agent.destroy(DOWN)
    agent.set_slot(4)
    agent.place(DOWN)
player.on_chat("4", on_on_chat)
```

## 測試與活動

- 靈魂砂水柱應把玩家往上推，岩漿塊水柱應把玩家往下拉。
- 請學生用不同顏色標示「上樓」與「下樓」入口。
- 如果氣泡沒有貫穿整條水柱，檢查每一格是否都是水源。

> 這份程式依既有教學資料整理，尚未在本次發布流程中重新實機驗證。
