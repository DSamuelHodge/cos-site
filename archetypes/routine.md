---
schema: cos.routine/v1
kind: routine
title: "{{ replace .File.ContentBaseName "-" " " | title }}"
description: ""
cadence: daily
when: morning
status: active
steps:
  - ""
tags: []
date: "{{ .Date }}"
draft: true
---
