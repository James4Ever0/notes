---
created: 2026-07-27T17:21:38+08:00
modified: 2026-07-27T17:23:03+08:00
---

# llm router like clash

像litellm这种 是否有跨平台免安装纯golang或者rust写的 llm routing （dynamic routing）版本的clash 兼容多种coding agent 来确保报错减少 重试减少 上下文增加 速度加快 确保token效率最大化 花的钱变少 本地部署 观察是否逻辑出问题 是否陷入循环 （用llm动态检查观察别的llm输出是否存在问题） 是否已经开源 或者类似的付费服务 附带dashboard 也就是说当别人把api key model name url还有等等导入的时候 会后台不定时检查可用性 像检查proxy一样 先检查url可达 然后检查模型可用 （不能虚假回答） 最好还加上某些安全检查 看看这个站是否有投毒嫌疑 不过这种功能比较复杂 总之先找一下看看

---

另外这些只针对llm吗 有没有针对embedding 视频生成 语音生成等等的 或者某些可灵活定制的中转 通用failover服务框架

---

根据你的需求，市场上确实存在多款用 **Go** 或 **Rust** 编写的、类似 LiteLLM 的高性能 LLM 路由网关。它们大多是**开源**的，支持本地部署，并内置了动态路由、健康检查、成本追踪和 Dashboard 等核心功能。

下面是按语言分类的重点项目推荐：

---

## 🦀 Rust 语言

| 项目 | 核心特性 | Dashboard / UI | 与需求的匹配度 |
|------|---------|----------------|---------------|
| **rolter** | OpenAI/Anthropic兼容，负载均衡，**LiteLLM-proxy直接替代品** | TypeScript + shadcn/ui Dashboard | ⭐⭐⭐⭐⭐ |
| **gproxy** | 多协议转换，路由，**内置Admin Console**，配额管理 | 内置控制台 `/console` | ⭐⭐⭐⭐⭐ |
| **synapse-gateway** | OpenAI兼容，fallback链，**Vertex AI原生支持**，成本台账 | Prometheus + OpenTelemetry | ⭐⭐⭐⭐ |
| **oxllm** | 极简（~2.6MB），**自适应熔断**，tiered failover，热重载 | 内置 `/status` 统计 | ⭐⭐⭐⭐ |
| **sturnus** | **自动延迟感知路由**，Session Affinity，零基础设施 | 无（设计取舍） | ⭐⭐⭐ |
| **openproxy** | 加权负载均衡，**健康检查**，fallback，连接池 | 结构化日志 | ⭐⭐⭐ |
| **croit/llm-gateway** | **OIDC登录**，RBAC，**内置Chat UI**，健康探针 | 内置Web UI | ⭐⭐⭐⭐ |

---

## 🐹 Go 语言

| 项目 | 核心特性 | Dashboard / UI | 与需求的匹配度 |
|------|---------|----------------|---------------|
| **TrustGate** | **语义路由**，健康检查，fallback，**Guardrails**，多租户 | Admin API + Console | ⭐⭐⭐⭐⭐ |
| **Nenya** | **Agent路由**，上下文管理，**Token预算裁剪**，23+内置provider | `/statsz`, `/metrics` | ⭐⭐⭐⭐⭐ |
| **Foreman** | **成本优先路由**，会话缓存亲和，**决策台账可追溯** | CLI + trace命令 | ⭐⭐⭐⭐ |
| **Wyolet Relay** | **Key Pooling**，批量处理，400+模型目录，Proxy模式 | Admin UI (8081端口) | ⭐⭐⭐⭐ |
| **Ferro Labs AI Gateway** | 100+ provider，**插件中间件**，API密钥管理 | 待确认 | ⭐⭐⭐⭐ |
| **femto-llm** | **Discovery-based路由**，健康检查时动态发现模型 | 无 | ⭐⭐⭐ |
| **llmio** | 负载均衡，**现代Admin UI** | 内置Admin UI | ⭐⭐⭐⭐ |
| **VoidLLM** | 隐私优先，**内置Admin UI**，用量追踪 | 内置Admin UI | ⭐⭐⭐⭐ |

