---
tags: [chatbot, conversation, interaction, pyjom, schedule]
title: 复读机 Chatbot
created: 2022-07-14T15:35:31+00:00
modified: 2023-07-22T18:41:20+08:00
---

# 复读机 Chatbot

利用带时间戳的QQ消息 提取和天气有关的内容 根据历史天气预报推断群友位置

根据聊天记录推断群友位置

测试聊天机器人的方式就是对聊 测试自媒体可以用自动测试 假数据进行测试

带二维码的图片 二维码对比度要低 避免被qq管家撤回

classify bilibili video which users recommend, then train the model against recent chats and topics with video tags

for our potential viewers, you may send them popular/hot things, place trackers (短链接统计) on those links, guess their favourites.

you may fool bilibili trackers, official parameter-based trackers.

对于qq上面聊骚的可以发a片给他们

get bilibili user email address by asking them from chat. if they give the email address, send setu as gift (regularly?)

of course you need to pass uid to us. either by parameters or by asking.

建立用户画像 cache足够多的信息 总结出来足够精确的话题 标签

发点啥吸引人的 提供某种服务 不然就会被踢

大晚上的不要说话 大家都睡觉 说话容易被踢

一般被引用的图片 发图之后被回复 图片下面比较激烈的回复代表着图片质量比较好 要取决于图片具体内容进行分类

note: in order to install libraries and dependencies, you need ubuntu inside termux. create shortcuts and alias to launch ubuntu. link files and directories to ububtu proot filesystem. also never attempt to update kali since that will break shit, especially for bumping python versions.

## 时序数据库

