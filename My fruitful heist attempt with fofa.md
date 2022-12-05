---
created: 2022-11-29T16:50:57+08:00
modified: 2022-12-05T17:48:05+08:00
---

# My fruitful heist attempt with fofa

Fofa api requires membership. I don't want to enroll.

You first test on your vulnerable machine/app, develop scanner, exploiter and listener, then mass exploit to millions.

All recorded here: `hack_all_the_thing/tests/get_log4j_vuln`

[zoomeye search for log4j](https://www.zoomeye.org/searchResult?q=log4j2&page=2&pageSize=20)

[seebug](https://www.seebug.org)

[shodan query for log4j2 (or anything)](https://www.shodan.io/search?query=log4j2)

[狮子鱼团购 fofa查询漏洞](https://blog.csdn.net/sinat_36001828/article/details/117729361?spm=1001.2101.3001.6650.2&utm_medium=distribute.wap_relevant.none-task-blog-2~default~CTRLIST~Rate-2-117729361-blog-121949437.wap_blog_relevant_default&depth_1-utm_source=distribute.wap_relevant.none-task-blog-2~default~CTRLIST~Rate-2-117729361-blog-121949437.wap_blog_relevant_default)

[Sqlmap post data inject](https://hackertarget.com/sqlmap-post-request-injection/)

To generate password dictionary without oom: `itertools.product(chrs, repeat=r)`

[search log4j2 in browser after login](https://fofa.info/result?qbase64=YXBwPSJMb2c0ajIi&page=2&page_size=10)

[info page of my first target](https://fofa.info/hosts/121.199.46.85) (login first!)

[fofa usage examples](https://zhuanlan.zhihu.com/p/460403187?utm_id=0)

[My first target login page](http://121.199.46.85:8888/admin/mylogin)

[gov site?](https://zww.gzjd.gov.cn/spa/spa/sdms?code=_PX5ips91MzPkvJJg--sfxzDdwAh0BDrBYbxPVSDXb8&state=STATE)

[Bing-upms](https://gitee.com/xiaobingby/bing-upms/tree/master/src/test/java/com/xiaobingby) the system used by my first target

[password dictionary topic in github](https://github.com/topics/password-dictionaries)
