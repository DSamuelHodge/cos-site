---
schema: cos.workflow/v1
kind: workflow
title: "AgentMail + Brand Design Cheat Sheet"
description: "Complete protocol for generating and sending consistent Text/HTML emails from hodge@agentmail.to using the full warm-neutral + accent design system. This file is the single source of truth for all email correspondence."
trigger: "Any outbound email, template creation, or AgentMail integration"
owner: cos
cadence: as-needed
status: active
steps:
  - "Use this cheat sheet as the protocol for every send (API reference + brand tokens)"
  - "Always send both text and full inlined HTML document"
  - "Default to Light Canvas; use accents (topaz for action, emerald for success) sparingly"
  - "Reuse nav-bar, card, btn-primary/ghost, mono-block, hairline, and signature partials from assets/brand/templates/"
  - "Log every send in CRM if it advances a relationship"
  - "Test rendering in Gmail, Outlook, Apple Mail before client send"
tags: ["agentmail", "email", "brand", "design-system", "templates", "protocol"]
date: "2026-08-25"
draft: false
---

# AgentMail + Brand Design Cheat Sheet

This file establishes the protocol for all email correspondence from hodge@agentmail.to. Follow it exactly for uniform, professional, on-brand communication.

## 1. API Reference — Send Message

POST /v0/inboxes/:inbox_id/messages/send  
Auth: Bearer <token>

| Field | Type | Required | Notes |
|---|---|---|---|
| to | string \| string[] | Optional | Recipient(s) |
| cc | string \| string[] | Optional | |
| bcc | string \| string[] | Optional | |
| reply_to | string \| string[] | Optional | Reply-to address(es) |
| subject | string | Optional | |
| text | string | Optional | Plain-text fallback — always send alongside html |
| html | string | Optional | Full HTML document, CSS inlined in <head><style> |
| labels | string[] | Optional | Tag the message |
| attachments | object[] | Optional | See Attachments doc |
| headers | map<string,string> | Optional | Custom headers |
| track_opens | boolean | Optional | Requires custom domain + HTML body; fires once per message |

Response: { message_id, thread_id }  
Limit: max 50 recipients total across to + cc + bcc.

### Related Endpoints
- messages.reply(inbox_id, message_id, text, html?, attachments?, reply_all?)
- messages.forward(inbox_id, message_id, to, subject?, text?, html?)
- messages.list(inbox_id, limit?, page_token?, labels?, before?, after?, from?, to?, subject?)
- messages.search(inbox_id, q, limit?, page_token?) — full-text, relevance-ranked
- messages.update(inbox_id, message_id, add_labels?, remove_labels?)
- messages.get / get_raw / get_attachment(inbox_id, message_id, ...)

### HTML + Text Best Practice
- Always send both text and html. HTML renders in most clients; text improves deliverability and covers clients that strip HTML.
- html = a full document (`<html><head>...</head><body>...</body></html>`), not a fragment.
- CSS must be inlined in a <style> tag inside <head> — most reliable cross-client method (Gmail, Outlook, Apple Mail).
- Max content width 600px, centered.

### Receiving Content
- extracted_text / extracted_html = new reply content only (quoted history auto-stripped).
- text`/`preview may be absent on HTML-only forwarded emails — treat html as primary, text as optional on inbound.

### Read/Unread Tracking
No native "mark as read" — use labels:

client.inboxes.messages.update(inbox_id, message_id, add_labels=["read"], remove_labels=["unread"])

Filter unread: messages.list(inbox_id, labels=["unread"])

### Inbound Auth
Emails failing SPF/DKIM/DMARC are dropped. Missing auth headers → processed but labeled unauthenticated.

### Python Example

```python
from agentmail import AgentMail
client = AgentMail(api_key="YOUR_KEY")

client.inboxes.messages.send(
    inbox_id="agent@agentmail.to",
    to="client@example.com",
    subject="Your workspace is ready",
    text="Plain text body",
    html="<!doctype html>...",
    labels=["notification"]
)
```

## 2. Brand Tokens

### Neutrals
| Token       | Light    | Dark     |
|-------------|----------|----------|
| canvas      | #f7f5f0  | #2b2622  |
| canvas-soft | #efe9de  | #383330  |
| hairline    | #e3ddd2  | #3f3a36  |
| ink         | #2b2622  | #f7f5f0  |
| body-strong | #453e35  | #dad2c1  |
| body        | #6f6759  | #c9c0ad  |
| mute        | #948c7d  | #aea69c  |

### Accents
| Token          | Base    | Deep (hover/text) | Tint (bg) | Use |
|----------------|---------|-------------------|-----------|-----|
| accent-topaz   | #C97C3D | #A85D2C           | #F6E4D2   | Elevated CTA, "action needed" states, invoices/deadlines |
| accent-emerald | #2E8B63 | #1F6B4C           | #DCEEE4   | Confirmation/success — paid, complete, approved |

**Rule**: neutral ink-on-canvas stays the *default* primary CTA. Reach for an accent only when a message needs to visually outrank a neutral CTA elsewhere in the same email, or to flag status. Never use both accents in one email.

