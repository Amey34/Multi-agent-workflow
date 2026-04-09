---
name: figma-pipeline
description: Full Figma-to-block pipeline - fetch/cached design, create ACF blocks, review, fix, optimize and test. Usage: /figma-pipeline <Figma node URL | cache:/absolute/path/to/cache.json>
---

Run the full Figma-to-block pipeline from either a Figma node URL or a local cached node JSON file.

## Steps

1. Validate `{{args}}`:
- if it starts with `cache:`, treat the remainder as a local cache JSON path.
- otherwise, treat it as a Figma node URL (`figma.com/design/...?...node-id=...`).
2. Delegate the entire pipeline to `build-from-figma-agent`, passing the original input as-is.
3. The agent will handle all stages autonomously:
- Fetch the Figma node via local `figma` MCP server OR load cached JSON
- Analyze the design and identify block sections
- Create all ACF block files via `acf-block-builder`
- Review each block via `code-review-agent`
- Fix any critical issues via `debug-agent` (conditional)
- Optimize each block via `performance-agent`
- Run interaction/responsive tests via `playwright-block-tester`
4. Surface the consolidated report returned by the agent.

## Input

Figma node URL or cache path: {{args}}
