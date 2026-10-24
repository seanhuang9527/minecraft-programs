# 挖礦挑戰賽 低階版

[返回程式資料庫](../README.md) · [麥塊程式首頁](../../README.md)

挖掘四種礦物時自動計分，並可隨時查分。

- 分類：進階
- 程式概念：變數、事件、計分系統
- 難度：初階
- [教學影片](https://youtu.be/TB4g48VBF6M?si=GCWYsIjLe4jb_Xjn)
- 聊天指令：`2`、`1`

## 準備

老師準備含煤、鐵、金與鑽石礦的礦坑，所有參賽學生使用同一種類的鎬子。

## MakeCode Python

```python
score = 0


def on_block_broken_iron_ore():
    global score
    score += 2
    player.tell(mobs.target(LOCAL_PLAYER), score)
blocks.on_block_broken(IRON_ORE, on_block_broken_iron_ore)


def on_chat_2():
    player.tell(mobs.target(LOCAL_PLAYER), score)
player.on_chat("2", on_chat_2)


def on_block_broken_coal_ore():
    global score
    score += 1
    player.tell(mobs.target(LOCAL_PLAYER), score)
blocks.on_block_broken(COAL_ORE, on_block_broken_coal_ore)


def on_block_broken_gold_ore():
    global score
    score += 3
    player.tell(mobs.target(LOCAL_PLAYER), score)
blocks.on_block_broken(GOLD_ORE, on_block_broken_gold_ore)


def on_chat_1():
    global score
    score = 0
    gameplay.title(mobs.target(LOCAL_PLAYER), "挖礦挑戰賽", "開始!")
player.on_chat("1", on_chat_1)


def on_block_broken_diamond_ore():
    global score
    score += 5
    player.tell(mobs.target(LOCAL_PLAYER), score)
blocks.on_block_broken(DIAMOND_ORE, on_block_broken_diamond_ore)
```

## 程式截圖

![既有教學程式截圖](../../batch-r-mining-challenge/images/low-score-blocks.png)

## 測試與活動

輸入 1 歸零，分別挖四種礦物，應共得 11 分；輸入 2 查分。老師統一計時，總分最高者獲勝。

> 依既有教學資料整理；本次尚未重新驗證 MakeCode 積木轉換與 Minecraft Education 實機執行。

原教學資料記錄此版本已通過實機與多人計分隔離測試；發布前未另行重測。
