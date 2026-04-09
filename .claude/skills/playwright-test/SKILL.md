---
name: playwright-test
description: Test a WordPress block in a real browser with Playwright MCP, validate frontend/editor behavior, and report issues concisely.
---

Use Playwright MCP for deterministic functional and visual checks.

## Preconditions

- require explicit page URL
- confirm target scope and expected behavior

## Test Checklist

1. Rendering
- frontend visible state
- editor preview (if available)

2. Responsive behavior
- representative mobile/tablet/desktop viewports
- wrapping, clipping, horizontal scroll checks

3. Interaction checks
- hover/focus/click behavior
- toggles, tabs, accordion, sliders (if present)

4. Console health
- JS errors/warnings impacting behavior

5. Keyboard access
- focus reachability
- actionable controls operable via keyboard

6. Media behavior
- autoplay/muted expectations for video
- poster/load behavior where relevant

## Output

Return only:
- pass/fail summary
- issue list with concise repro steps
- suggested fixes

Do not include verbose logs unless requested.
