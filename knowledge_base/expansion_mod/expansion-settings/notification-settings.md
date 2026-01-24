# NotificationSettings

---

## Settings Parameters

### **`m_Version`**
- **Type**: Integer
- **Description**: Contains the current setting version number, never change this value unless you really know what you are doing as it's used internally for automatic conversion of old settings whenever we change something.

---

### **`EnableNotification`**
- **Type**: Bool
- **Values**:
  - `0` = All the notifications will be disabled
  - `1` = Notifications will be enabled

---

## Player Join/Leave Notifications

### **`ShowPlayerJoinServer`**
- **Type**: Bool
- **Values**:
  - `0` = The "Player Joined the server" notification will not be displayed
  - `1` = The "Player Joined the server" notification will be enabled

---

### **`JoinMessageType`**
- **Type**: Integer
- **Values**:
  - `0` = The notification will be displayed in the chat
  - `1` = The notification will be displayed as a notification on the top left corner of your screen

---

### **`ShowPlayerLeftServer`**
- **Type**: Bool
- **Values**:
  - `0` = The "Player left the server" notification will not be displayed
  - `1` = The "Player left the server" notification will be enabled

---

### **`LeftMessageType`**
- **Type**: Integer
- **Values**:
  - `0` = The notification will be displayed in the chat
  - `1` = The notification will be displayed as a notification on the top left corner of your screen

---

## Airdrop Notifications

### **`ShowAirdropStarted`**
- **Type**: Bool
- **Values**:
  - `0` = The notification when ever an airdrop event started will not be displayed
  - `1` = Displays the notification when ever a airdrop event started

---

### **`ShowAirdropClosingOn`**
- **Type**: Bool
- **Values**:
  - `0` = The notification when ever an airdrop plane gets close to the drop location will not be displayed
  - `1` = Displays the notification when ever a airdrop plane gets close to the drop location

---

### **`ShowAirdropDropped`**
- **Type**: Bool
- **Values**:
  - `0` = The notification when ever an airdrop has been droped on the drop location will not be displayed
  - `1` = Displays the notification when ever a airdrop has been droped on the drop location

---

### **`ShowAirdropEnded`**
- **Type**: Bool
- **Description**: ("The Airdrop at ... was destroyed by infected.")
- **Values**:
  - `0` = The notification when ever an airdrop has ended on the drop location will not be displayed
  - `1` = Displays the notification when ever a airdrop has ended on the drop location

---

### **`ShowPlayerAirdropStarted`**
- **Type**: Bool
- **Values**:
  - `0` = The notification when ever a player calls an airdrop with an airdrop flare will not get displayed
  - `1` = Displays the notification when a player calls an airdrop with an airdrop flare

---

### **`ShowPlayerAirdropClosingOn`**
- **Type**: Bool
- **Values**:
  - `0` = The notification when ever a player calls an airdorop with an airdrop flare and it gets close to the drop location will not be displayed
  - `1` = Displays the notification when ever a player calls an airdorop with an airdrop flare and it gets close to the drop location

---

### **`ShowPlayerAirdropDropped`**
- **Type**: Bool
- **Values**:
  - `0` = The notification when ever a player calls an airdorop with an airdrop flare and it has been droped on the drop location will not be displayed
  - `1` = Displays the notification when ever a player calls an airdorop with an airdrop flare and it has been droped on the drop location

---

## Territory Notifications

### **`ShowTerritoryNotifications`**
- **Type**: Bool
- **Values**:
  - `0` = The notification when ever a player enters an territory will not be displayed
  - `1` = Displays the notification when ever a player enters an territory

---

## Kill-Feed Settings

### **`EnableKillFeed`**
- **Type**: Bool
- **Values**:
  - `0` = All the kill-feed notifications will be disabled
  - `1` = Kill-feed will be enabled

---

### **`KillFeedMessageType`**
- **Type**: Bool
- **Values**:
  - `0` = Kill-feed notification will be displayed in the chat
  - `1` = Kill-feed notification will be displayed as a notification on the top left corner of your screen

---

### **`KillFeedFall`**
- **Type**: Bool
- **Values**:
  - `0` = Disables the display of kill-feed notifications related to player deaths by fall damage
  - `1` = Displays kill-feed notifications related to player deaths by fall damage

---

### **`KillFeedCarHitDriver`**
- **Type**: Bool
- **Values**:
  - `0` = Disables the display of kill-feed notifications related to player deaths by an car hit with a driver in the car
  - `1` = Displays kill-feed notifications related to player deaths by a car hit with a driver in the car

---

### **`KillFeedCarHitNoDriver`**
- **Type**: Bool
- **Values**:
  - `0` = Disables the display of kill-feed notifications related to player deaths by an car hit with no driver in the car
  - `1` = Displays kill-feed notifications related to player deaths by an car hit with no driver in the car

---

### **`KillFeedCarCrash`**
- **Type**: Bool
- **Values**:
  - `0` = Disables the display of kill-feed notifications related to player deaths by an car crash as a driver
  - `1` = Displays kill-feed notifications related to player deaths by an car crash as a driver

---

### **`KillFeedCarCrashCrew`**
- **Type**: Bool
- **Values**:
  - `0` = Disables the display of kill-feed notifications related to player deaths by an car crash as a passanger
  - `1` = Displays kill-feed notifications related to player deaths by an car crash as a passanger

