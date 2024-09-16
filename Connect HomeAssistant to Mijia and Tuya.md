---
title: Connect HomeAssistant to Mijia and Tuya
created: '2024-09-08T15:35:50.923Z'
modified: '2024-09-16T06:49:45.675Z'
---

# Connect HomeAssistant to Mijia and Tuya

Mijia references:

https://github.com/rytilahti/python-miio

Tuya references:

https://github.com/jasonacox/tinytuya

---

For smoke detectors, we can use microphones to detect the beeping sound, then use Mijia SDK to automate PC switches. Meanwhile we can push notifications elsewhere.

If one cannot access Mijia switches, just execute `poweroff` command through `ssh`. Make sure `root` is accessible.

```bash
# molly-guard will not know this.
timeout 10 ssh root@<hostname> poweroff
```

---

You need to figure out if your machine actually contains any builtin microphone. If not, you may need to attach 3.5mm external microphones or USB microphone.

Run the following code:

```python
import pyaudio
audio = pyaudio.PyAudio()
```

If the following lines showing up, you may need to disable specific devices in ``:

```

```

