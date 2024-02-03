# Attribute OC/Object

Represents a script attribute/trigger.

---

## :material-new-box: Constructor

`oc attr(string unusedName, int type)`

Gets a new attribute.

---

## Attributes

### :fontawesome-solid-wrench: x

`float attr.x`

X position.

---

### :fontawesome-solid-wrench: y

`float attr.y`

Y position.

---

### :fontawesome-solid-wrench: y

`float attr.z`

Z position.

---

### :fontawesome-solid-wrench: bdid

`string attr.bdid`

Unknown. Getter only.

## Methods

### :material-function: isValid

`void attr->isValid()`

:warning: Dummy function.

---

### :material-function: setGround

`void attr->setGround()`

Unknown.

---

### :material-function: dispOn

`void attr->dispOn(int visible = true)`

Set whether the attr is visible.

---

### :material-function: dispOff

`void attr->dispOff(int invisible = true)`

Set whether the attr is invisible.

---

### :material-function: setSize

`void effect->setSize(float radius, float height)`

Sets the size as a cylinder shape.

---

### :material-function: setBox

`void attr->setBox(float fixX, float fixY, float fixZ, float rotY)`

Sets the size as a box shape.

---

### :material-function: inside

`bool attr->inside(oc unit = nil)`

Unknown.

---

### :material-function: insideNormal

`bool attr->insideNormal(oc unit)`

Unknown.