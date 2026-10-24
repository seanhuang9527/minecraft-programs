# 挖礦挑戰賽 高階版

[返回程式資料庫](../README.md) · [麥塊程式首頁](../../README.md)

在 60 秒內採礦計分，時間到後停止加分。

- 分類：進階
- 程式概念：變數、事件、迴圈、條件判斷、計分系統
- 難度：高階
- [教學影片](https://youtu.be/0JJ9qUJ2ZBM?si=5cEJBSfjcoxv27sN)
- 聊天指令：`2`、`1`

## 準備

老師準備礦坑並確認遊戲指令權限；所有參賽學生使用同一種類的鎬子。

## MakeCode Python

```python
time = 0
score = 0


def on_block_broken_iron_ore():
    global score
    if time > 0:
        score += 2
blocks.on_block_broken(IRON_ORE, on_block_broken_iron_ore)


def on_chat_2():
    player.execute("title @s actionbar 最後總分:" + str(score))
player.on_chat("2", on_chat_2)


def on_block_broken_coal_ore():
    global score
    if time > 0:
        score += 1
blocks.on_block_broken(COAL_ORE, on_block_broken_coal_ore)


def on_block_broken_gold_ore():
    global score
    if time > 0:
        score += 3
blocks.on_block_broken(GOLD_ORE, on_block_broken_gold_ore)


def on_chat_1():
    global time, score
    time = 60
    score = 0
    gameplay.title(mobs.target(LOCAL_PLAYER), "挖礦挑戰賽", "開始!")

    while time > 0:
        player.execute("title @s actionbar 時間:" + str(time) + " 分數:" + str(score))
        loops.pause(1000)
        time += 0 - 1

    player.execute("title @s actionbar 時間到 分數:" + str(score))
player.on_chat("1", on_chat_1)


def on_block_broken_diamond_ore():
    global score
    if time > 0:
        score += 5
blocks.on_block_broken(DIAMOND_ORE, on_block_broken_diamond_ore)
```

## 程式截圖

![既有教學程式截圖](../../batch-r-mining-challenge/images/high-main-timer-blocks.png)

![既有教學程式截圖](../../batch-r-mining-challenge/images/high-score-events-blocks.png)

## 測試與活動

輸入 1 開始；確認倒數與分數更新，時間到後挖礦不再加分；輸入 2 查最後總分。總分最高者獲勝。

> 依既有教學資料整理；本次尚未重新驗證 MakeCode 積木轉換與 Minecraft Education 實機執行。

原教學資料記錄此版本已通過實機與多人計分隔離測試；發布前未另行重測。
