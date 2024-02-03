# Cfs Plugin

Cfs Plugin API.

---

## cfs@mapJump

`void cfs@mapJump(int chapterId, int locationId, float x, float y, float z, int angle, string unused = nil, int unused8 = nil, int unused9 = nil)`

Jumps to a new map.

---

## cfs@mapJumpKillFadein

`void cfs@mapJumpKillFadein(int chapterId, int locationId, float x, float y, float z, int angle, string unused = nil, int unused8 = nil, int unused9 = nil)`

Jumps to a new map with fade in (used on death).

---

## cfs@mapJumpNoLoadIcon

`void cfs@mapJumpNoLoadIcon(int chapterId, int locationId, float x, float y, float z, int angle, string unused = nil, int unused8 = nil, int unused9 = nil)`

Jumps to a new map with fade in without a loading logo.

---

## cfs@setMesSheet

`void cfs@setMesSheet(string msgSheetName)`

Sets the bdat message sheet name to use.

---

## cfs@setMapJumpArea

`void cfs@setMapJumpArea(int chapterId, int locationId, float x1, float y1, float z1, float x2, float y2, float z2, float widthMaybe, float x3, float y3, float z3, float x4, float y4, float z4, int angle = 360, string unused = nil, int unused18 = nil, int unk19 = 0, int unk20 = 0, bool unk21 = false)`

Jumps to map with a specified area.

---

## cfs@setMapJumpAreaBox

`void cfs@setMapJumpAreaBox(int chapterId, int locationId, float a3, float a4, float a5, float a6, float a7, float a8, float a9, float a10; float a11, int a12 = 360, string unused = nil, int a14 = 0, int a15 = 0, int a16 = 0)`

Jumps to map with a specified area box.

---

## cfs@setWarpArea

`void cfs@setWarpArea(int chapterId, int locationId, float x1, float y1, float z1, float x2, float y2, float z2, float widthMaybe, float x3, float y3, float z3, float x4, float y4, float z4, int angle = 360, string unused = nil, int unused18 = nil, int unk19 = 0, int unk20 = 0)`

Jumps to map with warp area.

---

## cfs@setMapPreloadArea

`void cfs@setMapPreloadArea(int chapterId, int locationId, float a3, int a4, float a5, float a6, float a7, float a8, float a9, int a10)`

:warning: Dummy function.

---

## cfs@setMapPreloadArea2

`void cfs@setMapPreloadArea2(int chapterId, int locationId, float x, float y, float z, int unk, int unk2, int unk3)`

:warning: Dummy function.

---

## cfs@setEventArea

`void cfs@setEventArea(string a1, float a2, float a3, float a4, float a5, float a6, string a7 = nil, int a8 = 0)`

:warning: Dummy function.

---

## cfs@delEventArea

`void cfs@delEventArea(string a1)`

:warning: Dummy function.

---

## cfs@setTownArea

`void cfs@setTownArea(float x, float y, float z, float width, float height, string unused = nil, int a8 = 0, int a9 = 0)`

Creates a town area. (loads "XXXXam.sb" & "XXXXpm.sb" scripts?)

---

## cfs@setPopSheet

`void cfs@setPopSheet(string unk)`

:warning: Dummy function.

---

## cfs@addPopID

`void cfs@addPopID(int unk)`

:warning: Dummy function.

---

## cfs@setTimeSpeed

`void cfs@setTimeSpeed(int speed)`

Sets the speed of the clock. 0 is no progression. 1 is normal.

---

## cfs@changeWalker

`void cfs@changeWalker(int unk)`

:warning: Dummy function.

---

## cfs@eventStart

`void cfs@eventStart(int unk = 0, int unk2 = 0)`

Starts script event.

---

## cfs@eventStart

`void cfs@eventStart(int unk = 0)`

Ends script event.

---

## cfs@eventStart

`void cfs@eventStart(int unk = 0)`

Ends script event.

---

