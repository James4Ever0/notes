---
created: 2022-01-01T22:00:36+08:00
modified: 2022-01-02T14:11:07+08:00
---

# Baidu Account Registration

http://im.baidu.com/promo/about.html 这个百度hi接口也可以

https://passport.baidu.com/v2/?reg

贴吧极速版 百度网盘（安装在其他手机上？卸载？）

119620
abc123456

注意每个获取到的号码都必须正确处理(要么获取到验证码，要么加黑)。不能用的号码不加黑下次还会重复获取或者达到最大同时获取号码数。在获取手机号时，提示“-1暂无号码请延迟10秒后再次请求“，请使用循环每隔5秒钟请求一次手机号，没号了系统有监控会及时加号的。在发送短信完成后最好等待10秒再开始获取验证码，因为就算是正常手机接短信也是需要大概10秒时间的，如果服务器返回”暂无短信请延迟10秒后再次请求，请过5秒再试“，最好等待5秒后再次请求。当然你可以根据自己的意愿自行设定发完短信等待时间和请求验证码间隔。建议不要太频繁。所有返回信息必须完整打印出来，否则影响用户判断。接口调用需加入延时机制，否则会封帐号、IP。请求方式：仅支持get请求平台针对IP有检测,疯狂无延迟的请求将会封号,请自行控制请求间隔主服务器IP:http://api.lx967.com:8889备用地址ip: http://api2.lx967.com:8889登录接口(login):请求地址：http://api.lx967.com:8889/sms/api/login?username=API用户名&password=密码返回样例：{"msg":"success","code":0,"expire":604800,"token":"xxxxxxxxxxx"}获取手机接口(getPhone)请求地址：http://api.lx967.com:8889/sms/api/getPhone?token=登录时返回的令牌&sid=项目ID返回样例：{"msg":"success","code":0,"phone":"13852137155"}指定手机: 传入phone=18151615155输入要指定的手机号码 必须是平台上的号码 (可空)指定号段: 传入ascription=1取随机实卡号段，ascription=2取随机虚卡号段 (可空)获取验证码(getMessage)请求地址：http://api.lx967.com:8889/sms/api/getMessage?token=登陆返回的令牌&sid=项目ID&phone=取到的手机号码返回样例：{"msg":"success","code":0,"sms":"您的短信为10083"} 作者分成: 传入&tid=用户ID参数内容，作者UID可在客户端查看(可空)加黑手机（addBlacklist）请求地址：http://api.lx967.com:8889/sms/api/addBlacklist?token=登陆返回的令牌&sid=项目ID&phone=手机号码返回样例：{"msg":"success","code":0}获取金额：http://api.lx967.com:8889/sms/api/userinfo?token=登陆返回的令牌返回列子：{"msg":"success","code":0,"money":"1.0"}发送短信（sendMessage）请求地址：http://api.lx967.com:8889/sms/api/sendMessage?token=登陆返回的令牌&sid=项目ID&phone=手机号码&content=发送内容(如果含有中文)作者分成: tid=作者ID返回列子：{"msg":"success","code":0}获取发送结果(getSendMsgStatus)请求地址：http://api.lx967.com:8889/sms/api/getSendMsgStatus?token=登陆返回的令牌&sid=项目ID&phone=手机号码返回列子：{"msg":"success","code":0}释放项目号码(cancelRecv)请求地址：http://api.lx967.com:8889/sms/api/cancelRecv?token=登陆返回的令牌&sid=项目ID&phone=手机号码返回列子：{"msg":"success","code":0}释放所有号码，手机号填写[phone=all]
