In certain circumstances, you may want to automatically reboot your Valheim server on a daily schedule. ValheimServerGUI does not natively support this (yet), but you can achieve this using a simple script and Windows Task Scheduler. Follow the instructions below.

1. Create a new file called `vsg-restart.bat`, and paste the following contents into the file. Swap out the file path on the last line to the path to `ValheimServerGUI.exe` on your computer.

```batch
rem Kill any running instances of VSG and all child processes (the Valheim server itself)
rem This is a forceful stop, so you will lose any data that has not been saved since the last autosave.
taskkill /f /t /im ValheimServerGUI.exe

rem Wait 5 seconds
timeout 5 > NUL

rem Start VSG - enter your own path to the .exe here
start "" "%USERPROFILE%\Downloads\ValheimServerGUI.exe"
```

2. In ValheimServerGUI, make sure to check: Advanced Controls > "Start this server when ValheimServerGUI starts". Make sure this setting is saved to your server profile with File > Save Profile.
3. In Windows, search for "Task Scheduler", then:
    * On the right, click "Create Basic Task..."
    * Give the task a name, like "ValheimServerRestart"
    * Select a schedule, such as Daily at 06:00:00. Make sure to pick a time when nobody will be playing on the server.
    * For Action, select "Start a Program", then choose this batch file you created earlier.

That's it! This will forcefully restart ValheimServerGUI each day at the specified time. Since this is a forceful restart, your server **will not perform an autosave** before restarting.

