---
tags: [termux, reinstall, system manage, bug, brihg]
created: 2021-12-20T17:04:08+08:00
modified: 2022-05-31T12:32:57+08:00
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
cd .. && cd usr/etc && rm -rf motd
