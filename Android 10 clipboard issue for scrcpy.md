---
tags: [android, system manage, tweaks, clipboard, sync]
created: 2022-02-21T19:44:30+08:00
modified: 2022-02-21T21:23:52+08:00
---

# Android 10 clipboard issue for scrcpy

com.github.kr328.clipboard.ClipboardProxy.getPrimaryClip

Magisk Module:
Riru - Clipboard Whitelist
will white list clipboard manager app.

https://github.com/Kr328/Riru-ClipboardWhitelist

https://t.me/kr328_riru_modules

script.sh:

scrcpy -K -S 2>&1 | python3 reader.py

reader.py:

import os
import subprocess
import re

class Response(object):
    status = None
    data = None


def parseResponse(resultString):
    response = re.findall(r"^Broadcasting: Intent { flg=0x400000 cmp=ch.pete.adbclipboard/.ReadReceiver }\nBroadcast completed: result=-1, data=\"((.*\n?)+)\"$",resultString)[0][0]
    return response

def readFromDevice():
    adbProcess = subprocess.Popen(
        ['adb',
            'shell', 'am',
            'broadcast',
            '-n', 'ch.pete.adbclipboard/.ReadReceiver'],
        stdout=subprocess.PIPE)
    resultString = adbProcess.communicate()[0]
    print("read device response:\n{}"
              .format(resultString))
    try:
        result = parseResponse(resultString.decode("utf-8"))
        print("raw:\n",resultString)
        print("result:\n",result)
        return result
    except:
        traceback.print_exc()
    return


def setClipboard(data):
    with open("target.out","w+",encoding="utf-8") as f:
        f.write(data)
    fetch_clipboard = "cat target.out | xclip -selection c" 
    os.system(fetch_clipboard)
while True:
    content = input()
    print("CONTENT:",content)
    if "Calling uid 0 does not own package com.android.shell" in content:
        print("!!!!!!!!!!ERROR FETCHING CLIPBOARD!!!!!!!!!!")
        data = readFromDevice()
        if data is not None:
            setClipboard(data)
#        with open("target.out","wb"
#        os.system(fetch_clipboard)
