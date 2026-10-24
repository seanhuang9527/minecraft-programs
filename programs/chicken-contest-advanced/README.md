# 變數 抓雞大賽進階版

[返回程式資料庫](../README.md) · [麥塊程式首頁](../../README.md)

在抓雞計分之外，加入牛的扣分、羊的加速與蝙蝠的失明效果。

- 分類：進階
- 程式概念：變數、迴圈、條件判斷、函數
- 難度：高階
- [教學影片](https://www.youtube.com/watch?v=hw1fY27qx2E)
- 聊天指令：`2`、`1`

## 準備

老師在封閉場地準備雞、牛、羊與蝙蝠。輸入 1 歸零，再輸入 2 倒數。

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
        player.tell(mobs.target(LOCAL_PLAYER), "時間：" + str(TIME))
    player.tell(mobs.target(LOCAL_PLAYER), "時間到！")
player.on_chat("2", on_on_chat)


def on_mob_killed_sheep():
    player.tell(mobs.target(LOCAL_PLAYER), "吃到羊毛寶物！超級加速！")
    mobs.apply_effect(SPEED, mobs.target(LOCAL_PLAYER), 5, 5)
mobs.on_mob_killed(SHEEP, on_mob_killed_sheep)


def on_mob_killed_cow():
    global 抓到的雞
    抓到的雞 += -3
    player.tell(mobs.target(LOCAL_PLAYER), "攻擊錯了！扣三分！")
    player.tell(mobs.target(LOCAL_PLAYER), "分數：" + str(抓到的雞))
mobs.on_mob_killed(COW, on_mob_killed_cow)

def on_on_chat2():
    global 抓到的雞
    抓到的雞 = 0
    player.tell(mobs.target(LOCAL_PLAYER), "分數歸零")
player.on_chat("1", on_on_chat2)

def on_mob_killed_chicken():
    global 抓到的雞
    抓到的雞 += 1
    player.tell(mobs.target(LOCAL_PLAYER), "分數：" + str(抓到的雞))
mobs.on_mob_killed(CHICKEN, on_mob_killed_chicken)


def on_mob_killed_bat():
    player.tell(mobs.target(LOCAL_PLAYER), "砍到蝙蝠了！眼前一片黑！")
    mobs.apply_effect(BLINDNESS, mobs.target(LOCAL_PLAYER), 5, 5)
mobs.on_mob_killed(BAT, on_mob_killed_bat)
```

## 測試與活動

依序確認雞加 1、牛扣 3、羊加速、蝙蝠失明；本版時間到仍會觸發事件，老師宣布結束時停止操作並記錄分數。

## 課程回饋

親愛的家長您好：

延續上週的變數觀念，今天的麥塊程式課我們進入了更刺激的「進階擴充」階段！我們不再只是單純地寫出一個計分板，而是帶領孩子們從「程式設計師」的角度出發，思考如何讓一個遊戲變得更好玩、更具挑戰性。

今天我們在原本的「瘋狂抓雞大賽」中，加入了非常受歡迎的「陷阱與寶物機制」。以下是孩子們今天挑戰並掌握的程式核心能力：

- **正負數與條件後果（加扣分邏輯）**：
孩子們學會了設定不同目標的對應數值。打死普通的雞可以得 1 分；但不小心打到陷阱牛，不僅得不到分數，還會啟動程式碼 `+= -3`（加上負三），讓辛苦賺來的分數倒扣！這不僅是程式邏輯，更無形中鍛鍊了孩子們的數學基礎與專注力。
- **呼叫系統函數（賦予狀態效果）**：
孩子們學會使用 `mobs.apply_effect` 這組高階程式積木來改變玩家狀態。他們親手設定出：打死羊可以獲得「超級加速」的正面增益，而誤擊蝙蝠則會受到 5 秒鐘「眼前一片黑（失明）」的負面懲罰。
- **使用者體驗優化（專屬訊息）**：
我們今天還學到了一個高級技巧：讓電腦「只對自己說悄悄話」。透過特定的定位指令，孩子們的倒數計時與分數提示只會顯示在自己的畫面上，學會了如何避免在多人遊戲中「洗版」干擾他人，這是非常棒的數位素養練習！

> 依既有教學資料整理；本次尚未重新驗證 MakeCode 積木轉換與 Minecraft Education 實機執行。
