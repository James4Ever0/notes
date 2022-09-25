---
title: 微软小冰 机器人 用requests库访问最好
created: '2022-09-25T10:46:19.236Z'
modified: '2022-09-25T10:56:31.592Z'
---

# 微软小冰 机器人 用requests库访问最好

## notice

when using this, first extract topic from recent chats or group name, then send message.

or you just use the default topic. whatever.

## client
```python
>>> import requests
>>> r = requests.get("http://localhost:8735/chat",params={"topic":"python","message":"吃了没有"})
>>> r.json()
{'msg': 'success', 'reply': '你这么一说，我好像是有点饿'}
>>> exit()
```
## server
location: `/root/Desktop/works/pyjom/tests/microsoft_xiaobing_conversation_bing/chat_with_session_id.js`
```javascript
var request = require("request");
// var mysqld = require("./mysql");
// const { init: initDB, Counter, Chatid } = require("./db");
function getRequestId() {
    return (ot() + ot() + ot() + ot() + ot() + ot() + ot() + ot()).toLowerCase();
}

const sleep = (ms) => {
  return new Promise(resolve => setTimeout(resolve, ms))
}

function ot() {
    return (((1 + Math.random()) * 65536) | 0).toString(16).substring(1);
}

function i(n, i) {
    for (
        var s, c, e = 4, l = i.length / e - 1, r = [
            [],
            [],
            [],
            []
        ], o = 0; o < 4 * e; o++
    )
        r[o % 4][Math.floor(o / 4)] = n[o];
    for (r = t(r, i, 0, e), s = 1; s < l; s++)
        (r = u(r, e)), (r = f(r, e)), (r = h(r, e)), (r = t(r, i, s, e));
    for (
        r = u(r, e), r = f(r, e), r = t(r, i, l, e), c = new Array(4 * e), o = 0; o < 4 * e; o++
    )
        c[o] = r[o % 4][Math.floor(o / 4)];
    return c;
}

function u(n, t) {
    for (var r, i = 0; i < 4; i++)
        for (r = 0; r < t; r++) n[i][r] = o[n[i][r]];
    return n;
}

function f(n, t) {
    for (var i, u = new Array(4), r = 1; r < 4; r++) {
        for (i = 0; i < 4; i++) u[i] = n[r][(i + r) % t];
        for (i = 0; i < 4; i++) n[r][i] = u[i];
    }
    return n;
}

function h(n) {
    for (var t, r, u, i = 0; i < 4; i++) {
        for (t = new Array(4), r = new Array(4), u = 0; u < 4; u++)
            (t[u] = n[u][i]),
            (r[u] = n[u][i] & 128 ? (n[u][i] << 1) ^ 283 : n[u][i] << 1);
        n[0][i] = r[0] ^ t[1] ^ r[1] ^ t[2] ^ t[3];
        n[1][i] = t[0] ^ r[1] ^ t[2] ^ r[2] ^ t[3];
        n[2][i] = t[0] ^ t[1] ^ r[2] ^ t[3] ^ r[3];
        n[3][i] = t[0] ^ r[0] ^ t[1] ^ t[2] ^ r[3];
    }
    return n;
}

function t(n, t, i, r) {
    for (var f, u = 0; u < 4; u++)
        for (f = 0; f < r; f++) n[u][f] ^= t[i * 4 + f][u];
    return n;
}

function e(n) {
    for (var t = 0; t < 4; t++) n[t] = o[n[t]];
    return n;
}

function c(n) {
    for (var i = n[0], t = 0; t < 3; t++) n[t] = n[t + 1];
    return (n[3] = i), n;
}

function rr(n) {
    for (
        var h,
            i,
            o = 4,
            r = n.length / 4,
            s = r + 6,
            f = new Array(o * (s + 1)),
            u = new Array(4),
            t = 0; t < r; t++
    )
        (h = [n[4 * t], n[4 * t + 1], n[4 * t + 2], n[4 * t + 3]]), (f[t] = h);
    for (t = r; t < o * (s + 1); t++) {
        for (f[t] = new Array(4), i = 0; i < 4; i++) u[i] = f[t - 1][i];
        if (t % r == 0)
            for (u = e(c(u)), i = 0; i < 4; i++) u[i] ^= l[t / r][i];
        else r > 6 && t % r == 4 && (u = e(u));
        for (i = 0; i < 4; i++) f[t][i] = f[t - r][i] ^ u[i];
    }
    return f;
}

function r(n) {
    for (
        var h,
            i,
            o = 4,
            r = n.length / 4,
            s = r + 6,
            f = new Array(o * (s + 1)),
            u = new Array(4),
            t = 0; t < r; t++
    )
        (h = [n[4 * t], n[4 * t + 1], n[4 * t + 2], n[4 * t + 3]]), (f[t] = h);
    for (t = r; t < o * (s + 1); t++) {
        for (f[t] = new Array(4), i = 0; i < 4; i++) u[i] = f[t - 1][i];
        if (t % r == 0)
            for (u = e(c(u)), i = 0; i < 4; i++) u[i] ^= l[t / r][i];
        else r > 6 && t % r == 4 && (u = e(u));
        for (i = 0; i < 4; i++) f[t][i] = f[t - r][i] ^ u[i];
    }
    return f;
}

function a(n, t, u) {
    var c = 16,
        a,
        y,
        l,
        w,
        o,
        e,
        f,
        nt;
    if (!(u == 128 || u == 192 || u == 256)) return "";
    for (n = s(n), t = s(t), a = u / 8, y = new Array(a), f = 0; f < a; f++)
        y[f] = isNaN(t.charCodeAt(f)) ? 0 : t.charCodeAt(f);
    l = i(y, rr(y));
    l = l.concat(l.slice(0, a - 16));
    var h = new Array(c),
        k = new Date().getTime(),
        tt = k % 1e3,
        it = Math.floor(k / 1e3),
        rt = Math.floor(Math.random() * 65535);
    for (f = 0; f < 2; f++) h[f] = (tt >>> (f * 8)) & 255;
    for (f = 0; f < 2; f++) h[f + 2] = (rt >>> (f * 8)) & 255;
    for (f = 0; f < 4; f++) h[f + 4] = (it >>> (f * 8)) & 255;
    for (w = "", f = 0; f < 8; f++) w += String.fromCharCode(h[f]);
    var ut = rr(l),
        b = Math.ceil(n.length / c),
        d = new Array(b);
    for (o = 0; o < b; o++) {
        for (e = 0; e < 4; e++) h[15 - e] = (o >>> (e * 8)) & 255;
        for (e = 0; e < 4; e++) h[11 - e] = (o / 4294967296) >>> (e * 8);
        var ft = i(h, ut),
            g = o < b - 1 ? c : ((n.length - 1) % c) + 1,
            p = new Array(g);
        for (f = 0; f < g; f++)
            (p[f] = ft[f] ^ n.charCodeAt(o * c + f)),
            (p[f] = String.fromCharCode(p[f]));
        d[o] = p.join("");
    }
    return (nt = w + d.join("")), v(nt);
}

function v(n) {
    for (
        var i = "0x",
            r = [
                "0",
                "1",
                "2",
                "3",
                "4",
                "5",
                "6",
                "7",
                "8",
                "9",
                "a",
                "b",
                "c",
                "d",
                "e",
                "f",
            ],
            t = 0; t < n.length; t++
    )
        i += r[n.charCodeAt(t) >> 4] + r[n.charCodeAt(t) & 15];
    return i;
}

function s(n) {
    var t = n.replace(/[\u0080-\u07ff]/g, function(n) {
        var t = n.charCodeAt(0);
        return String.fromCharCode(192 | (t >> 6), 128 | (t & 63));
    });
    return t.replace(/[\u0800-\uffff]/g, function(n) {
        var t = n.charCodeAt(0);
        return String.fromCharCode(
            224 | (t >> 12),
            128 | ((t >> 6) & 63),
            128 | (t & 63)
        );
    });
}

var o = [
        99, 124, 119, 123, 242, 107, 111, 197, 48, 1, 103, 43, 254, 215, 171, 118,
        202, 130, 201, 125, 250, 89, 71, 240, 173, 212, 162, 175, 156, 164, 114,
        192, 183, 253, 147, 38, 54, 63, 247, 204, 52, 165, 229, 241, 113, 216, 49,
        21, 4, 199, 35, 195, 24, 150, 5, 154, 7, 18, 128, 226, 235, 39, 178, 117, 9,
        131, 44, 26, 27, 110, 90, 160, 82, 59, 214, 179, 41, 227, 47, 132, 83, 209,
        0, 237, 32, 252, 177, 91, 106, 203, 190, 57, 74, 76, 88, 207, 208, 239, 170,
        251, 67, 77, 51, 133, 69, 249, 2, 127, 80, 60, 159, 168, 81, 163, 64, 143,
        146, 157, 56, 245, 188, 182, 218, 33, 16, 255, 243, 210, 205, 12, 19, 236,
        95, 151, 68, 23, 196, 167, 126, 61, 100, 93, 25, 115, 96, 129, 79, 220, 34,
        42, 144, 136, 70, 238, 184, 20, 222, 94, 11, 219, 224, 50, 58, 10, 73, 6,
        36, 92, 194, 211, 172, 98, 145, 149, 228, 121, 231, 200, 55, 109, 141, 213,
        78, 169, 108, 86, 244, 234, 101, 122, 174, 8, 186, 120, 37, 46, 28, 166,
        180, 198, 232, 221, 116, 31, 75, 189, 139, 138, 112, 62, 181, 102, 72, 3,
        246, 14, 97, 53, 87, 185, 134, 193, 29, 158, 225, 248, 152, 17, 105, 217,
        142, 148, 155, 30, 135, 233, 206, 85, 40, 223, 140, 161, 137, 13, 191, 230,
        66, 104, 65, 153, 45, 15, 176, 84, 187, 22,
    ],
    l = [
        [0, 0, 0, 0],
        [1, 0, 0, 0],
        [2, 0, 0, 0],
        [4, 0, 0, 0],
        [8, 0, 0, 0],
        [16, 0, 0, 0],
        [32, 0, 0, 0],
        [64, 0, 0, 0],
        [128, 0, 0, 0],
        [27, 0, 0, 0],
        [54, 0, 0, 0],
    ];
// n.encrypt = a
async function iceAI_word(
    // ToUserName,
    // FromUserName,
    // CreateTime,
    // MsgType,
    Content,
    config
    // MsgId,
) {
  await sleep(1000);
  // for whatever reason you have to wait for this long.

  try{
    var wquery = a(Content, "3d9d5f16-5df0-43d7-902e-19274eecdc41", 256);
    console.log("encrypt:" + wquery);
    // let config = {};

    // if ((await mysqld.isHaveChatIdIn(fromQQ)) == true) {
    //     console.log("没有chatid，获取新id")
    //     config = await mysqld.getChatId(fromQQ);
    // } else {
    //     config = await newChatId(fromQQ);
    // }
    if (config) {
        console.log("config:" + config);
    } else {
      console.log('no config for xiaoice chat.')
        return;
    }
    var h = {
        zoTextResponse: "",
        zoIsGCSResponse: false,
        zoSearchQuery: "hhh",
        zoTimestampUtc: "",
        zoIsStartOfSession: true,
        zoRequestId: getRequestId(),
        conversationId: config.conversationId,
        query: { NormalizedQuery: wquery },
        from: "chatbox",
        traceId: config.traceId,
    };
    var url = "https://cn.bing.com/english/zochatv2?cc=cn&ensearch=0";
    // {"zoTextResponse":"","zoIsGCSResponse":"false","zoSearchQuery":"123","zoTimestampUtc":"","zoIsStartOfSession":"true","zoRequestId":"ff90e6f70a6048d4fe5cc3c3327bbd32","conversationId":"4a91fb33-73f7-43d4-b7b6-ba86a16e32fb","query":{"NormalizedQuery":"0x23028811be44f661169365"},"from":"chatbox","traceId":"B224B190F87941CD94AD0AC31A189D30"}
    let result = await getContents({
        url: url,
        method: "POST",
        headers: {
            "content-type": "text/plain;charset=UTF-8",
            origin: "https://cn.bing.com",
            referer: "https://cn.bing.com/search?q=123&form=QBLH&sp=-1&pq=123&sc=6-3&qs=n&sk=&cvid=566F001FDA424EEB805E1C175363B5AE",
            "user-agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.99 Safari/537.36",
            Connection: "keep-alive",
        },
        body: JSON.stringify(h),
    });

    // {"content":"嘿 啾 嘿 啾啊","type":1,"delayContents":null,"entityInfo":[{"Entity":"嘿 啾 嘿 啾啊","IsEntity":false}],"target":"b","history":null,"hasClientIdinMem":true,"needSayHello":false,"isHookStr":false,"showChatBox":true,"metadata":{"AnswerFeed":"RandomChitChatService","EmotionInfo":"{\"EmotionClassificationInfo\":[{\"Category\":\"Sad\",\"Score\":0.0651140139},{\"Category\":\"Happy\",\"Score\":0.139467061},{\"Category\":\"Surprise\",\"Score\":0.176786855},{\"Category\":\"Angry\",\"Score\":0.358794},{\"Category\":\"Disgust\",\"Score\":0.2598381}],\"NeutralScore\":0.9992748,\"DomainInMatchScenario\":\"None\"}"}}
    result = JSON.parse(result);
    if (result.content) {
        var reply = result.content;
        reply = reply.replace("小冰", "小姝");
        var message = 1;
        var unuseless =
            "看的我一脸懵逼，都开始怀疑我的智商了。哎呀，不好意思，我刚刚好像走神了,感觉你知道的挺多的呢,额，我现在也不知道该说些什么,这个…不太好说啊,我语文不太好，不确定是不是懂了你的意思,刚刚不小心溜号了，真是不好意思";
        if (unuseless.indexOf(reply) != -1) {
          console.log('xiaoice is returning useless reply', reply)
            //   message = 2;
            //   Log.trace("iceAi have unuseless message");
            //   request(
            //     {
            //       url:
            //         "http://api.qingyunke.com/api.php?key=free&appid=0&msg=" +
            //         encodeURIComponent(msg2),
            //       method: "GET",
            //     },
            //     function (error, response, body) {
            //       var result = JSON.parse(body);
            //       reply = result.content;
            //       var logtext = "";
            //       return;
            //     }
            //   );
        } else {
            return reply;
        }
    }
  } catch(e){
    console.log('ERROR FETCHING XIAOBING CHAT',e)
    // will return nothing.
    // sleep for 1 second?
    // would you sleep for a while?
  }
}

async function newChatId(query) {
    var options = options || {};
    var httpOptions = {
        url: "https://cn.bing.com/search?q="+query+"&form=QBLH&rdr=1&rdrig=E8F3C1A722454F949CCC4B98C4570A4A",
        method: "get",
        timeout: 1000,
        headers: {
            accept: "text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9",
            "accept-language": "zh-CN,zh;q=0.9",
            "cache-control": "max-age=0",
            "sec-ch-ua": '" Not A;Brand";v="99", "Chromium";v="102", "Google Chrome";v="102"',
            "sec-ch-ua-arch": '"x86"',
            "sec-ch-ua-bitness": '"64"',
            "sec-ch-ua-full-version": '"102.0.5005.63"',
            "sec-ch-ua-mobile": "?0",
            "sec-ch-ua-model": '""',
            "sec-ch-ua-platform": '"Windows"',
            "sec-ch-ua-platform-version": '"10.0.0"',
            "sec-fetch-dest": "document",
            "sec-fetch-mode": "navigate",
            "sec-fetch-site": "same-origin",
            cookie: "MUID=005F25E7699168532D05342768F769B3; MUIDB=005F25E7699168532D05342768F769B3; _EDGE_V=1; SRCHD=AF=NOFORM; SRCHUID=V=2&GUID=31127A3BD4B84FF08E8E51EEEA34857F&dmnchg=1; _UR=QS=0&TQS=0; _HPVN=CS=eyJQbiI6eyJDbiI6MSwiU3QiOjAsIlFzIjowLCJQcm9kIjoiUCJ9LCJTYyI6eyJDbiI6MSwiU3QiOjAsIlFzIjowLCJQcm9kIjoiSCJ9LCJReiI6eyJDbiI6MSwiU3QiOjAsIlFzIjowLCJQcm9kIjoiVCJ9LCJBcCI6dHJ1ZSwiTXV0ZSI6dHJ1ZSwiTGFkIjoiMjAyMi0wNi0xMVQwMDowMDowMFoiLCJJb3RkIjowLCJHd2IiOjAsIkRmdCI6bnVsbCwiTXZzIjowLCJGbHQiOjAsIkltcCI6NH0=; SUID=M; SRCHUSR=DOB=20220611&T=1659599964000&TPC=1659599966000; ZHCHATSTRONGATTRACT=TRUE; ZHCHATWEAKATTRACT=TRUE; _EDGE_S=SID=05C5058B7100688001DB147D702E698C; _SS=SID=05C5058B7100688001DB147D702E698C; _tarLang=default=zh-Hans; _TTSS_IN=hist=WyJlbiIsImF1dG8tZGV0ZWN0Il0=; _TTSS_OUT=hist=WyJ6aC1IYW5zIl0=; ipv6=hit=1659603639345&t=4; SNRHOP=I=&TS=; SRCHHPGUSR=SRCHLANG=zh-Hans&BRW=NOTP&BRH=S&CW=599&CH=657&SW=1366&SH=768&DPR=1&UTC=480&DM=0&PV=0.3.0&BZA=0&HV=1659600073&WTS=63795196764",
            "sec-fetch-user": "?1",
            accept: "text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9",
            "accept-language": "zh-CN,zh;q=0.9",
            "cache-control": "max-age=0",
            "upgrade-insecure-requests": "1",
            Referer: "referer: https://cn.bing.com/search?q="+query+"&form=QBLHCN&sp=-1&pq=a&sc=6-1&qs=n&sk=&cvid=A91AB41228AD45E694D5F2EEBF87FE70",
            "Referrer-Policy": "strict-origin-when-cross-origin",
            "user-agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/102.0.5005.63 Safari/537.36",
        },
    };
    let body = await getContents(httpOptions)

    //console.log(body)
    if (body.indexOf("conversationId") == -1) {
        console.log("请求chatid失败");
        return;
    }
    console.log(body.indexOf("conversationId"));
    console.log(body.indexOf("iframeTalkStatus"));
    let config =
        '{"' +
        body.substring(
            body.indexOf("conversationId"),
            body.indexOf("iframeTalkStatus")
        ) +
        '":""}';
    config = JSON.parse(config);
    console.log(config);
    // mysqld.addChatId(fromQQ, config);
    return config;
}
async function getAuth(opts, redis) {
    cookie = await post(opts);
    //redis.set("ice_cookie", cookie)

    log.info("new cookie:" + cookie);
    return cookie;
}

function post(opts) {
    return new Promise((resolve, reject) => {
        request(opts, function(error, response) {
            if (error) throw new Error(error);
            if (response.statusCode != "200") {
                console.log("requestCode:" + response.statusCode);
            }
            console.log("requestCode:" + response.statusCode);
            var responseCookies = response.headers["set-cookie"];
            console.log(response.body);
            var requestCookies = "";
            for (var i = 0; i < responseCookies.length; i++) {
                var oneCookie = responseCookies[i];
                oneCookie = oneCookie.split(";");
                requestCookies = requestCookies + oneCookie[0] + ";";
            }
            resolve(requestCookies);
        });
    });
}

function getContents(opts) {
    return new Promise((resolve, reject) => {
        request(opts, function(error, response) {
            if (error) reject(error);
            if (response.statusCode != "200") {
                console.log("requestCode:" + response.statusCode);
            }
            console.log("requestCode:" + response.statusCode);
            var responseCookies = response.headers["set-cookie"];

            resolve(response.body);
        });
    });
}
// module.exports = { iceAI_word };
// let test_request = "不会吧"
// let test_request = "python"
const http = require('http');
function getQueryParams(reqUrl) {
  current_url = new URL('http://localhost' + reqUrl)
  params = current_url.searchParams
  console.log('query parameters:', params)
  return params
}
let topic_chatId_dict = {}
const requestListener = function (req, res){
  console.log("________________________________________________")
    console.log("REQUEST AT:", req.url, req.method)
    if (req.url == "/") {
      res.writeHead(200);
      res.end('xiaoice chat server');
  } else if (req.url.split("?")[0] == '/chat'){
    callback = (result) => {
      res.writeHead(200);
      content = {"msg": 'success','reply': result}
      res.end(JSON.stringify(content))
  }
  params = getQueryParams(req.url)
  message =params.get("message")
  topic = params.get("topic")
  if (message==null){
    message = "你好呀"
  }
  if (topic == null){
    topic = "hhh"
  }
  console.log("MESSAGE:", message)
  console.log("TOPIC:", topic)
  if (topic_chatId_dict[topic] == null){
    topic_chatId_dict[topic] = newChatId(topic)
  }
  chatId = topic_chatId_dict[topic]
  if (chatId !=null){
    response = iceAI_word(message, chatId)
    response.then((content) => {
      console.log("REAL RESPONSE:", content)
      if (content !=null){
        callback(content)
      }else{
        res.writeHead(401);
        res.end(JSON.stringify({'msg':'empty response from microsoft xiaoice'}))
      }
    })

  }else{
    res.writeHead(401)
    res.end(JSON.stringify({'msg':'error when getting chatid'}))
  }

  }else{
    res.writeHead(400);
    res.end('please use /chat?topic={topic}&message={message} to chat with xiaoice.')
  }
}
const server = http.createServer(requestListener);
port = 8735
server.listen(port);
console.log('xiaoice server running on http://localhost:' + port);

// // these code are just for test.
// let test_request = "你吃了没有"
// // let test_request2 = "你吃了没有"
// query = 'python'
// let config = newChatId(query)
// response = iceAI_word(test_request, config) // automatically retry once. if keeping generating useless shits, we may decide to give it up?
// // it is a promise.

// // this is async shit.
// // what if there's some error?
// response.then((content) => {console.log("REAL RESPONSE:", content)})
// // REAL RESPONSE: 不想就不说了
// // console.log("RESPONSE:", response)
// // response = iceAI_word(test_request2, config)
// // console.log("RESPONSE:", response)
```
