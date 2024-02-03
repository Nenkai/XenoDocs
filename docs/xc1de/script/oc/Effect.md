# Effect OC/Object

Represents a world/field effect.

---

## :material-new-box: Constructor

`oc effect(string effectName, int effectId, int unused = nil)`

Gets a new effect.

Valid Names:

* `map` or `em`
* `common` or `er`

---

## Attributes

### :fontawesome-solid-wrench: x

`float effect.x`

X position.

---

### :fontawesome-solid-wrench: y

`float effect.y`

Y position.

---

### :fontawesome-solid-wrench: y

`float effect.z`

Z position.

---

### :fontawesome-solid-wrench: bdid

`string effect.bdid`

Unknown. Getter only.

## Methods

### :material-function: isValid

`void effect->isValid()`

:warning: Dummy function.

---

### :material-function: setGround

`void effect->setGround()`

Unknown.

---

### :material-function: dispOn

`void effect->dispOn(int visible = true)`

Set whether the effect is visible.

---

### :material-function: dispOff

`void effect->dispOff(int invisible = true)`

Set whether the effect is invisible.

---

### :material-function: signal

`void effect->signal(int mode)`

Unknown.

---

### :material-function: setCas

`void effect->setCas(oc unit)`

Sets caster.

---

### :material-function: setTgt

`void effect->setTgt(oc unit)`

Sets target.

---

### :material-function: setWeaponCas

`void effect->setWeaponCas(oc unit)`

Sets weapon caster.