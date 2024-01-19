# bdat_common

## Misc Tables

### bgm_list

*Human Readable Name*: Background Music List

Maps BGM IDs to their file names.

| Column      | Type     | Description                                         | Handled by |
|-------------|----------|-----------------------------------------------------|------------|
| `file_name` | `string` | BGM File Name. Will be hashed, see below            | `game::BGM::getBGMName`, `game::SoundUtil::findBGMID`, `game::SoundUtil::findBGMID` | 

!!! note "Hashing"

    ```c++
    // fw::SoundManager::playBattleBGM - 0x7100064A60 - 1.1.2
    mm::mtl::FixStr<32>::format(str, "%s_%03d", file_name, unk); 
    mm::mtl::FixStr<256>::format(final_str, "%s_%lu", str, this->LastID);
    IDFromString = AK::SoundEngine::GetIDFromString(final_str); // Audiokinetic Wwise
    // this->LastID++

    if ( v20 )
        v21 = "arrange";
    else
        v21 = "original";
    AK::SoundEngine::SetSwitch((AK::SoundEngine *)"battle_bgm", v21, (const char *)IDFromString); // Will hash on its own
    ```

---

### ene_arts

*Human Readable Name*: Enemy Arts

`MsTextId` linked to `ene_arts_ms`.

Represents all enemy arts.

