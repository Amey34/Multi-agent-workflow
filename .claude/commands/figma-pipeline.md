---
name: figma-pipeline
description: Full Figma-to-block pipeline — fetch design, create ACF blocks, review, fix, optimize and test. Usage: /figma-pipeline <Figma node URL>
---

Run the full Figma-to-block pipeline for the provided Figma node URL.

## Steps

1. Validate that `{{args}}` contains a Figma URL (`figma.com/design/...`). If missing, ask the user to provide one.
2. Delegate the entire pipeline to **`build-from-figma-agent`**, passing the Figma URL as the input.
3. The agent will handle all stages autonomously:
   - Fetch the Figma node via the local `figma` MCP server
   - Analyse the design and identify block sections
   - Create all ACF block files via `acf-block-builder`
   - Review each block via `code-review-agent`
   - Fix any critical issues via `debug-agent` (conditional)
   - Optimize each block via `performance-agent`
   - Run visual QA via `browser-qa-tester`
   - Run interaction tests via `playwright-block-tester`
4. Surface the consolidated report returned by the agent.

## Input

Figma node URL: {{args}}

