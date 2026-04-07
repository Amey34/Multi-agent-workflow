---
name: review-block
description: Review a block using code-review-agent + accessibility-agent in parallel, then auto-fix critical issues. Usage: /review-block <block-slug>
---

Review the specified ACF block, then auto-fix any critical issues found.

## Steps

1. Identify the target block slug from `{{args}}`. If no slug is provided, ask the user which block to review.
2. **Run in parallel** — delegate to both agents simultaneously:
   - `code-review-agent` — review `blocks/{slug}/`, ACF field group JSON, related SCSS/JS
   - `accessibility-agent` — audit the same block for ARIA, alt text, keyboard navigation, semantic HTML
3. Collect both reports.
4. **Auto-fix loop** — if either report flags critical issues or a "Needs Improvement" rating:
   - Delegate to `debug-agent` with the block slug and the combined list of critical issues.
   - After fixes are applied, **re-run Step 2 in parallel** (both agents again).
   - If issues persist, fix again and re-review. Repeat up to **3 iterations total**.
   - If issues remain after 3 iterations, stop and report what could not be resolved — do not ask the user to intervene mid-loop.
5. Return a consolidated report: final review rating, accessibility findings, fixes applied per iteration, and any unresolved issues.

## Input

Block slug: {{args}}