| Column      | Type      | Description                                         | Handled by |
|-------------|-----------|-----------------------------------------------------|------------|
| `name`      | `MsTextId`| Localized art name.                                 | `game::DataAttack::setupMapEnemyArtsAttack` | 
| `cast`      | `uint8`   | Time to cast.                                       | `game::DataAttack::setupMapEnemyArtsAttack` | 
| `recast`    | `uint8`   | Cast cooldown (if applicable).                      | `game::DataAttack::setupMapEnemyArtsAttack` | 
| `tp`        | `int8`    | Talent Gauge % used.                                | `game::DataAttack::setupMapEnemyArtsAttack` | 
| `dex`       | `int8`    | Dexterity/Accuracy.                                 | `game::DataAttack::setupMapEnemyArtsAttack` | 
| `rate1`     | `uint16`  | Power Min.                                          | `game::DataAttack::setupMapEnemyArtsAttack` | 
| `rate2`     | `uint16`  | Power Max.                                          | `game::DataAttack::setupMapEnemyArtsAttack` | 
| `arts_type` | `uint8`   | Art Type.                                           | `game::DataAttack::setupMapEnemyArtsAttack` | 
| `lv`        | `uint8`   | Level. Mainly affects arts that afflict statuses or causes Visions.   | `game::DataAttack::setupMapEnemyArtsAttack` | 
| `atk_type`  | `uint8`   | Attack Type.                                        | `game::DataAttack::setupMapEnemyArtsAttack` | 
| `elem`      | `uint8`   | Element.                                            | `game::DataAttack::setupMapEnemyArtsAttack` | 
| `dmg_time`  | `uint8`   | Number of Attacks.                                  | `game::DataAttack::setupMapEnemyArtsAttack` | 
| `tgt`       | `uint8`   | Target type.                                        | `game::DataAttack::setupMapEnemyArtsAttack` | 
| `range_type`| `uint8`   | Range type.                                         | `game::DataAttack::setupMapEnemyArtsAttack` | 
| `range`     | `uint16`  | Range (in centimeters).                             | `game::DataAttack::setupMapEnemyArtsAttack` | 
| `range_val` | `uint16`  | Range Radius/Width (depending on type).             | `game::DataAttack::setupMapEnemyArtsAttack` | 
| `flag`      | `uint32`  | Flags tied to the art.                              | `game::DataAttack::setupMapEnemyArtsAttack` | 
| `st_type`   | `uint8`   | [State/Buff/Effect](#btl_bufflist) to apply. No more than 0x132.   | `game::DataAttack::setupMapEnemyArtsAttack` | 
| `st_val`    | `uint8`   | Value 1 for the state.                              | `game::DataAttack::setupMapEnemyArtsAttack` | 
| `st_val2`   | `uint8`   | Value 2 for the state.                              | `game::DataAttack::setupMapEnemyArtsAttack` | 
| `st_time`   | `uint16`  | Duration. Divide by 100 for seconds.                | `game::DataAttack::setupMapEnemyArtsAttack` | 
| `st_itv`    | `uint8`   | State - Number of ticks per activation.             | `game::DataAttack::setupMapEnemyArtsAttack` | 
| `sp_cnd`    | `uint8`   | State condition.                                    | `game::DataAttack::setupMapEnemyArtsAttack` | 
| `sp_proc`   | `uint8`   | Bonus effect?                                       | `game::DataAttack::setupMapEnemyArtsAttack` | 
| `sp_val1`   | `uint16`  | Bonus effect value 1.                               | `game::DataAttack::setupMapEnemyArtsAttack` | 
| `sp_val2`   | `uint16`  | Bonus effect value 2.                               | `game::DataAttack::setupMapEnemyArtsAttack` | 
| `kb_type`   | `uint8`   | Knockback Type.                                     | `game::DataAttack::setupMapEnemyArtsAttack` | 
| `kb_lv`     | `uint8`   | Knockback level, above 2 = Daze. Up to 6.           | `game::DataAttack::setupMapEnemyArtsAttack` | 
| `act_idx`   | `uint8`   | Action index.                                       | `game::DataAttack::setupMapEnemyArtsAttack` | 
| `idx`       | `uint8`   | Index.                                              | `game::DataAttack::setupMapEnemyArtsAttack` | 

??? abstract "`arts_type`"

    * 0 = Normal
    * 1 = Special/Talent (has specific handlers - cannot be upgraded)
    * 2 = Unknown
    * 3 = Topple
    * 4 = Daze
    * 5 = Knockback
    * 6 = Blowdown
    * 7 = Debuff
    * 8 = Buff
    * 9 = Heal
    * 10 = Cleanse

??? abstract "`atk_type`"

    * 1 = "Physix"/Physical
    * 2 = Ether
    * 3 = Status
    * 4 = Summon
    * 6 = Discharge

??? abstract "`elem` aka `game::DataAttack::ElementType`"

    * 0 = None
    * 1 = Normal
    * 2 = Slash
    * 4 = Fire
    * 5 = Water
    * 6 = Electric
    * 7 = Ice
    * 8 = Wind
    * 9 = Earth

??? abstract "`tgt` aka `game::DataAttack::TargetType`"

    * 0 = Enemy
    * 1 = Self
    * 2 = Self/Allies
    * 3 = Allies only

??? abstract "`range_type` aka `game::DataAttack::RangeType`"

    * 0 = Single Target
    * 1 = Cone (ahead)
    * 2 = Cone (behind)
    * 4 = Circle (self)
    * 5 = Line
    * 6 = Circle (target)
    * 7 = All 

??? abstract "`flag`"

    * 0x01 - 1 << 0 = Anti-Mechon
    * 0x02 - 1 << 1 = Anti-Mechon 2?
    * 0x04 - 1 << 2 = Anti-Air/Monado
    * 0x400 - 1 << 10 - Status Effect applies on self
    * 0x800 - 1 << 11 - Bonus Status Effect applies on self
    * 0x1000 - 1 << 12 = Forced Vision
    * 0x2000 - 1 << 13 = Effect/knockback applies only on the last hit
    * 0x4000 - 1 << 14 = Unknown
    * 0x10000 - 1 << 16 = Vision can be interrupted by interposed terrain (i.e Mechonis Field boss)
    * 0x4000000 - 1 << 26 = Unknown
    * 0x8000000 - 1 << 27 = Unknown

??? abstract "`sp_cnd`"
    * 0 = Always
    * 2 = From side
    * 3 = From behind
    * 4 = In combo
    * 5 = On toppled
    * 6 = On dazed
    * 8 = Killing blow
    * 9 = On Mechon
    * 15 = In blizzard
    * 25 = On Mechon side

??? abstract "`kb_type`"

    * 0 = None
    * 1 = Pushback
    * 2 = Blowdown.

    ??? tip "Knockback power per level"

        As per `game::DataAttack::getKBPower`

        * 6.5
        * 8.0
        * 10.0
        * 12.5
        * 15.0
        * 0.0

    ??? tip "Knockback blow power per level"

        As per `game::DataAttack::getBlowPower`

        * 3.0
        * 4.0
        * 5.5
        * 7.0
        * 8.5
        * 10.0

    ??? tip "Knockback blow upper per level"

        As per `game::DataAttack::getBlowUpper`

        * 1.0
        * 1.2
        * 1.5
        * 1.8
        * 2.1
        * 2.4

    ??? tip "Knockback blow daze seconds per level"

        As per `game::DataAttack::getBlowFaint`

        * 0.0
        * 0.0
        * 3.0
        * 5.0
        * 10.0
        * 15.0
    
// game::EffUtil::getStatusEffectToCndEffId

// wpnlist->flag

---

### ene_atk

Represents enemy auto-attacks.

| Column      | Type      | Description                                         | Handled by |
|-------------|-----------|-----------------------------------------------------|------------|
| `name`      | `string`  | Name (debug).                                       | `game::DataAttack::setupMapEnemyAutoAttack` | 
| `dex`       | `int8`    | Dexterity/Accuracy.                                 | `game::DataAttack::setupMapEnemyAutoAttack` | 
| `rate`      | `uint16`  | Power.                                              | `game::DataAttack::setupMapEnemyAutoAttack` | 
| `atk_type`  | `uint8`   | Attack Type.                                        | `game::DataAttack::setupMapEnemyAutoAttack` | 
| `elem`      | `uint8`   | Element.                                            | `game::DataAttack::setupMapEnemyAutoAttack` | 
| `flag`      | `uint32`  | Flags tied to the art.                              | `game::DataAttack::setupMapEnemyAutoAttack` | 
| `st_type`   | `uint8`   | [State/Buff/Effect](#btl_bufflist) to apply. No more than 0x132.   | `game::DataAttack::setupMapEnemyArtsAttack` | 
| `st_val`    | `uint8`   | Value for the state.                                | `game::DataAttack::setupMapEnemyAutoAttack` | 
| `range_type`| `uint8`   | Range type.                                         | `game::DataAttack::setupMapEnemyAutoAttack` | 
| `range`     | `uint16`  | Range (in centimeters).                             | `game::DataAttack::setupMapEnemyAutoAttack` | 
| `range_val` | `uint16`  | Range Radius/Width (depending on type).             | `game::DataAttack::setupMapEnemyAutoAttack` | 
| `act_idx`   | `uint8`   | Action index.                                       | `game::DataAttack::setupMapEnemyAutoAttack` | 
| `idx`       | `uint8`   | Index.                                              | `game::DataAttack::setupMapEnemyAutoAttack` | 

---

### landmarklist

List of all the landmarks in the game.

| Column      | Type      | Description                                         | Handled by |
|-------------|-----------|-----------------------------------------------------|------------|
| `name`      | `MsTextId`| Localized landmark name.                            | `game::MenuGameDataMap::getLandmarkNameText` | 
| `category`  | `uint8`   | 0 = Landmark, 1 = Secret Area, 2 = Location         | `game::GimmickLandmark::initialize` | 
| `mapID`     | `uint16`  | [Map ID](#fld_maplist).                             | Too many.                         | 
| `S_FLG_MIN1`| `uint16`  | Minimum scenario flag for access.                   | `game::MenuGameDataMap::getLandmarkLockReason` | 
| `S_FLG_MAX1`| `uint16`  | Maximum scenario flag for access.                   | `game::MenuGameDataMap::getLandmarkLockReason` | 
| `posX`      | `int16`   | X position on the map.                              | `game::GimmickLandmark::initialize` | 
| `posY`      | `int16`   | X position on the map.                              | `game::GimmickLandmark::initialize` | 
| `posZ`      | `int16`   | X position on the map.                              | `game::GimmickLandmark::initialize` | 
| `areaR`     | `Uint16`  | Area radius.                                        | `game::GimmickLandmark::initialize` | 
| `areaY`     | `Uint16`  | Area Y.                                             | `game::GimmickLandmark::initialize` | 
| `areaZ`     | `Uint16`  | Area Z.                                             | `game::GimmickLandmark::initialize` | 
| `rotY`      | `Uint16`  | Rotation Y.                                         | `game::GimmickLandmark::initialize` | 
| `getEXP`    | `uint16`  | Discovery EXP reward.                               | `game::DataUtil::addExpApSpForLandmark` | 
| `getAP`     | `uint16`  | Discovery AP reward.                                | `game::DataUtil::addExpApSpForLandmark` | 
| `getPP`     | `uint16`  | Discovery PP reward.                                | `game::DataUtil::addExpApSpForLandmark` | 
| `jump_posX` | `int16`   | X position when teleporting to the landmark.        | `game::SeqMapJump::onInitialize` | 
| `jump_posY` | `int16`   | Y position when teleporting to the landmark.        | `game::SeqMapJump::onInitialize` | 
| `jump_posZ` | `int16`   | Z position when teleporting to the landmark.        | `game::SeqMapJump::onInitialize` | 
| `UI_posX`   | `int8`    | X position on the UI.                               | `game::MenuPartsAreaMapTopView::setMapFloorId` | 
| `UI_posY`   | `int8`    | Y position on the UI.                               | `game::MenuPartsAreaMapTopView::setMapFloorId` | 

---

### mnuXXX_contXX_txt

Each file is referenced from [MNU_TextLink_Mstxt](#mnu_textlink_mstxt).

Bdat loaded from `game::UILayerBuilderDefGrp::UILayerBuilderDefGrp` ctor.

Otherwise unknown. Seems to be used to set up some assets for certain menu layer groups.

| Column         | Type     | Description                                         | Handled by |
|----------------|----------|-----------------------------------------------------|------------|
| `rect_path`    | `uint8`  | Material Number. Unknown.                           | `game::UILayerBuilderDefGrp::buildUILayerRecursiveGroup` | 
| `text_file`    | `uint8`  | No more than 0x22.                                  | `game::UILayerBuilderDefGrp::buildUILayerRecursiveGroup` | 
| `text_id`      | `uint8`  | % in player damage when field damage triggers.      | `game::UILayerBuilderDefGrp::buildUILayerRecursiveGroup` | 
| `default_text` | `string` | Default text.                                       | `game::UILayerBuilderDefGrp::buildUILayerRecursiveGroup` | 

---

## Map Specific

!!! warning "Bdat mapping"

    Each file takes two numbers:
    
    * `%02d` - "Chapter" - uint16 - from `game::DataUtil::getChapterFromMapId`
        * `game::DataUtil::getChapterFromMapId` takes [FLD_maplist](#fld_maplist)->resource using map id, returns 3rd and 4th digit
    * `%02d` - "Location" - uint16 - from `game::DataUtil::getLocationFromMapId`
        * `game::DataUtil::getLocationFromMapId` takes [FLD_maplist](#fld_maplist)->resource using map id, returns 5th and 6th digit

---

### mapobjfileSys / mapobjfile|num|

*Human Readable Name*: Map Object Files

Represents objects/areas to be loaded for the map.

| Column      | Type     | Description                                         | Handled by |
|-------------|----------|-----------------------------------------------------|------------|
| `resource`  | `string` | File to be loaded from `chr/obj/`.                  | `game::ResMobjBinder::bind` | 
| `flag`      | `uint16` | Whether to load a character file.                   | `game::ResMobjBinder::bind` | 

!!! note

    Table accessor functions: `game::MenuObj::createObjImpl`, `game::ObjFactory::createTreasureBoxMobj`

### minimaplist|num|

*Human Readable Name*: Minimap File List (per map)

`MsTextId` linked to `mapobjlist|num|_ms`.

Represents minimap files to load per map.

| Column      | Type      | Description                                         | Handled by |
|-------------|-----------|-----------------------------------------------------|------------|
| `height`    | `int16`   | Display height.                                     | `game::MenuMinimapInfo::getInFloor` & more | 
| `file`      | `uint16`  | File.                                               |  | 
| `mapimg`    | `uint16`  | Default image. [SYS_filelist](#sys_filelist) ID.    | `game::BdatMnuMinimapList::mapimg` | 
| `floorname` | `MsTextId`| Localized floor name.                               | `game::impl::MenuPartsAreaMapDetailFloorListItem::setFloorId` | 
| `sflag`     | `uint16`  | Min Scenario flag condition for unlock.             | `game::MenuGameDataMap::getMapFloorImageName` | 
| `qflag1`    | `uint16`  | Quest condition for unlock.                         | `game::MenuGameDataMap::getMapFloorImageName` | 
| `val1`      | `string`  | Quest's state condition for unlock.                 | `game::MenuGameDataMap::getMapFloorImageName` | 
| `flag`      | `uint16`  | Whether to load a character file.                   | `game::ResMobjBinder::bind` | 
| `mapimg1`   | `uint16`  | Used depending on scenario status. [SYS_filelist](#sys_filelist) ID. | `game::BdatMnuMinimapList::mapimg1` | 
| `mapimg2`   | `uint16`  | Used depending on scenario & quest status. [SYS_filelist](#sys_filelist) ID.  | `game::BdatMnuMinimapList::mapimg2` | 

---

### mapobjlistSys

*Human Readable Name*: Map Object List (System)

Parameters for [mapobjfileSys](#mapobjfilesys--mapobjfile02d).

!!! note

    Table accessor functions: `game::GimmickMapSE::execSetup`

---

## Field
### FLD_dmobjlist

*Human Readable Name*: Field - Damage Object List

Represents objects/areas on the map field that hurt/damage the player.

| Column      | Type     | Description                                         | Handled by |
|-------------|----------|-----------------------------------------------------|------------|
| `matno`     | `uint8`  | Material Number. Unknown.                           | `game::StateUtil::procDmgField` | 
| `interval`  | `uint8`  | Interval in seconds which field damage will occur.  | `game::StateUtil::procDmgField` | 
| `dmg`       | `uint8`  | % in player damage when field damage triggers.      | `game::StateUtil::procDmgField` | 
| `map`       | `uint16` | [Map ID Number](#fld_maplist) (+ sector). Divide by 100 for actual map id.            | `game::StateUtil::procDmgField` | 

---

### FLD_effparam

*Human Readable Name*: Field - Effect Parameters

Represents effects on a certain map during certain times of the day. Relevant game object: `fw::EffectManager::XefbParam`


| Column      | Type      | Description                                         | Handled by |
|-------------|-----------|-----------------------------------------------------|------------|
| `map`       | `string`  | [Map ID](#fld_maplist).                             | `game::BehaviorMap::getEffParams` | 
| `daytime_A` | `uint16`  | Daytime [Effect Preset ID](#fld_effpriset) A.       | `game::BehaviorMap::getEffParams` | 
| `daytime_B` | `uint16`  | Daytime [Effect Preset ID](#fld_effpriset) B.       | `game::BehaviorMap::getEffParams` | 
| `daytime_C` | `uint16`  | Daytime [Effect Preset ID](#fld_effpriset) C.       | `game::BehaviorMap::getEffParams` | 
| `evening_A` | `uint16`  | Evening [Effect Preset ID](#fld_effpriset) A.       | `game::BehaviorMap::getEffParams` | 
| `evening_B` | `uint16`  | Evening [Effect Preset ID](#fld_effpriset) B.       | `game::BehaviorMap::getEffParams` | 
| `evening_C` | `uint16`  | Evening [Effect Preset ID](#fld_effpriset) C.       | `game::BehaviorMap::getEffParams` | 
| `night_A`   | `uint16`  | Night [Effect Preset ID](#fld_effpriset) A.         | `game::BehaviorMap::getEffParams` | 
| `night_B`   | `uint16`  | Night [Effect Preset ID](#fld_effpriset) B.         | `game::BehaviorMap::getEffParams` | 
| `night_C`   | `uint16`  | Night [Effect Preset ID](#fld_effpriset) C.         | `game::BehaviorMap::getEffParams` | 
| `d_room`    | `float`   | Daytime "room" effect value.                        | `game::BehaviorMap::getEffParams` | 
| `e_room`    | `float`   | Evening "room" effect value.                        | `game::BehaviorMap::getEffParams` | 
| `n_room`    | `float`   | Night "room" effect value.                          | `game::BehaviorMap::getEffParams` | 
| `cl_room`   | `float`   | Room effect chroma                                  | `game::BehaviorMap::getEffParams` | 

---

### FLD_effpriset

*Human Readable Name*: Field - Effect Parameter Preset

Represents effect presets (used by [FLD_effparam](#fld_effparam)). Relevant game object: `fw::EffectManager::XefbParam`

!!! note

    Similar values in `eff/effset.ini`.

| Column     | Type     | Description                                         | Handled by |
|------------|----------|-----------------------------------------------------|------------|
| `add`      | `float`  | Effect addition.                                    | `game::BehaviorMap::getEffParams` | 
| `sub`      | `float`  | Effect subtraction.                                 | `game::BehaviorMap::getEffParams` | 
| `blm`      | `float`  | Bloom.                                              | `game::BehaviorMap::getEffParams` | 
| `blmhold`  | `float`  | Bloom Hold.                                         | `game::BehaviorMap::getEffParams` | 
| `amb`      | `float`  | Ambient.                                            | `game::BehaviorMap::getEffParams` | 
| `dir`      | `float`  | Unknown.                                            | `game::BehaviorMap::getEffParams` | 
| `amdir`    | `float`  | Ambient Direction.                                  | `game::BehaviorMap::getEffParams` | 
| `ambcl`    | `float`  | Ambient Chroma.                                     | `game::BehaviorMap::getEffParams` | 
| `dircl`    | `float`  | "dir" Chroma.                                       | `game::BehaviorMap::getEffParams` | 
| `addcurve` | `float`  | Add Curve.                                          | `game::BehaviorMap::getEffParams` | 

---

### FLD_Lndchglist

*Human Readable Name*: Field - Landmark Change List

Represents NPCs tied to landmarks.

| Column     | Type     | Description                                         | Handled by |
|------------|----------|-----------------------------------------------------|------------|
| `npc_id`   | `uint16` | [NPC ID](#fld_npclist).                             | `game::BdatFldLndchglist::getLndIdFromNpcId` | 
| `lnd_id`   | `uint16` | [Landmark ID](#landmarklist).                       | `game::BdatFldLndchglist::getLndIdFromNpcId` | 

---

### FLD_npclist

*Human Readable Name*: Field - NPC List

Master table for all the npcs in the game.

| Column       | Type       | Description                                         | Handled by |
|--------------|------------|-----------------------------------------------------|------------|
| `name`       | `MsTextId` | Localized Name of the NPC.                          | `game::BdatFldNpclist::getName` & more | 
| `mob_name`   | `uint16`   | [Mob Name ID](#MNU_name). Used for generic NPCs.    | `game::SeqScriptEvent::onSubtitle` & more | 
| `resource`   | `uint16`   | [Resource ID](#KP_list).                            | `game::SeqScriptEvent::onSubtitle` & more | 
| `rlt_meet`   | `uint16`   | NPC Meet ID - Used to determine whether this NPC was previously met. | `game::DataUtil::getNpcMeetIdByNpcID` & more | 
| `remove`     | `uint8`    | Unknown. Possibly unused. |  | 
| `shop_list`  | `uint8`    | [Shop List](#shoplist) for this NPC, if any.        |  | 
| `icon_type`  | `uint8`    | Icon Type.                                          | `game::NpcControl::NpcControl`, `game::BehaviorNpc::canDecideEvent` | 
| `rlt_face`   | `uint8`    | Face name, used for npc relate/affinity chart. Links to [JNL_relatelist](#jnl_relatelist). Must 3 in length. | `game::MenuPartsKizunagramWorldView::getFaceIndexFromFaceName` | 
| `rlt_posX`   | `int16`    | X Position on the relate/affinity chart. | `game::MenuPartsKizunagramWorldView::addRelateMarker` & more |
| `rlt_posY`   | `int16`    | Y Position on the relate/affinity chart. | `game::MenuPartsKizunagramWorldView::addRelateMarker` & more |
| `rlt_texture`| `uint16`   | Texture for the relate/affinity chart. Links to [SYS_filelist](#sys_filelist) & [SYS_filelist_ex](#sys_filelist_ex) | `game::MenuGameDataNpc::getFaceIconIndex` |
| `rlt_lnd`    | `uint16`   | [Landmark ID](#landmarklist) for the relate/affinity chart. | `game::MenuItemIdExchangeListEnumerable::create` & more |
| `rlt_sex`    | `uint16`   | Sex type of the NPC for the relate/affinity chart. | |
| `range_s`    | `uint8`    | Hour range start in which this NPC appears. | `game::MenuPartsKizunagramNpcProfile::setupNpcProfileFromNpcId` |
| `range_e`    | `uint8`    | Hour range end after which NPC disspears. | `game::MenuPartsKizunagramNpcProfile::setupNpcProfileFromNpcId` |
| `rlt_job`    | `MsTextId` | Localized job name for the relate/affinity chart. | `game::MenuPartsKizunagramNpcProfile::setupNpcProfileFromNpcId` |
| `size`       | `uint8`    | Unknown. Possibly unused. |  |
| `scale`      | `uint8`    | Unknown. Possibly unused. |  |
| `family`     | `uint8`    | Unknown. Possibly unused. |  |
| `move_speed` | `uint8`    | Move speed of the NPC in kph. |  |
| `autotalk1`  | `uint8`    | ID of [autotalk list](#autotalklist) #1. | `game::BdatFldNpclist::autotalk1` & `game::GimmickNpc::updateAutoTalkCondition` |
| `autotalk2`  | `uint8`    | ID of [autotalk list](#autotalklist) #2. | `game::BdatFldNpclist::autotalk2` & `game::GimmickNpc::updateAutoTalkCondition` |
| `autotalk3`  | `uint8`    | ID of [autotalk list](#autotalklist) #3. | `game::BdatFldNpclist::autotalk3` & `game::GimmickNpc::updateAutoTalkCondition` |
| `autotalk4`  | `uint8`    | ID of [autotalk list](#autotalklist) #4. | `game::BdatFldNpclist::autotalk4` & `game::GimmickNpc::updateAutoTalkCondition` |
| `autotalk5`  | `uint8`    | ID of [autotalk list](#autotalklist) #5. | `game::BdatFldNpclist::autotalk5` & `game::GimmickNpc::updateAutoTalkCondition` |
| `autotalk6`  | `uint8`    | ID of [autotalk list](#autotalklist) #6. | `game::BdatFldNpclist::autotalk6` & `game::GimmickNpc::updateAutoTalkCondition` |
| `exc_talk_id`| `uint8`    | Localized text when trading with a NPC. Points to [extalklist](#extalklist) | `game::BehaviorNpc::setupForLoaded` |
| `exc_id1`    | `uint8`    | Item [trading/exchange list](#extalklist) when reputation is level 1. | `game::MenuItemIdExchangeListEnumerable::create` |
| `exc_id2`    | `uint8`    | Item [trading/exchange list](#extalklist) when reputation is level 2. | `game::MenuItemIdExchangeListEnumerable::create` |
| `exc_id3`    | `uint8`    | Item [trading/exchange list](#extalklist) when reputation is level 3. | `game::MenuItemIdExchangeListEnumerable::create` |
| `exc_id4`    | `uint8`    | Item [trading/exchange list](#extalklist) when reputation is level 4. | `game::MenuItemIdExchangeListEnumerable::create` |
| `exc_id5`    | `uint8`    | Item [trading/exchange list](#extalklist) when reputation is level 5. | `game::MenuItemIdExchangeListEnumerable::create` |

---

### FLD_maplist

*Human Readable Name*: Field - Map List

Master table for all the maps in the game.

| Column             | Type           | Description              | Handled by |
|--------------------|----------------|--------------------------|------------|
| `name`             | `MsTextId`     | Name of the map.         |
| `id_name`          | `string`       | Internal id of the map.  |
| `resource`         | `string`       | Resource name. Used for getting the files associated to this map i.e `menu/minimap/...` or `map/...`. |
| `ene_disp_r`       | `uint8`        | Unknown % chance for enemy spawning. |
| `ene_release_r`    | `uint8`        | Unknown % chance for enemy spawning. |
| `ene_release_h`    | `uint8`        | Unknown % chance for enemy spawning. |
| `npc_release_r`    | `uint8`        | Unused. |
| `bg_image`         | `MsTextId`     | Background image name for this map for menus, unused in XB1DE.  |
| `map_sflag`        | `uint16`       | Scenario flags. Used to determine whether the map is unlocked depending on the current save scenario flags. | `game::MenuGameDataMapIdEnumerable::isUnlockedMap` |
| `map_fileID`       | `uint16`       | [SYS_filelist ID](#sys_filelist). Responsible for the preview image in the 'Area Map' menu. | `game::MenuGameDataMap::getMapCaptureImageFileName`|
| `map_caption`      | `MsTextId`     | Localized caption for the map in the 'Area Map' menu. | `game::MenuGameDataMap::getMapDescText`  |
| `minimap_rate`     | `uint8`        | Full map view scale. |
| `minimap_origin`   | `uint16`       | Origin position of the map. Appears unused in XC1DE. |
| `minimap_painx`    | `uint16`       | Unknown. Appears unused in XC1DE. |
| `minimap_painy`    | `uint16`       | Unknown. Appears unused in XC1DE. |
| `minimap_x`        | `uint16`       | Unknown. Appears unused in XC1DE. |
| `minimap_y`        | `uint16`       | Unknown. Appears unused in XC1DE. |
| `morning_h`        | `uint8`        | Hour of the day which is considered morning. | `game::Clock::update` |
| `morning_m`        | `uint8`        | Minute of the day which is considered morning. | `game::Clock::update` |
| `daytime_h`        | `uint8`        | Hour of the day which is considered daytime. | `game::Clock::update` |
| `daytime_m`        | `uint8`        | Minute of the day which is considered daytime. | `game::Clock::update` |
| `evening_h`        | `uint8`        | Hour of the day which is considered evening. | `game::Clock::update` |
| `evening_m`        | `uint8`        | Minute of the day which is considered evening. | `game::Clock::update` |
| `night_h`          | `uint8`        | Hour of the day which is considered night. | `game::Clock::update` |
| `night_m`          | `uint8`        | Minute of the day which is considered night. | `game::Clock::update` |
| `index`            | `uint8`        | Display index in the 'Area Map'. The list is sorted using this. |
| `wa_type`          | `uint8`        | Data A. Weather type. | `game::Weather::initAreaDataA` | 
| `wa_pop_rate`      | `uint8`        | Data A. Chance in % for this weather to start. | `game::Weather::initAreaDataA` | 
| `wa_end_time`      | `uint8`        | Data A. Time before the weather ends.  | `game::Weather::initAreaDataA` | 
| `wa_time`          | `int16`        | Data A. Unknown flags.  | `game::Weather::initAreaDataA` | 
| `wa_size_X`        | `int16`        | Data A. Unknown.  | `game::Weather::initAreaDataA` | 
| `wa_size_Y`        | `int16`        | Data A. Unknown.  | `game::Weather::initAreaDataA` | 
| `wa_size_Z`        | `int16`        | Data A. Unknown.  | `game::Weather::initAreaDataA` | 
| `wa_radius`        | `int16`        | Data A. Unknown.  | `game::Weather::initAreaDataA` | 
| `wb_type`          | `uint8`        | Data B. Weather type. | `game::Weather::initAreaDataB` | 
| `wb_pop_rate`      | `uint8`        | Data B. Chance in % for this weather to start. | `game::Weather::initAreaDataB` | 
| `wb_end_time`      | `uint8`        | Data B. Time before the weather ends.  | `game::Weather::initAreaDataB` | 
| `wb_time`          | `int16`        | Data B. Unknown flags.  | `game::Weather::initAreaDataB` | 
| `wb_size_X`        | `int16`        | Data B. Unknown.  | `game::Weather::initAreaDataB` | 
| `wb_size_Y`        | `int16`        | Data B. Unknown.  | `game::Weather::initAreaDataB` | 
| `wb_size_Z`        | `int16`        | Data B. Unknown.  | `game::Weather::initAreaDataB` | 
| `wb_radius`        | `int16`        | Data B. Unknown.  | `game::Weather::initAreaDataB` | 
| `e_repoptime`      | `uint8`        | Time before enemy respawns in seconds. | `game::GimmickEnemyUpdater::setupRepop` |
| `wind_M`           | `uint8`        | Wind during morning. | `game::Weather::updateWeatherData` |
| `wind_D`           | `uint8`        | Wind during daytime. | `game::Weather::updateWeatherData` |
| `wind_E`           | `uint8`        | Wind during evening. | `game::Weather::updateWeatherData` |
| `wind_N`           | `uint8`        | Wind during night. | `game::Weather::updateWeatherData` |
| `wind_WA`          | `uint8`        | Wind during weather A. | `game::Weather::initAreaDataA` |
| `wind_WB`          | `uint8`        | Wind during weather B. | `game::Weather::initAreaDataB` |
| `a_S_FLG_MIN`      | `uint16`       | Scenario flag min condition for weather A. | `game::Weather::initAreaDataA` |
| `a_S_FLG_MAX`      | `uint16`       | Scenario flag max condition for weather A. | `game::Weather::initAreaDataA` |
| `b_S_FLG_MIN`      | `uint16`       | Scenario flag max condition for weather B. | `game::Weather::initAreaDataB` |
| `b_S_FLG_MAX`      | `uint16`       | Scenario flag max condition for weather B. | `game::Weather::initAreaDataB` |
| `mapATR`           | `uint8`        | Unknown bit flags. Data A uses flag 0x04 while B uses 0x10. | `game::Weather::updateWeatherData` |
| `minimaplt_x`      | `int16`        | Unknown. | `game::MenuPartsAreaMapTopView::MenuPartsAreaMapTopView` & more |
| `minimaplt_z`      | `int16`        | Unknown. | `game::MenuPartsAreaMapTopView::MenuPartsAreaMapTopView` & more |
| `minimaprb_x`      | `int16`        | Unknown. | `game::MenuPartsAreaMapTopView::MenuPartsAreaMapTopView` |
| `minimaprb_z`      | `int16`        | Unknown. | `game::MenuPartsAreaMapTopView::MenuPartsAreaMapTopView` |
| `mapimagesize_x`   | `uint16`       | Unknown. Appears unused in XC1DE. |  |
| `mapimagesize_y`   | `uint16`       | Unknown. Appears unused in XC1DE. |  |
| `minimap_cnt`      | `uint8`        | Number of floors in this map. Appears unused in XC1DE. | |

!!! note
    Many future connected checks are done through checking the id being above or equal 25.

---

### FLD_pointlist

*Human Readable Name*: Field - Point List

`MsTextId` linked to `FLD_pointlist_ms`.

List of all the triggers on the map fields. Heart to Hearts, crystals & everything else interactable.

| Column             | Type           | Description                | Handled by |
|--------------------|----------------|----------------------------|------------|
| `name`             | `MsTextId`     | Name of the trigger point. | `game::TriggerControl::createAsPoint`, `game::SeqField::checkEnableKizunaTalkPoint` | 
| `icon_type`        | `uint8`        | Display icon type. Up to 0x15, every type has a different priority.  |

---

### FLD_tboxlist

*Human Readable Name*: Field - Treasure Box List

List of all the non-dropped treasure "boxes"/chests on the map fields.

| Column             | Type           | Description                | Handled by |
|--------------------|----------------|----------------------------|------------|
| `gimID`            | `uint16`       | Gimmick ID. | `game::GimmickTrigger::openTreasureBox` | 
| `itm1ID`           | `uint16`       | 1st [Item](#itm_itemlist) in the treasure box. | `game::SeqTreasureBox::onEnter` | 
| `itm2ID`           | `uint16`       | 2nd [Item](#itm_itemlist) in the treasure box. | `game::SeqTreasureBox::onEnter` | 
| `itm3ID`           | `uint16`       | 3rd [Item](#itm_itemlist) in the treasure box. | `game::SeqTreasureBox::onEnter` | 
| `itm4ID`           | `uint16`       | 4th [Item](#itm_itemlist) in the treasure box. | `game::SeqTreasureBox::onEnter` | 

---

### FLD_valpoplist

*Human Readable Name*: Field - Valuable Item Pop List

List of all the important "red" bulb items on the map fields.

| Column             | Type           | Description                | Handled by |
|--------------------|----------------|----------------------------|------------|
| `mapID`            | `uint8`        | [Map ID](#fld_maplist). | `game::GimmickMapItem::setupValuable` | 
| `SFLG_MIN`         | `uint16`       | Scenario flag min condition to appear. | `game::GimmickMapItem::setupValuable` | 
| `SFLG_MAX`         | `uint16`       | Scenario flag max condition to appear. | `game::GimmickMapItem::setupValuable` | 
| `questID`          | `uint16`       | [Quest ID](#JNL_quest) | `game::GimmickMapItem::setupValuable` | 
| `quest_STFLG`      | `uint8`        | Unknown quest flags. | `game::GimmickMapItem::setupValuable` | 
| `popTime`          | `uint8`        | Time to spawn. | `game::GimmickMapItem::setupValuable` | 
| `wtrType`          | `uint8`        | Required weather to spawn. | `game::GimmickMapItem::setupValuable` | 
| `posX`             | `int16`        | Position X on the map field. | `game::GimmickMapItem::setupValuable` | 
| `posY`             | `int16`        | Position Y on the map field. | `game::GimmickMapItem::setupValuable` | 
| `posZ`             | `int16`        | Position Z on the map field. | `game::GimmickMapItem::setupValuable` | 
| `Radius`           | `uint16`       | Item collision radius. | `game::GimmickMapItem::setupValuable` | 
| `snap`             | `uint8`        | Whether the item snaps. | `game::GimmickMapItem::setupValuable` | 
| `popNum`           | `uint8`        | Number of items. | `game::GimmickMapItem::setupValuable` | 
| `itm1ID`           | `uint16`       | Actual [Item ID](#itm_itemlist). | `game::GimmickMapItem::setupValuable` | 

---

## File Resources

### KP_list

*Human Readable Name*: KP (Unknown) List

List of resource groups.

| Column             | Type           | Description                | Handled by |
|--------------------|----------------|----------------------------|------------|
| `model`            | `string`       | Model File Name. Maps to `chr/` where the first two letters is a sub-dir. | `game::NpcControl::initialize`, `game::ResNpcBinder::bind`, `game::BehaviorNpc::setupForLoaded` & more  | 
| `motion`           | `string`       | Motion File Name. Maps to `chr/obj/`. | `game::ResMobjBinder::bind` | 
| `action`           | `string`       | Action File Name. Maps to `chr/obj/`. | `game::ResMobjBinder::bind` | 
| `effect`           | `string`       | Effect File Name. Maps to `eff/` where the first two letters is a sub-dir. | `game::ResMobjBinder::bind` | 
| `sound`            | `string`       | Sound File Name. Will be hashed, see note below | `game::SoundUtil::playEnemySE`, `game::SoundUtil::playNpcVoice`, `game::SoundUtil::playNoponArchsageVoice`, `game::VoiceManager::playVoice` | 

!!! note "Hashing"

    ```c++
    // fw::SoundManager::playVoiceNpc - 0x7100066460 - 1.1.2
    mm::mtl::FixStr<32>::format(str, "%s_SE_%03d", sound_file_name, unk); 
    mm::mtl::FixStr<256>::format(final_str, "%s_%lu", str, this->LastID);
    int id = AK::SoundEngine::GetIDFromString(final_str); // Audiokinetic Wwise
    // this->LastID++
    ```

---

## Menu Localization

### MNU_battle

*Human Readable Name*: **Menu - Battle UI**

`MsTextId` linked to `MNU_battle_ms`.

Links battle UI components to their localized texts (and optionally, their captions - i.e Attack = "Initiate a Battle").

Many elements are naturally hardcoded to specific ids.

| Column   | Type      | Description                          | Handled by |
|----------|-----------|--------------------------------------|------------|
| `name`   | `MsTextId`| Localized component name.            | Too many.  |
| `help`   | `MsTextId`| Localized Art help/overview/caption/.| `game::MenuGameDataPcArts::getArtsOverviewText` | 

### MNU_bonus_exp

*Human Readable Name*: **Menu - Bonus Exp/Expert Mode UI**

`MsTextId` linked to `MNU_bonus_exp_ms`.

Links expert mode menu UI components to their localized texts.

Many elements are naturally hardcoded to specific ids.

| Column   | Type      | Description                | Handled by |
|----------|-----------|----------------------------|------------|
| `name`   | `MsTextId`| Localized component name.  | `game::MenuPartsBonusExpPcSelecterItem::setup`, `game::MenuPartsBonusExpPcSelecterItem::setLevel`, `game::MenuPartsBonusExpOnOffDialog::MenuPartsBonusExpOnOffDialog` & more  |

---

### MNU_col6

*Human Readable Name*: **Menu - Colony 6 UI**

`MsTextId` linked to `MNU_col6_ms`.

Links Colony 6 Reconstruction UI components to their localized texts. (and optionally, their captions).

Many elements are naturally hardcoded to specific ids.

| Column   | Type      | Description                          | Handled by |
|----------|-----------|--------------------------------------|------------|
| `name`   | `MsTextId`| Localized component name.            | Too many. Classes: `MenuPartsReviveColony6Util` & `MenuSeqReviveColony6LevelUp` |
| `help`   | `MsTextId`| Caption/overview.                    |            | 

---

### MNU_collect

*Human Readable Name*: **Menu - Collectopedia UI**

`MsTextId` linked to `MNU_collect_ms`.

Links Collectopedia UI components to their localized texts. (and optionally, their captions).

Many elements are naturally hardcoded to specific ids.

| Column   | Type      | Description                          | Handled by |
|----------|-----------|--------------------------------------|------------|
| `name`   | `MsTextId`| Localized component name.            | `game::MenuPartsCollepedia::updateDisplayCollectPage` |
| `help`   | `MsTextId`| Caption/overview.                    |            | 

---

### MNU_crystal

*Human Readable Name*: **Menu - Crystal/Gem Crafting UI**

`MsTextId` linked to `MNU_collect_ms`.

Links Gem Crafting UI components to their localized texts.

Many elements are naturally hardcoded to specific ids.

| Column   | Type      | Description                          | Handled by |
|----------|-----------|--------------------------------------|------------|
| `info`   | `MsTextId`| Localized component name.            |            |

### MNU_game_option_category

*Human Readable Name*: **Menu - Game Option Categories**

`MsTextId` linked to `MNU_main_ms`.

Links game setting category components to their localized texts.

| Column     | Type      | Description                | Handled by |
|------------|-----------|----------------------------|------------|
| `category` | `uint16`  | Category Type.     | `game::MenuGameDataOptionCategoryEnumable::create` |
| `priority` | `uint16`  | Priority/Order. 0 is not shown.    | `game::MenuGameDataOptionCategoryEnumable::create` | 
| `name`     | `MsTextId`| Localized name.    | `game::MenuGameDataOptionCategoryEnumable::create` | 
| `help`     | `MsTextId`| Localized caption. | `game::MenuGameDataOptionCategoryEnumable::create` | 

### MNU_event_theater_txt

*Human Readable Name*: **Menu - Event Theater Text**

`MsTextId` linked to `MNU_event_theater_txt`.

Links Event Theater UI components to their localized texts.


| Column           | Type      | Description                          | Handled by |
|------------------|-----------|--------------------------------------|------------|
| `name`           | `MsTextId`| Localized Name of the location. |  |

---

### MNU_item

*Human Readable Name*: **Menu - Item UI**

`MsTextId` linked to `MNU_item_ms`.

Links inventory/equipment menu UI components to their localized texts.

| Column     | Type      | Description                | Handled by |
|------------|-----------|----------------------------|------------|
| `name`     | `MsTextId`| Localized name.    | `game::MenuGameDataItem::getArmTypeMsText` | 
| `help`     | `MsTextId`| Localized caption. |  | 

---

### MNU_main

*Human Readable Name*: **Menu - Main UI**

`MsTextId` linked to `MNU_main_ms`.

Links main UI components to their localized texts.

| Column     | Type      | Description                | Handled by |
|------------|-----------|----------------------------|------------|
| `name`     | `MsTextId`| Localized name.    |  | 
| `help`     | `MsTextId`| Localized caption. |  | 


---

### MNU_map

*Human Readable Name*: **Menu - Map UI**

`MsTextId` linked to `MNU_map_ms`.

Links map UI components to their localized texts.

| Column     | Type      | Description                | Handled by |
|------------|-----------|----------------------------|------------|
| `name`     | `MsTextId`| Localized name.    |  | 
| `help`     | `MsTextId`| Localized caption. |  | 

---

### MNU_nopon

*Human Readable Name*: **Menu - Nopon UI**

`MsTextId` linked to `MNU_nopon_ms`.

**For Future Connected**. Links Nopon Ponspectors UI components to their localized texts.

| Column     | Type      | Description                | Handled by |
|------------|-----------|----------------------------|------------|
| `name`     | `MsTextId`| Localized name.    |  | 


---

### MNU_noponger

*Human Readable Name*: **Menu - Noponger**

**For Future Connected**. Links Nopon NPC IDs to their playable character ID.

| Column         | Type      | Description                | Handled by |
|----------------|-----------|----------------------------|------------|
| `npc_id`       | `uint16`  | [NPC ID](#fld_npclist).    |  | 
| `noponger_idx` | `uint8`   | [Playable Character ID](#btl_pclist) (15 + value). | `game::MenuGameDataMap::isVisibleNopongerNpcIcon` |

---

### MNU_party

*Human Readable Name*: **Menu - Nopon UI**

`MsTextId` linked to `MNU_party_ms`.

Links Party Change UI components to their localized texts.

| Column     | Type      | Description                | Handled by |
|------------|-----------|----------------------------|------------|
| `name`     | `MsTextId`| Localized name.            |  | 
| `help`     | `MsTextId`| Localized caption.         |  | 

---

### MNU_passive

*Human Readable Name*: **Menu - Passive Skill/Tree UI**

`MsTextId` linked to `MNU_passive_ms`.

Links Skill Tree UI components to their localized texts.

| Column     | Type      | Description                | Handled by |
|------------|-----------|----------------------------|------------|
| `name`     | `MsTextId`| Localized name.            |  | 

---

### MNU_quest

*Human Readable Name*: **Menu - Quest UI**

`MsTextId` linked to `MNU_quest_ms`.

Links Quest Menu UI components to their localized texts.

| Column     | Type      | Description                | Handled by |
|------------|-----------|----------------------------|------------|
| `name`     | `MsTextId`| Localized name.            |  | 

---

### MNU_relate

*Human Readable Name*: **Menu - Relate/Affinity Chart UI**

`MsTextId` linked to `MNU_relate_ms`.

Links Affinity Chart menu UI components to their localized texts.

| Column     | Type      | Description                | Handled by |
|------------|-----------|----------------------------|------------|
| `name`     | `MsTextId`| Localized name.            |  | 
| `help`     | `MsTextId`| Localized caption.         |  | 

---

### MNU_saveload_scenario

*Human Readable Name*: **Menu - Save/Load Menu UI**

`MsTextId` linked to `MNU_saveload_scenario_ms`.

Links Save/Load Menu UI components to their localized texts.

| Column     | Type      | Description                | Handled by |
|------------|-----------|----------------------------|------------|
| `flag`     | `uint16`  | Scenario Flag target.      |  | 
| `help`     | `MsTextId`| Localized name.            |  | 

---

### MNU_shop

*Human Readable Name*: **Menu - Shop Menu UI**

`MsTextId` linked to `MNU_shop_ms`.

Links Shop Menu UI components to their localized texts.

| Column     | Type      | Description                | Handled by |
|------------|-----------|----------------------------|------------|
| `name`     | `MsTextId`| Localized name.            |  | 
| `help`     | `MsTextId`| Localized name.            |  | 

---

### MNU_sysmes

*Human Readable Name*: **Menu - System Messages UI**

`MsTextId` linked to `MNU_sysmes_ms`.

Links System Messages UI components to their localized texts.

| Column     | Type      | Description                | Handled by |
|------------|-----------|----------------------------|------------|
| `name`     | `MsTextId`| Localized name.            |  | 
| `help`     | `MsTextId`| Localized name.            |  | 

---

### MNU_title

*Human Readable Name*: **Menu - Main Title UI**

`MsTextId` linked to `MNU_title_ms`.

Links Title Menu UI components to their localized texts.

| Column     | Type      | Description                | Handled by |
|------------|-----------|----------------------------|------------|
| `name`     | `MsTextId`| Localized name.            |  | 

---


### MNU_update

*Human Readable Name*: **Menu - Update/Notification UI**

`MsTextId` linked to `MNU_update_ms`.

Links Update/Notification Popup UI components to their localized texts.

| Column     | Type      | Description                | Handled by |
|------------|-----------|----------------------------|------------|
| `name`     | `MsTextId`| Localized name.            |  | 

---

## Menu Handling

### MNU_artsshop

*Human Readable Name*: **Menu - Arts Shop**

Defines arts available in the Arts/Manual Shop (XC1DE Future Connected). 

| Column   | Type      | Description                | Handled by |
|----------|-----------|----------------------------|------------|
| `item`   | `uint16`  | [Item ID](#itm_itemlist).  | `game::MenuSeqArtsshop::ArtsshopItemParam::getArtsId` |
| `price`  | `uint8`   | Price in art coins.        | `game::MenuSeqArtsshop::getSelectedItemPrice` | 
| `index`  | `uint8`   | Order index.               | `game::MenuSeqArtsshop::rebuildItemListFromPcID` | 
| `sflg`   | `uint16`  | Scenario flag required for this item to be available. | `game::MenuSeqArtsshop::ArtsshopItemParam::getScenarioFlag` | 

### MNU_dialog

*Human Readable Name*: **Menu - Crystal/Gem Crafting UI**

`MsTextId` depends on the `source` column.

List of all dialog/prompt parameters.

Many elements are naturally hardcoded to specific ids.

| Column           | Type          | Description                          | Handled by |
|------------------|---------------|--------------------------------------|------------|
| `type`           | `uint8`       | Dialog Type. 1 = Basic Dialog, 2 = Selection Dialog. | `game::MenuMnuDialog::getType` |
| `source`         | `uint8`       | Source bdat.                         | `game::MenuMnuDialog::getSource`, `game::MenuMnuDialog::getMsText` |
| `title`          | `MsTextId`    | Localized Dialog title.              | `game::MenuMnuDialog::getTitleText` |
| `message`        | `MsTextId`    | Localized Dialog message.            | `game::MenuMnuDialog::getMessage`   |
| `default_index`  | `uint8`       | Default selection index (when type is 2). | `game::MenuMnuDialog::getMessage`   |
| `cancel_key`     | `uint8`       | Unknown. Controls cancelling.        | `game::MenuMnuDialog::getCancelResult`   |
| `select`         | `MsTextId[]`  | Localized selection messages as a string representing the selections (when type is 2). | `game::MenuMnuDialog::getSelectTextCount`   |
| `open_sound_id`  | `uint16[]`     | Sound to play when the dialog is opened. | `game::MenuMnuDialog::getOpenSoundId`   |
| `sound_id`       | `uint16`       | Sound to play when a specific selection is chosen. | `game::MenuMnuDialog::getSoundId`   
| `cancel_sound_id`| `uint16`       | Sound to play when the dialog is closed. | `game::MenuMnuDialog::getCancelSoundId` |


!!! tip "`source`"

    * 1: `MNU_main`
    * 2: `MNU_main_ms`
    * 3: `MNU_sysmes`
    * 4: `MNU_sysmes_ms`
    * 5: `MNU_shop`
    * 6: `MNU_shop_ms`
    * 7: `MNU_item`
    * 8: `MNU_passive`
    * 9: `MNU_bonus_exp_ms`

---

### MNU_event_location

*Human Readable Name*: **Menu - Event Location**

`MsTextId` linked to `FLD_maplist_ms`.

Handles the main area/region location menu.

| Column           | Type      | Description                          | Handled by |
|------------------|-----------|--------------------------------------|------------|
| `name`           | `MsTextId`| Localized Name of the location. | `game::MenuMnuDialog::getType` |
| `old_file_name`  | `string`  | Unknown. Old effect file name. (maps to `eff\ev\ev`). |  |
| `map_id`         | `uint8`   | [Map ID](#fld_maplist).              | `game::MenuPartsAreaMapList::setMapIdDesc` |
| `wait`           | `uint16`  | Wait time (ms). Possibly unused.     | |
| `is_bionic`      | `uint8`   | Whether this location is on Bionis (and will display as such), otherwise Mechonis. Will use layer group `PointerBionis_mc` or `PointerMechonis_mc` from `mnu050_cont01.wilay` | ` game::MenuPartsAreaMapList::setMapIdDesc`  |
| `point_idx`      | `uint8`   | Point on the bionis/mechonis. Will start layer action `lay%02u`.   | `game::MenuPartsAreaMapList::setMapIdDesc`   |
| `event_name`     | `string`  | Used as key for searching.   | |

---

### MNU_event_logo

*Human Readable Name*: **Menu - Event Logo**

List of logo overlays for events i.e Xenoblade Logo.

| Column           | Type      | Description                          | Handled by |
|------------------|-----------|--------------------------------------|------------|
| `old_file_name`  | `string`  | Unknown. Old effect file name. (maps to `eff\ev\ev`). |  |
| `image_name`     | `string`  | Layer Logo image name (from `menu/image`). | `game::MenuSeqEventLogoAction::getLayerLogoImageName` |
| `wait`           | `uint16`  | Wait time (ms). Possibly unused.     | |
| `event_name`     | `string`  | Used as key for searching.   | |

---

### MNU_event_telop

*Human Readable Name*: **Menu - Event Captions**

`MsTextId` linked to `MNU_event_telop_ms`.

List of text overlays for events i.e "One Month Ago".

| Column           | Type      | Description                          | Handled by |
|------------------|-----------|--------------------------------------|------------|
| `name`           | `MsTextId`| Localized Name of the location. | `game::MenuMnuDialog::getType` |
| `old_file_name`  | `string`  | Unknown. Old effect file name. (maps to `eff\ev\ev`). |  |
| `wait`           | `uint16`  | Wait time (ms). Possibly unused.     | |
| `event_name`     | `string`  | Used as key for searching.   | |

---


### MNU_filter

*Human Readable Name*: **Menu - Filter**

`MsTextId` linked to `MNU_filter_ms`.

Handles menu filtering (i.e gear). 


| Column          | Type      | Description                          | Handled by |
|-----------------|-----------|--------------------------------------|------------|
| `category`      | `uint8`   | Category type.                       | `game::MenuFilterSortUtil::getListImpl` |
| `name`          | `MsTextId`| Localized Name of the filtering type.| `game::MenuFilterSortUtil::getListImpl` |
| `index`         | `uint8`   | Order index (?).                     | `game::MenuFilterSortUtil::getListImpl` |
| `conf_type`     | `uint8`   | Config Type. 1-5.                    | `game::MenuFilterSortUtil::getListImpl` |
| `conf_value`    | `uint16`  | Conf data depending on config type.  | `game::MenuFilterSortUtil::getListImpl` |
| `filter_type`   | `uint8`   | Filter Type. 0-11.                   | `game::MenuFilterSortUtil::getFilterType` |
| `filter_value`  | `uint8`   | Filter data depending on type.       | `game::MenuFilterSortUtil::getFilterValue` |
     
??? tip "category"

    * 0 = All
    * 1 = Clothes
    * 2 = Body Armor
    * 3 = Key Items
    * 4 = Arts
    * 5 = Gems
    * 7 = Collectibles
    * 9 = Quest List
    * 10 = Tutorial
    * 11 = Event Theater (?)

??? tip "conf_type"

    * 1 = Equal to `conf_value`?
    * 2 = `conf_value` is map ID for `landmarklist`
    * 3 = Unknown. May be related to playable character being in party as per `game::DataUtil::getPcJoin`
    * 4 = Unknown. `game::DataUtil::isRevivePC08` - Fiora Revive
    * 5 = Different than `conf_value`?

??? tip "filter_type"

    * 0 = Unknown
    * 1 = `game::MenuGameDataItem::getSlotSize` (`ITM_wpnlist`->jwl_slot)
    * 2 = `game::MenuGameDataItem::getSlotSize && !game::MenuGameDataItem::getUniFlag` 
    * 3 = `game::MenuGameDataItem::getUniFlag` (`ITM_wpnlist`->uni_flag)
    * 4 = filter_value == `game::MenuGameDataItem::getArmType` (`ITM_equiplist`->arm_type)
    * 5 = `game::MenuGameDataItem::getArmType - 4 <= 9` (`ITM_equiplist`->arm_type)
    * 6 = `game::MenuGameDataItem::isQuestTarget || game::MenuGameDataItem::isVisionTarget`
    * 7 = `!game::DataUtil::isUsedArtsBook`
    * 8 = `game::DataUtil::isUsedArtsBook`
    * 9 = `filter_value` compared against `BTL_skilllist`->attach - `game::MenuGameDataItem::getAttach`
    * 10 = `filter_value` compared against `BTL_skilllist`->category - `game::MenuGameDataItem::getCategory`
    * 11 = `filter_value` compared against `ITM_collectlist`->type - `game::MenuGameDataItem::getCollectType`
---

### MNU_game_option_item

*Human Readable Name*: **Menu - Game Option Items**

`MsTextId` linked to `MNU_main_ms`.

Links game setting item components to their localized texts.

| Column          | Type         | Description                    | Handled by |
|-----------------|--------------|--------------------------------|------------|
| `option_id`     | `uint16`     | Option ID. No more than 0x2A.  | `game::MenuGameDataOption::startup` |
| `category`      | `uint16`     | [Option Category ID](#mnu_game_option_category). | `game::MenuGameDataOption::startup` | 
| `priority`      | `uint16`     | Priority/Order. 0 is not shown.   | `game::MenuGameDataOptionCategoryEnumable::create` | 
| `show_type`     | `uint16`     | Unknown. 0-3.      | `game::MenuGameDataOptionEnumable::create` | 
| `parent_id`     | `uint16`     | Parent Item ID. If specified, will display as a subgroup. | `game::MenuGameDataOption::getParentOptionId` | 
| `name`          | `MsTextId`   | Localized name.                  |  | 
| `help`          | `MsTextId`   | Localized caption.               |  | 
| `type`          | `MsTextId`   | Type of option.                  | `game::MenuGameDataOption::adjustData` | 
| `default_value` | `uint16`     | Default value (if slider).       | `game::MenuGameDataOption::adjustData` | 
| `min_value`     | `uint16`     | Min value (if slider).           | `game::MenuGameDataOption::adjustData` | 
| `max_value`     | `uint16`     | Max value (if slider).           | `game::MenuGameDataOption::adjustData` | 
| `partition`     | `uint16`     | Increment value per de/increase. | `game::MenuGameDataOption::adjustData` | 
| `select_value`  | `uint16[]`   | Value of each select option.     | `game::BdatMnuGameOptionItem::select_value` | 
| `select_name`   | `MsTextId[]` | Localized name of each select option. | `game::MenuGameDataOption::getSelectItemText` | 

??? tip "type"

    * 1 = Combo Box
    * 2 = Slider
    * 3 = Brightness Slider
---

### MNU_header_info

*Human Readable Name*: **Menu - Header Info**

`MsTextId` linked to `MNU_header_text_ms`.

Unknown.

| Column          | Type         | Description                    | Handled by |
|-----------------|--------------|--------------------------------|------------|
| `name`          | `MsTextId`   | Localized header name.         | `game::MenuPartsHeaderTitle::setTitleInfo` |
| `image_no`      | `uint8`      | Image Number.                  | `game::MenuPartsHeaderTitle::setTitleInfo` | 
| `image_sub_no`  | `uint8`      | Sub Image Number.              | `game::MenuPartsHeaderTitle::setTitleInfo` | 

`image_no` and `image_sub_no` are combined into a `%03d_%02d` layer action string, loaded from some `fonr_hi_mc` or `fonr_mc` layer.

---

### MNU_header_text

*Human Readable Name*: **Menu - Header Text**

`MsTextId` linked to `MNU_header_text_ms`.

Unknown.

| Column          | Type         | Description                    | Handled by |
|-----------------|--------------|--------------------------------|------------|
| `name`          | `MsTextId`   | Localized header name.         | `game::MenuPartsHeaderTitle::setTitleInfo` |

---

### MNU_kyeassign

*Human Readable Name*: **Menu - Key Assign**

`MsTextId` linked to `MNU_kyeassign_ms`.

Links key UI menu UI components to their localized texts.

Many elements are naturally hardcoded to specific ids.

| Column     | Type      | Description                | Handled by |
|------------|-----------|----------------------------|------------|
| `fileID_1` | `uint16`  | Appears unused.            |  | 
| `fileID_2` | `uint16`  | Appears unused.            |  | 
| `help`     | `MsTextId`| Localized caption.         | `game::MenuPartsHudGuideControl::applyGuideLayerItem`, `game::MenuPartsInfo::MenuPartsInfo`, `game::MenuPartsPlayAward::reloadList`, ` game::MenuPartsTrialPartyInfo::MenuPartsTrialPartyInfo` | 


---

### MNU_name

*Human Readable Name*: **Menu - Name UI**

`MsTextId` linked to `MNU_name_ms`.

Possibly unused (no references found)

| Column     | Type      | Description                | Handled by |
|------------|-----------|----------------------------|------------|
| `name`     | `MsTextId`| Localized name.    |  | 


---

### MNU_operation_guide

*Human Readable Name*: **Menu - Operation Guide UI**

`MsTextId` linked to `MNU_operation_guide_ms`.

Unused. Moved to `MNU_kyeassign`

| Column            | Type      | Description                | Handled by |
|-------------------|-----------|----------------------------|------------|
| `guide_icon_1`    | `uint8`   | Guide Icon 1.              | `game::BdatMnuOperationGuide::guide_icon1` | 
| `guide_text_1`    | `uint8`   | Guide Text 1.              | `game::BdatMnuOperationGuide::guide_text1` | 
| `guide_icon_2`    | `uint8`   | Guide Icon 2.              | `game::BdatMnuOperationGuide::guide_icon2` | 
| `guide_text_2`    | `uint8`   | Guide Text 2.              | `game::BdatMnuOperationGuide::guide_text2` | 
| `guide_icon_3`    | `uint8`   | Guide Icon 3.              | `game::BdatMnuOperationGuide::guide_icon3` | 
| `guide_text_3`    | `uint8`   | Guide Text 3.              | `game::BdatMnuOperationGuide::guide_text3` | 
| `guide_icon_4`    | `uint8`   | Guide Icon 4.              | `game::BdatMnuOperationGuide::guide_icon4` | 
| `guide_text_4`    | `uint8`   | Guide Text 4.              | `game::BdatMnuOperationGuide::guide_text4` | 
| `guide_icon_5`    | `uint8`   | Guide Icon 5.              | `game::BdatMnuOperationGuide::guide_icon5` | 
| `guide_text_5`    | `uint8`   | Guide Text 5.              | `game::BdatMnuOperationGuide::guide_text5` | 
| `guide_icon_6`    | `uint8`   | Guide Icon 6.              | `game::BdatMnuOperationGuide::guide_icon6` | 
| `guide_text_6`    | `uint8`   | Guide Text 6.              | `game::BdatMnuOperationGuide::guide_text6` | 
| `guide_icon_7`    | `uint8`   | Guide Icon 7.              | `game::BdatMnuOperationGuide::guide_icon7` | 
| `guide_text_7`    | `uint8`   | Guide Text 7.              | `game::BdatMnuOperationGuide::guide_text7` | 
| `guide_icon_8`    | `uint8`   | Guide Icon 8.              | `game::BdatMnuOperationGuide::guide_icon8` | 
| `guide_text_8`    | `uint8`   | Guide Text 8.              | `game::BdatMnuOperationGuide::guide_text8` | 
| `ex_guide_icon_1` | `uint8`   | Extra Guide Text 1.        | `game::BdatMnuOperationGuide::ex_guide_icon1` | 
| `ex_guide_text_1` | `uint8`   | Extra Guide Icon 1.        | `game::BdatMnuOperationGuide::ex_guide_text1` | 
| `ex_guide_icon_2` | `uint8`   | Extra Guide Text 2.        | `game::BdatMnuOperationGuide::ex_guide_icon2` | 
| `ex_guide_text_2` | `uint8`   | Extra Guide Icon 2.        | `game::BdatMnuOperationGuide::ex_guide_text2` | 

---

### MNU_quest_task_message

*Human Readable Name*: **Menu - Quest Popup UI**

`MsTextId` linked to `MNU_quest_task_message_ms`.

Handles text for branching quests.

| Column              | Type      | Description                   | Handled by |
|---------------------|-----------|-------------------------------|------------|
| `quest_id`          | `uint16`  | [Quest ID](#jnl_quest).       |  | 
| `prog_a`            | `MsTextId`| Localized Quest Branch A Name | `game::BdatMnuQuestTaskMessage::getProgMsText` | 
| `prog_b`            | `MsTextId`| Localized Quest Branch B Name | `game::BdatMnuQuestTaskMessage::getProgMsText` | 
| `prog_a_target`     | `uint16`  | Localized Branch A Target.    | `game::BdatMnuQuestTaskMessage::getProgTargetMsText` | 
| `prog_b_target`     | `uint16`  | Localized Branch B Target.    | `game::BdatMnuQuestTaskMessage::getProgTargetMsText` | 
| `prog_a_target_max` | `uint8`   | Branch A Target Max.          | `game::BdatMnuQuestTaskMessage::getProgTargetMax` | 
| `prog_b_target_max` | `uint8`   | Branch B Target Max.          | `game::BdatMnuQuestTaskMessage::getProgTargetMax` | 

---

### MNU_sort

TODO

---

### MNU_ColorList

*Human Readable Name*: **Menu - Color List**

Defines colors for use with the menu UI. Depends on [MNU_EventTheater_kzn](#MNU_EventTheater_kzn)->col6_setting.

| Column   | Type      | Description                | Handled by |
|----------|-----------|----------------------------|------------|
| `name`   | `string`  | UI Component Name. | `game::UIDataLibrary::setupColorList` |
| `col_r`  | `uint8`   | Red Color. | `game::UIDataLibrary::setupColorList` | 
| `col_g`  | `uint8`   | Green Color. | `game::UIDataLibrary::setupColorList` | 
| `col_b`  | `uint8`   | Blue Color. | `game::UIDataLibrary::setupColorList` | 

---

### MNU_EventTheater_col6

*Human Readable Name*: **Menu - Event Theater - Colony 6**

`MsTextId` linked to `pc_arts` (may be a mistake)

Unknown. Possibly colony 6 parameters for when playing event theater?

| Column      | Type      | Description                | Handled by |
|-------------|-----------|----------------------------|------------|
| `house`     | `uint8`   | Housing level.   | `game::MenuSeqEventTheater::playEvent` | 
| `business`  | `uint8`   | Commerce level. | `game::MenuSeqEventTheater::playEvent` | 
| `industry`  | `uint8`   | Unknown.  | `game::MenuSeqEventTheater::playEvent` | 
| `military`  | `uint8`   | Unknown.  | `game::MenuSeqEventTheater::playEvent` | 
| `construct` | `uint8`   | Unknown.  | `game::MenuSeqEventTheater::playEvent` | 

---

### MNU_EventTheater_equip_pc

*Human Readable Name*: **Menu - Event Theater - Equipment - Playable Character**

Equipment settings for playable characters during event theater.

`MNU_EventTheater_equip_pc%02d` where:
* `%02d` - Character ID - 1 to 16

!!! note 

    Hardcoded to read from ID 1 to 16. Each file is checked if exists.

| Column      | Type      | Description                | Handled by |
|-------------|-----------|----------------------------|------------|
| `ev_id`     | `uint16`  | [Event ID](#EVT_cs)        | `game::MenuSeqEventTheater::playEvent` | 
| `eq_head`   | `uint16`  | Equipped head [Item ID](#itm_itemlist). | `game::MenuSeqEventTheater::playEvent` | 
| `eq_body`   | `uint16`  | Equipped body [Item ID](#itm_itemlist). | `game::MenuSeqEventTheater::playEvent` | 
| `eq_arm`    | `uint16`  | Equipped arm [Item ID](#itm_itemlist). | `game::MenuSeqEventTheater::playEvent` | 
| `eq_waist`  | `uint16`  | Equiped waist [Item ID](#itm_itemlist). | `game::MenuSeqEventTheater::playEvent` | 
| `eq_legg`   | `uint16`  | Equipped leggings [Item ID](#itm_itemlist). | `game::MenuSeqEventTheater::playEvent` | 
| `eq_wpn`    | `uint16`  | Equipped weapon [Item ID](#itm_itemlist). | `game::MenuSeqEventTheater::playEvent` | 

---

### MNU_EventTheater_kzn

*Human Readable Name*: **Menu - Event Theater - Kizuna**

`MsTextId` linked to `MNU_event_name_ms`.

List of all the event theater cutscenes.

!!! tip

    IDs will map to image files at `menu/image/evth_kzn_img%03d`.

| Column           | Type      | Description                | Handled by |
|------------------|-----------|----------------------------|------------|
| `kzn_no`         | `uint16`  | [JNL_Kizunalist ID](#JNL_Kizunalist)    | `game::MenuSeqEventTheater::MenuSeqEventTheater` | 
| `thumbnail`      | `uint16`  | Appears unused. |  | 
| `sort_index`     | `uint16`  | Sorting index on the UI. |  | 
| `fixed_time`     | `uint8`   | Fixed time of day type. | `game::MenuPartsEventTheaterSelect::setEvent` | 
| `fixed_weather`  | `uint16`  | Whether the weather does not change. | `game::MenuPartsEventTheaterSelect::setEvent` | 
| `ev01_id`        | `uint16`  | [Event ID](#EVT_cs) | `game::MenuSeqEventTheater::playEvent` | 
| `col6_setting`   | `uint16`  | [Colony 6 Setup ID](#mnu_eventtheater_col6) | `game::MenuSeqEventTheater::playEvent` | 
| `pos_x`          | `float`   | Position X. | `game::MenuSeqEventTheater::playEvent` | 
| `pos_y`          | `float`   | Position X. | `game::MenuSeqEventTheater::playEvent` | 
| `pos_Z`          | `float`   | Position X. | `game::MenuSeqEventTheater::playEvent` | 

---

### MNU_EventTheater_scn

*Human Readable Name*: **Menu - Event Theater - Scene?**

`MsTextId` linked to `MNU_event_name_ms`.

List of all the event theater scenes (?)

!!! tip

    IDs will map to image files at `menu/image/evth_scn_img%03d`.

| Column           | Type      | Description                | Handled by |
|------------------|-----------|----------------------------|------------|
| `title`          | `MsTextId`| Localized name. | `game::MenuSeqEventTheater::updateEventIDList` | 
| `thumbnail`      | `uint16`  | Appears unused. |  | 
| `scn_no`         | `uint16`  | Scn Number.     | `game::MenuSeqEventTheater::updateEventIDList` | 
| `sort_index`     | `uint16`  | Sorting index on the UI. |  | 
| `fixed_time`     | `uint8`   | Fixed time of day type. | `game::MenuPartsEventTheaterSelect::setEvent` | 
| `fixed_weather`  | `uint16`  | Whether the weather does not change. | `game::MenuPartsEventTheaterSelect::setEvent` | 
| `ev01_id`        | `uint16`  | [Event ID](#EVT_cs) #1. | `game::BDatMnuEventTheaterScn::getEventIDList` & more | 
| `ev02_id`        | `uint16`  | [Event ID](#EVT_cs) #2. | `game::BDatMnuEventTheaterScn::getEventIDList` & more | 
| `ev03_id`        | `uint16`  | [Event ID](#EVT_cs) #3. | `game::BDatMnuEventTheaterScn::getEventIDList` & more | 
| `ev04_id`        | `uint16`  | [Event ID](#EVT_cs) #4. | `game::BDatMnuEventTheaterScn::getEventIDList` & more | 
| `ev05_id`        | `uint16`  | [Event ID](#EVT_cs) #5. | `game::BDatMnuEventTheaterScn::getEventIDList` & more | 
| `ev06_id`        | `uint16`  | [Event ID](#EVT_cs) #6. | `game::BDatMnuEventTheaterScn::getEventIDList` & more | 
| `ev07_id`        | `uint16`  | [Event ID](#EVT_cs) #7. | `game::BDatMnuEventTheaterScn::getEventIDList` & more | 
| `ev08_id`        | `uint16`  | [Event ID](#EVT_cs) #8. | `game::BDatMnuEventTheaterScn::getEventIDList` & more | 
| `ev09_id`        | `uint16`  | [Event ID](#EVT_cs) #9. | `game::BDatMnuEventTheaterScn::getEventIDList` & more | 

---

### MNU_FacePatternList

*Human Readable Name*: **Menu - Face Pattern List**

Unknown. Appears unused in XC1DE.

!!! tip

    IDs will map to image files at `menu/image/evth_scn_img%03d`.

| Column      | Type      | Description                | Handled by |
|-------------|-----------|----------------------------|------------|
| `name`      | `string`  | Face Pattern Name. | `game::UIFontManager::loadFontSet` | 
| `image_no`  | `uint8`   | ? | `game::UIFontManager::loadFontSet` | 

---

### MNU_FontSet01

*Human Readable Name*: **Menu - Font Set**

Font set to use per language.

Tables per language:

* Global: `MNU_FontSet01`
* Korean: `MNU_FontSet01_kr`
* Chinese: `MNU_FontSet01_cn`
* Taiwannese: `MNU_FontSet01_tw`

| Column        | Type       | Description                | Handled by |
|---------------|------------|----------------------------|------------|
| `type`        | `uint8`    | See below | `game::UIFontManager::loadFontSet` | 
| `resource`    | `uint32`   | Maps to [MNU_ResFont](#mnu_resfont). | `game::UIFontManager::loadFontSet` | 
| `image_type`  | `uint32`   | Used when `type` is 6. Maps to | `game::UIFontManager::loadFontSet` | 

!!! note "Type"

    Minimum 6. 

    * 6 = [MNU_ResourceCategory](#mnu_resourcecategory) ID 4 or 5 depending on `image_type` being 1 or 2 = `menu/image/`
    * 8 = [MNU_ResourceCategory](#mnu_resourcecategory) ID 1 = `menu/font/`
    * 9 = [MNU_ResourceCategory](#mnu_resourcecategory) ID 2 = `menu/font/`
    * 10 = [MNU_ResourceCategory](#mnu_resourcecategory) ID 10 = `menu/msproj/`

---

### MNU_Hana_custom

Unknown. Appears unused in XC1DE.

---

### MNU_Input

Tables:

* `MNU_InputAct`
* `MNU_InputPad`
* `MNU_InputPointer`
* `MNU_InputWheel`

Unknown. Appears unused in XC1DE.

---

### MNU_Layer

*Human Readable Name*: **Menu - Layer**

Unknown. Appears unused in XC1DE.


| Column      | Type      | Description                | Handled by |
|-------------|-----------|----------------------------|------------|
| `group`     | `uint8`   | Layer group. | `game::MenuLayerBuilderManager::setupFromBdat` | 
| `filename`  | `string`  | Path to the layer file. | `game::MenuLayerBuilderManager::setupFromBdat` | 
| `prio`      | `uint8`   | Layer priority. Applied after group. | `game::MenuLayerBuilderManager::setupFromBdat` | 
| `cache`     | `uint8`   | Face Pattern Name. | `game::MenuLayerBuilderManager::setupFromBdat` | 

---

### MNU_ResFont

*Human Readable Name*: **Menu - Resource Font**

Files to be used when loading font resources. Referenced by [MNU_ResFont01](#mnu_fontset01) to append to a specific folder  when `type` is 8.


| Column      | Type      | Description                | Handled by |
|-------------|-----------|----------------------------|------------|
| `file`      | `string`  | File Name. | `game::UIResourceManager::getResourceNameFromId` | 

---

### MNU_ResFontStyle

*Human Readable Name*: **Menu - Resource Font Style**

Files to be used when loading font style resources. Referenced by [MNU_ResFont01](#mnu_fontset01) to append to a specific folder when `type` is 9.

| Column      | Type      | Description                | Handled by |
|-------------|-----------|----------------------------|------------|
| `file`      | `string`  | File Name. | | 

### MNU_ResImage

*Human Readable Name*: **Menu - Resource Image**

Files to be used when loading image resources. Referenced by [MNU_ResFont01](#mnu_fontset01) to append to a specific folder when `type` is 6.


| Column      | Type      | Description                | Handled by |
|-------------|-----------|----------------------------|------------|
| `file`      | `string`  | File Name. | | 

---

### MNU_ResLayout

*Human Readable Name*: **Menu - Resource Layout**

Files to be used when loading layout resources. Possibly unused/unreferenced in XC1DE.


| Column      | Type      | Description                | Handled by |
|-------------|-----------|----------------------------|------------|
| `file`      | `string`  | File Name. | | 

---

### MNU_ResMSProj

*Human Readable Name*: **Menu - Resource Monolith Soft Project**

Files to be used when loading monolith soft project resources. Referenced by [MNU_ResFont01](#mnu_fontset01) to append to a specific folder when `type` is 10.


| Column      | Type      | Description                | Handled by |
|-------------|-----------|----------------------------|------------|
| `file`      | `string`  | File Name. | | 

!!! tip "MS Files"

    Useful functions related to it:

    * `fw::ResMsprojData::buildResource`
    * `ms::MsWrapper::regist`
    * `LMS_InitProject`
    * Anything starting with `LMS`

---

### MNU_ResMotion

*Human Readable Name*: **Menu - Resource Motion**

Files to be used when loading motion resources. Possibly unused/unreferenced in XC1DE.


| Column      | Type      | Description                | Handled by |
|-------------|-----------|----------------------------|------------|
| `file`      | `string`  | File Name. | | 

---

### MNU_ResUio

*Human Readable Name*: **Menu - Resource Ui Object**

Files to be used when loading UI Object resources. Possibly unused/unreferenced in XC1DE.


| Column      | Type      | Description                | Handled by |
|-------------|-----------|----------------------------|------------|
| `file`      | `string`  | File Name. | | 

---

### MNU_ResourceCategory

*Human Readable Name*: **Menu - Resource Categories**

Maps resource IDs to their folder locations.

| Column        | Type      | Description                                | Handled by |
|---------------|-----------|--------------------------------------------|------------|
| `path_prefix` | `string`  | Folder location prefx for the resource category. | `game::UIResourceManager::getPathPrefixFromCategory` | 
| `res_type`    | `uint32`  | Actual resource type, used when loading files. | `game::UIResourceManager::loadResourceImplFromNormalizedPath` |

!!! tip "`res_type` file Handler"
    
    * 1 = `fw::ResLayImg` - `.wilay`
    * 2 = `fw::ResLayFont` - `.wifnt`
    * 3 = `fw::ResLayStyle` - `.wisty`
    * 4 = `fw::ResUIObject` - `.uio`
    * 5 = `fw::ResUIParticle` - `.uip`
    * 6 = `fw::ResUIMotion` - `.uim`
    * 7 = `fw::ResMsprojData` - `.msbp`
    * 8 = `fw::ResModel` - `.wimdo`
    * 9 = `fw::ResBdat` - `.bdat`
    * 10 = `Unused/Unsupported`

---

### MNU_ResourceType

*Human Readable Name*: **Menu - Resource Type**

Empty & Unused/unreferenced in XC1DE.

---

### MNU_StreamAnnounce

*Human Readable Name*: **Menu - Stream Announce**

Empty & Unused/unreferenced in XC1DE.

---

### MNU_StreamHelp

*Human Readable Name*: **Menu - Stream Help**

Empty & Unused/unreferenced in XC1DE.

---

### MNU_Stream

*Human Readable Name*: **Menu - Stream**

Empty & Unused/unreferenced in XC1DE.

---

### MNU_StyleArmorPc

*Human Readable Name*: **Menu - Style Armor Playable Character**

`MsTextId` linked to `ITM_fashionlist_ms`.

`MNU_StyleArmorPc%02d` where:

* `%02d` - Playable character ID - uint16 

Returns localized weapon style name if enabled for a specific body part. Depends on [ITM_wpnlist](#itm_wpnlist).

| Column      | Type                            | Description                | Handled by |
|-------------|---------------------------------|----------------------------|------------|
| `name`      | `MsTextId`  | File Name. | `game::MenuStyleEnumerable::create` | 
| `head`      | `uint8`     | Whether this style is enabled for head parts. | `game::BDatMnuStyleArmor::isEnableParts` | 
| `body`      | `uint8`     | Whether this style is enabled for body parts. | `game::BDatMnuStyleArmor::isEnableParts` | 
| `arm`       | `uint8`     | Whether this style is enabled for arm parts. | `game::BDatMnuStyleArmor::isEnableParts` | 
| `waist`     | `uint8`     | Whether this style is enabled for waist parts. | `game::BDatMnuStyleArmor::isEnableParts` | 
| `leg`       | `uint8`     | Whether this style is enabled for leg parts. | `game::BDatMnuStyleArmor::isEnableParts` | 
| `index`     | `uint8`     | Order index (?) | `game::BDatMnuStyleArmor::isEnableParts` | 

---

### MNU_StyleWeaponPc

*Human Readable Name*: **Menu - Style Armor Playable Character**

`MsTextId` linked to `ITM_fashionlist_ms`.

`MNU_StyleWeaponPc%02d` where:

* `%02d` - Playable character ID - uint16 

Returns localized weapon style names. Depends on [ITM_wpnlist](#itm_wpnlist).

| Column      | Type        | Description                | Handled by |
|-------------|-------------|----------------------------|------------|
| `name`      | `MsTextId`  | File Name.                 | `game::MenuStyleEnumerable::create` | 
| `index`     | `uint8`     | Order index (?)            |  | 

---

### MNU_Text_IdList

*Human Readable Name*: **Menu - Text ID List**

Table that points IDs to a specific bdat localized entry. **Possibly unused in XC1DE.**

| Column      | Type      | Description                | Handled by |
|-------------|-----------|----------------------------|------------|
| `text_file` | `uint16`  | [MNU_TextLink_MsTxt ID](#mnu_textlink_mstxt). | `game::UIDataLibrary::getTextFromTextIdList` | 
| `text_id`   | `uint32`  | Row ID for the specified Ms Bdat.             | `game::UIDataLibrary::getTextFromTextIdList` | 

---

### MNU_TextLink_Mstxt

*Human Readable Name*: **Menu - Text Link Table - Ms Text**

Used by [MNU_Text_IdList](#mnu_text_idlist) to link to bdat files. **Possibly unused in XC1DE.**

| Column      | Type      | Description                | Handled by |
|-------------|-----------|----------------------------|------------|
| `filename`  | `string`  | Localized Bdat File name.  | `game::UIDataLibrary::getTextFromTextIdList` | 

---

## System

### SYS_filelist

*Human Readable Name*: **System - File List**

Table of files. Used by:

* [FLD_npclist](#fld_npclist)
* [FLD_maplist](#fld_maplist)
* [MNU_minimap_list_fs](#mnu_minimap_list_fs)
* [MNU_minimap_list_hud](#mnu_minimap_list_hud)

| Column      | Type      | Description                | Handled by |
|-------------|-----------|----------------------------|------------|
| `filename`  | `string`  | File Name.                 | `game::MenuGameDataMap::getMapCaptureImageFileName`, `game::MenuGameDataNpc::getFaceTextureFileName`, `game::MenuGameDataMap::getMapFloorImageName` | 

---

### SYS_filelist_ex

*Human Readable Name*: **System - File List Ex**

Table of extra files. Used by:

* [ITM_itemlist](#itm_itemlist)->icon
* [ITM_itemlist](#itm_itemlist)->icon_base
* [pc_arts](#pc_arts)->icon
* [pc_arts](#pc_arts)->icon_base
* [nopon_arts](#nopon_arts)->icon
* [nopon_arts](#nopon_arts)->icon_base
* [BTL_enelist](#btl_enelist)->mnu_vision_face
* [BTL_bufflist](#btl_bufflist)->icon

Some ids are hardcoded for use.

| Column          | Type        | Description              | Handled by |
|-----------------|-------------|--------------------------|------------|
| `file_id`       | `uint16`    | Appears unused.          |  | 
| `res_image_idx` | `uint16`    | Appears unused.          |  | 
| `icon_idx`      | `uint8`     | Layer Icon Index.        | Too many. | 

---

### SYS_iconlist

*Human Readable Name*: **System - Icon List**

Possibly Unused.

| Column          | Type        | Description              | Handled by |
|-----------------|-------------|--------------------------|------------|
| `filename1`     | `uint16`    | Appears unused.          |  | 
| `filename2`     | `uint16`    | Appears unused.          |  | 

---

### SYS_viblist

*Human Readable Name*: **System - Vibration List**

Handles vibration. Many IDs are hardcoded depending on the situation.

| Column          | Type        | Description              | Handled by |
|-----------------|-------------|--------------------------|------------|
| `vibid`         | `uint16`    | Vibration ID             | `game::GameVib::playVibration` | 
| `gainLow`       | `float`     | Low Gain                 | `game::GameVib::playVibration` | 
| `pitchLow`      | `float`     | Low Pitch                | `game::GameVib::playVibration` | 
| `gainHigh`      | `float`     | Gain High                | `game::GameVib::playVibration` | 
| `pitchHigh`     | `float`     | Pitch High               | `game::GameVib::playVibration` | 
| `speed`         | `float`     | Speed                    | `game::GameVib::playVibration` | 



