---
type: concept
slug: log-md
title: log.md (the chronological log)
created: 2026-05-28
updated: 2026-05-28
sources: [research-report, karpathy-gist]
confidence: 5
kind: architecture
---

# log.md (the chronological log)

## Overview

The append-only history of an [[llm-wiki-pattern|LLM Wiki]]. Each [[ingest]] appends an entry like `## [2026-04-02] ingest | Article Title`, deliberately grep-parseable (`grep "^## \[" log.md`). Where [[index-md]] answers "what's in the wiki," log.md answers "what happened and when."

## Cross-references

- Appended by [[ingest]]
- Companion to [[index-md]]

## Open questions

- None significant; this is the simplest moving part of the pattern.
