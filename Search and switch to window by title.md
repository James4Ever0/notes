---
tags: [multi window manager, productivity, search window by name, window manager]
title: Search and switch to window by title
created: '2022-07-27T02:12:56.139Z'
modified: '2022-08-18T16:23:18.653Z'
---

# Search and switch to window by title

## windows

### yal

access and search windows

access files, programs, bookmarks, search engines

## macos

### finda

find windows, browser tabs, code editor buffers, browser history, apps, files

## linux

kupfer plugin window list

use xdotool and wmctrl

Window List command (wmctrl):
```bash
$ wmctrl -lx
0x0540043e  0 google-chrome.Google-chrome  ubunzeus Search for window title? - Ask Ubuntu - Google Chrome
0x050000ec  0 Mail.Thunderbird      ubunzeus Inbox - Mozilla Thunderbird
0x04e1068d  0 gnome-terminal-server.Gnome-terminal  ubunzeus ljames@ubunzeus: ~
```
Command to switch to specific window (xdotool)
```bash
$ xdotool windowactivate 0x0540043e
```
The above command will switch to the Windows with the ID 0x0540043e, which is specific from the list for this Askubuntu message entry.

They are both in the repository:
```bash
$ sudo apt install wmctrl xdotool
```
