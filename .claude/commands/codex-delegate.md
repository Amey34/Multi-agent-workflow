---
name: codex-delegate
description: Delegate a scoped implementation task to Codex using Codex MCP server tools. Usage: /codex-delegate <task>
---

Delegate `{{args}}` to Codex via MCP and review the result.

## Steps

1. Run preflight from `docs/claude-codex-preflight.md`.
2. Convert `{{args}}` into a precise brief with:
- goal
- likely files
- constraints
- acceptance criteria
3. Send brief to Codex MCP server.
4. Validate returned output against acceptance criteria.
5. If needed, run one refined follow-up pass.
6. Return:
- status
- files changed
- commands run
- blockers
