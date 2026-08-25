# Event Brief Runbook

**Trigger**: Inbox email with registration/confirmation keywords or cal.add for external event (PNC, conference, outlook, etc.).

**Automation** (Push job):
- Parse event (title, datetime, host, speakers) from email or calendar.
- `cal.add` via brain RPC with escalating alerts (1d, 1h, 15m) + same-day weather/traffic/travel summary.
- Web search host/speakers + `crm.contact_context` / `crm.log_interaction`.
- Compile Markdown brief (details, bios, CRM notes, prep questions, one-move).
- Save as `content/notes/briefings/YYYY-MM-event-slug.md` with briefing kind.
- Update cos-site, commit, push if approved.
- Deliver link in next briefing.

**PNC 2026 Investment & Economic Outlook**: Executed (registration from kelly.shockley@pnc.com, 8-10 AM September date, Stu Hoffman speaker, CRM logged, brief at notes/briefings/2026-09-pnc-outlook.md).

Run `push job validate` after edits. This is the reusable CoS pattern — no prompt needed.

Validated: 2026-08-25.
