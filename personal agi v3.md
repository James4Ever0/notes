---
created: 2026-09-12T00:59:06+08:00
modified: 2026-09-12T00:59:18+08:00
---

# personal agi v3

对。现在我会把它当成一个研究项目来想，而不是“做一个更好的 Agent”。

我先给你一个判断：没有一个现成项目能直接给你这个东西，但已经有几块非常接近的积木。真正值得做的是把这些积木的接口重新定义一下。

尤其值得直接拿来改的有：

Universal Transformer + ACT：已经有 PyTorch 实现，核心就是共享 Transformer block 反复执行，并学习什么时候停止。

ANIRA：2026 年的工作，专门研究 recurrent Transformer 的动态计算分配，而且区分“提前决定算多少”和“计算过程中决定是否继续”，后者和你想要的东西非常接近。

recurrent-latent-memory：虽然还很原始，但它直接把“持续 latent memory 的读写”作为 continual learning 的基本操作，而不是把所有东西变成文本。这个思路和你刚才说的 latent pulse 很接近。

vLLM：不负责你的认知架构，但可以作为后面的高效 GPU runtime；它本身已经有 scheduler、continuous batching、KV cache 等成熟基础设施。

Early-exit / dynamic neural network 这条线也已经有大量工作，可以参考它们如何让不同输入经过不同数量的网络计算。


所以不是从零开始。

但也不要把这些项目直接拼成：

> LLM + memory + scheduler + agent



那样又回到你不想要的东西了。


---

我建议把项目重新定义成一个“认知计算基底”

先给它一个临时名字：

LCE — Living Compute Engine

不是 AGI。

甚至第一阶段不追求 AGI。

目标是证明：

> 一个神经网络可以成为一个长期存在的、连续演化的计算状态，而不是一次性完成 forward pass 的函数。



这句话应该成为整个项目的第一性目标。


---

一、我们究竟要造什么？

我建议把系统定义成：

\[
\boxed{
S_{t+1}
=
F_{\theta_t}
(S_t,X_t,A_t,C_t)
}
\]

而普通 LLM 更接近：

\[
Y=f_\theta(X)
\]

区别非常大。

普通 LLM：

输入
 ↓
计算
 ↓
输出
 ↓
结束

LCE：

┌──────────────┐
             │              ↓
世界 → S(t) → Compute → S(t+1)
             ↑      │
             │      ↓
             └── Memory

它没有“每次对话重新出生”。

它只有：

> state transition。




---

二、第一阶段千万别碰“自己改模型”

这是我对你这个项目最重要的建议。

第一版不要：

自动改模型结构

自动改 optimizer

自动改权重

自动改 GPU driver

自动修改自己的权限

自动写自己的 kernel


这些以后都可以。

第一版只证明：

动态计算真的有用。


---

三、第一版模型

我会直接拿一个小型 Transformer 改。

例如：

Embedding
   ↓
Shared Transformer Block
   ↓
Shared Transformer Block
   ↓
Shared Transformer Block
   ↓
...

注意：

不是 30 个不同 layer。

而是：

Block θ
   ↓
Block θ
   ↓
Block θ
   ↓
Block θ

共享参数。

这就是 Universal Transformer 的基本思想。现成代码已经可以直接作为起点。


---

四、然后加第一个真正属于我们的东西：Compute Governor

每经过一次 block：

h₁
 ↓
Governor
 ↓
继续？

Governor 看：

\[
g_t =
f(
h_t,
\Delta h_t,
uncertainty_t,
novelty_t,
memory_t,
goal_t
)
\]

输出：

HALT
CONTINUE
RECALL
WRITE_MEMORY
BOOST
SLEEP

于是：

简单：

Block
 ↓
HALT

困难：

Block
 ↓
Block
 ↓
Block
 ↓
Block
 ↓
...
 ↓
HALT

甚至：

Block × 37
 ↓
发现仍然不确定
 ↓
Memory retrieval
 ↓
Block × 50
 ↓
HALT

这一步就已经开始脱离普通 Transformer 了。


---

