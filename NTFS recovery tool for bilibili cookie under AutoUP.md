---
tags: [NTFS, recovery, remedy, system manage, undelete]
title: NTFS recovery tool for bilibili cookie under AutoUP
created: '2022-07-17T19:09:33.000Z'
modified: '2022-08-18T16:01:46.697Z'
---

# NTFS recovery tool for bilibili cookie under AutoUP

unmount the disk before scanning!

ntfsundelete
autopsy
disk drill
recuperabit(good for small files)
recoverpy
korczis/foremost

could also try to retrieve from android phones (/data/data/tv.danmaku.bili)

https://roubert.name/joakim/androidfilerecovery/

apt-get install testdisk pv extundelete

adb shell ls /dev/block

Now let us dump the content of that /dev/block/mmcblk0 that we found to the computer. With adb shell we can become superuser and execute cat to dump the content like this:

$ ./adb shell su -c "cat /dev/block/mmcblk0" | pv > mmcblk0.raw

Pipe Viwer (pv) is optional, but I like to see the transfer progress information it provides.
(And of course you can change mmcblk0.raw to some other directory/filename if you want to.)

Addition: André Paixão wrote to me that he just got an empty file with the command above. He solved it by using adbd insecure.

Addition: Daniel Jeliński wrote to me that he ran into issues with LF encoding. The solution that worked for him was:

./adb shell su -c "cat /dev/block/mmcblk0" | pv | sed 's/^M$//' > mmcblk0.raw

...where ^M is what you get by pressing Ctrl+V followed by Ctrl+M.

Addition: Marc also ran into the LF problems, but solved it this way:

./adb shell "su -c 'stty raw; cat /dev/block/mmcblk0'" | pv > mmcblk0.raw

Addition: Tim de Waal wrote to me that he prefers using netcat/gzip instead:

On the Android device (adb shell with su), run:

dd if=/dev/block/mmcblk0 | gzip -9 | nc -l 5555

On the computer, run:

nc [AndroidIP] 5555 | pv -b > mmcblk0.img.gz

testdisk mmcblk0.raw
