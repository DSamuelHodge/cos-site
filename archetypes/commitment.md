---
schema: cos.commitment/v1
kind: commitment
title: "{{ replace .File.ContentBaseName "-" " " | title }}"
description: ""
status: open # open | kept | dropped
to: ""
when: ""
date: "{{ .Date }}"
draft: true
tags: []
---
