---
schema: cos.goal/v1
kind: goal
title: "{{ replace .File.ContentBaseName "-" " " | title }}"
description: ""
horizon: quarter
area: life
status: active
cadence: weekly
success: ""
tags: []
date: "{{ .Date }}"
draft: true
---
