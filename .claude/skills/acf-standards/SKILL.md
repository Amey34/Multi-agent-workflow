---
name: acf-standards
description: Production rules for building modern WordPress ACF Gutenberg blocks in this project.
disable-model-invocation: true
---

# ACF Block Standards

Apply this standard whenever creating or modifying ACF blocks.

## 1) Registration and Discovery

- Use `block.json` registration for each block.
- Do not use deprecated `acf_register_block_type()` patterns.
- Ensure `block.json` includes:
  - `apiVersion: 2`
  - stable `name`, `title`, `category`, `supports`
  - `acf.renderTemplate`
- Theme-level registration should follow project convention:
  `register_block_type(__DIR__ . '/blocks/{slug}')`

## 2) Required File Layout

Each block should have:
- `blocks/{slug}/block.json`
- `blocks/{slug}/render.php`
- `blocks/{slug}/_style.scss`
- `blocks/{slug}/script.js` only when needed
- `acf-json/{slug}-field-group.json`

## 3) Slug and Naming Rules

- Slug must be descriptive kebab-case.
- Use the same slug across:
  - folder name
  - block name
  - field prefixes
  - CSS class namespace
  - JSON filename
- Never leave placeholder slugs in committed files.

## 4) ACF Field Rules

- Use import-ready local JSON format.
- Field keys must be unique (`field_xxxxxxxx` pattern).
- Prefix field names with block slug.
- Keep field architecture editor-friendly:
  - shallow nesting where possible
  - repeaters only for true repeated structures
- Set image/link return formats intentionally.
- Include valid block location rules.

## 5) PHP Template Rules

- Use semantic, accessible markup.
- Apply `get_block_wrapper_attributes()` on outer element.
- Escape all dynamic output (`esc_html`, `esc_url`, `esc_attr`, etc.).
- Use null-safe checks for optional fields.
- Avoid unnecessary wrapper divs and duplicated logic.

## 6) SCSS Rules

- Block-scoped naming (BEM-style encouraged).
- Include responsive behavior for mobile/tablet/desktop.
- Prefer fluid sizing where appropriate (`clamp`, `rem`, `%`).
- Keep selectors maintainable and not overly specific.

## 7) JavaScript Rules

- Add JS only for actual interactivity.
- Must work in frontend and editor contexts.
- Reinitialize safely after editor rerenders when needed.
- Avoid global namespace leakage.

## 8) Integration Rules

- Add block style import to `assets/css/styles.scss` once:
  `@import '../../blocks/{slug}/style';`
- Never duplicate import lines.

## 9) Final Quality Gate

Before completion, verify:
- no hardcoded editor-managed content
- no unescaped dynamic output
- field names/types align with template usage
- responsive and semantic behavior remains sound