---

## 关于你提到的几个高级功能

### 1. “用LLM动态检查别的LLM输出是否出问题/陷入循环”

目前纯 Go/Rust 的项目中，**TrustGate** 内置了 **TrustGuard**  Guardrails，可对输入输出进行安全检查。Rust 生态中也有专门的 **llm-guard-rs**（零拷贝、亚毫秒级）和 **rupia**（输出验证+自我修复循环）。但“用另一个LLM来检查当前LLM的输出”这种 **LLM-as-Judge** 模式，目前更多是在 Python 生态（如 Guardrails AI）中实现。Rust/Go 项目大多采用**规则/模式匹配**方式，如果你需要真正的 LLM-as-Judge，可能需要自己集成或二次开发。

### 2. “后台不定时检查可用性，像检查proxy一样”

几乎所有列出的项目都支持 **健康检查（Health Check）** + **熔断（Circuit Breaker）** + **自动故障转移（Failover）**。例如 **oxllm** 有自适应熔断和 tiered failover，**TrustGate** 支持健康检查和 fallback chains。

### 3. “安全检查/投毒嫌疑”

Go 生态中有专门的安全代理，如 **agentproxy**（敏感内容扫描）、**llm-sentinel**（PII检测 + prompt注入拦截）、**ClawShield**（prompt注入、PII、密钥扫描）。但这些是独立的安全工具，而非 LLM 路由网关的内置功能。你可以将它们部署在路由网关前面，形成安全层。

### 4. “Dashboard”

多数项目都提供 Dashboard 或 Admin UI：
- **rolter**：TypeScript + shadcn/ui Dashboard
- **gproxy**：内置 Admin Console
- **Wyolet Relay**：Admin UI 在 8081 端口
- **croit/llm-gateway**：内置 Web UI
- **VoidLLM**：内置 Admin UI

---

## 总结建议

| 你的需求 | 最佳匹配项目 |
|---------|------------|
| **Rust + 完整 Dashboard + LiteLLM替代** | **rolter** |
| **Rust + 内置控制台 + 多协议** | **gproxy** |
| **Go + 语义路由 + Guardrails + 企业级** | **TrustGate** |
| **Go + Agent路由 + 上下文管理** | **Nenya** |
| **Go + 成本优化 + 决策追溯** | **Foreman** |
| **Go + Key Pooling + Admin UI** | **Wyolet Relay** |

**特别提醒**：
- **rolter** 明确自称 “LiteLLM-proxy alternative”，是最直接的替代品
- **TrustGate** 和 **Nenya** 在 Agent/Coding Agent 场景下支持最好
- 如果你对“LLM 检查 LLM”有强需求，目前可能需要结合 **llm-guard-rs** 或 **rupia** 等工具做二次开发，纯开箱即用的方案暂时较少

这些项目大多采用 **Apache-2.0**、**MIT** 或 **AGPL-3.0** 许可证，均为开源，可以自由本地部署。

---

针对非 LLM 模型（如 embedding、视频、语音生成），确实存在一些类似的路由服务。但它们主要可分为两类：**多模态 AI 网关**和**通用 API 网关/框架**。

下面为你梳理了相关的开源项目。

### 🧬 多模态 AI 网关

这类网关专为 AI 模型设计，能统一接入并路由多种类型的模型请求。

**1. Ollama Herd**
*   **路由能力**：LLM、**图像生成、语音识别 (STT)、Embedding**。
*   **核心技术**：Python，通过 mDNS 自动发现节点。
*   **主要特性**：零配置、智能评分路由、实时 Dashboard、自动重试与故障转移。
*   **注意**：主要面向 Ollama 生态。

