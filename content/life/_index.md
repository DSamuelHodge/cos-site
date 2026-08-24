---
schema: cos.page/v1
kind: section
title: Life
description: "Personal operating system. Public-safe titles and status only. Child kinds: person, ops, focus, education."
weight: 1
date: 2026-08-24
draft: false
cascade:
  type: docs
---

People, operations, focus, and education. CRM detail stays in `cos.db`. These pages are indexes.

**Child contract** — every new page under Life starts from `schema: cos.page/v1` plus:

| kind | Extra fields | status values |
|---|---|---|
| `person` | `role`, `relation` | `active`, `paused` |
| `ops` | `area`, `cadence` | `active`, `paused` |
| `focus` | `area`, `cadence` | `active`, `paused` |
| `education` | `subject`, `level`, `goal` | `learning`, `paused`, `done` |

Always set `title` and `description`. No phones, emails, or private notes.

{{< cards >}}
  {{< card link="people/" title="People" icon="users" subtitle="kind: person" >}}
  {{< card link="ops/" title="Operations" icon="home" subtitle="kind: ops" >}}
  {{< card link="focus/" title="Focus" icon="sparkles" subtitle="kind: focus" >}}
  {{< card link="education/" title="Education" icon="academic-cap" subtitle="kind: education" >}}
{{< /cards >}}
