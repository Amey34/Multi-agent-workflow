---
name: playwright-test
description: Detailed browser QA checklist for block validation via Playwright MCP, including rendering, interaction, responsiveness, and runtime health.
---

# Playwright Test Skill

## Purpose

Provide consistent, reproducible browser verification for block-level work.

## Preconditions

- explicit target URL is required
- clarify test scope (specific block or full page)
- note any expected interactions provided by user

## Test Phases

### Phase 1: Render Sanity

- confirm key sections are visible
- verify no immediate clipping/overlap issues
- ensure critical content is not hidden offscreen

### Phase 2: Interaction Validation

- test hover/focus/click behavior
- validate toggles/accordion/tabs/sliders where present
- ensure interactive states are visually clear

### Phase 3: Responsive Checks

Run at representative sizes:
- mobile
- tablet
- desktop

Check:
- wrapping
- spacing consistency
- overflow/horizontal scroll
- major layout shifts

### Phase 4: Runtime Diagnostics

- inspect console for errors/warnings
- prioritize issues that affect UX/functionality

### Phase 5: Keyboard Basics

- tab path reaches actionable controls
- focus remains visible and logical

## Reporting Rules

For each issue include:
- severity
- concise reproduction steps
- observed behavior
- expected behavior
- suggested minimal fix

## Output Contract

Return only:
- pass/fail summary
- issue list
- concise fix recommendations

Avoid verbose logs unless requested.

## Severity Guide

- Critical: core interaction broken or page unusable
- High: major layout or interaction issue
- Medium: noticeable but non-blocking defect
- Low: minor polish issue
