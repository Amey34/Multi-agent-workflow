---
name: optimize-block
description: Optimize a block by running performance-agent and refactor-agent in parallel. Usage: /optimize-block <block-slug>
---

Optimize the specified ACF block for performance and code quality.

## Steps

1. Identify the target block slug from `{{args}}`. If no slug is provided, ask the user which block to optimize.
2. **Run in parallel** — delegate to both agents simultaneously:
   - `performance-agent` — audit and optimize DOM size, CSS, JS, images, and responsive styles
   - `refactor-agent` — improve code structure, remove duplication, improve readability
3. Collect both reports.
4. Return a consolidated report: optimizations applied, refactors made, and files modified.

## Input

Block slug: {{args}}
