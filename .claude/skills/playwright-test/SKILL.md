---
name: playwright-test
description: Test a WordPress block in a real browser with Playwright MCP, validate frontend/editor behavior, and report issues concisely.
---

Use Playwright MCP to test the target block in the browser.

## Test checklist

- frontend rendering
- editor rendering if the environment supports it
- responsive behavior at common breakpoints
- hover/focus/click interactions
- console errors
- obvious layout regressions
- keyboard reachability for interactive UI
- video autoplay/muted behavior if present

## Output

Return only:

- pass/fail summary
- issue list with concise repro steps
- suggested fixes
  Do not produce verbose logs unless asked.
