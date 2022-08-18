---
tags: [autologin, freelancer, reverse engineering, tieba]
title: Baidu Tieba Login (QR Code)
created: '2021-12-19T21:56:45.000Z'
modified: '2022-08-18T13:47:06.071Z'
---

# Baidu Tieba Login (QR Code)

Assigned a job.

Cloud Phone:
`http://www.ddyun.com/sem/pcddybdyunkong/?bd_vid=7609174489837191328
17756220843:fsfs5214`

QR Link:
https://wappass.baidu.com/wp/?qrlogin&t=1640006201&error=0&sign=v1_13fa5a31cf31fa864475cbf3fd2fc&cmd=login&lp=pc&tpl=tb&adapter=3&logPage=traceId%3Apc_loginv4_1640006201%2ClogPage%3Aloginv4&qrloginfrom=pc&local=%E5%8D%97%E4%BA%AC

This job has no public data to refer. we need to monitor the tieba app.
mitmproxy --mode socks5 --listen-port 8050 --save-stream-file logs
Run mitmproxy without options to generate the mitm certificate. Install the certificate (usually ~/.mitmproxy/mitmproxy-ca-cert.cer) in the Android phone. It may be needed to change the extension to .crt to install it.

frida is needed to disable certificate-pinning, or if this is somehow possible. (also via justtrustme, xposed)
https://hub.fastgit.org/httptoolkit/frida-android-unpinning
https://httptoolkit.tech/blog/frida-certificate-pinning/

setenforce 0
to disable stack errors

to connect to frida-server:

https://github.com/15872998154/frida_termux

./frida_server -l 0.0.0.0:27042 

frida -H 127.0.0.1:27042 --codeshare sowdust/universal-android-ssl-pinning-bypass-2  -f com.baidu.tieba --no-pause

i will not know if the client will be satisfied or not. i only know this would be very hard to solve. if not good i will quit.


to read flow:
mitmproxy -n --showhost -r logs.log

print xxd line and ascii parse only:
cat logs2.log | xxd | awk '{print $1" "$NF}'

cat logs2.log | xxd | awk '{print $1" "$NF}' | grep -C 5 http://wap
0012f020: ss-Control-Allow
0012f030: -Methods,18:GET,
0012f040: OPTIONS,]
0012f050: 59:27:Access-Con
0012f060: trol-Allow-Origi
0012f070: n,24:http://wapp
0012f080: ass.baidu.com,]2
0012f090: 8:10:Connection,
0012f0a0: 10:keep-alive,]2
0012f0b0: 7:16:Content-Enc
0012f0c0: oding,4:gzip,]44

cat logs2.log | xxd | awk '{print $1" "$NF}' | grep -C 5 https://wap
001190e0: ite,]28:14:sec-f
001190f0: etch-mode,7:no-c
00119100: ors,]26:14:sec-f
00119110: etch-dest,5:styl
00119120: e,]40:7:referer,
00119130: 26:https://wappa
00119140: ss.baidu.com/,]3
00119150: 6:15:accept-enco
00119160: de
00119170: flate,]37:15:acc
00119180: ept-language,14:
--
0011aed0: ite,]28:14:sec-f
0011aee0: etch-mode,7:no-c
0011aef0: ors,]27:14:sec-f
0011af00: etch-dest,6:scri
0011af10: pt,]40:7:referer
0011af20: ,26:https://wapp
0011af30: ass.baidu.com/,]
0011af40: 36:15:accept-enc
0011af50: d
0011af60: eflate,]37:15:ac
0011af70: cept-language,14
--
0011ccd0: -site,]28:14:sec
0011cce0: -fetch-mode,7:no
0011ccf0: -cors,]26:14:sec
0011cd00: -fetch-dest,5:st
0011cd10: yle,]40:7:refere
0011cd20: r,26:https://wap
0011cd30: pass.baidu.com/,
0011cd40: ]36:15:accept-en
0011cd50: coding,13:gzip,
0011cd60: deflate,]37:15:a
0011cd70: ccept-language,1
--
00121f40: -site,]28:14:Sec
00121f50: -Fetch-Mode,7:no
00121f60: -cors,]26:14:Sec
00121f70: -Fetch-Dest,5:im
00121f80: age,]40:7:Refere
00121f90: r,26:https://wap
00121fa0: pass.baidu.com/,
00121fb0: ]36:15:Accept-En
00121fc0: coding,13:gzip,
00121fd0: deflate,]37:15:A
00121fe0: ccept-Language,1
--
0012f550: in,]28:14:Sec-Fe
0012f560: tch-Mode,7:no-co
0012f570: rs,]27:14:Sec-Fe
0012f580: tch-Dest,6:scrip
0012f590: t,]256:7:Referer
0012f5a0: ,241:https://wap
0012f5b0: pass.baidu.com/w
0012f5c0: p/?qrlogin&t=163
0012f5d0: 9980306&error=0&
0012f5e0: sign=v1_f3b74f3a
0012f5f0: 21e355010985e711
--
00139700: ,]28:14:Sec-Fetc
00139710: h-Mode,7:no-cors
00139720: ,]26:14:Sec-Fetc
00139730: h-Dest,5:image,]
00139740: 40:7:Referer,26:
00139750: https://wappass.
00139760: baidu.com/,]36:1
00139770: 5:Accept-Encodin
00139780: defla
00139790: te,]37:15:Accept
001397a0: -Language,14:en-
--
0013db70: 39997136312&tpl=
0013db80: tb&auto_statisti
0013db90: c=e2V2ZW50VHlwZT
0013dba0: p0b3VjaC1qcy1lcn
0013dbb0: Jvcn0=&extrajson
0013dbc0: =https://wappass
0013dbd0: .baidu.com/wp/?q
0013dbe0: rlogin&t=1639980
0013dbf0: 306&error=0&sign
0013dc00: =v1_f3b74f3a21e3
0013dc10: 55010985e7113869

