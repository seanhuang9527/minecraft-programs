# 蓋樓梯往下

[返回程式資料庫](../README.md) · [麥塊程式首頁](../../README.md)

配合階梯方塊方向，使用轉向、後退與下降建造樓梯。

- 分類：基礎與建築
- 程式概念：迴圈
- 難度：初階
- [教學影片](https://www.youtube.com/watch?v=Fyf5om0xSjk)
- 聊天指令：`1`

## 準備

Agent 目前選取欄放至少 10 個階梯方塊，從高處出發，預留向下延伸空間。

## MakeCode Python

```python
def on_on_chat2():
    agent.turn(LEFT_TURN)
    agent.turn(LEFT_TURN)
    agent.move(BACK, 1)
    for index in range(10):
        agent.place(DOWN)
        agent.move(BACK, 1)
        agent.move(DOWN, 1)
player.on_chat("1", on_on_chat2)
```

## 測試與活動

確認兩次左轉後階梯朝向正確；讓玩家從高台沿樓梯走到地面。

## 課程回饋

蓋樓梯往下

程式練習
學習利用機器人實現自動化蓋樓梯往下。透過轉向與後退指令，精確控制具備方向性的方塊擺放。

學習重點

1. 初始轉向邏輯：一開始執行兩次轉向指令，是為了配合階梯方塊的方向性，讓機器人能以正確的朝向往後方建築。
2. 組合位移：交替使用向後與向下指令。
3. 建築邏輯順序：掌握放置、向後、向下的序列。
4. 迴圈應用：利用 for 迴圈控制樓梯往下延伸的長度。

> 依既有教學資料整理；本次尚未重新驗證 MakeCode 積木轉換與 Minecraft Education 實機執行。
