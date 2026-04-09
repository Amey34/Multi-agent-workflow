---
name: security-seo
description: Comprehensive security and semantic-SEO review checklist for WordPress ACF block templates and audits.
disable-model-invocation: true
---

# Security and SEO Skill

## Purpose

Ensure block outputs are safe, semantically strong, and discoverability-friendly while preserving accessibility and performance.

## Security Section

### Output Escaping

Use context-correct escaping:
- text -> `esc_html()`
- URL -> `esc_url()`
- attribute -> `esc_attr()`
- controlled rich HTML -> `wp_kses_post()` when justified

### Data Guarding

- validate optional arrays before nested access
- guard repeater/group loops for empty states
- avoid assumptions that create notices/fatals

### Script/Data Safety

- avoid injecting untrusted content into JS contexts
- avoid unsafe inline scripting patterns

## Semantic SEO Section

- maintain heading hierarchy
- use meaningful sectioning and landmarks
- ensure CTA/link text communicates destination/action
- maintain meaningful media alt strategy

## Accessibility Alignment

- semantic controls before ARIA
- interactive elements must be keyboard reachable
- focus states should remain visible
- avoid unlabeled or duplicate ambiguous controls

## Performance-Aware Markup

- avoid unnecessary wrappers
- reduce duplicated heavy markup branches
- use lazy loading for non-critical images when suitable

## Review Output Standard

For every issue report:
- severity
- file + line
- why it matters
- minimal remediation approach

## Severity Guide

- Critical: security exposure or severe semantic breakage
- High: major user/search/accessibility risk
- Medium: quality and maintainability gaps
- Low: polish improvements

## Done Criteria

- no critical unresolved security issues in scope
- semantic structure and content signals are coherent
- findings are actionable and specific
