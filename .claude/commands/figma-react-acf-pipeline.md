---
name: figma-react-acf-pipeline
description: Separate orchestrated pipeline for converting React code into production-ready ACF blocks. Usage: /figma-react-acf-pipeline react:/abs/path.tsx
---

Run the dedicated React-to-ACF conversion pipeline.

## Input forms

- `react:/absolute/path/to/component.tsx`
- `react-dir:/absolute/path/to/components`

Examples:
- `/figma-react-acf-pipeline react:/c/xampp/htdocs/acf_blocks_practice/wp-content/themes/abp1/react-src/Hero.tsx`
- `/figma-react-acf-pipeline react-dir:/c/xampp/htdocs/acf_blocks_practice/wp-content/themes/abp1/react-src`

## Steps

1. Validate input contains at least one React source (`react:` or `react-dir:`).
2. Delegate execution to `figma-react-to-acf-orchestrator` with the original arguments.
3. Require an explicit site URL before running browser QA and Playwright testing.
4. Return the orchestrator's consolidated report:
- block partition plan
- field architecture
- files created/updated
- review/fix summary
- QA/testing results
