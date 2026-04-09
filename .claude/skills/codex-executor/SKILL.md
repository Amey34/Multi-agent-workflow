---
name: codex-executor
description: Delegate implementation tasks to Codex via Codex MCP server, then review and finalize.
---

Delegate implementation-heavy work to Codex MCP with controlled scope and clear acceptance checks.

## Workflow

1. Run preflight
- apply `docs/claude-codex-preflight.md`
- confirm constraints and target paths

2. Build Codex brief from `{{args}}`
Include:
- goal
- exact scope
- likely files
- constraints
- acceptance criteria

3. Add role policy when requested
- if user asked for a specific role, include `.codex/agents/<name>.md` context

4. Execute via Codex MCP
- use MCP server tools directly
- do not use cloud or wrapper scripts

5. Validate result
- compare returned changes against acceptance criteria
- ensure output format compliance if required

6. Optional refinement pass
- if criteria not met, run one scoped second pass
- avoid multi-pass churn

7. Return final summary
- status
- files changed
- commands run
- blockers

## Rules

- keep delegation prompts specific and bounded
- avoid endless retry loops
- escalate blockers with concrete context
