---
tags: [big model training, deepspeed, hardware specs, pytorch]
title: gpt-2 ram requirements
created: '2022-04-28T02:22:06.000Z'
modified: '2022-08-18T07:52:35.576Z'
---

# gpt-2 ram requirements

服务器重量在25公斤以上 运输和搬运均需注意

服务器制造的热风需要用空调降温 或者需要有专门的通风管道

服务器的功耗是非常大的 服务器标配暴力风扇 虽然降温稳定性能很好 可以随时更换 但是噪音非常大 如果插上了不支持的显卡那么风扇会高速旋转 可能需要转接卡或者适配装置 待机功耗300w起步 而一般的台式机待机100w 如果加装了显卡那么功耗还会继续上升 同时满载的m1 ultra的mac studio功耗在140w-200w左右 相对比较节能

服务器需要标配灭火装置和烟雾报警装置

服务器需要放置在隔音机柜里面 专门的隔音机柜非常的贵 但是如果自己只买铁皮机柜加隔音棉那么会便宜一些 可能需要再加装一层外壳 透明的玻璃可能需要被更换成不透明的 同时改装之后需要留出专门的风道 风道内部塞管道隔音棉 风道出入口添加防尘网

to support multiple gpus, one must use pci-e extended cable. 128g per ram slot.

Dell r750 series, using dell riser card to connect gpu

https://github.com/hpcaitech/ColossalAI

for monsterious models, zero offload, pytorch loghtning, distributed training in pytorch, or deepspeed, fairscale, colossalai, Horovod is needed. no single gpu is able to hold gpt3-175B at once.

exporting to onnx:

https://huggingface.co/docs/transformers/serialization?highlight=onnx

lower model precision (quantization):

如果想要在GPU上操作，可以先使用torch.nn.export函数将模型转换成onnx格式，然后就可以放到TensorRT框架上inference了。（TensorRT目前不能直接解析Pytorch的网络模型，需要转换成onnx）

https://www.jianshu.com/p/cf83c877d71d
https://blog.csdn.net/zimiao552147572/article/details/105910915
https://pytorch.org/docs/stable/quantization.html
https://github.com/huggingface/transformers/issues/14839 (training gpt-j on colab)

# 使用torch.quantization.quantize_dynamic获得动态量化的模型
# 量化的网络层为所有的nn.Linear的权重，使其成为int8
quantized_model = torch.quantization.quantize_dynamic(
    model, {torch.nn.Linear}, dtype=torch.qint8
)
 
# 打印动态量化后的BERT模型
print(quantized_model)

how to use huggingface trainer:

https://zhuanlan.zhihu.com/p/363670628
https://zhuanlan.zhihu.com/p/486938936
https://zhuanlan.zhihu.com/p/358525654

https://huggingface.co/docs/transformers/main_classes/deepspeed#custom-deepspeed-zero-inference
https://huggingface.co/docs/transformers/main_classes/deepspeed

zero offload requires sufficient RAM.

https://github.com/alibaba/EasyParallelLibrary

https://github.com/SeanNaren/minGPT/tree/stage3

https://github.com/prigoyal/pytorch_memonger/blob/master/tutorial/Checkpointing_for_PyTorch_models.ipynb

https://github.com/eladrich/pixel2style2pixel
https://github.com/EleutherAI/gpt-neox
https://www.eleuther.ai

training turing-nlg:
https://www.microsoft.com/en-us/research/blog/turing-nlg-a-17-billion-parameter-language-model-by-microsoft/

cited from deepspeed:

Extremely memory efficient: With just a single GPU, ZeRO-Offload of DeepSpeed can train models with over 10B parameters, 10x bigger than the state of the art, democratizing multi-billion-parameter model training such that many deep learning scientists can explore bigger and better models.

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

普通台式机上Tesla M40显卡paddleGPU深度学习柯南的变身器上机体验 

最近在paddlepaddle溜达，看到了柯南变身器，于是从aistudio下载到本地玩，单位的1060 6G版显卡，跑起来，语句一场就不行，遂上淘宝，咸鱼溜达一圈，见到了tesla k80 m40等一系列的卡卡。于是经过多番考虑（知乎一位买k80说翻车的帖子），于是最终下手m40。咸鱼有卖1800的，我问他保一个月质保不，他说，不保，我说谢谢，我考虑一下，他骂***（这时代也不知道怎么了，我就发了两条消息，这货好像脑子有点问题了，随后拉黑。因此不建议上咸鱼买，毕竟想上m40卡的应当希望稳妥一点）。随后在淘宝找了一家1945包邮的，还送一条转接线。挺合适，单买电源转接线需要30左右。（其实我怀疑这两家是一家，因为都是上海的）。淘宝这个质保3个月。当个保险。我用的机器配置如下，都是王牌(快玩完了的)产品。附上大师截图。大师我们需要它，他是给我们装显卡驱动的。win10自己好像不太认。以下配置，绝对可以跑paddlepaddleGPU框架。除了U，别的都挺便宜，刚开始买来做NAS的奈何功耗太高40w了，搁置了，现在加上m40满血复活。整套下来5000千元。当然，内存大家没必要这么大。4千完全够。我这主要是普通台式机使用m40，大家完全可以用二手服务器。买完之后，我发现网上很多说m40这些系列必须专门的主板和u才能跑，所以，那心情大家都能猜到，已经做好，再买板子的准备的我。

正文
两天到货了，同时购买的电源，没有收到，买的600W电源，没办法，偏远小城市，快递缓慢。
建议大家 买大于600w的电源，我原本一台没有独显的机器用的是300W电源，随机迫于心急之情，开始剪线，改电源。

改电源线
我原本的电源提供一个常规的显卡供电口，是6+2=8的结构，3x12V 3xGND 2GND结构

而Tesla系列根据知乎朋友的介绍和，我的实际观察，确定其为一排4x12V 一排4xGND的结构，也就是和我的主板CPU供电一致。所以，知乎这位朋友说，他一开始用常规显卡接口供电，将他的k80干坏电容问题，估计很真实，也是这个前车之鉴，我小心对比了电源结构，最终开始剪掉了老板送电源线和我自己那个300W电源的12V显卡口，（其实一开始，准备只剪我自己这个电源的显卡口，改一下线路来着，奈何我这90块钱的电源，那线 细的就像头发丝 让我直接干断了）。接完线，我还发现我用的那个接口保护的热缩管，给小了，无奈，只能用电胶带缠绕。
