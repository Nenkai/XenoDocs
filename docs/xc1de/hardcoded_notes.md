List of weird functions to investigate or do excessive hardcoding

* `game::MenuGameDataMapUtil::GetMapAreaIdFromMapId` hardcodes map id to region.
* `game::DataMenuUtil::isEquipStyleViewSys` is weird
* Check `evu::EvtResName::getResType`
* Check `game::MenuGameQuestAcc::isTaskCompleted`
* Check `game::MenuGameBattleStateUtil::getType`
* Check `game::EffUtil::getStatusEffectToCndEffId`
* Check `game::MenuGameDataMap::getLandmarkLockReason`
* Check `game::SeqMapJump::onInitialize`
* Check `game::DataPassiveSkill::isLinkLocked`
* Check `game::DataUtil::isNebula` hardcoded to en070101
* Check `game::DataUtil::isMonadoShulk`
* Check `game::DataUtil::calcExpApSpForBattle`
* Check `game::MenuPartsReviveColony6Util::incrementRevivalLevel` - hardcoded levels
* Check `game::DataUtil::isRevivalCol6Enabled`
* Check `game::GimmickQstMarker::updateGimmicklist` - if ( (unsigned __int16)v44 == 636 && State == 121 )
* `game::SeqMapJump::resoterTreasureBox` 32 boxes

game::DataBdat::setupFp
