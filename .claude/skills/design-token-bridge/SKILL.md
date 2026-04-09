---
name: design-token-bridge
description: Token normalization guidance for translating Figma/React styling intent into durable ACF block variables and SCSS usage.
disable-model-invocation: true
---

# Design Token Bridge Skill

## Purpose

Provide a deterministic method for converting ad hoc visual values into maintainable theme/block tokens.

## Section 1: Token Hierarchy

- global tokens: brand color, type scale, spacing scale
- semantic tokens: surface, text-muted, accent, border-subtle
- block tokens: exceptional values local to one block

Prefer global -> semantic -> block fallback order.

## Section 2: Mapping Heuristics

- same meaning, different value: consolidate if visual delta is negligible
- same value, different meaning: keep semantic aliases
- one-off decorative effects: keep local unless reused >= 2 blocks

## Section 3: Typography Rules

- map heading/body/caption roles before mapping exact sizes
- preserve hierarchy contrast across breakpoints
- avoid introducing arbitrary font families per block

## Section 4: Spacing and Radius

- normalize to a small, predictable scale
- reduce near-duplicates (for example 23px vs 24px)
- keep intentional asymmetry only when visually meaningful

## Section 5: Implementation Pattern

- define variables at theme scope where possible
- consume via block-scoped CSS variables or SCSS variables
- avoid hardcoded literals in deeply repeated selectors

## Section 6: Verification

- compare key breakpoints after token migration
- watch for line-height and overflow side effects
- ensure fallbacks exist for missing variables

