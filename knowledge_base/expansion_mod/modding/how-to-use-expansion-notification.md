# How to Use Expansion Notification

## How does it work?

Some examples:

```cpp
ExpansionNotification("Title Text", "My notification message").Success(identity);  // Example for a success message in expansion
ExpansionNotification("Title Text", "My notification message").Error(identity);     // Example for a fail message in expansion
ExpansionNotification("Title Text", "My notification message").Info(identity);     // Example for a info message in expansion

// Examples for a message where you can control icon (parameter 3), color (parameter 4) and the time (parameter 5) how long the notification gets displayed
ExpansionNotification(new CF_Localiser("STR_EXPANSION_MISSION_NOTIF_TITLE", "Airdrop"), new StringLocaliser("STR_EXPANSION_MISSION_AIRDROP_HEADING_TOWARDS", "Kamenka"), "Airdrop", COLOR_EXPANSION_NOTIFICATION_MISSION, 7.0).Create(identity); // Format to use CF_Localiser

ExpansionNotification("Title Text", "My notification message", "Boat", COLOR_EXPANSION_NOTIFICATION_MISSION, time).Create(identity);  // Format to use normal string text
```

---

## Parameters

### ICON

Expansion provides a wide variety of default icons you can use, see **List of default icon names**.

See Adding custom icons on how to add custom icons. You can also provide a full path, although that is not recommended. The icon need to be in edds or paa format.

---

### COLOR

The color must be in ARGB. By default expansion have 14 colors configured but you can also use this site to generate any kind of color integer for your color: https://argb-int-calculator.netlify.app/

**Available color constants:**
- `COLOR_EXPANSION_ITEM_HIGHLIGHT_TEXT`
- `COLOR_EXPANSION_ITEM_NORMAL_TEXT`
- `COLOR_EXPANSION_ITEM_HIGHLIGHT_ELEMENT`
- `COLOR_EXPANSION_ITEM_NORMAL_ELEMENT`
- `COLOR_EXPANSION_NOTIFICATION_INFO`
- `COLOR_EXPANSION_NOTIFICATION_ERROR`
- `COLOR_EXPANSION_NOTIFICATION_SUCCSESS`
- `COLOR_EXPANSION_NOTIFICATION_ORANGE`
- `COLOR_EXPANSION_NOTIFICATION_ASPHALT`
- `COLOR_EXPANSION_NOTIFICATION_AMETHYST`
- `COLOR_EXPANSION_NOTIFICATION_TURQUOISE`
- `COLOR_EXPANSION_NOTIFICATION_ORANGEVILLE`
- `COLOR_EXPANSION_NOTIFICATION_EXPANSION`
- `COLOR_EXPANSION_NOTIFICATION_MISSION`

---

### TIME

Floating point. This value is the amount of seconds it will stay on the screen of the player. We recommend you to use a number between 5 and 10.

---

### PLAYER_IDENTITY

You need to enter the players identity to send the notification from the server to a client if you execute the notification code from sever side. If the notification gets executed on server side and no player identity is given the message gets send to all active clients.

**Example for server side execution to a single active player:**
```cpp
PlayerBase player; //! You need to define player somehow, this is just a example code line with no legit instance to the PlayerBase player variable.
PlayerIdentity playerIdentity = player.GetIdentity(); //! Get the players identity instance.
ExpansionNotification("Title Text", "My notification message", "Boat", COLOR_EXPANSION_NOTIFICATION_MISSION, time).Create(playerIdentity);
```

**Example for server side execution to all active players:**
```cpp
ExpansionNotification("Title Text", "My notification message", "Boat", COLOR_EXPANSION_NOTIFICATION_MISSION, time).Create();
```

**Example for client side execution to the player:**
```cpp
ExpansionNotification("Title Text", "My notification message", "Boat", COLOR_EXPANSION_NOTIFICATION_MISSION, time).Create();
```
