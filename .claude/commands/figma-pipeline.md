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
- Validate ACF schema/template contracts via `acf-contract-auditor-agent`
- Sync design tokens via `design-token-sync-agent`
- Review each block via `code-review-agent`
- Fix any critical issues via `debug-agent` (conditional)
- Optimize each block via `performance-agent`
- Run visual parity checks via `visual-regression-agent` when reference/baseline is provided
- Run interaction/responsive tests via `playwright-block-tester`
4. After pipeline completion, run the post gate command:
- `/post-pipeline-quality-gate source:<same-input> scope:all [site-url:...] [reference:...]`
5. Surface the consolidated report returned by the agent plus the post-gate summary.

## Input

Figma node URL or cache path: {{args}}
