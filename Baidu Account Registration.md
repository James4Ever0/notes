---
tags: [auto registration, automation, baidu, credentials, freelancer, SMS]
title: Baidu Account Registration
created: '2022-01-01T14:00:36.000Z'
modified: '2022-08-18T12:06:16.612Z'
---

# Baidu Account Registration

http://app.sendsmscode.com/index/loginnew/getsms?
projectid=4231398&phone=15601041101&key=acbc178db5349222adde7c785cde3d2d3019382524

远程地址:bh49.84684.net:49003 
　　管理员:administrator密码:fsfs5214 
　　拨号帐号：801097密码825697

sms platform 1

获取号码和获取短信说明：(1)每行文本最前面11位是手机号码，不用再从平台取号。(2)“---”后面的内容为取短信的地址，地址中包含了有项目id，手机号码和密钥。发送验证码后，直接调用获取短信的地址，可以获取短信内容。(3)获取短信后，不用释放。例如：17607098524---http://107.148.0.217:8011/index/loginnew/getsms?projectid=4770800&phone=17607098524&key=df8b2f588edd00905439d97066e757a698该行手机号码为：17607098524获取短信地址为：http://107.148.0.217:8011/index/loginnew/getsms?projectid=4770800&phone=17607098524&key=df8b2f588edd00905439d97066e757a698获取短信

http://107.148.0.217:8011/01642097789_1d000741d23636f753366777546ed73c.txt

http://107.148.0.217:8011/index.php/index/login/getsms?projectid=4231398&phone=13049705657&key=27bd27f908b645a4
http://107.148.0.217:8011/index.php/index/login/getsms?projectid=4231398&phone=13049705647&key=205ce85ceefc8c3e

获取短信功能获取短信获取地址http://107.148.0.217:8011/index.php/index/login/getsms?projectid=4411792&phone=13049777657&key=e21oie8e379550da8请求方法GET响应成功code=1,message返回最新一条短信内容失败code=0,message返回错误信息{"code":1,"message":"您申请注册微博的验证码为：755437（30分钟内有效，如非本人操作请忽略或咨询4000960960，本条免费）。【微博】"}备注每次获取最新一条短信

获取短信功能获取短信获取地址http://107.148.0.217:8011/index.php/index/login/getsms?projectid=4231398&phone=156788888821请求方法GET响应成功code=1,message返回最新一条短信内容失败code=0,message返回错误信息{"code":1,"message":"您申请注册微博的验证码为：755437（30分钟内有效，如非本人操作请忽略或

sms platform 2

项目id1006

API说明地址： http://www.sa4233.club:8543/api/v1编码：UTF-8提交方式：GET提交数据：地址&参数名1=值1....。例如登录的提交数据是：/login?&username=用户名&password=密码返回数据：所有API成功统一返回 {"code":0,"data":"参数",msg:"错误提示"}，失败统一返回{"code":7,"message":"没有可用号码"}。例如登录时提交了正确的用户密码，那么返回为{"code":0,"data":"fdbc9a5a56d11f880a17e5219be2eb48", "message":""}其中0表示是成功了，后面的fdbc9a5a56d11f880a17e5219be2eb48是API返回的token，如果提交了错误的账号密码，注意：每个获取到的号码都必须正确回馈数据。在获取手机号时，提示“没有可用号码“，请使用死循环每隔三秒钟请求一次手机号，没号了系统有监控会及时加号的。如果服务器返回”验证码还没有回来“，最好等待3秒后再次请求。当建议不要太频繁，系统负载过高的情况下会针对高并发用户临时封IP。登录方法[Login]网页地址： http://www.sa4233.club:8543/api/v1/login提交参数：username=用户名&password=密码调用实例：http://www.sa4233.club:8543/api/v1/login?username=用户名&password=密码返回值：{"code":0,"data":"token",msg:""} (token是重要的返回参数，后面所有的请求都要传这个参数值)返回值：{"code":7,"data":"",msg:"错误提示"}获取手机号[phone]网页地址： http://www.sa4233.club:8543/api/v1/phone提交参数：token=登录时返回的令牌 projectId=项目id调用实例：http://www.sa4233.club:8543/api/v1/phone?token=登录时返回的令牌&projectId=项目id返回值：{"code":0,"data":"phone",msg:""} (这代表成功获取到手机号码)返回值：{"code":7,"data":"",msg:"没有可用号码"}当返回 "没有可用号码" ，请过3秒后重新取号。当返回 "抱歉，您的余额不足请充值后再试" , 请及时充值等存在“余额不足”的字眼，请停止软件运行。获取验证码[message]网页地址： http://www.sa4233.club:8543/api/v1/message提交参数：token=登录时返回的令牌&phone=取出来的手机号&projectId=项目id调用实例： www.sa4233.club:8543/api/v1/message?token=登录时返回的令牌&phone=取出来的手机号&projectId=项目id返回值：{"code":0,"data":"验证码",msg:""}返回值：{"code":7,"data":"",msg:"错误信息"}回馈注册结果[result]网页地址： http://www.sa4233.club:8543/api/v1/result提交参数：token=登录时返回的令牌&phone=取出来的手机号&projectId=项目id&status=(1=成功 2=失败)回馈成功： www.sa4233.club:8543/api/v1/result?token=登录时返回的令牌&phone=取出来的手机号&projectId=项目id&status=(1=成功 2=失败)回馈失败： www.sa4233.club:8543/api/v1/result?token=登录时返回的令牌&phone=取出来的手机号&projectId=项目id&status=(1=成功 2=失败)返回值：{"code":0,"data":"ok",msg:""}返回值：{"code":7,"data":"",msg:"错误信息"}


