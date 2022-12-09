---
title: 'add certificate to termux, especially for fastgithub'
created: '2022-12-09T18:55:52.063Z'
modified: '2022-12-09T18:55:53.970Z'
---

# add certificate to termux, especially for fastgithub
 
install `openssl-tools` then use `add-trusted-certificate` against the `.crt` file, so curl will work fine (still not for elinks, i wonder why that works on macos and linux, or maybe not? just use playwright instead.)
 
chromebook is different. you need to export the proxy to `0.0.0.0` by means of nginx or something, so you can configure proxy to `100.115.92.14` or `100.115.92.2` as seen in termux by `ifconfig`
