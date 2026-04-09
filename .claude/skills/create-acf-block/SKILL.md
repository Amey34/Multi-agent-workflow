---
name: create-acf-block
description: Create a production-ready WordPress ACF block from a screenshot, Figma section, or brief description, write files to disk, and return only a manifest.
---

Create or update one production-ready ACF block aligned with this project.

## Input Modes

- screenshot/design reference
- Figma-derived section notes
- short textual brief

## Step-by-Step

1. Identify block purpose and infer descriptive slug.
2. Read minimum relevant files only.
3. Use existing theme/block patterns as implementation reference.
4. Create/update required block files and field JSON.
5. Register style import if missing.
6. Apply security/a11y/responsive sanity checks.

## Required Outputs on Disk

- `blocks/{slug}/block.json`
- `blocks/{slug}/render.php`
- `blocks/{slug}/_style.scss`
- `blocks/{slug}/script.js` if interactivity requires
- `acf-json/{slug}-field-group.json`

## Chat Output Contract

Return only:
- manifest of created/updated files
- short notes on assumptions or risks

Do not paste full source unless explicitly asked.
