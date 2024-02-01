# UI Plugin

UI Plugin API.

---

## ui@winTalk

`void ui@winTalk(int unk, string unk2)`

Dummy function.

---

## ui@pcTalk

`void ui@pcTalk(int type)`

Triggers playable character talk. Type maps to [pctalk01](../../tables/bdat_common.md#pctalk_01). 

Calls `game::ScriptCfs::startPcTalk`.

---

## ui@winTalkWait

`void ui@winTalkWait()`

Waits for talk to finish (if any talk UI is open) before resuming execution.

---

## ui@winTalkNoName

`void ui@winTalkNoName(int id)`

Shows text on-screen without a dialog or name. ID will map to bdat file [script_msg_ms] with matching script name. Calls `game::ScriptUI::openNoNameSubtitleSEV`.

!!! tip

    This is used during High Entia Tomb cutscenes when the ancestor AI speaks to Melia.

---

## ui@fadeIn

`void ui@fadeIn(int unk, int unk2 = 0)`

Dummy Function.

---

## ui@fadeOut

`void ui@fadeOut(int unk, int unk2 = 0)`

Dummy Function.

---

## ui@fadeWait

`void ui@fadeWait()`

Dummy Function.

---

## ui@createCol6Sys

`void ui@createCol6Sys()`

Opens Colony 6 Reconstruction UI.


---

## ui@createCol6Hint

`void ui@createCol6Hint()`

Unknown.

---

## ui@createCol6Invite

`void ui@createCol6Invite(int npcId, int extraReconstruction, int extraPopulation)`

Creates & processes a colony 6 npc invitation. ID is [FLD_npclist](../../tables/bdat_common.md#fld_npclist).

---

## ui@createCol6Init

`void ui@createCol6Init()`

Dummy function.

---

## ui@checkCol6Bat

`void ui@checkCol6Bat()`

Opens Colony 6 attack ui if one is expected. Calls `game::ScriptUI::openIfColony6Attack`.

---

## ui@simpleEventStart

`void ui@simpleEventStart()`

Dummy function.

---

## ui@simpleEventEnd

`void ui@simpleEventEnd()`

Dummy function.

---

## ui@setTrust

`void ui@setTrust(int spc1, int spc2, int kizunaFlag, int increase)`

Changes the trust between two playable characters.

---

## ui@setItemMulti

`void ui@setItemMulti(int itemId1 = 1, int itemId2 = nil, int itemId3 = nil, int itemId4 = nil, bool unk = nil)`

Brings up a multi-item selection prompt.

---

## ui@setKizunaTalk

`void ui@setKizunaTalk(int kznId)`

Shows a kizuna (relation) dialog.

---

## ui@winSys

`void ui@winSys(int msgId)`

Shows a generic system dialog. ID will map to bdat file [script_msg_ms] with matching script name.

---

## ui@winSysSelect

`void ui@winSysSelect(int selectMsgId1, int selectMsgId2, int selectMsgId3)`

Shows a generic system dialog with selection. ID will map to bdat file [script_msg_ms] with matching script name.

!!! tip

    This is used for the last point of no return or confirmations before proceeding.

---

## ui@getSelectNum

`int ui@getSelectNum()`

Gets the dialog selection item index chosen (when `ui@winSysSelect` is used).

---

## ui@mesGetArts

`int ui@mesGetArts(int pcId, int artId)`

Shows an art unlocked message.

---

## ui@mesAddPT

`int ui@mesAddPT(int unk)`

Dummy function.

---

## ui@mesSubPT

`int ui@mesSubPT(int unk)`

Dummy function.

---

## ui@mesVisionON

`int ui@mesVisionON()`

Dummy function.

---

## ui@mesVisionOFF

`void ui@mesVisionOFF()`

Dummy function.

---

## ui@mesMonadoON

`void ui@mesMonadoON()`

Dummy function.

---

## ui@mesMonadoOFF

`void ui@mesMonadoOFF()`

Dummy function.

---

## ui@ptChangeNotice

`void ui@ptChangeNotice()`

Shows a party change dialog.

---

## ui@save

`void ui@save()`

Shows a save dialog.

---

## ui@kizunaTalkStart

`void ui@kizunaTalkStart()`

Starts a relation/heart-to-heart talk.

---

## ui@kizunaTalkEnd

`void ui@kizunaTalkStart()`

Ends a relation/heart-to-heart talk.

---

## ui@kizunaTalkEnd

`bool ui@isPrioReq()`

Unknown.

---

## ui@gameClear

`void ui@gameClear()`

Opens save dialog with the game cleared flag.

---

## ui@setLastTalkNpc

`void ui@setLastTalkNpc(int rltMeet)`

Unknown. ID is matched through [FLD_npclist](../../tables/bdat_common.md#fld_npclist)->rlt_meet.

---

## ui@isSETalkVoiceWait

`bool ui@isSETalkVoiceWait()`

Returns whether talk voice is ongoing.

---

## ui@setSETalkVoiceWait

`void ui@setSETalkVoiceWait()`

Dummy function.

---

## ui@clearSETalkVoiceWait

`void ui@clearSETalkVoiceWait()`

Dummy function.

---

## ui@createTrialSelect

`void ui@createTrialSelect()`

Creates time attack/trial dialog.

---

## ui@joinNopongerDialog

`void ui@joinNopongerDialog(int nopongerId)`

Creates a nopon ponspector join dialog (Future Connected).

---

## ui@isJoinPc

`bool ui@isJoinPc(int nopongerId)`

Returns whether a nopon ponspector has joined (Future Connected).

---

## ui@isEndMeliaClearSave

`bool ui@isEndMeliaClearSave()`

Returns whether Future Connected has been completed.

---