---
name: sync-design-tokens
description: Normalize and sync design tokens from Figma/React sources into ACF block styles. Usage: /sync-design-tokens <figma:URL|cache:/abs.json|react:/abs.tsx|react-dir:/abs/dir> [scope:block-slug|all]
---

Run design-token synchronization to reduce style drift and hardcoded values.

## Steps

1. Validate that `{{args}}` includes one supported source prefix:
   - `figma:`, `cache:`, `react:`, or `react-dir:`
2. Delegate execution to `design-token-sync-agent` with the original arguments.
3. Return the agent report with:
   - token mapping table
   - files updated
   - drift/deferred mapping notes

## Input

Source and optional scope: {{args}}