https://blog.csdn.net/qq_27644127/article/details/112987332

with a plugin to collect statistics:
http://file.taotaoya.top/load/TT.rar

that guy wants me to discover barcode first.

i may paste cookies here:
https://termbin.com/lq5e

use ccrypt, xxd and nc to do transport. (do you have these?)

cat cookies.log.cpt | xxd | nc termbin.com 9999
xxd -r
ccrypt -c cookies.log.cpt

passwd:abcdefg


a typical QR login link on android:
https://wappass.baidu.com/wp/?qrlogin&t=1639929144&error=0&sign=v1_3b3e89197877163a12614a9a7f519&cmd=login&lp=pc&tpl=tb&adapter=3&clientfrom=native&qrloginfrom=native&local=%E9%93%9C%E9%99%B5

parsed with elinks copied with termux-clipboard-set:

   Link: [1]canonical
   Link: [2]alternate (handheld)

                         百度贴吧二维码登录--python爬虫

   [3]lxguang_tao 2021-01-22 18:11:49 547 收藏
   分类专栏： [4]python 文章标签： [5]python
   版权声明：本文为博主原创文章，遵循 [6]CC 4.0 BY-SA 版权协议，转载请附上原
   文出处链接和本声明。
   本文链接：[7]https://blog.csdn.net/qq_27644127/article/details/112987332
   版权
   [8][IMG] [9]python 专栏收录该内容
   1 篇文章 0 订阅
   订阅专栏

  百度贴吧二维码登录--python爬虫

     • 
          • [10]研究思路
          • 
               • [11]探索过程
               • [12]思路总结

          • [13]代码实现
          • 
               • 
                    • [14]所需技术
                    • [15]代码

          • [16]总结

