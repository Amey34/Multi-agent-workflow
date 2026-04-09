# .claude Workspace Guide

This folder contains the Claude-side operating system for this repository:
- **Agents**: specialized execution roles
- **Skills**: reusable standards/checklists/frameworks
- **Commands**: slash-command style workflows that orchestrate agents

## Folder Layout

```text
.claude/
  agents/
  skills/
  commands/
  CLAUDE.md
  settings.json
```

## Agents

| Agent | Purpose | Typical Use |
|---|---|---|
| `accessibility-agent` | Accessibility audit + remediation for ACF blocks | Keyboard/screen-reader/semantic fixes |
| `acf-block-builder` | End-to-end block implementation | Build block files + ACF JSON from design intent |
| `acf-field-mapper-agent` | ACF schema architecture | Convert UI/content structure into field groups |
| `architecture-agent` | Theme/block architecture review | Identify maintainability and structural risks |
| `build-from-figma-agent` | Full Figma-to-ACF pipeline orchestrator | Build blocks from a Figma node or cached payload |
| `code-review-agent` | Risk-focused code review | Security/correctness/a11y/perf/maintainability findings |
| `debug-agent` | Root-cause debugging + minimal fixes | Fix broken rendering, logic, JS, or field mismatch issues |
| `figma-react-to-acf-orchestrator` | React-to-ACF multi-agent coordinator | Run full analysis-to-build-to-QA pipeline for React input |
| `performance-agent` | Block performance optimization | Reduce DOM/CSS/JS cost without regressions |
| `playwright-block-tester` | Browser QA via Playwright MCP | Validate rendering/interactions/responsive behavior |
| `react-component-analyzer-agent` | Read-only React decomposition | Produce partition + field candidate blueprint |

## Skills

| Skill | Purpose | Used By |
|---|---|---|
| `acf-standards` | Canonical standards for ACF block structure, escaping, naming, and integration | Builder/mapper/review architecture-related agents |
| `codex-executor` | Delegation workflow standard for Codex MCP tasks | `codex-*` command paths |
| `playwright-test` | Browser QA checklist and reporting format | `playwright-block-tester` |
| `react-to-acf-mapping` | Framework for converting React patterns to ACF schema/template | React analyzer + field mapper + Figma/React pipeline roles |
| `security-seo` | Security escaping + semantic SEO + accessibility alignment checklist | Review/debug/perf/a11y and build agents |

## Commands

| Command | Input | What It Does |
|---|---|---|
| `/codex-delegate` | `<task>` | Delegates a scoped implementation task to Codex MCP |
| `/codex-agent-delegate` | `agent:<name> task:<work>` | Delegates to Codex MCP with explicit `.codex/agents/*.md` policy |
| `/debug-block` | `<block-slug> <issue>` | Runs focused debug flow via `debug-agent` |
| `/figma-block` | `<Figma node URL>` | Builds one production-ready ACF block from Figma node |
| `/figma-cache` | `<Figma node URL>` | Fetches one Figma node and caches JSON in `.claude/figma-cache/` |
| `/figma-pipeline` | `<Figma URL \| cache:/abs/path.json>` | Full Figma-to-block pipeline via `build-from-figma-agent` |
| `/figma-react-acf-pipeline` | `react:/abs/file.tsx` or `react-dir:/abs/dir` | Full React-to-ACF conversion via orchestrator |
| `/optimize-block` | `<block-slug>` | Runs optimization pass via `performance-agent` |
| `/review-block` | `<block-slug>` | Parallel code + accessibility review with auto-fix loop |
| `/review-all` | *(no args)* | Parallel review across all blocks with iterative critical-fix loops |

## Suggested Workflow

1. Build from design:
   - `/figma-block ...` for one block
   - `/figma-pipeline ...` for end-to-end sections/pipeline
2. Harden quality:
   - `/review-block <slug>` during development
   - `/review-all` before release
3. Targeted improvements:
   - `/debug-block <slug> <issue>`
   - `/optimize-block <slug>`
4. React migration:
   - `/figma-react-acf-pipeline react:/...`

## Notes

- `CLAUDE.md` contains project-level behavior and constraints.
- `settings.json` exists and is currently empty.
- Commands are designed to keep scope tight (block-level by default) and automate review/fix loops where configured.
