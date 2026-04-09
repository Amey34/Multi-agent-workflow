---
name: react-to-acf-mapping
description: Mapping rules for converting Figma Make React components into WordPress ACF block structures, fields, and safe PHP rendering contracts.
disable-model-invocation: true
---

# React to ACF Mapping Rules

Use this skill to convert React structures into maintainable ACF block architecture.

## 1) Block Partitioning

- Prefer section-level block boundaries.
- Keep tiny presentational fragments inside parent block unless reused.
- Avoid over-fragmentation that hurts editor usability.

## 2) Data Mapping

- static JSX copy -> text/textarea/wysiwyg
- image `src` + `alt` -> image field (array return)
- link `href` + label -> link field
- repeated arrays/maps -> repeater
- optional nested structures -> group fields
- transient UI state usually stays out of ACF

## 3) Styling Migration

- translate utility-heavy classes to scoped SCSS
- use semantic, slug-based class naming
- preserve responsive intent from React layout
- avoid framework runtime style assumptions

## 4) JSX to PHP Translation

- conditionals -> null-safe PHP `if` branches
- list maps -> `have_rows()` + `the_row()` loops
- fragments -> semantic wrappers only when required
- escape every dynamic output value

## 5) JavaScript Translation

- add `script.js` only for meaningful interactivity
- avoid React dependency in final frontend
- ensure editor/frontend safe initialization

## 6) Authoring Experience

- editor-friendly field labels
- minimal required fields
- sensible defaults for common content fields
- avoid over-configuring decorative details

## 7) Validation Checklist

- every editable item is field-backed
- field names align with slug prefixes
- template contract matches field structure
- resulting block is secure, semantic, and maintainable
