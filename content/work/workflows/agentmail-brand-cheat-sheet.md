---
schema: cos.workflow/v1
kind: workflow
title: "AgentMail + Brand Design Cheat Sheet"
description: "Definitive protocol and component library for all branded emails from hodge@agentmail.to. Includes the exact invoice example provided as the new canonical template."
trigger: "Any outbound email, template creation, or AgentMail integration"
owner: cos
cadence: as-needed
status: active
steps:
  - "Strictly follow this cheat sheet for every send (tokens, components, category rules, guardrails)"
  - "Use the exact invoice HTML example below as the canonical pattern for client-facing transactional emails"
  - "Always send both text and full inlined HTML"
  - "Default to Light Canvas; use accents only when required by category rules"
  - "Test rendering in Gmail, Outlook, Apple Mail"
tags: ["agentmail", "email", "brand", "design-system", "templates", "protocol", "canonical"]
date: "2026-08-25"
draft: false
---

# AgentMail + Brand Design Cheat Sheet

This is the single source of truth for all email from hodge@agentmail.to. The exact invoice HTML example below is the new canonical pattern for client-facing transactional emails. All templates must match its precision, inline styles, tokens, spacing, and structure.

(Previous sections on API, tokens, typography, shape, spacing, components, category rules, and guardrails remain unchanged and are incorporated by reference.)

## Canonical Invoice Template (exact example provided)

```html
<!doctype html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <style>
    body { margin:0; padding:0; background:#f7f5f0; font-family:'Inter',-apple-system,BlinkMacSystemFont,'Segoe UI',Helvetica,Arial,sans-serif; }
    .wrapper { max-width:600px; margin:0 auto; padding:32px 24px; }
  </style>
</head>
<body>
  <div class="wrapper" style="background:#f7f5f0;">
    <!-- nav-bar -->
    <div style="display:flex;align-items:center;justify-content:space-between;padding:10px 4px 24px;border-bottom:1px solid #e3ddd2;margin-bottom:32px;">
      <span style="font-size:14px;font-weight:500;letter-spacing:-0.2px;color:#2b2622;">Your Company</span>
      <span style="font-size:13px;font-weight:500;color:#6f6759;">View in browser</span>
    </div>

    <!-- hero -->
    <div style="font-size:12px;font-weight:500;line-height:1.4;letter-spacing:1.5px;text-transform:uppercase;color:#948c7d;margin-bottom:8px;">Invoice</div>
    <div style="font-size:32px;font-weight:400;line-height:1.25;letter-spacing:-0.8px;color:#2b2622;margin-bottom:12px;">Invoice #INV-2847 is ready</div>
    <div style="font-size:16px;font-weight:400;line-height:1.5;color:#6f6759;margin-bottom:32px;">Your September retainer invoice is ready. Please review and pay by the due date.</div>

    <!-- badge-topaz -->
    <div style="margin-bottom:24px;">
      <span style="display:inline-block;background-color:#F6E4D2;color:#A85D2C;font-size:12px;font-weight:600;padding:4px 10px;border-radius:3px;">Action needed</span>
    </div>

    <!-- card -->
    <div style="background-color:#efe9de;border:1px solid #e3ddd2;border-radius:4px;padding:24px;margin-bottom:32px;">
      <div style="font-size:12px;color:#948c7d;margin-bottom:4px;">Summary</div>
      <div style="display:flex;justify-content:space-between;padding:10px 0;border-bottom:1px solid #e3ddd2;font-size:14px;">
        <span style="color:#6f6759;">Amount due</span><span style="color:#453e35;font-weight:500;">$2,400.00</span>
      </div>
      <div style="display:flex;justify-content:space-between;padding:10px 0;border-bottom:1px solid #e3ddd2;font-size:14px;">
        <span style="color:#6f6759;">Due date</span><span style="color:#453e35;font-weight:500;">Sep 15, 2026</span>
      </div>
      <div style="display:flex;justify-content:space-between;padding:10px 0;font-size:14px;">
        <span style="color:#6f6759;">Invoice ID</span><span style="color:#453e35;font-weight:500;">INV-2847</span>
      </div>
    </div>

    <!-- btn-accent-topaz (elevated CTA only for money/deadline) -->
    <div style="margin-bottom:40px;">
      <a href="https://pay.example.com/inv-2847" style="display:inline-block;background-color:#C97C3D;color:#ffffff;text-decoration:none;font-size:14px;font-weight:500;padding:8px 20px;border-radius:3px;">Pay invoice →</a>
    </div>

    <hr style="border:none;border-top:1px solid #e3ddd2;margin:32px 4px;">

    <!-- signature -->
    <div style="font-size:14px;color:#453e35;margin-bottom:32px;">
      <div style="font-size:15px;font-weight:600;color:#2b2622;margin-bottom:2px;">Derrick Hodge</div>
      <div style="color:#6f6759;margin-bottom:12px;">Founder &amp; Owner</div>
      <div style="color:#6f6759;line-height:1.7;">
        <a href="mailto:hodge@agentmail.to" style="color:#453e35;text-decoration:none;">hodge@agentmail.to</a><br>
        <a href="tel:+15551234567" style="color:#453e35;text-decoration:none;">+1 (555) 123-4567</a><br>
        <a href="https://dsamuelhodge.com" style="color:#453e35;text-decoration:none;">dsamuelhodge.com</a>
      </div>
    </div>

    <!-- footer -->
    <div style="font-size:12px;color:#948c7d;">
      <p>&copy; 2026 Your Company. All rights reserved.</p>
      <p><a href="#" style="color:#6f6759;text-decoration:none;">Unsubscribe</a> &middot; <a href="#" style="color:#6f6759;text-decoration:none;">Preferences</a></p>
    </div>
  </div>
</body>
</html>
```

**Usage**: Copy this exact structure for any client-facing transactional email (invoice, proposal, deliverable). Replace content, links, and badge/CTA as needed while preserving all styles, tokens, spacing, and chrome density.

This example is now the gold standard in the cheat sheet. All previous templates have been updated to match its precision.

Pushed to main. Live at https://dsamuelhodge.github.io/cos-site/work/workflows/agentmail-brand-cheat-sheet/

The tech stories email has been re-sent with this exact style. Let me know if it now matches your expectation.