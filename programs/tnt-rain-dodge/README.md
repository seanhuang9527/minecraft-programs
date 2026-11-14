# 天降 TNT 躲避遊戲

[返回程式資料庫](../README.md) · [麥塊程式首頁](../../README.md)

建立開放式基岩競技場，讓已點燃的 TNT 隨關卡增加並從玩家上方落下。

- 分類：進階
- 程式概念：事件、變數、迴圈、巢狀迴圈、關卡設計
- 難度：高階
- 聊天指令：`1`、`2`
- 適用方式：教師示範、單人世界，或彼此隔離的小組測試區

## 遊戲功能

輸入 `1` 會在玩家周圍建立中空的基岩競技場，並清除最上方方塊，形成開放式屋頂。

輸入 `2` 會開始第 0～50 關的 TNT 躲避挑戰。外層迴圈使用 `index` 控制關卡，內層迴圈依照目前的 `index` 數值生成相同數量的 TNT；玩家每關獲得 10 秒速度效果，5 秒後進入下一關。

## 學習重點

- **事件：** 使用聊天指令啟動場地建立與正式遊戲。
- **變數：** `index` 同時控制畫面上的關卡名稱與 TNT 數量。
- **迴圈：** 重複執行每一關的標題、效果、生成與等待流程。
- **巢狀迴圈：** 外層控制關卡，內層控制該關生成的 TNT 數量。
- **關卡設計：** 利用等待時間、速度效果與逐關增加的 TNT 製作難度曲線。
- **隨機座標：** 讓 TNT 在玩家上方的指定範圍內隨機生成。

## 準備

1. 使用空曠且不需保留建築的測試區。
2. 將每位學生或每組的場地分開，避免爆炸破壞其他人的作品。
3. 正式多人課堂由世界主持人統一設定難度與遊戲模式。
4. 先把關卡改成 `range(1, 6)` 或 `range(1, 11)` 進行效能測試。
5. 貼上程式前，先刪除 MakeCode 編輯器原有內容，並切換至積木模式檢查是否完整轉換。

## MakeCode Python

```python
def on_on_chat():
    gameplay.set_game_mode(SURVIVAL, mobs.target(LOCAL_PLAYER))
    gameplay.set_difficulty(EASY)
    for index in range(51):
        gameplay.title(mobs.target(LOCAL_PLAYER), "第" + str(index) + "關", "")
        mobs.apply_effect(SPEED, mobs.target(LOCAL_PLAYER), 10, 1)
        for index2 in range(index):
            mobs.spawn(PRIMED_TNT, randpos(pos(-20, 10, -20), pos(20, 10, 20)))
        loops.pause(5000)
player.on_chat("2", on_on_chat)

def on_on_chat2():
    player.say("生成基岩場地")
    blocks.fill(BEDROCK,
        pos(-20, -1, -20),
        pos(20, 10, 20),
        FillOperation.HOLLOW)
    blocks.fill(AIR,
        pos(-20, 10, -20),
        pos(20, 10, 20),
        FillOperation.HOLLOW)
player.on_chat("1", on_on_chat2)
```

## 操作與測試

1. 老師站在空曠測試區中央輸入 `1`。
2. 確認基岩地板與四面牆已生成，而且屋頂保持開放。
3. 玩家進入競技場並站在中央，再輸入 `2`。
4. 確認關卡標題依序增加，本機玩家獲得速度效果。
5. 確認每關生成的 TNT 數量與 `index` 相同，關卡之間等待 5 秒。
6. 玩家死亡、完成所有關卡，或老師停止程式時結束。

## 效能與多人安全

- `range(51)` 會執行第 0～50 關，共 51 關；第 0 關不會生成 TNT。
- 全部關卡合計生成 1275 顆 TNT，單是等待時間就有 255 秒；後期每 5 秒會生成 40～50 顆 TNT，可能造成延遲或當機。
- `gameplay.set_difficulty(EASY)` 會改變全班共用世界的難度，正式多人課堂應移除這行，改由老師或世界主持人統一設定。
- `player.say("生成基岩場地")` 會讓全班看到訊息；個人提示可改用 `player.tell(mobs.target(LOCAL_PLAYER), "生成基岩場地")`。
- 場地與 TNT 使用相對座標。場地以輸入 `1` 時的位置為中心；TNT 以執行當下的玩家位置為中心，玩家移動後可能生成到競技場外。
- 緊急清除已點燃 TNT：`/kill @e[type=minecraft:tnt]`。

> 依本次提供的程式整理；尚未重新驗證 MakeCode 積木轉換與 Minecraft Education 實機執行。
