---
title: Linux restore window sessions
created: '2022-07-27T00:06:40.000Z'
modified: '2022-08-04T06:04:01.384Z'
---

# Linux restore window sessions

to relaunch app in given workspace

tools:
wmctrl
[devilspie](https://help.ubuntu.com/community/Devilspie)
[launch_on_workspace](https://github.com/xblahoud/launch_on_workspace)

npm install -g linux-window-session-manager
restore session manually

dconf-editor
org.gnome.gnome-session
auto-save-session -> on
