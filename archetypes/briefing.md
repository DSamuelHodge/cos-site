---
schema: cos.briefing/v1
kind: briefing
title: "{{ replace .File.ContentBaseName "-" " " | title }}"
description: ""
cadence: weekday
period: "{{ .Date.Format "2006-01-02" }}"
status: published
attention: []
due: []
open_loops: []
one_move: ""
tags: []
date: "{{ .Date }}"
draft: true
---

## Attention

## Due

## Open loops

## One move
