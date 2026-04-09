---
name: acf-standards
description: Canonical implementation standards for production ACF Gutenberg blocks in this repository.
disable-model-invocation: true
---

# ACF Standards

Apply these rules whenever creating or modifying block code.

## 1. Registration and Metadata

- use `block.json` registration
- avoid deprecated block registration APIs
- ensure stable identifiers and `acf.renderTemplate`
- include supports/settings that match real block behavior

## 2. Required File Set

Each block should include:
- `block.json`
- `render.php`
- `_style.scss`
- `script.js` only when interaction exists
- local ACF JSON in `acf-json/`

## 3. Naming Consistency

- descriptive kebab-case slug
- slug aligned across folder, block name, fields, and CSS namespace
- no placeholder/demo slugs in final output

## 4. Field Architecture

- use import-ready local JSON
- stable, unique field keys
- slug-prefixed field names
- editor-friendly structure with minimal nesting
- explicit return formats for links/images

## 5. Template Standards

- semantic markup and accessible structure
- escaped dynamic output everywhere
- null-safe rendering for optional fields
- avoid unnecessary wrapper depth

## 6. SCSS Standards

- block-scoped selectors
- responsive coverage for mobile/tablet/desktop
- maintainable specificity
- fluid typography/spacing where appropriate

## 7. JS Standards

- add JS only for real behavior
- support frontend + editor lifecycle
- avoid global namespace leakage

## 8. Theme Integration

- ensure block style import exists once in `assets/css/styles.scss`
- avoid duplicate imports

## 9. Final Gate

Before completion confirm:
- editable content is field-driven
- template and field contracts align
- escaping/a11y basics pass
- responsive behavior is preserved
