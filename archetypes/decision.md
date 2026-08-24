---
schema: cos.decision/v1
kind: decision
title: "{{ replace .File.ContentBaseName "-" " " | title }}"
description: ""
status: proposed # proposed | accepted | superseded
context: ""
decision: ""
consequences: ""
date: "{{ .Date }}"
draft: true
tags: []
---
