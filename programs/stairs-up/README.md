# 蓋樓梯往上

[返回程式資料庫](../README.md) · [麥塊程式首頁](../../README.md)

用向上、放置、向前的順序建造十階樓梯。

- 分類：基礎與建築
- 程式概念：迴圈
- 難度：初階
- [教學影片](https://www.youtube.com/watch?v=gGlp29YvFlU)
- 聊天指令：`1`

## 準備

Agent 目前選取欄放至少 10 個階梯方塊，確認朝向，前上方預留十格。

## MakeCode Python

```python
def on_on_chat():
    for index in range(10):
        agent.move(UP, 1)
        agent.place(DOWN)
        agent.move(FORWARD, 1)
player.on_chat("1", on_on_chat)
```

## 測試與活動

執行後走上樓梯，確認階梯方向可順利通行；調整迴圈次數連接不同高度的平台。

## 課程回饋

蓋樓梯往上

**程式練習**
學習利用機器人實現自動化蓋樓梯往上。

**【學習重點】**

- **組合位移**：交替使用向上（UP）與向前（FORWARD）指令。
- **邏輯順序**：掌握「移動、放置（DOWN）、再移動」的序列。
- **迴圈應用**：利用 `for` 迴圈控制樓梯高度。

> 依既有教學資料整理；本次尚未重新驗證 MakeCode 積木轉換與 Minecraft Education 實機執行。
