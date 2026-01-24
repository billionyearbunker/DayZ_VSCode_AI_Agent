# Advanced quest events and features

---

## Mission file modding

The following methods can be used in your missions `init.c` to fire custom-coded events in different quest event scenarios. Please take note that these are not all useful methods that can be used here. For more information, you can dig in our script repository.

```cpp
class CustomMission: MissionServer
{
#ifdef EXPANSIONMODQUESTS
	//! Event called when a player connects/reconnects to the server and the quest system and his quests are initialized for the player.
	override void Expansion_OnQuestPlayerInit(ExpansionQuestPersistentData playerQuestData, PlayerIdentity identity) {}

	//! Condition check method if given player identity can start the quest with the given configuration.
	override bool Expansion_CanStartQuest(ExpansionQuestConfig questConfig, PlayerIdentity identity)
	{
		bool condition = super.Expansion_CanStartQuest(questConfig, identity);
		return condition;
	}

	//! Condition check method if given player identity can complete the given quest instance.
	override bool Expansion_CanCompleteQuest(ExpansionQuest quest, PlayerIdentity identity) {}

	//! Event method that gets called when a quest is started.
	override void Expansion_OnQuestStart(ExpansionQuest quest) {}
	
	//! Event method that gets called when a quest is continued.
	override void Expansion_OnQuestContinue(ExpansionQuest quest) {}
	
	//! Event method that gets called when a quest objective timer runs out.
	override void Expansion_OnObjectiveTimeLimitReached(ExpansionQuestObjectiveEventBase objectiveEventBase) {}
	
	//! Event method that gets called when a quest gets cancled by the player or quest system.
	override void Expansion_OnQuestCancel(ExpansionQuest quest) {}
	
	//! Event method that gets called when all quest objectives of a quest are completed.
	override void Expansion_OnQuestObjectivesComplete(ExpansionQuest quest) {}
	
	//! Event method that gets called when one quest objective of a quest gets incompleted and all quest objective where completed once.
	override void Expansion_OnQuestObjectivesIncomplete(ExpansionQuest quest) {}
	
	//! Event method called when a quest is completed (turned-in).
	override void Expansion_OnQuestCompletion(ExpansionQuest quest)
	{
		super.Expansion_OnQuestCompletion(quest);
	}
#endif
};
```

---

## Create/delete and check temporary quest NPCs

```cpp
//! Create new temporary quest NPC data
//! ID, NPC class name, NPC name, and default quest menu text that is shown to the player.
ExpansionTempQuestHolder questHolder = new ExpansionTempQuestHolder(4000, \"ExpansionQuestNPCAIFrida\", \"Marina Sidorova\", \"There is nothing to do here for you...\");
if (!questHolder)
	return;

questHolder.SetNPCEmoteID(EmoteConstants.ID_EMOTE_SITA); //! Emote ID of the NPC if it is an AI. 
questHolder.SetLoadoutName(\"SurvivorLoadout\"); //! Loadout file name that gets applied to the NPC if it is a normal or AI NPC.
ExpansionTempQuestHolderPosition questHolderPos = new ExpansionTempQuestHolderPosition(\"9029.09 9.36924 10112.8\", \"55.5735 0 -0\"); //! World position and orientation of the NPC when spawned.
ExpansionQuestModule.GetModuleInstance().SpawnQuestHolder(questHolder, questHolderPos); //! Spawn the temporary quest NPC.
```

```cpp
//! Delete an existing temporary quest NPC if it exists.
//! Need the temporary quest NPC ID and NPC type integer to find and delete the entity.
ExpansionQuestModule.GetModuleInstance().DeleteQuestHolder(4000, ExpansionQuestNPCType.AI);
```

```cpp
//! Check if a temporary quest NPC with the given ID has already been spawned.
ExpansionQuestModule.GetModuleInstance().TempQuestHolderExists(4000)
```

---

## Advanced useful quest methods

```cpp
ExpansionQuest quest;
//! Condition check if any other quest with the given quest ID is active for other players.
//! Returns true if another active quest instance with the same quest ID is found.
ExpansionQuestModule.GetModuleInstance().IsOtherQuestInstanceActive(quest);
```

---

## Mission file modding examples

Example modifications for mission `init.c` that can be used with the DayZ-Expansion-Quests mod in combination with the DayZ-Expansion-Hardline and DayZ-Expansion-AI mods.

### Add specific faction reputation to quest players when completing a certain quest

```cpp
class CustomMission: MissionServer
{
    //! Event method that fires on quest completion	
    override void Expansion_OnQuestCompletion(ExpansionQuest quest)
    {
        int factionID;

        switch (quest.GetQuestConfig().GetID())
        {
            //! Quest ID of the quest where this event should fire
            case 1:
            {
                typename factionType = eAIFactionEast; //! Faction type class name for that the player should get reputation.
                factionID = eAIRegisterFaction.s_FactionIDs[factionType];
                if (factionID != 0)
                {
                    //! If the quest is a group quest we add the reputation to all members unless the "RewardsForGroupOwnerOnly" is set to 1 (true).
                    if (quest.GetQuestConfig().IsGroupQuest())
                    {
                        set<string> memberUIDs = quest.GetPlayerUIDs();
                        foreach (string memberUID: memberUIDs)
                        {
                            if (m_Config.RewardsForGroupOwnerOnly())
                            {
                                if (memberUID != quest.GetPlayerUID())
                                    continue;
                            }

                            PlayerBase groupPlayer = PlayerBase.GetPlayerByUID(memberUID);
                            if (!groupPlayer)
                                continue;

                            groupPlayer.Expansion_AddFactionReputation(100, factionID);
                        }
                    }
                    //! If the quest is not a group quest we just add the reputation to the main quest player.
                    else
                    {
                        PlayerBase player = quest.GetPlayer();
                        if (player)
                            player.Expansion_AddFactionReputation(100, factionID);
                    }
                }
            }
            break;
        }

        super.Expansion_OnQuestCompletion(quest);
    }
};
```

---

### Fail specific quest if the player leaves the server

```cpp
class CustomMission: MissionServer
{
    //! Event method that fires when a player disconnects
    override void InvokeOnDisconnect(PlayerBase player, PlayerIdentity identity)
    {
        super.InvokeOnDisconnect(player, identity);
        
        if (!player || !identity)
            return;
        
        //! Get all active quests for the player
        array<ref ExpansionQuest> activeQuests = new array<ref ExpansionQuest>;
        ExpansionQuestModule.GetModuleInstance().GetPlayerActiveQuests(identity.GetId(), activeQuests);
        
        foreach (ExpansionQuest quest: activeQuests)
        {
            //! Cancel quest with specific ID when player disconnects
            if (quest.GetQuestConfig().GetID() == 1)
            {
                ExpansionQuestModule.GetModuleInstance().CancelQuest(quest.GetQuestInstanceID());
            }
        }
    }
};
```
class CustomMission: MissionServer
{
    //! Event method that fires on player reconnect for already started quests
    override void Expansion_OnQuestContinue(ExpansionQuest quest)
    {
        super.Expansion_OnQuestContinue(quest);

        ExpansionQuestConfig questConfig = quest.GetQuestConfig();

        switch (questConfig.GetID())
        {
            // In this example we want to fail the quest 10 or quest 22 if the player logged of or crashed
            // before completing the quest
            case 10:
            case 22:
            {
                ExpansionQuestModule questModule;
                if (!CF_Modules<ExpansionQuestModule>.Get(questModule))
                    return;

                questModule.CancelQuestServer(quest);
            }
            break;
        }
    }
};
