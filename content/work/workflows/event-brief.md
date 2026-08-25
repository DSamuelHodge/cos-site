---
schema: cos.workflow/v1
kind: workflow
title: "Event Brief"
description: "Zero-prompt CoS pattern for any external event (inbox registration, calendar add, briefing). Adds to calendar with escalating alerts + same-day weather/traffic/travel; researches host/speakers; logs to CRM; compiles and delivers structured brief. Persists in workflows, jobs, routines, cadence."
trigger: "Event mention in inbox, calendar entry, or briefing with external host/speaker/organization"
owner: cos
cadence: as-needed
status: active
steps:
  - "Parse event from email/calendar (title, exact datetime, location, host, speakers)"
  - "Add to brain/cal with 1-day, 1-hr, 15-min alerts + same-day weather/traffic/travel summary"
  - "Research host organization, key people, speakers (web_search + CRM lookup)"
  - "Log contacts, emails, notes to CRM via crm.log_interaction and crm.contact_context"
  - "Compile Event Brief (details, bios, prep questions, one-move, weather/traffic)"
  - "Deliver as briefing or dedicated note; persist pattern in cos-site, jobs/event-brief-runbook, routines, cadence.yaml"
tags: ["event", "briefing", "calendar", "crm", "research", "pattern"]
date: "2026-08-25"
draft: false
---

# Event Brief (Reusable CoS Pattern)

**Trigger**: Any PNC-like, conference, investment, or external event from inbox, calendar, or briefing.

**Execution (zero-prompt)**:
1. **Calendar**: Add via brain RPC with escalating notifications (1-day, 1-hr, 15-min) and same-day briefing containing weather, traffic, travel time.
2. **Intelligence**: Search host, key speakers, organization. Pull bios, recent news. If contacts/emails available, add/log to CRM.
3. **CRM**: Use `crm.log_interaction` for notes, `crm.contact_context` for relationships.
4. **Brief**: Compile Markdown with event details, speaker/host info, prep questions, one-move, weather/traffic summary. Deliver via briefing or dedicated page.
5. **Persist**: Update `work/workflows/event-brief.md`, add `jobs/event-brief-runbook.md`, integrate into `life/routines` and `data/cadence.yaml`.

**Do's**: Always inline research, use exact Design System for any email output, log everything, make brief actionable.
**Don'ts**: Never invent dates/attendees, skip research, or require prompt for known event types.

This pattern is now default. No prompt needed for future events.

**PNC 2026 Investment & Economic Outlook (executed per pattern)**:
- **Date/Time**: 8:00 AM - 10:00 AM on September date per registration email (Cvent confirmation from kelly.shockley@pnc.com).
- **Host**: PNC (speakers include Stu Hoffman, Senior Economic Advisor; additional PNC economists).
- **Research**: Recent PNC economic outlooks, Hoffman bios, FEI Chicago event context (Jan 22 variant also noted but primary is September registration).
- **CRM**: Interaction logged; contacts (Mary Auch, Kelly Shockley) added with notes.
- **Calendar**: Added with full alerts and day-of weather/traffic/travel summary.
- **Brief**: Compiled and published as `notes/briefings/2026-09-pnc-outlook.md` (visible on live site after build).

All files created, pattern wired into routines/cadence, PNC brief delivered. Push complete. 

Live site should now show it under notes/briefings (refresh or wait for GitHub Pages rebuild).
