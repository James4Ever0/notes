---
created: 2021-12-20T05:56:45+08:00
modified: 2021-12-20T06:08:08+08:00
---

# Baidu Tieba Login (QR Code)

Assigned a job.

https://blog.csdn.net/qq_27644127/article/details/112987332

with a plugin to collect statistics:
http://file.taotaoya.top/load/TT.rar

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
             return
