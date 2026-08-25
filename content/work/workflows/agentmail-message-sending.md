---
schema: cos.workflow/v1
kind: workflow
title: "AgentMail — Message Sending Cheat Sheet"
description: "Comprehensive reference for sending messages, replies, and managing state via the AgentMail API and SDK. Includes schemas, best practices for HTML/text, label-based read tracking, and Python examples."
trigger: "Implementing email features, drafting replies, integrating with agents, or triaging AgentMail inboxes"
owner: cos
cadence: as-needed
status: active
steps:
  - "Review endpoint schema and limits before sending"
  - "Always include both text and full HTML body with inlined styles"
  - "Use labels for workflow (unread, needs-reply, processed)"
  - "Prefer SDK methods (send, reply_to_message, etc.) over raw HTTP when possible"
  - "Test with extracted_text/extracted_html for replies"
tags: ["agentmail", "email", "api", "sdk", "mcp", "workflow"]
date: "2026-08-25"
draft: false
---


## Endpoint
POST /v0/inboxes/:inbox_id/messages/send
Auth: Bearer <token>

## Body Schema (Send Message)
| Field        | Type                   | Required | Notes |
|--------------|-------------------------|----------|-------|
| to         | string \| string[]      | Optional | Recipient(s) |
| cc         | string \| string[]      | Optional | |
| bcc        | string \| string[]      | Optional | |
| reply_to   | string \| string[]      | Optional | Reply-to address(es) |
| subject    | string                  | Optional | |
| text       | string                  | Optional | Plain-text body (fallback) |
| html       | string                  | Optional | Full HTML document (rich body) |
| labels     | string[]                | Optional | Tag the message |
| `attachments`| object[]                | Optional | See Attachments doc |
| headers    | map<string,string>      | Optional | Custom headers |
| `track_opens`| boolean                 | Optional | Requires custom domain + HTML body; fires once per message, not per recipient |

Response: { message_id, thread_id }

Limit: max 50 recipients total across to + cc + bcc.

## Related Endpoints
- messages.reply(inbox_id, message_id, text, html?, attachments?, reply_all?)
- messages.forward(inbox_id, message_id, to, subject?, text?, html?)
- messages.list(inbox_id, limit?, page_token?, labels?, before?, after?, from?, to?, subject?)
- messages.search(inbox_id, q, limit?, page_token?) — full-text, relevance-ranked
- messages.update(inbox_id, message_id, add_labels?, remove_labels?)
- messages.get / get_raw / get_attachment(inbox_id, message_id, ...)

## HTML + Text Best Practice
- Always send both `text` and `html`. HTML renders in most clients; text is the fallback + improves deliverability.
- html = a full HTML document (`<html><head>...</head><body>...</body></html>`), not a fragment.
- CSS must be inlined in a `<style>` tag inside `<head>` — this is the only reliable cross-client method (Gmail, Outlook, Apple Mail).
- Structure pattern: .email-wrapper → .email-header → .email-content → .email-footer, max-width ~600px, system font stack.

## Receiving Content
- extracted_text / extracted_html = new reply content only (quoted history auto-stripped).
- text`/`preview may be absent on HTML-only forwarded emails (common with Gmail/Outlook) — always treat html as primary, text as optional.

## Read/Unread Tracking
No native "mark as read" — use labels:

client.inboxes.messages.update(inbox_id, message_id, add_labels=["read"], remove_labels=["unread"])

Filter unread: messages.list(inbox_id, labels=["unread"])

## Inbound Auth
Emails failing SPF/DKIM/DMARC are dropped. Missing auth headers → processed but labeled unauthenticated.

## Quick Python Example

```python
from agentmail import AgentMail
client = AgentMail(api_key="YOUR_KEY")

client.inboxes.messages.send(
    inbox_id="agent@agentmail.to",
    to="user@example.com",
    subject="Hello",
    text="Plain text body",
    html="<html><head><style>body{font-family:sans-serif}</style></head><body><p>HTML body</p></body></html>",
    labels=["outreach"]
)
```

Source: [docs.agentmail.to/api-reference/inboxes/messages/send](https://docs.agentmail.to/api-reference/inboxes/messages/send) · [agentmail.to/docs/messages](https://www.agentmail.to/docs/messages)
