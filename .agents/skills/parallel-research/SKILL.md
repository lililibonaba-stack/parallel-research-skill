---
name: parallel-research
description: >-
  Research a current-events or knowledge question by decomposing it into
  independent search tasks, running them through the grok-search MCP tool
  (search_by_grok), then producing a deduplicated, source-linked synthesis.
  Use when the user asks to investigate a topic broadly, compare multiple
  aspects, or explicitly wants parallel research with multiple searches.
---

# Parallel Research Workflow

Use this skill for research tasks that benefit from independent web searches.
The deliverable is a concise, source-backed synthesis, not code changes.

The search backend is the `search_by_grok` tool from the `grok-search` MCP
server (clients may prefix the name, e.g. `mcp__grok-search__search_by_grok`).
If that tool is unavailable, stop and tell the user the workflow cannot run;
do not silently substitute a different search mechanism.

## 1. Define the research scope

- Identify the topic, the user's time boundary, geographic scope, and desired
  output language and detail level.
- If no time boundary is given for a current-events request, interpret
  "latest" as the most recent information available today and state the
  cutoff date in the final answer.
- Split the request into two or more non-overlapping questions. Prefer
  complementary angles such as chronology and official statements, or
  economic effects and positions of major stakeholders.
- Make every subtask answerable independently. For a single simple lookup,
  skip the split and make one search.

## 2. Run the searches

- Issue all searches in parallel in a single message: one `search_by_grok`
  call per subtask. Keep the fan-out modest (2-4 calls per round; more only
  when the topic genuinely needs it).
- Write each query to stand alone: include the topic, the specific angle, and
  any time frame, because each call has no memory of the others.
- Do not include instructions about output language or report format in the
  queries; raw findings are raw material, and the synthesis is yours to write.
- If a call fails or returns thin results, retry that query once with adjusted
  wording before giving up. Report persistent gaps honestly; never fabricate
  missing findings.

## 3. Synthesize and verify

- Combine overlapping findings and remove duplicate claims.
- Separate verified facts, attributed positions, analysis, and unresolved
  claims. Never present a model's speculation as established fact.
- Prefer primary sources such as official government, intergovernmental,
  company, court, or research-institution pages. Use reputable reporting to
  provide context, not as the only support for consequential claims.
- Check that dates, names, numerical values, and the meaning of quotations are
  consistent across sources. Call out conflicts rather than averaging them.
- When two searches disagree, run at most one targeted follow-up search on the
  disputed point instead of silently picking a side.
- Preserve source URLs next to the claims they support and include a compact
  source list when useful.

## 4. Final response format

Respond in Chinese unless the user requested another language. Include:

1. A one-paragraph executive summary.
2. Short sections organized by the research angles or the topic's chronology.
3. The information cutoff date and relevant uncertainty or source conflicts.
4. Inline source links for material claims.
5. A brief note on how many parallel searches were run, only when it helps
   explain the research method.

Keep the result proportional to the request. Do not include raw tool output or
irrelevant implementation details.
