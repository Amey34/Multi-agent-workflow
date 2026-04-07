---
name: security-seo
description: Security, accessibility, and SEO standards for WordPress block generation in this project.
disable-model-invocation: true
---

# Security, accessibility, and SEO standards

## Security

- Escape all frontend output.
- Sanitize attributes and URLs.
- Never expose secrets or credentials.
- Never add inline JS that interpolates untrusted values unsafely.
- Prefer minimal PHP logic in templates.
- If external links are intentionally opened in a new tab, include safe rel attributes where appropriate.
- Avoid raw HTML output unless the field is explicitly intended for trusted WYSIWYG use and handled carefully.

## Accessibility

- Use semantic elements like `section`, `header`, `article`, `ul`, `li`, `figure`, `figcaption` when appropriate.
- Images require meaningful alt text fallback logic.
- Buttons and links must have visible or accessible labels.
- Decorative media should not create noise for screen readers.
- Preserve keyboard usability for interactive JS.
- Carousels, tabs, accordions, and videos must be accessible if used.

## SEO

- Prefer clean semantic hierarchy.
- Avoid multiple competing H1-style outputs inside reusable sections.
- Use meaningful text for CTAs and links.
- Support editor-controlled heading tags when appropriate.
- Use image alt text from media library or a dedicated field fallback.
- Avoid unnecessary div nesting.
- Ensure block markup is indexable and not dependent on JS for basic content visibility.

## Performance

- Only load `script.js` when needed.
- Keep DOM output lean.
- Avoid unnecessary duplicate wrappers and redundant assets.
- Reuse Bootstrap only where it helps instead of over-structuring markup.
