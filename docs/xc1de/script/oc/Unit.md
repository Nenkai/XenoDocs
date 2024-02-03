# Unit OC/Object

Represents a battle unit object.

---

## :material-new-box: Constructor

`oc unit(string bdat, int id = 0, int unk = 0)`

Gets a bdat unit.

Valid names:

* `FLD_npclist` or `npc`
* `BTL_enelist` or `ene`
* `BTL_pclist` or `pc`
* `player`

---

## Attributes

### :fontawesome-solid-wrench: x

`float unit.x`

X position.

---

### :fontawesome-solid-wrench: y

`float unit.y`

Y position.

---

### :fontawesome-solid-wrench: y

`float unit.z`

Z position.

---

### :fontawesome-solid-wrench: dir

`float unit.dir`

Direction.

---

### :fontawesome-solid-wrench: name

`string unit.name`

Unit name.

---

### :fontawesome-solid-wrench: bdid

`string unit.bdid`

Unknown. Getter only.

---

### :fontawesome-solid-wrench: ID

`string unit.ID`

ID. Getter only.

---

### :fontawesome-solid-wrench: HP

`string unit.HP`

Current HP. Getter only.

---

## Methods

### :material-function: isValid

`void unit->isValid()`

:warning: Dummy function.

---

### :material-function: setGround

`void unit->setGround()`

Unknown.

---

### :material-function: dispOn

`void unit->dispOn(int visible = true)`

Set whether the unit is visible.

---

### :material-function: dispOff

`void unit->dispOff(int invisible = true)`

Set whether the unit is invisible.

---

### :material-function: forceDispOff

`void unit->forceDispOff(int invisible = true)`

Unknown.

---

### :material-function: dispWeapon

`void unit->dispWeapon(bool visible)`

Sets whether the unit's weapon is visible.

---

### :material-function: moveMode

`void unit->moveMode(int mode)`

Sets the move mode.

---

### :material-function: getMoveMode

`int unit->getMoveMode()`

Gets the move mode.

---

### :material-function: isSetDir

`int unit->isSetDir()`

:warning: Dummy function.

---

### :material-function: setModeChange

`void unit->setModeChange(bool unk)`

Unknown.

---

### :material-function: setModeChange

`void unit->setModeChange(float x, float y, float z, int param, int moveMode)`

Unknown.

---

### :material-function: walkR

`void unit->walkR(float unk)`

:warning: Dummy function.

---

### :material-function: walkIdleTime

`void unit->walkIdleTime(int unk)`

:warning: Dummy function.

---

### :material-function: initWalk

`void unit->initWalk(float x, float y, float z)`

:warning: Dummy function.

---

### :material-function: movePoint

`void unit->movePoint(int start, int end, array param, float angle = 360)`

Moves to a point.

---

### :material-function: isMoveEnd

`bool unit->isMoveEnd()`

Returns whether the unit is done moving.

---

### :material-function: waitMoveEnd

`void unit->waitMoveEnd()`

Waits until the unit is done moving.

---

### :material-function: moveTo

`void unit->moveTo(int unk, float x, float y, float z, float angle = 360, int a6 = 0, bool a7 = false, bool a8 = false)`

Moves to a specific point.

---

### :material-function: moveToRun

`void unit->moveToRun(int unk, float x, float y, float z, float angle = 360, int a6 = 0, bool a7 = false, bool a8 = false)`

Runs to a specific point.

---

### :material-function: moveToWalk

`void unit->moveToWalk(int unk, float x, float y, float z, float angle = 360, int a6 = 0, bool a7 = false, bool a8 = false)`

Walks to a specific point.

---

### :material-function: moveToSpd

`void unit->moveToSpd(float speed)`

Sets the movement speed.

---

### :material-function: moveToTurnSpd

`void unit->moveToTurnSpd(float speed)`

Sets the turning speed.

---

### :material-function: loopMotion

`void unit->loopMotion(int type)`

Sets the looping motion.

