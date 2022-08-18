---
created: 2021-12-20T05:56:45+08:00
modified: 2021-12-23T15:14:58+08:00
---

# Baidu Tieba Login (QR Code)

Assigned a job.

Cloud Phone:
http://www.ddyun.com/sem/pcddybdyunkong/?bd_vid=7609174489837191328
17756220843:fsfs5214

QR Link:
https://wappass.baidu.com/wp/?qrlogin&t=1640006201&error=0&sign=v1_13fa5a31cf31fa864475cbf3fd2fc&cmd=login&lp=pc&tpl=tb&adapter=3&logPage=traceId%3Apc_loginv4_1640006201%2ClogPage%3Aloginv4&qrloginfrom=pc&local=%E5%8D%97%E4%BA%AC

This job has no public data to refer. we need to monitor the tieba app.
mitmproxy --mode socks5 --listen-port 8050 --save-stream-file logs
Run mitmproxy without options to generate the mitm certificate. Install the certificate (usually ~/.mitmproxy/mitmproxy-ca-cert.cer) in the Android phone. It may be needed to change the extension to .crt to install it.

frida is needed to disable certificate-pinning, or if this is somehow possible. (also via justtrustme, xposed)
https://hub.fastgit.org/httptoolkit/frida-android-unpinning
https://httptoolkit.tech/blog/frida-certificate-pinning/

setenforce 0
to disable stack errors

to connect to frida-server:

https://github.com/15872998154/frida_termux

./frida_server -l 0.0.0.0:27042 

frida -H 127.0.0.1:27042 --codeshare sowdust/universal-android-ssl-pinning-bypass-2  -f com.baidu.tieba --no-pause

i will not know if the client will be satisfied or not. i only know this would be very hard to solve. if not good i will quit.


to read flow:
mitmproxy -n --showhost -r logs.log

print xxd line and ascii parse only:
cat logs2.log | xxd | awk '{print $1" "$NF}'

cat logs2.log | xxd | awk '{print $1" "$NF}' | grep -C 5 http://wap
0012f020: ss-Control-Allow
0012f030: -Methods,18:GET,
0012f040: OPTIONS,]
0012f050: 59:27:Access-Con
0012f060: trol-Allow-Origi
0012f070: n,24:http://wapp
0012f080: ass.baidu.com,]2
0012f090: 8:10:Connection,
0012f0a0: 10:keep-alive,]2
0012f0b0: 7:16:Content-Enc
0012f0c0: oding,4:gzip,]44

cat logs2.log | xxd | awk '{print $1" "$NF}' | grep -C 5 https://wap
001190e0: ite,]28:14:sec-f
001190f0: etch-mode,7:no-c
00119100: ors,]26:14:sec-f
00119110: etch-dest,5:styl
00119120: e,]40:7:referer,
00119130: 26:https://wappa
00119140: ss.baidu.com/,]3
00119150: 6:15:accept-enco
00119160: de
00119170: flate,]37:15:acc
00119180: ept-language,14:
--
0011aed0: ite,]28:14:sec-f
0011aee0: etch-mode,7:no-c
0011aef0: ors,]27:14:sec-f
0011af00: etch-dest,6:scri
0011af10: pt,]40:7:referer
0011af20: ,26:https://wapp
0011af30: ass.baidu.com/,]
0011af40: 36:15:accept-enc
0011af50: d
0011af60: eflate,]37:15:ac
0011af70: cept-language,14
--
0011ccd0: -site,]28:14:sec
0011cce0: -fetch-mode,7:no
0011ccf0: -cors,]26:14:sec
0011cd00: -fetch-dest,5:st
0011cd10: yle,]40:7:refere
0011cd20: r,26:https://wap
0011cd30: pass.baidu.com/,
0011cd40: ]36:15:accept-en
0011cd50: coding,13:gzip,
0011cd60: deflate,]37:15:a
0011cd70: ccept-language,1
--
00121f40: -site,]28:14:Sec
00121f50: -Fetch-Mode,7:no
00121f60: -cors,]26:14:Sec
00121f70: -Fetch-Dest,5:im
00121f80: age,]40:7:Refere
00121f90: r,26:https://wap
00121fa0: pass.baidu.com/,
00121fb0: ]36:15:Accept-En
00121fc0: coding,13:gzip,
00121fd0: deflate,]37:15:A
00121fe0: ccept-Language,1
--
0012f550: in,]28:14:Sec-Fe
0012f560: tch-Mode,7:no-co
0012f570: rs,]27:14:Sec-Fe
0012f580: tch-Dest,6:scrip
0012f590: t,]256:7:Referer
0012f5a0: ,241:https://wap
0012f5b0: pass.baidu.com/w
0012f5c0: p/?qrlogin&t=163
0012f5d0: 9980306&error=0&
0012f5e0: sign=v1_f3b74f3a
0012f5f0: 21e355010985e711
--
00139700: ,]28:14:Sec-Fetc
00139710: h-Mode,7:no-cors
00139720: ,]26:14:Sec-Fetc
00139730: h-Dest,5:image,]
00139740: 40:7:Referer,26:
00139750: https://wappass.
00139760: baidu.com/,]36:1
00139770: 5:Accept-Encodin
00139780: defla
00139790: te,]37:15:Accept
001397a0: -Language,14:en-
--
0013db70: 39997136312&tpl=
0013db80: tb&auto_statisti
0013db90: c=e2V2ZW50VHlwZT
0013dba0: p0b3VjaC1qcy1lcn
0013dbb0: Jvcn0=&extrajson
0013dbc0: =https://wappass
0013dbd0: .baidu.com/wp/?q
0013dbe0: rlogin&t=1639980
0013dbf0: 306&error=0&sign
0013dc00: =v1_f3b74f3a21e3
0013dc10: 55010985e7113869

https://blog.csdn.net/qq_27644127/article/details/112987332

with a plugin to collect statistics:
http://file.taotaoya.top/load/TT.rar

that guy wants me to discover barcode first.

i may paste cookies here:
https://termbin.com/lq5e

use ccrypt, xxd and nc to do transport. (do you have these?)

cat cookies.log.cpt | xxd | nc termbin.com 9999
xxd -r
ccrypt -c cookies.log.cpt

passwd:abcdefg


a typical QR login link on android:
https://wappass.baidu.com/wp/?qrlogin&t=1639929144&error=0&sign=v1_3b3e89197877163a12614a9a7f519&cmd=login&lp=pc&tpl=tb&adapter=3&clientfrom=native&qrloginfrom=native&local=%E9%93%9C%E9%99%B5

parsed with elinks copied with termux-clipboard-set:

   Link: [1]canonical
   Link: [2]alternate (handheld)

                         ç¾åº¦è´´å§äºç»´ç ç»å½--pythonç¬è«

   [3]lxguang_tao 2021-01-22 18:11:49 547 æ¶è
   åç±»ä¸æ ï¼ [4]python æç« æ ç­¾ï¼ [5]python
   çæå£°æï¼æ¬æä¸ºåä¸»ååæç« ï¼éµå¾ª [6]CC 4.0 BY-SA çæåè®®ï¼è½¬è½½è¯·éä¸å
   æåºå¤é¾æ¥åæ¬å£°æã
   æ¬æé¾æ¥ï¼[7]https://blog.csdn.net/qq_27644127/article/details/112987332
   çæ
   [8][IMG] [9]python ä¸æ æ¶å½è¯¥åå®¹
   1 ç¯æç«  0 è®¢é
   è®¢éä¸æ 

  ç¾åº¦è´´å§äºç»´ç ç»å½--pythonç¬è«

     â¢Â 
          â¢Â [10]ç ç©¶æè·¯
          â¢Â 
               â¢Â [11]æ¢ç´¢è¿ç¨
               â¢Â [12]æè·¯æ»ç»

          â¢Â [13]ä»£ç å®ç°
          â¢Â 
               â¢Â 
                    â¢Â [14]æéææ¯
                    â¢Â [15]ä»£ç 

          â¢Â [16]æ»ç»

