---
tags: [mail sending]
title: 自动发短信 邮件 mail sms automatic sending ad broadcasting
created: '2022-07-04T12:47:02.000Z'
modified: '2022-08-18T16:00:42.596Z'
---

# 自动发短信 邮件 mail sms automatic sending ad broadcasting

发送短信 邮件 第一步是收集目标的邮箱和手机号码 收集目标ID 可从社工库中获取 可以根据社工的metadata决定推送内容类别

smsboom by whalefall 远程获取的api 不知道是干啥的 有待研究
这个的原理是收集了大量发验证码到目标的手机号的api
repo转移到了openethan下面
考虑破解这些网站 获取它们的短信验证所需要的credential
https://github.com/WhaleFell/SMSBoom

send sms 1 per day per ip (you might use tor to do ip switching):
https://textbelt.com/
https://github.com/HACK3RY2J/Anon-SMS
https://github.com/typpo/textbelt

freesms:
https://www.afreesms.com/freesms/

yoy might want phone number lists for sending ads via free sms providers

shows [number]@139.com is the only email2sms gateway in china
https://email2sms.info

list of email2sms providers:
https://www.howtogeek.com/howto/27051/use-email-to-send-text-messages-sms-to-mobile-phones-for-free/
http://www.mutube.com/projects/open-email-to-sms/gateway-list/
http://en.wikipedia.org/wiki/List_of_carriers_providing_Email_or_Web_to_SMS
