---
title: gitter developer tokens and qq opqbot, reverse engineering qq protocols and more
created: 2022-08-13T08:54:17+08:00
modified: 2022-08-14T23:29:06+08:00
---

# gitter developer tokens and qq opqbot, reverse engineering qq protocols and more

opqbotå®æ¹å·²ç»è¯´äº ç»éè¿ç¨ä¸­ä¼ç¨å°è¿ç¨çæå¡å¨ è¿ä¸ªæå¡å¨ç©¶ç«å¨å¹²ä»ä¹ä¸å¾èç¥ å¯è½åç»éæå³ä¹å¯è½æ²¡æå³ç³» ä½æ¯æå¡å¨ç»´æ¤æé´æ¯æ²¡æ³æ«ç ç»å½ç å¦ææå¯ä»¥æ­£å¸¸ä½¿ç¨çsecdataæ¯å¯ä»¥ç´æ¥å¯å¨æå¡ç ä¸éè¦æå¡å¨ æä»¥ä¼°è®¡è¿ä¸ªæå¡å¨å¾å¯è½å°±æ¯æ¿æ¥è§£æcookieç

login error:
```
2022/08/14 00:01:24.808 [I]  Scan Status 48 Uin 0 
2022/08/14 00:01:25.880 [I]  Scan Status 48 Uin 0 
2022/08/14 00:01:26.937 [I]  Scan Status 53 Uin 0
2022/08/14 00:01:27.998 [I]  Scan Status 53 Uin 0 
2022/08/14 00:01:29.054 [N]  User <userId> ç»å½ä¸­..è¯·å¿è¿ç»­æä½,ç»å½æååæéæ¾è¿æ¥åå¨ç»§ç»­æä½ ç»éæååè¯·å¿é¢ç¹æ«ç åæ¬¡ç»é(é¤éå»ç»å¯¼è´çæçº¿) åä¸åºå»ç¾¤æ¶æ¯è¯·ææºå å¤© TXæ¥å¸¸é£æ§
=========æ¬æ¡æ¶ ð åè´¹ ð ä½¿ç¨ è°¨é² â ï¸ è¯éª â ï¸ æ¶è´¹ åå¿ç¨äº ð²ï¸ é ð²ï¸ æ³ç¨é
=========äº¤æµç¾¤:757360354 TGç¾¤ç»:https://t.me/IOTQQ      
=========å¼æºç¤¾åº ð https://github.com/opq-osc ð       
=========é¡¹ç®ä¸»é¡µ ð https://github.com/OPQBOT/OPQ/wiki ð
=========é¡¹ç®Wiki ð https://github.com/OPQBOT/OPQ/wiki ð
2022/08/14 00:02:30.234 [W]  recvPump session 0D48F5949075DA13D3A9F83838903920
2022/08/14 00:02:30.234 [A]  Default Closed:0D48F5949075DA13D3A9F83838903920
2022/08/14 00:02:30.235 [D]  Unregister In Conn -> 0D48F5949075DA13D3A9F83838903920
```

