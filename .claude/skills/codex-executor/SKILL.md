---
name: codex-executor
description: Delegate scoped implementation tasks to Codex MCP with preflight checks and bounded validation loops.
---

Use this skill to route implementation-heavy work through Codex MCP predictably.

## Workflow

1. Preflight
- run `docs/claude-codex-preflight.md`
- stop delegation if preflight fails

2. Build delegation brief from `{{args}}`
Include:
- objective
- precise scope
- likely file paths
- constraints/guardrails
- acceptance criteria

3. Optional role policy
- if user requests specific role, include `.codex/agents/<name>.md`

4. Delegate via Codex MCP
- use MCP tools directly
- no script bridge
- no cloud workflow

5. Validate response
- compare output to acceptance criteria
- verify scope and obvious regression risk

6. Optional refinement
- run one targeted follow-up only when needed
- avoid unbounded retry loops

## Final Output Contract

- status
- files changed
- commands run
- blockers
