---
title: 'RSIBreak, Break Reminder'
created: '2023-04-04T01:23:42.270Z'
modified: '2023-04-04T03:14:52.425Z'
---

# RSIBreak, Break Reminder

## DIY

if you want to do it on your own, you have to know how to send notifications on different operating systems.

----

on macOS:

```bash
osascript -e 'display notification "This message should be showing on the notification" with title "Coding Tips"'
```

[terminal-notifier](https://github.com/julienXX/terminal-notifier) (brew installable)

[alerter](https://github.com/vjeantet/alerter)

----

on linux:

```bash
notify-send "Dinner ready!"
```

using `remind`:

```bash
remind "I'm still here" now
remind "Time to wake up!" in 5 minutes
remind "Dinner" in 1 hour
remind "Take a break" at noon
remind "It's Friday pints time!" at 17:00
```

----

on windows:

```cmd
msg /SERVER:DestinationPC * /TIME:60 “This is the message to be sent to a PC named DestinationPC and closes in 60 seconds."
```

[notify-send-for-Windows](https://github.com/Fonata/notify-send-for-Windows (needs AHK)

[tutorial](https://superuser.com/questions/1179758/how-can-i-send-a-notification-to-a-windows-10-computer-from-the-command-line)

## break reminder tools

[RSIBreak](https://userbase.kde.org/RSIBreak) is for linux, and it does not work well.

[stretchly](https://github.com/hovancik/stretchly) has [an online version](https://web.stretchly.net). on macOS make sure your browser is allowed to post notifications.

"Drink." on mac app store is a water drinking reminder for macOS.

[BreakTimer](https://breaktimer.app/) has windows, macOS and linux version. on linux you better use snap or appimage version.
