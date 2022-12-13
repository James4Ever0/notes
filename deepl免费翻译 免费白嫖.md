---
title: deepl免费翻译 免费白嫖
created: '2022-09-06T08:52:42.837Z'
modified: '2022-12-13T16:14:00.281Z'
---

# deepl免费翻译 免费白嫖

heroku no longer provides free tiers (dyno)

change ip frequently by using proxychains and clash

RELEASES STILL VISIBLE [HERE](https://github.com/zu1k/removed-2022-07-12/releases/tag/0.1.2)

you can google for it. maybe the internet archive has it.
`https://github.com/zu1k/deepl-api-rs/releases/download/0.1.2/deepl-aarch64-unknown-linux-musl-0.1.2.gz`
`https://github.com/zu1k/deepl-api-rs/releases/download/0.1.2/deepl-x86_64-unknown-linux-musl-0.1.2.gz`
for other triplets i am not so familiar so i cannot guess that out.

从[zu1k的文章](https://zu1k.com/posts/)来看 应该是搞安全的

为了更准确的翻译， deepl的API是很重要的
但是这个deepl却不让免费用 网页端的js复杂的要死

deepl的客户端的现在分为3类：
- 免费 自动操控浏览器
- 付费 申请api
- 免费 破解交互协议

为了连续使用deepl以及其他可能会封ip的翻译软件 使用clash做代理是很关键的 如何找到好的代理 zu1k有[proxypool](https://github.com/zu1k/proxypool)可以自动爬取代理 同时推荐大佬的[proxypool](https://github.com/Python3WebSpider/ProxyPool) 据说是专业爬虫架构

zu1k本人下架了deepl的docker镜像 但是release现在居然还可以下载 只不过不可以直接访问页面罢了

zu1k的[copy translator](https://github.com/zu1k/copy-translator)连接的应该就是他自己写的[deepl-rust服务器](https://deepl.zu1k.com/translate) 只不过现在没法访问了 (话说大佬没事翻译个啥又不是看不懂 hhh) 历史的release版本中有连接本地的版本 估计也没有开源原来的docker破解deepl的二进制

[deeplx](https://deeplx.herokuapp.com/)在 heroku上面运行 目前应该不能正常运行 它的ip感觉是被封了 [它的仓库](https://github.com/devockr/deeplx)用的是现在没法访问的deepl的docker镜像


有人（很可能就是zu1k）破解了deepl客户端的交互逻辑 应该是windows的deepl协议（c#好破解 没加壳） 现在可以[看看是如何破解的](https://mp.weixin.qq.com/s?__biz=MzI3NTEwOTA4OQ==&mid=2649181781&idx=1&sn=3591257c389292ed139692637181e70a&chksm=f31a2bdbc46da2cdf4e01b9f663eae934b53fcdb256193b8db0662a41522a31c8af6bca034d3&scene=126&&sessionid=0)

-----------------------

安全不仅仅是一门朴素的学问，更是一门权衡的艺术。有时一个简单的设计可以规避掉大多数攻击问题，下面分享一篇在网上看到的DeepL API的反爬设计。

这篇博文本应该在去年完成 DeepL 客户端逆向的时候发布，但考虑到相关细节一旦公开，恐怕会被广泛采用而被 DeepL 官方封杀，因此迟迟未开始。前段时间我发布了 DeepL Free Api 的 Docker 镜像，也在 GitHub 上公开了相关二进制程序，就下载量来看已经有不少人在使用了，相信 DeepL 不久就会有动作，因此我认为现在已经可以公开相关细节。

我逆向的是 DeepL 的 Windows 客户端，因为是 C# 开发依附于 .net，也未进行任何混淆和加壳，可以轻松逆出源码。通过前段时间与一些其他研究者交流，我认为已经有不少感兴趣的同学也进行了逆向，也许是一种默契，都害怕 DeepL 在发觉后进行修改，所以大家也都没有对外公开，目前网络中搜不到任何相关的内容。本文的目的是给相关小伙伴一点思路，不过希望大家还是不要直接公开代码，以继续欺骗 DeepL，让其相信还没有人发现他们的把戏。

在我实现 DeepL Free Api 的过程中，我发现 DeepL 并没有像之前见到的一些接口设计那样，通过签名等手段来避免接口滥用，相反，他们使用了一些欺骗战术来混淆视听，从而尝试让抓包分析者放弃，本文将围绕此进行讨论。

过程
进入研究生阶段，为了方便阅读论文，为自己开发了划词翻译工具，在众多翻译引擎中 DeepL 的效果尤为出色。DeepL 官方的 Api 需要绑定信用卡进行认证，但其并未在中国大陆经营业务，所以并不支持国内的信用卡。我也尝试过从淘宝购买别人用国外信用卡认证过的帐号，价格贵不说，在没有滥用的情况下，DeepL 在两个月内封禁了我的帐号，因此我决定用一些其他手段。

考虑到 DeepL 有提供免费版本的翻译服务，支持 Web，Windows、Android 和 iOS 都有相应的客户端，我便想使用这些客户端使用的免费接口。不出所料，在广泛使用打包和混淆技术的当下，DeepL 的 Web 端 js 代码也不是人看的东西，但通过简单的抓包，我发现其接口参数非常清晰，根本没有额外的签名、token等认证技术，我觉得自己又行了，几行 Python 代码便完成了接口对接工作。

但测试下来，我发现当修改翻译内容，有极大概率遇到 429 Too many requests，并且一旦出现 429，后续的所有请求便都是 429 了。
```json
{
    "jsonrpc": "2.0",
    "error":{
        "code":1042902,
        "message":"Too many requests."
    }
}
```

在 GitHub 搜索之后，我发现已经有前人尝试利用过 DeepL 的免费接口了，早在 2018 年他们就已经遇到了这个 429 问题，并且到现在都没有解决。

我尝试转向客户端的免费接口，苹果设备可以轻松 MITM，于是我便在 iPad 上对 DeepL 客户端进行抓包，让我意想不到的是，客户端的请求竟然比 Web 端的简单不少，接口参数数量仅有必须的几个，非常有利于利用。于是我又觉得自己行了，两三行 Python 代码完成接口对接。

简单测试，我又傻眼了。伪造的请求明明跟客户端发起的完全相同，但只要一更换翻译的内容，返回马上就变成 429。干！我都开始怀疑自己了。
```json
{
    "jsonrpc": "2.0",
    "method": "LMT_handle_texts",
    "params": {
        "texts": [{
            "text": "translate this, my friend"
        }],
        "lang": {
            "target_lang": "ZH",
            "source_lang_user_selected": "EN",
        },
        "timestamp": 1648877491942
    },
    "id": 12345,
}
```
你自己看看，这个接口多么清楚明白，但怎么就伪造不了呢？

我想了又想，这里面也就 id 比较可疑，因为这个参数我不知道它是怎么生成的，是随机的还是根据某种规则计算出来的，我们无从知道。但从目前结果来看，随机的 id 无法被服务器认可。

当然，我也考虑过其他的服务端判断滥用的方法，例如某些 http 头、ssl 层面的方法（例如之前 Go 实现中 SSL 协商过程中加密算法的顺序等），我也想办法进行了伪造，可就是不行。疲惫了，不想搞了。

第二天，突然想起他的 Windows 客户端，稍微一分析惊喜的发现是 C#，还没加壳，果断扔进 dnSpy，发现也没混淆，真是柳暗花明又一村啊。分析之后，也就一切都清楚明白了，原来 DeepL 根本一开始就在想方设法让你觉得你行啊。

看前面那个接口的参数，我之所以觉得我行，就是因为这个接口它太简单了。接口的参数少，参数含义又非常明确，它并不像某些厂那样用一些不知所以然的缩写，这里的每一个参数，它的名称都在告诉我它的含义、它是干什么的以及它是怎么生成的。

jsonrpc 是版本号，method 是方法，一个固定的字符串。params 里面 texts 是多段待翻译的文本，lang 里面是翻译的语言选项，是枚举类型。timestamp 是 UNIX 风格的时间戳，id 就是序号。大眼一看，这里面只有 id 是最可疑的，这也确实是我最初犯的错误。

真相 现在我来告诉你，DeepL 到底是怎么认证的。（下面并不是 DeepL 客户端的代码，是我写的 Rust 利用代码，但逻辑不变）

```rust
fn gen_fake_timestamp(texts: &Vec<String>) -> u128 {
    let ts = tool::get_epoch_ms();
    let i_count = texts
            .iter()
            .fold(
                1, 
                |s, t| s + t.text.matches('i').count()
            ) as u128;
    ts - ts % i_count + i_count
}
```

哈哈！没想到吧！人家的时间戳不是真的！

DeepL 先计算了文本中所有 i 的数量，然后对真正的时间戳进行一个小小的运算 ts - ts % i_count + i_count，这个运算差不多仅会改变时间戳的毫秒部分，这个改变如果用人眼来验证根本无法发现，人类看来就是一个普通的时间戳，不会在意毫秒级的差别。

但是 DeepL 拿到这个修改后的时间戳，既可以与真实时间对比(误差毫秒级)，又可以通过简单的运算（是否是 i_count 的整倍数）判断是否是伪造的请求。真是精妙啊！

还有更绝的！你接着看：

```rust
let req = req.replace(
    "\"method\":\"",
    if (self.id + 3) % 13 == 0 || (self.id + 5) % 29 == 0 {
        "\"method\" : \""
    } else {
        "\"method\": \""
    },
);
```

怎么样？我觉得我一开始就被玩弄了，人家的 id 就是纯粹的随机数，只不过后续的请求会在第一次的随机 id 基础上加一，但是这个 id 还决定了文本中一个小小的、微不足道的空格。

按照正常的思路，为了方便人类阅读和分析，拿到请求的第一时间，我都会先扔编辑器里格式化一下 Json，我怎么会想到，这恰恰会破坏掉人家用来认证的特征，因此无论我如何努力都难以发现。

总结
在我以往的经验中，接口防滥用，要不就是用户专属的 token，要不就是对请求进行签名或者加密，这些对抗滥用的方法都是明面上的，就是明白告诉你我有一个签名，怎么签的，你去分析去吧，但是我代码混淆了，你看看你是要头发还是要算法。

要不就是高级点的，更具技术性的，利用某些客户端特有的实现造成的特征进行认证，我印象中最深刻的就是 Go 的 SSL 协商过程中的算法顺序。这类方法要求更高的技术，当然分析起来也肯定更加困难，并且找到这样一种方法本身也不容易。

从 DeepL 的方法中，我找到了另外一种思路。利用人心理的弱点，一开始让其感觉非常简单，但是无论如何都无法得到想要的结果，给分析者造成心理上的打击和自我怀疑，让其浅尝辄止自行放弃分析。同时利用人行为上的惯式，使其自行破坏掉某些关键信息，从而给分析造成难以发现的阻碍。

原来，除了技术以外，还有这样一条道路啊，真是有趣！


