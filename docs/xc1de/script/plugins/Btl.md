# Btl (Battle) Plugin

Battle Plugin API.

---

## btl@startObserve

`void btl@startObserve()`

Unknown. Calls `game@ScriptBtl@setMonitorEnemyKill(true)` internally.

---

## btl@endObserve

`void btl@endObserve()`

Unknown. Calls `game@ScriptBtl@setMonitorEnemyKill(false)` internally.

---

## btl@defeatingCount

`int btl@defeatingCount(int enemyId)`

Returns the number of defeated specified enemy.

---

## btl@isEnd

`bool btl@isEnd()`

Returns whether the battle has ended.

---

## btl@end

`bool btl@end()`

Does nothing. Empty function.

---

## btl@attack

`bool btl@attack(bool flag = true)`

Calls `game@ScriptBtl@attack` which does nothing. Empty function.

---

---

## btl@attackEne

`bool btl@attackEne(bool flag = true)`

Does nothing. Empty function.

---

## btl@selectTgt

`bool btl@selectTgt(oc targetObject = nil)`

Selects battle target. Calls `game@ScriptBtl@startBattle` (with a specified target if provided - might not be used).

---

## btl@vision

`void btl@vision(bool unk = false)`

Does nothing. Empty function.

---

## btl@voiceEvent

`void btl@voiceEvent(bool unk = false)`

Does nothing. Empty function.

---

## btl@isVoiceEvent

`bool btl@isVoiceEvent()`

Dummy function.

---

## btl@unlockMonadoArts

`void btl@unlockMonadoArts()`

Unlocks monado arts & allows upgrading to advanced levels. Calls `game@ScriptCfs@unlockMonadoArts`.

---

## btl@setTensionLv

`void btl@setTensionLv(int level = 0)`

Sets the battle tension level. Calls `game@ScriptBtl@setTensionLv`.

---


## btl@setTensionLvOA

`void btl@setTensionLvOA(int level = 0)`

Sets the battle tension level 'only arrive'. Calls `game@ScriptBtl@setTensionLvOnlyArrive`.

---

## btl@getTensionLv

`int btl@getTensionLv()`

Gets the battle tension. Calls `game@ScriptBtl@getTensionLv`.

---

## btl@setTP

`void btl@setTP(int tp = 100, int pcIdMaybe = 0)`

Sets TP. Calls `game@ScriptBtl@setTP`.

---

## btl@breakVision

`void btl@breakVision(int unk = 0)`

Dummy function.

---

## btl@setPTG

`void btl@setPTG(int ptyGauge)`

Sets Party Gauge. Calls `game@ScriptBtl@setPartyGauge`.

---

## btl@getPTG

`int btl@getPTG()`

Gets Party Gauge. Calls `game@ScriptBtl@getPartyGauge`.

---

## btl@isPcExtinction

`bool btl@isPcExtinction()`

Unknown (return death status?). Calls `game@ScriptBtl@isPcExtinction`.

---

## btl@test

`bool btl@test()`

Dummy function.
