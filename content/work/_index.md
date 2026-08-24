---
schema: cos.page/v1
kind: section
title: Work
description: "Projects and tasks use Kaneo field names. GitHub issues dispatch agents. This site is the public index, not the task database."
weight: 2
date: 2026-08-24
draft: false
cascade:
  type: docs
---

Projects, tasks, and commitments. The site shows status. GitHub issues dispatch agents. Kaneo ingest uses the same keys as `data/schemas/project.yaml` and `data/schemas/task.yaml`.

**Kaneo task** (`POST /task/{projectId}`): `title`, `description`, `priority`, `status` required; `startDate`, `dueDate`, `userId` optional.

**Kaneo project** (`POST /project`): `name`, `workspaceId`, `icon`, `slug` required.

**Shared board values**

| Field | Allowed |
|---|---|
| `priority` | `no-priority`, `low`, `medium`, `high`, `urgent` |
| `status` | `todo`, `in-progress`, `blocked`, `done` (column slugs; create matching Kaneo columns) |
| `assignee_kind` | `cos`, `kaneo`, `linear`, `other-agent` |

{{< cards >}}
  {{< card link="projects/" title="Projects" icon="folder" subtitle="schema: cos.project/v1" >}}
  {{< card link="tasks/" title="Tasks" icon="check-circle" subtitle="schema: cos.task/v1" >}}
  {{< card link="commitments/" title="Commitments" icon="calendar" subtitle="schema: cos.commitment/v1" >}}
{{< /cards >}}
