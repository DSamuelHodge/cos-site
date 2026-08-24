---
schema: cos.feed/v1
kind: feed
title: "{{ replace .File.ContentBaseName "-" " " | title }}"
description: ""
source: "" # public URL or "cos"
date: "{{ .Date }}"
draft: false
tags: []
---
