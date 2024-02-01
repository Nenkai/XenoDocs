# Camera Plugin

Camera Plugin API.

---

## cam@select

`void cam@setCamera(int camera)`

Sets the current camera type.

---

## cam@select

`void cam@setCamera(int unk = 0, int unkBool = false)`

Restores to normal camera.

---

## cam@setPos

`void cam@setCamera(float x, float y, float z)`

Sets the camera position.

---

## cam@setDir

`void cam@setDir(float dirX, float dirY)`

Sets the camera direction.

---

## cam@setLookat

`void cam@setLookat(float x, float y, float z)`

Sets the camera lookat position.

---

## cam@setLookat

`void cam@setTarget(oc target)`

Sets the camera lookat position.

---

## cam@setRotX

`void cam@setRotX(float x)`

Sets camera X rotation.

---

## cam@setRotY

`void cam@setRotY(float x)`

Sets camera Y rotation.

---

## cam@setFov

`void cam@setFov(float fov)`

Sets camera FoV (Field of View).

---

## cam@getPos

`float cam@getPos(int component)`

Gets camera position (component is used as element index i.e `cameraPosition[component]`).

---

## cam@getRot

`float cam@getRot(int component)`

Gets camera rotation (component is used as element index i.e `cameraRotation[component]`).

---

## cam@setPosOfs

`void cam@setPosOfs(oc unk, float x, float y, float z, int unk = 0)`

Sets position offset.

---

## cam@setLookatOfs

`void cam@setLookatOfs(oc unk, float x, float y, float z, int unk = 0)`

Sets camera lookat offset.

---

## cam@beginKey

`void cam@beginKey(int unk, int unk2, int unk3 = 0, int unk4 = 0, oc unk5 = nil)`

Unknown.

---

## cam@endKey

`void cam@endKey()`

Unknown.

---

## cam@addKey

`void cam@endKey(int unk, float unk2, float unk3, float unk4, float unk5, float unk6, float unk7, float unk8 = 0, int unk9 = 0)`

Unknown.

---

## cam@isKeyMove

`bool cam@isKeyMove()`

Unknown.

---

## cam@waitKeyMove

`bool cam@waitKeyMove()`

Waits until key is done moving.

---

## cam@shake

`void cam@shake(int a1, float a2, float a3, float a4, float a5, float a6, float a7, float a8, float a9, float a10, float a11, float a12, bool a13)`

Starts camera shake.

---

## cam@stopShake

`void cam@stopShake()`

Stops camera shake.

---

## cam@setNearFar

`void cam@setNearFar(int val)`

Sets camera near/far.

---

## cam@setNextPos

`void cam@setNextPos(float x = 0, float y = 0, float z = 0)`

Sets the next camera position.