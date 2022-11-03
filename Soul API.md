---
tags: [API, audio source, information gathering, scraping, soul, text source, video source]
title: Soul API
created: '2022-07-08T15:57:27.000Z'
modified: '2022-11-03T08:52:26.220Z'
---

# Soul APIs


[soul绕过ssl双向验证](https://www.freesion.com/article/9811692393/) justTRUSTME(xposed)加上反编译SDK获取证书密码 [backup blog](https://blog.csdn.net/qq_38316655/article/details/104176882)

[use adb to setup mitmproxy on android](https://www.trickster.dev/post/setting-up-mitmproxy-with-android/)

```bash
cd ~/Library/Android/sdk/platform-tools/

# Get the hash of the mitmproxy-ca certificate.
openssl x509 -inform PEM -subject_hash_old -in ~/.mitmproxy/mitmproxy-ca.pem | head -1

# We will use this hash value, append '.0' (dot zero) and use this as the filename for the resulting Android certificate
cat ~/.mitmproxy/mitmproxy-ca.pem > c8750f0d.0
openssl x509 -inform PEM -text -in ~/.mitmproxy/mitmproxy-ca.pem -out /dev/null >> c8750f0d.0

# In an other terminal, we will start the emulator with writable /system volume
cd ~/Library/Android/sdk/emulator/

# In order to launch an available avd, we list them first.
./emulator -list-avds
./emulator -writable-system @Pixel_3a_XL_API_28

# We go back to the first terminal and we use adb tool to transfert the certificate
adb root
adb push c8750f0d.0 /storage/emulated/0/Download

# Then, we will mount the volume and get access to the shell
adb shell mount -o rw,remount /;
adb shell

# In the device Android shell, we will move the certificate inside the system partition in the folder '/system/etc/security/'
cp /storage/emulated/0/Download/c8750f0d.0 /system/etc/security/cacerts/
chmod 644 /system/etc/security/cacerts/c8750f0d.0
```

可能的系统设置

```log
su -c settings list global | grep proxy
global_http_proxy_exclusion_list=
                                global_http_proxy_host=
                      global_http_proxy_port=0
             global_proxy_pac_url=
 http_proxy=:0
```

灵魂测试卡片信息，获取签名*
https://api.soulapp.cn/html/measureResult/info/v2?userIdEcpt=加密用户ID

用户头像和签名等信息*
https://api-h5.soulapp.cn/html/v2/user/info?userIdEcpt=加密用户ID

单条瞬间展开信息*
https://api-h5.soulapp.cn/html/v3/post/detail?postIdEcpt=加密瞬间ID

单条瞬间展开页面*
https://w3.soulapp-inc.cn/activity/#/web/topic/detail?postIdEcpt=加密瞬间ID

用户发布瞬间信息，只有最新的10条*
https://api-h5.soulapp.cn/html/v2/post/homepage?userIdEcpt=加密用户ID

用户发布瞬间页面，只有最新的10条*
https://w3.soulapp-inc.cn/activity/#/web/user?userIdEcpt=加密用户ID

获取热门瞬间，只有最新的30条*
https://api-h5.soulapp.cn/html/v2/post/hot?pageIndex=1（前3页）

获取标签的瞬间信息，只有最新的30条*
https://api-h5.soulapp.cn/html/v2/tag/post?tagIdEcpt=加密标签ID

获取标签的瞬间页面，只有最新的30条*
https://w3.soulapp-inc.cn/activity/#/web/tag?tagIdEcpt=加密标签ID

随机播放音频信息，随机几首*
https://api-h5.soulapp.cn/html/v2/post/orimusicList/recommend

设置超萌捏脸页面*
https://app.soulapp.cn/avator/#/avatar/create?sex=1&version=3.10.0

注销账号页面*
https://app.soulapp.cn/app/#/account
https://app.soulapp.cn/app/#/destroy
