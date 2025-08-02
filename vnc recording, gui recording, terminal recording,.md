---
created: 2025-08-02T09:25:02+08:00
modified: 2025-08-02T18:26:21+08:00
---

# vnc recording, gui recording, terminal recording,

timecode and Metadata is important in gui action recordings

we need to embed the timecode and session uuid into terminal capture, monitor capture and video/audio capture.

---

manual key frame annotated gui operation video: gui-world

https://arxiv.org/html/2406.10819v2

---

record raw tcp data of vnc and parse results, so we can get the keyboard and mouse events

we can use websocketify to record tcp data

---

use customized vnc client to simplify human input events and translate into specific events to server, eliminating various disturbance like random moving cursor, dragging and dropping etc

---

dockerized Ubuntu environment vnc server

https://github.com/x11vnc/x11vnc-desktop

---

time code can also be used for real time agent clustering and collaboration

---

vnc recording:

vncproxy
novnc
vnc2video

https://github.com/amitbet/vncproxy

https://github.com/vprix/vncproxy

https://github.com/evangwt/go-vncproxy

---

terminal capture:

asciinema
terminal-recorder

https://github.com/asciinema/asciinema

https://github.com/asciinema/agg

---

hardware recording:

video recording with timecode
keyboard/mouse usb signal recording with kernel, Wireshark and timecode
