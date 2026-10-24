# 隨機數：閃動格子

[返回程式資料庫](../README.md) · [麥塊程式首頁](../../README.md)

用隨機數決定安全顏色，讓其餘顏色的羊毛消失。

- 分類：進階
- 程式概念：事件、變數、條件判斷
- 難度：中階

- **適用平台：** Minecraft Education＋Microsoft MakeCode
- **預設完成目標：** 中階版

- **使用方式：** 低、中、高是三份獨立程式，不要疊在同一個專案。三個版本都輸入聊天指令 `1` 執行。
- **學生任務：** 學生只負責隨機數與地板消失程式；場地建立與恢復由老師負責。

## 遊戲功能

程式會把1～4中的隨機結果存進 `safe`，分別代表紅、黃、綠、藍四種安全顏色。高階版宣布安全顏色後等待3秒，再讓其他三種顏色的羊毛地板消失。

## 初階版：設定變數與隨機數

**學習重點：** 認識變數 `safe`，使用 `randint(1, 4)` 讓電腦從1、2、3、4中隨機選出一個數字。

**完成標準：** 輸入 `1` 後，程式設定隨機數並顯示完成訊息。

```python
safe = 0

def on_on_chat():
    global safe
    safe = randint(1, 4)
    player.tell(mobs.target(LOCAL_PLAYER), "隨機數已設定！")
player.on_chat("1", on_on_chat)
```

![程式與遊戲示範](../../batch-m-random-flashing-floor/images/student-beginner.png)

**測試方式：** 連續輸入幾次 `1`，確認每次都會顯示完成訊息。

## 中階版：用條件判斷顯示結果

**學習重點：** 把隨機數連接到四個條件判斷，顯示 `safe` 抽到的數字。

**完成標準：** 輸入 `1` 後，聊天訊息顯示1、2、3或4其中一個結果。

```python
safe = 0

def on_on_chat():
    global safe
    safe = randint(1, 4)
    if safe == 1:
        player.tell(mobs.target(LOCAL_PLAYER), "1")
    if safe == 2:
        player.tell(mobs.target(LOCAL_PLAYER), "2")
    if safe == 3:
        player.tell(mobs.target(LOCAL_PLAYER), "3")
    if safe == 4:
        player.tell(mobs.target(LOCAL_PLAYER), "4")
player.on_chat("1", on_on_chat)
```

![程式與遊戲示範](../../batch-m-random-flashing-floor/images/student-intermediate.png)

**測試方式：** 連續輸入幾次 `1`，確認結果可能出現1、2、3或4。

## 高階版：完整閃動格子

**學習重點：** 使用隨機數選出安全顏色，再用條件判斷讓其他三種顏色消失。

**執行位置：** 站在任一座8×8練習場入口的金塊上。

**完成標準：** 輸入 `1` 後宣布安全顏色；等待3秒後，其他三種顏色的羊毛地板消失。

```python
safe = 0

def on_on_chat():
    global safe
    safe = randint(1, 4)
    if safe == 1:
        player.tell(mobs.target(LOCAL_PLAYER), "安全顏色：紅色！")
    if safe == 2:
        player.tell(mobs.target(LOCAL_PLAYER), "安全顏色：黃色！")
    if safe == 3:
        player.tell(mobs.target(LOCAL_PLAYER), "安全顏色：綠色！")
    if safe == 4:
        player.tell(mobs.target(LOCAL_PLAYER), "安全顏色：藍色！")
    loops.pause(3000)
    if safe != 1:
        blocks.replace(AIR, RED_WOOL, pos(-8, -1, -8), pos(8, -1, 8))
    if safe != 2:
        blocks.replace(AIR, YELLOW_WOOL, pos(-8, -1, -8), pos(8, -1, 8))
    if safe != 3:
        blocks.replace(AIR, GREEN_WOOL, pos(-8, -1, -8), pos(8, -1, 8))
    if safe != 4:
        blocks.replace(AIR, BLUE_WOOL, pos(-8, -1, -8), pos(8, -1, 8))
    player.tell(mobs.target(LOCAL_PLAYER), "地板消失！")
player.on_chat("1", on_on_chat)
```

![程式與遊戲示範](../../batch-m-random-flashing-floor/images/student-advanced-1.png)

![程式與遊戲示範](../../batch-m-random-flashing-floor/images/student-advanced-2.png)

![程式與遊戲示範](../../batch-m-random-flashing-floor/images/student-advanced-3.png)

**測試方式：** 輸入 `1` 後確認只保留宣布的安全顏色，另外三色消失；老師再恢復該座場地供下一次測試。

## `safe` 與座標

- `safe` 是保存隨機結果的變數：1代表紅色、2代表黃色、3代表綠色、4代表藍色。
- `safe != 1` 代表安全數字不是1，因此紅色不是安全顏色，紅色地板要消失。
- `pos()` 是以玩家目前位置為中心的相對座標。
- 玩家站在入口金塊上，地板比玩家腳下低一格，因此Y使用 `-1`。
- X與Z使用 `-8` 到 `8`，讓搜尋範圍足以涵蓋整座8×8練習地板。
- `blocks.replace()` 只替換指定顏色的羊毛，不會讓玻璃牆、金塊或史萊姆消失。

## 程式示範影片

- [示範影片一](https://youtu.be/7jB5HjT0ZA0?si=qXL6wPtXgAY9D9Wn)
- [示範影片二](https://youtu.be/4AYH0QIoIT8?si=pahM1N-g5sxhFThu)

## P.S. 注意

- 貼上程式前，先刪除 MakeCode 編輯器原有內容。
- 初、中、高三個版本是獨立專案，不要放在同一份程式中。
- 高階版必須站在練習場入口金塊上執行，讓相對座標涵蓋正確場地。
- 學生不需要建立或恢復場地；這兩個功能由老師統一執行。
- 個人提示使用 `LOCAL_PLAYER`，不會洗滿全班聊天室。

## 完整教案

[查看半日營教案](../../batch-m-random-flashing-floor/lesson-plan.md)

高階版會修改相對座標範圍內的羊毛；同一場地由一位指定操作者執行，個人練習區保持互不重疊。宣布顏色後請原地等候 3 秒，避免玩家移動改變替換範圍。

> 依既有教學資料整理；本次尚未重新驗證 MakeCode 積木轉換與 Minecraft Education 實機執行。
