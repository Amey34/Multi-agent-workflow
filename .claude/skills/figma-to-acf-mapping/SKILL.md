---
name: figma-to-acf-mapping
description: Deterministic conversion framework for translating Figma node structure into ACF block partitions, field architectures, and render contracts.
disable-model-invocation: true
---

# Figma to ACF Mapping Skill

## Purpose

Provide a structured, Figma-specific method for converting visual design nodes into editor-ready ACF block implementations.

## Section 1: Block Partition Strategy

- treat each top-level Figma frame or section as a candidate block boundary
- split when editor ownership is distinct (e.g. hero vs. testimonial vs. CTA strip)
- do not split purely presentational sub-components that are not independently editable
- name blocks after content purpose, not Figma layer names (e.g. `hero-banner`, not `Frame 42`)

## Section 2: Content Ownership Classification

For each Figma frame, classify every element:
- **editor-managed**: text content, images, links, CTA labels — these become ACF fields
- **decorative**: background shapes, dividers, icon flourishes — hardcode in template or CSS
- **layout**: auto-layout spacing, padding, alignment — translate to SCSS, not fields

Only editor-managed content becomes ACF fields. Do not expose decorative or layout decisions to editors.

## Section 3: Field Type Mapping from Figma Elements

| Figma Element | ACF Field Type |
|---|---|
| Single-line text / heading | `text` |
| Multi-line body copy | `textarea` or `wysiwyg` |
| Rich text with formatting | `wysiwyg` |
| Image fill / placed image | `image` (array return) |
| Icon + label button / CTA | `link` |
| Repeated sibling frames | `repeater` |
| Optional content group | `group` |
| Boolean visibility toggle | `true_false` |
| Constrained text options | `select` or `radio` |

Avoid `flexible_content` unless the Figma design shows genuinely open-ended layout variation.

## Section 4: Auto-Layout → Markup Translation

- horizontal auto-layout → `display: flex; flex-direction: row;`
- vertical auto-layout → `display: flex; flex-direction: column;`
- fixed-size frame → explicit `width`/`height` or `max-width` constraint in SCSS
- fill container → `flex: 1` or `width: 100%`
- gap property → `gap:` in SCSS, not margin hacks
- padding → SCSS padding on the block wrapper, not inline styles

## Section 5: Component Variants → ACF Field Options

When Figma shows component variants (e.g. Button/Primary, Button/Secondary):
- map variant property to a `select` or `radio` ACF field (e.g. `{slug}_button_style`)
- apply the chosen value as a modifier class in `render.php` (e.g. `btn--primary`)
- keep SCSS variant rules under the block namespace

## Section 6: Responsive Intent

- Figma breakpoint frames (mobile/tablet/desktop variants) → SCSS `@media` breakpoints
- element visibility changes across breakpoints → `display: none` / `display: block` at breakpoints
- image crop changes → use `object-fit` + `aspect-ratio` constraints in SCSS
- font size changes → map to breakpoint-specific type scale, not inline font-size values

## Section 7: Null-Safety and Fallbacks

- every ACF field read needs a null-safe guard in `render.php`
- define empty-state behavior before building the template (e.g. skip section if no heading)
- repeater blocks must guard for zero rows: use `have_rows()` before looping

## Section 8: Validation Checklist

Before handing off to `acf-block-builder`:
- every editable Figma element has a corresponding field candidate
- block slugs are descriptive and kebab-case
- field names are slug-prefixed
- repeater/group justification is documented
- decorator/layout elements are explicitly excluded from field list