## cfs@battleEventStart

`void cfs@battleEventStart()`

:warning: Dummy function.

---

## cfs@delAttr

`void cfs@delAttr(int unk)`

Unknown.

---

## cfs@setMono

`void cfs@setMono(bool unk)`

:warning: Dummy function.

---

## cfs@setMapDispID

`void cfs@setMapDispID(int unkPartId, bool withAlpha, bool unusedMaybe, bool unusedMaybe2, bool unused)`

Unknown.

---

## cfs@loadCfEvent

`void cfs@loadCfEvent(string cfEventScriptName)`

Loads CF event. Waits first if a map jump is in progress.

---

## cfs@loadCfEvent

`void cfs@loadCfEvent(string cfEventName)`

Loads CF event. Waits first if a map jump is in progress. 

Will not load if in event viewer.

---

## cfs@addItem

`int cfs@addItem(int unk)`

:warning: Dummy function.

---

## cfs@delItem

`void cfs@delItem(int itemId, int removeAmount = 1)`

Removes one or multiple of an item from the inventory.

---

## cfs@totalItem

`int cfs@totalItem(int item)`

Gets the number of a specific item in the inventory.

---

## cfs@equipItem

`void cfs@equipItem(int pcId, int headItemId, int bodyItemId, int armItemId, int legItemId, int footItemId)`

Equips a playable character with the specified armor items.

---

## cfs@equipWeapon

`void cfs@equipWeapon(int pcId, int weaponItemId)`

Equips a playable character with the specified weapon.

---

## cfs@getWeaponSlot

`int cfs@getWeaponSlot(int pcId)`

Gets a playable character's current weapon.

---

## cfs@setWeaponSlot

`int cfs@getWeaponSlot(int pcId, int itemId)`

Sets a playable character's current weapon.

---

## cfs@setWeaponSlot

`int cfs@getWeaponSlot(int pcId, int itemId)`

Sets a playable character's current weapon.

---

## cfs@waitEventRes

`void cfs@waitEventRes()`

Wait until the current script event is ready.

---

## cfs@waitCfEvent

`void cfs@waitCfEvent()`

Wait until the current script event ends.

---

## cfs@isMainParty

`bool cfs@isMainParty(int pcId)`

Returns whether a character is in the current party.

---

## cfs@isResvParty

`void cfs@isResvParty(int pcId)`

Returns whether a character is in the reserve party.

---

## cfs@addParty

`void cfs@addParty(int pcId)`

Adds a character to the party.

---

## cfs@delParty

`void cfs@delParty(int pcId)`

Removes a character from the party.

---

## cfs@makeParty

`void cfs@makeParty(int pc1, int pc2 = nil, int pc3 = nil)`

Changes the current party.

---

## cfs@makeGuestParty

`void cfs@makeGuestParty(int pc1 = nil, int pc2 = nil, int pc3 = nil)`

Changes the current guest party.

---

## cfs@setFade

`void cfs@setFade(float a1, float a2, float a3, float a4, int a5 = 0)`

:warning: Dummy function.

---

## cfs@setFade

`void cfs@setFade(float a1, float a2, float a3, float a4, int a5 = 0)`

:warning: Dummy function.

---

## cfs@applyPcPrm

`void cfs@applyPcPrm(int pc, int unk)`

Unknown.

---

## cfs@setDispOffArea

`void cfs@setDispOffArea(oc unit, int unk2)`

:warning: Dummy function.

---

## cfs@setWeather

`void cfs@setWeather(int weatherType)`

:warning: Dummy function.

---

## cfs@setWeatherArea

`void cfs@setWeatherArea(int weatherType)`

Sets the weather for the area.

---

## cfs@setGimmick

`void cfs@setGimmick(int gimmickId, int state)`

Sets a gimmick.


---

## cfs@setElvGim

`void cfs@setElvGim(int gimmickId)`

Sets an elevator gimmick.

---

## cfs@setActMapObj

