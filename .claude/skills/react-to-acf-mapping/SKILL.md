---
name: react-to-acf-mapping
description: Long-form mapping framework for converting React structures into robust, editor-friendly ACF block implementations.
disable-model-invocation: true
---

# React to ACF Mapping Skill

## Purpose

Provide a deterministic conversion framework from React UI patterns to ACF schema + PHP templates.

## Section 1: Partition Strategy

- prefer section-level block boundaries
- avoid splitting tiny presentational fragments into separate blocks
- split when editor ownership or reuse justifies it

## Section 2: Content Ownership

For each React section, classify:
- editor-managed text/media/actions
- decorative static assets
- runtime-only state

Only editor-managed content becomes ACF fields.

## Section 3: Field Mapping Matrix

- static copy -> text/textarea/wysiwyg
- image src/alt -> image field (array return)
- link href/label -> link field
- repeated arrays -> repeater fields
- optional nested sets -> group fields

Avoid flexible content unless variation is truly open-ended.

## Section 4: Template Translation

- React conditionals -> null-safe PHP branches
- React maps -> repeater loops
- preserve semantic HTML hierarchy
- escape dynamic outputs by context

## Section 5: Styling Migration

- convert utility-heavy class stacks to maintainable SCSS
- keep class names block-scoped
- preserve responsive intent
- avoid copying framework runtime dependencies into template

## Section 6: Interaction Migration

- add `script.js` only for true behavior needs
- no React runtime dependency in final block frontend
- ensure editor/frontend re-init safety

## Section 7: Editor Experience

- labels should match editor language
- required fields should be minimal
- defaults should reduce friction for common use cases
- avoid exposing overly technical controls to editors

## Section 8: Validation Checklist

- every editable visual element is field-backed
- field naming follows slug conventions
- template logic matches field shapes
- no critical a11y/security regressions introduced
