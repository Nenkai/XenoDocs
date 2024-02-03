# Sound Plugin

Sound Plugin API.

---

## sound@playBgm

`void sound@playBgm(int bgmId, float fadetime, bool flag = false)`

:warning: Dummy function.

---

## sound@stopBgm

`void sound@stopBgm(float fadetime)`

:warning: Dummy function.

---

## sound@setFieldBgm

`void sound@setFieldBgm(int bgmId = 0, int bgmIdBattle = 0, float fadetime = 0, bool flag = false)`

Sets field+battle background music.

---

## sound@setTownBgm

`void sound@setTownBgm(int bgmId = 0, int bgmIdBattle = 0, float fadetime = 0, bool flag = false)`

Sets town+battle background music.

---

## sound@stopFieldBgm

`void sound@stopFieldBgm(float fadetime = 0)`

Stops field background music.

---

## sound@stopTownBgm

`void sound@stopTownBgm(float fadetime = 0)`

Stops town background music.

---

## sound@forceFieldBgm

`void sound@forceFieldBgm(float fadetime = 0)`

Forces field background music regardless of context.

---

## sound@stopBgm

`void sound@stopBgm(float unk, float unk2 = 0)`

:warning: Dummy function.

---

## sound@playVoice

`void sound@playVoice(string voiceName)`
 
Plays a voice file.

---

## sound@stopVoice

`void sound@stopVoice(string voiceName = nil)`
 
:warning: Dummy function.

---

## sound@waitVoice

`void sound@waitVoice()`
 
Waits for voice playback to end.

---

## sound@playSeCommon

`void sound@playSeCommon(int id, float unk = 1, float unk2 = 0)`
 
Plays a sound effect.

---

## sound@playSeMap

`void sound@playSeMap(int id, float unk = 1, float unk2 = 0)`
 
Plays a map sound effect.

---

## sound@volSeMap

`void sound@volSeMap(int id, float unk = 1, float unk2 = 0)`

Unknown.

---

## sound@stopSeCommon

`void sound@stopSeCommon(int unk, float unk2)`

Stops sound effect.

---

## sound@stopSeMap

`void sound@stopSeMap(int unk, float unk2)`

Stops map sound effect.

---

## sound@setCamPos

`void sound@setCamPos(float x, float y, float z, float unk = 0, float unk2 = 0, float unk3 = 0)`

Sets camera sound position.

---

## sound@clearCamPos

`void sound@clearCamPos()`

Clears camera sound position.

---

## sound@setEnableFadeVolume

`void sound@setEnableFadeVolume(bool enable = true)`

Sets whether to enable fading volume.

---

## sound@playNpcVoice

`void sound@playNpcVoice(int unkId, int unk2)`

Plays NPC voice. ID is used against `FLD_npclist`->resource which is then used for `KP_list`->sound.

!!! warning

    Calls `game::ScriptSound::playNpcVoice` which has an hardcoded check of ID 201 max.

---