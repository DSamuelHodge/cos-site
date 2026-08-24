---
schema: cos.page/v1
kind: section
title: Routines
description: "Repeating personal cadence. Kind routine. Daily, weekday, weekly, or monthly. Review on the first weekly briefing of the month."
weight: 6
date: 2026-08-24
draft: false
---

Not a Kaneo board. These are the habits that keep Life moving. Ops is the domain; routines are the clock.

**Cadence values:** `daily` | `weekday` | `weekly` | `monthly`

```yaml
schema: cos.routine/v1
kind: routine
title: ""
description: ""
cadence: daily
when: morning
status: active
steps: []
```

New page: `hugo new --kind routine life/routines/slug.md`
