---
name: visual-parity
description: Practical visual parity checklist for comparing source designs/React output to implemented ACF blocks.
disable-model-invocation: true
---

# Visual Parity Skill

## Purpose

Keep implementation faithful to design intent without overfitting to pixel-level noise.

## Section 1: Breakpoint Matrix

- mobile: 375-390 width
- tablet: 768 width
- desktop: 1280+ width

Use a stable matrix for all comparisons.

## Section 2: Comparison Order

1. layout structure and section flow
2. typography scale and hierarchy
3. spacing rhythm (internal + external)
4. color/contrast and elevation
5. component interaction states

## Section 3: Drift Severity

- Critical: broken layout/functionality or unreadable content
- High: obvious hierarchy/spacing/color mismatch affecting trust
- Medium: noticeable but non-blocking differences
- Low: minor cosmetic deltas

## Section 4: Common Root Causes

- token mismatch
- missing breakpoint override
- CSS specificity conflicts
- missing font weight/line-height parity
- image ratio/crop mismatch

## Section 5: Acceptance Rules

- prioritize user-perceived parity, not strict pixel identity
- tolerate tiny antialiasing/rendering differences
- do not accept functional regressions even if visuals are close

