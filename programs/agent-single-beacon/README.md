# Agent 蓋單層烽火台

[返回程式資料庫](../README.md) · [麥塊程式首頁](../../README.md)

讓 Agent 鋪出 3 × 3 底座，並在中央放置烽火台。

- 程式概念：迴圈、平面填充
- 難度：中階
- 啟動指令：在聊天室輸入 `3`
- [教學影片](https://www.youtube.com/watch?v=Z900N44vIXw)

## 準備

1. 第 1 格放鐵、金、鑽石、綠寶石或獄髓方塊，第 2 格放烽火台。
2. 至少準備 9 個底座方塊與 1 個烽火台。
3. 將 Agent 放在底座一角的上方，周圍保留 3 × 3 空間。

## MakeCode Python

```python
def on_on_chat():
    agent.move(UP, 1)
    for index in range(3):
        agent.set_slot(1)
        agent.place(DOWN)
        agent.move(FORWARD, 1)
    agent.move(BACK, 3)
    agent.move(RIGHT, 1)
    for index2 in range(3):
        agent.set_slot(1)
        agent.place(DOWN)
        agent.move(FORWARD, 1)
    agent.move(BACK, 3)
    agent.move(RIGHT, 1)
    for index3 in range(3):
        agent.set_slot(1)
        agent.place(DOWN)
        agent.move(FORWARD, 1)
    agent.move(BACK, 3)
    agent.move(LEFT, 1)
    agent.move(FORWARD, 1)
    agent.set_slot(2)
    agent.place(DOWN)
player.on_chat("3", on_on_chat)
```

## 測試與活動

- 確認底座是完整的 3 × 3，烽火台位於中央上方。
- 把三段相似的鋪設程式改寫成巢狀迴圈。

> 公開版已把原資料中的重複巢狀迴圈整理為三段清楚的列填充程式；尚未在本次發布流程中重新實機驗證。