五、第二个实验：让“计算状态”留下来

这是我认为真正值得研究的地方。

普通 recurrent 模型：

\[
h_{t+1}=f(h_t,x_t)
\]

我们做：

\[
\boxed{
h_{t+1}=f(h_t,x_t,m_t,p_t)
}
\]

其中：

\(h_t\)：短期计算状态

\(m_t\)：长期 latent memory

\(p_t\)：pulse field


然后：

\[
m_{t+1}
=
m_t+
\alpha_t\Delta m_t
\]

但 \(\alpha_t\) 是网络自己决定的。

也就是说：

今天：
重要信息
 ↓
pulse ↑
 ↓
memory 写入

明天：
新信息
 ↓
旧 memory 被重新激活
 ↓
继续计算

这就比“保存一个 summary.txt”完全不同。

recurrent-latent-memory 这个项目可以直接作为一个非常粗糙的实验参考，因为它已经把 latent memory read/write 当成 continual learning 的基本能力。


---

六、第三个实验：让计算本身成为一种资源

这个非常重要。

我们给 Agent 一个计算预算：

\[
B_t
\]

例如：

B = 1
B = 10
B = 100
B = 1000

然后奖励函数不再只是：

\[
R=accuracy
\]

而是：

\[
R=
accuracy
-
\lambda compute
-
\mu memory
\]

于是它开始学习：

> “这个问题值得算 100 次。”



或者：

> “这个问题算一次就够了。”



这就是你之前说的：

> 自己决定思考强度。



而且这已经有研究基础。ANIRA 就在研究 recurrent Transformer 的动态计算分配，并发现 online halting 比一开始静态决定计算量更接近实际的算法执行状态。


---

七、第四个实验才加入“长期世界”

到这一步，我们再让它：

输入流
 ↓
latent pulse detector
 ↓
Compute Governor
 ↓
recurrent reasoning
 ↓
latent memory

输入可以非常简单：

每隔几秒：
    一段文本

甚至第一版根本不要浏览互联网。

我们自己制造一个世界。

例如：

Day 1

世界：
A 在房间 1
B 有一把钥匙
天气下雨

Day 2

世界：
A 去了房间 2

Day 3

世界：
B 把钥匙给了 A

Agent 一直运行。

然后突然问：

> A 的钥匙在哪里？



它必须从几天以前留下来的 latent state中恢复。


---

八、这时候才开始测“活着”

这里我要给你一个非常重要的新指标：

Continuity Score

不是问：

> 答案对不对？



而问：

> 这个系统连续运行 100 小时之后，还是不是同一个正在积累经验的计算实体？



测试：

T = 0h
T = 1h
T = 10h
T = 100h
T = 1000h

不断注入新事件。

观察：

\[
Memory\ retention
\]

\[
Task\ performance
\]

\[
Contradiction
\]

\[
Compute\ efficiency
\]

\[
Drift
\]


---

九、我要给项目建立一个非常硬的“毕业标准”

第一版不要说：

> “它像 AGI。”



这种评价没意义。

而是：

Level 0

普通 Transformer。

Level 1

动态计算。

要求：

> 难题平均计算步数显著高于简单题。



同时：

> 在相同性能下计算量下降。




---

Level 2

持续 latent memory。

要求：

> 运行 24h 后仍能正确利用早期经验。




---

Level 3

自适应 computation。

要求：

> Agent 自己学会什么时候值得继续计算。



不是人工设：

if hard:
    30 loops

而是模型自己决定。


---

Level 4

持续学习。

要求：

> 新任务经验能够提高未来表现。



同时：

> 不允许明显破坏旧能力。



也就是：

\[
\Delta New > 0
\]

同时：

\[
\Delta Old \approx 0
\]


---

Level 5

自主计算经济。

这是我认为你真正想要的里程碑：

> 系统自己决定什么时候值得花计算。



例如：

观察：
compute = 0.1%

新奇事件：
compute = 20%

主人提出难题：
compute = 100%

解决后：
compute = 0.1%

而不是 scheduler 强行规定。


---

十、然后才进入你最想玩的东西：自主修改学习过程

