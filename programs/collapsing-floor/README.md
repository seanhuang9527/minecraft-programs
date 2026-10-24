# 條件判斷：方塊崩落大逃亡

[返回程式資料庫](../README.md) · [麥塊程式首頁](../../README.md)

利用走路事件讓指定羊毛地板消失。

- 分類：進階
- 程式概念：事件、條件判斷
- 難度：中階

- **適用平台：** Minecraft Education＋Microsoft MakeCode
- **預設完成目標：** 中階版

- **使用方式：** 低、中、高是三份獨立程式，每位學生只建立符合自己程度的一份。
- **座標設定：** 三份程式均使用 `pos(0, -1, -1)`，代表玩家位置下方 1 格、世界 Z 軸負方向 1 格。

## 遊戲功能

學生在三層羊毛平台上移動，程式會讓走過的方塊消失。掉到第二層或第三層仍可繼續，掉出第三層才淘汰；最後留在平台上的玩家獲勝。

## 低階版：方塊取代

**學習重點：** 玩家走路事件、相對座標、方塊取代。

**完成標準：** 玩家走路時，後下方一格的白色羊毛消失；其他方塊不被破壞。

```python
def on_travelled_walk():
    blocks.replace(
        AIR,
        WOOL,
        pos(0, -1, -1),
        pos(0, -1, -1)
    )
player.on_travelled(WALK, on_travelled_walk)
```

![程式與遊戲示範](../../batch-s-collapsing-floor/images/low-program.png)

**測試方式：** 沿主要 Z 軸方向走過白色羊毛，確認身後形成缺口。

## 中階版：條件判斷

**學習重點：** 使用「如果」判斷指定位置是不是白色羊毛。

**完成標準：** 指定位置是白色羊毛時才移除，踩到黃色羊毛或石頭不執行移除。

```python
def on_travelled_walk():
    if blocks.test_for_block(WOOL, pos(0, -1, -1)):
        blocks.place(AIR, pos(0, -1, -1))
player.on_travelled(WALK, on_travelled_walk)
```

![程式與遊戲示範](../../batch-s-collapsing-floor/images/medium-program.png)

**測試方式：** 分別走過白色羊毛、黃色羊毛及石頭，確認只有白色羊毛消失。

## 高階版：跳躍與加速

**學習重點：** 第二個條件判斷、跳躍提升與速度效果。

**完成標準：** 走路時持續獲得跳躍提升；白色羊毛消失；黃色羊毛提供 3 秒速度效果後也消失。

```python
def on_travelled_walk():
    mobs.apply_effect(
        JUMP_BOOST,
        mobs.target(LOCAL_PLAYER),
        3,
        2
    )

    if blocks.test_for_block(WOOL, pos(0, -1, -1)):
        blocks.place(AIR, pos(0, -1, -1))

    if blocks.test_for_block(YELLOW_WOOL, pos(0, -1, -1)):
        mobs.apply_effect(
            SPEED,
            mobs.target(LOCAL_PLAYER),
            3,
            1
        )
        blocks.place(AIR, pos(0, -1, -1))

player.on_travelled(WALK, on_travelled_walk)
```

![程式與遊戲示範](../../batch-s-collapsing-floor/images/high-program.png)

**測試方式：** 確認跳躍提升能跨越一格缺口；踩黃色羊毛會加速且方塊消失；效果只套用在本機玩家。

## 遊戲畫面

![程式與遊戲示範](../../batch-s-collapsing-floor/images/gameplay.png)

## 程式示範影片

[56.條件判斷：方塊崩壞大逃亡](https://youtu.be/QOAgEzOvPzw?si=ob1MxCdVxPLJyXGm)

## P.S. 注意

- 貼上程式前，先刪除 MakeCode 編輯器原有內容。
- `pos(0, -1, -1)` 的 Z 軸方向不會跟著玩家面向旋轉，正式活動要依場地主要移動方向安排起點。
- 高階跳躍效果較強，使用前確認玩家不會跳出場地玻璃牆。
- 多人世界中，每位學生只執行自己的版本；速度與跳躍效果使用 `LOCAL_PLAYER`，不會套用到其他玩家。

## 完整教案

[查看半日營教案](../../batch-s-collapsing-floor/lesson-plan.md)

> 依既有教學資料整理；本次尚未重新驗證 MakeCode 積木轉換與 Minecraft Education 實機執行。
