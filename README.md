# parallel-research

并行网络调研 skill：把一个宽泛的调研问题拆分为多个互不重叠、可独立回答的搜索任务，通过 `grok-search` MCP 服务器的 `search_by_grok` 工具在单条消息中并行执行，最后汇总为去重、附来源链接的中文研究报告。

## 文件位置

- Skill 定义：`.agents/skills/parallel-research/SKILL.md`
- 将该文件按相同路径放入你的项目 `.agents/skills/parallel-research/` 目录即可使用。

## 用途

适用于需要广泛调查某个话题、对比同一问题的多个侧面、或明确要求多路并行搜索的调研任务。产出物是一份简明、有来源支撑的综述，而不是代码改动。

## 触发条件

- 用户要求广泛调查某个话题。
- 用户希望对比一个问题的多个方面。
- 用户明确要求以多次并行搜索的方式进行调研。

## 前置条件

使用本 skill 前，需要先安装并配置 [grok-search-mcp](https://github.com/lililibonaba-stack/grok-search-mcp) —— 即提供 `search_by_grok` 工具的 MCP 服务器：

1. 安装 [uv](https://docs.astral.sh/uv/) 并确认其在 PATH 中可用（用 `uv --version` 验证）。
2. 获取 [cheapapis.net](https://cheapapis.net) 的 API key，创建方式见该仓库的 [get_apikey_tutorial.md](https://github.com/lililibonaba-stack/grok-search-mcp/blob/main/get_apikey_tutorial.md)。
3. 克隆或下载 grok-search-mcp 仓库，在你的 MCP 客户端中注册名为 `grok-search` 的本地服务器：命令为 `uv run --with fastmcp==4.0.2 --with httpx==0.28.1 python <grok_search.py 的完整路径>`，并在 `environment`/`env` 中设置 `CHEAPAPIS_API_KEY`。Kilo、Claude Desktop、Cursor 的完整配置示例见其 [README](https://github.com/lililibonaba-stack/grok-search-mcp#configuration)。
4. API key 只放在客户端的 `environment`/`env` 块或系统环境变量中，不要提交到 git。

## 依赖

- `grok-search` MCP 服务器提供的 `search_by_grok` 工具（部分客户端中名称带前缀，例如 `mcp__grok-search__search_by_grok`）；安装与配置方式见上方[前置条件](#前置条件)。
- 该工具不可用时，skill 会停止并告知无法执行工作流，不会静默替换为其他搜索机制。

## 核心工作流

1. **界定调研范围**：确定主题、时间边界、地域范围与输出要求；将请求拆分为两个以上互不重叠、可独立回答的子问题；简单的单一查询无需拆分。
2. **并行执行搜索**：在单条消息中一次性发出全部 `search_by_grok` 调用（每轮 2-4 个）；每条查询自成一体，包含主题、具体角度与时间范围；查询中不混入输出语言或报告格式要求；失败或结果单薄的查询换措辞重试一次，仍缺失的如实报告，不编造。
3. **汇总与核验**：合并重叠发现、去除重复主张；区分已核实事实、有出处的立场、分析与未解决主张；优先引用官方等一手来源；来源间冲突时明确指出而非平均处理；分歧点至多追加一次针对性搜索。
4. **输出报告**：默认用中文回复，包含执行摘要、按调研角度或时间线分节的正文、信息截止日期与不确定性说明、关键主张的内联来源链接。

## 输出特点

- 简明、有来源支撑的中文报告，关键主张保留来源 URL，必要时附紧凑的来源列表。
- 明确区分事实、立场、分析与未解决的主张，不把模型推测当作已确立的事实。
- 说明信息截止日期与来源冲突；仅在有助于说明调研方法时提及并行搜索次数。
- 结果篇幅与请求相称，不包含原始工具输出或无关实现细节。
