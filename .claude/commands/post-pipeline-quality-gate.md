---
name: post-pipeline-quality-gate
description: Runs contract validation, token sync, and visual regression in sequence after a Figma/React pipeline run. Usage: /post-pipeline-quality-gate source:<figma:URL|cache:/abs.json|react:/abs.tsx|react-dir:/abs/dir> scope:<block-slug|all> [site-url:https://...] [reference:figma:URL|cache:/abs.json|baseline:/abs/dir]
---

Run the standard post-pipeline quality gate for ACF workflows.

## Steps

1. Validate `{{args}}` contains:
   - `source:`
   - `scope:`
2. Run checks in strict sequence:
   - `/validate-acf-contracts <scope>`
   - `/sync-design-tokens <source> [scope:<scope>]`
   - if `site-url:` is provided, `/visual-regression-block site-url:... scope:... [reference:...]`
3. Return one consolidated summary:
   - contract findings/fixes
   - token sync outcomes
   - visual drift findings (or skipped with reason)

## Input

Quality gate args: {{args}}

