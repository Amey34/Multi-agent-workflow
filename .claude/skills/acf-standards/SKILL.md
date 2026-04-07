---
name: acf-standards
description: Production rules for building modern WordPress ACF Gutenberg blocks in this project.
disable-model-invocation: true
---

# ACF block standards

Apply these rules every time you create or modify a block.

## Registration

- Use `block.json` registration only.
- Do not use `acf_register_block_type()`.
- Ensure `block.json` includes:
  - `apiVersion: 2`
  - appropriate `supports`
  - `acf.renderTemplate`
- The theme must register the block with:
  `register_block_type(__DIR__ . '/blocks/{slug}')`

## File structure

Create/update exactly:

- `blocks/{slug}/block.json`
- `blocks/{slug}/render.php`
- `blocks/{slug}/_style.scss`
- `blocks/{slug}/script.js` only if required
- `acf-json/{slug}-field-group.json`

## Slug rules

- Infer a descriptive kebab-case slug from the design/content.
- Never use `block-slug` literally.
- Use the same slug in:
  - folder name
  - field prefixes
  - block name
  - CSS classes
  - JSON filename

## ACF field rules

- Use import-ready local JSON format.
- Field keys must be unique and look like `field_xxxxxxxx`.
- Field names must be prefixed with the block slug.
- Group fields logically.
- Use the correct field type.
- Images return arrays.
- Links return arrays.
- Repeaters use `have_rows()` / `the_row()`.
- Include a proper block location rule.

## PHP rules

- Use semantic markup.
- Use `get_block_wrapper_attributes()` on the outermost element.
- Escape all output with `esc_html()`, `esc_url()`, `esc_attr()`, etc.
- Do not hardcode content.
- Avoid unnecessary wrapper divs.
- Ensure accessibility.

## SCSS rules

- Use BEM naming.
- Use responsive styles for mobile, tablet, desktop.
- Use `clamp()` where appropriate.
- Keep SCSS production-ready.

## JS rules

- Include JS only when required.
- It must work on frontend and in the editor.
- Reinitialize correctly after editor renders if needed.
- Avoid global scope leakage.

