---
schema: cos.project/v1
kind: project
title: "{{ replace .File.ContentBaseName "-" " " | title }}"
name: "{{ replace .File.ContentBaseName "-" " " | title }}"
slug: "{{ .File.ContentBaseName }}"
icon: folder
description: ""
workspaceId: ""
kaneo_id: ""
status: todo
priority: no-priority
goal: ""
parent: ""
assignee_kind: cos
acceptance:
  - Outcome is shipped or explicitly dropped
  - Child tasks are closed or moved
links:
  site: ""
  github: ""
  kaneo: ""
  linear: ""
tags: []
date: "{{ .Date }}"
draft: true
---
