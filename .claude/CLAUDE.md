# Project operating rules

This repository contains a custom WordPress theme using modern ACF blocks with `block.json` registration.

## Agents

Use these agents for autonomous multi-step tasks. Do not replicate their work inline.

| Agent | When to use |
|---|---|
| `acf-block-builder` | Build or update ACF blocks from screenshot/Figma/description |
| `playwright-block-tester` | Multi-step browser testing for rendering, interactions, console errors, and responsiveness |
| `code-review-agent` | Review ACF blocks and theme code for security, SEO, performance, accessibility, and best practices |
| `debug-agent` | Identify and fix ACF/block issues, layout bugs, JS errors, and responsiveness problems |
| `performance-agent` | Optimize blocks for DOM size, CSS efficiency, image loading, and JS footprint |
| `accessibility-agent` | Audit and fix accessibility issues such as semantics, labels, and keyboard access |
| `architecture-agent` | Review theme folder structure, block organization, and asset loading patterns |
| `build-from-figma-agent` | Full Figma-to-block pipeline orchestration |
| `figma-to-pen-agent` | Convert a Figma node/cache payload into a structured `.pen` design document |
| `figma-react-to-acf-orchestrator` | React-to-ACF pipeline orchestration |
| `react-component-analyzer-agent` | Analyze React structure and propose block split + field mapping hints |
| `acf-field-mapper-agent` | Build ACF field architecture from React-derived structures |
| `acf-contract-auditor-agent` | Validate ACF JSON schema, render contracts, and field/template consistency |
| `design-token-sync-agent` | Normalize and sync design tokens from Figma/React into SCSS/CSS variables |
| `visual-regression-agent` | Screenshot-based visual parity checks across breakpoints vs. source reference |

## Skills

These skills are loaded automatically by agents and commands.

| Skill | Type | Purpose |
|---|---|---|
| `acf-standards` | Reference | Block registration, file structure, PHP, SCSS, JS standards |
| `security-seo` | Reference | Escaping, sanitization, accessibility, SEO, performance checks |
| `playwright-test` | Reference | Playwright test checklist and output format |
| `playwright-test` | Executable + Reference | Single-pass Playwright test via `/playwright-test` |
| `react-to-acf-mapping` | Reference | Rules for translating React components/props into ACF fields/templates |
| `figma-to-acf-mapping` | Reference | Rules for translating Figma node structure into ACF block partitions and fields |
| `acf-contracts` | Reference | Field JSON ↔ template contract validation framework and escaping rules |
| `design-token-bridge` | Reference | Token normalization from Figma/React design values to SCSS/CSS variables |

## Commands

Dedicated command files in `.claude/commands/`. Executable skills are also invocable as `/skill-name`.

| Command | Usage |
|---|---|
| `/figma-block <Figma node URL>` | Draft/prototype path — single block build with contract validation only; use `/figma-pipeline` for full quality-gated output |
| `/figma-cache <Figma node URL>` | Fetch a single Figma node once and store local cache JSON |
| `/figma-to-pen <figma:<URL> | cache:/abs/path.json> [pen:/abs/path/output.pen]` | Convert Figma source directly into `.pen` using figma+pencil MCP (delegates to `figma-to-pen-agent`) |
| `/review-block <block-slug>` | Run full code review on a block (delegates to `code-review-agent`) |
| `/debug-block <block-slug> <issue>` | Debug a broken or misbehaving block (delegates to `debug-agent`) |
| `/optimize-block <block-slug>` | Optimize a block for performance (delegates to `performance-agent`) |
| `/figma-pipeline <Figma node URL | cache:/abs/path.json>` | Run full Figma-to-build pipeline (delegates to `build-from-figma-agent`) |
| `/figma-react-acf-pipeline react:/abs/path.tsx` | Run React-to-ACF pipeline (delegates to `figma-react-to-acf-orchestrator`) |
| `/review-all` | Review every block in parallel, auto-fix critical issues, and return consolidated report |
| `/validate-acf-contracts <block-slug\|all>` | Validate ACF JSON ↔ render.php contract mismatches with optional auto-fix |
| `/sync-design-tokens <source> [scope:]` | Normalize and sync design tokens from Figma/React into block SCSS variables |
| `/visual-regression-block site-url: scope: [reference:]` | Screenshot parity checks across breakpoints vs. Figma/cache/baseline |
| `/post-pipeline-quality-gate source: scope: [site-url:] [reference:]` | Sequenced gate: contract audit → token sync → visual regression after any pipeline run |
| `/codex-delegate <task>` | Delegate scoped implementation task to Codex MCP; supports optional `agent:<name> task:<work>` form for policy-context delegation |

## Core expectations

- Build production-ready WordPress blocks only.
- Prefer project-scoped work over broad repository scanning.
- Read only the minimum files required for the task.
- Use `intervaults` theme structure and naming as the reference.
- Follow WordPress coding standards, accessibility, security, and SEO best practices.
- Do not print large code dumps in chat when the task is to create/update files.

## Architecture rules

- Bootstrap is the CSS framework; reuse it where appropriate.
- Support Gutenberg spacing/color/alignment where appropriate.
- The theme auto-registers all `blocks/*/block.json` directories via `glob`.

## Context discipline

Before reading files, identify the smallest relevant set first.
Usually allowed:
- target block folder
- one similar reference block
- `functions.php` or block registration file
- directly related SCSS partials

Avoid unrelated templates, plugins, build artifacts, media, or secrets.

## Security

Never read or expose:
- `.env`
- `.env.*`
- `secrets/**`
- credential files
- build artifacts

Always escape output in PHP.

## SEO + accessibility

- Use semantic headings and sectioning.
- Avoid heading-level jumps when content suggests hierarchy.
- Support meaningful image alt text.
- Use safe URLs and sensible labels for links.
- Avoid empty interactive elements.
- Keep markup lean.

## Codex MCP Bridge

Codex delegation must run through Codex MCP server tools.

- Plain delegation: `/codex-delegate <task>`
- With agent policy: `/codex-delegate agent:<name> task:<work>`

Guardrails:
- use Codex MCP server (no script bridge)
- no Codex Cloud
- one refinement retry maximum