地址：http://117.50.175.176/请求方式：POST示例：http://117.50.175.176/ POST type=getcode&token=xxx&id=xxx&account=xxx获取手机号 随机取码类型：type=getcodetoken：文本，登录返回的tokenproject：文本，项目idaccount：文本，账户释放手机号类型 ：type=getreleasePhoneNotoken：文本，登录返回的tokenphone：文本，手机号获取验证码类型 ：type=takemessagetoken：文本，登录返回的tokenproject：文本，项目idphone：文本，手机号account：文本，账户获取子账户余额类型：type=takemoneytoken：文本，登录返回的tokenaccount：文本，账户子账户登录，返回加密的token类型：type=aloginaccount：文本，账户password：文本，密码



[27/6]生成成功:S_IQbNu0hFXIvT[10元]
[27/5]生成成功:S_OC5VruqBCBAI[10元]
[27/4]生成成功:S_eByy5SzNDeL0[10元]
[27/3]生成成功:S_cv4FrZMBAaFx[10元]


远程地址:bh76.84684.net:11527 
　　管理员:administrator密码:fsfs5214 
　　拨号帐号：801006密码152415 

bh19.84684.net:19055

administrator

fsfs5214

[50/44]生成成功:S_yJLsyW8hSw9R[10元]

http://www.66daili.cn

714180884@qq.com

fsfs5214

[90/33]生成成功:S_E926kBLiITjQ[10元]

http://www.dididati.com/user

17756220843

fs5214

http://im.baidu.com/promo/about.html 这个百度hi接口也可以

https://passport.baidu.com/v2/?reg

贴吧极速版 百度网盘（安装在其他手机上？卸载？）

username:
119620

api_username:
api-OvxtGsBA

abc123456

@all 服务器地址已经更新请大家及时更新，所有客户端和api地址都需要更新，老的地址将在24小时后停用。（重启自动更新或者在网址下载https://wwx.lanzoui.com/b010k124j 密码:1122）
2. 任何人问你们要密码或者密保都是骗子，主动私聊你们涨权重都是骗子
3. 珍惜自己的账号，不要给任何人


注意每个获取到的号码都必须正确处理(要么获取到验证码，要么加黑)。不能用的号码不加黑下次还会重复获取或者达到最大同时获取号码数。在获取手机号时，提示“-1暂无号码请延迟10秒后再次请求“，请使用循环每隔5秒钟请求一次手机号，没号了系统有监控会及时加号的。在发送短信完成后最好等待10秒再开始获取验证码，因为就算是正常手机接短信也是需要大概10秒时间的，如果服务器返回”暂无短信请延迟10秒后再次请求，请过5秒再试“，最好等待5秒后再次请求。当然你可以根据自己的意愿自行设定发完短信等待时间和请求验证码间隔。建议不要太频繁。所有返回信息必须完整打印出来，否则影响用户判断。接口调用需加入延时机制，否则会封帐号、IP。请求方式：仅支持get请求平台针对IP有检测,疯狂无延迟的请求将会封号,请自行控制请求间隔主服务器IP:http://api.lx967.com:8889备用地址ip: http://api2.lx967.com:8889登录接口(login):请求地址：http://api.lx967.com:8889/sms/api/login?username=API用户名&password=密码返回样例：{"msg":"success","code":0,"expire":604800,"token":"xxxxxxxxxxx"}获取手机接口(getPhone)请求地址：http://api.lx967.com:8889/sms/api/getPhone?token=登录时返回的令牌&sid=项目ID返回样例：{"msg":"success","code":0,"phone":"13852137155"}指定手机: 传入phone=18151615155输入要指定的手机号码 必须是平台上的号码 (可空)指定号段: 传入ascription=1取随机实卡号段，ascription=2取随机虚卡号段 (可空)获取验证码(getMessage)请求地址：http://api.lx967.com:8889/sms/api/getMessage?token=登陆返回的令牌&sid=项目ID&phone=取到的手机号码返回样例：{"msg":"success","code":0,"sms":"您的短信为10083"} 作者分成: 传入&tid=用户ID参数内容，作者UID可在客户端查看(可空)加黑手机（addBlacklist）请求地址：http://api.lx967.com:8889/sms/api/addBlacklist?token=登陆返回的令牌&sid=项目ID&phone=手机号码返回样例：{"msg":"success","code":0}获取金额：http://api.lx967.com:8889/sms/api/userinfo?token=登陆返回的令牌返回列子：{"msg":"success","code":0,"money":"1.0"}发送短信（sendMessage）请求地址：http://api.lx967.com:8889/sms/api/sendMessage?token=登陆返回的令牌&sid=项目ID&phone=手机号码&content=发送内容(如果含有中文)作者分成: tid=作者ID返回列子：{"msg":"success","code":0}获取发送结果(getSendMsgStatus)请求地址：http://api.lx967.com:8889/sms/api/getSendMsgStatus?token=登陆返回的令牌&sid=项目ID&phone=手机号码返回列子：{"msg":"success","code":0}释放项目号码(cancelRecv)请求地址：http://api.lx967.com:8889/sms/api/cancelRecv?token=登陆返回的令牌&sid=项目ID&phone=手机号码返回列子：{"msg":"success","code":0}释放所有号码，手机号填写[phone=all]
