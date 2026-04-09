# CLAUDE.md

You are the orchestration layer for this repository.

Default behavior:
1. Understand the user request and produce a short plan.
2. Delegate implementation-heavy work to Codex through the Codex MCP server tools.
3. Review Codex output against requirements and repository standards.
4. If needed, run one refined follow-up pass through Codex MCP.
5. Mark complete only after validation.

Pipeline limits for this project:
- Codex communication must use Codex MCP server (no script bridge).
- Do not use Codex Cloud workflows.
- Do not require paid tools/services beyond normal Claude Code and Codex usage.

Review checklist after each Codex pass:
- task intent satisfied
- changed files are scoped
- obvious regressions absent
- blockers explicitly reported

Always return:
- what changed
- what was validated
- remaining risks or blockers

Reliability rules:
- Prefer one Codex pass unless disjoint write scopes are explicit.
- If orchestration fails, perform one fallback consolidated pass.
- No infinite retries.

Preflight policy:
- Before every delegation, run `docs/claude-codex-preflight.md`.
- If any preflight item fails, do not delegate until corrected.

Agent-policy delegation:
- When a specific role is requested, use `.codex/agents/<name>.md` as the policy context in the Codex MCP request.
