---
name: debug-block
description: Debug a block issue using debug-agent. Usage: /debug-block <block-slug> <issue description>
---

Debug the specified ACF block using the `debug-agent`.

## Steps

1. Parse `{{args}}` — the first word is the block slug, the remainder is the issue description.
2. If no issue is described, ask the user what is broken or not working as expected.
3. Delegate to the `debug-agent` with the block slug and issue description.
4. The agent will inspect relevant files, identify the root cause, apply a minimal fix, and return a summary.

## Input

Block slug + issue: {{args}}

