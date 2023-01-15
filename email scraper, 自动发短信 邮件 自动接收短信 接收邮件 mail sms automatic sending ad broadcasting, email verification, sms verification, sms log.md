---
tags: [advertising, mail sending, SMS]
title: 'email scraper, 自动发短信 邮件 自动接收短信 接收邮件 mail sms automatic sending ad broadcasting, email verification, sms verification, sms login, email login, temp mail, email OSINT'
created: '2022-07-04T12:47:02.000Z'
modified: '2023-01-15T00:25:38.817Z'
---

# email scraper, 自动发短信 邮件 自动接收短信 接收邮件 mail sms automatic sending ad broadcasting, email verification, sms verification, sms login, email login, temp mail, email OSINT

## email

### email OSINT

OSINT/recon 其实就是社工 但是一般人喜欢把社工库和社工分开 因为社工库是社工收集来的数据集合 而社工则是一个过程

#### check registration account with email

[reg007 counterpart](https://github.com/CreditTone/regchecker) only check if that account "exists", but no actual account shown. [search for reg007 on github](https://github.com/search?p=1&q=reg007.com&type=Code) you will get a bunch of links relating to OSINT.

[holehe](https://github.com/megadose/holehe) only check if an email address is registered as account elsewhere using "forget my password" APIs.

#### email account verifier

Usually it only verify existance of given email, like [emailhippo](https://tools.verifyemailaddress.io/) (100 requests free per day per ip), or [mailforguess](https://github.com/WildSiphon/Mailfoguess) checking "gmail","laposte","protonmail","yahoo" emails

Some of them verify email with password: [verify email address and password with API of my.com](https://github.com/MachineKillin/Email-Account-Generator-Checker/blob/main/main.py)

### email connectors/client

[proton mail unofficial client in python](https://github.com/ShellCode33/ProtonMail)

### email registration

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

email marketing is quantity over quality. know your customers' preference by linking their accounts on other platforms, telemetry.

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

