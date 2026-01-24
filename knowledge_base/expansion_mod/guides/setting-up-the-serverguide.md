# Setting up the server

---

## Table of Contents

- What mods do you need?
- Mission Files (types)
- Server Config
- I have an error!
- Downloading the mods you need/want

---

## Required Mods

### The Essentials

- **Community Framework (CF)**
- **Dabs Framework (DF)**
- **Community-Online-Tools (COT - Optional)**

### "All in One"

- **DayZ-Expansion-Bundle**
- **DayZ-Expansion-Licensed** (Not Included in Bundle)
- **DayZ-Expansion-Animations** (Not Included in Bundle - Optional)

### Individual Mods

- DayZ-Expansion-Core
- DayZ-Expansion
- DayZ-Expansion-Animations
- DayZ-Expansion-BaseBuilding
- DayZ-Expansion-Chat
- DayZ-Expansion-Groups
- DayZ-Expansion-MapAssets
- DayZ-Expansion-Missions
- DayZ-Expansion-Navigation
- DayZ-Expansion-Weapons
- DayZ-Expansion-Vehicles
- DayZ-Expansion-Market
- DayZ-Expansion-Name-Tags
- DayZ-Expansion-Spawn-Selection
- DayZ-Expansion-Book
- DayZ-Expansion-Hardline
- DayZ-Expansion-Quests
- DayZ-Expansion-Personal-Storage
- DayZ-Expansion-Licensed
- DayZ-Expansion-AI

---

## Installing Mods

Install the mods where your server is installed (as shown in the first picture).

Inside each mod you should find a "key" folder with a bikey for each mod (if the key already exists this is fine). Copy all these keys and paste them inside your keys folder (Also in your root directory of your server).

**Finding Mods**: If you do not know where to get the mods, open your DayZ launcher, right click on the desired mod, and choose "Open folder". A pop up will ask you if you know what you are doing, say yes and now Windows Explorer should open. You should see all the downloaded mods you have on your computer. All you have to do is to copy paste the mods you want in your server root directory.

---

## Adding Mods to Server

Now you need to add the mods to your mod list. You may have a panel to load a mod in your server. But if this is not the case, you will probably need to edit a command line. Something similar to this:

```
"-mod=@CF;@Dabs Framework;@DayZ-Expansion-Bundle;@DayZ-Expansion-Licensed"
```

Make sure they all have the same name in this command line as in your server directory root. If a mod folder is named `Community-Online-Tools`, the command line will need to have the same name.

If a mod has spaces in its name (for example `@Dabs Framework`), you can remove the space in the mod name (folder name and in the command line) if your server provider doesn't support mods with spaces.

---

## start.bat

If you are creating a local server (on your computer or on a local machine without omega manager for example) and don't know how or where to add these lines, do the following:

Create a txt file and paste inside the file this config:

```bat
@echo off
start DayZServer_x64.exe -config=serverDZ.cfg -port=2302 "-mod=@CF;@Dabs Framework;@DayZ-Expansion-Bundle;@DayZ-Expansion-Licensed" -profiles=ServerProfile -netlog
```

And save as `MyName.bat`!

Now all you have to do is to execute this bat file to launch your server 😃

Make sure your bat file is inside your server folder as shown with the picture above!

---

## Mission Files

Download the latest files at https://github.com/ExpansionModTeam/DayZ-Expansion-Missions

Follow the instructions in the `README_TUTORIAL.txt` to import the content you need into your mission.

This template includes:

- xml files for the items, vehicles, weapons and more (types.xml)
- mapping/traders for servers using the Expansion Market mod (optional)

---

## Server Config

After starting your server with the DayZ Expansion mod for the first time, the server will generate the ExpansionMod folder in your profile folder (sometimes also named "sc" or "config"). In this folder, all the DayZ Expansion related settings will be stored. If you want to toggle any part of DayZ Expansion go into the settings folder and open the file you want to modify. If you want to learn more about the server settings click here.

---

## How to find what is wrong?

In your server root directory you should have a folder with at least one of these names (sc, profile, server profile, instance_xxxx, profile, config). This folder should have some folders with the name of some of the mods you are using (trader, expansionmod, communityonlinetool, vpp, dayzeditor, permissionframework, and many other mods) but also many files with time and dates in their names.

First, look for a crash log. It should be a text file with the name `crash_timedate.log`. Open this file and try to see if this error is already documented below!

If you don't see any crash logs, look for `dayzserver_timedate_timedate.rpt` (not mdmp). Open it. If this file is really small (only a couple of lines), it might be an issue with your mod loading list. Probably a typo!

---

## Troubleshooting

### Bad type 'StringLocaliser'

Make sure you have the correct mods and up to date! (in this case, it can't find CF)

### Function 'Exec_CreateNotification' is marked as override

You are missing CF. The server is not detecting the mod, probably a typo somewhere!

### !!! String CORRUPTED - FIX OnStoreLoad() !!! (or) scripted variables corrupted

Your "storage_x" (x being a number) is using the vanilla storage format. Wipe this folder to use the CF storage format. This will wipe all player progression however.

### Infinite loading screen, server frozen

Check your logs and look for an error. If you can find an error talking about a json error with a setting file, it usually means this file is broken (missing line for example). Revert your changes or fix the mistake manually or with a json validator.

If you can't find any errors in the logs try the following :

Delete the folder "ExpansionMod" (in your "server profile" aka "config" aka "sc")
Make sure you are loading a Expansion mission
Please note: Some users thought their server was frozen while in fact it was the "!!! String CORRUPTED - FIX OnStoreLoad() !!!" issue.

Server not powerful enough
Some server providers are not powerful enough to run the expansion custom mapping and building interiors. You can disable this two features in your server profile (in your "server profile" aka "config" aka "sc") => expansionmod => settings => GeneralSettings.json and change this two settings from 1 to 0 if it's enabled.

ExpansionMod, Missions folder empty
If your server profile (aka "config" aka "sc") => expansionmod => missions is empty, delete the "MissionSettings.json" from the settings folder

The server can't find the mission (mpmission/dayzoffline.mapname)
In this case, make sure the server is trying to open a mission with the correct name. A missing letter can change everything !

BattlEye initialization failed
The battlEye dll is missing from the battlEye folder of your server profile (also known as "config" or "sc"). A copy paste of this missing dll should do the job in most cases.
