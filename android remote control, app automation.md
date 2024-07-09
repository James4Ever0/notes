---
title: android remote control, app automation
created: 2022-10-15T13:21:37+00:00
modified: 2024-07-09T17:34:46+08:00
---

# android remote control, app automation

to change the resolution of android device run this command:

```bash
# <width>x<height>
adb shell wm size 3000x2000

# reset window size
adb shell wm size reset
```
---

launch scrcpy with HID simulation and screen off:

```bash
scrcpy -SK
```

---

run android in docker, run adb in docker

device discovery, termux daemon, remote unlock

unlock requires screenshot and input events.

https://technastic.com/unlock-android-phone-pin-pattern-adb/

click ok after input password:

https://stackoverflow.com/questions/29072501/how-to-unlock-android-phone-through-adb

scrcpy client

https://github.com/leng-yue/py-scrcpy-client
https://leng-yue.github.io/py-scrcpy-client/guide.html#bind-events

you want to use android emulator on macos m1?

https://github.com/google/android-emulator-m1-preview/releases/tag/0.3

check android screen lock/unlock state

https://android.stackexchange.com/questions/191086/adb-commands-to-get-screen-state-and-locked-state

Bonjour/Avahi/Zeroconf

logic: if the kill switch is off, when no physical input events happens, or not focused on scrcpy window with keyboard/mouse input events on pc for some time, allow to interact with the phone.

get physical events:

warning: this command could be offline for a short period of time after using the scrcpy. must automatically reconnect if the device is not offline.

```bash
adb -s 192.168.10.3:5555 shell getevent
```

to get focused window title:
hint: for headless ssh sessions, must set apropriate xorg environment variables, eg: `env XAUTHORITY="/run/user/0/gdm/Xauthority" DISPLAY=:1 python3`

general method:
```python
import pywinctl
pywinctl.getActiveWindowTitle()
```

for linux:
```bash
watch -n 2 xdotool getactivewindow getwindowname
```

for macos: (allow permission first, deprecated since it will not get the window title instead of the program name)
https://alvinalexander.com/mac-os-x/applescript-unix-mac-osx-foreground-application-result/
(where is the window name?)
```bash
sleep 3 && osascript -e 'tell application "System Events"' -e 'set frontApp to name of first application process whose frontmost is true' -e 'end tell'
```


to get input events on macos:
download keylogger here:
https://hackernoon.com/writing-an-keylogger-for-macos-in-python-24adfa22722
https://github.com/beatsbears/pkl?ref=hackernoon.com
```bash
python pkl_nowriting.py
```

input events on linux:

```bash
xinput test-xi2 --root
```
