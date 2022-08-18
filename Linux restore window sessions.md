---
tags: [linux, restore, restore session, service]
title: Linux restore window sessions
created: '2022-07-27T00:06:40.000Z'
modified: '2022-08-18T14:57:27.381Z'
---

# Linux restore window sessions

to relaunch app in given workspace

tools:
wmctrl
[devilspie](https://help.ubuntu.com/community/Devilspie)
[launch_on_workspace](https://github.com/xblahoud/launch_on_workspace)

references:
https://unix.stackexchange.com/questions/27050/how-to-start-an-application-on-a-different-workspace
https://askubuntu.com/questions/89946/open-application-in-specific-workspace

npm install -g linux-window-session-manager
restore session manually

dconf-editor
org.gnome.gnome-session
auto-save-session -> on