**Assets**: See `assets/brand/templates/` for reusable shell, nav-bar, card, buttons, signature, and the 5 core templates (general notification, status update, invoice, proposal, cold outreach). All follow this exact system.

**Protocol**: This page is the single source of truth. Every outbound email must conform. Update here first, then templates.


## 3. Typography

| Token | Size | Weight | Line Height | Tracking | Use |
|---|---|---|---|---|---|
| hero | 32px | 400 | 1.25 | -0.8px | Email headline |
| body-lg | 16px | 400 | 1.5 | 0 | Lead paragraph |
| body-md | 14px | 400 | 1.5 | 0 | Default body, card rows |
| body-md-strong | 14px | 500 | 1.5 | 0 | Values, emphasis |
| caption | 12px | 500 | 1.4 | 1.5px, uppercase | Eyebrow labels |
| mono | 13px | 400 | 1.4 | 0 | Status/reference lines |

Font stack: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Helvetica, Arial, sans-serif  
Mono stack: 'DM Mono', 'SFMono-Regular', Consolas, monospace  
Hero weight stays 400 — no bold display type, ever.

## 4. Shape & Elevation

| Token | Value |
|---|---|
| radius-sm (buttons) | 3px |
| radius-md (cards, mono blocks) | 4px |
| Pill shapes | Not used in this system |

No drop shadows. Elevation = surface contrast (`canvas` vs `canvas-soft`) + 1px `hairline` border only.

## 5. Spacing

Base unit 4px · content max-width 600px · section padding 24–40px vertical · card interior padding 24px.

---

## 6. Component Library

### nav-bar
Wordmark left, single utility link right ("View in browser"). Bottom border 1px hairline. Text-only wordmark, no logo required.

<div style="display:flex;align-items:center;justify-content:space-between;padding:10px 4px 24px;border-bottom:1px solid #e3ddd2;margin-bottom:32px;">
  <span style="font-size:14px;font-weight:500;letter-spacing:-0.2px;color:#2b2622;">Derrick Hodge</span>
  <span style="font-size:13px;font-weight:500;color:#6f6759;">View in browser</span>
</div>

### hero
Eyebrow (caption token) + headline (hero token) + one supporting sentence (body-lg). One idea per email.

### btn-primary (neutral, default)

<a href="#" style="display:inline-block;background-color:#2b2622;color:#f7f5f0;
  text-decoration:none;font-size:14px;font-weight:500;padding:8px 20px;border-radius:3px;">
  Open workspace →
</a>

### btn-ghost (secondary action)

<a href="#" style="display:inline-block;background-color:transparent;color:#2b2622;
  text-decoration:none;font-size:14px;font-weight:500;padding:8px 16px;border-radius:3px;
  border:1px solid #e3ddd2;">
  View details
</a>

### btn-accent-topaz (elevated CTA — use sparingly)

<a href="#" style="display:inline-block;background-color:#C97C3D;color:#ffffff;
  text-decoration:none;font-size:14px;font-weight:500;padding:8px 20px;border-radius:3px;">
  Pay invoice →
</a>

### badge-emerald (confirmed/complete status)

<span style="display:inline-block;background-color:#DCEEE4;color:#1F6B4C;
  font-size:12px;font-weight:600;padding:4px 10px;border-radius:3px;">
  Payment received
</span>

### badge-topaz (action-needed status)

<span style="display:inline-block;background-color:#F6E4D2;color:#A85D2C;
  font-size:12px;font-weight:600;padding:4px 10px;border-radius:3px;">
  Action needed
</span>

### card
Fill canvas-soft, 1px hairline border, 4px radius, 24px padding. Rows separated by hairline, label in body, value in body-strong.

<div style="background-color:#efe9de;border:1px solid #e3ddd2;border-radius:4px;padding:24px;">
  <div style="font-size:12px;color:#948c7d;margin-bottom:4px;">Summary</div>
  <div style="display:flex;justify-content:space-between;padding:10px 0;border-bottom:1px solid #e3ddd2;font-size:14px;">
    <span style="color:#6f6759;">Plan</span><span style="color:#453e35;font-weight:500;">Starter</span>
  </div>
</div>

### mono-block
Reference numbers, timestamps, status lines only — never paragraphs.

<div style="background-color:#efe9de;border:1px solid #e3ddd2;border-radius:4px;padding:16px 18px;
  font-family:'DM Mono','SFMono-Regular',Consolas,monospace;font-size:13px;color:#6f6759;">
  <span style="color:#948c7d;">bill to</span>&nbsp; Acme Manufacturing Co.
</div>

### hairline divider

<hr style="border:none;border-top:1px solid #e3ddd2;margin:32px 4px;">

**Protocol**: This page is the single source of truth for all email from hodge@agentmail.to. Update here first, then sync templates in `assets/brand/templates/`. Every send must conform.
Pushed to main. Live at https://dsamuelhodge.github.io/cos-site/work/workflows/agentmail-brand-cheat-sheet/
