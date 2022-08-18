---
tags: [circumvention, clash, github, network]
title: Clash route only github related domains to fastgithub
created: '2022-07-27T16:45:37.000Z'
modified: '2022-08-18T14:14:03.317Z'
---

# Clash route only github related domains to fastgithub

## DNS

use clash official DNS settings to resolve issues related to domain resolution, especially when used as a system proxy.

[documentation](https://github.com/Dreamacro/clash/wiki/configuration#dns)

to persist program using platform-specific service manager like nssm on windows:

## macos

use launchctl(launchd) or easyd

## linux

create systemd
need to change system wide proxy settings in init files

or use [monit](https://mmonit.com/monit/documentation/monit.html), with control over the service itself.

or shell script alike [linuxNSSM](https://github.com/guolisongIsesol/linuxNssm)
