---
title: gpt-2 ram requirements
created: '2022-04-28T02:22:06.000Z'
modified: '2022-08-15T07:35:20.280Z'
---

# gpt-2 ram requirements

æå¡å¨ééå¨25å¬æ¤ä»¥ä¸ è¿è¾åæ¬è¿åéæ³¨æ

æå¡å¨å¶é çç­é£éè¦ç¨ç©ºè°éæ¸© æèéè¦æä¸é¨çéé£ç®¡é

æå¡å¨çåèæ¯éå¸¸å¤§ç æå¡å¨æ éæ´åé£æ è½ç¶éæ¸©ç¨³å®æ§è½å¾å¥½ å¯ä»¥éæ¶æ´æ¢ ä½æ¯åªé³éå¸¸å¤§ å¦ææä¸äºä¸æ¯æçæ¾å¡é£ä¹é£æä¼é«éæè½¬ å¯è½éè¦è½¬æ¥å¡æèééè£ç½® å¾æºåè300wèµ·æ­¥ èä¸è¬çå°å¼æºå¾æº100w å¦æå è£äºæ¾å¡é£ä¹åèè¿ä¼ç»§ç»­ä¸å åæ¶æ»¡è½½çm1 ultraçmac studioåèå¨140w-200wå·¦å³ ç¸å¯¹æ¯è¾èè½

æå¡å¨éè¦æ éç­ç«è£ç½®åçé¾æ¥è­¦è£ç½®

æå¡å¨éè¦æ¾ç½®å¨éé³æºæéé¢ ä¸é¨çéé³æºæéå¸¸çè´µ ä½æ¯å¦æèªå·±åªä¹°éç®æºæå éé³æ£é£ä¹ä¼ä¾¿å®ä¸äº å¯è½éè¦åå è£ä¸å±å¤å£³ éæçç»çå¯è½éè¦è¢«æ´æ¢æä¸éæç åæ¶æ¹è£ä¹åéè¦çåºä¸é¨çé£é é£éåé¨å¡ç®¡ééé³æ£ é£éåºå¥å£æ·»å é²å°ç½

to support multiple gpus, one must use pci-e extended cable. 128g per ram slot.

Dell r750 series, using dell riser card to connect gpu

https://github.com/hpcaitech/ColossalAI

for monsterious models, zero offload, pytorch loghtning, distributed training in pytorch, or deepspeed, fairscale, colossalai, Horovod is needed. no single gpu is able to hold gpt3-175B at once.

exporting to onnx:

https://huggingface.co/docs/transformers/serialization?highlight=onnx

lower model precision (quantization):

å¦ææ³è¦å¨GPUä¸æä½ï¼å¯ä»¥åä½¿ç¨torch.nn.exportå½æ°å°æ¨¡åè½¬æ¢æonnxæ ¼å¼ï¼ç¶åå°±å¯ä»¥æ¾å°TensorRTæ¡æ¶ä¸inferenceäºãï¼TensorRTç®åä¸è½ç´æ¥è§£æPytorchçç½ç»æ¨¡åï¼éè¦è½¬æ¢æonnxï¼

https://www.jianshu.com/p/cf83c877d71d
https://blog.csdn.net/zimiao552147572/article/details/105910915
https://pytorch.org/docs/stable/quantization.html
https://github.com/huggingface/transformers/issues/14839 (training gpt-j on colab)

# ä½¿ç¨torch.quantization.quantize_dynamicè·å¾å¨æéåçæ¨¡å
# éåçç½ç»å±ä¸ºææçnn.Linearçæéï¼ä½¿å¶æä¸ºint8
quantized_model = torch.quantization.quantize_dynamic(
    model, {torch.nn.Linear}, dtype=torch.qint8
)
 
# æå°å¨æéååçBERTæ¨¡å
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

NVIDIA Tesla M40  24G ä¸ä¸è¿ç® è±ä¼è¾¾ å¾å½¢GPUå éæ·±åº¦å­¦ä¹ æ¾å¡

æä¾é­æ¹æç¨ï¼éè¦ä¸å¼ äº®æºå¡ï¼ç¨ä¸½å°K600å½äº®æºå¡å°±è¡ï¼é­æ¹åå¯ç¨æ­¤å¡ææ¸¸æ

