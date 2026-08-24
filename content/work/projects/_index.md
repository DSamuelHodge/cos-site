---
schema: cos.page/v1
kind: section
title: Projects
description: Bounded outcomes. Kind project. Kaneo name/slug/icon plus CoS goal, status, assignee_kind. Index only.
weight: 1
date: 2026-08-24
draft: false
---

Each project is a parent GitHub issue (`type: project`). Child tasks set `parent` (GitHub) and `projectId` (Kaneo).

Open with the [Project issue form](https://github.com/DSamuelHodge/cos-site/issues/new?template=project.yml). New page: `hugo new --kind project work/projects/slug.md`

```yaml
schema: cos.project/v1
kind: project
title: ""
name: ""          # Kaneo; same as title
slug: ""          # Kaneo; URL-safe
icon: folder      # Kaneo
description: ""
workspaceId: ""   # after Kaneo create
kaneo_id: ""
status: todo      # todo | in-progress | blocked | done
priority: no-priority
goal: ""
parent: ""
assignee_kind: cos
acceptance: []
links: { site: "", github: "", kaneo: "", linear: "" }
```
