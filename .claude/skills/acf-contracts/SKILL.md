---
name: acf-contracts
description: Contract validation framework between ACF field group schema and PHP render templates.
disable-model-invocation: true
---

# ACF Contracts Skill

## Purpose

Prevent broken editor/runtime behavior caused by schema-template mismatches.

## Section 1: Contract Inventory

For each block, build an inventory of:
- `get_field` calls
- `have_rows`/`the_row` loops
- expected return structures (`image`, `link`, `group`, `repeater`)

Then cross-check against ACF JSON definitions.

## Section 2: Required Matching Rules

- field names must exist in JSON
- repeater subfields must match loop usage
- template assumptions about array keys must match return format

## Section 3: Null and Type Safety

- use null-safe guards before nested array reads
- coerce numeric values when used in arithmetic or style attributes
- avoid ambiguous truthiness checks for arrays vs strings

## Section 4: Escaping Contracts

- text node: `esc_html`
- attribute: `esc_attr`
- URL: `esc_url`
- textarea: `esc_textarea`
- rich HTML: `wp_kses` with explicit allowlist

## Section 5: Evolution Rules

- never delete existing fields silently in mature blocks
- additive schema changes should keep backward compatibility
- document migration notes for renamed fields

## Section 6: Audit Output

For each mismatch include:
- field name
- template location
- JSON location
- risk level
- safe fix strategy