研究思路

     如果阅读此文章的小伙伴之前研究过贴吧相关的接口的话，就会知道，那些需要登
     录才能实现的功能接口，你去爬虫的话要携带一个Cookie BDUSS，有了它就会通过
     身份验证。这个BDUSS也可以通过浏览器访问贴吧页面，从而获得，但在同一个浏
     览器中如果更换帐号登录，那么你从这个浏览器中拿到的之前那个BDUSS就会失效
     （不可能这个浏览器永远挂着这个帐号，并且保证不会去修改密码）。为了获得一
     个永不失效的BDUSS，我们可以通过登录方法来获取BDUSS，但我们不可能会使用这
     个BDUSS去做退出和切换帐号操作，所以它一般拿到后就不会失效（除非改了密码
     ）。

  探索过程

   [17]二维码

    1. 不管是贴吧首页，还是其他地方的贴吧登录页面，都会有这个二维码登录的地方
       。我们第一步是看怎么去拿到这个二维码图片地址。

    2. 思路：爬取这个页面，从页面元素中找到这个二维码连接，结果就是，二维码连
       接不是响应页面加载出来的，那就说明是通过后续的接口返回的然后添加到页面
       中的。所以我们接下来要去寻找加载二维码的接口。

    3. 寻找接口：打开F12，切换到Network，刷新页面，你会看到一条类型为png的记
       录，点开看到响应正是这张二维码图片
       [18]二维码请求地址

    4. 查看请求相关内容：地址，参数，类型。Get请求，有三个参数分别是sign,lp
       和qrloginfrom，看到后两个参数的值都是pc。盲猜应该可以是固定值pc(电脑
       端)。所以现在就只剩下一个参数需要搞清楚，那就是sign。
       [19]在这里插入图片描述

    5. 遵循代码从上往下运行的规则，这个sign肯定是在二维码加载前就获取到了，所
       以我们要在它的上面的记录里寻找一下。经过一番寻找，最终
       在“https://passport.baidu.com/v2/api/getqrcode?lp=pc&qrloginfrom=pc&gid=1527EF2-1333-475F-BA75-319AF40E53E7&callback=tangram_guid_1611304323880&apiver=v3&tt=1611304324028&tpl=tb&_=1611304324032”
       的响应中找到了sign，当然响应中有整个图片链接。

    6. 不过坑爹啊，这个请求中也有好多个参数。不过看到这个参数，发现有好几个都
       是无意义的。tt和_我们看长度可以推断出应该是时间戳，经过验证，确实是当
       时时间的时间戳。所以我们主要需要攻破的就是gid与callback。还是老样子，
       先找gid，去上面找但是就是找不到。看gid像是那种唯一值，python中叫uuid。
       既然找不到，那就可能是前端生成的，所以我们可以去找这个请求发起的js。看
       看它这个参数到底是怎么来的。在F12 Source中按 Ctrl+Shift+F全局搜
       索“v2/api/getqrcode”。
       [20]参数

    7. 通过搜索我们发现确实是前端生成的随机唯一值。那我们就可以放心大胆的自己
       去生成了，当然要生成出来的格式一样。现在就只剩下callback了。正当我苦思
       冥想找不到的时候，真的想破口而出：怎么这么难找啊，tmd烦死了。我后面发
       现，嗯它后面那一串数字跟下面的时间戳基本一样。好家伙，这都能算一个参数
       ，我是真的服。这样最后一个参数我们也能靠自己生成。这个接口拿下。
       [21]在这里插入图片描述

    8. 到现在我们已经实现了，（1）请求返回二维码地址的接口。（2）返回二维码图
       片的地址。相当于我们做好了获取BDUSS的第一步。（长舒一口气）

    9. 现在我们要进行第二部，扫码后进行怎样的处理。

     扫码登录原理：网页生成二维码后，后面轮询进行一个请求，来返回当前二维码的
     状态。
     当二维码被扫后，访问二维码内容，服务端会进行处理（是否登录，做登录操作）
     当然如果一直没有扫码请求，那么就一直循环请求，直到二维码过期为止。

   10. 查看Network后续内容，发现确实有一个接口在不停的请求。查看参数发现，都
       是我们玩剩下的，除了channel_id是图片链接中的一个参数换了名字外，其他我
       们都有办法获得。
       [22]监听
   11. 我们现在要做的就是模拟浏览器进行轮询请求，当请求返回正确登录的响应的时
       候，发现它返回了
       **tangram_guid_1611307815857({"errno":0,"channel_id":"v1_cf81fb2823935db841b5395152de2","channel_v":"{\"status\":0,\"v\":\"3f1a8f93cca689cead144ad405b03945\",\"u\":\"\"}"})
       ** 这跟登录有毛关系啊，发现后面它又调用了一个借口，看这名字就知道了，
       就是它了。
   12. /v3/login/main/qrbdusslogin
       [23]有这几个参数
   13. 发现了联系，bduss是刚才轮询接口返回的。其他参数看着无意义的都直接用它
       的。先调用再说。如果调用成功，返回的是一个JSON数据，但是并没有BDUSS
       。tmd，都忘了我们去拿BDUSS的是去哪拿的吗。恍然大悟，Cookie啊。果然，从
       响应中，看到写入浏览器了Cookie。
       [24]cookie
   14. 至此是通过二维码登录拿到BDUSS的全部过程。虽然看上去简单，但是实际去操
       作的时候，还是有一些坑的。回过头来看看，那些坑也是必经之路吧，坑走过一
       遍后，就更加印象深刻。

  思路总结

   总结一下： 基本上是从人的思考方式下手。从二维码从哪来开始，其实也就是一直
   不断的在调接口，找参数，处理响应。不管哪一步，基本都离不开这三样。当然这次
   的最重要的是理解二维码登录的实际原理，只有理解了它的原理才能去做好对策。

