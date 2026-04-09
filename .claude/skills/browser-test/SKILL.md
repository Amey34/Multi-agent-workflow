---
name: browser-test
description: Run visual and UX checks for a block using browser tools MCP with emphasis on responsiveness, accessibility, and SEO-sensitive markup.
disable-model-invocation: true
---

Use browser tools MCP to validate the target page/block with concise, actionable findings.

## Preconditions

- Require an explicit URL before starting.
- Confirm target scope (single block vs full page).

## Test Checklist

1. Layout and spacing
- alignment consistency
- unexpected gaps/collisions
- clipping and overflow

2. Typography and hierarchy
- heading order sanity
- readable contrast and sizing issues
- CTA prominence consistency

3. Media rendering
- image distortion/cropping
- lazy loading side effects
- broken media or placeholders

4. Interaction visibility
- button/link visibility and labels
- focus states for keyboard users
- obvious hover/click anomalies

5. Responsive behavior
- mobile, tablet, desktop spot checks
- wrapping, stacking, and viewport edge behavior

6. Markup-sensitive SEO/a11y
- obvious heading misuse
- unlabeled interactive elements
- duplicate or unclear call-to-action labels

## Output

Return only:
- concise QA summary
- issue list (severity + repro note)
- recommended fixes

Keep output actionable and brief.
