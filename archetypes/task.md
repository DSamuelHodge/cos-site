---
schema: cos.task/v1
kind: task
title: "{{ replace .File.ContentBaseName "-" " " | title }}"
description: ""
projectId: ""
parent: ""
priority: no-priority
status: todo
startDate: ""
dueDate: ""
userId: ""
kaneo_id: ""
goal: ""
assignee_kind: cos
acceptance:
  - ""
links:
  site: ""
  github: ""
  kaneo: ""
  linear: ""
tags: []
date: "{{ .Date }}"
draft: true
---
