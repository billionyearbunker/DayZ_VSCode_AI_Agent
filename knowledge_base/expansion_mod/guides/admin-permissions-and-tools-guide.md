# Admin Permissions and Tools

## Contents

- [Granting someone admin](#granting-someone-admin)
- [Setting up permissions](#setting-up-permissions)
- [Setting up roles](#setting-up-roles)
- [Troubleshooting](#troubleshooting)

---

## Granting Someone Admin

### 1. Getting the Player ID

Firstly, make sure your admin logs are enabled! How so? By adding `-adminlog` in your server launch options.

**P.S.** You can also find this ID from the `dayzserver_timedate_timedate.rpt` logs but will be a lot more messy.

**Server Launch Options**

Now your server should generate new log files in **ADM format** in your server profile (or config) folder.

**ADM file in server profile**

You will be able to get Player IDs from this file. However to see the player ID of someone, this player must have joined the server while this launch option was active!

Here is an example of what you should find:

**Inside the ADM file**

### 2. Granting the Player Admin Role

Now that you have found where to find the player ID, go to:

```
YourDayZServer\Profile(or config)\PermissionFramework\Players\
```

You should see one or multiple files with player IDs. Open the file with the player ID you saw in the ADM logs and you should have something similar:

**Player roles**

Change `everyone` to `admin` and save. Now this player has the admin role ingame!

**Inside the player roles**

---

## Setting up Permissions

**Disclaimer:** This part is more advanced and does not require you to do the following steps to have a functional server and/or admin tool.

### 1. How do permissions work?

- **`0` (INHERIT)** - It will gain the permission value of the next parent permission which is not inherit. So if you have `Admin.Player.Set` set to `INHERIT` and `Admin` set to `ALLOW` then `Admin.Player.Set` will be `ALLOW` but if you had `Admin.Player` set to `DISALLOW` as well then `Admin.Player.Set` is now `DISALLOW`.
- **`1` (DISALLOW)** - No access
- **`2` (ALLOW)** - Full access

### 2. How to add specific permissions to a user?

In `ServerProfile\PermissionsFramework\Permissions` open the file with the GUID of the user you want to edit his permissions.

---

## Setting up Roles

**Disclaimer:** This part is more advanced and does not require you to do the following steps to have a functional server and/or admin tool.

In `ServerProfile\PermissionsFramework\Roles` create a txt file with the name of your role. In this example we will create a `moderator.txt` file.

Open the `everyone.txt` file, copy all its content and paste it inside your new file (`moderator.txt`).

Now change the permissions to your liking!

If you want to assign someone with this role, simply add the file name in his Roles like you did with admin previously!

---

## Troubleshooting

### I only see vanilla vehicles in my spawnlist!

**vehicle spawner only vanilla**

Go inside your server config at `YourDayZServer\Profile(or config)\` and delete the `CommunityOnlineTool` folder. It will force the admin tool to regenerate the list!

### I can't open some menus in my admin tool!

Go inside your server config at `YourDayZServer\Profile(or config)\PermissionFramework\Roles\` and delete (or rename) the `everyone.txt` and `admin.txt` files. It will force the admin tool to regenerate the files and up to date!
