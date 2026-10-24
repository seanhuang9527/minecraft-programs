# 變數 抓雞大賽

[返回程式資料庫](../README.md) · [麥塊程式首頁](../../README.md)

用變數記錄抓雞分數，並顯示 30 秒倒數。

- 分類：進階
- 程式概念：變數、迴圈、條件判斷
- 難度：高階
- [教學影片](https://www.youtube.com/watch?v=qrPjrtQVTF0)
- 聊天指令：`2`、`1`

## 準備

老師準備圍欄與雞，學生建立自己的專案；先輸入 1 歸零，再輸入 2 倒數。

## MakeCode Python

```python
TIME = 0
抓到的雞 = 0

def on_on_chat():
    global TIME
    TIME = 30
    player.tell(mobs.target(LOCAL_PLAYER), "開始！")
    for index in range(30):
        TIME += -1
        loops.pause(1000)
        player.tell(mobs.target(LOCAL_PLAYER), "Time: " + ("" + str(TIME)))
    player.tell(mobs.target(LOCAL_PLAYER), "時間到！")
player.on_chat("2", on_on_chat)

def on_on_chat2():
    global 抓到的雞
    抓到的雞 = 0
    player.tell(mobs.target(LOCAL_PLAYER), "分數歸零")
player.on_chat("1", on_on_chat2)

def on_mob_killed_chicken():
    global 抓到的雞
    抓到的雞 += 1
    player.tell(mobs.target(LOCAL_PLAYER), "分數：" + ("" + str(抓到的雞)))
mobs.on_mob_killed(CHICKEN, on_mob_killed_chicken)
```

## 測試與活動

抓一隻雞確認加 1 分，確認倒數結束訊息。本版時間到仍會計分，老師宣布結束後立即停止操作，以當時分數比較。

## 課程回饋

親愛的家長您好：



今天的主題是（「變數（Variables）」



「變數」聽起來是個生硬的工程名詞，但我們透過一場「麥塊抓雞大賽」，讓孩子們在遊戲中自然而然地吸收了這個核心邏輯。

今天，孩子們化身為遊戲設計師，親手寫出了專屬的「全自動計分板」與「倒數計時器」。

以下是孩子們今天掌握的三大程式能力：

把變數具象化為「魔法箱」：孩子們學會了在系統中建立名為「分數」與「時間」的專屬箱子，用來儲存與追蹤遊戲中的數據。

精準區分「設為」與「改變）」：

他們學會遊戲開始前，必須先將分數「設為 0」（清空箱子）。

每成功抓到一隻雞，程式就會讓分數「改變 +1」；同時讓倒數時間「改變 -1」。

控制電腦的運算節奏：電腦的計算速度比閃電還快，孩子們今天學會使用 『暫停1000毫秒』指令，精準要求電腦「暫停 1 秒鐘（1000毫秒）」。

這個步驟不僅讓倒數計時器完美運作，更深刻鍛鍊了孩子們控制程式流程的邏輯思維。

> 依既有教學資料整理；本次尚未重新驗證 MakeCode 積木轉換與 Minecraft Education 實機執行。
