---
created: 2025-10-12T19:29:50+08:00
modified: 2025-10-12T19:34:26+08:00
---

# How to monitor for fire alarm and other emergency events

Use an online server to pull data from ntfy.io constantly and monitor for potential problems. If anything bad happens, you can trigger an alarm in one of your endpoint receivers, or just trigger immediate local actions in first place such as switching off power supply.

You can monitor camera feed. If no new camera feed coming through, you could fire a camera offline event.

Before the real world use cases, you first test the effectiveness of such alarm system

Make sure the data collection system can only send data to the external server, but not vice versa. Close all unnecessary ports and connections.