`void cfs@setActMapObj(int unk, int unk2)`

Unknown.

---

## cfs@setDispMapObj

`void cfs@setDispMapObj(int unk, bool unk2)`

Unknown.

---

## cfs@getMapID

`int cfs@getMapID()`

Returns the current map id.

---

## cfs@clearGimmickJump

`void cfs@clearGimmickJump()`

:warning: Dummy function.

---

## cfs@partyMember

`bool cfs@partyMember(int slot)`

Returns if a party member exists at the specified slot (1-3).

---

## cfs@clearPartyGauge

`void cfs@clearPartyGauge()`

:warning: Dummy function.

---

## cfs@waitPop

`void cfs@waitPop()`

Waits until the enemy is ready/has popped.

---

## cfs@partyWarp

`void cfs@partyWarp()`

Unknown.

---

## cfs@setMoney

`void cfs@setMoney(int money)`

Set the current money.

---

## cfs@addMoney

`void cfs@addMoney(int money)`

Adds money.

---

## cfs@isTimeSkip

`bool cfs@isTimeSkip()`

Returns if currently time skipping.

---

## cfs@isTimeSkipFirst

`bool cfs@isTimeSkipFirst()`

Unknown.

---

## cfs@delHoldBox

`void cfs@delHoldBox(int unk)`

:warning: Dummy function.

---

## cfs@getWeaponID

`void cfs@getWeaponID(int pcId)`

Gets the weapon id for a playable character.

---

## cfs@clearTreasureBox

`void cfs@clearTreasureBox()`

Clears all treasure boxes/chests on the map.

---

## cfs@setScheduleType

`void cfs@setScheduleType(oc npc, int unk)`

Unknown.

---

## cfs@returnTitle

`void cfs@returnTitle()`

Returns to the title screen.

---

## cfs@dispLoading

`void cfs@dispLoading()`

:warning: Dummy function.

---

## cfs@addItemLimit

`void cfs@addItemLimit(int unk)`

:warning: Dummy function.

---

## cfs@clearItemLimit

`void cfs@clearItemLimit()`

:warning: Dummy function.

---

## cfs@clearEquipGem

`void cfs@clearEquipGem()`

:warning: Dummy function.

---

## cfs@setPcCtrl

`void cfs@setPcCtrl(bool unk)`

Unknown.

---

## cfs@setFieldVision

`void cfs@setFieldVision()`

Shows vision (on the field).

---

## cfs@saveNamedCount

`void cfs@saveNamedCount()`

:warning: Dummy function.

---

## cfs@isPal

`bool cfs@isPal()`

:warning: Dummy function.

---

## cfs@setIgnorePal

`bool cfs@setIgnorePal(bool ignore)`

:warning: Dummy function.

---

## cfs@isVoiceJP

`bool cfs@isVoiceJP()`

Returns whether the voice is set to japanese.


---

## cfs@waitEventViewer

`void cfs@waitEventViewer()`

Waits until the event viewer is done.

---

## cfs@setCfEventCutScene

`void cfs@setCfEventCutScene(string name)`

Unknown.

---

## cfs@setCfEventCutSceneList

`void cfs@setCfEventCutSceneList(string name)`

Unknown.

---

## cfs@isScenarioMelia

`void cfs@isScenarioMelia()`

Returns whether this is Future Connected.

---

## cfs@returnDefectGem

`void cfs@returnDefectGem(int unk)`

Unknown.

---

## cfs@addArtsCoin

`void cfs@addArtsCoin(int coins, bool unk)`

Adds arts coins (Future Connected).

---

## cfs@waitModelStream

`void cfs@waitModelStream()`

Waits until model streaming is done.

---

## cfs@canAcceptOrder

`bool cfs@canAcceptOrder()`

Unknown.

---

## cfs@setAllowEventSkip

`void cfs@setAllowEventSkip(bool canSkip)`

Sets whether event skipping is enabled.