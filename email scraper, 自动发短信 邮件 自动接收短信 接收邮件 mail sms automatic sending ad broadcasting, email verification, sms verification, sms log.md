---
tags: [advertising, mail sending, SMS]
title: email scraper, 自动发短信 邮件 自动接收短信 接收邮件 mail sms automatic sending ad broadcasting, email verification, sms verification, sms login, email login, temp mail, email OSINT
created: 2022-07-04T12:47:02+00:00
modified: 2023-01-19T22:00:33+08:00
---

# email scraper, 自动发短信 邮件 自动接收短信 接收邮件 mail sms automatic sending ad broadcasting, email verification, sms verification, sms login, email login, temp mail, email OSINT

## email

### email OSINT

OSINT/recon 其实就是社工 但是一般人喜欢把社工库和社工分开 因为社工库是社工收集来的数据集合 而社工则是一个过程

loading/transforming leaked txt files will be time-consuming. use pypy to speedup the process. use database specific batch processing method to import the data.

[entity fragmentation in followthmoney](https://followthemoney.readthedocs.io/en/latest/fragments.html) is kind of for "entity recognition in multiple social platforms", suitable for finding patterns/clients in large leaked databases.

#### email collector

[socialscan](https://github.com/iojw/socialscan) Python library for accurately querying username and email usage on online platforms

[Zen](https://github.com/s0md3v/Zen) collect email on github

[maigret](https://github.com/soxoj/maigret) a powerful fork of [sherlock](https://github.com/sherlock-project/sherlock) (customizable, finding accounts by username, but only [having 300+ sites](https://github.com/sherlock-project/sherlock/blob/master/sites.md) ) with 2000+ sites

[emailAll](https://github.com/Taonn/EmailAll) collect email by passing domain

[emailfinder](https://github.com/Josue87/EmailFinder) find email by domain

[theHarvestor](https://github.com/laramies/theHarvester) email, subdomain and names collector

[gitscan](https://github.com/sea-god/gitscan/blob/master/gitscan.py) scan for email and password (if possible) with predefined domains and rules by searching github

[ghunt](https://github.com/mxrch/ghunt) needs companion browser plugin to get credentials. can collect info on given email

[EMAGNET](https://github.com/wuseman/EMAGNET) collect database leaks, email and password from recent pastebin records

#### leaked email and data

occrp (anti corruption & crime) aleph is a bad source for getting email (anonymous/unauthorized user can only get hundreds, having no clue what the email relates to). however, it has a tool called [follow the money](https://followthemoney.readthedocs.io/) which works with csv files and exports cypher to neo4j

##### leaks on github

search for leaked database on github

[linkedin database leak 2021](https://github.com/guptaofficial17/Linkedin-Leak-2021/blob/main/Leak/Leak.txt) (hate mega since it has download quota)

##### leaks from forums

you typically find links to these databases on `anonfiles.com` (or else), so query like `site:anonfiles.com email rar` in duckduckgo (no DMCA censorship)

[breachedforum's index](https://breached.vc/Announcement-Database-Index) contains "credits only" threads which requires 4-8 credits to unlock. to get credits you need to create thread (which will earn 0 credit) and get 1 credit per reply. post to trivial threads like manga.

in [leakbase](https://leakbase.cc/) you earn credits and download leaked databases easier. it has [official telegram bot](https://t.me/leakbase_official) claims to leak free databases everyday.

##### telegram bots

find telegram bots collection in [privacy.club](https://www.privacys.club/) (only OSINT bots) and [here](https://www.ff98sha.me/archives/147) (with many other bots)

[摆烂bot](https://t.me/bailansgbot) 永久免费

[SGKmainNEWbot](https://t.me/SGKmainNEWbot?start=IVT1073A377)

[sgkmainbot](https://t.me/sgkmainbot?start=IVT7FBE782B)

(gone?) [FreeSGKbot](https://t.me/FreeSGKbot?start=SGKETRAYJU)

[FreeSGKbot4](https://t.me/s/FreeSGKbot4?before=123)

[KernelBugXBot](https://t.me/KernelBugXBot)

##### download links

although i find many leaked databases as torrent, but those torrent search engines usually collect video/movies instead of anything related to leaked database.

[44.65GB QQ 微博社工库](http://4563.org/?p=201481) or [qq8e/qq](https://github.com/qq8e/qq) 基本上传的就是这个了 或许可以在QQ群里面找到一些别的社工库 使用这个数据库的还有 [q绑](http://qb.shegongk.com/) (有反调试 带去水印工具 但是其实这个到处都有吧) [aiuys's retrofit](https://privacy.aiuys.com/) 后台是[privacy](https://github.com/Chordp/privacy) (只是部分的可以导入 其他的自行处理)

Using aMule on macOS, Kad is firewalled (2.2.1 works well [said by people](http://bugs.amule.org/view.php?id=1368), but I'd not use macOS), reason unclear. Maybe on Linux or Windows it will be different.

Some (dead) links of other databases in ed2k emule format:
```
ed2k://|file|2010.06-江西移动全库-408万-access.7z|1329999527|5231E1EC5EE1123C6E694AD6399F9807|h=DORZC7XFNG63ZWX6C3RSN3Q7CWZXG5G4|/
ed2k://|file|2012.01-千脑-70万-csv.rar|34017079|A30DD3EF32C03C86E71032CDCA1C5EF9|h=2Z7TKJED7P2NJCKUCINNHMWLXV3KVVS4|/
ed2k://|file|2012.02-AcFun-15万-txt.rar|2241909|C2439FAB2BC7322273DE5D512A530A83|h=QJWQ3LWZ3UFJMPQHPD6WGXYYZHPRLQ43|/
ed2k://|file|2012.03-圆通数据库-mssql.rar|127496748|75F92807F541FB0EBB4773BA83D5157A|h=YAOCNQEUXCNBBTIM226NNZLJA7SMMSDS|/
ed2k://|file|2012.07-yahoo-45万-txt.bz2|6871089|8769EC2314C1AF2C98237DF58C7076D2|h=VSJ52KZ6O6JUZNZKXKT7F3LRXHBKJKMN|/
ed2k://|file|2012.08-小米论坛-828万-mysql.rar|518891223|87704FEA5B191C21F605A0C135BAF98E|h=6UQWS3OQ4VGUXLYW2L6H6TL2GKZOJAUA|/
ed2k://|file|2012.08-小米论坛-828万-txt.rar|361627120|2ED96D2F0E515321F67A31E84DC77B3C|h=UNNVFRMNWNP7UAIXZ6Y6AFCKOLBFJILW|/
ed2k://|file|2013.04-DNF-700万-mysql.zip|306178725|169CE4FA4D4F467BCB7F8297CE6EE032|h=C3KZ6C637ARBAPD5UNF2YMYMT5LTS2UK|/
ed2k://|file|2013.08-酒店开房记录-2000万-excel.rar|610164988|26F994CA1ABA72051ECE497F9AB7959A|h=EDLQDIHSRAJHB5SVNDQVMNPHOXVO3XB6|/
ed2k://|file|2013.08-酒店开房记录-2000万-mssql.bak|8030079488|6FCCDC6DE213DC72A4EFEE19AF2FC1AC|h=5YJSQJY46OYKYMQA5P4G3DUAQGATYDFI|/
ed2k://|file|2014.08-企业400号段数据-mssql.rar|46506453|4F44726413F3B9F9F701635FB498EAAB|h=LP47JMAJGOX233HQR2V3K673G7LE22RI|/
ed2k://|file|2014.08-台湾某财经电视台数据库-2014-txt.zip|53519|95160AAE4A9E3074BACB04C606C0748F|h=3KQJJ4ADWKNOGNJIZIICBXQ5SLPD62R5|/
ed2k://|file|2014.08-房产网-11万-sql.7z|6095432|D99DE175A27D179A5EB9F34D2D975FB0|h=2GN2RLDSDDVZ4POQZVIEJODQJVH2CJ4G|/
ed2k://|file|2014.09-mail.ru邮箱地址-466万-txt.7z|30715779|5247DC686608FD2317A31E8BA67899F4|h=DFVLYBFEQQLDZSXIEOWHWY2BMA5DKDBO|/
ed2k://|file|2014.09-yandex.ru-100万-txt.zip|16200283|80C4A344D51DBAE12F0A0D50202E9313|h=RA2KA6RRGELDAMXBAKXVFI3W7SIJ6TEE|/
ed2k://|file|2014.12-12306-13万-txt.7z|4470710|7B25F299C7862BFA855B63B04BB00E2A|h=VURCVAXE4UVFI2TOIEC6DIZUBSYELY76|/
ed2k://|file|2016.04-卡塔尔国家银行QNB-csv.zip|534384790|D7D81061307568AE47A3EE6C894D6C6C|h=VRQGQASTAHXFRGBZXAAIABVTFJRRIV7G|/
ed2k://|file|2016.04-土耳其公民数据mernis-5000万-sql.gz|1555520122|22B660CB494D89FC84198A6EEA66E3B6|h=HYBIW22P3G56CUB7RR34CJVD7RKO34BS|/
ed2k://|file|2011.03-多玩游戏网-800万-txt.rar|227441723|F8388A178222518978550D3E64B6129B|h=XMR2CYVQI3HOMKVRGUCCFGYZ3JVHKLCG|/
ed2k://|file|2011.03-当当网买家信息-101万-Excel.zip|7822098|1F66086AE57B74D69BF75A2EF7900B2E|h=VRWZME24KH7UTIF3HPTCO5V5KNTEHUAQ|/
ed2k://|file|2011.04-766游戏网-12万-sql.rar|5031951|BBE2D87564A2A8E4B083B57C697FD24E|h=DUFDLSY2A4F5SPZMMCN5JP7TE2HWA4EV|/
ed2k://|file|2011.04-IS语音-969万-txt.zip|177030850|B153DDF9FE16EFFF30C589664592F85A|h=HCB5NVNHVGVGKMDCS7HXHI4MNQASG5SY|/
ed2k://|file|2011.04-亚马逊中国买家信息-20万.zip|7570413|356D9E9C07D62243EF8A62745819E85C|h=BXLWB7OFKIFTCSCUU4Y47DHMX67GF7DO|/
ed2k://|file|2011.04-凡客诚品买家信息-20万-Excel.zip|7784030|AEC527EA7E816DBD75FF92B0C26BC480|h=VXC2RO23H23OCZISUXTEO62RTVHGQFPZ|/
ed2k://|file|2011.04-爱拍游戏网-1100万-txt.zip|267845795|87F9FFE887B0F53CAFD2A11205CB6C52|h=G6AQRSNJ7CHDTX5MTV6RYGB2OHYOAEXA|/
ed2k://|file|2011.05-木蚂蚁-13万-sql.zip|8598547|680F8999D4E27174553D1C11118DF978|h=5G2YZ7Z6RAQ5M5XUNCEFNX7ZYAITMZPZ|/
ed2k://|file|2011.07-土木在线-540万-sql.zip|645903048|4ED3B64224752DE3AB11B11D2FD9DA06|h=UL3F74NI266IR4IHI7UHDKMZRQMX3PFX|/
ed2k://|file|2011.10-178游戏网-1000万-txt.rar|108534783|FFCD04A52339701C8CB5197BDCF9F4DC|h=C2UYTR264YXVM6NSJNUV5R2PC5VZNAYU|/
ed2k://|file|2011.10-CSDN.NET-600万-sql.rar|109942505|A29D9468556CF73AFB48A3A8427629DC|h=VTPXT56G3BGRTHBROKQEWW6XAQTMYPLZ|/
ed2k://|file|2011.10-嘟嘟牛-66277-txt.rar|215666725|EF7187E33A8EBD9FD806343B7B1CAA82|h=Z5YU2Z6P6GUT5DUKQ6L4X5YFMZZNZ4YZ|/
ed2k://|file|2011.11-7k7k小游戏-2000万-txt.rar|203648704|6EB70910C1C193F5BE04610B503EF4A0|h=Y4ITT7C5Z5LOOREJPWXA25TM2NLKEEDX|/
ed2k://|file|2011.11-人人网-500万-txt.rar|51969611|8CD19B7A2EB9F1F74CB8BFBDE7BD144D|h=SDNOOZCYR6PXZIRZTZPEICNRNZ67BQJJ|/
ed2k://|file|2011.12-天涯社区-4000万-txt.rar|493480455|E4E0CFD85E2A783A3C3BD2539AA28FC3|h=4FB7J7QPRWRIPX7QWWTYVZCKMWDZ5VIQ|/
ed2k://|file|2011.12-淘宝买家卖家邮箱-2500万-txt.zip|135534861|F40C3C9F32F2C30B1A2484FAB3CB1257|h=GLUDUAAYPAALG3GPHD4EHT5OB6V6WBVB|/
ed2k://|file|2012.10-QQ精准客户名单-4500万-txt.rar|131416815|134F81AA90B27F55818E7A521D3CB35B|h=NRF2HAH2IXDT635UV6NDEGSA2HSOSSHZ|/
ed2k://|file|2012.06-LinkedIn-16737万-txt.rar|7503170474|A50C488915FC70E1DE644AA5F3432D6F|h=E2NEXLXOOA6PONPKUGVRVIMEU54EC6P4|/
ed2k://|file|2013.06-Myspace.com-36021万-txt.7z|12419587039|A1B14F88891885D636DE9F642A3E06DF|h=3QBXWEHRBUSUEWJOSHCF47B7HEC4Q5BM|/
```

#### check registration account with email

[reg007 counterpart](https://github.com/CreditTone/regchecker) only check if that account "exists", but no actual account shown. [search for reg007 on github](https://github.com/search?p=1&q=reg007.com&type=Code) you will get a bunch of links relating to OSINT.

[holehe](https://github.com/megadose/holehe) only check if an email address is registered as account elsewhere using "forget my password" APIs.

[sreg](https://github.com/n0tr00t/Sreg) is found from a collection of [security tools](https://github.com/jay900323/securitytools), which is a deprecated tool for getting registration status with phone/email/username on multiple chinese platforms.

#### (email) account verifier

Usually it only verify existance of given email, like [emailhippo](https://tools.verifyemailaddress.io/) (100 requests free per day per ip), or [mailforguess](https://github.com/WildSiphon/Mailfoguess) checking "gmail","laposte","protonmail","yahoo" emails

Some of them verify email with password: [verify email address and password with API of my.com](https://github.com/MachineKillin/Email-Account-Generator-Checker/blob/main/main.py)

[h8mail](https://github.com/khast3x/h8mail) email osint tool, can chase and link to social profile, with many API-key required free services

[mosint](https://github.com/alpkeskin/mosint) automated email osint tool, requires many API keys.

[ignorant](https://github.com/megadose/ignorant) checks if a phone number is used for snapchat/instagram

### email connectors/client

[proton mail unofficial client in python](https://github.com/ShellCode33/ProtonMail)

### email registration

#### [yandexmail account creator](https://github.com/hendrikbgr/YandexMail-Account-Creator)

before it was using 2captcha, now using [5sim](https://5sim.net/) to receive sms

only login such account through pop3 and imap to prevent revocation

#### [outlook email generator](https://github.com/MatrixTM/OutlookGen)

using 2captcha and anycaptcha for captcha solving (paid)

#### [protonmail email generator](https://github.com/baum1810/protonmail-generator)

using noptcha or [nopecha](https://nopecha.com/) browser extension (free for 100 captcha solves per day) solving hcaptcha, recaptcha. this extension cannot be used with proxy.

#### [muumuu (which reminds me of someone) email registration using 2captcha, selenium and pyautogui](https://github.com/KenshiroSugiyama/automation_email_create/blob/main/create.py)

I place the list under `/root/.muumuu_emails`

the [muumuu mail](https://muumuu-mail.com/) is programmatically connectable using account and password. seems it is using default ports for these services. [POP3](pop3.muumuu-mail.com) is for both sending and receiving. [IMAP](imap4.muumuu-mail.com) is for receiving. [SMTP](smtp.muumuu-mail.com) is for sending.

this guy's code is full of hacks. seems only being able to run on his own computer and will break on slightest errors.

he stored potential password combinations and also registered accounts (need testing, some may not work) on [this google doc](https://docs.google.com/spreadsheets/d/1GPpVKAA1okFjpifE494Ax4laHYQ5XaMvIZ6CQByPD_Y/edit#gid=0). you can download the sheet named "Sheet1" by [this api](https://docs.google.com/spreadsheets/d/1GPpVKAA1okFjpifE494Ax4laHYQ5XaMvIZ6CQByPD_Y/gviz/tq?tqx=out:csv&sheet=Sheet1), which adds double quotes and takes more space than exported from web interfaces, method described [here](https://chewett.co.uk/blog/2445/how-to-use-an-api-to-download-a-google-docs-sheets-spreadsheet-as-csv/).

### receiving-only email services

#### temp email

[tempumail](https://tempumail.com/mailbox) get free temp edu email

#### [erine.email](https://erine.email)

email proxy for resending email to you, which I used for github registration (but with a very high block rate without proxy)

### email aliasing for sending

icloud's "hide my email" service seems only provide few email aliases. but according to [3rd party icloud alias generator](https://github.com/rtunazzz/hidemyemail-generator) (cannot be used for chinese version of icloud) you can generate at least 10 aliases. or use [hidemyemail-api](https://github.com/liej6799/hidemyemail-api) to login with pyicloud and get aliases as API service. account registered from web without logged in any apple device (maybe virtualbox -> macos has a shot?) will not have email service.

to send email from alias, you can try setting "FROM" address as your alias via smtp protocol, but the credential shall stay the same. the working approach could be platform specific

yahoo provides the most email alias up to 500, but 10 for send only emails. however to get one yahoo account one needs offshore phone numbers. 

### email collection, email scraping

searching for "site:pastebin.com @yahoo.com" to get some email addresses, also searching in github might help as well.

[mailcat](https://github.com/sharsil/mailcat) find email address by nickname (check if deliverable?)

[theharvestor: email harvestor](https://awesomeopensource.com/project/laramies/theHarvester)

[email collector](https://awesomeopensource.com/project/Taonn/EmailAll)

[domain and email collector](https://awesomeopensource.com/project/bit4woo/teemo)

### email marketing

use other's links/contents to increase diversity and increase anonymity. put your related contents among them.

email marketing is quantity over quality. know your customers' preferences and behaviors (language, country, life schedule (by year? month? week? time in a day?)) by linking their accounts on other platforms, telemetry.

email bulk senders are equipped with email templates, statistics (like opened or not, click data monitoring)

vary your email style and content unless you want to get blocked/trashed by servers

#### email templates

[premail](https://github.com/premail/premail) is an easy-to-use component-based build system for [MJML](https://mjml.io/), the email templating language

## SMS

### sending SMS

发送短信 邮件 第一步是收集目标的邮箱和手机号码 收集目标ID 可从社工库中获取 可以根据社工的metadata决定推送内容类别

#### SMS flooding

smsboom by whalefall 远程获取的api 不知道是干啥的 有待研究
这个的原理是收集了大量发验证码到目标的手机号的api
repo转移到了openethan下面
考虑破解这些网站 获取它们的短信验证所需要的credential
https://github.com/WhaleFell/SMSBoom

#### sending SMS with content

send sms 1 per day per ip (you might use tor to do ip switching):
https://textbelt.com/
https://github.com/HACK3RY2J/Anon-SMS
https://github.com/typpo/textbelt

freesms: (don't work for my phone number as recipient though, but I found [some interesting projects](https://github.com/search?q=afreesms.com&type=code) on github relating to free SMS sending, [some using OCR](https://github.com/seadog007/FreeSMS-OCR) to crack captcha and access API)
https://www.afreesms.com/freesms/

yoy might want phone number lists for sending ads via free sms providers

shows [number]@139.com is the only email2sms gateway in china
https://email2sms.info

list of email2sms providers:
https://www.howtogeek.com/howto/27051/use-email-to-send-text-messages-sms-to-mobile-phones-for-free/
http://www.mutube.com/projects/open-email-to-sms/gateway-list/
http://en.wikipedia.org/wiki/List_of_carriers_providing_Email_or_Web_to_SMS

### receiving SMS

#### paid sms receiving

[5sim](https://5sim.net/) paid sms receive service worldwide

#### free sms receiving

[sms auto regist](https://github.com/linabellbiu/sms-auto-regist) is written in go, utilizing `yunjiema.top` for sms receiving

online sms receivers are not so reliable (not even usable for yahoo registration), and those found from google searches (like [free receive sms](https://www.freereceivesms.com/) (这个网站有反js调试 [打开debugger自动暂停执行](http://learnspider.evilrecluse.top/)), which has simple interface for fetching data, and you can [search this site on github](https://github.com/search?q=freereceivesms.com&type=code) to get more sources and potential API adaptors like [disposable phonebook](https://github.com/anroots/disposable-phonebook/blob/769bc2b23071ba4c854a00a5012cf5c2b7a2036f/dphonebook/lib/providers/free_receive_sms_com.py)) have chances to get registered yahoo accounts.

## account registration helpers: verification, captcha solving, proxies

[account generator helper](https://github.com/Dionis1902/AccountGeneratorHelper) including:

```
Temp email services
Receive SMS
Generate data
Proxy parser
Captcha solving
```

### proxies

[Proxy-Cheap](https://www.proxy-cheap.com/) pay by data amount
