---
name: playwright-test
description: Real-browser QA checklist for block-level rendering, interaction, responsiveness, and runtime health.
---

Use this skill for focused Playwright-based validation.

## Preconditions

- explicit URL is mandatory
- define target scope (specific block/section/page)

## Test Checklist

1. Rendering
- expected content and structure appear
- no obvious clipping/overlap defects

2. Responsiveness
- test representative mobile/tablet/desktop widths
- check wrapping, overflow, and layout shifts

3. Interactions
- hover/focus/click behavior
- controls toggle/navigate as intended

4. Runtime health
- inspect console for errors/warnings that affect UX

5. Keyboard basics
- interactive elements reachable by tab
- focus visible and progression sane

## Output Contract

Return only:
- pass/fail summary
- issues with concise repro steps
- minimal suggested fixes

Do not include noisy logs unless specifically requested.