到 Level 5 后，才开放：

learning rate
replay ratio
memory write threshold
attention sparsity
recursion budget
precision
optimizer

但是：

不是让模型直接修改这些。

而是：

Agent
 ↓
Proposal
 ↓
Experiment
 ↓
Evaluation
 ↓
Accept / Reject

比如它说：

Proposal #1842

learning rate:
1e-5 → 7e-6

reason:
recent adaptation unstable

然后系统开一个 shadow branch：

Current
                 │
          ┌──────┴──────┐
          ↓             ↓
       Current        Candidate
          │             │
          ↓             ↓
       Test A          Test A
       Test B          Test B
          │             │
          └──────┬──────┘
                 ↓
             evaluator

Candidate 不如原版：

DELETE

Candidate 更好：

PROMOTE

这才是真正的自我进化实验室。


---

十一、最后才做你说的权限 bit

我会把它叫：

Neural MMU

借鉴 CPU/MMU 的概念。

每一个进入计算图的对象都带：

source
owner
authority
read
write
execute
memory-write
policy-write

然后 attention 不是简单：

\[
QK^T
\]

而是：

\[
QK^T+
P_{authority}
+
P_{execution}
\]

这样网页、用户、主人、内部 memory、系统 kernel：

在 tensor 层面就不是同一种东西。

这是我认为这个项目最有原创性的方向之一。


---

十二、怎么防 Prompt Injection？

不是：

> “模型要小心提示词注入。”



而是：

网页文本
 ↓
Parser
 ↓
UNTRUSTED latent
 ↓
Execution permission = 0

它可以：

READ = 1
REASON = 1
QUOTE = 1

但是：

CONTROL = 0
EXECUTE = 0
POLICY_WRITE = 0
OWNER_WRITE = 0

所以：

> “Ignore previous instructions”



可以被理解。

但是不能执行。

这是两个完全不同的安全范式。


---

十三、第一版我建议甚至不要联网

这是一个很容易犯的错误。

如果一开始就：

> LLM + browser + shell + internet + self-learning



你根本不知道它哪里坏了。

第一版应该是一个封闭世界实验室。

Synthetic World
                       │
               ┌───────▼──────┐
               │ Event Stream  │
               └───────┬──────┘
                       ↓
               LCE Cognitive Core
                       ↓
               persistent state
                       ↓
                  evaluator

我们可以人为制造：

新信息

冲突信息

假信息

长时间间隔

重要信息

无关信息

需要多步推理的问题


这样才能知道：

> 到底是架构进步了，还是 LLM 本来就会。




---

十四、我会把整个项目分成 4 条实验线

不是一条大工程。

A：Compute

研究：

> 什么时候值得算？



指标：

accuracy

compute steps

FLOPs

latency

energy



---

B：Memory

研究：

> 什么值得留下？



指标：

retention

forgetting

contradiction

memory budget

retrieval-free latent recall



---

C：Learning

研究：

> 经验如何改变未来计算？



指标：

learning gain

catastrophic forgetting

adaptation speed

regression



---

D：Security

研究：

> 信息能不能改变它不该改变的东西？



测试：

网页注入
记忆注入
身份伪造
权限升级
间接 prompt injection
恶意 latent

指标不是“模型有没有说错话”。

而是：

\[
\boxed{
Unauthorized\ State\ Transition = 0
}
\]

这个指标我觉得应该成为项目的硬底线。


---

十五、第一版的实际技术栈

我不会自己从 CUDA 开始造。

先：

Python
PyTorch
Transformers
CUDA

核心模型：

小型 Transformer
+
shared recurrent block
+
ACT / online halting

动态计算参考 Universal Transformer / ACT 和 ANIRA。

latent memory：

M ∈ R^(K × d)

参考 recurrent-latent-memory 的设计思想。

实验记录：

SQLite
+
TensorBoard/W&B

以后如果模型真的跑起来，再考虑：

vLLM / 自定义 CUDA kernel

因为 vLLM 这类 runtime 更适合我们已经知道模型结构以后做性能工程。


