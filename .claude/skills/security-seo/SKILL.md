---
name: security-seo
description: Security and semantic-SEO hardening checklist for ACF block templates and reviews.
disable-model-invocation: true
---

Apply this checklist during implementation and review.

## 1. Security Fundamentals

- escape dynamic output by context (`esc_html`, `esc_url`, `esc_attr`)
- use allowlisted HTML (`wp_kses_post`) only when needed
- guard optional field structures before access
- never pass untrusted data into inline scripts

## 2. Data Contract Safety

- field names/types must match template expectations
- handle empty repeater/group states gracefully
- avoid assumptions that lead to notices/fatals

## 3. Semantic SEO Baseline

- maintain logical heading hierarchy
- use meaningful section/landmark structure
- ensure link text conveys intent
- ensure non-decorative media has alt strategy

## 4. Accessibility Cross-Checks

- prefer semantic controls before ARIA
- ensure keyboard reachability of interactive elements
- keep focus states visible
- avoid unlabeled controls

## 5. Markup Performance Hygiene

- reduce unnecessary wrapper depth
- avoid repeated heavy markup patterns
- use lazy loading where contextually appropriate

## 6. Review Output Requirements

When reporting findings include:
- severity
- file + line
- impact summary
- minimal fix recommendation

Keep findings specific and actionable.
