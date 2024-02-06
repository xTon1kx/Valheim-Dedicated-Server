## I'm getting an error that Valheim Dedicated Server is not installed when I start the app

In order to use this application, you must have Valheim Dedicated Server (VDS) installed on your machine. VDS is included for free with your purchase of Valheim. If you have not installed VDS, see the installation guide [here](../Installing-Valheim-Dedicated-Server).

You may also get this warning if you have installed VDS somewhere other than the default Steam directory. If you have installed VDS somewhere else, you can change the path by going to **File > Set Directories** and changing the path for **Valheim Server .EXE**.

## It keeps saying my server name/password is not allowed

Valheim enforces some rules about your server information. It must meet the following requirements:

* Your server name cannot be the same as the name of the world you're hosting
* Your password must be at least 5 characters long
* Your password must not contain either the name of the server or the name of the world you're hosting

If you're running a mod that can bypass server password requirements (such as Valheim Plus), you can disable these password requirements in VSG by going to File > Preferences, and unchecking the option "Validate password when starting server".

## I think something is messed up with my saved settings

You can delete or modify your user preferences for ValheimServerGUI by going to the following path in Windows File Explorer:

```%USERPROFILE%\AppData\LocalLow\Runeberry\ValheimServerGUI```

Your preferences are stored in `userprefs.json`.

## ValheimServerGUI matched a character name with the wrong player

There are some cases where ValheimServerGUI cannot accurately match up a player's name with their Steam/Xbox ID based on the server's logs. Particularly, this can happen when multiple players join the server at the same time. In these cases, the app will take its "best guess" as to what the correct name pairing should be.

To fix a mismatched name, click "View Player Details..." for the affects players, and add/remove character names as needed. The next time the players join the server, the app will prefer to match them up to a name that's already in that player's list.

To avoid this entirely, have each player join your server one at a time - specifically, make sure there are no two players in the "Joining" status at the same time. Once ValheimServerGUI is able to match up a Character Name / Steam ID confidently, it will remember this for future sessions so that it's less likely to happen again.

## I created a world, but it's not showing up in the Existing Worlds dropdown

Worlds that are created within the Valheim game itself are now stored in the Steam Cloud by default. ValheimServerGUI will not recognize this folder for world saves by default. You can fix this by doing one of the following:

* If you **DO NOT** want your world file synced to the Steam Cloud:
  * From the Valheim main menu, go to Start > Manage Saves > Worlds tab > select your world and click "Move to Local".
* If you **DO** want your world file synced to the Steam Cloud:
  * Locate your local copy of the world save files on your computer. Open `C:\Program Files (x86)\Steam\userdata`, click your steam ID, then go to `892970\remote\worlds`. You should see your world save in there.
  * Copy the path to the `remote` folder. It should look like: `C:\Program Files (x86)\Steam\userdata\{your-steam-id}\892970\remote`
  * In ValheimServerGUI, go to File > Set Directories, and paste the path to the `remote` folder in the Valheim Save Data Folder field, and click save.