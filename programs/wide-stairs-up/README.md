# 樓梯往上 巢狀迴圈

[返回程式資料庫](../README.md) · [麥塊程式首頁](../../README.md)

用巢狀迴圈建出四格寬、十階高的樓梯。

- 分類：基礎與建築
- 程式概念：迴圈、巢狀迴圈
- 難度：中階
- [教學影片](https://www.youtube.com/watch?v=QnCRodCGamE)
- 聊天指令：`3`

## 準備

Agent 目前選取的物品欄放至少 40 個建築方塊，從樓梯底部一角開始；前方與上方各保留十格。

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
        agent.move(UP, 1)
player.on_chat("3", on_on_chat)
```

## 測試與活動

檢查每階是否四格寬；沿樓梯登頂，改變迴圈次數比較寬度與高度。

> 依既有教學資料整理；本次尚未重新驗證 MakeCode 積木轉換與 Minecraft Education 實機執行。
