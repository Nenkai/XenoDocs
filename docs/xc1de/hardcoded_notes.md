List of weird functions to investigate or do excessive hardcoding

* `game::MenuGameDataMapUtil::GetMapAreaIdFromMapId` hardcodes map id to region.
* `game::DataMenuUtil::isEquipStyleViewSys` is weird
* Check `evu::EvtResName::getResType`
* Check `game::MenuGameQuestAcc::isTaskCompleted`
* Check `game::MenuGameBattleStateUtil::getType`
* Check `game::EffUtil::getStatusEffectToCndEffId`
* Check `game::MenuGameDataMap::getLandmarkLockReason`
* Check `game::SeqMapJump::onInitialize`
* `game::SeqMapJump::resoterTreasureBox` 32 boxes
game::DataBdat::setupFp
