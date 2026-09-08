# 免费 LLM 收集目录（Free LLM Collection）

免费大语言模型收集目录，持续收录可免费调用的模型，并从稳定性、调用限制、上下文长度、参数规模和适用场景等维度进行整理。

本项目关注：

- 哪些模型目前可以免费调用
- 哪个 Provider 提供免费访问
- 每分钟可以调用多少次
- 服务是否稳定
- 模型官方发布日期
- 参数规模和上下文长度
- 模型最适合什么任务

> 免费状态、调用限制和服务稳定性可能随时变化。使用前请以对应 Provider 的最新页面和官方文档为准。

## 快速推荐

| 使用场景 | 当前推荐 | 推荐理由 |
|---|---|---|
| 长上下文和 Agent 编排 | NVIDIA Nemotron 3 Ultra | 1M 上下文，适合长流程 Agent 和复杂任务 |
| 软件工程和代码 Agent | Poolside Laguna S 2.1 | 面向软件工程，118B 总参数，262K 上下文 |
| 高频轻量任务 | NVIDIA Nemotron 3.5 Lightning | 激活参数较少，适合速度优先的任务 |
| 金融分析 | inclusionAI Ling 3.0 Flash Fin | 针对金融任务和长周期规划进行优化 |
| 通用推理 | DeepSeek V4 Pro | 适合通用问答、推理和代码任务 |
| 中文任务 | GLM-5.3 Flash | 中文能力和通用任务覆盖较好 |
| 轻量级任务 | GPT-OSS-20B | 参数规模适中，适合一般推理和代码辅助 |

## 收录列表

以下权重为本项目整理收录时的评价维度说明，不代表统一基准测试结果。

| 评价维度 | 权重 | 说明 |
|---|---:|---|
| 稳定性 | 35% | 请求成功率、错误率、超时率和服务持续时间 |
| 调用限制 | 20% | 每分钟调用次数、每日额度和并发限制 |
| 任务适配度 | 25% | 是否适合代码、Agent、长文本、中文或其他专业任务 |
| 上下文能力 | 20% | 上下文窗口长度和长文本处理表现 |

模型排名不分先后，序号仅用于引用列表项。

