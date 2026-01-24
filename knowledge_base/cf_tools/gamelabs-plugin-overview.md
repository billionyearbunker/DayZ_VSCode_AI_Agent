# GameLabs Plugin for DayZ

## Introduction

The GameLabs plugin for DayZ allows your game server to interact with the CFTools Cloud GameAPI.

It will automatically transmit relevant events as well as player and environment information. Additionally, it acts as a library for other mods to interact with CFTools Cloud components or core GameLabs data.

To install GameLabs follow the "Installation" section.

## Requirements

- CFTools Cloud server registration or Open GameLabs compatible API Server
- Server Id and API Key (Server, Manage, Settings, API Key)

## Installation

Install/load this mod to you the target game server deployment.

For the configuration, create a file called `gamelabs.cfg` in your profiles directory (Do not add any additional file extensions). Inside this file, put following JSON configuration:

```json
{
	"debugEnabled": 0,
	"connectionVerification": 0,
	"serverId": "Server-Id",
	"apiKey": "API-Key",
	"preventDynamicItemPopulation": 0,
	"chatSanitizeBattlEyeJoinLeave": 0,
	"chatSanitizeBattlEyePrefix": 0,
	"advancedChatInterface": 0,
	"lockServerOnStart": 0,
	"enableMetricsDump": 0
}
```

Replace the `Server-Id` and `API-Key` placeholders with your appropriate API information. The file must be saved in either ANSI or UTF-8 format, depending on your OS language settings.

## Extended Configuration

### connectionVerification

GameLabs will automatically verify its access credentials and shut down the server if the API is unreachable or the credentials are invalid. To disable GameLabs shutting down your server for when the API is unreachable set `connectionVerification` to `0`.

When connection verification is disabled, we can and will not guarantee that GameLabs is functioning correctly.

### debugEnabled

Enable or disable GameLabs's debug mode. If you encounter issues, it is recommend to enable debug mode and check the log output generated in `profiles/@Logging`.

### preventDynamicItemPopulation

GameLabs automatically scans your game server for all available items. If your server has more than 50,000 unique items, this may lead to issues. We heavily discourage disabling this setting. Consult CFTools Cloud support if you think your setup requires this.

### serverId / apiKey

These fields must contain your API credentials. You can find them under "Manage", "Settings", "API Key". Only the owner of any specific server may access them. These credentials are required in order for GameLabs to function and the server must be registered with CFTools Cloud before GameLabs can be used.

### chatSanitizeBattlEyeJoinLeave

Sanitize chat from BattlEye join/leave messages.

### chatSanitizeBattlEyePrefix

Remove BattlEye message prefix.

### advancedChatInterface

Support for stylizing RCon messages or displaying them as notification. This may break other chat mods, so testing is recommended.

### lockServerOnStart

This flag will cause the game server to become locked during startup. When enabled, a manual (or automated for example CFCloud Scheduler) unlock is required.

## Extended Functionality

### DayZ Expansion

GameLabs is able to transmit Side and Team chat for DayZ Expansion.

**GameLabs MUST be launched on the client side to achieve this**

### Message Styling

Requires `advancedChatInterface` to be enabled and GameLabs to be installed on both client and server.

To send stylized RCon messages you prefix the specific messages the following way:

- `|>N` - Sending a notification
- `|>C(HEX)` - Sending a colorized message

Full examples for RCon messages:

```
"|>NThis is a notification"
"|>C37ff00This message will appear green"
```

Messages stylized this way, will not have any prefix.

**Note:** Chat styling is not compatible with every chat mod.

## Logging

GameLabs has an integrated and custom logger. The log files will be generated inside a `@Logging` directory, which is being located in the configured profiles directory.

## Managing User Consent

Depending on your region, you might require a "cookie consent" banner when using client performance metrics (gathering of client game FPS for server metrics, etc.). You can enable this by adding:

```c
#define GAMELABSCLIENTCONSENT
```

in any mod that is loaded before GameLabs on the client.

## Game Server Monetization

The usage of GameLabs on monetized servers is allowed. The usage of GameLabs for commercial use is forbidden in compliance with the DayZ Tools EULA.

## Usage

The usage of GameLabs is subject to the CFTools Cloud Terms of Use.

## Compatibility

GameLabs is compatible with most modifications, however we do not guarantee explicit compatibility with any specific mod.

## Support

No support will be provided via Steam or the Steam Workshop.

For support you can join our [Discord](https://discord.cftools.cloud) or [open a ticket](https://app.cftools.cloud).

## Other Branches

For experimental and unstable features of GameLabs we provide following additional versions of GameLabs:

- Experimental
- Unstable
- Pre-Release

## License

GameLabs and its code is copyrighted content of © 2017 - 2025 CFTools™. All rights reserved.

The usage on both client and server side falls under our [EULA](https://cftools.cloud).

For usage with third party Open GameLabs compatible API servers, contact the operator for licensing information.

## Links

- **Site:** [https://cftools.com](https://cftools.com)
- **Support:** [app.cftools.cloud/support](https://app.cftools.cloud/support)
