---
created: 2022-04-28T10:22:06+08:00
modified: 2022-04-30T23:15:37+08:00
---

# gpt-2 ram requirements

for monsterious models, distributed training in pytorch, or deepspeed, fairscale is needed. no single gpu is able to hold gpt3-175B at once.

https://github.com/EleutherAI/gpt-neox
https://www.eleuther.ai

need p40/m40 which has 24gb vram. need at least 60gb ram to load model.

using low ram devices need library like deepspeed, bminf or megengine.

you can also use others provided web services.

can use colab/kaggle or aistudio to do the job. paid training enviorment is also avaliable.

https://github.com/TsinghuaAI/CPM-1-Generate
https://github.com/arrmansa/Basic-UI-for-GPT-J-6B-with-low-vram
https://pythonawesome.com/finetune-gpt2-xl-and-gpt-neo-on-a-single-gpu-with-huggingface-transformers-using-deepspeed
https://github.com/OpenBMB/BMInf

web api for chinese plug:
https://m.nlp.aliyun.com/mportal#/textGenerate

NVIDIA Tesla M40  24G 专业运算 英伟达 图形GPU加速深度学习显卡

提供魔改教程，需要一张亮机卡，用丽台K600当亮机卡就行，魔改后可用此卡打游戏

散热器可看图片，用3D打印散热风道，加上风扇就能用了

虚拟化 用这些卡 K1 K2 K340 K520（不需要授权） M60 P4 P10 P100 T4 RTX6000 RTX8000 V100 RTXA6000 P40 （需要授权）

虚拟化 VGPU 有两种模式 一种是VPC 适合普通办公 一种是VDWS 适合专业图形应用 然后P40两种模式都支持

购买之前先了解以下信息（您必须了解）：

1、电源供电有没有8针供电；

2、普通台式机X99以上主板，DDR4内存；

3、主板要支持多显卡显示；

4、建议电源功率在600W以上；

5、机箱内的空间是否足够（卡宽双挡片位置，卡长度28~30cm）

6、普通台式机需要加装主动散热，服务器可以选择被动散热

7、先查看主板bios的pcie设置里面有没有above 4g选项

超微服务器原装拆机 成色超新 测试好发货

显卡安装
打开App



YaquePeng
关注
普通台式机上Tesla M40显卡paddleGPU深度学习柯南的变身器上机体验 原创
2021-11-26 22:01:35
 2点赞
 
YaquePeng  

码龄8年

关注
Tesla M40显卡上机体验
废话
正文
改电源线
放入显卡准备散热工具
尝试开机
开装驱动
cuda行列
paddlepaddlegpu版安装
上大佬的柯南变声器代码
本地运行
实测效果
提醒
购机需谨慎
免责声明
总结
改善
引导
废话
最近在paddlepaddle溜达，看到了柯南变身器，于是从aistudio下载到本地玩，单位的1060 6G版显卡，跑起来，语句一场就不行，遂上淘宝，咸鱼溜达一圈，见到了tesla k80 m40等一系列的卡卡。于是经过多番考虑（知乎一位买k80说翻车的帖子），于是最终下手m40。咸鱼有卖1800的，我问他保一个月质保不，他说，不保，我说谢谢，我考虑一下，他骂***（这时代也不知道怎么了，我就发了两条消息，这货好像脑子有点问题了，随后拉黑。因此不建议上咸鱼买，毕竟想上m40卡的应当希望稳妥一点）。随后在淘宝找了一家1945包邮的，还送一条转接线。挺合适，单买电源转接线需要30左右。（其实我怀疑这两家是一家，因为都是上海的）。淘宝这个质保3个月。当个保险。我用的机器配置如下，都是王牌(快玩完了的)产品。附上大师截图。大师我们需要它，他是给我们装显卡驱动的。win10自己好像不太认。以下配置，绝对可以跑paddlepaddleGPU框架。除了U，别的都挺便宜，刚开始买来做NAS的奈何功耗太高40w了，搁置了，现在加上m40满血复活。整套下来5000千元。当然，内存大家没必要这么大。4千完全够。我这主要是普通台式机使用m40，大家完全可以用二手服务器。买完之后，我发现网上很多说m40这些系列必须专门的主板和u才能跑，所以，那心情大家都能猜到，已经做好，再买板子的准备的我。
在这里插入图片描述

在这里插入图片描述
在这里插入图片描述

正文
两天到货了，同时购买的电源，没有收到，买的600W电源，没办法，偏远小城市，快递缓慢。
建议大家 买大于600w的电源，我原本一台没有独显的机器用的是300W电源，随机迫于心急之情，开始剪线，改电源。

改电源线
我原本的电源提供一个常规的显卡供电口，是6+2=8的结构，3x12V 3xGND 2GND结构

而Tesla系列根据知乎朋友的介绍和，我的实际观察，确定其为一排4x12V 一排4xGND的结构，也就是和我的主板CPU供电一致。所以，知乎这位朋友说，他一开始用常规显卡接口供电，将他的k80干坏电容问题，估计很真实，也是这个前车之鉴，我小心对比了电源结构，最终开始剪掉了老板送电源线和我自己那个300W电源的12V显卡口，（其实一开始，准备只剪我自己这个电源的显卡口，改一下线路来着，奈何我这90块钱的电源，那线 细的就像头发丝 让我直接干断了）。接完线，我还发现我用的那个接口保护的热缩管，给小了，无奈，只能用电胶带缠绕。
