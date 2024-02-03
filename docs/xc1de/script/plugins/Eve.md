# Event Plugin

Event Plugin API.

---

## eve@getFlag

`int eve@getPcHp(int flag, int arrayIndex)`

Gets flag value.

---

## eve@setFlag

`void eve@getPcHp(int flag, int arrayIndex, int value)`

Sets flag value.

---

## eve@getAwardFlagF16

`int eve@getAwardFlagF16(int unk)`

:warning: Dummy function.

---

## eve@addAwardFlagF16

`void eve@addAwardFlagF16(int unk, int unk2 = 0)`

:warning: Dummy function.

---

## eve@setAwardFlagF1

`void eve@setAwardFlagF1(int unk, int unk2 = 0)`

Sets award/achievement. ID matches [MNU_playaward](../../tables/bdat_menu_award.md#mnu_playaward).

!!! warning

    Hardcoded. Only IDs 170 to 174 are accepted (Heart-to-Heart awards).

---

## eve@realtimeEventStart

`void eve@realtimeEventStart(bool unk = false)`

Waits until ready to start a real time event.

---

## eve@realtimeEventPlay

`void eve@realtimeEventPlay(string eventName)`

Starts a new real time event. `eve@realtimeEventStart` should be called first as it ensure that the script has waited for any ongoing event to be done before starting a new one.

---

## eve@realtimeEventEnd

`void eve@realtimeEventEnd()`

Ends the current real time event.

---

## eve@waitRealtimeEvent

`void eve@waitRealtimeEvent()`

Waits until the current real time event ends.

---

## eve@checkEvent

`void eve@checkEvent(bool unk)`

Unknown. Calls `game::ScriptCfs::setContinuousEvent`.

---

## eve@clearEventSkip

`void eve@clearEventSkip(bool unk)`

Unknown. Calls `game::ScriptCfs::setMultiEventSkip`.

---

## eve@isEvent

`bool eve@isEvent()`

Unknown. Returns status of `game::ScriptCfs::isContinuousEvent`.

---

## eve@isTalkEvent

`bool eve@isTalkEvent()`

Unknown. Returns status of `game::ScriptCfs::isFieldTalking`.

---

## eve@isTalkEvent

`bool eve@isTalkEvent()`

:warning: Dummy function. Always returns false.

---

## eve@onTalk

`nil eve@isTalkEvent()`

:warning: Dummy function. Always returns nil.

---

## eve@onTalkEnd

`bool eve@onTalkEnd()`

Unknown. Returns status of `game::ScriptCfs::isFieldTalkEnd`.

---

## eve@fadeIn

`bool eve@fadeIn(int frame = 0, int black = 0)`

Fades in.

---

## eve@fadeOut

`bool eve@fadeOut(int frame = 0, int black = 0)`

Fades out.

---

## eve@fadeWait

`void eve@fadeWait()`

Waits for fade to end.

---

## eve@isFading

`bool eve@isFading()`

Returns whether the screen is currently fading.

---

## eve@isEventFromBGM

`bool eve@isEventFromBGM()`

Unknown. Returns status of `game::ScriptCfs::isContinuousEventFromBGMScript`.

---

## eve@prohibitMenu

`bool eve@prohibitMenu(bool prohibit)`

Sets whether menuing is prohibited.