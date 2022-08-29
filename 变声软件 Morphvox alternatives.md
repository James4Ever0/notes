---
tags: [model training, pyjom, speech synthesis, stub, voice changer, vst]
title: 变声软件 Morphvox alternatives
created: '2022-05-28T16:14:51.000Z'
modified: '2022-08-29T04:20:44.984Z'
---

# 变声软件 Morphvox alternatives

## vits变声
https://github.com/w4123/vits

[白嫖原神语音 有对如何训练原神语音作出的修改](https://github.com/w4123/vits) 想白嫖[访问demo的api](http://233366.proxy.nscc-gz.cn:8888/?text=你好&speaker=派蒙) 这个模型读英语不行 可能需要原神英文语音包吧 当然也可以直接考虑变声器模型 读阿拉伯数字也不可以 如何把非汉字内容变为可以读的内容

[]

[原神语音包解压](https://github.com/Vextil/Wwise-Unpacker/releases)

[米游社 原神语音包](https://bbs.mihoyo.com/ys/search/4?keyword=%E8%AF%AD%E9%9F%B3%E5%8C%85)

[obtain all genshin impact voices in all languages in quotes, with text](https://genshin.honeyhunterworld.com/ayaka_002/?lang=EN#delim_5)

[genshin voice scraper with text, also have scraped voice and text inside](https://github.com/CSUSTers/mys-voice-genshin)

[genshin limited english voice](https://github.com/ChrisBryann/GenshinSoundList)

## tactron2 变声 训练

MoeTTS是一个Tacotron2/HifiGAN模型+编译好的GUI版本发布仓库 有多个语音包
项目地址：https://github.com/luoyily/MoeTTS

主要的vst变声插件：

变声插件以及其他VST的选择，大家可以参考上一篇专栏，本人现在用的是Avox Mutator调整声调，Little Alterboy调整共振峰的搭配：

[gachikoe! core](https://sakurane-sachi.booth.pm/items/1236505) sign in with pixiv to download for free

[VST机架 变声 设置教程](https://www.bilibili.com/read/mobile?id=6275919&from=articleDetail)

需要多个vst插件相互连接

可能只适合个别声音 如果是野生音源 需要预处理 再进行输入

本篇教程是上一篇教程的延续，咕咕了大半年的我也做了很多新的尝试，本篇文章包含的内容是：1. 介绍一个免费的更加适合直播用途的机架Cantabile（替代Reaper）；2.  介绍目前咱自己调出来的，可以实现比较自然变声效果的VST链。关于如何使用OBS矫正变声器延迟导致的与模型嘴型、歌回时伴奏不同步的问题，我会在下一期中介绍（我真的不会再咕咕半年了）。



关于Voicemeeter与声卡配置的补充

请参照上一期，完成硬件设备以及Voicemeeter Banana的配置（重要！），Reaper的部分用下文的Cantabile代替~

本文中将会使用上一篇专栏中外置声卡的Asio驱动+第二张声卡（或者使用电脑自带的输出，比如一般电脑都有Realtek High Definition Audio）的方案。打开Voicemeeter的设置界面，在Output A1中点击ASIO设备的名称的话，会跳出声卡的配置界面：

点击红框处

声卡配置界面 - 采样率（Sample Rage）

声卡配置界面 - 缓存大小（Buffer Size）
采样率建议选择48kHz足够满足直播用途，太高的话会提高音频处理时的资源占用；如果在之后配置完变声器发现有爆音的现象，可以尝试提高Buffer Size（推荐512左右）。需要注意的是，Voicemeeter的ASIO方案虽然效率很高但可能是因为驱动的原因，并不适用于所有声卡，比如Focusrite的Scarlett系列。咱财力有限，只测试了Steinberg的UR系列声卡，不过在官方论坛上暂时也只看到了对Focusrite驱动支持问题的反馈，所以理论上大部分常用的声卡应该没有问题（大概

至此，前期准备完成！



Cantabile配置

下载地址：https://www.cantabilesoftware.com/download/

下载Stable Build并完成安装后，根据自己的操作系统选择运行64位/32位版本，选择Cantabile Lite版本（免费）。如果要求注册账户，按照步骤使用邮箱完成注册后，会在邮箱内收到注册码，使用注册码激活即可。

选择“Cantabile 3 Lite”
进入Cantabile后，在菜单中选择Tools→Options，在Audio Engine中选择ASIO - Voicemeeter Virtual ASIO：

Audio Engine
将Audio Ports如下图配置（先按照上一篇专栏配置好Voicemeeter哦）：

Audio Ports
同时在下面的Plugin Options中选择Add→Browse可以添加自己安装VST插件的文件夹，然后等待扫描完成，这样才可以使用已经安装的插件：

Plugins Options
在Cantabile的主界面中黑色部分右键选择Insert Plugin可以插入插件，右键已经插入的插件选择Delete可以删除该插件。实现变声器需要的插件的连接方法也非常简单，从Main Microphone拖出一条线到第一个插件的Stereo / Mono in，再将插件的Stereo / Mono Out连接到下一个插件的Stereo / Mono in，一直到最后一个插件的Stereo / Mono Out连接到Main Speakers。这样连接的原理很简单，就是将一个插件处理完的音频继续交由下一个插件处理，打到叠加的效果。下图是一个示例：

插件连接示例
为了方便监听效果，记得按照上一篇教程Voicemeeter配置部分的最后所说，保持Voicemeeter开启，点亮Voicemeeter绿框中的A2与B2，将Main Microphone到Main Speaker的线路连通应该就能从Voicemeeter右上角A2你选择的设备中听到此时经过处理的声音了，如果未连通应该是不会听到任何声音的。

至此，Cantabile配置完成！



搭建变声器所需插件

首先，介绍一下在搭建变声器的过程中需要的插件，下载与购买地址在文章末尾。在保证效果的前提下咱已经尽量把插件的选择精简，比如Waves、Soundtoys、Fabfilter的插件有捆绑包而不需要一个个购买，文章里没有提到的插件大家也可以自己玩一玩。个人的配置方案会在后文贴出：

（一）变声器插件（当然是必选）

经过一大堆尝试（Elastique Pitch，KeroVee，Antares Throat，等等...），效果最让咱满意的是来自Soundtoys的Little Alter Boy（售价$99，很贵，某些地方可以搜到Soundtoys的插件合辑但希望大家可以支持正版）。可以用的替代品是插件版的Gachikoe，需要加入作者桜音さち老师的Fanbox才能下载，要求一个月1000日元，下载完了可以取消，同样尽量支持作者~

变声器插件调节的是人声的音调（Pitch）以及共振峰（Formant）。在很多变声器插件中，Pitch的范围是-12到+12。一个八度有12个半音，从降一个八度到升一个八度，就是-12到+12这个范围的含义。咱推荐把Pitch直接调到+12，因为升高一个八度的话在歌回时不必另外对歌曲进行降调操作。相应的Formant请通过监听自己的声音慢慢调节，一般在3-4左右。如果想要自然一些并且不介意声音低沉一些的话，低一些的Pitch也是可以的。如何在OBS中进行对声音延迟的校正，让变声处理后的声音与耳机里听到的伴奏同步输出咱会写在下一篇专栏里~

（二）均衡器 / EQ（强烈推荐）

简单来说，均衡器调整的是各个频段的响度。由于男生和女生发生结构导致的响度分布不同，在调整音调的之前之后，我们都需要用到均衡器，不然可能会导致中频过强等问题。本人用的EQ是Fabfilter Pro Q3。

（三） 降噪器 / De-noiser（强烈推荐）

降噪器自然是为了处理噪声。在通过变声器之前，一些噪声可能并不刺耳，甚至可能都不会被注意到，但是在经过了变声器处理后，一些中低频的噪声会随着音调提高而变得刺耳，比如风声和电流声。因此，在声音通过变声器之前咱通常会放一个降噪器。本人用的是Waves WNS 1。

（四）限制器 / Limiter（强烈推荐）

限制器是其实可以说是压缩器的一种，将超出声音阈值的部分完全削除。在输出之前加一个-1分贝左右的限制器可以防止爆音以及大音量造成的失真保护观众的耳膜。咱用的是Waves Vcomp压缩器附带的限制器。

（五）Roth-AIR（推荐）

Roth-AIR是一个免费的、增加声音“空气感”的插件。本质上来说，应该属于EQ，但是使用非常方便（其实只需要调节一个旋钮）并且效果很好因此单独列出，咱在EQ之后会继续用Roth-Air调节高频。

（六）齿音消除器 / De-esser（推荐）

所谓齿音，是在说话或者唱歌时，开口说“嘶”、“次”这些音节时的尖锐声音。这些声音同样也会被变声器放大而变得刺耳。解决方法的方法，一种是使用插件，一种时给麦克风加上防喷网，也可结合使用。咱用的是防喷网+Waves DeEsser。

（七）压缩器 / Compressor（可选）

压缩器是当声音强度超过一定阈值时，对超出部分按照一定的比例进行响度衰减，以此减小声音的动态范围，同时不同的压缩器也会给声音带来不同的音染。希望让自己的声音更加饱满或者和麦克风距离忽近忽远导致声音忽大忽小的小伙伴可以尝试一下这类插件。本人在VST链最后加了Waves Vcomp插件。

介绍完毕，可以正式开工了！



正式配置变声器

大致的VST链顺序：

输入→降噪器→均衡器1→变声器→齿音消除器→EQ2→RothAIR→压缩器→输出

Cantabile配置
降噪插件的参数可以在自己不说话的情况下，点击频谱图右边的Suggest，会自动适配参数：

WNS 1 参数设置
第一个均衡器的配置，个人方案，请根据自己情况调节：

均衡器参数设置
变声器的配置，个人方案，请根据自己情况调节：

变声器配置
齿音消除器，第二个均衡器，RothAIR以及最后的压缩器参数就不贴图了，各位自己根据自己的声音多做尝试吧~

变声器教程完结！撒花！



一些大家可能会问的问题：
Q：只要有变声器就好了吗？

A：并不是，想要达到最好的效果还是需要控制自己的说话方式以及呼吸，之后可能会出专门的专栏讨论这个问题。

Q：这个方案的缺点？

A：资源占用不低，且有较大的延迟，不适合直播时监听变声过后的效果，因此需要练习把握住自己的语气。至于直播时变声器延迟导致的与伴奏不同步，与模型嘴型不同步我会在下期讲解怎么解决（咕咕咕）。以及，正版的插件价格很贵土真好吃，但还是希望大家尽可能支持正版。至于值不值得，大家可以听一下效果演示再做决定~

Q：除了文中提到的软件，是否有更好的选择？

A：有。本人自用的机架是Gig Performer 3（$149），价格贵但是更加稳定，对VST3插件的支持更好。以及，Waves插件之外，iZotope全家桶的效果也很好，但是因为巨大的延迟，比起直播更加适合后期处理，有兴趣和钱的话可以研究一下。



写在最后的话：

首先，咱只是一个爱好者，并不是什么后期调音man，甚至耳朵也很木，但我写在这里的是我自己目前为止研究出来的，毫无保留的最佳方案。当然，这个方案有着巨大的改进余地，希望它能抛砖引玉，各位有更好的方案希望能不吝分享。写这篇专栏的原因是在搜寻的过程中看到了不少效果尚不尽如人意的变声器，甚至有打着“免费变声器”、“主播同款”名号的视频，提供QQ群号，提供破解的机架下载，然后推荐声卡，最后再收费调音，被质疑调完音效果仍然不好就消失换个号继续，所谓的演示视频也很明显是由一男一女分开录音的。当然，这些也是个别现象，我还是遇见了很多前辈们有启发性的视频，但大家还是要对这类陷阱提高警惕~

最后，谢谢看到这里的你！祝早日成为美少女




Soundtoys官网：

https://www.soundtoys.com/

Gachikoe插件版Fanbox链接：

https://sakuranesachi.fanbox.cc/posts/498211

Roth-AIR官网：

https://www.danielrothmann.com/#downloads

Fabfilter官网：

https://www.fabfilter.com/

Waves插件官网：

https://www.waves.com/


xidada's tts:
https://huggingface.co/spaces/X*i-J*i*nP*i*n*g/X*i-J*i*nP*i*n*g-TTS # remove asterisks!

哔哩哔哩上看到的免费变声器
下载地址：
https://yuanqiyinpin.github.io/
本机架为二次开源软件，优点是占用率滴，不吃电脑配置，上手简单，免费使用

SoundTouch
萝莉音 青年音
https://github.com/jrising/pysoundtouch

gan based voice changer:
https://github.com/yl4579/StarGANv2-VC

install crossover to run windows app on linux

compile crossover from source on macos(code avaliable from official website):
https://gist.github.com/Alex4386/4cce275760367e9f5e90e2553d655309
https://www.codeweavers.com/crossover/source

变声器一般是vst类型的

run vst on linux headlessly:
https://github.com/hq9000/cython-vst-loader
https://github.com/hq9000/py_headless_daw

linux vst wrapper/bridge:
https://github.com/osxmidi/LinVst

VST bridge for Windows vst on Linux 
https://github.com/abique/vst-bridge

use vst 2.4 on macos with obs studio:
https://github.com/obsproject/obs-vst

pyvst vst wrapper for windows:
https://github.com/mbrucher/PyVST

python vst2 wrapper for windows:
https://pypi.org/project/neil-vst/

yabridge use windows vst3, vst2 plugins on linux using wine, with reaper:
https://github.com/robbert-vdh/yabridge

lyrebird voice changer for linux gtk3:
https://github.com/lyrebird-voice-changer/lyrebird

voice changer based on MHW Audio Modding Tool (not recommended):
https://github.com/ItsBurpee/MHWVoiceChanger

mozilla voice changer and visualizer based on  web api:
https://github.com/mdn/voice-change-o-matic

Real time voice changer in python:
https://github.com/symphonly/figaro

Pyvoicechanger:
https://github.com/juancarlospaco/pyvoicechanger

change the Pitch of the voice:
https://github.com/wittymindstech/change-voice-pitch

change pitch in real time:
https://github.com/jmt329/PitchShifter