**2. JAiRouter**
*   **路由能力**：**Chat、Embedding、Rerank、TTS (语音合成)** 等。
*   **核心技术**：Spring Boot (Java)。
*   **主要特性**：功能全面的 Web 控制台、配置版本控制、分布式追踪、JWT + API Key 双认证。

**3. 35gateway**
*   **路由能力**：**文本、图片、视频、音频、音乐**。
*   **主要特性**：源码可用、支持多供应商智能路由与自带 Key 混合使用。商业版提供完整运营后台。

**4. Bella OpenAPI**
*   **路由能力**：Chat、**文本向量化 (Embedding)、ASR (语音识别)、TTS (语音合成)、文生图、图生图**。
*   **主要特性**：集成计费、限流和资源管理，声称经过大规模生产环境验证。

**5. OpenRouter**
*   **路由能力**：**图像、视频、音频、Embedding、转录**。
*   **主要特性**：**付费服务**，提供统一的 OpenAI 兼容 API，支持 failover 和成本/延迟排序。
*   **注意**：需注意其专用端点和模型限制。

**6. Rath (Rust)**
*   **路由能力**：LLM、**Embedding、图像、视频、音频** API。
*   **核心技术**：Rust。
*   **主要特性**：Provider-agnostic 的 Rust API 层，通过统一的 Model URL 格式进行路由。

**7. croit/llm-gateway (Rust)**
*   **路由能力**：`/chat/completions`、**`/embeddings`**、**`/audio/transcriptions`**。
*   **核心技术**：Rust。
*   **主要特性**：多后端路由、健康检查、负载均衡、模型别名与 fallback。

**8. OmniRoute**
*   **路由能力**：100+ 提供商的 AI 模型。
*   **主要特性**：智能路由到免费和低成本模型，并具备自动 fallback。

**9. Triton OpenAI Gateway**
*   **路由能力**：多模态输入、**Embedding、Rerank**。
*   **核心技术**：为 NVIDIA Triton 和 vLLM 提供 OpenAI 兼容网关。

### 🧩 通用 API 网关/框架

这类是更通用的工具，可用来构建自定义的模型路由层。

**1. Apache APISIX**
*   云原生 API 网关，其 `ai-proxy-multi` 插件可简化对 LLM 和 **Embedding 模型**的访问，并支持负载均衡。

**2. go-aisdk (Go)**
*   一个 Go 语言库，为**对话、图像生成、视频生成、音频处理和向量嵌入**等提供统一的 API 接口。

**3. 传统负载均衡器**
*   像 **HAProxy** 或 **Traefik** 这类成熟的工具，也可以作为基础的负载均衡和 failover 方案，为 **Embedding 模型**推理等服务提供支持。

### 💎 总结与建议

*   **如果你希望快速获得一个功能全面的多模态网关**：
    *   可以优先考察 **JAiRouter**（功能最全，Java）、**Bella OpenAPI**（经生产验证）和 **Ollama Herd**（配置最简单，Python）。
    *   如果预算允许，**OpenRouter** 是省去运维工作的付费服务选项。

*   **如果你是 Rust 技术栈的开发者**：
    *   **Rath** 提供了灵活的 API 层，而 **croit/llm-gateway** 则是一个功能更完整的网关实现。

*   **如果你倾向于使用 Go 语言**：
    *   **go-aisdk** 是一个不错的起点，或者你也可以基于 **APISIX** 这样的通用网关进行二次开发。

*   **关于“通用 failover 服务框架”**：
    *   目前没有发现一个专门为所有 AI 模型类型设计的“通用”框架。大部分项目仍以 LLM 为核心，逐步扩展支持其他模态。
    *   不过，**APISIX** 这类云原生网关提供了很好的基础。你可以利用其插件机制，为不同类型的 AI 模型服务（文本、图像、视频等）分别配置路由、负载均衡和 failover 策略，从而构建出一个满足你需求的“通用”框架。

选择哪个项目，主要取决于你首要支持的模型类型和你熟悉的技术栈。
