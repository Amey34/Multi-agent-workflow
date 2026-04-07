# Project operating rules

This repository contains a custom WordPress theme using modern ACF blocks with `block.json` registration.

## Agents

Use these agents for autonomous multi-step tasks. Do not replicate their work inline.

| Agent | When to use |
|---|---|
| `acf-block-builder` | Building or updating any ACF block from a screenshot, Figma section, or description |
| `browser-qa-tester` | Visual, responsive, accessibility, and SEO QA on a rendered page or block |
| `playwright-block-tester` | Autonomous multi-turn browser testing — rendering, interactions, console errors, responsiveness; use over `/playwright-test` when the task needs several steps or decisions |
| `code-review-agent` | Review ACF blocks and theme code for security, SEO, performance, accessibility, and WordPress best practices |
| `debug-agent` | Identify and fix broken layouts, ACF field issues, JS errors, responsiveness problems, or design mismatches |
| `performance-agent` | Optimize a block for DOM size, CSS efficiency, responsive styles, image loading, and JS footprint |
| `refactor-agent` | Improve block code structure, remove duplication, and improve readability without changing behaviour |
| `accessibility-agent` | Audit and fix accessibility issues — ARIA, alt text, keyboard navigation, semantic HTML |
| `architecture-agent` | Review theme folder structure, block organisation, and asset loading patterns |
| `build-from-figma-agent` | Full pipeline orchestrator — fetch Figma design, create blocks, review, fix, optimize, and test end-to-end |

## Skills

These skills are loaded automatically by agents and commands. Do not restate their rules inline.

| Skill | Type | Purpose |
|---|---|---|
| `acf-standards` | Reference | Block registration, file structure, PHP, SCSS, JS rules (loaded by `acf-block-builder`, `code-review-agent`, and `create-acf-block`) |
| `security-seo` | Reference | Escaping, sanitization, accessibility, SEO, performance (loaded by all agents) |
| `browser-test` | Reference | Browser QA focus areas and output format (loaded by `browser-qa-tester`) |
| `playwright-test` | Reference | Playwright test checklist and output format (loaded by `playwright-block-tester`) |
| `create-acf-block` | Executable | Standalone single-pass block creation (loads `acf-standards` + `security-seo`); invoke as `/create-acf-block` |
| `playwright-test` | Executable + Reference | Lightweight single-pass Playwright test; invoke as `/playwright-test` when a full agent run is not needed |

## Commands

Dedicated command files in `.claude/commands/`. Executable skills above are also directly invocable as `/skill-name`.

| Command | Usage |
|---|---|
| `/figma-block <Figma node URL>` | Fetch a Figma node and build a production-ready ACF block (delegates to `acf-block-builder`) |
| `/review-block <block-slug>` | Run a full code review on a block (delegates to `code-review-agent`) |
| `/debug-block <block-slug> <issue>` | Debug a broken or misbehaving block (delegates to `debug-agent`) |
| `/optimize-block <block-slug>` | Optimize a block for performance (delegates to `performance-agent`) |
| `/figma-pipeline <Figma node URL>` | Run the full Figma → build → review → fix → optimize → test pipeline (delegates to `build-from-figma-agent`) |
| `/review-all` | Review every block in the project in parallel, auto-fix critical issues, return consolidated report |

## Core expectations

- Build production-ready WordPress blocks only.
- Prefer project-scoped work over broad repository scanning.
- Read only the minimum files required for the task.
- Use `intervaults` theme structure and naming as the reference.
- Follow WordPress coding standards, accessibility, security, and SEO best practices.
- Do not print large code dumps in chat when the task is to create/update files.
- When creating a block from a screenshot or Figma section:
  1. infer a descriptive kebab-case slug
  2. create/update files under `blocks/{slug}/`
  3. create/update `acf-json/{slug}-field-group.json`
  4. output only a short manifest and brief notes

## Architecture rules

Full block conventions are in the `acf-standards` and `security-seo` skills. Project-specific decisions:

- Bootstrap is the CSS framework — reuse it where it helps; do not over-structure markup around it.
- Support Gutenberg spacing/color/alignment where appropriate.
- The theme auto-registers all `blocks/*/block.json` directories via `glob` — no manual registration needed when adding a new block.

## Context discipline

Before reading files, first identify the smallest set of relevant files.
Usually allowed:

- the target block folder
- one similar reference block
- `functions.php` or the theme block registration file
- directly related SCSS partials
  Avoid reading unrelated templates, plugins, build artifacts, media, or secrets.

## Security

Never read or expose:

- `.env`
- `.env.*`
- `secrets/**`
- credentials files
- build artifacts
  Escape output properly in PHP.

## SEO + accessibility

- Use semantic headings and sectioning
- avoid heading-level jumps when block content suggests a heading
- support meaningful image alt text
- links must have safe URLs and sensible labels
- avoid empty interactive elements
- keep markup lean
