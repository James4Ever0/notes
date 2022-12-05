---
tags: [botnet, crypto mining, hacking, tutorial, virus]
title: 'Hacking tutorials, tools'
created: '2022-07-11T15:43:20.000Z'
modified: '2022-12-05T07:55:14.681Z'
---

别动不动就想日站 收集信息 熟悉工具 做好能做到的 把一路学到的经验总结下来

[cryptographic related python libraries](https://blog.csdn.net/DARKNOTES/article/details/119154603) gmpy2 pycryptodome libnum yafu rsa-wiener-attack RsaCtfTool

[pwntools](https://github.com/Gallopsled/pwntools) used by fmyy and more [doc](http://pwntools.com/)

[angr](https://angr.io/) to reverse engineer binaries, mostly in ctf? [docs](https://docs.angr.io/advanced-topics)

angr ctf use cases: [case 1](https://blog.csdn.net/qq_44370676/article/details/119741664) [case 2](https://blog.csdn.net/u013648063/article/details/108685416)

[angr ctf reverse binaries and print "good job"](http://angr.oregonctf.org/)

[defcon ctf quals 2021 ooo](https://oooverflow.io/dc-ctf-2021-quals/)

[factordb.com](http://factordb.com/) find prime numbers, decomposition for rsa

[reverse shell generator](https://github.com/0dayCTF/reverse-shell-generator) while shellcode cannot have null bytes, you need to xor your things with tool or assembly.

挖0day 或者利用现成漏洞 [fuzzers for kali](https://en.kali.tools/all/?category=fuzzer)

[kali tools](https://www.kali.org/tools/)

[blackarch tools](https://www.blackarch.org/tools.html)

[all in one hacking tool](https://github.com/Z4nzu/hackingtool)

[villainbackdoorgenerator](https://github.com/t3l3machus/Villain)

don't aim big, aim small. things like bilibili password database dump, or some Intel internal data leak, are done by professional hackers on professional hardware. some corp will even attempt to retaliate like nvidia. you have been warned.

To exploit zerodays, you need [rasp](https://rasp.baidu.com), aka 'is my application doing something undefined/unexpected?'

利用公共WiFi 比如用WiFi炮连接远处的WiFi 控制云端的攻击服务器

黑客第一步是找目标 （CTF可能不会教你怎么找目标  白帽也不会 因为目标很单一）不管漏洞存不存在 目标究竟是个啥目标 是人（联系方式？）还是机器（URL？）还是AI （验证码？）怎么交互（可能）是什么漏洞 以及采取什么攻击措施 都得先把目标罗列清楚 可以借助搜索引擎 fofa漏洞搜索 邮箱信息 社交软件的信息 木马跟踪他人的信息 大多数人访问的信息 爬虫信息 监控本地软件访问网络的记录 或者直接随便扫描 存到数据库里面

第二步就是交互 利用漏洞 装后门 控制目标 比如挖矿 继续收集网站信息 密码信息 cookies 继续散播病毒 拓展攻击面

第三步持久作战 持续提高反侦查意识 学习收集信息工具 提高黑客能力 利用各种方法 比如社会工程学 利用匿名账号或者免费邮箱账号 传播带木马的免费应用程序 病毒邮件 坚持就是胜利

https://github.com/mikaelkall/HackingAllTheThings

https://github.com/akenofu/HackAllTheThings

memory editing, game hacking:

https://github.com/qb-0/pyMeow

https://github.com/srounet/Pymem

[mirai botnet](https://github.com/aleixrodriala/Mirai-Source-Code)

[defcon](https://defcon.org) for news, intro, wiki

[infocon](https://infocon.org) for software, code, wordlists

[mec](https://github.com/jm33-m0/mec) mass exploiting

## notes

[pc微信hook 获取二维码](https://blog.csdn.net/a1165559068/article/details/110450166?app_version=5.9.0&code=app_1562916241&csdn_share_tail=%7B%22type%22%3A%22blog%22%2C%22rType%22%3A%22article%22%2C%22rId%22%3A%22110450166%22%2C%22source%22%3A%22a1165559068%22%7D&uLinkId=usr1mkqgl919blen&utm_source=app)

[pc微信逆向](https://note.youdao.com/s/KRl8DIR0)

几个觉得还不错的靶场

封神台：https://hack.zkaq.cn/index

Hack The Box ：https://www.hackthebox.com/

htb邀请码获取方法：https://www.mad-coding.cn/2019/11/11/hackthebox%E5%88%9D%E6%8E%A2%E4%B9%8B%E8%8E%B7%E5%8F%96%E9%82%80%E8%AF%B7%E7%A0%81/#0x00-%E5%89%8D%E8%A8%80

Vulhub：https://www.vulnhub.com/

Pikachu：https://github.com/zhuifengshaonianhanlu/pikachu

## search engines

[youcode](https://you.com/code) search engine for coders, enter coding question to get result

self-hosted recon intelligence tool: [osint](https://github.com/lockfale/osint-framework)

[ivre](https://github.com/ivre/ivre) network recon framework

[publicwww: search for html/css/js source code in website](https://publicwww.com/)

[searchpedia: search engine collection](https://hackernoon.com/searchpedia-a-list-of-250-search-engines-40198146adfc)

[top 5 recon/intelligence/information gathering tools](https://resources.infosecinstitute.com/topic/top-five-open-source-intelligence-osint-tools/)

[search engine hacking, manual and automation](https://resources.infosecinstitute.com/topic/search-engine-hacking-manual-and-automation/)

[best hacker search engines](https://dekisoft.com/best-hacker-search-engines-to-use/)

## scripting

[writing nmap scripts](https://www.cnblogs.com/bhlsheji/p/5175516.html)

## information gathering

[uncover](https://github.com/projectdiscovery/uncover) quickly discover hosts using multiple search engines

[dirsearch](https://github.com/maurosoria/dirsearch) scan web paths

```bash
pip3 install dirsearch
```

## virus, botnet

[botnet with super escalation system for linux and windows, automatically spread the virus out](https://github.com/ThrillQuks/Pitraix)

[webshell 免杀](https://zu1k.com/posts/security/web-security/hide-your-webshell/)

## Hacking tutorials

maybe you should follow kali/parrot/blackarch tutorials first?

暗网 社工库 数据库 暗网黑客教学

暗网自由社区，中文社区，无下限讨论
zuw2gvomnfx5mt6g626srambeqo2yxmac5jpoccttq54z7se36svmlyd.onion

the payload, dedicated tutorial
https://github.com/swisskyrepo/PayloadsAllTheThings

sure it needs everything to hack. the assembly, the tools, the experience, the examples, the automation, the persistence, the vision.

all in one hack tool:
https://github.com/Z4nzu/hackingtool

awesome hacking:
https://github.com/Hack-with-Github/Awesome-Hacking

hacking tutorials and tools:
https://github.com/carpedm20/awesome-hacking
https://github.com/sundowndev/hacker-roadmap
https://github.com/jekil/awesome-hacking
https://github.com/carlospolop/hacktrick

ctf tutorials and tools:
https://github.com/xtiankisutsa/awesome-mobile-CTF
https://github.com/Naetw/CTF-pwn-tips
https://github.com/firmianay/CTF-All-In-One
https://github.com/taviso/ctftool
https://github.com/UnaPibaGeek/ctfr
https://github.com/RsaCtfTool/RsaCtfTool
https://github.com/Gallopsled/pwntools
https://github.com/0Chencc/CTFCrackTools
https://github.com/google/google-ctf
https://github.com/ctf-wiki/ctf-wiki
https://github.com/apsdehal/awesome-ctf
https://github.com/p4-team/ctf
https://github.com/zardus/ctf-tools

some other tools and resources

https://github.com/jopohl/urh

https://github.com/sundowndev/hacker-roadmap

[all in one hacking tool](https://github.com/Z4nzu/hackingtool) for kali linux

https://github.com/edoardottt/awesome-hacker-search-engines

[hacker pro](https://github.com/jaykali/hackerpro) hacktool for termux and linux, maybe macos?

[sql/xxs scanner, dos, bruteforce ftp/ssh/mail accounts](https://github.com/b3-v3r/Hunner)

https://github.com/hacktoolspack/hack-tools

https://github.com/hahwul/WebHackersWeapons

https://github.com/jekil/awesome-hacking