æ£ç­å¨å¯çå¾çï¼ç¨3Dæå°æ£ç­é£éï¼å ä¸é£æå°±è½ç¨äº

èæå ç¨è¿äºå¡ K1 K2 K340 K520ï¼ä¸éè¦ææï¼ M60 P4 P10 P100 T4 RTX6000 RTX8000 V100 RTXA6000 P40 ï¼éè¦ææï¼

èæå VGPU æä¸¤ç§æ¨¡å¼ ä¸ç§æ¯VPC éåæ®éåå¬ ä¸ç§æ¯VDWS éåä¸ä¸å¾å½¢åºç¨ ç¶åP40ä¸¤ç§æ¨¡å¼é½æ¯æ

è´­ä¹°ä¹ååäºè§£ä»¥ä¸ä¿¡æ¯ï¼æ¨å¿é¡»äºè§£ï¼ï¼

1ãçµæºä¾çµææ²¡æ8éä¾çµï¼

2ãæ®éå°å¼æºX99ä»¥ä¸ä¸»æ¿ï¼DDR4åå­ï¼

3ãä¸»æ¿è¦æ¯æå¤æ¾å¡æ¾ç¤ºï¼

4ãå»ºè®®çµæºåçå¨600Wä»¥ä¸ï¼

5ãæºç®±åçç©ºé´æ¯å¦è¶³å¤ï¼å¡å®½åæ¡çä½ç½®ï¼å¡é¿åº¦28~30cmï¼

6ãæ®éå°å¼æºéè¦å è£ä¸»å¨æ£ç­ï¼æå¡å¨å¯ä»¥éæ©è¢«å¨æ£ç­

7ãåæ¥çä¸»æ¿biosçpcieè®¾ç½®éé¢ææ²¡æabove 4géé¡¹

è¶å¾®æå¡å¨åè£ææº æè²è¶æ° æµè¯å¥½åè´§

æ®éå°å¼æºä¸Tesla M40æ¾å¡paddleGPUæ·±åº¦å­¦ä¹ æ¯åçåèº«å¨ä¸æºä½éª 

æè¿å¨paddlepaddleæºè¾¾ï¼çå°äºæ¯ååèº«å¨ï¼äºæ¯ä»aistudioä¸è½½å°æ¬å°ç©ï¼åä½ç1060 6Gçæ¾å¡ï¼è·èµ·æ¥ï¼è¯­å¥ä¸åºå°±ä¸è¡ï¼éä¸æ·å®ï¼å¸é±¼æºè¾¾ä¸åï¼è§å°äºtesla k80 m40ç­ä¸ç³»åçå¡å¡ãäºæ¯ç»è¿å¤çªèèï¼ç¥ä¹ä¸ä½ä¹°k80è¯´ç¿»è½¦çå¸å­ï¼ï¼äºæ¯æç»ä¸æm40ãå¸é±¼æå1800çï¼æé®ä»ä¿ä¸ä¸ªæè´¨ä¿ä¸ï¼ä»è¯´ï¼ä¸ä¿ï¼æè¯´è°¢è°¢ï¼æèèä¸ä¸ï¼ä»éª***ï¼è¿æ¶ä»£ä¹ä¸ç¥éæä¹äºï¼æå°±åäºä¸¤æ¡æ¶æ¯ï¼è¿è´§å¥½åèå­æç¹é®é¢äºï¼éåæé»ãå æ­¤ä¸å»ºè®®ä¸å¸é±¼ä¹°ï¼æ¯ç«æ³ä¸m40å¡çåºå½å¸æç¨³å¦¥ä¸ç¹ï¼ãéåå¨æ·å®æ¾äºä¸å®¶1945åé®çï¼è¿éä¸æ¡è½¬æ¥çº¿ãæºåéï¼åä¹°çµæºè½¬æ¥çº¿éè¦30å·¦å³ãï¼å¶å®ææçè¿ä¸¤å®¶æ¯ä¸å®¶ï¼å ä¸ºé½æ¯ä¸æµ·çï¼ãæ·å®è¿ä¸ªè´¨ä¿3ä¸ªæãå½ä¸ªä¿é©ãæç¨çæºå¨éç½®å¦ä¸ï¼é½æ¯çç(å¿«ç©å®äºç)äº§åãéä¸å¤§å¸æªå¾ãå¤§å¸æä»¬éè¦å®ï¼ä»æ¯ç»æä»¬è£æ¾å¡é©±å¨çãwin10èªå·±å¥½åä¸å¤ªè®¤ãä»¥ä¸éç½®ï¼ç»å¯¹å¯ä»¥è·paddlepaddleGPUæ¡æ¶ãé¤äºUï¼å«çé½æºä¾¿å®ï¼åå¼å§ä¹°æ¥åNASçå¥ä½åèå¤ªé«40wäºï¼æç½®äºï¼ç°å¨å ä¸m40æ»¡è¡å¤æ´»ãæ´å¥ä¸æ¥5000ååãå½ç¶ï¼åå­å¤§å®¶æ²¡å¿è¦è¿ä¹å¤§ã4åå®å¨å¤ãæè¿ä¸»è¦æ¯æ®éå°å¼æºä½¿ç¨m40ï¼å¤§å®¶å®å¨å¯ä»¥ç¨äºææå¡å¨ãä¹°å®ä¹åï¼æåç°ç½ä¸å¾å¤è¯´m40è¿äºç³»åå¿é¡»ä¸é¨çä¸»æ¿åuæè½è·ï¼æä»¥ï¼é£å¿æå¤§å®¶é½è½çå°ï¼å·²ç»åå¥½ï¼åä¹°æ¿å­çåå¤çæã

