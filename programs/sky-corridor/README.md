# 空中通道 巢狀迴圈

[返回程式資料庫](../README.md) · [麥塊程式首頁](../../README.md)

用巢狀迴圈鋪出四格寬、十格長的空中通道。

- 分類：基礎與建築
- 程式概念：迴圈、巢狀迴圈
- 難度：中階
- [教學影片](https://www.youtube.com/watch?v=TTQNbcqo8hs)
- 聊天指令：`2`

## 準備

Agent 目前選取欄放至少 40 個方塊，從通道一角開始，預留 4 × 10 範圍。

## MakeCode Python

```python
def on_on_chat():
    agent.move(UP, 1)
    for index in range(10):
        for index2 in range(4):
            agent.place(DOWN)
            agent.move(RIGHT, 1)
        agent.move(LEFT, 4)
        agent.move(FORWARD, 1)
player.on_chat("2", on_on_chat)
```

## 測試與活動

確認通道沒有缺口，再讓玩家走過；比較改變內、外層迴圈會影響寬度還是長度。

> 依既有教學資料整理；本次尚未重新驗證 MakeCode 積木轉換與 Minecraft Education 實機執行。
