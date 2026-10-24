# Agent 蓋三層烽火台

[返回麥塊程式首頁](../../README.md)

用巢狀迴圈依序鋪出 7 × 7、5 × 5、3 × 3 三層底座，最後放上烽火台。

- 程式概念：巢狀迴圈、方向、庫存管理
- 難度：高階
- 啟動指令：在聊天室輸入 `3`
- [教學影片](https://www.youtube.com/watch?v=XdIebWGLsKk)

## 準備

1. 第 1 格至少放 49 個可用於烽火台底座的礦物方塊。
2. 第 2 格至少放 34 個相同底座方塊，第 3 格放烽火台。
3. 將 Agent 放在最底層一角，周圍保留至少 7 × 7 × 4 空間。

## MakeCode Python

```python
def on_on_chat():
    agent.set_slot(1)
    agent.move(UP, 1)
    for index in range(7):
        for index2 in range(7):
            agent.place(DOWN)
            agent.move(FORWARD, 1)
        agent.move(BACK, 7)
        agent.move(RIGHT, 1)
    agent.move(UP, 1)
    agent.move(LEFT, 6)
    agent.move(FORWARD, 1)
    agent.set_slot(2)
    for index3 in range(5):
        for index4 in range(5):
            agent.place(DOWN)
            agent.move(FORWARD, 1)
        agent.move(BACK, 5)
        agent.move(RIGHT, 1)
    agent.move(UP, 1)
    agent.move(LEFT, 4)
    agent.move(FORWARD, 1)
    for index5 in range(3):
        for index6 in range(3):
            agent.place(DOWN)
            agent.move(FORWARD, 1)
        agent.move(BACK, 3)
        agent.move(RIGHT, 1)
    agent.move(LEFT, 2)
    agent.set_slot(3)
    agent.place(FORWARD)
player.on_chat("3", on_on_chat)
```

## 測試與活動

- 檢查三層底座是否完整，烽火台是否位於最上層中央。
- 計算三層總共需要多少底座方塊，並和準備數量核對。
- 挑戰把三段程式改寫成可重複呼叫的自訂函數。

> 這份程式依既有教學資料整理，尚未在本次發布流程中重新實機驗證。
