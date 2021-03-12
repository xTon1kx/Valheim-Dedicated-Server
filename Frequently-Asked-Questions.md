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

You can - sort of! Simply open multiple ValheimServerGUI windows and input the information for each server that you want to run, then start them up. The info for the most-recently-started server will be saved to your user preferences. Make sure you run the servers on different ports!

At time of writing, ValheimServerGUI is being developed with non-technical users in mind, and may not ever have true multi-server support. If you need more powerful tools for hosting multiple servers on one machine, check out [Valheim Server Warden](https://github.com/Razzmatazzz/ValheimServerWarden), which is being developed by another team.