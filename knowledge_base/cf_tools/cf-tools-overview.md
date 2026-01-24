# CFTools Cloud Documentation

## Mod Update Notifications

Details about mod update notifications - WebHooks

### Availability
- **Titles:** DayZ
- **Plans:** Basic, Pro, Community, Advanced

Mod Update Notifications backed by CFTools Cloud WebHook Integrations will automatically trigger a WebHook event once an upstream mod update has been detected.

This feature does not require any additional configurations. CFTools Cloud automatically detects which mods your game server has enabled.

There is no need to run additional software and there are no limitations regarding the choice of game server provider.

Mod Update Notifications can be enabled through Server Integrations settings by enabling the `gameupdate.mod_update` event type.

### Steam Workshop Specifics

CFTools Cloud tracks all Steam Workshop items for supported titles. These will be updated every 5-10 minutes.

Mod Update Notifications based on Steam Workshop mods will have a delay based on this tracking cycle.

### Additional Information
- **DayZ:** Server side mod updates will not be tracked
- The notification will be sent once a new version of a mod has been detected. Your game server will require an update. This system does not track if an update has been applied to your game server.

## Player Risk

Learn how Radar calculates and indicates player risk factors

### Overview
Player Risk Indicators are a part of CFTools Radar functionality.

**Plan Availability:** Pro, Community, Advanced

These indicators aim to help you get an early warning for players showing specific factors indicating risk to your server operations. The evaluation includes an analysis of previous activity, current connection information, as well as game play statistics and more.

Player Risk Indicators are evaluated through the CFTools Radar risk model, and is based on a statistical analysis for each unique game title supported by CFTools Cloud. The evaluation is performed live during each game session start.

While certain indicators are easily identifiable by you, the system aids in the automatic identification of a greater number of such indicators and has the ability to detect potentially dangerous conduct that may not be readily apparent to the human eye.

The entire system operates on a false negative baseline, so it will never or only very rarely display players with a wrong category and will always prefer a lower category unless definite risk factors have been identified.

### Risk Categories
Each player is assigned into a risk category based on their Risk Indicator scoring.

#### No and Low Risk
Most players who do not exhibit any or only minimal risk factors are unlikely to cause any disruptions to your game server operations.

#### Risk
Players categorized as "Risk" will have a "Risk Player" label displayed on the server dashboard. This label signifies that the player has been assessed to have a moderate level of risk. This assessment is based on factors such as prolonged anonymization, unusual gameplay statistics, and other irregularities.

#### High Risk
Players who fall into the "High Risk" category will be labeled as "High Risk Player" on your dashboard, and their label will be highlighted in red.

It is crucial to thoroughly assess players in order to maintain the integrity of your game server operations.

#### Risk Indicators
CFTools Cloud tracks various data across all attached servers, as well as game play statistics via GameLabs. All this data is being processed using our Radar specific machine learning models.

## DayZ

### DayZ Game Integration
The DayZ game integration requires our GameLabs plugin to be installed and active on your game servers. More details and installation instructions can be found at https://steamcommunity.com/sharedfiles/filedetails/?id=2464526692.

### Available Features
| Feature         | Availability                                          |
|-----------------|-------------------------------------------------------|
| Map             | ✅ (Requires supported map and Basic plan or higher) |
| Logging         | ✅                                                    |
| API             | ✅                                                    |
| Mod Licensing   | ✅ (Availability on request)                          |
| Game actions    | ✅                                                    |
| Key-Value Store | ✅ (Availability on request)                          |

### Synchronization
DayZ does not offer a stable way of pushing data live to our systems, therefore we bulk updates to reduce stress on your game servers.

| Metric                   | Timing                                     |
|--------------------------|--------------------------------------------|\n| Server metrics reporting | Every 5 seconds, 60 seconds on Free plan   |
| Map data updates         | Every 10 seconds, unavailable on Free plan |
| Game action delivery     | Every 5 seconds, 60 seconds on Free plan   |


## Availability

### About the availability of game integration for the different supported titles
The Game Integration CFTools Cloud offers, allows administrators to fully manage their game servers remotely and track state of in-game resources remotely.

Different titles supported by CFTools Cloud offer different ways to integrate with our game integration interface, but not all do allow this. Furthermore, the available functions differ greatly based on the underlying interfacing options exposed by the game server.

## Public Listing

### Do's and don'ts of public ban listings
Congratulations, your banned list can now be displayed publicly. This means that you now have the option to enable this setting on the Overview page of your ban list.

With this option comes responsibility. You should make sure that your ban list remains objective and reasonable, and that the wording is polite. Your ban list can now also be reported. So, if others feel that you are violating good manners, you run the risk of being removed from the list again.

We advise you to establish some general quality and conduct guidelines with your staff for issuing ban entries, and to review your existing ban entries before enabling the listing option.

For example, if you only issue ban entries for server-specific issues, your ban list would not need to be listed at all. All ban entries should stand up to general scrutiny.

## Ban List Basics

### Basics about ban lists, display status and more
Ban lists are a collection of ban entries, administrators can issue to keep their servers clean of malicious individuals.

Ban entries are enforced on identity or ip level, meaning that you can ban any individual player with a unique identity, or ban a ip address or even entire ip range. Depending on the type of ban you want to issue, this can be done either through the player profile (identity) or through the ban list database (ip).

In order for ban entries to apply, a ban list must be added to a game server. For ban lists that you own, this is achieved through the ban list setting under Servers, Settings, Ban list. Alternatively, you can configure it as primary ban list, to unlock automated banning options for Triggers, and Chat/Name Filters.

A ban list is inherently private, but may be used by other servers or followed, using the share code provided on the ban list overview page. Beyond that, a ban list may become listed or verified.

The listed status is granted automatically for ban lists that exceed certain criteria, which aim at measuring a ban lists outreach, activity and substantiality.  

## Feature Availability

### Feature availability across our supported titles

| Feature              | DayZ | ArmA 2/3 | Rust (closed early access) |
|----------------------|------|----------|----------------------------|
| RCon                 | ✅             | ✅       | ✅                         |
| Server stats         | ✅             | ✅       | ✅                         |
| Player database      | ✅             | ✅       | ✅                         |
| Notes                | ✅             | ✅       | ✅                         |
| Profiles             | ✅             | ✅       | ✅                         |
| Audit Log            | ✅             | ✅       | ✅                         |
| Server Log           | ✅             | ✅       | ✅                         |
| RCon protocol        | ✅             | ✅       | ✅                         |
| Banning              | ✅             | ✅       | ✅                         |
| Whitelist            | ✅             | ✅       | ✅                         |
| Chat filters         | ✅             | ✅       | ✅                         |
| Name filters         | ✅             | ✅       | ✅                         |
| Chat commands        | ✅             | ✅       | ✅                         |
| Localization         | ✅             | ✅       | ✅                         |
| Scheduler            | ✅             | ✅       | ✅                         |
| Messenger            | ✅             | ✅       | ✅                         |
| Triggers             | ✅             | ✅       | ✅                         |
| Integrations         | ✅             | ✅       | ✅                         |
| Queue Priority       | ✅             | ❌       | ❌                         |
| Reserved Slots       | ❌             | ❌       | ❌                         |
| GUID conversion      | ✅             | ✅       | Not applicable             |
| Ping limiter         | ✅             | ✅       | ✅                         |
| VPN protection       | ✅             | ✅       | ✅                         |
| Geo blocking         | ✅             | ✅       | ✅                         |
| Steam integration    | ✅             | ✅       | ✅                         |
| BattlEye integration | ✅             | ✅       | Not applicable             |
| EAC integration      | Not applicable | Not applicable | Closed beta          |


## Troubleshoot BattlEye RCon

### Troubleshoot BattlEye RCon
BattlEye RCon is used in many titles. The features and setup differ per title.

**Relevant titles:** DayZ, ArmA 2, ArmA 3, ArmA Reforger

*Title not listed? Check for the correct troubleshooting guide here: RCon Troubleshooting*

### DayZ, ArmA 2, ArmA 3

#### Locate your RCon configuration and verify it exists
1. Check your game servers launch parameters for `profiles` or `battleye` parameters. `battleye` overrules `profiles` for RCon configuration placement.
2. Open the target folder location
3. Check if a `BEServer_x64.dll` or `BEServer_x64.so` file exists in the folder
   - If none exists, you are not in the correct folder
   - If one exists, proceed with the troubleshooting
4. Locate a file `BEServer_x64.cfg` the file might have a `_active_{code}` suffix
   - If the file does not exist: RCon has not yet been set up: Set up RCon
   - If the file exists, proceed with the troubleshooting
