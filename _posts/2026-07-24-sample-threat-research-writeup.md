---
layout: post
title: "sample: anatomy of a threat research write-up"
description: >
  A placeholder post showing the formatting available for analysis write-ups —
  headings, code, tables, and IOC lists.
categories: [threat-research]
tags: [sample]
---

> This is a **sample post** demonstrating the template's formatting. Replace it
> with a real write-up and delete this note.

A good analysis post usually follows the same skeleton: summary up front,
technical detail in the middle, indicators and detections at the end.

* toc
{:toc}

## executive summary

Two or three sentences a busy reader can stop after. What was found, why it
matters, what to do about it.

## technical analysis

Inline code like `rundll32.exe` or `HKCU\Software\...` stands out from prose.
Code blocks get full syntax highlighting, with optional file names and
captions:

```python
# file: "sha256_file.py"
import hashlib

def sha256_file(path: str) -> str:
    h = hashlib.sha256()
    with open(path, "rb") as f:
        for chunk in iter(lambda: f.read(8192), b""):
            h.update(chunk)
    return h.hexdigest()
```

Shell sessions work too:

```console
$ file sample.bin
sample.bin: PE32+ executable (GUI) x86-64, for MS Windows
```

### detection notes

Blockquotes work well for analyst commentary or quoted report text. Hydejack
also renders a floating table of contents on large screens.

## indicators of compromise

Wide IOC tables scroll horizontally on small screens:

| Type   | Value                                                              | Note               |
|--------|--------------------------------------------------------------------|--------------------|
| SHA256 | `0000000000000000000000000000000000000000000000000000000000000000` | placeholder        |
| Domain | `example[.]invalid`                                                | defanged, sample   |
| IP     | `203.0.113.10`                                                     | TEST-NET-3, sample |

## references

- [MITRE ATT&CK](https://attack.mitre.org/)
- Link lists render like this.
