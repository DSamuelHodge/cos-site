---
schema: cos.person/v1
kind: person
title: "{{ replace .File.ContentBaseName "-" " " | title }}"
description: ""
role: ""
relation: ""
status: active # active | paused
date: "{{ .Date }}"
draft: true
tags: []
---
# Names and roles only. No phones, emails, or private detail.