---

### :material-function: corpMotion

`void unit->corpMotion(int unk, int unk2, int unk3)`

Unknown. Values appears to be the same as loop motion (types).

---

### :material-function: isTalk

`bool unit->isTalk()`

:warning: Dummy function.

---

### :material-function: winTalk

`void unit->winTalk(int id)`

Opens a talking balloon with the specified message id.

---

### :material-function: winTalk2

`void unit->winTalk2(string script, int messageItem)`

Opens a talking balloon with the specified message (V2).

---

### :material-function: holdTalk

`void unit->holdTalk(bool hold)`

Whether to hold talk.

---

### :material-function: holdTalk

`void unit->holdTalk(bool hold = true)`

Whether to hold talk.

---

### :material-function: winAutoTalk

`bool unit->winAutoTalk()`

:warning: Dummy function.

---

### :material-function: onEvent

`bool unit->onEvent()`

Returns whether the unit is currently on an event.

---

### :material-function: onEventAutoTalk

`bool unit->onEventAutoTalk()`

:warning: Dummy function.

---

### :material-function: winTalkSelect

`int unit->winTalkSelect()`

Gets the selected auto talk balloon option index.

---

### :material-function: winTalkToSimpleEve

`void unit->winTalkToSimpleEve(int id)`

Unknown. Might summon a script.

---

### :material-function: setAct

`void unit->setAct(int id, float speed = nil)`

Sets the current action.

---

### :material-function: setActDirect

`void unit->setActDirect(int id, float speed = nil)`

Sets the current direct action.

---

### :material-function: setActSpd

`void unit->setActSpd(float speed = nil)`

Sets the current action speed.

---

### :material-function: lookAt

`void unit->lookAt(oc other, bool maybeUnused = false, bool enableSpine = true, bool bodyLink = false, bool BF1IKMode = true, bool BF1ZIKMode = false)`

Looks at another unit.

---

### :material-function: turn

`void unit->turn(int angle, bool unk = false)`

Turns.

---

### :material-function: setPcNpcWeapon

`void unit->setPcNpcWeapon()`

Unknown.

---

### :material-function: setPcNpcWeapon2

`void unit->setPcNpcWeapon2()`

Unknown.

---

### :material-function: getTargetOC

`oc unit->getTargetOC()`

Gets the current targetted oc for this unit.

---

### :material-function: getTargetOC

`int unit->getTargetID()`

:warning: Dummy function.

---

### :material-function: isPC

`bool unit->isPC()`

Returns whether the current unit is a playable character.

---

### :material-function: isNPC

`bool unit->isNPC()`

Returns whether the current unit is a NPC.

---

### :material-function: isENE

`bool unit->isENE()`

Returns whether the current unit is an enemy.

---

### :material-function: isPT

`bool unit->isPT()`

:warning: Dummy function.

---

### :material-function: invin

`void unit->invin(bool invincible)`

:warning: Dummy function.

---

### :material-function: setBtlState

`void unit->setBtlState(int state, int time = 0, int val1 = 0, int val2 = 0, int interval = 0)`

Sets a battle state.

---

### :material-function: clearBtlState

`void unit->clearBtlState(int state)`

Clears a battle state.

---

### :material-function: setColi

`void unit->setColi(bool collision)`

Sets collision status.

---

### :material-function: setEye

`void unit->setEye(int unk)`

:warning: Dummy function.

---

### :material-function: setGravity

`void unit->setGravity(bool gravity)`

Sets gravity mode.

---

### :material-function: setDyRstOff

`void unit->setDyRstOff(bool unk)`

:warning: Dummy function.

---

### :material-function: dispHighlight

`void unit->dispHighlight(bool dispHighlight)`

Whether to display highlight.

---

### :material-function: setRot

`void unit->setRot(float x, float y, float z)`

Sets unit rotation.

---

### :material-function: setKiriEff

`void unit->setKiriEff(int unk = 0)`

Unknown.