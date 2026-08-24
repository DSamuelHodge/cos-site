---
schema: cos.page/v1
kind: section
title: Goals
description: "What this season is for. Kind goal. Review weekly with the Sunday briefing. Horizon quarter, year, or ongoing."
weight: 5
date: 2026-08-24
draft: false
---

Projects and tasks must name a `goal`. This page is the list those fields point at. Public-safe titles only.

**Cadence:** review `weekly` (Sunday briefing). Rewrite `quarter` or `year` when the horizon ends.

```yaml
schema: cos.goal/v1
kind: goal
title: ""
description: ""
horizon: quarter
area: life
status: active
cadence: weekly
success: ""
```

New page: `hugo new --kind goal life/goals/slug.md`
