---
name: optimize-block
description: Optimize a block using performance-agent. Usage: /optimize-block <block-slug>
---

Optimize the specified ACF block for performance and maintainability.

## Steps

1. Identify target slug from `{{args}}`. If missing, ask user for block slug.
2. Delegate to `performance-agent` for focused optimization (DOM, CSS, JS, responsive behavior).
3. Return a consolidated report: optimizations applied and files modified.

## Input

Block slug: {{args}}
