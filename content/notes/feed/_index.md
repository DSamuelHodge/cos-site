---
schema: cos.page/v1
kind: section
title: Feed
description: Shareable newsfeed. Kind feed. Subscribe to this section RSS. Public-safe items only.
weight: 2
date: 2026-08-24
draft: false
---

Own and shareable updates. Humans read this page. Readers and agents subscribe to [feed RSS](index.xml) and [JSON](index.json).

```yaml
schema: cos.feed/v1
kind: feed
title: ""
description: ""   # this is the RSS summary
source: cos       # public URL or "cos"
date: ""          # item date
tags: []
draft: false
```

New item: `hugo new --kind feed notes/feed/YYYY-MM-DD-slug.md`
