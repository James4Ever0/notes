---
tags: [android, brightness, bug, reinstall, system manage, termux]
title: After Termux Reinstallation
created: '2021-12-20T09:04:08.000Z'
modified: '2022-08-18T12:29:26.544Z'
---

# After Termux Reinstallation

grant permission for termux:api

android.permission.WRITE_SETTINGS can only be granted in settings tab.

https://github.com/TilesOrganization/support/wiki/How-to-use-ADB-to-grant-permissions

adb shell pm grant com.rascarlo.quick.settings.tiles android.permission.WRITE_SECURE_SETTINGS

pm grant com.termux.api android.permission.WRITE_SECURE_SETTINGS

pm list packages

the brightness bug is solved by uninstalling the unintended settings app. i don't know if this will cause more problems.

to remove termux banner/ termux welcome message:
```bash
cd .. && cd usr/etc && rm -rf motd
```

