---
name: figma-cache
description: Fetch a Figma node once and cache it locally for offline/repeat pipeline runs. Usage: /figma-cache <Figma node URL>
---

Fetch and cache a single Figma node so future runs can use local JSON instead of repeated MCP/API calls.

## Steps

1. Validate that `{{args}}` contains a Figma node URL with `node-id`.
2. Parse:
- file key from `/design/<fileKey>/...`
- node ID from query param `node-id`, then convert dash to colon for API calls.
3. Fetch only that node using the `figma` MCP server.
4. If the file is not registered, call `add_figma_file` once, then retry node fetch once.
5. If fetch returns 429, wait 15 seconds and retry once; if it still fails, stop and report the error.
6. Create directory `.claude/figma-cache/` if missing.
7. Save node JSON to:
`/.claude/figma-cache/<fileKey>__<nodeIdColon>.json`
8. Return only:
- cache file path
- file key
- node ID used
- short summary of top-level frame/section names

Do not paste raw JSON in chat.

## Input

Figma node URL: {{args}}