代码实现

    所需技术

   python request模块，json模块，re模块，time, uuid

    代码

 """
 QrCodeLogin.py 二维码登录
 """
 """
 1、访问首页，获取二维码
 2、请求响应接口
 3、。。。。
 """

 import requests, re, time, json, uuid

 class qrcodeLogin:
     def __init__(self):
         self.get_qrcode_url = "https://passport.baidu.com/v2/api/getqrcode"
         self.unicast_url = "https://passport.baidu.com/channel/unicast"
         self.login_url = "https://passport.baidu.com/v3/login/main/qrbdusslogin"
         self.qrcode = ""
         self.gid = str(uuid.uuid4()).upper()
         self.callback = ""
         self.sign = ""
         self.bduss = ""
         self.headers = {
             "User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:74.0) Gecko/20100101 Firefox/74.0"
         }

     def get_qrcode(self):
         self.callback = "tangram_guid_{}".format(str(int(round(time.time() * 1000))))
         parms = {
             "lp":"pc",
             "qrloginfrom": "pc",
             "gid": self.gid,
             "callback": self.callback,
             "apiver": "v3",
             "tt": int(round(time.time() * 1000)),
             "tpl": "tb",
             "-": int(round(time.time() * 1000))
         }
         html = requests.get(url=self.get_qrcode_url, params=parms, headers=self.headers, verify=False).content.decode('utf-8', errors='ignore')
         # print(html)
         p = re.compile('"imgurl":"(.*?)"')
         p2 = re.compile('"sign":"(.*?)"')


         qrcode = p.findall(html)
         self.sign = p2.findall(html)
         if len(qrcode) == 0:
             return None
         else:
             print("https://"+qrcode[0].replace("\\", ""))
             self.qrcode = "https://"+qrcode[0].replace("\\", "")

     def unicast(self):
         start = time.time()
         errno = 1
         status = 1
         flag = True
         pattern = re.compile('({.*})')
         while(True):
             end = time.time()
             if (end - start) > 300:
                 break
             parms = {
                 "channel_id": self.sign,
                 "qrloginfrom": "pc",
                 "gid": self.gid,
                 "callback": self.callback,
                 "apiver": "v3",
                 "tt": int(round(time.time() * 1000)),
                 "tpl": "tb",
                 "-": int(round(time.time() * 1000))
             }
             jsons = requests.get(url=self.unicast_url, params=parms, headers=self.headers, verify=False)
             html = jsons.content.decode('utf-8', errors="ignore").replace('\\', '').replace('"{', "{").replace('}"', "}")
             try:
                 if errno or status:
                     message = json.loads(re.search(pattern, html).group())
                     errno = message['errno']
                     if errno == 0 and flag:
                         flag = False
                     elif errno == 0:
                         status = message['channel_v']['status']
                 if not errno and not status:
                     message = json.loads(re.search(pattern, html).group())
                     self.bduss = message['channel_v']['v']
                     BDUSS = self.login()
                     print(BDUSS)
                     return BDUSS
             except Exception as e:
                 print(e)
                 break
         return None

     def login(self):
         parm = {
             'v': int(round(time.time() * 1000)),
             'u': 'https://tieba.baidu.com/index.html',
             'bduss': self.bduss,
             'loginVersion': 'v4',
             'qrcode': '1',
             'tpl': 'tb',
             'apiver': 'v3',
             'tt': int(round(time.time() * 1000)),
             'traceid': None,
             'time': round(time.time()),
             'alg': 'v3',
             'sig': 'EsdgfadNMU5rQVl4NWhSDFSDCVSDGFSdfsdfsf8xcVEveFNqanFGK2ZRdDBiejdXQXVhK1ZlRDZKMzsdfDSES==',
             'elapsed': 3,
             'shaOne': '00edf2343d07csdf23478b6ccd34f9a92290d3tg',
             'callback': 'bd__cbs__o5224l',
         }

         login_r = requests.get(self.login_url, headers=self.headers, params=parm, verify=False)
         str_html = login_r.content.decode('utf-8')
         # print(str_html)
         for i in login_r.cookies:
             if i.name == "BDUSS":
                 print('登陆成功')
                 pname = re.compile('"displayName": "(.*?)"')
                 name_list = pname.findall(str_html)
                 # print(name_list)
                 if len(name_list) > 0:
                     name = name_list[0]
                     return (i.value, name)
                 return (i.value, '')
         return None


     def getImg(self):
         img = requests.get(url=self.qrcode, headers=self.headers, verify=False)
         # print(img.content)
         # with open("tieba.gif", 'wb') as w:
         #     w.write(img.content)
         return img.content



 if __name__ == '__main__':
     s = qrcodeLogin()
     s.get_qrcode()
     s.getImg()
     s.unicast()





