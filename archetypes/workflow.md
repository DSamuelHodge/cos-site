---
schema: cos.workflow/v1
kind: workflow
title: "{{ replace .File.ContentBaseName "-" " " | title }}"
description: ""
trigger: ""
owner: cos
cadence: as-needed
status: active
steps:
  - ""
tags: []
date: "{{ .Date }}"
draft: true
---