---

### **`KillFeedHeliHitDriver`**
- **Type**: Bool
- **Values**:
  - `0` = Disables the display of kill-feed notifications related to player deaths by an heli hit with a pilot
  - `1` = Displays kill-feed notifications related to player deaths by an heli hit with a pilot

---

### **`KillFeedHeliHitNoDriver`**
- **Type**: Bool
- **Values**:
  - `0` = Disables the display of kill-feed notifications related to player deaths by an heli hit with no pilot
  - `1` = Displays kill-feed notifications related to player deaths by an heli hit with no pilot

---

### **`KillFeedHeliCrash`**
- **Type**: Bool
- **Values**:
  - `0` = Disables the display of kill-feed notifications related to player deaths by an heli crash as a pilot
  - `1` = Displays kill-feed notifications related to player deaths by an heli crash as a pilot

---

### **`KillFeedHeliCrashCrew`**
- **Type**: Bool
- **Values**:
  - `0` = Disables the display of kill-feed notifications related to player deaths by an heli crash as a passanger
  - `1` = Displays kill-feed notifications related to player deaths by an heli crash as a passanger

---

### **`KillFeedBarbedWire`**
- **Type**: Bool
- **Values**:
  - `0` = Disables the display of kill-feed notifications related to player deaths by hit damage from barbed wires
  - `1` = Displays kill-feed notifications related to player deaths by hit damage from barbed wires

---

### **`KillFeedFire`**
- **Type**: Bool
- **Values**:
  - `0` = Disables the display of kill-feed notifications related to player deaths by hit damage from fireplaces
  - `1` = Displays kill-feed notifications related to player deaths by hit damage from fireplaces

---

### **`KillFeedWeaponExplosion`**
- **Type**: Bool
- **Values**:
  - `0` = Disables the display of kill-feed notifications related to player deaths by hit damage from a weapon explosion (granades, satchels..)
  - `1` = Displays kill-feed notifications related to player deaths by hit damage from a weapon explosion

---

### **`KillFeedDehydration`**
- **Type**: Bool
- **Values**:
  - `0` = Disables the display of kill-feed notifications related to player deaths by dehydration
  - `1` = Displays kill-feed notifications related to player deaths by dehydration

---

### **`KillFeedStarvation`**
- **Type**: Bool
- **Values**:
  - `0` = Disables the display of kill-feed notifications related to player deaths by starvation
  - `1` = Displays kill-feed notifications related to player deaths by starvation

---

### **`KillFeedBleeding`**
- **Type**: Bool
- **Values**:
  - `0` = Disables the display of kill-feed notifications related to player deaths by blood loss
  - `1` = Displays kill-feed notifications related to player deaths by blood loss

---

### **`KillFeedSuicide`**
- **Type**: Bool
- **Values**:
  - `0` = Disables the display of kill-feed notifications related to player deaths by a suicide
  - `1` = Displays kill-feed notifications related to player deaths by a suicide

---

### **`KillFeedWeapon`**
- **Type**: Bool
- **Values**:
  - `0` = Disables the display of kill-feed notifications related to player deaths by a fire weapon
  - `1` = Displays kill-feed notifications related to player deaths by a fire weapon

---

### **`KillFeedMeleeWeapon`**
- **Type**: Bool
- **Values**:
  - `0` = Disables the display of kill-feed notifications related to player deaths by a melee weapon
  - `1` = Displays kill-feed notifications related to player deaths by a meele weapon

---

### **`KillFeedBarehands`**
- **Type**: Bool
- **Values**:
  - `0` = Disables the display of kill-feed notifications related to player deaths by an other player in a fist fight
  - `1` = Displays kill-feed notifications related to player deaths by an other player in a fist fight

---

### **`KillFeedInfected`**
- **Type**: Bool
- **Values**:
  - `0` = Disables the display of kill-feed notifications related to player deaths by an infected/zombie
  - `1` = Displays kill-feed notifications related to player deaths by an infected/zombie

---

### **`KillFeedAnimal`**
- **Type**: Bool
- **Values**:
  - `0` = Disables the display of kill-feed notifications related to player deaths by an wild animal
  - `1` = Displays kill-feed notifications related to player deaths by an wild animal

---

### **`KillFeedKilledUnknown`**
- **Type**: Bool
- **Values**:
  - `0` = Disables the display of kill-feed notifications related to player deaths by and unknown source with an entity
  - `1` = Displays kill-feed notifications related to player deaths by and unknown sourcew ith an entity

---

### **`KillFeedDiedUnknown`**
- **Type**: Bool
- **Values**:
  - `0` = Disables the display of kill-feed notifications related to player deaths by and unknown source
  - `1` = Displays kill-feed notifications related to player deaths by and unknown source

---

## Discord Integration

### **`EnableKillFeedDiscordMsg`**
- **Type**: Bool
- **Note**: **THIS SYSTEM DOES NOT WORK CORRECTLY AS INTENDED SO FAR AND IS DISABLED BY DEFAULT!**
- **Values**:
  - `0` = Disables the display of kill-feed discord messages when the CF webhook has been configured correctly
  - `1` = Displays kill-feed discord messages when the CF webhook has been configured correctly
