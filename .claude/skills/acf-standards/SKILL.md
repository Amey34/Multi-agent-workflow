---
name: acf-standards
description: Comprehensive production standards for ACF Gutenberg block implementation in this repository.
disable-model-invocation: true
---

# ACF Standards Skill

This is the canonical reference for building or updating ACF blocks.

## Purpose

Ensure every block is consistent, secure, maintainable, and editor-friendly.

## Section 1: Registration Standards

- prefer `block.json` registration patterns
- avoid deprecated APIs
- keep metadata stable and descriptive

Required metadata checks:
- `apiVersion`
- `name`, `title`, `category`
- `supports`
- `acf.renderTemplate`

## Section 2: Required File Structure

For each block, expect:
- `blocks/{slug}/block.json`
- `blocks/{slug}/render.php`
- `blocks/{slug}/_style.scss`
- `blocks/{slug}/script.js` only if behavior requires
- `acf-json/{slug}-field-group.json`

## Section 3: Slug and Naming Conventions

- use descriptive kebab-case slugs
- enforce slug consistency across:
  - folder
  - block name
  - field names
  - CSS namespace
  - JSON file naming

Avoid placeholders and temporary names in final files.

## Section 4: ACF Field Design Rules

- use import-ready local JSON format
- stable and unique field keys
- slug-prefixed field names
- avoid unnecessary deep nesting
- repeaters only for true repeated structures
- group fields for cohesive optional subsets
- explicit return formats for images/links/selects

## Section 5: Template Rules (`render.php`)

- semantic HTML first
- context-appropriate escaping for all dynamic output
- null-safe field handling
- minimal wrapper depth
- predictable conditional logic

## Section 6: SCSS Rules

- scope styles to block namespace
- include responsive behavior at practical breakpoints
- avoid overly specific selectors
- maintain readable structure and naming

## Section 7: JS Rules

- include JS only for meaningful interactions
- support frontend and editor lifecycle
- avoid global leaks
- keep initialization idempotent

## Section 8: Integration Rules

Ensure style import exists exactly once:
`@import '../../blocks/{slug}/style';`

No duplicate imports.

## Section 9: Quality Gate Checklist

Before considering block complete:
- editor-managed content is field-driven
- field/template contract matches
- dynamic outputs are escaped
- no critical a11y issues in scope
- responsive behavior still correct

## Section 10: Anti-Patterns

Do not:
- hardcode content that editors should control
- over-engineer field schemas
- add JS for non-interactive effects
- broaden scope into unrelated architecture changes
