---
name: figma-to-pen
description: Convert a Figma node URL or cached node JSON into a .pen design document using figma + pencil MCP. Usage: /figma-to-pen <figma:<Figma node URL> | cache:/abs/path.json> [pen:/abs/path/output.pen]
---

Convert a Figma source into a Pencil `.pen` document through the dedicated bridge agent.

## Input forms

- `figma:<Figma node URL>`
- `cache:/absolute/path/to/node-cache.json`
- optional output override: `pen:/absolute/path/to/output.pen`

Examples:
- `/figma-to-pen figma:https://www.figma.com/design/<fileKey>/...?...node-id=543-4196`
- `/figma-to-pen cache:/c/xampp/htdocs/acf_blocks_practice/.claude/figma-cache/<fileKey>__543:4196.json`
- `/figma-to-pen figma:https://www.figma.com/design/<fileKey>/...?...node-id=543-4196 pen:/c/xampp/htdocs/acf_blocks_practice/designs/home-hero.pen`

## Steps

1. Validate `{{args}}` contains either `figma:` or `cache:`.
2. Preserve the original input string (and optional `pen:` target) without rewriting user paths.
3. Delegate the operation to `figma-to-pen-agent`.
4. Require output to include:
- status
- `.pen` file path
- top-level node manifest
- layout issue summary
- screenshot/export paths (when generated)
5. Surface only the consolidated summary; do not print raw Figma payloads.

## Input

Source + optional pen path: {{args}}
