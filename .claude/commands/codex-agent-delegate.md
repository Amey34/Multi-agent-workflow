---
name: codex-agent-delegate
description: Delegate a task to Codex via MCP using a specific policy from `.codex/agents/*.md`. Usage: /codex-agent-delegate agent:<agent-name> task:<work>
---

Delegate to Codex with explicit agent policy context through MCP.

## Input format

`agent:<agent-name> task:<task description>`

## Steps

1. Run preflight from `docs/claude-codex-preflight.md`.
2. Parse `{{args}}` into:
- `agent`
- `task`
3. Load `.codex/agents/<agent>.md` as policy context.
4. Send policy + task to Codex MCP server.
5. Validate returned output against acceptance criteria.
6. Return:
- status
- files changed
- commands run
- blockers

If parsing fails, stop and ask user to provide `agent:<name> task:<...>` format.