5. Verify the parameters `RConPort` and `RConPassword` are set (case sensitive)
6. Verify the `RConPassword` value does not contain any non alphanumeric (only numbers and normal letters, no special characters) and is not over 24 characters long
7. (If using shared hosting, or fixed static ip address) check that an `RConIP` parameter is set and the value is the same one your hosting provider has given you (through UI or other means of communication) or otherwise matches the launch parameter the server is bound to

#### Check server log if RCon is correctly loaded
1. If `-dologs` (launch parameter) is not enabled, enable it to receive game server logs
2. If `logFile={path};` is not set in your serverDZ.cfg, enable it to receive the game server console logs
3. Check the `profiles` folder (or the equivalent for your hosting provider) for `server_console.log` or its equivalent based on your serverDZ.cfg configuration for the `logFile` parameter
4. Scan the log output for early log lines starting with `BattlEye`
5. The log lines should contain your full RCon configuration, if it doesnt show up, or the content is not correct, revise your RCon configuration: Set up RCon

#### Verify network connectivity
1. Gather the game server ip, the configured RCon port and the configured RCon password
2. Download BE RCON (https://www.battleye.com/downloads/) (or any similar utility for simple testing)
3. Start the program on your personal device (or a different device if your server is located on the same device as you are testing on)
4. Enter the connection details you have gathered

**If you are seeing a connection error:** Your router and/or firewall is not correctly configured for RCon traffic. Revise firewall/router policies.
- RCon traffic is UDP, inbound on the configured RCon port.

**If you are not seeing any errors:** RCon is correctly set up


## BattlEye RCon

### BattlEye RCon
BattlEye RCon is used by the following CFTools supported titles:
- DayZ (PC)
- ArmA 2
- ArmA 3

### General
BattlEye RCon is a configurable optional UDP based protocol allowing specific remote control operations to be made for supported game servers.

The BE-RCon interface can be configured through a dedicated configuration file `BEServer_x64.cfg` (Windows) or `beserver_x64.cfg` (Linux).

### Configuration File
The location of the configuration file is dependent on the hosting environment, and does not have a pre-defined place.
Common locations are within `profiles/BattlEye` (`profiles` may be `config` or `SC` or be named differently). It is generally located where the `BEServer_x64.dll` is located.

The configuration syntax does not allow for many options, the documented functioning parameters are documented in the table below.

| Parameter    | Possible value | Details                                                                                                                                                                                                            |
|--------------|----------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
| RConPassword | `<string>`     | Your RCon password. Maximum of 32 characters. No special symbols or spaces allowed.                                                                                                                               |
| RestrictRCon | 1 or 0         | When set to 1, this will restrict all RCon connections and prevent certain actions such as kicking, banning or shutting the server down. When not defined, default value is 1.                                   |
| RConPort     | `<int>`        | Allows to change the port BattlEye listens for RCon traffic.                                                                                                                                                      |
| LogFile      | `<string>`     | (OPTIONAL) Path to where a log file of RCon communication should be stored.                                                                                                                                        |
| RConIP       | `<string>`     | (OPTIONAL) IPv4 for the RCon interface. Should only be used if the game server itself has been bound to a specific network interface.                                                                            |

### Firewall considerations
BattlEye RCon is a UDP based protocol running on the configured RConPort.

We suggest the RConPort to be the game port + 3.

**Example:** Game Port: 2302; RConPort = 2302+3 => 2305

### CFTools Cloud
The RCon interface must be available over the internet and firewall rules must be made appropriately.

For kicks etc. to function `RestrictRCon` must be set to the value of `0`.

## Legitimate URIs

### CFTools Cloud URIs
CFTools Cloud uses multiple URIs to provide its services. You may find a list of these in the table below.

| URI           | Status | Usage               |
|---------------|--------|---------------------|
| cftools.cloud | Active | Client & API        |
| cftools.com   | Active | Client & API        |
| cftools.dev   | Active | API                 |
| cftools.de    | Active | API & CDN           |
| cftools.tech  | Active | API & DNS           |
| cftools.email | Active | E-Mail delivery     |
| cftools.me    | Active | Profile short-links |

### Non CFTools branded domains used:

| URI              | Status   | Usage     |
|------------------|----------|-----------|
| bancheck.io      | Inactive | API       |
| gamelabs.cloud   | Active   | API       |
| usrcdn.com       | Active   | API & CDN |
| gameserver.cloud | Inactive | -         |

**Warning:** Domains not listed and sending traffic or being accessed may be malicious and you shall proceed with caution.

You can report such incidents by e-mail to abuseteam@cftools.cloud

## Server Metadata Crawler

### Information about how our systems retrieve server metadata
**Note:** This information is accurate for server metadata only and does NOT apply to RCon.

CFTools Cloud is one of the consumers of your game servers metadata interface. The type of interface used and underlying protocol depends on the game server title you are operating.

| Title            | Interface                               | Protocol |
|------------------|-----------------------------------------|----------|
| DayZ (PC)        | Steam & Bohemia Interactive proprietary | A2S      |
| ArmA 2           | Steam & Bohemia Interactive proprietary | A2S      |
| ArmA 3           | Steam & Bohemia Interactive proprietary | A2S      |
| Rust             | Steam                                   | A2S      |
| Hell Let Loose   | Steam                                   | A2S      |
| Squad            | Steam                                   | A2S      |
| DayZ (PS4, XBox) | Steam (limited)                         | A2S      |

These interface operate from a "query port" which must be available to all players, Steam and our crawlers. Without this server metadata, CFTools Cloud and more important your players are not able to properly find your server in server browsers.

You need to configure this query port in your server configuration, and it must only be once. Multiple servers may not use the same port, and the port can not be used for anything else while in use. You may need to create firewall rules in your system and network level firewall appropriate to your configuration and environment.

Our crawlers operate from a dedicated IPv4/IPv6 (if supported) for each individual title. You may find the used address below:

| Title          | IP            | Supported IP protocols |
|----------------|---------------|------------------------|
| DayZ (PC)      | 162.55.52.17  | IPv4                   |
| ArmA 2         | 5.75.145.245  | IPv4                   |
| Hell Let Loose | 5.75.145.245  | IPv4                   |
| Squad          | 5.75.145.245  | IPv4                   |
| ArmA 3         | 159.69.10.10  | IPv4                   |
| Rust           | 91.107.224.81 | IPv4                   |


## GSP Information

### Wanting to let your customers use CFTools Cloud with ease?
CFTools Cloud is a SaaS solution for game server administration and management. Your customers may use CFTools Cloud for various tasks regarding their game servers in regards to administration, automation and player interaction.

The core CFTools Cloud platform, works based off RCon. Each game title has different RCon protocols and specifications. The fundamental requirement is that the game title supports RCon, and you are properly configuring and exposing the RCon interface.

In addition to RCon, Steam based game servers require to be indexed to properly function with the platform. Our Steam metadata crawlers are documented here: https://help.cftools.com/en/technical/server-metadata-crawler

### Technical recommendations

#### DayZ
DayZ blocks game port +2 & +4 for internal use.

**Recommended RCon port allocation:** game port +3

DayZ RCon adheres to the BattlEye RCon protocol eg. utilizes UDP and sends a high frequency of packets, rate limiting should be set to higher frequencies +/- 300 pps

#### ArmA 2
DayZ blocks game port +4 for internal use.

**Recommended RCon port allocation:** game port +3

ArmA 2 RCon adheres to the BattlEye RCon protocol eg. utilizes UDP and sends a high frequency of packets, rate limiting should be set to higher frequencies +/- 300 pps

#### ArmA 3
DayZ blocks game port +4 for internal use.

**Recommended RCon port allocation:** game port +3

ArmA 3 RCon adheres to the BattlEye RCon protocol eg. utilizes UDP and sends a high frequency of packets, rate limiting should be set to higher frequencies +/- 300 pps

## Server Rating

### CFTools Server Rating
The Player Hub sports a server list and server profiles. While each server has its own unique aspects, we try to generalize player appeal based on overall statistics and performance values for each server.

CFTools calculates a rating based on following parameters:
- Server uptime
- Player counts
- Queue counts
- Server latency within the respective region

Servers that are modifying or misrepresenting certain characteristics, for example spoofing player counts, will be automatically excluded from the rating and be less visible in the overall server list.

ADM Log Pending
The "ADM Log Pending" warning appears if OmegaManager has not yet located an active .ADM file to monitor for server events. This will happen on each server start for a maximum duration of 60 seconds. After this period a useable .ADM file should have been located. Should the message appear when the game server is still running, an error occurred locating the active file.

In most cases, the .ADM log file has been disabled, you can check if you have removed the "-dologs" or "-adminlog". Removing any of them will prompt the DayZ server to not generate an .ADM log file resulting the the "ADM Log Pending" message to stay during the entire runtime.

Game/Workshop updates not functioning
Should you encounter the issue of your deployments no longer updating in case of game or Workshop item updates, you are encountering a SteamCMD issue. This requires advanced debugging using the raw OmegaManager console.

The first step is to highlight the OmegaManager console and trigger a manual upstream check. Now you will see several SteamCMD related messages printed in the console, and you will also be able to see the issue you are encountering.

Rate limit errors
Your account got rate-limited from logging in to Steam. This automatically blocks your server from logging in to any particular Steam account for 1 to 48 hours. This can not be circumvented and does not require any manual work to get resolved.

Steam guard / 2FA issues
We do not recommend using 2FA on the used Steam account due to common authentication issues and we can not provide support for issues that stem from it. The easiest way to get rid of this issue is to disable 2FA. For securing your Steam account, we recommend using the e-mail Steam Guard level and using a 64 character alpha numeric password.

Access denied for individual updates
Your account either does not own DayZ, or got banned from the Workshop. Nothing we can do here, except use a different Steam account or buy DayZ.

No longer receiving messages for shutdowns and updates
OmegaManager uses an RCon based approach to lock, kick and send messages for its shutdown and update procedures. The configuration for the RCon interface is automatically loaded from your BattlEye RCon configuration folder.

Should the messaging no longer work - without configuration change - there are two possible reasons for this:

RCon port has been double allocated
RCon configuration has been doubled/copied and contains conflicting information
RCon port has been double allocated
Issue: Multiple game server deployments attempt to use the same RCon port. Only the first one to boot will reserve this port and the other RCon interface will simply fail to start.
Solution: Go through all RCon configuration files of all server deployments, and check the port configurations. If more than one deployment uses the same port, adjust the port. Also check if your firewall has opened this new port (host & provider)
RCon configuration has been doubled/copied and contains conflicting information
Issue: The BattlEye RCon folder contains more than one configuration file with conflicting configurations. This may happen if a server has been copied and the RCon port was not adjusted, or in rare cases if the RCon interface did not properly shut down, some files may double and leave leftover files which are not automatically cleaned up.
Solution: Open the RCon configuration folder (profiles/BattlEye) of the impacted server deployment and look for RCon configuration files. These may be called BEServer_x64.cfg or some variation of it containing additional random characters. If there are more than one, go through each and delete the one that contains outdated information. You should only have one configuration file in this folder.

## OmegaManager - Windows Server

### Learn how to install OmegaManager on your Windows system

#### Installation requirements
- Windows Server 2016 or newer
- A Steam account with a valid DayZ license and access to the Steam Workshop
- At least 30 GiB of free disk space (SSDs offer the best performance)

#### Installation steps

##### 1. Download OmegaManager
To download OmegaManager, access following link: Download

*OmegaManager and all usage falls under the OmegaManager EULA, available here*

##### 2. Creating the directory structure
On your server Desktop, create a folder called "OmegaManager". Move the downloaded OmegaManager.exe into the OmegaManager folder.

##### 3. Seeding process
OmegaManager installs itself using a self-contained installation script. To install, just double click the OmegaManager.exe and wait for the process to complete.

You will see several folders being created during this process and you will be prompted to install the required third party software in order to run the DayZ server process.

Once completed, you will be automatically prompted to edit the OmegaManager configuration file called manager.cfg.

##### 4. Basic configuration
Within the manager.cfg configuration file, which has been automatically opened, you now have the option to set up everything to your liking. Most settings have been pre-configured to suit the most common setups and is thus considered the express installation.

The only required settings at this time are your Steam account credentials, which need to be entered into the appropriate fields.

**Note:** Steam Authenticator / Steam 2FA can not be used with OmegaManager as of 07.02.2020 and must be deactivated in your Steam account settings

As of OmegaManager, you no longer need to configure a Steam API key, as it will retrieve all information from our official Steam relay system.

##### 4. Optional configuration
We generally recommend to change your Windows DNS servers to a public resolver, instead of using ISP or hosting provider ones. Our recommendation in this case is the 1.1.1.1 Cloudflare DNS (https://1.1.1.1/dns/).

##### 5. Perform a system reboot
In order for all dependencies to fully install and register with your system, you must now perform a reboot of your operating system. Please use the "Reboot" option instead of shutdown.

##### 6. Start OmegaManager
To start OmegaManager, navigate back to the installation folder and double click the executable.

OmegaManager will now perform its initial boot routine and download the DayZ server files and place them within its folder structure.

Once this process is completed, you can access the OmegaManager user interface at http://localhost:8081

OmegaManager is now installed and running, for configuration options and other considerations, please navigate back in the documentation document.

## Enabling Unicode Support

### OmegaManager requires Unicode support, learn here how to enable it.

1. Press Win+R on your keyboard
2. Type `intl.cpl` and press enter
   - This will open the Windows Region setting window
3. Select the **Administration** tab
4. Click on **Change system locale**
5. Tick the box for enabling Unicode UTF-8 support
6. Press **Ok**
7. Press **Apply** and then **Ok**

## Remote Access

### Learn how to access OmegaManager from remote systems

#### Proxy
*This is the recommended approach*

To make the OmegaManager interface available to the public it is best to set up a reverse proxy using Apache, nginx or similar.

Setting up a reverse proxy can be achieved by following this guide: https://httpd.apache.org/docs/2.4/howto/reverse_proxy.html

Additionally, it is recommended to set up a form of authentication (HTTP Basic Auth etc.) and to utilize HTTPS when communicating with the webserver.

#### Native webserver
The OmegaManager has a integrated "internet mode" which exposes the OmegaManager port to all available networking interfaces and launches a HTTPS server instead of HTTP with self-signed certificates. The generated certificates are self-signed and thus not recommended to use in production. They will be stored in the `certs` directory.

To re-configure the OmegaManager for this following adjustments need to be made to the manager.cfg file:

```json
"webserver": {
    "port": 8081,
    "internet_accessibility": true,
    "authentication": true,
    "username": "username",
    "password": "changeme"
}
```

| Parameter              | Description                                                                  |
|------------------------|------------------------------------------------------------------------------|
| port                   | Which port the OmegaManager listens on                                       |
| internet_accessibility | Whether to expose the webserver to all interfaces or only bind to localhost  |
| authentication         | Enable HTTP basic auth                                                       |
| username               | HTTP Basic Auth Username                                                     |
| password               | HTTP Basic Auth Password                                                     |

## Introduction

### What is OmegaManager and how can it benefit you?
OmegaManager is a software to automate your daily tasks as a DayZ server operator and drastically reduce your overall maintenance requirements.

Using a full Steam integration, it is capable of downloading, installing and automatically updating your server deployments as well as workshop items.

The integrated monitoring system makes sure that your game servers are always running and issues process restarts should it notice a crash of your game server happen. No action required, OmegaManager watches your game servers 24/7, 365 days a year.

To learn how to download and install OmegaManager on your system, you may refer to the OS specific installation instructions available within this space.

## Configuration and Workflows

### Documentation for common configuration parameters and instructions on how to perform basic tasks

#### General information

##### General considerations
- Dual CPU setups are not supported
- Steam account requires owned copy of DayZ to download and manage mods
- The launch parameter `limitFPS` is not supported
- Large mods that exceed 800 MiB in size are not properly handled by SteamCMD and require either a manual download or several restarts of the OmegaManager. Subsequent updates will work flawlessly

##### Creating server deployments
- You can not copy and paste or import your existing server. You have to deploy and configure a new instance
- You can not run the OmegaManager with the same Steam account you are logged in to the Steam Client on the same computer

##### Existing server installations
OmegaManager requires a specific directory layout along with its own configuration file. Therefore adding existing servers is not possible.

To add existing installations, a new deployment needs to be created. Afterwards all existing configuration files and the database can be copied over.

##### New server deployments
You can create new server deployments using the **Deploy Server** button.

##### Stopping OmegaManager
OmegaManager should be stopped by pressing `CTRL+C` while the OmegaManager console is focused. This will ensure a clean exit of OmegaManager.

##### Adding non-workshop mods
1. Create new directory called `@%yourmodname%` in the server root
2. Open `omega.cfg`
3. Copy existing mod configuration and adjust directory and set `file_id` to `0`
4. Save and close `omega.cfg`
5. Restart game server

#### manager.cfg Configuration

| Setting                            | Function                                                                                                          | Note                                                                                                                                                                                                                                                                              |
|------------------------------------|-------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| debug                              | Enable debug logging.                                                                                             | Enable this should you experience any issues with OmegaManager and require support.                                                                                                                                                                                               |
| steamcmd_debug                     | Only to be used in conjunction with steam.mode "tty".                                                             | Enables raw Steam output to console.                                                                                                                                                                                                                                              |
| steam.mode                         | "tty" or "basic". Defines the mode SteamCMD is being used in.                                                     | "tty" places a lock on the Steam account, meaning it can not be used for anything else, including additional OmegaManager instances. However, it is more resilient and does not prompt rate limit errors.                                                                         |
| steam.username                     | Your Steam username.                                                                                              |                                                                                                                                                                                                                                                                                   |
| steam.password                     | Your Steam password.                                                                                              |                                                                                                                                                                                                                                                                                   |
| steam.api_key                      | A valid Steam API Key                                                                                             | When registering with Steam, use your domain name or "localhost".                                                                                                                                                                                                                 |
| steam.mobile_authenticator         | Enable when using the Steam Mobile Authenticator for the Steam account.                                           |                                                                                                                                                                                                                                                                                   |
| deployment.firewall_rules          | Whether or not OmegaManager should automatically manage Windows firewall entries.                                 |                                                                                                                                                                                                                                                                                   |
| hosting.system_space               | Run all processes as a system service                                                                             | This has an impact on performance when running multiple servers in parallel. This will prevent any non elevated access to the process. Process detection will be automatically enabled when using this setting. Do not have multiple servers configured with the same game ports. |
| hosting.interactive                | Display the DayZ console window when run in SYSTEM space                                                          | Keep this off, unless you definitely need it                                                                                                                                                                                                                                      |
| updater.workshop_force_upstream    | Do not attempt to use CFTools Data API system and only rely on Steam Workshop API                                 |                                                                                                                                                                                                                                                                                   |
| updater.experimental               | Switch SteamCMD to use experimental branch of DayZ                                                                |                                                                                                                                                                                                                                                                                   |
| updater.shutdown_gameservers       | Shutdown game servers if game update is detected                                                                  | May be changed per instance                                                                                                                                                                                                                                                       |
| updater.shutdown_on_mod_update     | Shutdown game servers if Workshop item update is detected                                                         | May be changed per instance                                                                                                                                                                                                                                                       |
| updater.shutdown_ignore_serverside | Do not shutdown game servers if updated Workshop item is serverside                                               | May be changed per instance and item                                                                                                                                                                                                                                              |
| updater.interval                   | Base interval in seconds for update checks                                                                        | Do not use a value below 300 seconds                                                                                                                                                                                                                                              |
| updater.grace_period               | Duration in which shutdown or update notice is sent and server kept online after update has been detected         | Do not use a value above the configured updater interval                                                                                                                                                                                                                          |
| updater.notify_interval            | Interval in which shutdown or update notice is sent                                                               | Value in seconds                                                                                                                                                                                                                                                                  |
| updater.rcon_lock                  | Lock server when applying mod/game updates.                                                                       |                                                                                                                                                                                                                                                                                   |
| updater.rcon_kick_delayed          | Kick players when applying mod/game updates.                                                                      |                                                                                                                                                                                                                                                                                   |
| updater.rcon_kick_delay            | Delay of when to kick players relative to server shutdown. eg. X seconds prior to shutdown.                       | Value in seconds                                                                                                                                                                                                                                                                  |
| manager.discord_avatar_url         | Modify Discord avatar url for Discord WebHooks                                                                    | URL must be available from the internet, can not be a local file                                                                                                                                                                                                                  |
| manager.discord_username           | Modify Discord username for Discord WebHooks                                                                      |                                                                                                                                                                                                                                                                                   |
| manager.shutdownhandler            | Disable registration of the OM shutdown handler. This will result in servers being kept active when OM closes.    | true / false, Default: true                                                                                                                                                                                                                                                       |

## Architect - Frequently Asked Questions

### Frequently asked questions about Architect

#### Q: Architect Manager is not connecting to my Agent

Architect Manager is connecting to your Agent based on its IP-address and port. The port used for Architect (8090 by default) must be forwarded in your firewalls.

- **Protocol:** TCP
- **Direction:** In & Out

#### Q: Can Architect be used with game server providers?

Architect exists to automate self-hosted environments. When using a game server provider, you will not be able to install Architect.

#### Q: Can I move servers between OmegaManager and Architect?

This is not possible. Architect works based on a database system and existing servers or servers maintained through OmegaManager can not be added.

#### Q: I dont see any DayZ/other title console window popping up

In order to improve CPU scheduling for game servers, these are run in "service mode" (Windows). This results in the game server processes to be better scheduled within Windows and ends up more stable in the long run.

#### Q: How do I get the console windows back?

Should you absolutely require the console windows, you need to start Architect in foreground mode and not as a Windows service. You can do so by adding the flag `--mode debug` to its launch parameters.

**Note:** This will not launch Architect as Windows service!

#### Q: What does "volatile" mean for game branches

We mark specific game branches a volatile when they update very often. This will lead to your game servers restarting often and updating often. So these should not be used for production game servers.

#### Q: Why can't I use certain ports when deploying servers?

Architect automatically checks your suggested port configuration against servers locally deployed. If the ports are blocked by an existing game server, these can not be re-used. This is a safeguard against double port allocation.

#### Q: When I change the RCon password in my files, the change is not deployed

Architect is maintaining your RCon configuration files automatically. You need to set an RCon password through Architect Manager or through the API.

#### Q: Why is there a "cache" directory created in my file system?

Architect is locally caching files used for your game servers. This makes it faster to deploy new servers, as well as perform "difference based updates". Meaning that files that you have modified will not be touched during updates.

This folder and its contents are required and should never be touched.

## Moving an Agent Installation

### Move an agent installation to either a different folder/drive or system

#### Moving individual Agent directories
Depending on requirement, you may not require to move the entire installation, it is possible to change the locations of the following directories:

```toml
# Internal folder structure
# database_dir = "" # optional override for database directory, full path
# log_dir = "" # optional override for agent logs directory, full path
# deployments_dir = "" # optional override for deployments directory, full path
# cache_dir = "" # optional override for cache directory, full path
# certs_dir= "" # optional override for certs directory, full path
# backups_dir= "" # optional override for backups directory, full path
```

**To perform this change:**

1. Stop the Agent
2. Create new directory at new target location
3. Copy the contents of the current folder you want to override to the new location
4. Update the `config.toml` according to the changes you intend to make
5. Restart the Agent

#### Moving an Agent to a new installation location
**Before going forward, verify that this change is absolutely required as it may result in issues.**

Follow these steps:

1. Stop the Agent
2. Open a Windows CMD / Linux Shell and navigate to the Agent installation directory
3. Execute the following command:

```bash
# Windows
ArchitectAgent.exe --mode=remove --tray-uninstall

# Linux
ArchitectAgent --mode=remove
```

4. Create new directory at target location
5. Copy the entire contents of the existing installation to the new location
6. Modify the `agent_dir` parameter within `config.toml` to point to the new location
7. Execute the following command:

```bash
# Windows
ArchitectAgent.exe --mode=install --tray-install

# Linux
ArchitectAgent --mode=install
```

#### Moving an Agent between systems
The agent can not be copy-pasted between systems.

It is not possible to transmit agent settings between installations.
Given you have already installed the agent on a new system, perform following actions to transmit the server deployments:

1. Click "Export" under Server, Maintenance for each game server deployment you want to migrate
   - This is a LONG running task as all files within the deployment will be packed alongside metadata about the deployment itself. To speed up the process, delete ALL UNNECESSARY files before creating the archive.
2. Upload all generated export files to the new agent installation directory where the ArchitectAgent(.exe) resides
3. Prepare the deployment of the archived deployments by switching to the archive deployment mode on the new agent
4. Start the deployment process for a new server, and allocate new ports or re-use the ports for the existing deployments
5. Wait for the archive deployment to complete.
   - This is a LONG running task as all titles, mods will be downloaded checked and restored, alongside unpacking all existing data.
6. Once all deployments have been deployed from their respective archives, you have fully copied the entire game server to their new agent. You can now go through the process of setting up the agent environment, (users, webhooks etc.) to your liking again.

## Updating an Architect Agent

### Manually updating an Architect Agent
This applies only to manual agent updates, should your agent not be automatically updated.

#### Windows
1. Download new `ArchitectAgent.exe`
2. Stop Architect Agent through Task Manager
3. Open Architect Agent installation directory in your Windows explorer
4. Replace existing `ArchitectAgent.exe` with the newer version
5. Re-Start Architect Agent through Task Manager

#### Linux
1. Download new `ArchitectAgent`
2. Stop service
   ```bash
   systemctl stop architect-agent
   ```
3. Navigate to the Architect Agent installation directory via `cd`
4. Replace existing ArchitectAgent with the newer version
5. Start service
   ```bash
   systemctl start architect-agent
   ```

## Windows Interactive Processes
title:Windows Interactive Process tag:easy_language
This information applies to Windows only
Architect Agent is a Windows service. This means that the service will start and run in the background. The Agent is not a desktop application and thus will not show up when you access your Windows GUI.

As the Agent is run as a service, it runs in Windows special SYSTEM space. This space is reserved for services and all other core functions running in a separate and isolated space.

When the Agent is now running and attempting to start game server processes, the processes will also be started in the SYSTEM space.

When you log in to Windows, you are logging in to a specific user account, for example Administrator. This user is not the SYSTEM user, so it does not see the console windows for game servers.

### Enforce Interactive Processes
To run the game servers processes within a normal user account, the Agent can employ a Windows technique called "token duplication" to grab a token from a logged in user and then use it to start the game server processes.

This will result in the process showing up when logging into the Windows GUI and the process being run as the selected user.

It is important to note that this only works, if the user account was logged in to at least once, prior to the Agent starting. When you reboot your Windows system, and have your servers on auto start, the first time, the console will not show up when logging in. Log in once, or set up Auto-Logon, and the console will then show up.

### Configuring interactive processes

This is a snippet of the config.toml, you need to place it at the appropriate position within your existing config.toml:

```toml
[windows]
start_server_non_interactive = false
session_username = "USERNAME" # case sensitive
```

Place the snippet inside your existing config.toml. If these parameters are already defined, but commented out (# in front) then uncomment them and fill in the username. The username must be case sensitive.

If your username is Administrator, you need to write Administrator. The user name is case sensitive.

## Download System

### Insights about the Agents download system
Downloads differ based on the specific title and ecosystem

#### Steam
**China:** Agents located in China will automatically select Steam China CDN servers, this can be overriden only through your config.toml

Steam based downloads are handled automatically with no additional setup required.

The Agent will automatically select a CDN server based upon Steams preferences in your region. The exact sorting depends on the overall load of the individual CDN servers.

It will always prefer CDN servers that are under lower load. Should the Agent encounter issues with individual CDN servers, it will be excluded from downloads. The list of available CDN servers are refreshed every 24 hours or if there are no download servers eligible for download (due to blacklisting).

#### Download Pipeline
By default, the agent will process downloads like a normal Steam Client, eg. select multiple Steam CDN servers for download processing and the download as fast as possible. Chunks are cached in memory until they are written to disk.

This behavior allows for extremely fast downloads, but may not be suitable for every situation.
In case of memory issues, the memory buffer for downloads can be adjusted through `disable_buffered_download`. The overall CPU/Net I/O consumption can be controlled by limiting parallel downloads through `download_batch_size`.
For details revise your config.toml under reference from available configuration parameters.

## Agent Firewall Entries

### Firewall rules required for the operation of the Architect Agent

All traffic inbound and outbound from the Agent is HTTP WebSocket traffic.

Traffic from the Manager to your Agent(s) is by default using self signed certificates and using WSS (WebSocket Secure) eg. WebSocket via TLS.

The port used for your Agents is 8090 by default, but may be changed. If changed, your firewall rules must reflect this as well.

**Firewall rules required for each agent:**

- TCP inbound for agent port
- TCP outbound for agent port
- TCP inbound for the corresponding cloud controller gateway
- TCP outbound for the corresponding cloud controller gateway

**FQDNs required to be whitelisted for Agent operations:**

- gw.gameserver.cloud (Global default)
- ru.gw.gameserver.cloud (Moscow, Russia)
- us-e.gw.gameserver.cloud (US East, used for entirety of NA and SA)

### IP resolving

IP addresses for all cloud controllers are not static and might change. Whitelisting based on port/hostname should be preferred.

| Hostname                 | Loc.   | IPv4           | IPv6          | Ports            |
|--------------------------|--------|----------------|---------------|------------------|
| gw.gameserver.cloud      | Global | 88.99.150.149  | Not supported | 8080, 8081, 666  |
| ru.gw.gameserver.cloud   | Russia | 5.129.200.120  | Not supported | 8000             |
| us-e.gw.gameserver.cloud | NA, SA | 5.78.163.44    | Not supported | 8080             |

## System Requirements
Minimum and recommended system specifications for Architect
These are the system requirements and recommendations for Architect Agent. 
Game servers need to be considered separately.
Minimum requirements
1 CPU core @ 2.0 GHz (x64, x86 architecture)
500 MiB free RAM
1 GiB free disk space (SSD)
16 MB/s network connection
Persistent internet connection to licensing server required
(Network requirements)
Windows: Windows Powershell must be available on the system
Full administrative privileges are required on the system
Recommended specifications
2 CPU core @ 2.0 GHz (x64, x86 architecture)
2 GiB free RAM
1 GiB free disk space (NVME SSD)
100 MB/s network connection
Persistent internet connection to licensing server required
(Network requirements)
Windows: Windows Powershell must be available on the system
Full administrative privileges are required on the system
Additional notes
Some hosting providers require specific system settings for the Agent to function correctly, you can review these here.

Any installation or usage of the Architect Agent falls under it's license agreement. For usage on shared systems, the software administrator must inform all users about the license agreement and ensure their compliance.

Compatible operating systems
Windows	Linux
Windows Server is recommended. Client/Home versions are not officially supported.

Windows Server 2016
Windows Server 2019
Windows Server 2022
Windows Server 2025
Not officially supported

Windows 10 (Professional)
Windows 11 (Professional)
Debian 11
Debian 12
Ubuntu 20.04 LTS
Ubuntu 24.04 LTS
May be run in a containerized environment.

Considerations for game server deployments
Each game server deployment requires additional disk space
System specifications for individual game server deployments must be kept in mind at all times
Game servers are optimally run on non-virtualized hardware
For best performance a SSD should be used

Windows Operations
Architect Agent specifics for Windows
Architect Agent is by default installed as a Windows Service. With that, Architect will automatically start up on system boot, and automatically restart itself should it be shut down unexpectedly.

You can control the service either through Windows Task Manager or Windows Service Manager.

Running in service mode allows the Agent to start fully in background and take advantage of service exclusive features like starting game server processes in service mode to enhance CPU scheduling.

Unlike OmegaManager, Architect Agent will not show a console window by default.

Title and mod cache
Learn about caching
Architect downloads all files on-demand and caches the latest up-to-date version locally.

You can find the raw file cache under the folder name `cache`. The cache for each title is differentiated into bundles and mods.

Bundles
A bundle contains a full server deployment. This acts as a template to quick deploy new servers and reference when updating deployments.

The bundle cache exists only once per title instead of twice with OmegaManager.

You can clear bundles by deleting the title in Manager under Titles. This requires that the title is not currently in use by any deployment.

Mods
Mods are cached the same way bundles are, however their lifecycle is fully dependant on the mod configuration of your servers.

Should no server be actively using any specific mod, the mod cache directory will automatically be wiped.

Configuration
Architect Agent config.toml
The Architect Agent comes with certain fixed settings that are loaded at startup. You can adjust the Agent's behavior by changing specific values in this configuration.

Default configuration
[authorization]
# Replace <license_key> with your license key
license_key = "<license_key>"

# Option to disable "root" user access from remote networks (limits to localhost/127.0.0.1)
# disable_remote_root = false # accepted values: true, false

# Fail2Ban automatically blocks authentication attempts from ip addresses trying to authenticate with wrong credentials
fail2ban_attempts = 5 # accepted values: numeric
fail2ban_ban_time = 60 # accepted values: numeric, time in seconds

[logging]
# Allows you to enable console and debug logging
verbose = true # accepted values: true, false

# How long API audit logs are retained
audit_logs_retention = 7 # accepted values: numeric, time in days

[filesystem]
# Insert the full path where you want to install the Agent
agent_dir = "<installation_directory>" 

# Limit maximum file size to be downloaded through read_file/download_file
# max_manager_download_size = 32 # accepted values: numeric, size in mib

# Internal folder structure
# database_dir = "" # optional override for database directory, full path
# log_dir = "" # optional override for agent logs directory, full path
# deployments_dir = "" # optional override for deployments directory, full path
# cache_dir = "" # optional override for cache directory, full path
# certs_dir= "" # optional override for certs directory, full path
# backups_dir= "" # optional override for backups directory, full path

# Lifecycle hooks
# python_path = "" # optional path to your python installation you want to use, omit for auto discovery

[http_server]
# Allows you to rebind Architect to a specific network interface
address = "0.0.0.0" # 0.0.0.0 means that Architect will listen to all network interfaces and ip's

# Port which Architect agent will listen on for Architect Manager and API connections
port = 8090 # default: 8090

# Whether or not to use SSL for connections, turning this off is NOT recommended
# You can exchange the SSL certificates with custom ones by replacing the self-signed ones in `certs`
use_ssl = true 

[steam_servers]
# Timeout for chunk download from Steam CDN
chunk_download_timeout = 5 # accepted values: numeric, time in seconds

# Allowed concurrent chunks
# Higher values will increase your CPU/RAM usage
# download_batch_size = 60 # accepted values: numeric

# Maximum parallel downloads per Steam CDN server
# The default is 8. Safe values are 8-16. Higher values will result in individual chunk downloads 
# failing due to rate limitations
# max_downloads_per_cdn = 8 # accepted values: numeric

# Option to disable caching of downloaded chunks in memory and instead write to disk as .part files
# Useful for low memory machines
# disable_buffered_download = false # accepted values: true, false

[dayz]
# Enable DZSALauncher queries
dzsa_launcher_update_enable = true # accepted values: true, false

# Interval for DZSALauncher queries
dzsa_launcher_update = 60 # accepted values: numeric, time in seconds

[rcon]
# Disable RCon integration for Agent
disable_rcon = false # accepted values: true, false

# Optional local network ip address in case 127.0.0.1 does not resolve
# rcon_ip_address = "" # accepted values: ipv4, ipv6

[windows]
# Set an optional execution policy for Powershell scripts (lifecycle hooks)
# powershell_execution_policy = "Bypass" # accepted values: str, a valid Windows Powershell Execution policy

# Control if server should be pushed to a user session in order for the console to be displayed
# start_server_non_interactive = false # accepted values: true, false

# Control which session should be hijacked, falls back to non interactive if hijacked fails
# When empty, uses a random active session
# session_username = "" # accepted values: Windows username (Case Sensitive)

Installing an Architect Agent
Installing an Architect Agent
Beta version downloads are available through Discord

discord.cftools.cloud
Any Agent installation requires a license key

License keys are valid for a certain amount of Agent installations. For details, check your purchase confirmation.
Prior to any installation, please check the system requirements.


Some providers require specific system settings for the Agent to function correctly, you can review these here.
Windows
Beta version downloads are available through Discord

discord.cftools.cloud
Full non-arbitrarily restricted administrator privileges are required on the system.
Video Walkthrough: https://www.youtube.com/watch?v=7cre0XxOaiM

Installation through automated installer
Download installer through your CFTools Cloud account
Execute installer
Enter license key
Finalize installation
Perform base configuration
Verify firewall rules are set for your Agent port (TCP, inbound and outbound)
Retrieve `root` user password, from agent installation directory from `root.txt` file
Manual Installation
Advanced topic, installation through installer is recommended
Create directory structure where you want to install your Agent
Download executable through your CFTools account
Move executable to installation directory
Create config.toml alongside executable (config.toml format)
Start command prompt (CMD/Bash) as Administrator
Install agent as Windows service through the command
ArchitectAgent.exe --mode install
Linux
Beta version downloads are available through Discord

discord.cftools.cloud
ARM is not supported
List of supported Linux distros: System requirements
All steps must be executed as root user.
Installation via systemd/systemctl
Download installer through your CFTools Cloud account
Execute installer
Enter license key
Finalize installation
Perform base configuration
Verify firewall rules are set for your Agent port (TCP, inbound and outbound)
Retrieve `root` user password, from agent installation directory from `root.txt` file
Installation via Docker
Prerequisites:

Functional Docker installation
Docker image is not provided during beta period.

Enable Agent stdout feed
To retrieve the agents stdout feed directly in Manager, follow these steps
Make sure that the user you are using is either `root` or you have the appropriate permissions `agent.enable_stdout`, otherwise the stdout feed will remain blank.
Navigate to Home
Open the application settings


3. Enable "Agent Console Output" 



Your page will reload and upon connecting to any agent, you will now see a new icon in the lower right corner of the Manager.



Clicking this icon, opens the agent stdout console.


System status display
System status display
System status display is dependent on each agent individually. Depending on your region, specific entries might differ from agent to agent, particularly the status of CDN systems.
The manager contains an active indicator that displays the current system status of the Architect system, as well as attachment systems like Steam.



The small icon will be either green or yellow depending on the general status.

Clicking the indicator allows you to view the detailed system status.

Download Progress
Download progress state
The Manager is able to display the current status of all active downloads.

Once a download is currently active, you will see a download progressing badge in the header.



Clicking the indicator will open the download progress pop up, showing the details of the current download.



Limitations
Should the manager be connected to an agent that already has a download active, the download progress will start relative to the next progress event send by the agent. In this case the download duration might not be accurate. 

Game Server Crashing
Your game server is crashing. Unfortunate, but it can be fixed.
Isolate the source of the problem
Deploy a second game server of the same title. Make only minimal changes to the configuration to ensure it can start, but do not configure it further or install any mods.

Does the new game server run?
If it does, the issue is game server related.
If it does not run, the issue is hosting related.

Hosting related issues
If the problem appears to be hosting related, check the following points carefully:

Resources
Make sure the host system has enough memory, CPU, and storage available. Running out of any of these can cause the server to crash or fail to start.

Permissions
The Architect Agent must be allowed to read, write, and execute files in the game server directory. Incorrect permissions can prevent the server from working properly.

Ports and firewall
Ensure the required network ports are open and not blocked by a firewall. Also verify that no other process is already using the same ports.

File integrity
If files are missing or corrupted, the server will fail. Redeploy or verify the installation through Architect to restore clean files.

Operating system environment
Check that the operating system and all required dependencies are installed and up to date. Missing runtime libraries or outdated packages can cause startup issues.

Game server related issues
If a fresh deployment works but your configured one does not, the cause is in your own setup. In that case, review the following:

Configuration files
Return to default configuration and apply changes one at a time. Invalid syntax or unsupported settings often prevent servers from launching.

Mods and plug-ins
Disable all mods and test again. Re-enable them one at a time until the issue appears. A single broken or outdated mod can stop the server.

File paths
Verify that all mods, keys, and configuration files are in the correct directories.

Startup parameters
Remove any custom command-line arguments and test again. Incorrect or conflicting parameters can cause immediate startup failure.

Windows specifics
Windows specifics regarding the operation of game servers and Architect
This page only relates to Windows operating systems
Power Mode
The power mode setting dictates how your operating system handles your CPU. By default, Windows will use the "Balanced" power setting. This results in your CPU not clocking to its full potential in order to preserve power, which is not efficient for game servers.

Architect Manager will display a warning if you have either enabled "Balanced" or "Eco" power mode, as those will result in your game servers not operating to their maximum capacity.

Audit Logs
Tracking and tracing of all user actions
The agent archives all actions performed by every user in an audit log. By default, all actions of 30 days are recorded (configurable in config.toml).

You can access the audit log within the manager under Users, Audit Log.



The audit log allows you to filter by user and date (user filter requires `user.list` permission).

 

In addition to the general action, you are able to check the exact session id of any connection for the user, as well as the authoring IP address and exact payload sent by the user. To view these, click on the chevron.



Server process configuration
How the server process is managed and started
All server process settings can be managed through Settings.



Launch parameters
Launch parameters are a series of string values that are added to the individual launch command for each game server process. These usually regulate specific behavior for the game server and can be freely adjusted.

Depending on the title, some settings (eg. network interface for DayZ) will be handled through a launch parameter, instead of a server setting. In this case, the launch parameter will be automatically managed by the agent and the manual input will be ignored.

For titles with mod support, the mod relevant launch parameters will be automatically managed, and can not be overriden.
Port configuration
You can change the game server ports only through Settings. Manually editing specific configuration files (if managed by Architect) will be reverted to the  Agent configuration.

CPU affinity mask
This setting allows you to bind the game server process to specific CPU cores on your device. This setting is compatible with Linux and Windows.

Consult the game developer/publisher regarding the effectiveness of using affinity masks.
Priority level
The priority level is a OS level setting telling the operating system to prioritize execution of individual processes. This allows your process to receive more CPU time depending on your OS. This setting is compatible with Linux and Windows. Linux utilizes nice values instead of static priority labels.

Consult the game developer/publisher regarding the effectiveness of using process priority.
Network interface
Some games allow you to bind the game server to a specific network interface eg. ip address. If that is the case, you are able to configure this directly through Architect.

Architect will NOT manage the network routing/forwarding within your network equipment.

To bind a game server to a specific network interface, the ip address must be registered by the operating system. You are not able to put in any arbitrary ip address.

In order to revert the specific settings or let the game server listen on all available network interfaces, use `0.0.0.0`.

Agent Shell
Architect Agent Shell via Manager
Advanced topic
The Architect Agent operates as service, which does not offer a traditional console window with life output or logs. Within Manager you can access the direct Agent Shell by clicking the shell icon



This will toggle the raw Agent Shell, providing you with the raw logs and an option to manually issue commands directly against the Agent API.



All shell inputs are raw JSON payloads as they would be sent over the WebSocket API.

Backup Management
Architect offers automated backup management with integrated options to create, manage and restore backups. Backups work on a static configuration for each individual game server instance and must be explicitly set up.

Backups can be configured under Configuration, Server Operations.

All backups are automatically compressed to save disk space.



Backup at Startup
Controls if a backup should be created, just before the server process is initiated.

Backup Interval
An interval in which the backup should be created while the game server is running.

Can be disabled by setting value to `0`
Maximum Keep Time
To automatically clean up older backups, you are able to configure individual clean up times in days. 

Can be disabled by setting value to `0`
Backup Paths
Only the relative path to the file/folder needs to be configured.
Backup paths are fully dynamic, meaning you can backup primary folders, individual files or files using a dynamic pattern.

An example configuration for the folder `logs` would prompt all files contained in the `logs` older, including all sub directories to be backed up.

Wildcards are available by using `*` within the path.

Management of created Backups


Backup management is available through the Backups tab for each server.

You are able to create a manual backup, or delete and restore backups. As well as getting details about the created backups currently locally present.

Restoring backups will fully overwrite the files or re-create them.

File manager
Architect File Manager
Using Architect, you can remotely manage server files. You can upload, delete, rename, view, download and edit files.

The file manager is available for all titles that allow you to have access to server files.



You are able to view and edit files that contain text. Binary files can not be displayed or changed.

You can search for files using the Search files input field. The refresh icon allows you to ad-hoc refresh the file tree.

File editing


To edit a file, simply click on it. From there on you can make your customizations and click on save to apply your changes.

Important notes:
- Some files can not be edited when the server is running
- Architect does not validate your input
- Files larger than your configured file size limit can not be viewed (32 MiB by default)
By clicking the refresh icon next to the file name, you are able to refresh file contents. Any unsaved changes will be overwritten.

Rename and delete
You can rename or delete files and folders by right clicking them.



Move folders and files
When moving a file that has the same name as an existing file in the target directory, that file will be overwritten.
You can move folders or files by drag-and-dropping them. When dragging a file or folder, the target will be highlighted in blue.

Uploading files
When uploading a file that has the same name as an existing file in the root directory, that file will be overwritten.
You can upload files or entire folders. To do that you simply drag any file or folder from your device into the Manager window until the drop zone appears.



Uploaded files will always be written to the server root directory. Should you upload a folder, the folder will be written to the root directory with its contents in place.

Important notes:
- Files larger than your configured file size limit can not be written (32 MiB by default)
- Uploading a lot of files or large files may prompt the Agent to respond slower for other users
All files that can be uploaded will be shown in the update progress screen.

WebHooks
Architect WebHooks
Architect supports WebHooks for different events. You are able to send fully customizable payload structures to any specified URL.

Once a WebHook has been created, the specified URL will be contacted once such an event occurs.



WebHook deliveries
All WebHook events are sent from the Agent directly. You are able to customize the amount of retries, the HTTP timeout and supply custom headers for all deliveries of any WebHook.

Deliveries are individually tracked and contain a unique delivery id. A record about all deliveries is kept for 7 days.

In case any specific delivery fails, it will be retried based on your configured retry counter.

All delivers carry certain technical headers that allow you to identify an Architect WebHook event:

Key	Description
X-WebHook	Static string: "Architect Agent"
X-WebHook-Id	Unique id of the WebHook registration
X-WebHook-Event	Event type of the delivery
X-Event-Idempotence	Idempotence token that is static for each delivery to catch double deliveries in case of retries
You are able to access the WebHooks your agent has executed from WebHooks, Deliveries:



Templating
WebHook payloads can be templated. Different events have different templating values available that carry information about that specific event.

Parameters can be embedded in the format `{{parameter}}` where parameter represents the individual values name.

Events
agent.ready
General event, not specific to any reference entity
Sent when an Agent has started.

Value	Description
date	 UTC Unix timestamp of event occurrence
session.begin
General event, not specific to any reference entity
Sent when a user connects to an Agent.

Value	Description
date	 UTC Unix timestamp of event occurrence
user	 Username
ip_address	 IP address used to connect
session	 Unique session id
session.ended
General event, not specific to any reference entity
Sent when a user disconnects from an Agent.

Value	Description
date	 UTC Unix timestamp of event occurrence
user	 Username
ip_address	 IP address used to connect
session	 Unique session id
server.started
Filtered event, only applies to specific entities or all
Sent when a server starts.

Value	Description
date	 UTC Unix timestamp of event occurrence
server	 Server identifier
server.stopped
Filtered event, only applies to specific entities or all
Sent when a server stops.

Value	Description
date	 UTC Unix timestamp of event occurrence
server	 Server identifier
reason	 Reason code for server stop:
 - requested
 - killed
server.updated_title
Filtered event, only applies to specific entities or all
Sent when a server is updated (after update completes).

Value	Description
date	 UTC Unix timestamp of event occurrence
server	 Server identifier
title	 Title id
server.updated_mod
Filtered event, only applies to specific entities or all
Sent when a mod update is applied to the server (after update completes).

Value	Description
date	 UTC Unix timestamp of event occurrence
server	 Server identifier
mod	
 Mod name (depending on modding ecosystem)

mod_id	
 Mod id (depending on modding ecosystem)

title.updated
General event, not specific to any reference entity
Sent when a title update has been discovered.

Value	Description
date	UTC Unix timestamp of event occurrence
title	Title id
mod.updated
General event, not specific to any reference entity
Sent when a mod update has been discovered.

Value	Description
date	UTC Unix timestamp of event occurrence
mod	Mod name (depending on modding ecosystem)
mod_id	Mod id (depending on modding ecosystem)

Multi-User and RBAC
Architect agent multi user support
Architect supports multiple users in parallel combined with role base access control.

All users and roles are exclusive to each agent and can be configured separately. 



Users
Users are standalone users each Architect Agent has. This means they have a unique username and their own password for access.

This gives you control about who accesses your agent, and allows you to grant access to your team without them having control over everything.

Root user

Each agent generates an automatic `root` user that has all permissions and is able to manage everything. The default password will be written to a `.txt` file within the agents installation directory.

It is not possible to delete or alter the roles for the root user.

Additional users

You can create additional users by clicking the `Add new User` button and entering a unique username.



Once created, you will be prompted a pop up with the users initial password.



By clicking the three dots, next to a user entry, you are able to manage that users roles or delete the user.



Assigning and removing roles

Assigning and removing roles is available after you click on "Manager User".



You are able to assign new roles to the user or remove roles.

The default role can not be revoked.
Roles
Architect works with role based access controls (RBAC) that allows you to create roles, and assign them permissions. These roles can be allocated to users.



Two roles are created by default: root, default

These roles can not be deleted or altered. They contain import permission presets.

Creating new roles



You can create new roles by clicking "Create new Role". You are able to fine-tune your roles permissions.

Some permissions are marked as required, if they are required to utilize Architect Manager.

To create a fine-grained role that is intended for API users, utilize the API to create those.

Server scoping

By default roles are not bound to any specific server instances. Meaning users having a role are able to access all servers with their specified privileges. You are able to scope this more finely grained by using server scoping.

DayZ
Architect for DayZ
Universe
Steam

Supported Branches
DayZ is split into two Steam applications, separately tracked by Architect.

Branch	App Id	Status
public	223350	Supported
experimental	1042420	Supported
Server Maintenance
Windows
All requirements are installed automatically.
Linux
As of 1.28 DayZ for Linux remains unstable and error prone. 
For Linux, additional packages must be installed. Architect will not handle this automatically.

Debian

apt-get install lib32gcc-s1
Modding
DayZ mods are automatically tracked by Architect and available for install. public and experimental branch servers both utilize the default DayZ Workshop (App Id 221100)

Health Check HTTP
Architect Agents HTTP endpoint for external health checks
Advanced topic
Similar to the WebSocket API, the Agent exposes a plain HTTP interface on its listening port. You can contact it through either HTTP or HTTPS depending on your Agents SSL configuration.

When running a default Agent configuration, you can locally test the Health Checking endpoint by accessing `https://127.0.0.1:8090` in your browser or requesting it through your command line.

When trying to reach it externally, you need to exchange `127.0.0.1` with your devices external ip.
The health check will respond with a JSON formatted response of the following format

{
  agent: {
    version: <str>
    ssl: <bool>
  }
  system: {
    hostname: <str>
  }
  status: <str> (always "running")
}

Basics
Agent API basics
Advanced topic
The Architect Agent comes with an integrated WebSocket API. The API is used by Architect Manager internally and may be accessed by you through custom scripts.

To access the API, you need to create a WebSocket connection to your Agent by connecting through `ws` or `wss` to your Agents public ip, on the configured listening port.

Whether you need to connect to `ws` or `wss` (SSL) depends on your Agents SSL setting. By default, SSL is turned on with self signed certificates.

Connections through common WS libraries require you to explicitly accept self signed certificates
To programmatically authenticate against an Agent, you need to initiate the connection with a header

Sec-Websocket-Protocol: SMP1.0, {username}, {password}
Any connection, without providing the authentication header will be blocked.

Once connected, commands can be sent as JSON formatted payload. It is following this struct pattern:

{
   action: <str>
   parameters: <map>
}
You are able to retrieve all commands supported by your Agent version by sending the following

{
   action: "list_actions",
   parameters: {}
}
You will receive a list of supported actions, their required parameters and data types.

Examples
Python 3
#!/usr/bin/env python3
"""
This is a minimal class to interface with the Architect Agent programmatically.
"""
from __future__ import annotations

import re
import ssl
import json
import uuid
import types
import asyncio
from typing import Callable, Awaitable, Any, Dict, Optional

import websockets
from websockets import WebSocketClientProtocol


class CFToolsArchitectAgentClient:
	def __init__(
		self,
		host: str,
		port: int,
		*,
		use_tls: bool,
		username: str,
		password: str,
		on_event: Optional[Callable[[dict], Awaitable[None]]] = None,
		on_connected: Optional[Callable[[dict], Awaitable[None]]] = None,
	) -> None:
		self._host = host
		self._port = port
		self._use_tls = use_tls
		self._username = username
		self._password = password
		self._on_event = on_event or (lambda _: asyncio.create_task(asyncio.sleep(0)))
		self._on_connected = on_connected

		proto = "wss" if self._use_tls else "ws"
		self._uri = f"{proto}://{self._host}:{self._port}/ws"
		self._subprotocols = ["SMP1.0", self._username, self._password]

		self._ws: WebSocketClientProtocol | None = None
		self._receiver_task: asyncio.Task[None] | None = None
		self._pending: Dict[str, asyncio.Future[dict]] = dict()

		self._actions: list = list()
		self._populated_actions: bool = False

	async def connect(self) -> None:
		"""Establish the WebSocket and launch the passive receiver."""
		ssl_ctx = ssl.create_default_context()
		ssl_ctx.check_hostname = False
		ssl_ctx.verify_mode = ssl.CERT_NONE

		self._ws = await websockets.connect(
			self._uri,
			ssl=ssl_ctx,
			subprotocols=self._subprotocols,
		)
		print(f"Connected to {self._uri} (sub-protocol: {self._ws.subprotocol!r})")

		# Start the background listener
		self._receiver_task = asyncio.create_task(self._receiver())

	async def close(self) -> None:
		if self._receiver_task:
			self._receiver_task.cancel()
			with contextlib.suppress(asyncio.CancelledError):
				await self._receiver_task
		if self._ws:
			await self._ws.close()

		print("Connection closed")

	async def send_request(
		self, payload: dict, *, timeout: float | None = 10.0
	) -> dict:
		"""
		Fire-and-await request/response conversation.

		- Adds an `idempotence` token.
		- Returns the first message that echoes that token.
		"""

		if not self._ws:
			raise RuntimeError("Not connected")

		token = str(uuid.uuid4()).replace('-', '')
		outgoing = dict(payload, idempotence=token)

		fut: asyncio.Future[dict] = asyncio.get_running_loop().create_future()
		self._pending[token] = fut

		await self._ws.send(json.dumps(outgoing))
		try:
			return await asyncio.wait_for(fut, timeout=timeout)

		finally:
			# Clean up even on timeout/cancel
			self._pending.pop(token, None)

	async def _receiver(self) -> None:
		"""Runs forever, routing every incoming frame."""
		assert self._ws  # no-connect guard
		asyncio.create_task(self._populate_actions())
		
		try:
			async for raw in self._ws:
				try:
					msg = json.loads(raw)
				except json.JSONDecodeError:
					continue  # ignore non-JSON frames

				token = msg.get("idempotence")
				if token and token in self._pending:
					# Wake the awaiting send_request()
					self._pending[token].set_result(msg)

				else:
					# Unsolicited event → callback
					asyncio.create_task(self._on_event(msg))

		except websockets.ConnectionClosedOK:
			pass

		except Exception as exc:
			# Cancel all waiters on fatal connection error
			for fut in self._pending.values():
				if not fut.done():
					fut.set_exception(exc)
			raise

	async def _populate_actions(self) -> dict:
		await asyncio.sleep(1)
		catalogue: dict = await self.list_actions()

		def _make_stub(action: str, meta: dict, py_name: str):
			"""Factory: returns a bound coroutine for an action."""
			async def _stub(self, **params):
				required = meta.get("required_parameters", [])
				if required is None:
					required = []

				missing = [p for p in required if p not in params]
				if missing:
					raise TypeError(
						f"Missing {missing} for action '{action}'"
					)

				payload = {"action": action, "parameters": params}
				return await self.send_request(payload)

			_stub.__name__ = py_name
			_stub.__doc__ = (
				f"Dynamically generated wrapper for remote action '{action}'.\n"
				f"Remote description: {meta.get('description', 'n/a')}"
			)
			return _stub

		for action_name, meta in catalogue.items():
			if meta.get("cloud_controller_only"):
				continue

			py_name = action_name

			stub = _make_stub(action_name, meta, py_name)
			setattr(self, py_name, types.MethodType(stub, self))
			self._actions.append(action_name)

		self._populated_actions = True
		if self._on_connected:
			asyncio.create_task(self._on_connected())

	async def list_actions(self) -> dict:
		"""Utility wrapper around the `list_actions` request."""
		reply = await self.send_request({"action": "list_actions", "parameters": {}})
		return reply["parameters"]["actions"]


async def main() -> None:
	client: CFToolsArchitectAgentClient = None

	async def handle_event(event: dict) -> None:
		print("event:", event)

	async def handle_connected() -> None:
		print('Connected.')
		print(await client.servers())

	HOST = "your ip / hostname"
	PORT = 8090
	USE_TLS = True
	USERNAME = "username"
	PASSWORD = "password"

	client = CFToolsArchitectAgentClient(
		host = HOST,
		port = PORT,
		use_tls = USE_TLS,
		username = USERNAME,
		password = PASSWORD,
		on_event=handle_event,
		on_connected=handle_connected
	)
	await client.connect()

	# Keep running; Ctrl-C to exit
	try:
		while True:
			await asyncio.sleep(3600)
	finally:
		await client.close()


if __name__ == "__main__":
	import contextlib
	try:
		asyncio.run(main())

	except KeyboardInterrupt:
		pass
```

## Architect Foundation Platform

### Enterprise level game server management at scale

CFTools Architect Foundation is a platform solution for large-scale, professional game server management environments.

It is designed to bring structure, consistency, and automation to every stage of a game server's lifecycle - from its initial deployment, through its continuous operation and orchestration, all the way to its eventual decommissioning and removal. 

Foundation serves as a layer atop of the CFTools Architect ecosystem, providing the high level framework that enables reliable, scalable, and secure management of complex game server infrastructures.

At its core, Foundation bridges the gap between individual game server instances and the broader infrastructure that supports them. It coordinates how servers are deployed, how resources are allocated, and how user environments are isolated. This ensures that every server operates within a controlled and predictable environment, significantly reducing the risk of conflicts, misconfigurations, and downtime. By standardizing the deployment and management process, Foundation allows operators to focus on optimizing their player's experiences rather than troubleshooting infrastructure issues.

Foundation-enabled agents extend the functionality of the Architect Agent by introducing deeper integration with the host system. This includes hardware management capabilities such as performance monitoring, load balancing, and intelligent resource allocation, ensuring that physical and virtual resources are used efficiently.

For larger operators or hosting providers, Foundation offers a unified orchestration layer that can manage hundreds or thousands of game servers simultaneously. It enables consistent configuration across multiple machines, automatic synchronization of updates, and streamlined lifecycle management through standardized workflows. The Architect Foundation platform delivers a complete, enterprise-grade management experience suitable for both private and commercial environments.

**You are a game server provider or game studio wanting to integrate Architect Foundation?**

Contact us by e-mail at sales@cftools.software