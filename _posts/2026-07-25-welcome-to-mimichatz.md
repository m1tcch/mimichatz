---
layout: post
title: welcome to mimichatz
description: >
  What this blog is, what it covers, and why it exists.
categories: []
tags: [meta]
---

Welcome to **mimichatz** — a blog documenting threat research, interesting
projects, and tooling.

Research that never gets written up might as well not have happened. This site
is the forcing function: if it was worth investigating, it's worth documenting.

Expect posts on:

- Malware analysis and TTP write-ups
- Detection engineering notes
- Tools — built, broken, or reviewed
- Lab and homelab projects

## writing posts

New posts are Markdown files in `_posts/` named `YYYY-MM-DD-title.md` with a
small front matter block:

```yaml
---
layout: post
title: my post title
description: >
  One-line summary shown on cards, in feeds and in search results.
categories: [threat-research]
tags: [malware, windows]
---
```

Posts with a category from `_featured_categories/` (currently
`threat-research`, `tooling`, `projects`) appear on that category's own page,
linked in the sidebar. Commit, push, and GitHub Pages does the rest.