ç ç©¶æè·¯

     å¦æéè¯»æ­¤æç« çå°ä¼ä¼´ä¹åç ç©¶è¿è´´å§ç¸å³çæ¥å£çè¯ï¼å°±ä¼ç¥éï¼é£äºéè¦ç»
     å½æè½å®ç°çåè½æ¥å£ï¼ä½ å»ç¬è«çè¯è¦æºå¸¦ä¸ä¸ªCookie BDUSSï¼æäºå®å°±ä¼éè¿
     èº«ä»½éªè¯ãè¿ä¸ªBDUSSä¹å¯ä»¥éè¿æµè§å¨è®¿é®è´´å§é¡µé¢ï¼ä»èè·å¾ï¼ä½å¨åä¸ä¸ªæµ
     è§å¨ä¸­å¦ææ´æ¢å¸å·ç»å½ï¼é£ä¹ä½ ä»è¿ä¸ªæµè§å¨ä¸­æ¿å°çä¹åé£ä¸ªBDUSSå°±ä¼å¤±æ
     ï¼ä¸å¯è½è¿ä¸ªæµè§å¨æ°¸è¿æçè¿ä¸ªå¸å·ï¼å¹¶ä¸ä¿è¯ä¸ä¼å»ä¿®æ¹å¯ç ï¼ãä¸ºäºè·å¾ä¸
     ä¸ªæ°¸ä¸å¤±æçBDUSSï¼æä»¬å¯ä»¥éè¿ç»å½æ¹æ³æ¥è·åBDUSSï¼ä½æä»¬ä¸å¯è½ä¼ä½¿ç¨è¿
     ä¸ªBDUSSå»åéåºååæ¢å¸å·æä½ï¼æä»¥å®ä¸è¬æ¿å°åå°±ä¸ä¼å¤±æï¼é¤éæ¹äºå¯ç 
     ï¼ã

  æ¢ç´¢è¿ç¨

   [17]äºç»´ç 

   Â 1.Â ä¸ç®¡æ¯è´´å§é¦é¡µï¼è¿æ¯å¶ä»å°æ¹çè´´å§ç»å½é¡µé¢ï¼é½ä¼æè¿ä¸ªäºç»´ç ç»å½çå°æ¹
       ãæä»¬ç¬¬ä¸æ­¥æ¯çæä¹å»æ¿å°è¿ä¸ªäºç»´ç å¾çå°åã

   Â 2.Â æè·¯ï¼ç¬åè¿ä¸ªé¡µé¢ï¼ä»é¡µé¢åç´ ä¸­æ¾å°è¿ä¸ªäºç»´ç è¿æ¥ï¼ç»æå°±æ¯ï¼äºç»´ç è¿
       æ¥ä¸æ¯ååºé¡µé¢å è½½åºæ¥çï¼é£å°±è¯´ææ¯éè¿åç»­çæ¥å£è¿åçç¶åæ·»å å°é¡µé¢
       ä¸­çãæä»¥æä»¬æ¥ä¸æ¥è¦å»å¯»æ¾å è½½äºç»´ç çæ¥å£ã

   Â 3.Â å¯»æ¾æ¥å£ï¼æå¼F12ï¼åæ¢å°Networkï¼å·æ°é¡µé¢ï¼ä½ ä¼çå°ä¸æ¡ç±»åä¸ºpngçè®°
       å½ï¼ç¹å¼çå°ååºæ­£æ¯è¿å¼ äºç»´ç å¾ç
       [18]äºç»´ç è¯·æ±å°å

   Â 4.Â æ¥çè¯·æ±ç¸å³åå®¹ï¼å°åï¼åæ°ï¼ç±»åãGetè¯·æ±ï¼æä¸ä¸ªåæ°åå«æ¯sign,lp
       åqrloginfromï¼çå°åä¸¤ä¸ªåæ°çå¼é½æ¯pcãç²çåºè¯¥å¯ä»¥æ¯åºå®å¼pc(çµè
       ç«¯)ãæä»¥ç°å¨å°±åªå©ä¸ä¸ä¸ªåæ°éè¦ææ¸æ¥ï¼é£å°±æ¯signã
       [19]å¨è¿éæå¥å¾çæè¿°

   Â 5.Â éµå¾ªä»£ç ä»ä¸å¾ä¸è¿è¡çè§åï¼è¿ä¸ªsignè¯å®æ¯å¨äºç»´ç å è½½åå°±è·åå°äºï¼æ
       ä»¥æä»¬è¦å¨å®çä¸é¢çè®°å½éå¯»æ¾ä¸ä¸ãç»è¿ä¸çªå¯»æ¾ï¼æç»
       å¨âhttps://passport.baidu.com/v2/api/getqrcode?lp=pc&qrloginfrom=pc&gid=1527EF2-1333-475F-BA75-319AF40E53E7&callback=tangram_guid_1611304323880&apiver=v3&tt=1611304324028&tpl=tb&_=1611304324032â
       çååºä¸­æ¾å°äºsignï¼å½ç¶ååºä¸­ææ´ä¸ªå¾çé¾æ¥ã

   Â 6.Â ä¸è¿åç¹åï¼è¿ä¸ªè¯·æ±ä¸­ä¹æå¥½å¤ä¸ªåæ°ãä¸è¿çå°è¿ä¸ªåæ°ï¼åç°æå¥½å ä¸ªé½
       æ¯æ æä¹çãttå_æä»¬çé¿åº¦å¯ä»¥æ¨æ­åºåºè¯¥æ¯æ¶é´æ³ï¼ç»è¿éªè¯ï¼ç¡®å®æ¯å½
       æ¶æ¶é´çæ¶é´æ³ãæä»¥æä»¬ä¸»è¦éè¦æ»ç ´çå°±æ¯gidä¸callbackãè¿æ¯èæ ·å­ï¼
       åæ¾gidï¼å»ä¸é¢æ¾ä½æ¯å°±æ¯æ¾ä¸å°ãçgidåæ¯é£ç§å¯ä¸å¼ï¼pythonä¸­å«uuidã
       æ¢ç¶æ¾ä¸å°ï¼é£å°±å¯è½æ¯åç«¯çæçï¼æä»¥æä»¬å¯ä»¥å»æ¾è¿ä¸ªè¯·æ±åèµ·çjsãç
       çå®è¿ä¸ªåæ°å°åºæ¯æä¹æ¥çãå¨F12 Sourceä¸­æ Ctrl+Shift+Få¨å±æ
       ç´¢âv2/api/getqrcodeâã
       [20]åæ°

   Â 7.Â éè¿æç´¢æä»¬åç°ç¡®å®æ¯åç«¯çæçéæºå¯ä¸å¼ãé£æä»¬å°±å¯ä»¥æ¾å¿å¤§èçèªå·±
       å»çæäºï¼å½ç¶è¦çæåºæ¥çæ ¼å¼ä¸æ ·ãç°å¨å°±åªå©ä¸callbackäºãæ­£å½æè¦æ
       å¥æ³æ¾ä¸å°çæ¶åï¼ççæ³ç ´å£èåºï¼æä¹è¿ä¹é¾æ¾åï¼tmdç¦æ­»äºãæåé¢å
       ç°ï¼å¯å®åé¢é£ä¸ä¸²æ°å­è·ä¸é¢çæ¶é´æ³åºæ¬ä¸æ ·ãå¥½å®¶ä¼ï¼è¿é½è½ç®ä¸ä¸ªåæ°
       ï¼ææ¯ççæãè¿æ ·æåä¸ä¸ªåæ°æä»¬ä¹è½é èªå·±çæãè¿ä¸ªæ¥å£æ¿ä¸ã
       [21]å¨è¿éæå¥å¾çæè¿°

   Â 8.Â å°ç°å¨æä»¬å·²ç»å®ç°äºï¼ï¼1ï¼è¯·æ±è¿åäºç»´ç å°åçæ¥å£ãï¼2ï¼è¿åäºç»´ç å¾
       ççå°åãç¸å½äºæä»¬åå¥½äºè·åBDUSSçç¬¬ä¸æ­¥ãï¼é¿èä¸å£æ°ï¼

   Â 9.Â ç°å¨æä»¬è¦è¿è¡ç¬¬äºé¨ï¼æ«ç åè¿è¡ææ ·çå¤çã

     æ«ç ç»å½åçï¼ç½é¡µçæäºç»´ç åï¼åé¢è½®è¯¢è¿è¡ä¸ä¸ªè¯·æ±ï¼æ¥è¿åå½åäºç»´ç ç
     ç¶æã
     å½äºç»´ç è¢«æ«åï¼è®¿é®äºç»´ç åå®¹ï¼æå¡ç«¯ä¼è¿è¡å¤çï¼æ¯å¦ç»å½ï¼åç»å½æä½ï¼
     å½ç¶å¦æä¸ç´æ²¡ææ«ç è¯·æ±ï¼é£ä¹å°±ä¸ç´å¾ªç¯è¯·æ±ï¼ç´å°äºç»´ç è¿æä¸ºæ­¢ã

   10.Â æ¥çNetworkåç»­åå®¹ï¼åç°ç¡®å®æä¸ä¸ªæ¥å£å¨ä¸åçè¯·æ±ãæ¥çåæ°åç°ï¼é½
       æ¯æä»¬ç©å©ä¸çï¼é¤äºchannel_idæ¯å¾çé¾æ¥ä¸­çä¸ä¸ªåæ°æ¢äºåå­å¤ï¼å¶ä»æ
       ä»¬é½æåæ³è·å¾ã
       [22]çå¬
   11.Â æä»¬ç°å¨è¦åçå°±æ¯æ¨¡ææµè§å¨è¿è¡è½®è¯¢è¯·æ±ï¼å½è¯·æ±è¿åæ­£ç¡®ç»å½çååºçæ¶
       åï¼åç°å®è¿åäº
       **tangram_guid_1611307815857({"errno":0,"channel_id":"v1_cf81fb2823935db841b5395152de2","channel_v":"{\"status\":0,\"v\":\"3f1a8f93cca689cead144ad405b03945\",\"u\":\"\"}"})
       ** è¿è·ç»å½ææ¯å³ç³»åï¼åç°åé¢å®åè°ç¨äºä¸ä¸ªåå£ï¼çè¿åå­å°±ç¥éäºï¼
       å°±æ¯å®äºã
   12.Â /v3/login/main/qrbdusslogin
       [23]æè¿å ä¸ªåæ°
   13.Â åç°äºèç³»ï¼bdussæ¯åæè½®è¯¢æ¥å£è¿åçãå¶ä»åæ°ççæ æä¹çé½ç´æ¥ç¨å®
       çãåè°ç¨åè¯´ãå¦æè°ç¨æåï¼è¿åçæ¯ä¸ä¸ªJSONæ°æ®ï¼ä½æ¯å¹¶æ²¡æBDUSS
       ãtmdï¼é½å¿äºæä»¬å»æ¿BDUSSçæ¯å»åªæ¿çåãæç¶å¤§æï¼Cookieåãæç¶ï¼ä»
       ååºä¸­ï¼çå°åå¥æµè§å¨äºCookieã
       [24]cookie
   14.Â è³æ­¤æ¯éè¿äºç»´ç ç»å½æ¿å°BDUSSçå¨é¨è¿ç¨ãè½ç¶çä¸å»ç®åï¼ä½æ¯å®éå»æ
       ä½çæ¶åï¼è¿æ¯æä¸äºåçãåè¿å¤´æ¥ççï¼é£äºåä¹æ¯å¿ç»ä¹è·¯å§ï¼åèµ°è¿ä¸
       éåï¼å°±æ´å å°è±¡æ·±å»ã

  æè·¯æ»ç»

   æ»ç»ä¸ä¸ï¼ åºæ¬ä¸æ¯ä»äººçæèæ¹å¼ä¸æãä»äºç»´ç ä»åªæ¥å¼å§ï¼å¶å®ä¹å°±æ¯ä¸ç´
   ä¸æ­çå¨è°æ¥å£ï¼æ¾åæ°ï¼å¤çååºãä¸ç®¡åªä¸æ­¥ï¼åºæ¬é½ç¦»ä¸å¼è¿ä¸æ ·ãå½ç¶è¿æ¬¡
   çæéè¦çæ¯çè§£äºç»´ç ç»å½çå®éåçï¼åªæçè§£äºå®çåçæè½å»åå¥½å¯¹ç­ã

