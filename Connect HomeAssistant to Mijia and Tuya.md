---
title: Connect HomeAssistant to Mijia and Tuya
created: '2024-09-08T15:35:50.923Z'
modified: '2024-09-15T14:14:11.613Z'
---

# Connect HomeAssistant to Mijia and Tuya

Mijia references:

https://github.com/rytilahti/python-miio

Tuya references:

https://github.com/jasonacox/tinytuya

---

For smoke detectors, we can use microphones to detect the beeping sound, then use Mijia SDK to automate PC switches. Meanwhile we can push notification elsewhere.

If one cannot access Mijia switches, just execute the `poweroff` command through `ssh`. Make sure `root` is accessible.

```bash
# molly-guard will not know this.
timeout 10 ssh root@<hostname> poweroff
```

