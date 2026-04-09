---
name: codex-executor
description: Detailed delegation workflow for sending scoped tasks to Codex MCP with preflight, validation, and bounded iteration.
---

# Codex Executor Skill

## Purpose

Standardize reliable delegation of implementation-heavy tasks through Codex MCP.

## Delegation Principles

- scope must be explicit
- acceptance criteria must be testable
- retries must be bounded
- output must be validated before acceptance

## Phase 1: Preflight

Always run `docs/claude-codex-preflight.md` before delegation.

If preflight fails:
- do not delegate
- report failure reason clearly

## Phase 2: Brief Construction

Transform `{{args}}` into a strict brief containing:
- objective
- scope boundaries
- likely file set
- constraints/guardrails
- acceptance criteria
- explicit non-goals

## Phase 3: Optional Policy Injection

If user requests specific role behavior:
- include `.codex/agents/<name>.md` context
- ensure role policy does not conflict with repository constraints

## Phase 4: MCP Delegation

- send task through Codex MCP tools only
- do not use cloud bridges or script wrappers

## Phase 5: Validation

Validate returned result against:
- acceptance criteria
- scope boundaries
- regression risk
- required output format

## Phase 6: Single Refinement Pass (Optional)

If needed:
- run one targeted correction pass
- avoid open-ended loops

## Final Output Contract

Return:
- status
- files changed
- commands run
- blockers
- brief risk note if validation incomplete

## Failure Handling

If delegation fails:
- report exact failure stage
- include actionable next step
- avoid repeating same failing command blindly
