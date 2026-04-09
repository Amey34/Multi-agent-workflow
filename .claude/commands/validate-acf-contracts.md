---
name: validate-acf-contracts
description: Validate and optionally auto-fix ACF JSON <-> render.php contract mismatches. Usage: /validate-acf-contracts <block-slug|all>
---

Run contract auditing for ACF schema and block templates.

## Steps

1. Parse `{{args}}` as either:
   - a specific block slug, or
   - `all` for full theme contract audit.
2. Delegate to `acf-contract-auditor-agent` with the same scope.
3. If critical mismatches are fixed, summarize fixes and residual risks.
4. If unresolved blockers remain, return explicit file-level blockers.

## Input

Audit scope: {{args}}