ä»£ç å®ç°

    æéææ¯

   python requestæ¨¡åï¼jsonæ¨¡åï¼reæ¨¡åï¼time, uuid

    ä»£ç 

 """
 QrCodeLogin.py äºç»´ç ç»å½
 """
 """
 1ãè®¿é®é¦é¡µï¼è·åäºç»´ç 
 2ãè¯·æ±ååºæ¥å£
 3ããããã
 """

 import requests, re, time, json, uuid

 class qrcodeLogin:
     def __init__(self):
         self.get_qrcode_url = "https://passport.baidu.com/v2/api/getqrcode"
         self.unicast_url = "https://passport.baidu.com/channel/unicast"
         self.login_url = "https://passport.baidu.com/v3/login/main/qrbdusslogin"
         self.qrcode = ""
         self.gid = str(uuid.uuid4()).upper()
         self.callback = ""
         self.sign = ""
         self.bduss = ""
         self.headers = {
             "User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:74.0) Gecko/20100101 Firefox/74.0"
         }

     def get_qrcode(self):
         self.callback = "tangram_guid_{}".format(str(int(round(time.time() * 1000))))
         parms = {
             "lp":"pc",
             "qrloginfrom": "pc",
             "gid": self.gid,
             "callback": self.callback,
             "apiver": "v3",
             "tt": int(round(time.time() * 1000)),
             "tpl": "tb",
             "-": int(round(time.time() * 1000))
         }
         html = requests.get(url=self.get_qrcode_url, params=parms, headers=self.headers, verify=False).content.decode('utf-8', errors='ignore')
         # print(html)
         p = re.compile('"imgurl":"(.*?)"')
         p2 = re.compile('"sign":"(.*?)"')


         qrcode = p.findall(html)
         self.sign = p2.findall(html)
         if len(qrcode) == 0:
             return None
         else:
             print("https://"+qrcode[0].replace("\\", ""))
             self.qrcode = "https://"+qrcode[0].replace("\\", "")

     def unicast(self):
         start = time.time()
         errno = 1
         status = 1
         flag = True
         pattern = re.compile('({.*})')
         while(True):
             end = time.time()
             if (end - start) > 300:
                 break
             parms = {
                 "channel_id": self.sign,
                 "qrloginfrom": "pc",
                 "gid": self.gid,
                 "callback": self.callback,
                 "apiver": "v3",
                 "tt": int(round(time.time() * 1000)),
                 "tpl": "tb",
                 "-": int(round(time.time() * 1000))
             }
             jsons = requests.get(url=self.unicast_url, params=parms, headers=self.headers, verify=False)
             html = jsons.content.decode('utf-8', errors="ignore").replace('\\', '').replace('"{', "{").replace('}"', "}")
             try:
                 if errno or status:
                     message = json.loads(re.search(pattern, html).group())
                     errno = message['errno']
                     if errno == 0 and flag:
                         flag = False
                     elif errno == 0:
                         status = message['channel_v']['status']
                 if not errno and not status:
                     message = json.loads(re.search(pattern, html).group())
                     self.bduss = message['channel_v']['v']
                     BDUSS = self.login()
                     print(BDUSS)
                     return BDUSS
             except Exception as e:
                 print(e)
                 break
         return None

     def login(self):
         parm = {
             'v': int(round(time.time() * 1000)),
             'u': 'https://tieba.baidu.com/index.html',
             'bduss': self.bduss,
             'loginVersion': 'v4',
             'qrcode': '1',
             'tpl': 'tb',
             'apiver': 'v3',
             'tt': int(round(time.time() * 1000)),
             'traceid': None,
             'time': round(time.time()),
             'alg': 'v3',
             'sig': 'EsdgfadNMU5rQVl4NWhSDFSDCVSDGFSdfsdfsf8xcVEveFNqanFGK2ZRdDBiejdXQXVhK1ZlRDZKMzsdfDSES==',
             'elapsed': 3,
             'shaOne': '00edf2343d07csdf23478b6ccd34f9a92290d3tg',
             'callback': 'bd__cbs__o5224l',
         }

         login_r = requests.get(self.login_url, headers=self.headers, params=parm, verify=False)
         str_html = login_r.content.decode('utf-8')
         # print(str_html)
         for i in login_r.cookies:
             if i.name == "BDUSS":
                 print('ç»éæå')
                 pname = re.compile('"displayName": "(.*?)"')
                 name_list = pname.findall(str_html)
                 # print(name_list)
                 if len(name_list) > 0:
                     name = name_list[0]
                     return (i.value, name)
                 return (i.value, '')
         return None


     def getImg(self):
         img = requests.get(url=self.qrcode, headers=self.headers, verify=False)
         # print(img.content)
         # with open("tieba.gif", 'wb') as w:
         #     w.write(img.content)
         return img.content



 if __name__ == '__main__':
     s = qrcodeLogin()
     s.get_qrcode()
     s.getImg()
     s.unicast()