总结

   这一步是打开贴吧自动化大门的关键，有了它我们就能轻松做很多事情了。
   贴上自己做的一些统计工具的截图，如果有小伙伴感兴趣，或者需要帮做小功能的，
   可以评论私信哦。
   附上下载地址：[25]地址
   [26]在这里插入图片描述[27]在这里插入图片描述

   [28][IMG][29]lxguang_tao
   [30]关注 关注

     • 2
       点赞
     • 
       踩
     • [31][IMG] [32]1
       评论
     • [33][IMG] [34][IMG] [35][IMG] [36]0
       收藏
     • [37]一键三连
       一键三连
     • 

     • [38][IMG]

       扫一扫，分享海报

   专栏目录
   [39]tieba_sign::mobile_phone: 百度贴吧多线程扫码登陆 自动签到 自动打码-源
   码
   05-07
   [40]Tieba_Sign 百度贴吧多线程扫码登陆 / 自动签到 / 自动打码 经测试：在三个
   帐号，一共207个贴吧的情况下，全部签到完成速度为5s左右。(Cookies登录情况下)
   Use：Python3.6以上 效果 使用教程 1.安装依赖 pip install -r
   requirements.txt # Centos yum install zbar -y # Ubuntu sudo apt-get
   install libzbar-dev -y 2.增加用户配置 (tieba_sign.py) user_lists = ['用户
   名'] # 用户名,例如['用户1', '用户2', '用户3'] 一共3个用户 # 请按照从前往后
   的顺序来依次进行登陆 运行 python tieba_sign.py # 开始登录并签到 请注意，在
   最新版本中，需要扫码登陆，程序运行的时候，会问你是否有百度贴吧
   [41]python爬虫解决百度贴吧登陆验证码问题
   [42]weixin_34236869的博客
   06-29 222
   [43]作为贴吧重度用户，写了个贴吧爬虫脚本 抄了一些别人的代码。记得有个验证
   码解决的。可是忘了链接了，今天最终自己攻克了。 首先要让登陆须要验证码，不
   停地登陆就好了。。。度娘非常快会加上验证码大法的。。。须要验证码的情况下，
   直接登陆返回的错误信息是error=257 打开贴吧首页选择登陆，弹出验证码，找到验
   证码的链接是 右键在新标签页中打开 注意到链接是 ...
   评论1
   [44][IMG]
   [45]
   _____________________
   请先登录 后发表评论~
   [46]表情包 插入表情
   [47]表情包 代码片

     • HTML/XML
     • objective-c
     • Ruby
     • PHP
     • C
     • C++
     • JavaScript
     • Python
     • Java
     • CSS
     • SQL
     • 其它

   [48][ 评论 ] [49][ 评论 ]
   [50]Python爬虫系列之百度贴吧爬取
   [51]Packager
   11-28 176
   [52]今天给的一个爬虫小事例，贴吧段子爬取这样一个小功能，数据呢仅仅娱乐，没
   有恶意想法 若有侵权，请私信删除 此次用到的一个解析库Beautiful Soup，更轻量
   简单地对数据进行解析，已获得目标数据 贴吧做的还是比较好，有一定的反爬机制
   ，所以我们也应该有一定的应对措施，具体对应我们requests获取到的数据对应页面
   源代码，通过观察发现数据的是否异步与注释等等反爬问题 以下是代码部分 #
   -*-...
   [53]Python 网络爬虫实战：爬取百度贴吧高清原图
   最新发布
   [54]亮出锋芒，剑指苍穹
   11-15 654
   [55]前段时间受哥儿们所托，爬取贴吧某帖子里的高清图片。 事情是这样的，我哥
   们发现被贴吧中有好多漂亮的图片，想下载原图做壁纸，但是帖子里图片太多了，他
   全都要，于是想让我帮忙写个爬虫，批量下载下来。 要求只有两个： 下载原图 实
   现批量下载 话不多说，直接开始。 1. 分析网站 哥们提供的帖子地址：
   https://tieba.baidu.com/p/6516084831 。 先分析 url 组成，我们可以猜到
   6516084831 是帖子的 id 。 在 勾选只看楼主，翻页 等这些操作之后，链接变成了
   这样 ht

   [56]Python模拟二维码登录百度
   [57]ljc545w的博客
   12-11 872
   [58]模拟二维码登录百度写在前面准备工作二维码地址登录状态获取gid登录参数代
   码部分二维码展示获取cookie完整代码写在后面 写在前面 前段时间写了利用BDUSS
   到达百度首页，这一次尝试使用二维码模拟登录，目前网上能搜到的相关内容基本失
   效了，但是思路基本不变，无非是百度改了些参数。本文较为复杂，要求对python
   的requests模块以及Chrome审查元素有一定了解，我不确定自己是否能完全讲明白，
   讲多少是多少吧，各位看官请坐。 准备工作 二维码地址 打开Chrome浏览器，清理
   掉baidu.com下的所有co
   [59]python模拟登陆百度
   [60]kaerbuka的博客
   07-02 786
   [61]本文原地址 目录 说明 环境准备 登陆过程分析 登陆过程完整代码 有效性测试
   说明 本文做的是百度二维码扫码登陆，至于为什么要做扫码登陆，主要是因为：1，
   用账号密码登陆时，在测试过程中，如果清除cookie，会弹出验证码，这个倒是无所
   谓，要命的是在登陆过程中有可能出发百度的账号保护机制，就算输入验证码，百度
   还会强制要求手机短信进行二次验证，这个触发机制目前还不明确。 准备环境 准
   备python...
   [62]Python爬取百度贴吧回帖中的微信号（基于简单http请求）
   [63]草小诚的博客
   01-03 368
   [64]前些日子媳妇儿有个需求，想要一个任意贴吧近期主题帖的所有回帖中的微信号
   ，用来做一些微商的操作，你懂的。因为有些贴吧专门就是微商互加，或者客户留微
   信的，还有专门特定用户群的贴吧，非常精准，我们一致认为比其他加人模式效率要
   高，所以如果能方便快捷的提取微信号，价值还是很高的（事后来看微信号到购买转
   化率约1%，已经很满意了）。 那需求很明确，说干就干，当天晚上就想把这个工具
   实现出来，我呢打开电脑开始调研 ...
   [65]17-用python爬取下载女神照片
   [66]bigzql的博客
   10-13 1万+
   [67]今天咱们要爬取花瓣网 https://huaban.com/ 设计师寻找灵感的天堂!有海量的
   图片素材可以下载,是一个优质图片灵感库 这次我们用 requests 登录花瓣网，爬取
   页面，再用正则与json提取有用信息，最后把获取的图片信息 保存到本地 一 、用
   到技术 python 基础 requests 登录页面获取session用户会话，下载图片 正则表达
   式 提取页面的有用信息 json解析页面中的图片 二、 目标页面
   https://huaban.com/search/?q=女神&catego
   [68]精心整理|Python爱好者社区历史文章合集（作者篇）--20190925从豆瓣获取
   [69]小仙女说：但行好事，不问前程
   09-25 4719
   [70]精心整理|Python爱好者社区历史文章合集（作者篇） 参考文件地址
   ：http://www.360doc.com/content/18/0801/00/2990557_774796873.shtml（供共同
   学习python的同学食用） 若侵权，联系删除 7月16日更新： Python爬取起点中文网
   小说排行榜信息（上海线下培训作业） 唯一小编王大...
   [71]python百度贴吧登录协议_python爬虫解决百度贴吧登陆验证码问题
   [72]weixin_39974223的博客
   12-03 166
   [73]作为贴吧重度用户，写了个贴吧爬虫脚本抄了一些别人的代码。记得有个验证码
   解决的。可是忘了链接了，今天最终自己攻克了。首先要让登陆须要验证码，不停地
   登陆就好了。。。度娘非常快会加上验证码大法的。。。须要验证码的情况下，直接
   登陆返回的错误信息是error=257打开贴吧首页选择登陆，弹出验证码，找到验证码
   的链接是 右键在新标签页中打开 注意到链接是这个时候依据之前写的代码，判定登
   陆成功是依据post登录...
   [74]python贴吧-qpython贴吧
   [75]q6q6q的专栏
   10-28 250
   [76]广告关闭腾讯云双11爆品提前享，精选热门产品助力上云，云服务器首年88元起
   ，买的越多返的越多，最高满返5000元！目录1. url的组成 2. 贴吧爬虫2.1. 只爬
   贴吧第一页2.2. 爬取所有贴吧的页面 3. get和post的区别3.1. get请求3.2. post
   请求3.3. 有道翻译模拟发送post请求...wd=%e7%bc%96%e7%a8%8b%e5%90%a7我们也可
   以在pyth...
   [77]百度贴吧新玩法你会用吗？
   [78]张一刻
   08-19 161
   [79]大家好，我是张一刻，专注于营销多年 今天我们来聊聊贴吧营销，可能在很多
   人心里 贴吧已经落伍了，贴吧营销不被大家看好，但这还是一种渠道，不自己试试
   怎能轻易否定呢？ 最近我正好在研究如何从贴吧导用户到微信公众号上，分享一下
   心得，希望对你有帮助： 1、用二维码做头像2、将二维码做成签名图片（注册满3个
   月才能设置签名档） 3、个人简介里添加微信号 4、发文章，正文中含品牌名、关键
   词和微信号，标题含品牌关键...
   [80]【HTTP】百度贴吧WEB版签到流程分析
   [81]大东的博客
   01-03 542
   [82]文章目录流程图接口抓包与分析获取二维码轮询扫码结果获取Cookie获取关注的
   吧贴吧签到总结 流程图 接口抓包与分析 获取二维码 Url
   ：https://passport.baidu.com/v2/api/getqrcode 请求方式：Get 请求参数
   ：lp=pc 虽然抓包发现有很多参数，但是经过实际测试发现只需要传lp这一个就可以
   了，后续接口不再做说明 返回结果： { “imgurl”:...
   [83]贴吧二维码图秒删处理
   [84]小胡实战引流
   11-07 2898
   [85]今天和大家分享的是这几天把 最流行 简单的 发二维码 这节课不是侧重实操，
   如果大家看过我以前的视频，这个就很好做了 我们来看一下 ，最近发二维码有多么
   猖狂
   https://tieba.baidu.com/f?ie=utf-8&kw=%E8%AF%9A%E6%8B%9B%E4%BB%A3%E7%90%86&fr=search
   大家可以看到这都是直接就发二维码图基本上都不处理...
   [86]贴吧一发二维码就被删！是你没掌握技术
   [87]星空软件
   03-07 5039
   [88]贴吧防删图制作！在利用百度贴吧做推广引流的小伙伴们，你们是不是会遇到这
   样的一个情况，自己发的图片有时候被度娘给秒删了？为什么会这样呢？今天聪明星
   小编就来为你分享下百度贴吧发图片的技术干货，小板凳可要做好了！ 被度娘秒删
   的帖子多少跟自己账号也有一定的关系，关于账号的问题，下期我们会在我的csdn账
   号里面在分享《百度贴吧如何发帖？贴吧发帖防删技巧干货分享！》，此处就不在赘
   述了。还有一种原因就是图片的...
   [89]Golang 百度云扫码登录
   [90]ALakers的博客
   12-24 262
   [91]文件结构： http_client.go代码如下： package client import ( "bytes"
   "fmt" "io" "io/ioutil" "net/http" "net/http/cookiejar" "net/url" "strings"
   "time" ) // HTTPClient http client type HTTPClient struct { *http.Client
   UserAgent string } var ( UserAgen
   [92]1.爬虫基础——了解html&什么是爬虫
   [93]python伊甸园的博客
   10-10 3141
   [94]众所周知：我们上网浏览的网页，他们的本质是一个又一个html页面。那什么
   是html呢？可以这么理解，编写JAVA有JAVA的语言逻辑，编写Python有Python的语言
   逻辑，编写网页就需要遵从html的语言逻辑，而编写好了的html就可以显示出来我们
   所看到的网页了。 如下示例： 图1 图2 正如我们在上面所看到的，当我们查
   看https://www.baidu.com/这个网址的时候，...
   [95]学会这招，小姐姐看你的眼神将不一样
   热门推荐
   [96]kimol君的博客
   10-03 2万+
   [97]学会这招，小姐姐看你的眼神将不一样前言一、爬虫分析二、爬取项目ID1.抓取
   帖子的URL2.提取帖子中的UUID3.完整代码三、爬取项目的数据写在最后 前言 今天
   某小丽同学来找我，有个实验需要用到轻松筹的数据进行一个分析。可是没有足够的
   数据，如何办是好？ 乐于助人的我，当然不会置之不理~ （ps.毕竟是小姐姐嘛，拒
   绝了不好，对叭） 于是乎，我抄起家伙，说干就干。 一、爬虫分析 通过简单的分
   析，可以发现轻松筹提供了一个接口，可以返回某个项目的相关数据，具体如下：
   地址如下，xxxxxx表示项目的UUID： h
   ©️2021 CSDN 皮肤主题: 游动-白 设计师:白松林 [98]返回首页
   [99][IMG]
   [100]lxguang_tao  CSDN认证博客专家 CSDN认证企业博客
   码龄7年 [101][IMG] [102]暂无认证

   3
   原创

   27万+
   周排名

   25万+
   总排名

   2242
   访问

   [103][IMG]
   等级

   44
   积分

   14
   粉丝

   6
   获赞

   1
   评论

   7
   收藏
   [104]GitHub
   [105]签到达人
   [106]新秀勋章
   [107]勤写标兵Lv1
   [108]分享学徒
   [109]私信
   关注
   [110]_____________________

  热门文章

     • [111]百度贴吧二维码登录--python爬虫 [112][IMG] [113]539
     • [114]C# 引用后visual studio不报错，生成报错 [115][IMG] [116]122
     • [117]windows系统下使用docker运行容器挂载卷报错问题 [118][IMG] [119]69

  分类专栏

     • [120][IMG] [121]python 1篇
     • [122][IMG] [123]C# 1篇

  最新评论

     • [124]百度贴吧二维码登录--python爬虫

       [125]乎你: 代码之路任重道远，愿跟博主努力习之。

  您愿意向朋友推荐“博客详情页”吗？

     • 
       强烈不推荐
     • 
       不推荐
     • 
       一般般
     • 
       推荐
     • 
       强烈推荐

   [126]_____________________ 提交

  最新文章

     • [127]windows系统下使用docker运行容器挂载卷报错问题
     • [128]C# 引用后visual studio不报错，生成报错

   [129]2021年2篇
   [130]2020年1篇

   [131]IFrame

  目录

  目录

   [132]IFrame

  分类专栏

     • [133][IMG] [134]python 1篇
     • [135][IMG] [136]C# 1篇

   实付元
   [137]使用余额支付
   点击重新获取
   扫码支付
   [138]( ) 钱包余额 0

   抵扣说明：

   1.余额是钱包充值的虚拟货币，按照1:1的比例进行支付金额的抵扣。
   2.余额无法直接购买下载，可以购买VIP、C币套餐、付费专栏及课程。

   [139][IMG][140]余额充值

References

   Visible links
   1. https://blog.csdn.net/qq_27644127/article/details/112987332
   2. file:///data/data/com.termux/files/home/works/tieba_job/content.html#
   3. https://blog.csdn.net/qq_27644127
   4. https://blog.csdn.net/qq_27644127/category_10614803.html
   5. https://so.csdn.net/so/search/s.do?q=python&t=blog&o=vip&s=&l=&f=&viparticle=
   6. http://creativecommons.org/licenses/by-sa/4.0/
   7. https://blog.csdn.net/qq_27644127/article/details/112987332
   8. https://blog.csdn.net/qq_27644127/category_10614803.html
   9. python
	https://blog.csdn.net/qq_27644127/category_10614803.html
  10. file:///data/data/com.termux/files/home/works/tieba_job/content.html#_1
  11. file:///data/data/com.termux/files/home/works/tieba_job/content.html#_5
  12. file:///data/data/com.termux/files/home/works/tieba_job/content.html#_37
  13. file:///data/data/com.termux/files/home/works/tieba_job/content.html#_39
  14. file:///data/data/com.termux/files/home/works/tieba_job/content.html#_40
  15. file:///data/data/com.termux/files/home/works/tieba_job/content.html#_42
  16. file:///data/data/com.termux/files/home/works/tieba_job/content.html#_192
  25. http://file.taotaoya.top/load/TT.rar
  28. https://blog.csdn.net/qq_27644127
  29. https://blog.csdn.net/qq_27644127
  30. javascript:;
  31. file:///data/data/com.termux/files/home/works/tieba_job/content.html#commentBox
  32. file:///data/data/com.termux/files/home/works/tieba_job/content.html#commentBox
  33. javascript:;
  34. javascript:;
  35. javascript:;
  36. javascript:;
  37. javascript:;
  38. javascript:;
  39. https://download.csdn.net/download/weixin_42122432/18441287
  40. https://download.csdn.net/download/weixin_42122432/18441287
  41. https://blog.csdn.net/weixin_34236869/article/details/86453208
  42. https://blog.csdn.net/weixin_34236869
  43. https://blog.csdn.net/weixin_34236869/article/details/86453208
  44. javascript:void(0);
  50. https://lmsoft.blog.csdn.net/article/details/84582372
  51. https://blog.csdn.net/qq_41287993
  52. https://lmsoft.blog.csdn.net/article/details/84582372
  53. https://smartcrane.blog.csdn.net/article/details/121341944
  54. https://blog.csdn.net/wenxuhonghe
  55. https://smartcrane.blog.csdn.net/article/details/121341944
  56. https://blog.csdn.net/ljc545w/article/details/111054624
  57. https://blog.csdn.net/ljc545w
  58. https://blog.csdn.net/ljc545w/article/details/111054624
  59. https://blog.csdn.net/kaerbuka/article/details/94471507
  60. https://blog.csdn.net/kaerbuka
  61. https://blog.csdn.net/kaerbuka/article/details/94471507
  62. https://blog.csdn.net/cxcjoker7894/article/details/85685115
  63. https://blog.csdn.net/cxcjoker7894
  64. https://blog.csdn.net/cxcjoker7894/article/details/85685115
  65. https://cpython.blog.csdn.net/article/details/109063267
  66. https://blog.csdn.net/bigzql
  67. https://cpython.blog.csdn.net/article/details/109063267
  68. https://blog.csdn.net/qq_32670879/article/details/101391892
  69. https://blog.csdn.net/qq_32670879
  70. https://blog.csdn.net/qq_32670879/article/details/101391892
  71. https://blog.csdn.net/weixin_39974223/article/details/110545065
  72. https://blog.csdn.net/weixin_39974223
  73. https://blog.csdn.net/weixin_39974223/article/details/110545065
  74. https://blog.csdn.net/q6q6q/article/details/109346811
  75. https://blog.csdn.net/q6q6q
  76. https://blog.csdn.net/q6q6q/article/details/109346811
  77. https://blog.csdn.net/u013177154/article/details/99288349
  78. https://blog.csdn.net/u013177154
  79. https://blog.csdn.net/u013177154/article/details/99288349
  80. https://blog.csdn.net/d745282469/article/details/103819585
  81. https://blog.csdn.net/d745282469
  82. https://blog.csdn.net/d745282469/article/details/103819585
  83. https://blog.csdn.net/weixin_44027887/article/details/102948182
  84. https://blog.csdn.net/weixin_44027887
  85. https://blog.csdn.net/weixin_44027887/article/details/102948182
  86. https://blog.csdn.net/qq_15159657/article/details/104721232
  87. https://blog.csdn.net/qq_15159657
  88. https://blog.csdn.net/qq_15159657/article/details/104721232
  89. https://blog.csdn.net/ALakers/article/details/111619137
  90. https://blog.csdn.net/ALakers
  91. https://blog.csdn.net/ALakers/article/details/111619137
  92. https://blog.csdn.net/weixin_42830697/article/details/102474659
  93. https://blog.csdn.net/weixin_42830697
  94. https://blog.csdn.net/weixin_42830697/article/details/102474659
  95. https://blog.csdn.net/kimol_justdo/article/details/108912073
  96. https://blog.csdn.net/kimol_justdo
  97. https://blog.csdn.net/kimol_justdo/article/details/108912073
  98. https://blog.csdn.net/
  99. https://blog.csdn.net/qq_27644127
 100. lxguang_tao
	https://blog.csdn.net/qq_27644127
 101. https://i.csdn.net/#/uc/profile?utm_source=14998968
 102. 暂无认证
	https://i.csdn.net/#/uc/profile?utm_source=14998968
 103. https://blog.csdn.net/blogdevteam/article/details/103478461
 109. https://im.csdn.net/chat/qq_27644127
 111. https://blog.csdn.net/qq_27644127/article/details/112987332
 112. https://blog.csdn.net/qq_27644127/article/details/112987332
 113. https://blog.csdn.net/qq_27644127/article/details/112987332
 114. https://blog.csdn.net/qq_27644127/article/details/111566657
 115. https://blog.csdn.net/qq_27644127/article/details/111566657
 116. https://blog.csdn.net/qq_27644127/article/details/111566657
 117. https://blog.csdn.net/qq_27644127/article/details/118380655
 118. https://blog.csdn.net/qq_27644127/article/details/118380655
 119. https://blog.csdn.net/qq_27644127/article/details/118380655
 120. https://blog.csdn.net/qq_27644127/category_10614803.html
 121. https://blog.csdn.net/qq_27644127/category_10614803.html
 122. https://blog.csdn.net/qq_27644127/category_10685120.html
 123. https://blog.csdn.net/qq_27644127/category_10685120.html
 124. https://blog.csdn.net/qq_27644127/article/details/112987332#comments_14757654
 125. https://blog.csdn.net/m0_50944918
 127. https://blog.csdn.net/qq_27644127/article/details/118380655
 128. https://blog.csdn.net/qq_27644127/article/details/111566657
 129. https://blog.csdn.net/qq_27644127/article/month/2021/07
 130. https://blog.csdn.net/qq_27644127/article/month/2020/12
 131. https://kunpeng-sc.csdnimg.cn/?timestamp=1623163941/#/preview/8608?positionId=57&queryWord=&spm=1001.2101.3001.5001
 132. https://kunpeng-sc.csdnimg.cn/?timestamp=1623163941/#/preview/8608?positionId=479&queryWord=&spm=1001.2101.3001.4834
 133. https://blog.csdn.net/qq_27644127/category_10614803.html
 134. https://blog.csdn.net/qq_27644127/category_10614803.html
 135. https://blog.csdn.net/qq_27644127/category_10685120.html
 136. https://blog.csdn.net/qq_27644127/category_10685120.html
 137. javascript:;
 139. https://i.csdn.net/#/wallet/balance/recharge
 140. https://i.csdn.net/#/wallet/balance/recharge![Image](./187fd2da45fcb4448f060830c830f812.png)![Image](./187fd2da45fcb4448f060830c830f812.png)
