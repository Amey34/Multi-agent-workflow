---
name: visual-regression-block
description: Run visual parity checks for a block/page using screenshot comparisons. Usage: /visual-regression-block site-url:https://... scope:<block-slug|page|all> [reference:figma:URL|cache:/abs.json|baseline:/abs/dir]
---

Run visual regression checks to detect drift between source intent and rendered output.

## Steps

1. Validate `{{args}}` includes:
   - `site-url:`
   - `scope:`
2. Delegate to `visual-regression-agent` with all provided arguments.
3. Return:
   - breakpoint-level drift summary
   - severity-ranked findings
   - likely root causes and smallest-fix suggestions

## Input

Visual test args: {{args}}

