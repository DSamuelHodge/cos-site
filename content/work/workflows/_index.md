---
schema: cos.page/v1
kind: section
title: Workflows
description: "How work actually moves. Kind workflow. Review when a process breaks or a new agent is added. Trigger plus ordered steps."
weight: 4
date: 2026-08-24
draft: false
---

Playbooks for Lucas, Kaneo, and Derrick. Tasks execute a workflow; the workflow is not itself a task.

**Cadence:** `as-needed`. Monthly glance during the first weekly briefing.

```yaml
schema: cos.workflow/v1
kind: workflow
title: ""
description: ""
trigger: ""
owner: cos
cadence: as-needed
status: active
steps: []
```

New page: `hugo new --kind workflow work/workflows/slug.md`
