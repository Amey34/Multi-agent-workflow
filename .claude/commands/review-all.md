---
name: review-all
description: Review all blocks in the project in parallel, auto-fix critical issues, and return a consolidated report. Usage: /review-all
---

Review every block in the project simultaneously, auto-fix critical issues, and return a single consolidated report.

## Steps

1. Read `blocks/` to get all block slugs — every directory containing a `block.json` is a block.
2. **Run in parallel for every block simultaneously** — delegate to both agents at once across all blocks:
   - `code-review-agent` — review `blocks/{slug}/`, ACF field group JSON, related SCSS/JS
   - `accessibility-agent` — audit the same block for ARIA, alt text, keyboard navigation, semantic HTML
3. Collect all reports.
4. **Auto-fix loop** — for each block rated "Needs Improvement" or with critical issues:
   - Delegate to `debug-agent` with the block slug and combined critical issues list.
   - After fixes, **re-run both review agents in parallel** for that block.
   - Repeat up to **3 iterations**. If issues remain after 3, log as unresolved and move on.
5. Return one consolidated report covering all blocks:
   - Per-block rating and issue summary
   - Fixes applied per block (with iteration count)
   - Any unresolved issues
   - Overall project health: count of Excellent / Good / Needs Improvement blocks