æ­£æ
ä¸¤å¤©å°è´§äºï¼åæ¶è´­ä¹°ççµæºï¼æ²¡ææ¶å°ï¼ä¹°ç600Wçµæºï¼æ²¡åæ³ï¼åè¿å°åå¸ï¼å¿«éç¼æ¢ã
å»ºè®®å¤§å®¶ ä¹°å¤§äº600wççµæºï¼æåæ¬ä¸å°æ²¡æç¬æ¾çæºå¨ç¨çæ¯300Wçµæºï¼éæºè¿«äºå¿æ¥ä¹æï¼å¼å§åªçº¿ï¼æ¹çµæºã

æ¹çµæºçº¿
æåæ¬ççµæºæä¾ä¸ä¸ªå¸¸è§çæ¾å¡ä¾çµå£ï¼æ¯6+2=8çç»æï¼3x12V 3xGND 2GNDç»æ

èTeslaç³»åæ ¹æ®ç¥ä¹æåçä»ç»åï¼æçå®éè§å¯ï¼ç¡®å®å¶ä¸ºä¸æ4x12V ä¸æ4xGNDçç»æï¼ä¹å°±æ¯åæçä¸»æ¿CPUä¾çµä¸è´ãæä»¥ï¼ç¥ä¹è¿ä½æåè¯´ï¼ä»ä¸å¼å§ç¨å¸¸è§æ¾å¡æ¥å£ä¾çµï¼å°ä»çk80å¹²åçµå®¹é®é¢ï¼ä¼°è®¡å¾çå®ï¼ä¹æ¯è¿ä¸ªåè½¦ä¹é´ï¼æå°å¿å¯¹æ¯äºçµæºç»æï¼æç»å¼å§åªæäºèæ¿éçµæºçº¿åæèªå·±é£ä¸ª300Wçµæºç12Væ¾å¡å£ï¼ï¼å¶å®ä¸å¼å§ï¼åå¤åªåªæèªå·±è¿ä¸ªçµæºçæ¾å¡å£ï¼æ¹ä¸ä¸çº¿è·¯æ¥çï¼å¥ä½æè¿90åé±ççµæºï¼é£çº¿ ç»çå°±åå¤´åä¸ è®©æç´æ¥å¹²æ­äºï¼ãæ¥å®çº¿ï¼æè¿åç°æç¨çé£ä¸ªæ¥å£ä¿æ¤çç­ç¼©ç®¡ï¼ç»å°äºï¼æ å¥ï¼åªè½ç¨çµè¶å¸¦ç¼ ç»ã
