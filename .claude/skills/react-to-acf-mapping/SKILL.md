---
name: react-to-acf-mapping
description: Mapping rules for converting Figma Make React components into WordPress ACF block structures, fields, and safe PHP rendering contracts.
disable-model-invocation: true
---

# React to ACF Mapping Rules

Use this when converting React UI structures into ACF blocks.

## Component to block partitioning

- Prefer section-level components as block candidates.
- Keep tiny presentational components inside the same block unless reused across multiple sections.
- One block should represent one editor-manageable section.

## Prop/state mapping

- Static JSX copy -> text/textarea/WYSIWYG ACF fields.
- Image `src`/`alt` pairs -> ACF image field (array return).
- Link `href` + label -> ACF link field.
- Repeated array maps -> repeater fields.
- Optional nested objects -> group fields.
- Avoid mapping ephemeral UI state (hover toggles, temporary filters) unless editor-controlled.

## Styling migration

- Convert utility-heavy class stacks into maintainable SCSS selectors.
- Keep semantic class names scoped by block slug.
- Preserve responsive intent from breakpoints.
- Do not copy framework-specific runtime styles directly into PHP templates.

## JSX to PHP conversion

- React conditional render -> PHP `if` guards with null-safe checks.
- React list map -> `have_rows()` loops for repeaters.
- Convert fragments into semantic wrappers only when needed.
- Escape all dynamic output.

## JavaScript migration

- If interactivity is simple (tabs, accordion, slider hooks), use `script.js`.
- Avoid React runtime dependency in the final block frontend.
- Ensure editor-safe re-init behavior where required.

## Authoring experience

- Use field labels that match content editor language, not developer jargon.
- Keep required fields minimal.
- Provide sensible defaults for headline, CTA label, and spacing options where useful.
