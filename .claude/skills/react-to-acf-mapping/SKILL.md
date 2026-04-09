---
name: react-to-acf-mapping
description: Practical mapping rules for converting React structures into ACF field models and safe PHP templates.
disable-model-invocation: true
---

# React to ACF Mapping

Use this guide when converting React components into editor-manageable ACF blocks.

## 1. Partition Strategy

- map major sections to block candidates
- keep tiny view-only fragments inside parent block
- split only when editor ownership or reuse justifies it

## 2. Field Mapping Rules

- static text -> text/textarea/wysiwyg
- link pairs -> link field
- image `src + alt` -> image field (array return)
- repeated arrays -> repeater
- optional nested objects -> group field
- transient UI state usually stays in JS

## 3. Template Translation

- React conditionals -> null-safe PHP conditionals
- `map()` loops -> repeater loops
- preserve semantic heading and section structure
- escape all dynamic output

## 4. Styling Translation

- convert utility-heavy class stacks into maintainable SCSS
- keep class naming block-scoped and semantic
- preserve responsive intent

## 5. Interaction Translation

- add `script.js` only when behavior is required
- avoid React runtime dependency on frontend
- ensure editor/frontend safe re-init for dynamic blocks

## 6. Editor Experience

- human-readable field labels
- minimal required fields
- sensible defaults for common content patterns
- avoid over-configuring decorative controls

## 7. Validation

- each editable value is field-backed
- field names align with block slug
- render logic matches field shapes
- output remains secure, semantic, maintainable
