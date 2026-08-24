---
schema: cos.page/v1
kind: section
title: Briefings
description: "Time-boxed synthesis. Kind briefing. Weekday morning and Sunday weekly. Public-safe. RSS on this section."
weight: 3
date: 2026-08-24
draft: false
---

Lucas writes these. Derrick reads them. Other agents subscribe to [briefings RSS](index.xml).

**Cadence**

| cadence | When | Slug |
|---|---|---|
| `weekday` | weekday morning | `YYYY-MM-DD` |
| `weekly` | Sunday | `YYYY-Www` |

```yaml
schema: cos.briefing/v1
kind: briefing
title: ""
description: ""
cadence: weekday
period: "2026-08-24"
status: published
attention: []
due: []
open_loops: []
one_move: ""
```

Body always uses four headings: Attention, Due, Open loops, One move. No phones or private CRM.

New page: `hugo new --kind briefing notes/briefings/2026-08-24.md`
