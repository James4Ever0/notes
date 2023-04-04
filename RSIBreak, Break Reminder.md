---
title: 'RSIBreak, Break Reminder'
created: '2023-04-04T01:23:42.270Z'
modified: '2023-04-04T02:36:18.382Z'
---

# RSIBreak, Break Reminder

if you want to do it on your own, you have to know how to send notifications on different operating systems.

on macOS:

```bash
osascript -e 'display notification "This message should be showing on the notification" with title "Coding Tips"'
```

on linux:

```bash
notify-send
```

on windows:

```cmd
msg /SERVER:DestinationPC * /TIME:60 “This is the message to be sent to a PC named DestinationPC and closes in 60 seconds."
```

[notify-send-for-Windows](https://github.com/Fonata/notify-send-for-Windows (needs AHK)
----

[RSIBreak](https://userbase.kde.org/RSIBreak) is for linux, and it does not work well.

[stretchly](https://github.com/hovancik/stretchly) has [an online version](https://web.stretchly.net). on macOS make sure your browser is allowed to post notifications.

"Drink." on mac app store is a water drinking reminder for macOS.

[BreakTimer](https://breaktimer.app/) has windows, macOS and linux version. on linux you better use snap or appimage version.
