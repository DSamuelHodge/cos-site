---
schema: cos.workflow/v1
kind: workflow
title: "Email Brand Design System"
description: "Warm-neutral design language for hodge@agentmail.to consulting emails. Light canvas default. Tokens, typography, layout, elevation, shape, and components (btn-primary, btn-ghost, card, mono-block). Prioritizes 5 lean templates that establish reusable patterns."
trigger: "Creating or updating email templates, client communications, or brand assets"
owner: cos
cadence: as-needed
status: active
steps:
  - "Default to Light Canvas for deliverability"
  - "Use provided token set, Inter fallback stack, no shadows, 4px base unit, max-width 600px"
  - "Implement card, btn-primary/ghost, mono-block, and owner signature consistently"
  - "Test in Gmail, Outlook, Apple Mail; provide both text + HTML"
  - "Reference this spec for all day-to-day sends (notification, status, invoice, proposal, outreach)"
tags: ["email", "brand", "design-system", "templates", "agentmail", "workflow"]
date: "2026-08-25"
draft: false
---

# Email Brand Design System

A warm-neutral design language for consulting-business email communications. Two canvas modes share one token set — swap the values, keep the structure.

## Colors

### Light Canvas (default — safest for deliverability & dark-mode inversion)

| Token       | Hex     | Use                              |
|-------------|---------|----------------------------------|
| canvas      | #f7f5f0 | Page / body background           |
| canvas-soft | #efe9de | Card fill, mono/status blocks    |
| hairline    | #e3ddd2 | 1px borders, dividers            |
| ink         | #2b2622 | Primary text, button-primary fill|
| body-strong | #453e35 | Mid-emphasis text (signature names, values) |
| body        | #6f6759 | Secondary body text              |
| mute        | #948c7d | Captions, fine print, labels     |

### Dark Canvas (use selectively — see note below)

| Token       | Hex     | Use                              |
|-------------|---------|----------------------------------|
| canvas      | #2b2622 | Page / body background           |
| canvas-soft | #383330 | Card fill, mono/status blocks    |
| hairline    | #3f3a36 | 1px borders, dividers            |
| ink         | #f7f5f0 | Primary text, button-primary fill|
| body-strong | #dad2c1 | Mid-emphasis text                |
| body        | #c9c0ad | Secondary body text              |
| mute        | #aea69c | Captions, fine print, labels     |

No chromatic accent color. The system runs entirely on warm neutrals — ink-on-canvas contrast does the work a brand color usually would. If a template needs a status color (e.g. "overdue" on an invoice), use a single desaturated warm red/amber sparingly rather than introducing a new hue family.

**Deliverability note:** dark-canvas HTML renders unpredictably across Outlook desktop and Gmail's forced dark-mode inversion. Default to light canvas for anything client-facing; reserve dark for internal or tightly-controlled sends.

## Typography

- Primary face: Inter. Not web-safe for email — every template must declare the fallback stack below; expect most clients to render the fallback, not true Inter.
- Fallback stack: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Helvetica, Arial, sans-serif
- Mono face: DM Mono, for status lines / reference numbers / code-like content only. Fallback: 'DM Mono', 'SFMono-Regular', Consolas, monospace

| Token          | Size  | Weight | Line Height | Tracking     | Use                              |
|----------------|-------|--------|-------------|--------------|----------------------------------|
| hero           | 32px  | 400    | 1.25        | -0.8px       | Email headline                   |
| body-lg        | 16px  | 400    | 1.5         | 0            | Lead paragraph                   |
| body-md        | 14px  | 400    | 1.5         | 0            | Default body, card rows          |
| body-md-strong | 14px  | 500    | 1.5         | 0            | Values, emphasis                 |
| caption        | 12px  | 500    | 1.4         | 1.5px, uppercase | Eyebrow labels               |
| mono           | 13px  | 400    | 1.4         | 0            | Status / reference lines         |

Hero weight stays at 400 — no bold display type. Confidence comes from restraint, not size or weight.

## Layout & Spacing

- Base unit: 4px
- Content max-width: 600px, centered
- Section padding: 24–40px vertical
- Card interior padding: 24px
- Nothing wider than 600px — assume a narrow email client viewport by default

## Elevation

No drop shadows, anywhere. Elevation comes from two things only:
1. Surface contrast (`canvas` vs `canvas-soft`)
2. A 1px hairline border

## Shape

| Token      | Value   | Use                     |
|------------|---------|-------------------------|
| radius-sm  | 3px     | Buttons                 |
| radius-md  | 4px     | Cards, mono blocks      |
| radius-pill| 9999px  | Avoid — no pill shapes in this system |

## Components

### btn-primary
Fill: ink. Text: canvas. Padding: 8px 20px. Radius: radius-sm. Weight 500, 14px.

### btn-ghost
Fill: transparent. Border: 1px hairline. Text: ink. Same padding/radius as primary.

### card
Fill: canvas-soft. Border: 1px hairline. Radius: radius-md. Padding: 24px.  
Internal rows (`card-row`) separated by 1px hairline, justify-content: space-between, label in body color / value in body-strong.

### mono-block
Fill: canvas-soft. Border: 1px hairline. Radius: radius-md. Font: mono stack. Used for reference numbers, timestamps, status lines — not paragraphs.

**Prioritized starter templates** (general notification, status update, invoice, proposal delivery, cold outreach) were sent to hodgedomain@google.com for review using these exact tokens and components. They establish the reusable patterns for all other sends.

## Nav-bar
Wordmark left, single utility link right (e.g. "View in browser"). Bottom border 1px hairline. No logo mark required — text wordmark is sufficient.

## Signature
Structure, top to bottom:
1. Name — body-strong, 15px, weight 600
2. Title — body, 14px
3. Contact lines (email / phone / site) — body, 14px, links in body-strong, 1.7 line-height
Sits between two hairline dividers when it closes an email.

## Hairline (divider)
1px solid hairline color, no shadow, 32px vertical margin.

---

## Do's and Don'ts

**Do**
- Keep every template to a single primary CTA plus at most one ghost/secondary action
- Reuse the shared shell + signature partial rather than rebuilding chrome per template
- Always send text and html together (see Messages API note)
- Inline all CSS in a `<style>` tag inside `<head>` — do not rely on external stylesheets

**Don't**
- Don't introduce a chromatic accent color for buttons or links
- Don't use bold/heavy hero type — 400 weight only
- Don't add drop shadows — hairline + surface contrast only
- Don't exceed 600px content width
- Don't use pill-shaped buttons

---

## File Map (this kit)

`templates/`
  - `00-shell-light.html` — reference shell, light canvas, no content
  - `00-shell-dark.html` — reference shell, dark canvas, no content
  - `01-general-notification.html` — catch-all single-CTA notification
  - `02-status-update.html` — project status w/ summary card
  - `03-invoice.html` — line-item table + payment CTA
  - `04-proposal-delivery.html` — engagement summary + review/sign CTA
  - `05-cold-outreach.html` — minimal, low-chrome outreach template
  - `signature-snippet.html` — copy-paste signature partial

**Next:** Create the `assets/brand/templates/` directory and populate the 8 reference files using the exact tokens, typography, components, and structure defined above. The previous review email to hodgedomain@google.com used an early version of these patterns.

See `assets/brand/` for any supporting files. Update this page when the system evolves.
