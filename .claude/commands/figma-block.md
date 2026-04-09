---
name: figma-block
description: "DRAFT/PROTOTYPE PATH — builds a single ACF block from a Figma node with contract validation only. For full quality-gated output (review, token sync, optimization, Playwright) use /figma-pipeline instead. Usage: /figma-block <Figma node URL>"
---

Build a production-ready ACF block from the provided Figma node link.

## Steps

1. Validate `{{args}}` contains a Figma node URL (`figma.com/design/...?...node-id=...`).
2. Parse file key and node-id, then convert node-id from dash format (`543-4196`) to colon format (`543:4196`) for node-view tools.
3. Use the `figma` MCP server to fetch only the target node (never the whole file if node-id is present).
4. If the file is not registered, call `add_figma_file` once, then retry node fetch once.
5. If node fetch returns 429, wait 15 seconds and retry once; if it fails again, stop and report the rate-limit error.
6. Analyze design and infer a descriptive kebab-case block slug.
7. Delegate to `acf-block-builder` to implement files.
8. Ensure output follows project ACF, security, accessibility, SEO, and responsive standards.
9. After builder completes, automatically run `/validate-acf-contracts <slug>` to catch any field/template mismatches before reporting done.
10. Output only a manifest of created/updated files, contract validation outcome, and brief notes. Do not print raw Figma JSON.

## Input

Figma node URL: {{args}}