[tdengine stream processing](https://docs.tdengine.com/develop/stream/)

[influxdb python client](https://docs.influxdata.com/influxdb/v2.3/api-guide/tutorials/python/)

## 智能问答

[智能问答与深度学习 附带代码](https://github.com/l11x0m7/book-of-qna-code)

## 近义词

[use wordnet to find hyponyms and antonyms](https://www.tutorialspoint.com/natural_language_toolkit/natural_language_toolkit_looking_up_words_in_wordnet.htm#:~:text=To%20get%20a%20list%20of%20Synsets%2C%20we%20can,follows%20−%20from%20nltk.corpus%20import%20wordnet%20as%20wn)

[find antonyms for chinese with wordnet](https://github.com/nltk/nltk/issues/2972)

[中文近义词](https://github.com/chatopera/Synonyms) 以及[如何扩充词库](https://github.com/chatopera/Synonyms/issues/5)

## 话题建模 句向量

[10 nlp libraries](https://www.qblocks.cloud/blog/best-nlp-libraries-python)

[gensim word2vec](https://radimrehurek.com/gensim/models/word2vec.html)

[word embedding using word2vec](https://www.geeksforgeeks.org/python-word-embedding-using-word2vec/)

[gensym word2vec complete guide](https://www.askpython.com/python-modules/gensim-word2vec)

[go-cqhttp 自定义合并转发消息 生成不存在的合并转发消息](https://www.jianshu.com/p/dbf10744bde0)

- [ ] 渐进式领红包 对于某个群 先是两分钟（左右）之后领一次 领不到就时间减半下一次再领 如果领到了就不减半 最快6秒领 不能再减了 防止某些群为了检测机器人而发红包

- [ ] 处理信息不要流水线处理 放在messagepool里面 要有重要度排序 相关性排序

- [ ] QQ漂流瓶机器人 捡漂流瓶API

- [ ] 改回群昵称 总有些脑瘫喜欢给我乱起名 一天检查一次 模仿其他人的群昵称 看看有没有能用的马甲

- [ ] mitm Chatbot

chatbot frameworks:

[convai-bot 1337](https://github.com/sld/convai-bot-1337) the best hybrid convai bot

[omeglemiddleman](https://github.com/ash47/OmegleMiddleMan)

[chatterbot](https://github.com/gunthercox/ChatterBot) able to learn while having conversation

[qary: nlpia-bot](https://github.com/nlpia/nlpia-bot) a hybrid framework for developing chatbot by mannings

[mitm-omegle](https://github.com/olegberman/mitm-omegle) watch strangers talk

[ai chatbot framework](https://github.com/alfredfrancis/ai-chatbot-framework)

- [ ] 用sentence bert做search based dialog 替代levenshtein 最好是asymetrical semantic search
- [x] 有人有测试红包外挂的红包 可能有“test”、“测试”、“别抢”、“不要”之类的字眼 这种红包不要抢 抢了飞机票

- [ ] 群聊的下一句话不一定是上一句话的回答 训练模型寻找句子相关性 计算相关度 以及句子顺序

- [x] 对接小冰

- [ ] **管理员/群主在的时候 或者管理员经常出现的群里面 不要冒泡 不然容易被封**

转发的图片 至少要在之前一小时以内或更长时间内没有被重复发送才行 同一个信息内也不能出现重复图片 否则不发送这个信息（很有可能是广告）
有二维码不发送 有网址不发送
图片里面的文字要是有广告也是不能要的
文字信息不要广告 用简单分类器

[个性化搜索推荐 elasticsearch](https://github.com/mtianyan/FunpySpiderSearchEngine)

按照老毛的思想 要一边造谣一边辟谣 一边承认一边否定 同样的话颠三倒四可以说无数遍 也可以选择不说 这样可以和很多的类似故事杂交

- [ ] 处理私聊信息 每回复一个人就清除他的所有历史发言 每隔一段时间处理其中的一个人 不会相互挤占 只有在不闲聊的时候处理私聊信息 特定的人不能进行私聊
- [x] 白天聊天 收集数据 晚上离线训练 （此逻辑可以推广到任意的机器学习驱动的平台）
- [ ] 增加训练数据的context 不要只是一问一答 总语句数量要增加
- [ ] 占用系统显卡训练的时候 需要专门acquire一个filelock 表示大量资源被占用 系统忙
- [ ] 选取质量好有情感的聊天样本 长短适中 不要广告不要偏激违禁词 去掉表情包 去掉链接 清洗数据 同时模型用于对话的时候不要输入输出一些违禁词 可以通过话题建模进一步细分归类对话数据之间的联系

schedule the training on minute basis first for complete test, then schedule it on fixed time per day.

for qq client: dump 500 continual sentences when adding one new while holding the filelock, do not block or stop running if GPT not responding

for gpt2 server: (where to train? how to prevent maching from burning? for how long?)
rename the dataset while holding the filelock
always keep the latest 2 models, remove those not readable first, then delete older ones.

if train on CPU, still need to limit training time, sleep while doing so. GPU for sure we need sleep during training, and do not use VRAM for other applications.
- [ ] 把"汪汪"翻译成表情包 同时可以随机添加其他表情
- [x] 根据实时群聊数据训练gpt2
- [ ] 根据离线群聊数据训练gpt2


自动骂人
https://github.com/liuke-wuhan/ZuAnBot

- [ ] 添加一个FileLock在gpt2 main server里面 不要让多个对话同时进行处理

- [ ] 在人多的群里面少说话 具体表现为每次说话的时间间隔变长 次数变少 同时要注意 聊天内容过于严肃 专业的群尽量不要水

[dialogpt documentation](https://huggingface.co/docs/transformers/model_doc/dialogpt)

闲聊chitchat dialog bot training framework by facebook:
https://github.com/facebookresearch/ParlAI

debug the consecutive group reply thresholding protocol

reply according to individual description and group description

- [ ] 同时推广自己和别人的视频或者内容 收集推荐反馈 同时逐步减小推荐别人视频或者内容的频率
- [ ] 推广视频的时候可以加入别人的视频高赞评论 动态的GIF 音频 或者是短视频 然后再发送xml

- [ ] 增加复读图片的功能 增加chatlocal返回图片的功能

- [ ] 增加反馈功能 根据发言之后群里面的回复来确定发言是否有益

- [ ] 用txtai或者其他information retrieval (semantic search, smart search)语义查找工具来代替levenshtein的history based reply logic 查找时要包括上下文

- [ ] 复读机不能使得死群活起来 但是主动推送可以 推送长的 自言自语的对话到群里面 不能是同一个群 主题要相关 filter out too negative ones

- [ ] 拉人到别的群里面来 最好是多个号不共享群但是话题有交集的人

- [ ] add `involution` option, allow to append unqualified replies to input message, separated by space.

- [ ] add extend conversation option, allow to reply more than one sentence at a time (proper delay needed) -> could be achieved by using GPT2 alike generation model

- [ ] 可以给群友点赞

- [ ] 可以发语音

每次对话输入的context不能太小 不然看起来假

- [ ] 添加复读原句子的功能 触发条件为sentiment

往群里面发b站视频广告的话 最好和群聊主题相关 和最近接收到的消息相关 同时频率不能太高 要设置全局的counter 群聊每发送一条消息trigger一次counter counter mod period == 0 的时候就执行发广告命令 同时可以考虑渲染任务 和发广告的逻辑要解耦合 同时访问一片数据 比如redis 根据最近聊到的内容制作和上传视频 不能在同一个群里面以太快的频率发送相同视频 相同的视频必须间隔一段时间再往其他群发送 最好用schedule库实现 方法内部要实现delay或者放弃schedule的效果

如果群聊被踢 可以考虑换头像 换昵称 更改个人资料 然后重新申请 同样可以考虑更改b站的信息 用外网网红信息来填充自己的信息 更改资料频率和申请频率都需要控制 需要单独设置每天的quota quota保存在文件里面 申请的信息最好用ai生成 或者paraphrase一下 或者到网上搜索 收集相关内容 先训练一下 头像可以全网到处爬 可以选择二次元头像（动漫头识别）对比度高的 可以是类似头像 不能是系统默认头像不然太过无聊 可以和群聊主题相关 资料抄别人的 别的群里面的 抄该群群成员的资料 或者别的群的资料 不能是管理员资料


- [ ] 根据模板生成下一句 不要直接生成 素材可以是群公告 群主题 接收到的信息
模板生成要和新词发现结合
模板生成 paraphraser可以和chatlocal或者repeater结合


```python
>>> import re
>>> re.split(r"(abc|acd)","aaabcaaacdaaa")
['aa', 'abc', 'aa', 'acd', 'aaa']
>>> word="aaabcaaacdaaa"
>>> word="aaabcaaacdaaa"
>>> re.escape("abc")   
'abc'
>>> re.escape("efgh")
'efgh'
>>>
```

可以拆分句子为列表

- [ ] 去除经常生成的话语 比如你好之类的

挑选levenshtein距离大于0（不能是它本身）的上一句，排序 选择10句 根据情绪激烈程度（正负皆可 去掉过于负面的）排序 输出第一名 选择下一句作为回答 然后记录这个回答在机器人的回答历史中

句子如果是取同一个group里面的 不能太recent 起码距离要有50个句子的距离

文字 图片 视频 都可以搜索百度 搜狗 中文搜索api 根据相关度和情绪来排序 （语种一致）回答文字或者多媒体

拆分大句子为小句子 依次放入 注意要过滤掉广告 一般广告比较长 有链接？

- [ ] 输入的内容不能有违禁词否则不回答

- [ ] 输出内容的时候不能有违禁词语 放进来的可以违禁 或者用拼音或者拆字转换这些违禁词语 保证上下文一致性 文本审查

bad chinese -> letter(pinyin initials) -> leetspeek

下一次挑选的时候自动过滤掉这些下一句在历史回答里面的句子对

那个lock 要限制自身的读取/删除操作以及新消息的append操作

- [ ] 关于情绪激烈程度 如何提高生成器的情绪激烈度 做一个鉴别器 可以选择性的不去back propagate情绪不激烈的生成结果 或者直接用鉴别器筛选输入的语料