| 序号 | 模型 | 模型厂商 | 免费 Provider | 每分钟限制 | 稳定性 | 参数量 | 上下文 | 擅长方向 | 官方发布日期 | 验证日期 |
|---:|---|---|---|---:|---:|---:|---|---:|---|---|
| 1 | Nemotron 3 Ultra | NVIDIA | [OpenRouter](https://openrouter.ai/nvidia/nemotron-3-ultra-550b-a55b:free) | 20 RPM；50/1000 RPD | 8/10 | 55B active / 550B total，MoE | 1M（官方）；OpenRouter 当前页 262K | Agent 编排、长文本、复杂推理 | 2026-06-04 | 2026-09-08 |
| 2 | Laguna S 2.1 | Poolside | [OpenRouter](https://openrouter.ai/poolside/laguna-s-2.1:free) | 20 RPM；50/1000 RPD | 8/10 | 8B active / 118B total，MoE | 262K（免费端点） | 软件工程、代码 Agent、长流程任务 | 2026-07-21 | 2026-09-08 |
| 3 | Nemotron 3.5 Lightning | NVIDIA | [OpenRouter](https://openrouter.ai/nvidia/nemotron-3.5-lightning:free) | 20 RPM；50/1000 RPD | 8/10 | 约 3-3.6B active / 约 30-31.6B total，MoE | 1M | 高频轻量任务、代码、工具调用 | 2026-08-11 | 2026-09-08 |
| 4 | Ling 3.0 Flash Fin | inclusionAI | [OpenRouter](https://openrouter.ai/inclusionai/ling-3.0-flash-fin:free) | 20 RPM；50/1000 RPD | 7/10 | 约 5.1B active / 124B total，MoE | 262K | 金融研究、财报分析、规划、推理、代码 | 2026-08-27 | 2026-09-08 |
| 5 | DeepSeek V4 Pro | DeepSeek | [cheapapis](https://cheapapis.net/pricing) | 20 RPM | 8/10 | 约 49B active / 1.6T total，MoE | 1M | 通用推理、代码、数学、长文本 | 2026-08-12/13（GA） | 2026-09-08 |
| 6 | GLM-5.3 Flash | 智谱 AI（Z.ai） | [cheapapis](https://cheapapis.net/pricing) | 20 RPM | 8/10 | 18B active / 320B total，MoE | 1M | 中文、多模态、通用问答、代码 | 2026-08-26 | 2026-09-08 |
| 7 | Kimi K3 | Moonshot AI | [cheapapis](https://cheapapis.net/pricing) | 20 RPM | 7/10 | 约 104B active / 2.8T total，MoE | 1M | 中文、长文本、推理、Agent | 2026-07-16（服务）；2026-07-27（权重） | 2026-09-08 |
| 8 | MiniMax M3 | MiniMax | [cheapapis](https://cheapapis.net/pricing) | 20 RPM | 8/10 | 约 23B active / 428B total，MoE | 1M | 中文、通用任务、代码、Agent | 2026-06-01 | 2026-09-08 |
| 9 | Muse Glimmer 30B | Meta Superintelligence Labs | [cheapapis](https://cheapapis.net/pricing) | 20 RPM | 7/10 | 约 30B，Dense | 128K-131K | 通用任务、创作、代码、工具调用 | 2026-08-10 | 2026-09-08 |
| 10 | GPT-OSS-20B | OpenAI | [cheapapis](https://cheapapis.net/pricing) | 20 RPM | 8/10 | 约 3.6B active / 20.9-21B total，MoE | 128K-131K | 通用推理、代码辅助、工具调用 | 2025-08-05 | 2026-09-08 |

## 免费 Provider

### OpenRouter

[OpenRouter](https://openrouter.ai/)

目前确认可通过 OpenRouter 免费端点访问的前四个模型包括：

- NVIDIA Nemotron 3 Ultra
- Poolside Laguna S 2.1
- NVIDIA Nemotron 3.5 Lightning
- inclusionAI Ling 3.0 Flash Fin

OpenRouter 免费端点的公开限制为：

- `20 RPM`
- 账户累计购买额度少于 10 credits 时为 `50 RPD`
- 账户累计购买额度达到 10 credits 后为 `1000 RPD`

以上限制是 OpenRouter 平台级限制，具体 Provider 仍可能额外限流。详见 [OpenRouter Rate Limits](https://openrouter.ai/docs/api-reference/limits)。

### cheapapis

[cheapapis](https://cheapapis.net/pricing)

目前从 cheapapis 页面收集到的免费模型包括：

- `gpt-oss-20b-free`
- `deepseek-v4-pro-0813-free`
- `glm-5.3-flash-free`
- `kimi-k3-free`
- `minimax-m3-free`
- `muse-glimmer-30b-free`

当前按 cheapapis 页面记录为 `20 RPM`。cheapapis 的每日额度、并发限制和不同模型的实际成功率仍需后续测试确认，因此暂不填写 RPD 和并发数。

## 字段说明

### 每分钟调用限制

使用 RPM（Requests Per Minute）表示一分钟内允许发送的请求数量。如果 Provider 没有公开限制，则记录实际测试结果，并注明测试日期。例如：

```text
20 RPM，实测于 2026-09-08
```

如存在其他限制，同时记录 RPD（每日请求数）和最大并发数：

```text
20 RPM / 1000 RPD / 2 concurrent
```

### 稳定性

稳定性使用 `1-10` 分。当前分数为主观初评：

| 分数 | 含义 |
|---:|---|
| 9-10 | 长时间运行稳定，成功率高，极少超时 |
| 7-8 | 整体稳定，偶尔限流或短暂错误 |
| 5-6 | 可以使用，但错误和超时较明显 |
| 3-4 | 经常限流、排队或请求失败 |
| 1-2 | 基本无法稳定使用 |

稳定性测试记录请求成功率、平均响应时间、P95 响应时间、超时率、错误率和限流频率。

### 参数量和上下文

MoE 模型同时记录激活参数和总参数，例如：

```text
8B active / 118B total
```

上下文长度使用模型官方支持的最大 Token 数量，例如 `262K` 或 `1M`。上下文长度较大不代表模型一定擅长长文本任务，最终表现仍需实际测试。

### 擅长方向

统一使用以下标签：

`代码` `Agent` `推理` `数学` `中文` `英文` `长文本` `多模态` `金融` `写作` `知识问答` `工具调用` `快速响应`

## 测试方法

### 速率限制测试

每个 Provider 分别测试单请求连续调用、逐步增加每分钟请求数、并发请求和连续运行 10 分钟，记录首次限流的请求数量及恢复时间。

测试结果只代表测试时间点的实际表现，不代表 Provider 的官方承诺。

### 稳定性测试

建议每天对每个模型发送固定数量的测试请求，连续测试至少 7 天，并记录：

```text
success_rate
timeout_rate
rate_limit_count
average_latency
p95_latency
```

## 数据来源

模型信息优先来自模型厂商官方公告、官方文档、官方仓库或权重发布页面。Provider 信息来自 OpenRouter、cheapapis 等服务页面；RPM、稳定性和实测评分来自本项目测试。

本次资料核实使用的公开来源：

- [OpenRouter 免费模型列表](https://openrouter.ai/collections/free-models)
- [OpenRouter 限流说明](https://openrouter.ai/docs/api-reference/limits)
- [Nemotron 3 Ultra](https://openrouter.ai/nvidia/nemotron-3-ultra-550b-a55b:free)
- [Laguna S 2.1](https://openrouter.ai/poolside/laguna-s-2.1:free)
- [Nemotron 3.5 Lightning](https://openrouter.ai/nvidia/nemotron-3.5-lightning:free)
- [Ling 3.0 Flash Fin](https://openrouter.ai/inclusionai/ling-3.0-flash-fin:free)
- [NVIDIA Nemotron 3 Ultra 官方资料](https://research.nvidia.com/labs/nemotron/Nemotron-3-Ultra/)
- [Ling 3.0 Flash Fin 模型卡](https://huggingface.co/inclusionAI/Ling-3.0-flash-Fin)
- [GPT-OSS-20B 官方文档](https://developers.openai.com/api/docs/models/gpt-oss-20b)

模型厂商与 Provider 分开记录：

- 模型厂商：负责模型本身
- Provider：负责免费调用入口
- 本项目：负责整理、测试和比较

## 贡献

欢迎提交新免费模型、免费 Provider、官方发布日期、参数量、上下文信息、RPM、RPD、并发限制、稳定性测试结果，以及模型下线或免费状态变化。

提交信息时请尽量包含：

```text
模型名称：
模型 ID：
模型厂商：
免费 Provider：
官方发布日期：
参数量：
上下文长度：
每分钟调用限制：
每日调用限制：
测试时间：
测试结果：
信息来源：
```

## 免责声明

本项目只负责信息整理和模型推荐，不提供模型服务。

- 免费状态可能随时变化
- Provider 可能修改调用限制
- 模型信息可能存在延迟
- 测试结果不代表 Provider 的服务承诺
- 不建议将免费模型直接用于关键生产业务
- 使用 API 前请确认 Provider 的隐私政策和数据处理方式
- 请通过官方渠道获取 API Key，谨防仿冒网站和钓鱼链接

最后更新时间：2026-09-08
