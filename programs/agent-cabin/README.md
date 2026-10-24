# Agent 蓋小木屋

[返回程式資料庫](../README.md) · [麥塊程式首頁](../../README.md)

用自訂函數讓 Agent 重複蓋牆，完成四層高的小木屋外牆。

- 程式概念：函數、迴圈、方向
- 難度：中階
- 啟動指令：在聊天室輸入 `1`
- [教學影片](https://www.youtube.com/watch?v=yAdJfSHwuIU)

## 準備

1. 第 1 格放 64 個橡木材。
2. 將 Agent 放在預定牆角，周圍保留至少 6 × 6 × 5 空間。
3. 程式先完成外牆；門、窗與屋頂由玩家在活動中自行設計。

## MakeCode Python

```python
def build_wall():
    for index in range(4):
        agent.place(DOWN)
        agent.move(FORWARD, 1)

def build_layer():
    build_wall()
    agent.turn(RIGHT_TURN)
    build_wall()
    agent.turn(RIGHT_TURN)
    build_wall()
    agent.turn(RIGHT_TURN)
    build_wall()
    agent.turn(RIGHT_TURN)

def on_on_chat():
    agent.set_slot(1)
    agent.move(UP, 1)
    build_layer()
    agent.move(UP, 1)
    build_layer()
    agent.move(UP, 1)
    build_layer()
    agent.move(UP, 1)
    build_layer()
player.on_chat("1", on_on_chat)
```

## 測試與活動

- 確認四面牆接合，Agent 每完成一層都回到原本朝向。
- 手動開出門窗，再設計階梯屋頂或平屋頂。
- 進階挑戰：把四次 `build_layer()` 改成迴圈。

> 公開版已修正原資料的事件語法、方向常數與超出 Agent 單格容量的材料數量；尚未在本次發布流程中重新實機驗證。
