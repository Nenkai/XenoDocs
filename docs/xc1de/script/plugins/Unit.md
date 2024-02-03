# Unit Plugin

Battle Unit Plugin API.

---

## unit@getPcHp

`int unit@getPcHp(int pc)`

:warning: Dummy function.

---

## unit@getPcHpRate

`int unit@getPcHpRate(int pc)`

:warning: Dummy function.

---

## unit@getEneHp

`int unit@getEneHp(int eneId)`

Gets the health of an enemy.

---

## unit@getEneHp

`int unit@getEneHp(int eneId)`

Gets the health of an enemy. Calls `game::ScriptUnit::getEnemyHp`.

---

## unit@getEneHpRate

`int unit@getEneHpRate(int eneId)`

Gets the health rate (percentage?) of an enemy. Calls `game::ScriptUnit::getEnemyHpRate`.

---

## unit@setPcBtlState

`void unit@setPcBtlState(int bdid, int state, int time = 0, int val1 = 0, int val2 = 0, int interval = 0)`

Sets the battle state of a playable character. Calls `game::ScriptUnit::setPcBtlState`.

---

## unit@existPcBtlState

`bool unit@existPcBtlState(int bdid, int state)`

Checks if the battle state of a player character exists. Calls `game::ScriptUnit::existPcBtlState`.

---

## unit@clearPcBtlState

`void unit@clearPcBtlState(int bdid, int state)`

:warning: Dummy function.

---

## unit@setEneBtlState

`void unit@setEneBtlState(int bdid, int state, int time = 0, int val1 = 0, int val2 = 0, int interval = 0)`

Sets the battle state of an enemy. Calls `game::ScriptUnit::setEneBtlState`.

---

## unit@clearEneBtlState

`void unit@clearEneBtlState(int bdid, int state)`

Clears the battle state of a battle enemy. Calls `game::ScriptUnit::clearEneBtlState`.

---

## unit@onPcArtsAttack

`int unit@onPcArtsAttack(int bdid, int state)`

:warning: Dummy function.

---

## unit@onEneArtsAttack

`bool unit@onEneArtsAttack(int bdid, int state, int unused = 0)`

Returns whether an enemy art attack is enabled. Calls `game::ScriptUnit::isOnEneArtsAttack`.

---

## unit@synchro

`void unit@synchro(int id1, int id2)`

Unknown. Calls `game::ScriptUnit::setSynchro`.

---

## unit@learnArts

`void unit@learnArts(int pc_arts_id)`

Learns an art. Calls `game::ScriptUnit::learnArts`.

!!! tip

    Art ID is from [pc_arts](../../tables/bdat_common.md#pc_arts).
    
---

## unit@getPcHandle

`int unit@getPcHandle()`

Unknown. Gets party handle. Calls `game::ScriptUnit::getPartyHandle`.
 
---