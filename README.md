# parallel-research

This skill is similar to Perplexity's Deep Research, but it is built on grok's powerful search capability. In some scenarios, combining GPT's strong reasoning with grok's powerful search can match or even outperform the research performance of Perplexity's Deep Research.

## File Location

- Skill definition: `.agents/skills/parallel-research/SKILL.md`
- Place the file at the same path in your project's `.agents/skills/parallel-research/` directory to use it.

## Purpose

Suitable for research tasks that require broad investigation of a topic, comparison of multiple facets of the same question, or explicitly require multiple parallel searches. The output is a concise, source-backed overview rather than code changes.

## Trigger Conditions

- The user asks to broadly investigate a topic.
- The user wants to compare multiple aspects of a question.
- The user explicitly requests research conducted via multiple parallel searches.

## Prerequisites

Before using this skill, install and configure [grok-search-mcp](https://github.com/lililibonaba-stack/grok-search-mcp) — the MCP server that provides the `search_by_grok` tool:

1. Install [uv](https://docs.astral.sh/uv/) and confirm it is available in PATH (verify with `uv --version`).
2. Get an API key from [cheapapis.net](https://cheapapis.net); see the repo's [get_apikey_tutorial.md](https://github.com/lililibonaba-stack/grok-search-mcp/blob/main/get_apikey_tutorial.md) for how to create one.
3. Clone or download the grok-search-mcp repository, and register a local server named `grok-search` in your MCP client with the command `uv run --with fastmcp==4.0.2 --with httpx==0.28.1 python <full path to grok_search.py>`, setting `CHEAPAPIS_API_KEY` in the `environment`/`env` block. See its [README](https://github.com/lililibonaba-stack/grok-search-mcp#configuration) for full configuration examples for Kilo, Claude Desktop, and Cursor.
4. Keep the API key only in the client's `environment`/`env` block or system environment variables; never commit it to git.

## Dependencies

- The `search_by_grok` tool provided by the `grok-search` MCP server (in some clients the tool name carries a prefix, e.g. `mcp__grok-search__search_by_grok`); for installation and configuration, see [Prerequisites](#prerequisites) above.
- If the tool is unavailable, the skill stops and reports that it cannot execute the workflow; it will not silently substitute another search mechanism.

## Core Workflow

1. **Scope the research**: define the topic, time boundaries, geographic scope, and output requirements; split the request into two or more non-overlapping, independently answerable sub-questions; a simple single query does not need splitting.
2. **Run searches in parallel**: issue all `search_by_grok` calls in a single message (2-4 per round); each query must be self-contained, including the topic, the specific angle, and the time range; do not mix output-language or report-format requirements into queries; retry a failed or thin query once with rephrasing, and report anything still missing honestly instead of fabricating.
3. **Synthesize and verify**: merge overlapping findings and deduplicate claims; distinguish verified facts, sourced positions, analysis, and unresolved claims; prefer primary sources such as official ones; when sources conflict, call out the conflict explicitly rather than averaging it; add at most one additional targeted search for points of disagreement.
4. **Produce the report**: reply in Chinese by default, including an executive summary, a body organized by research angle or timeline, the information cutoff date with uncertainty notes, and inline source links for key claims.

## Output Characteristics

- A concise, source-backed Chinese report with source URLs preserved for key claims, plus a compact source list when needed.
- Clearly distinguishes facts, positions, analysis, and unresolved claims; never presents model speculation as established fact.
- States the information cutoff date and source conflicts; mentions the number of parallel searches only when it helps explain the research method.
- Report length is proportional to the request; no raw tool output or irrelevant implementation details.