å³äºèªå¨å ç¾¤ å¯ä»¥èèä½¿ç¨å®åææºèªå¯å¨åè½ï¼éè¦ä¸è½½[startup manager](https://play.google.com/store/apps/details?id=imoblife.startupmanager) æè[boot manager](https://play.google.com/store/apps/details?id=de.defim.apk.bootmanager&showAllReviews=true)ï¼ærootæéåxposedæ¡æ¶ï¼ï¼ ç¨[termux-appium](https://www.npmjs.com/package/termux-appium) èªå¨æä½ææºå¨èç½çæåµä¸èªå¯å¨å ç¾¤

ç°å¨æä¸¤ä¸ªæ å[onebot](https://onebot.dev/) [nonebot](https://nb2.baka.icu/)

è¿ä¸¤ä¸ªåè®®é½ä¸æ¯æä¸»å¨å å¥½å å ç¾¤ è¿ææ¶çº¢åæ¹æ³ è³å°mac qqåè®®æ¯æè¿äºæ¹æ³ ä½æ¯å¶ä»çåè®®æ¯å¦æè¡¨ ipadåè®®æ¯ä¸æ¯æå°±ä¸æ¸æ¥äº

onebotæå¤§éç[qqééå¨](https://onebot.dev/ecosystem.html#onebot-12) ènonebotæ[å¤§éçæä»¶åé¤äºqqä»¥å¤çè¿æ¥å¨](https://nb2.baka.icu/store)

nonebotå¯ä»¥[è¿æ¥onebot](https://onebot.adapters.nonebot.dev/docs/guide/installation)

å¨onebotçqqééå¨ä¸­ oicqå¯ä»¥æ¥çqqåå²èå¤©è®°å½ï¼æå¾éªè¯ï¼ å¯è½å¯¹qqçæ°æ®ç¬åæå¸®å© è§é¢ç¬å [oicq](https://github.com/takayama-lily/oicq)è¿ä¸ªééå¨æå¨ç¾¤éé¢å å¥½åçæ¹æ³`addFriend(gid, uid)`å¯ä»¥åè,æä¾äºä¸äºç¨äºéåqqåè®®çç¨åºï¼

[txhook](https://github.com/fuqiuluo/TXHook) è¯¥è½¯ä»¶éåå¨å®å8.0ä»¥ä¸ç³»ç»è¿è¡ï¼çè®ºæ¯æå®å7.0ä»¥ä¸ï¼ä½æ¯å¾å¤é®é¢ãç¾¤å·ï¼901422091 702991373
- è·åShareKey\PublicKey\D2\A2...
- ä¸»å¨æ¦æªåºå®Ecdhå¯é¥åçæ¬
- å¯¹Jce\Protobufçèªå¨åæ
- è¿æ»¤æåï¼æ¯æé«çº§è¿æ»¤ï¼é¿ææåé¡µé¢çæç´¢æ å±ç¤º/éèå¾æ ï¼

[protobuf online decode](https://protobuf-decoder.netlify.app)
[protobuf unpack-tools](https://github.com/takayama-lily/unpack-tools)

ä¹æä¸äºå¯ä»¥è¿è¡äºæ¬¡å¼åç[qq web api](https://github.com/takayama-lily/oicq/blob/main/web-api.md) æç´¢QQå·åç¾¤å· ä¸æä¸ªæ§ç­¾åç­æ´å¤ä¿¡æ¯ æè®¸å¯ä»¥æç´¢å³é®è¯ï¼

è¿äºééå¨ä¸­æçæä¾äºqqé¢éçæ¯æï¼

[oicq-guild](https://github.com/takayama-lily/oicq-guild)

ä¹å¯ä»¥èèç¨[frida](https://frida.re/) [ghidra](https://github.com/NationalSecurityAgency/ghidra) [radare2](https://rada.re/n/radare2.html) [cutter](https://cutter.re/)æ¥[éåopqbotçgoç¼è¯å¥½äºçç¨åº](https://cn.bing.com/search?q=reverse+go+binary&form=CHRDEF&sp=-1&pq=reverse+go+binary&sc=0-17&qs=n&sk=&cvid=3A1FCCCF9C2F495DB516CB656D281DCA&ghsh=0&ghacc=0&ghpl=) æèéååæopqbotçç½ç»è¯·æ±æ°æ® çè³ç´æ¥å¨æè°ç¨opqbotéé¢çæ¹æ³ ç´æ¥ç¨å¶ä»æºå¨äººç»éä¹åè·å¾çcookieè¿è¡æä½

to get the token, login first, then visit [here](https://developer.gitter.im/apps) or click "sign in" [here](https://developer.gitter.im/)

æ®è¯´æ«ç ç»å½åªæ¯æåä¸ä¸ªipä¸é¢çç»é ä¸ç¥éä¸ºä»ä¹è¿ä¸ªopqbotç»éå¤±è´¥ ä½æ¯å¶ä»æºå¨äººé½æä¾äºè´¦å·å¯ç ç»éçæ¸ é å°opqbotçåè®®éååºæ¥ æè®¸å¯ä»¥æé«ç»éæåç å®ç°ç¸åçåè½

é»è®¤(å¯ä¿®æ¹)å¨ ./data/your-account/ ä¸ä¼èªå¨çædevice.jsonè®¾å¤æä»¶ï¼ç»å½å®æåæ­¤è®¾å¤æä»¶é¿æææ
è®¾å¤æä»¶ççæå¹¶ééæºï¼èæ¯ä½¿ç¨åºå®ç®æ³ï¼ä¸ä¸ªè´¦å·ä¼æ°¸è¿çæåä¸ä»½è®¾å¤æä»¶
å¦æéè¦å¨å¼å°æå¡å¨ä¸ç»å½ï¼å»ºè®®åå¨å¸¸ç¨å°éè¿è®¾å¤éªè¯å¹¶ç»å½ææºä¸æ®µæ¶é´
ç±äºä¼çæç¸åè®¾å¤æä»¶ï¼åªè¦ä¸æå¨ä¿®æ¹ï¼åªééªè¯ä¸æ¬¡ï¼å¨ä»»ä½å°åºé½å¯ç´æ¥ç»å½


it seems the login issue of opqbot is related to the account itself, not gitter token, software version or proxy

by the way we could always use go-cqhttp, without the ability to collect red packet and add group/friends.

qq add group/friends may be enabled by our windows virtual machines. without opq, it is very memory intensive.

tokens:
```
74eb7eb14aa36d1b9c2c663bc49335e8becd5318
```
```
2d391bd7639362032d09abfc5a9cc6368b7664d5
```
```
bdf52599d992665509ee5b0b533d5eed08452def
```
