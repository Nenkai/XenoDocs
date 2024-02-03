# Point OC/Object

Represents a world/field point.

---

## :material-new-box: 
Constructor

`oc point(string unusedName, int pointId, int unused = nil)`

Gets a new point from [FLD_pointlist](../../tables/bdat_common.md#fld_pointlist).

---

## Attributes

### :fontawesome-solid-wrench: x

`float point.x`

X position.

---

### :fontawesome-solid-wrench: y

`float point.y`

Y position.

---

### :fontawesome-solid-wrench: y

`float point.z`

Z position.

---

### :fontawesome-solid-wrench: bdid

`string point.bdid`

Unknown. Getter only.

## Methods

### :material-function: isValid

`void point->isValid()`

:warning: Dummy function.

---

### :material-function: setGround

`void point->setGround()`

Unknown.

---

### :material-function: dispOn

`void point->dispOn(int visible = true)`

Set whether the point is visible.

---

### :material-function: dispOff

`void obj->dispOff(int invisible = true)`

Set whether the point is invisible.

---

### :material-function: moveMode

`void point->moveMode(int mode)`

Sets the move mode.

---

### :material-function: isSetDir

`int point->isSetDir()`

:warning: Dummy function.

---

### :material-function: winTalk

`void point->winTalk(int id)`

Opens a talking balloon with the specified message id.

---

### :material-function: onEvent

`bool point->onEvent()`

Returns whether the point is currently on an event.

---

### :material-function: winTalkSelect

`int point->winTalkSelect()`

Gets the selected auto talk balloon option index.

---

### :material-function: winTalkToSimpleEve

`void point->winTalkToSimpleEve(int id)`

Unknown. Might summon a script.