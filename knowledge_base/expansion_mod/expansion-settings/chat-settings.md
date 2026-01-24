# Chat Settings

## Configuration Parameters

### **`m_Version`**
- **Type:** `Integer`
- **Description:** Contains the current setting version number, never change this value unless you really know what you are doing as it's used internally for automatic conversion of old settings whenever we change something.

---

### **`EnableGlobalChat`**
- **Type:** `Bool`
- **Values:**
  - `0` = The global chat (blue chat) will be disabled
  - `1` = It will enable the global chat. The global chat allows players to talk to anyone from anywhere on the map

---

### **`EnablePartyChat`**
- **Note:** Requires DayZ-Expansion-Groups or Bundle
- **Type:** `Bool`
- **Values:**
  - `0` = The party chat (green chat) will be disabled
  - `1` = It will enable the party chat. The party chat allows players to talk to anyone in their group from anywhere on the map

---

### **`EnableTransportChat`**
- **Type:** `Bool`
- **Values:**
  - `0` = The transport chat (yellow chat) will be disabled
  - `1` = It will enable the transport chat. The transport chat allows players to talk to anyone inside the same vehicle as you

---

### **`ChatColors`**
- **Type:** `Array<String, String>`
- **Description:** A list of Hex colors for each chat channels. The first part of the setting is the name of the chat channel we want to target and the second part is its new color.

**Example:**
```json
"MyChannel_ChatColor": "EB45EBFF",
```

You can find many online tools and software to find the desired color like this website for example: https://www.color-hex.com/ (without the #)

**Default Colors:**
```json
"SystemChatColor": "EB45EBFF",
"AdminChatColor": "FF392BFF",
"GlobalChatColor": "58C3FFFF",
"DirectChatColor": "FFFFFFFF",
"TransportChatColor": "FFCE09FF",
"PartyChatColor": "0AFA7AFF",
"TransmitterChatColor": "F9FF49FF"
```

**Channel Descriptions:**
- **SystemChatColor:** When the SERVER is writing a message - Everyone can see this channel
- **AdminChatColor:** When an ADMIN is writing a message - Everyone can see this channel
- **GlobalChatColor:** When someone is writing a server wide (global) message
- **DirectChatColor:** The "local" chat, this chat is the default channel DayZ provides
- **TransportChatColor:** When a player in the same vehicle as you is writing
- **PartyChatColor:** When a player from your group is writing - Only if you have Expansion Party!
- **TransmitterChatColor:** When a player is using PE in a town and you are in the area
