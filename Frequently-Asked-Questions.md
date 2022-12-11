## What is a dedicated server?

A dedicated server allows you to run the multiplayer component of Valheim in the background without having the whole game running. This lets other players hop in and out of your multiplayer game event while you (the host) are not actively playing.

## Why would I want to run a dedicated server?

Running a dedicated server from your own PC has a few benefits:

* As host, you can run a game for your friends without needing to actively play the game at the same time.
* This means if you leave your PC on with the dedicated server running, you can have your friends play while you're away, at work, or asleep, without having to worry about your own character getting mauled by a wandering Greyling.
* You can hop to your own single-player world while still hosting a multiplayer game - so you can access that personal stash of iron we all know you're pulling from.
* You could get all these benefits from a paid server provider as well, but this is 100% free - as long as you're willing to leave your PC on!

## Why should I use ValheimServerGUI?

Currently, running a dedicated server is a little hacky and involves editing a batch file that may get overwritten by Steam. This may improve over time (the game is in Early Access, after all), but for now I've written this application that will do the same thing just by editing a few form fields. Plus, you get all the nice features listed in the [README](https://github.com/runeberry/ValheimServerGUI/blob/main/README.md) for free!

## Can you host multiple Valheim servers with ValheimServerGUI?

Yes! As of v2.0.0, ValheimServerGUI supports running multiple servers at once. Here's how you do it:

1. Go to File > New Window. Each server will run in a separate window.
2. In the new window, to go File > New Profile, and enter a name for this server configuration. You can now modify the server details in this window independently from the Default profile.
3. You can save your server details at any time with File > Save Profile. Your profile is also saved each time you start the server, unless you have disabled this setting under File > Preferences.
4. To switch between profiles in any window, go to File > Load Profile.

## Does ValheimServerGUI work with server side mods?

Yes! As long as you are still ultimately running your server through `valheim_server.exe`, you can use your mods in conjunction with ValheimServerGUI. For example, it's been tested and working with a Valheim Plus server configuration.

_If you have a server-side mod that you're unable to use with ValheimServerGUI, please [open an issue](https://github.com/runeberry/ValheimServerGUI/issues) and let me know. I'll see if it's something I can support._

## Why is there a warning icon ⚠ next to a player's Character Name?

There are some cases where ValheimServerGUI cannot accurately match up a player's name with their Steam ID based on the server's logs. Particularly, this can happen when multiple players join the server at the same time. This is a limitation of Valheim Dedicated Server and may be fixed in a future release. In these cases, the app will take its "best guess" as to what the correct Name/Steam ID pairing should be, and show this warning when it's not 100% sure that it's been matched up right.

To avoid this entirely, have each player join your server one at a time - specifically, make sure there are no two players in the "Joining" status at the same time. Once ValheimServerGUI is able to match up a Character Name / Steam ID confidently, it will remember this for future sessions so that it's less likely to happen again.