---
schema: cos.page/v1
kind: section
title: Tasks
description: "One executable unit. Kind task. Kaneo createTask fields plus GitHub parent and assignee_kind. Index only."
weight: 2
date: 2026-08-24
draft: false
---

GitHub is the dispatch surface. Kaneo is the board. This page is not a second database.

Open with the [Task issue form](https://github.com/DSamuelHodge/cos-site/issues/new?template=task.yml). New page: `hugo new --kind task work/tasks/slug.md`

```yaml
schema: cos.task/v1
kind: task
title: ""            # Kaneo required
description: ""      # Kaneo required
projectId: ""        # Kaneo path param
parent: ""           # GitHub project issue number
priority: no-priority
status: todo         # column slug
startDate: ""
dueDate: ""
userId: ""
kaneo_id: ""
goal: ""
assignee_kind: cos
acceptance: []
links: { site: "", github: "", kaneo: "", linear: "" }
```
