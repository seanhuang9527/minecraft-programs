# 水電梯向上

[返回麥塊程式首頁](../../README.md)

讓 Agent 建出向上的水電梯外框與靈魂砂底座。

- 程式概念：迴圈、方向
- 難度：中階
- 啟動指令：在聊天室輸入 `4`
- [教學影片](https://youtu.be/y_kpUSxoNQY)
- [短片示範](https://www.youtube.com/shorts/F-Q0tEFXr6Y)

## 準備

1. 第 1 格放電梯外框方塊，第 2 格放入口或邊框方塊，第 3 格放靈魂砂。
2. 將 Agent 放在電梯底部，面向預定的電梯正面。
3. 程式完成後加水，並用海帶把整條水柱轉成水源。

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
player.on_chat("4", on_on_chat)
```

## 測試與活動

- 進入水柱後應被氣泡向上推升。
- 改變第一個迴圈的次數，製作不同高度的電梯。
- 如果沒有氣泡，檢查每一格是否都是水源，底部是否為靈魂砂。

> 這份程式依既有教學資料整理，尚未在本次發布流程中重新實機驗證。
