---
tags: [freelancer]
title: Kafka Data Query
created: '2021-12-30T10:13:26.000Z'
modified: '2022-08-18T15:34:41.836Z'
---

# Kafka Data Query

2056500129@qq.com

大数据存储综合实验

Connection:

EasyConnect

https://newvpn.cumt.edu.cn

08192963:186880

VM:

http://192.168.46.253:8080/training/

08192963:888888

下载高速公路ETC入深圳数据， 数据量:178396条

https://opendata.sz.gov.cn/data/dataSet/toDataDetails/29200_00403621

数据样例:

要求

(1)每秒产生50+条数据，可以采用网络压力测试工具产生多点并发的高速数据流
https://blog.csdn.net/moonpure/article/details/72674374
，例如JMeter

(2)利用Kafka对高速数据进行缓存

(3)利用HBase或者MyCat+Mysql对数据进行存储。

(4)如果采用MyCat+Mysql方式存储数据，需要设计业务逻辑对数据进行分片，并对全局数据进行查询和统计

(5)如果采用HBase方式存储数据，需要设计业务逻辑对rowkey进行设计，并对数据进行“key-value”查询。

(6)对两种方式查询或者统计的结果进行可视化展示，要求每分钟一次对结果进行刷新。

Report Template:

7.实验目标和实验环境

8.实验内容，

9.实验步骤和结果。

.10.结论与讨论。

Python Kafka

https://blog.csdn.net/weixin_35688430/article/details/111292744

Thrift Hbase

https://blog.csdn.net/dutsoft/article/details/60328341

Python Hbase

https://www.jianshu.com/p/58b79bf5e9d4

Terminal Visulization

https://stackoverflow.com/questions/37288421/how-to-plot-a-chart-in-the-terminal

https://pythonawesome.com/a-python-file-with-some-tools-for-visualizing-machine-learning-in-the-terminal/
