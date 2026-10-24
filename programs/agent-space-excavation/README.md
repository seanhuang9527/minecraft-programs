# Agent 5x5x5 空間爆破

[返回程式資料庫](../README.md) · [麥塊程式首頁](../../README.md)

讓 Agent 逐格挖出 5 × 5 × 5 的空間。

- 分類：自動化開採技術
- 程式概念：函數、迴圈、巢狀迴圈
- 難度：高階
- [教學影片](https://www.youtube.com/watch?v=emNFTJZeqeY)
- 聊天指令：`4`

## 準備

將 Agent 放在開採區上方的一角，朝向開採區；每人使用獨立區域。

## MakeCode Python

```python
def on_on_chat():
    for index in range(5):
        for index2 in range(5):
            for index3 in range(5):
                agent.destroy(DOWN)
                agent.move(DOWN, 1)
                agent.collect_all()
            agent.move(UP, 5)
            agent.move(FORWARD, 1)
        agent.move(BACK, 5)
        agent.move(RIGHT, 1)
player.on_chat("4", on_on_chat)
```

## 測試與活動

確認坑洞寬、長、深各 5 格，檢查收集到的方塊；利用挖出的空間建地下基地。

> 依既有教學資料整理；本次尚未重新驗證 MakeCode 積木轉換與 Minecraft Education 實機執行。
