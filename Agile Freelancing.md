---
created: 2022-01-10T18:42:04+00:00
modified: 2022-01-12T17:16:43+00:00
---

# Agile Freelancing

Apps like QQ, Wechat, Dingtalk can be launched on linux, windows.

闲鱼要anbox 在 Windows上面需要虚拟机 或者直接http投屏就可以 也可以监控的

https://blog.csdn.net/qq_36737934/article/details/90346757

https://mirrors.aliyun.com/deepin apricot (with respect to dist/*)

deb packages are missing from community mirror.
https://github.com/vufa/deepin-wine-qq-arch/issues/27

https://www.bilibili.com/read/cv12914431


podman run -d --name qq \
    --device /dev/snd --ipc="host"\
    -v $HOME/TencentFiles:/TencentFiles \
    -v /tmp/.X11-unix:/tmp/.X11-unix \
    -e XMODIFIERS=@im=fcitx \
    -e QT_IM_MODULE=fcitx \
    -e GTK_IM_MODULE=fcitx \
    -e DISPLAY=unix$DISPLAY \
    -e AUDIO_GID=`getent group audio | cut -d: -f3` \
    -e VIDEO_GID=`getent group video | cut -d: -f3` \
    -e GID=`id -g` \
    -e UID=`id -u` \
    bestwu/qq:im

podman run -d --name wechat --device /dev/snd --ipc="host"\
    -v /tmp/.X11-unix:/tmp/.X11-unix \
    -v $HOME/WeChatFiles:/WeChatFiles \
    -e DISPLAY=unix$DISPLAY \
    -e XMODIFIERS=@im=fcitx \
    -e QT_IM_MODULE=fcitx \
    -e GTK_IM_MODULE=fcitx \
    -e AUDIO_GID=`getent group audio | cut -d: -f3` \
    -e GID=`id -g` \
    -e UID=`id -u` \
    bestwu/wechat