æ»ç»

   è¿ä¸æ­¥æ¯æå¼è´´å§èªå¨åå¤§é¨çå³é®ï¼æäºå®æä»¬å°±è½è½»æ¾åå¾å¤äºæäºã
   è´´ä¸èªå·±åçä¸äºç»è®¡å·¥å·çæªå¾ï¼å¦ææå°ä¼ä¼´æå´è¶£ï¼æèéè¦å¸®åå°åè½çï¼
   å¯ä»¥è¯è®ºç§ä¿¡å¦ã
   éä¸ä¸è½½å°åï¼[25]å°å
   [26]å¨è¿éæå¥å¾çæè¿°[27]å¨è¿éæå¥å¾çæè¿°

   [28][IMG][29]lxguang_tao
   [30]å³æ³¨ å³æ³¨

     â¢Â 2
       ç¹èµ
     â¢Â 
       è¸©
     â¢Â [31][IMG] [32]1
       è¯è®º
     â¢Â [33][IMG] [34][IMG] [35][IMG] [36]0
       æ¶è
     â¢Â [37]ä¸é®ä¸è¿
       ä¸é®ä¸è¿
     â¢Â 

     â¢Â [38][IMG]

       æ«ä¸æ«ï¼åäº«æµ·æ¥

   ä¸æ ç®å½
   [39]tieba_sign::mobile_phone: ç¾åº¦è´´å§å¤çº¿ç¨æ«ç ç»é èªå¨ç­¾å° èªå¨æç -æº
   ç 
   05-07
   [40]Tieba_Sign ç¾åº¦è´´å§å¤çº¿ç¨æ«ç ç»é / èªå¨ç­¾å° / èªå¨æç  ç»æµè¯ï¼å¨ä¸ä¸ª
   å¸å·ï¼ä¸å±207ä¸ªè´´å§çæåµä¸ï¼å¨é¨ç­¾å°å®æéåº¦ä¸º5så·¦å³ã(Cookiesç»å½æåµä¸)
   Useï¼Python3.6ä»¥ä¸ ææ ä½¿ç¨æç¨ 1.å®è£ä¾èµ pip install -r
   requirements.txt # Centos yum install zbar -y # Ubuntu sudo apt-get
   install libzbar-dev -y 2.å¢å ç¨æ·éç½® (tieba_sign.py) user_lists = ['ç¨æ·
   å'] # ç¨æ·å,ä¾å¦['ç¨æ·1', 'ç¨æ·2', 'ç¨æ·3'] ä¸å±3ä¸ªç¨æ· # è¯·æç§ä»åå¾å
   çé¡ºåºæ¥ä¾æ¬¡è¿è¡ç»é è¿è¡ python tieba_sign.py # å¼å§ç»å½å¹¶ç­¾å° è¯·æ³¨æï¼å¨
   ææ°çæ¬ä¸­ï¼éè¦æ«ç ç»éï¼ç¨åºè¿è¡çæ¶åï¼ä¼é®ä½ æ¯å¦æç¾åº¦è´´å§
   [41]pythonç¬è«è§£å³ç¾åº¦è´´å§ç»ééªè¯ç é®é¢
   [42]weixin_34236869çåå®¢
   06-29 222
   [43]ä½ä¸ºè´´å§éåº¦ç¨æ·ï¼åäºä¸ªè´´å§ç¬è«èæ¬ æäºä¸äºå«äººçä»£ç ãè®°å¾æä¸ªéªè¯
   ç è§£å³çãå¯æ¯å¿äºé¾æ¥äºï¼ä»å¤©æç»èªå·±æ»åäºã é¦åè¦è®©ç»éé¡»è¦éªè¯ç ï¼ä¸
   åå°ç»éå°±å¥½äºãããåº¦å¨éå¸¸å¿«ä¼å ä¸éªè¯ç å¤§æ³çãããé¡»è¦éªè¯ç çæåµä¸ï¼
   ç´æ¥ç»éè¿åçéè¯¯ä¿¡æ¯æ¯error=257 æå¼è´´å§é¦é¡µéæ©ç»éï¼å¼¹åºéªè¯ç ï¼æ¾å°éª
   è¯ç çé¾æ¥æ¯ å³é®å¨æ°æ ç­¾é¡µä¸­æå¼ æ³¨æå°é¾æ¥æ¯ ...
   è¯è®º1
   [44][IMG]
   [45]
   _____________________
   è¯·åç»å½ ååè¡¨è¯è®º~
   [46]è¡¨æå æå¥è¡¨æ
   [47]è¡¨æå ä»£ç ç

     â¢Â HTML/XML
     â¢Â objective-c
     â¢Â Ruby
     â¢Â PHP
     â¢Â C
     â¢Â C++
     â¢Â JavaScript
     â¢Â Python
     â¢Â Java
     â¢Â CSS
     â¢Â SQL
     â¢Â å¶å®

   [48][Â è¯è®ºÂ ] [49][Â è¯è®ºÂ ]
   [50]Pythonç¬è«ç³»åä¹ç¾åº¦è´´å§ç¬å
   [51]Packager
   11-28 176
   [52]ä»å¤©ç»çä¸ä¸ªç¬è«å°äºä¾ï¼è´´å§æ®µå­ç¬åè¿æ ·ä¸ä¸ªå°åè½ï¼æ°æ®å¢ä»ä»å¨±ä¹ï¼æ²¡
   ææ¶ææ³æ³ è¥æä¾µæï¼è¯·ç§ä¿¡å é¤ æ­¤æ¬¡ç¨å°çä¸ä¸ªè§£æåºBeautiful Soupï¼æ´è½»é
   ç®åå°å¯¹æ°æ®è¿è¡è§£æï¼å·²è·å¾ç®æ æ°æ® è´´å§åçè¿æ¯æ¯è¾å¥½ï¼æä¸å®çåç¬æºå¶
   ï¼æä»¥æä»¬ä¹åºè¯¥æä¸å®çåºå¯¹æªæ½ï¼å·ä½å¯¹åºæä»¬requestsè·åå°çæ°æ®å¯¹åºé¡µé¢
   æºä»£ç ï¼éè¿è§å¯åç°æ°æ®çæ¯å¦å¼æ­¥ä¸æ³¨éç­ç­åç¬é®é¢ ä»¥ä¸æ¯ä»£ç é¨å #
   -*-...
   [53]Python ç½ç»ç¬è«å®æï¼ç¬åç¾åº¦è´´å§é«æ¸åå¾
   ææ°åå¸
   [54]äº®åºéèï¼åæèç©¹
   11-15 654
   [55]åæ®µæ¶é´åå¥å¿ä»¬ææï¼ç¬åè´´å§æå¸å­éçé«æ¸å¾çã äºææ¯è¿æ ·çï¼æå¥
   ä»¬åç°è¢«è´´å§ä¸­æå¥½å¤æ¼äº®çå¾çï¼æ³ä¸è½½åå¾åå£çº¸ï¼ä½æ¯å¸å­éå¾çå¤ªå¤äºï¼ä»
   å¨é½è¦ï¼äºæ¯æ³è®©æå¸®å¿åä¸ªç¬è«ï¼æ¹éä¸è½½ä¸æ¥ã è¦æ±åªæä¸¤ä¸ªï¼ ä¸è½½åå¾ å®
   ç°æ¹éä¸è½½ è¯ä¸å¤è¯´ï¼ç´æ¥å¼å§ã 1. åæç½ç« å¥ä»¬æä¾çå¸å­å°åï¼
   https://tieba.baidu.com/p/6516084831 ã ååæ url ç»æï¼æä»¬å¯ä»¥çå°
   6516084831 æ¯å¸å­ç id ã å¨ å¾éåªçæ¥¼ä¸»ï¼ç¿»é¡µ ç­è¿äºæä½ä¹åï¼é¾æ¥åæäº
   è¿æ · ht

   [56]Pythonæ¨¡æäºç»´ç ç»å½ç¾åº¦
   [57]ljc545wçåå®¢
   12-11 872
   [58]æ¨¡æäºç»´ç ç»å½ç¾åº¦åå¨åé¢åå¤å·¥ä½äºç»´ç å°åç»å½ç¶æè·ågidç»å½åæ°ä»£
   ç é¨åäºç»´ç å±ç¤ºè·åcookieå®æ´ä»£ç åå¨åé¢ åå¨åé¢ åæ®µæ¶é´åäºå©ç¨BDUSS
   å°è¾¾ç¾åº¦é¦é¡µï¼è¿ä¸æ¬¡å°è¯ä½¿ç¨äºç»´ç æ¨¡æç»å½ï¼ç®åç½ä¸è½æå°çç¸å³åå®¹åºæ¬å¤±
   æäºï¼ä½æ¯æè·¯åºæ¬ä¸åï¼æ éæ¯ç¾åº¦æ¹äºäºåæ°ãæ¬æè¾ä¸ºå¤æï¼è¦æ±å¯¹python
   çrequestsæ¨¡åä»¥åChromeå®¡æ¥åç´ æä¸å®äºè§£ï¼æä¸ç¡®å®èªå·±æ¯å¦è½å®å¨è®²æç½ï¼
   è®²å¤å°æ¯å¤å°å§ï¼åä½çå®è¯·åã åå¤å·¥ä½ äºç»´ç å°å æå¼Chromeæµè§å¨ï¼æ¸ç
   æbaidu.comä¸çææco
   [59]pythonæ¨¡æç»éç¾åº¦
   [60]kaerbukaçåå®¢
   07-02 786
   [61]æ¬æåå°å ç®å½ è¯´æ ç¯å¢åå¤ ç»éè¿ç¨åæ ç»éè¿ç¨å®æ´ä»£ç  æææ§æµè¯
   è¯´æ æ¬æåçæ¯ç¾åº¦äºç»´ç æ«ç ç»éï¼è³äºä¸ºä»ä¹è¦åæ«ç ç»éï¼ä¸»è¦æ¯å ä¸ºï¼1ï¼
   ç¨è´¦å·å¯ç ç»éæ¶ï¼å¨æµè¯è¿ç¨ä¸­ï¼å¦ææ¸é¤cookieï¼ä¼å¼¹åºéªè¯ç ï¼è¿ä¸ªåæ¯æ æ
   è°ï¼è¦å½çæ¯å¨ç»éè¿ç¨ä¸­æå¯è½åºåç¾åº¦çè´¦å·ä¿æ¤æºå¶ï¼å°±ç®è¾å¥éªè¯ç ï¼ç¾åº¦
   è¿ä¼å¼ºå¶è¦æ±ææºç­ä¿¡è¿è¡äºæ¬¡éªè¯ï¼è¿ä¸ªè§¦åæºå¶ç®åè¿ä¸æç¡®ã åå¤ç¯å¢ å
   å¤python...
   [62]Pythonç¬åç¾åº¦è´´å§åå¸ä¸­çå¾®ä¿¡å·ï¼åºäºç®åhttpè¯·æ±ï¼
   [63]èå°è¯çåå®¢
   01-03 368
   [64]åäºæ¥å­åª³å¦å¿æä¸ªéæ±ï¼æ³è¦ä¸ä¸ªä»»æè´´å§è¿æä¸»é¢å¸çææåå¸ä¸­çå¾®ä¿¡å·
   ï¼ç¨æ¥åä¸äºå¾®åçæä½ï¼ä½ æçãå ä¸ºæäºè´´å§ä¸é¨å°±æ¯å¾®åäºå ï¼æèå®¢æ·çå¾®
   ä¿¡çï¼è¿æä¸é¨ç¹å®ç¨æ·ç¾¤çè´´å§ï¼éå¸¸ç²¾åï¼æä»¬ä¸è´è®¤ä¸ºæ¯å¶ä»å äººæ¨¡å¼æçè¦
   é«ï¼æä»¥å¦æè½æ¹ä¾¿å¿«æ·çæåå¾®ä¿¡å·ï¼ä»·å¼è¿æ¯å¾é«çï¼äºåæ¥çå¾®ä¿¡å·å°è´­ä¹°è½¬
   åççº¦1%ï¼å·²ç»å¾æ»¡æäºï¼ã é£éæ±å¾æç¡®ï¼è¯´å¹²å°±å¹²ï¼å½å¤©æä¸å°±æ³æè¿ä¸ªå·¥å·
   å®ç°åºæ¥ï¼æå¢æå¼çµèå¼å§è°ç  ...
   [65]17-ç¨pythonç¬åä¸è½½å¥³ç¥ç§ç
   [66]bigzqlçåå®¢
   10-13 1ä¸+
   [67]ä»å¤©å±ä»¬è¦ç¬åè±ç£ç½ https://huaban.com/ è®¾è®¡å¸å¯»æ¾çµæçå¤©å !ææµ·éç
   å¾çç´ æå¯ä»¥ä¸è½½,æ¯ä¸ä¸ªä¼è´¨å¾ççµæåº è¿æ¬¡æä»¬ç¨ requests ç»å½è±ç£ç½ï¼ç¬å
   é¡µé¢ï¼åç¨æ­£åä¸jsonæåæç¨ä¿¡æ¯ï¼æåæè·åçå¾çä¿¡æ¯ ä¿å­å°æ¬å° ä¸ ãç¨
   å°ææ¯ python åºç¡ requests ç»å½é¡µé¢è·åsessionç¨æ·ä¼è¯ï¼ä¸è½½å¾ç æ­£åè¡¨è¾¾
   å¼ æåé¡µé¢çæç¨ä¿¡æ¯ jsonè§£æé¡µé¢ä¸­çå¾ç äºã ç®æ é¡µé¢
   https://huaban.com/search/?q=å¥³ç¥&catego
   [68]ç²¾å¿æ´ç|Pythonç±å¥½èç¤¾åºåå²æç« åéï¼ä½èç¯ï¼--20190925ä»è±ç£è·å
   [69]å°ä»å¥³è¯´ï¼ä½è¡å¥½äºï¼ä¸é®åç¨
   09-25 4719
   [70]ç²¾å¿æ´ç|Pythonç±å¥½èç¤¾åºåå²æç« åéï¼ä½èç¯ï¼ åèæä»¶å°å
   ï¼http://www.360doc.com/content/18/0801/00/2990557_774796873.shtmlï¼ä¾å±å
   å­¦ä¹ pythonçåå­¦é£ç¨ï¼ è¥ä¾µæï¼èç³»å é¤ 7æ16æ¥æ´æ°ï¼ Pythonç¬åèµ·ç¹ä¸­æç½
   å°è¯´æè¡æ¦ä¿¡æ¯ï¼ä¸æµ·çº¿ä¸å¹è®­ä½ä¸ï¼ å¯ä¸å°ç¼çå¤§...
   [71]pythonç¾åº¦è´´å§ç»å½åè®®_pythonç¬è«è§£å³ç¾åº¦è´´å§ç»ééªè¯ç é®é¢
   [72]weixin_39974223çåå®¢
   12-03 166
   [73]ä½ä¸ºè´´å§éåº¦ç¨æ·ï¼åäºä¸ªè´´å§ç¬è«èæ¬æäºä¸äºå«äººçä»£ç ãè®°å¾æä¸ªéªè¯ç 
   è§£å³çãå¯æ¯å¿äºé¾æ¥äºï¼ä»å¤©æç»èªå·±æ»åäºãé¦åè¦è®©ç»éé¡»è¦éªè¯ç ï¼ä¸åå°
   ç»éå°±å¥½äºãããåº¦å¨éå¸¸å¿«ä¼å ä¸éªè¯ç å¤§æ³çãããé¡»è¦éªè¯ç çæåµä¸ï¼ç´æ¥
   ç»éè¿åçéè¯¯ä¿¡æ¯æ¯error=257æå¼è´´å§é¦é¡µéæ©ç»éï¼å¼¹åºéªè¯ç ï¼æ¾å°éªè¯ç 
   çé¾æ¥æ¯ å³é®å¨æ°æ ç­¾é¡µä¸­æå¼ æ³¨æå°é¾æ¥æ¯è¿ä¸ªæ¶åä¾æ®ä¹ååçä»£ç ï¼å¤å®ç»
   éæåæ¯ä¾æ®postç»å½...
   [74]pythonè´´å§-qpythonè´´å§
   [75]q6q6qçä¸æ 
   10-28 250
   [76]å¹¿åå³é­è¾è®¯äºå11çåæåäº«ï¼ç²¾éç­é¨äº§åå©åä¸äºï¼äºæå¡å¨é¦å¹´88åèµ·
   ï¼ä¹°çè¶å¤è¿çè¶å¤ï¼æé«æ»¡è¿5000åï¼ç®å½1. urlçç»æ 2. è´´å§ç¬è«2.1. åªç¬
   è´´å§ç¬¬ä¸é¡µ2.2. ç¬åææè´´å§çé¡µé¢ 3. getåpostçåºå«3.1. getè¯·æ±3.2. post
   è¯·æ±3.3. æéç¿»è¯æ¨¡æåépostè¯·æ±...wd=%e7%bc%96%e7%a8%8b%e5%90%a7æä»¬ä¹å¯
   ä»¥å¨pyth...
   [77]ç¾åº¦è´´å§æ°ç©æ³ä½ ä¼ç¨åï¼
   [78]å¼ ä¸å»
   08-19 161
   [79]å¤§å®¶å¥½ï¼ææ¯å¼ ä¸å»ï¼ä¸æ³¨äºè¥éå¤å¹´ ä»å¤©æä»¬æ¥èèè´´å§è¥éï¼å¯è½å¨å¾å¤
   äººå¿é è´´å§å·²ç»è½ä¼äºï¼è´´å§è¥éä¸è¢«å¤§å®¶çå¥½ï¼ä½è¿è¿æ¯ä¸ç§æ¸ éï¼ä¸èªå·±è¯è¯
   æè½è½»æå¦å®å¢ï¼ æè¿ææ­£å¥½å¨ç ç©¶å¦ä½ä»è´´å§å¯¼ç¨æ·å°å¾®ä¿¡å¬ä¼å·ä¸ï¼åäº«ä¸ä¸
   å¿å¾ï¼å¸æå¯¹ä½ æå¸®å©ï¼ 1ãç¨äºç»´ç åå¤´å2ãå°äºç»´ç åæç­¾åå¾çï¼æ³¨åæ»¡3ä¸ª
   ææè½è®¾ç½®ç­¾åæ¡£ï¼ 3ãä¸ªäººç®ä»éæ·»å å¾®ä¿¡å· 4ãåæç« ï¼æ­£æä¸­å«åçåãå³é®
   è¯åå¾®ä¿¡å·ï¼æ é¢å«åçå³é®...
   [80]ãHTTPãç¾åº¦è´´å§WEBçç­¾å°æµç¨åæ
   [81]å¤§ä¸çåå®¢
   01-03 542
   [82]æç« ç®å½æµç¨å¾æ¥å£æåä¸åæè·åäºç»´ç è½®è¯¢æ«ç ç»æè·åCookieè·åå³æ³¨ç
   å§è´´å§ç­¾å°æ»ç» æµç¨å¾ æ¥å£æåä¸åæ è·åäºç»´ç  Url
   ï¼https://passport.baidu.com/v2/api/getqrcode è¯·æ±æ¹å¼ï¼Get è¯·æ±åæ°
   ï¼lp=pc è½ç¶æååç°æå¾å¤åæ°ï¼ä½æ¯ç»è¿å®éæµè¯åç°åªéè¦ä¼ lpè¿ä¸ä¸ªå°±å¯ä»¥
   äºï¼åç»­æ¥å£ä¸ååè¯´æ è¿åç»æï¼ { âimgurlâ:...
   [83]è´´å§äºç»´ç å¾ç§å å¤ç
   [84]å°è¡å®æå¼æµ
   11-07 2898
   [85]ä»å¤©åå¤§å®¶åäº«çæ¯è¿å å¤©æ ææµè¡ ç®åç åäºç»´ç  è¿èè¯¾ä¸æ¯ä¾§éå®æï¼
   å¦æå¤§å®¶çè¿æä»¥åçè§é¢ï¼è¿ä¸ªå°±å¾å¥½åäº æä»¬æ¥çä¸ä¸ ï¼æè¿åäºç»´ç æå¤ä¹
   çç
   https://tieba.baidu.com/f?ie=utf-8&kw=%E8%AF%9A%E6%8B%9B%E4%BB%A3%E7%90%86&fr=search
   å¤§å®¶å¯ä»¥çå°è¿é½æ¯ç´æ¥å°±åäºç»´ç å¾åºæ¬ä¸é½ä¸å¤ç...
   [86]è´´å§ä¸åäºç»´ç å°±è¢«å ï¼æ¯ä½ æ²¡ææ¡ææ¯
   [87]æç©ºè½¯ä»¶
   03-07 5039
   [88]è´´å§é²å å¾å¶ä½ï¼å¨å©ç¨ç¾åº¦è´´å§åæ¨å¹¿å¼æµçå°ä¼ä¼´ä»¬ï¼ä½ ä»¬æ¯ä¸æ¯ä¼éå°è¿
   æ ·çä¸ä¸ªæåµï¼èªå·±åçå¾çææ¶åè¢«åº¦å¨ç»ç§å äºï¼ä¸ºä»ä¹ä¼è¿æ ·å¢ï¼ä»å¤©èªææ
   å°ç¼å°±æ¥ä¸ºä½ åäº«ä¸ç¾åº¦è´´å§åå¾ççææ¯å¹²è´§ï¼å°æ¿å³å¯è¦åå¥½äºï¼ è¢«åº¦å¨ç§å 
   çå¸å­å¤å°è·èªå·±è´¦å·ä¹æä¸å®çå³ç³»ï¼å³äºè´¦å·çé®é¢ï¼ä¸ææä»¬ä¼å¨æçcsdnè´¦
   å·éé¢å¨åäº«ãç¾åº¦è´´å§å¦ä½åå¸ï¼è´´å§åå¸é²å æå·§å¹²è´§åäº«ï¼ãï¼æ­¤å¤å°±ä¸å¨èµ
   è¿°äºãè¿æä¸ç§åå å°±æ¯å¾çç...
   [89]Golang ç¾åº¦äºæ«ç ç»å½
   [90]ALakersçåå®¢
   12-24 262
   [91]æä»¶ç»æï¼ http_client.goä»£ç å¦ä¸ï¼ package client import ( "bytes"
   "fmt" "io" "io/ioutil" "net/http" "net/http/cookiejar" "net/url" "strings"
   "time" ) // HTTPClient http client type HTTPClient struct { *http.Client
   UserAgent string } var ( UserAgen
   [92]1.ç¬è«åºç¡ââäºè§£html&ä»ä¹æ¯ç¬è«
   [93]pythonä¼ç¸å­çåå®¢
   10-10 3141
   [94]ä¼æå¨ç¥ï¼æä»¬ä¸ç½æµè§çç½é¡µï¼ä»ä»¬çæ¬è´¨æ¯ä¸ä¸ªåä¸ä¸ªhtmlé¡µé¢ãé£ä»ä¹
   æ¯htmlå¢ï¼å¯ä»¥è¿ä¹çè§£ï¼ç¼åJAVAæJAVAçè¯­è¨é»è¾ï¼ç¼åPythonæPythonçè¯­è¨
   é»è¾ï¼ç¼åç½é¡µå°±éè¦éµä»htmlçè¯­è¨é»è¾ï¼èç¼åå¥½äºçhtmlå°±å¯ä»¥æ¾ç¤ºåºæ¥æä»¬
   æçå°çç½é¡µäºã å¦ä¸ç¤ºä¾ï¼ å¾1 å¾2 æ­£å¦æä»¬å¨ä¸é¢æçå°çï¼å½æä»¬æ¥
   çhttps://www.baidu.com/è¿ä¸ªç½åçæ¶åï¼...
   [95]å­¦ä¼è¿æï¼å°å§å§çä½ çç¼ç¥å°ä¸ä¸æ ·
   ç­é¨æ¨è
   [96]kimolåçåå®¢
   10-03 2ä¸+
   [97]å­¦ä¼è¿æï¼å°å§å§çä½ çç¼ç¥å°ä¸ä¸æ ·åè¨ä¸ãç¬è«åæäºãç¬åé¡¹ç®ID1.æå
   å¸å­çURL2.æåå¸å­ä¸­çUUID3.å®æ´ä»£ç ä¸ãç¬åé¡¹ç®çæ°æ®åå¨æå åè¨ ä»å¤©
   æå°ä¸½åå­¦æ¥æ¾æï¼æä¸ªå®éªéè¦ç¨å°è½»æ¾ç­¹çæ°æ®è¿è¡ä¸ä¸ªåæãå¯æ¯æ²¡æè¶³å¤ç
   æ°æ®ï¼å¦ä½åæ¯å¥½ï¼ ä¹äºå©äººçæï¼å½ç¶ä¸ä¼ç½®ä¹ä¸ç~ ï¼ps.æ¯ç«æ¯å°å§å§åï¼æ
   ç»äºä¸å¥½ï¼å¯¹å­ï¼ äºæ¯ä¹ï¼ææèµ·å®¶ä¼ï¼è¯´å¹²å°±å¹²ã ä¸ãç¬è«åæ éè¿ç®åçå
   æï¼å¯ä»¥åç°è½»æ¾ç­¹æä¾äºä¸ä¸ªæ¥å£ï¼å¯ä»¥è¿åæä¸ªé¡¹ç®çç¸å³æ°æ®ï¼å·ä½å¦ä¸ï¼
   å°åå¦ä¸ï¼xxxxxxè¡¨ç¤ºé¡¹ç®çUUIDï¼ h
   Â©ï¸2021 CSDN ç®è¤ä¸»é¢: æ¸¸å¨-ç½ è®¾è®¡å¸:ç½æ¾æ [98]è¿åé¦é¡µ
   [99][IMG]
   [100]lxguang_tao  CSDNè®¤è¯åå®¢ä¸å®¶ CSDNè®¤è¯ä¼ä¸åå®¢
   ç é¾7å¹´ [101][IMG] [102]ææ è®¤è¯

   3
   åå

   27ä¸+
   å¨æå

   25ä¸+
   æ»æå

   2242
   è®¿é®

   [103][IMG]
   ç­çº§

   44
   ç§¯å

   14
   ç²ä¸

   6
   è·èµ

   1
   è¯è®º

   7
   æ¶è
   [104]GitHub
   [105]ç­¾å°è¾¾äºº
   [106]æ°ç§åç« 
   [107]å¤åæ åµLv1
   [108]åäº«å­¦å¾
   [109]ç§ä¿¡
   å³æ³¨
   [110]_____________________

  ç­é¨æç« 

     â¢Â [111]ç¾åº¦è´´å§äºç»´ç ç»å½--pythonç¬è« [112][IMG] [113]539
     â¢Â [114]C# å¼ç¨åvisual studioä¸æ¥éï¼çææ¥é [115][IMG] [116]122
     â¢Â [117]windowsç³»ç»ä¸ä½¿ç¨dockerè¿è¡å®¹å¨æè½½å·æ¥éé®é¢ [118][IMG] [119]69

  åç±»ä¸æ 

     â¢Â [120][IMG] [121]python 1ç¯
     â¢Â [122][IMG] [123]C# 1ç¯

  ææ°è¯è®º

     â¢Â [124]ç¾åº¦è´´å§äºç»´ç ç»å½--pythonç¬è«

       [125]ä¹ä½ : ä»£ç ä¹è·¯ä»»ééè¿ï¼æ¿è·åä¸»åªåä¹ ä¹ã

  æ¨æ¿æåæåæ¨èâåå®¢è¯¦æé¡µâåï¼

     â¢Â 
       å¼ºçä¸æ¨è
     â¢Â 
       ä¸æ¨è
     â¢Â 
       ä¸è¬è¬
     â¢Â 
       æ¨è
     â¢Â 
       å¼ºçæ¨è

   [126]_____________________ æäº¤

  ææ°æç« 

     â¢Â [127]windowsç³»ç»ä¸ä½¿ç¨dockerè¿è¡å®¹å¨æè½½å·æ¥éé®é¢
     â¢Â [128]C# å¼ç¨åvisual studioä¸æ¥éï¼çææ¥é

   [129]2021å¹´2ç¯
   [130]2020å¹´1ç¯

   [131]IFrame

  ç®å½

  ç®å½

   [132]IFrame

  åç±»ä¸æ 

     â¢Â [133][IMG] [134]python 1ç¯
     â¢Â [135][IMG] [136]C# 1ç¯

   å®ä»å
   [137]ä½¿ç¨ä½é¢æ¯ä»
   ç¹å»éæ°è·å
   æ«ç æ¯ä»
   [138](Â ) é±åä½é¢ 0

   æµæ£è¯´æï¼

   1.ä½é¢æ¯é±ååå¼çèæè´§å¸ï¼æç§1:1çæ¯ä¾è¿è¡æ¯ä»éé¢çæµæ£ã
   2.ä½é¢æ æ³ç´æ¥è´­ä¹°ä¸è½½ï¼å¯ä»¥è´­ä¹°VIPãCå¸å¥é¤ãä»è´¹ä¸æ åè¯¾ç¨ã

   [139][IMG][140]ä½é¢åå¼

References

   Visible links
   1. https://blog.csdn.net/qq_27644127/article/details/112987332
   2. file:///data/data/com.termux/files/home/works/tieba_job/content.html#
   3. https://blog.csdn.net/qq_27644127
   4. https://blog.csdn.net/qq_27644127/category_10614803.html
   5. https://so.csdn.net/so/search/s.do?q=python&t=blog&o=vip&s=&l=&f=&viparticle=
   6. http://creativecommons.org/licenses/by-sa/4.0/
   7. https://blog.csdn.net/qq_27644127/article/details/112987332
   8. https://blog.csdn.net/qq_27644127/category_10614803.html
   9. python
	https://blog.csdn.net/qq_27644127/category_10614803.html
  10. file:///data/data/com.termux/files/home/works/tieba_job/content.html#_1
  11. file:///data/data/com.termux/files/home/works/tieba_job/content.html#_5
  12. file:///data/data/com.termux/files/home/works/tieba_job/content.html#_37
  13. file:///data/data/com.termux/files/home/works/tieba_job/content.html#_39
  14. file:///data/data/com.termux/files/home/works/tieba_job/content.html#_40
  15. file:///data/data/com.termux/files/home/works/tieba_job/content.html#_42
  16. file:///data/data/com.termux/files/home/works/tieba_job/content.html#_192
  25. http://file.taotaoya.top/load/TT.rar
  28. https://blog.csdn.net/qq_27644127
  29. https://blog.csdn.net/qq_27644127
  30. javascript:;
  31. file:///data/data/com.termux/files/home/works/tieba_job/content.html#commentBox
  32. file:///data/data/com.termux/files/home/works/tieba_job/content.html#commentBox
  33. javascript:;
  34. javascript:;
  35. javascript:;
  36. javascript:;
  37. javascript:;
  38. javascript:;
  39. https://download.csdn.net/download/weixin_42122432/18441287
  40. https://download.csdn.net/download/weixin_42122432/18441287
  41. https://blog.csdn.net/weixin_34236869/article/details/86453208
  42. https://blog.csdn.net/weixin_34236869
  43. https://blog.csdn.net/weixin_34236869/article/details/86453208
  44. javascript:void(0);
  50. https://lmsoft.blog.csdn.net/article/details/84582372
  51. https://blog.csdn.net/qq_41287993
  52. https://lmsoft.blog.csdn.net/article/details/84582372
  53. https://smartcrane.blog.csdn.net/article/details/121341944
  54. https://blog.csdn.net/wenxuhonghe
  55. https://smartcrane.blog.csdn.net/article/details/121341944
  56. https://blog.csdn.net/ljc545w/article/details/111054624
  57. https://blog.csdn.net/ljc545w
  58. https://blog.csdn.net/ljc545w/article/details/111054624
  59. https://blog.csdn.net/kaerbuka/article/details/94471507
  60. https://blog.csdn.net/kaerbuka
  61. https://blog.csdn.net/kaerbuka/article/details/94471507
  62. https://blog.csdn.net/cxcjoker7894/article/details/85685115
  63. https://blog.csdn.net/cxcjoker7894
  64. https://blog.csdn.net/cxcjoker7894/article/details/85685115
  65. https://cpython.blog.csdn.net/article/details/109063267
  66. https://blog.csdn.net/bigzql
  67. https://cpython.blog.csdn.net/article/details/109063267
  68. https://blog.csdn.net/qq_32670879/article/details/101391892
  69. https://blog.csdn.net/qq_32670879
  70. https://blog.csdn.net/qq_32670879/article/details/101391892
  71. https://blog.csdn.net/weixin_39974223/article/details/110545065
  72. https://blog.csdn.net/weixin_39974223
  73. https://blog.csdn.net/weixin_39974223/article/details/110545065
  74. https://blog.csdn.net/q6q6q/article/details/109346811
  75. https://blog.csdn.net/q6q6q
  76. https://blog.csdn.net/q6q6q/article/details/109346811
  77. https://blog.csdn.net/u013177154/article/details/99288349
  78. https://blog.csdn.net/u013177154
  79. https://blog.csdn.net/u013177154/article/details/99288349
  80. https://blog.csdn.net/d745282469/article/details/103819585
  81. https://blog.csdn.net/d745282469
  82. https://blog.csdn.net/d745282469/article/details/103819585
  83. https://blog.csdn.net/weixin_44027887/article/details/102948182
  84. https://blog.csdn.net/weixin_44027887
  85. https://blog.csdn.net/weixin_44027887/article/details/102948182
  86. https://blog.csdn.net/qq_15159657/article/details/104721232
  87. https://blog.csdn.net/qq_15159657
  88. https://blog.csdn.net/qq_15159657/article/details/104721232
  89. https://blog.csdn.net/ALakers/article/details/111619137
  90. https://blog.csdn.net/ALakers
  91. https://blog.csdn.net/ALakers/article/details/111619137
  92. https://blog.csdn.net/weixin_42830697/article/details/102474659
  93. https://blog.csdn.net/weixin_42830697
  94. https://blog.csdn.net/weixin_42830697/article/details/102474659
  95. https://blog.csdn.net/kimol_justdo/article/details/108912073
  96. https://blog.csdn.net/kimol_justdo
  97. https://blog.csdn.net/kimol_justdo/article/details/108912073
  98. https://blog.csdn.net/
  99. https://blog.csdn.net/qq_27644127
 100. lxguang_tao
	https://blog.csdn.net/qq_27644127
 101. https://i.csdn.net/#/uc/profile?utm_source=14998968
 102. ææ è®¤è¯
	https://i.csdn.net/#/uc/profile?utm_source=14998968
 103. https://blog.csdn.net/blogdevteam/article/details/103478461
 109. https://im.csdn.net/chat/qq_27644127
 111. https://blog.csdn.net/qq_27644127/article/details/112987332
 112. https://blog.csdn.net/qq_27644127/article/details/112987332
 113. https://blog.csdn.net/qq_27644127/article/details/112987332
 114. https://blog.csdn.net/qq_27644127/article/details/111566657
 115. https://blog.csdn.net/qq_27644127/article/details/111566657
 116. https://blog.csdn.net/qq_27644127/article/details/111566657
 117. https://blog.csdn.net/qq_27644127/article/details/118380655
 118. https://blog.csdn.net/qq_27644127/article/details/118380655
 119. https://blog.csdn.net/qq_27644127/article/details/118380655
 120. https://blog.csdn.net/qq_27644127/category_10614803.html
 121. https://blog.csdn.net/qq_27644127/category_10614803.html
 122. https://blog.csdn.net/qq_27644127/category_10685120.html
 123. https://blog.csdn.net/qq_27644127/category_10685120.html
 124. https://blog.csdn.net/qq_27644127/article/details/112987332#comments_14757654
 125. https://blog.csdn.net/m0_50944918
 127. https://blog.csdn.net/qq_27644127/article/details/118380655
 128. https://blog.csdn.net/qq_27644127/article/details/111566657
 129. https://blog.csdn.net/qq_27644127/article/month/2021/07
 130. https://blog.csdn.net/qq_27644127/article/month/2020/12
 131. https://kunpeng-sc.csdnimg.cn/?timestamp=1623163941/#/preview/8608?positionId=57&queryWord=&spm=1001.2101.3001.5001
 132. https://kunpeng-sc.csdnimg.cn/?timestamp=1623163941/#/preview/8608?positionId=479&queryWord=&spm=1001.2101.3001.4834
 133. https://blog.csdn.net/qq_27644127/category_10614803.html
 134. https://blog.csdn.net/qq_27644127/category_10614803.html
 135. https://blog.csdn.net/qq_27644127/category_10685120.html
 136. https://blog.csdn.net/qq_27644127/category_10685120.html
 137. javascript:;
 139. https://i.csdn.net/#/wallet/balance/recharge
 140. https://i.csdn.net/#/wallet/balance/recharge![Image](./187fd2da45fcb4448f060830c830f812.png)![Image](./187fd2da45fcb4448f060830c830f812.png)
