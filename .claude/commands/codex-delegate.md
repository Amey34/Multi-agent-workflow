---
name: codex-delegate
description: Delegate a scoped implementation task to Codex using Codex MCP server tools. Supports optional agent policy context. Usage: /codex-delegate <task> or /codex-delegate agent:<name> task:<work>
---

Delegate to Codex via MCP and review the result.

## Input forms

- `/codex-delegate <task description>` — plain delegation
- `/codex-delegate agent:<name> task:<work>` — delegation with explicit `.codex/agents/<name>.md` policy context

## Steps

1. Run preflight from `docs/claude-codex-preflight.md`.
2. Parse `{{args}}`:
   - if it contains `agent:` and `task:`, extract both values and load `.codex/agents/<agent>.md` as policy context
   - otherwise treat the entire input as the task description
3. Convert task into a precise brief with:
   - goal
   - likely files
   - constraints
   - acceptance criteria
4. Send brief (plus policy context if provided) to Codex MCP server.
5. Validate returned output against acceptance criteria.
6. If needed, run one refined follow-up pass.
7. Return:
   - status
   - files changed
   - commands run
   - blockers

If `agent:task:` format is detected but malformed, stop and ask user to provide `agent:<name> task:<...>` format.
