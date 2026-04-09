---
name: security-seo
description: Security, accessibility-aware SEO, and output-hardening checklist for WordPress ACF block templates.
disable-model-invocation: true
---

Apply this checklist whenever reviewing or implementing block templates.

## 1) Security Hardening

- Escape all dynamic output:
  - text: `esc_html()`
  - URLs: `esc_url()`
  - attributes: `esc_attr()`
  - rich content: controlled allowlist via `wp_kses_post()` when needed
- Guard optional fields with null-safe checks.
- Do not trust field data shape without validation.
- Avoid inline scripts with untrusted data.

## 2) Semantic SEO Foundations

- Use proper heading hierarchy without skips.
- Keep landmark/section structure meaningful.
- Ensure link text is descriptive.
- Provide alt text strategy for non-decorative images.

## 3) Accessibility Alignment

- Prefer semantic HTML before ARIA.
- Ensure interactive controls are keyboard reachable.
- Keep visible focus states intact.
- Avoid ambiguous repeated CTA labels without context.

## 4) Performance-aware Markup

- avoid excessive wrapper elements
- reduce duplicate markup for similar states
- use lazy loading for below-the-fold images where appropriate

## 5) ACF Template Safety

- match field return types with template usage
- handle empty repeater rows gracefully
- avoid fatal behavior when fields are missing

## 6) Output Review Format

When used in review mode, report:
- issue severity
- file + line
- why it matters
- minimal fix recommendation

Keep findings specific and actionable.
