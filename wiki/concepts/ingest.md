---
type: concept
slug: ingest
title: Ingest (operation)
created: 2026-05-28
updated: 2026-05-28
sources: [research-report, karpathy-gist]
confidence: 5
kind: operation
---

# Ingest (operation)

## Overview

The first of the [[llm-wiki-pattern]]'s three operations, and the one where the real work happens. When a new source enters [[raw-layer|the raw layer]], the LLM reads it, discusses key takeaways with the user, writes a summary page, updates the index, updates relevant entity and concept pages across the wiki, and appends an entry to the log. "A single source might touch 10-15 wiki pages."

## Cost profile

Ingest is the expensive operation (~30-80k tokens for a substantial source) but it is paid **once per source** and amortized across all future queries. This is the core bet of [[compilation-vs-retrieval]].

## Discuss-first discipline

Karpathy's preferred mode is one-at-a-time and supervised: discuss takeaways before writing, because the user's memory and the source often disagree. Batch ingest is valid but less controllable.

## Cross-references

- Step in [[llm-wiki-pattern]]
- Updates [[index-md]] and [[log-md]]
- Guarded against duplicates by the Identity guard, see [[three-failure-modes]]

## Open questions

- How much supervision is too much? The friction of discuss-first vs the safety it provides.