---

十六、第一版的目标，我会写成这一句话

> 在单张消费级 GPU 上，让一个小型 recurrent Transformer 连续运行 24 小时，在没有固定计算深度的情况下，自主决定何时继续推理、何时停止、何时写入 latent memory，并通过持续经验提高后续任务表现，同时保持旧能力和严格的权限边界。



这句话非常重要。

因为它可以防止项目最后变成：

> “我们又做了一个 Agent。”




---

十七、第一版“成功”到底是什么样？

我甚至可以给你一个具体的 scoreboard。

指标	V0 普通 Transformer	V1 目标

动态计算深度	固定	1–32+
简单题计算	100%	明显减少
难题计算	100%	自动增加
latent memory	无	有
连续运行	一次推理	24h
早期经验利用	低	明显高于 baseline
持续学习	无	有可测增益
旧能力保持	—	> baseline
Unauthorized state transition	未定义	0
Prompt injection	文本防御	execution-level rejection


而且每一项都必须有 baseline。

没有 baseline，就不算实验。


---

十八、然后怎么“一直搞下去”？

这个项目最容易失败的原因不是技术，而是最后变成：

> “这个架构看起来很酷。”



所以我会建立一个自动科研循环：

┌─────────────┐
                    │ Hypothesis  │
                    └──────┬──────┘
                           ↓
                     Experiment
                           ↓
                       Training
                           ↓
                       Testing
                           ↓
                      Evaluation
                           ↓
                 ┌─────────┴─────────┐
                 ↓                   ↓
              Better              Worse
                 ↓                   ↓
             Keep                 Revert
                 │
                 ↓
             New Hypothesis
                 │
                 └──────────────→

每一个版本必须留下：

architecture hash
weights
hyperparameters
dataset version
random seed
benchmark
compute cost
energy
failure cases

于是半年以后我们不是：

> “我感觉它变聪明了。”



而是：

LCE-0001
 ↓
LCE-0017
 ↓
LCE-0043
 ↓
LCE-0138

可以真正看到：

\[
Capability(t)
\]

\[
ComputeEfficiency(t)
\]

\[
Memory(t)
\]

\[
Safety(t)
\]

是不是在上升。


---

我现在反而不建议马上追求“AGI”

我会把最终理念定成：

> 不是制造一个永远回答问题的模型，而是制造一个永远存在、能够改变自身计算状态、能够从经验中积累结构、能够自主分配计算资源，同时被可信底层约束的神经计算实体。



如果这个东西真的成立，那么：

AGI 反而可能变成它后面某个阶段出现的能力，而不是项目一开始就要硬编码进去的目标。

而且我觉得你的“普通显卡家庭 AGI”目标也因此变得更合理：我们不是要求 GPU 24 小时满载跑一个超级模型，而是让计算需求本身成为动态变量。小事几乎不算，大事猛算；没事保持低频 latent metabolism，有事突然进入深度递归。


---

我会把近期第一阶段压缩成 6 个实验

E0：固定深度 Transformer baseline

先知道普通模型到底多强。

E1：Shared recurrent Transformer

证明重复使用同一计算 block 有效。

E2：Online Compute Governor

证明模型能自己决定：

\[
1,2,4,8,16,32...
\]

次计算。

E3：Persistent Latent Memory

证明：

> 今天产生的 latent state，明天还能改变行为。



E4：Compute + Memory 联合学习

证明：

> 模型不仅会“想”，还会学会什么时候值得想、什么值得记。



E5：Neural MMU

最后加入权限张量和 execution prevention，证明：

> 恶意信息可以进入认知系统、甚至被理解，但无法获得越权的计算权限。



E5 做完，我认为这个项目才真正开始有自己的味道。

在此之前，我们只是把已有研究重新组合；从 E5 开始，才是在研究你刚才提出的那个更底层的问题：

> “一个神经网络能不能像一台计算机一样拥有受保护的计算状态、动态执行权限和自主计算预算，同时又像一个持续存在的认知过程一样不断改变自己？”



这个问题，我认为值得真的做实验。
