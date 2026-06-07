---
type: concept
slug: query
title: Query (operation)
created: 2026-05-28
updated: 2026-05-28
sources: [research-report, karpathy-gist]
confidence: 5
kind: operation
---

# Query (operation)

## Overview

The second operation of the [[llm-wiki-pattern]]. The LLM reads [[index-md]] first to orient, drills into the 3-5 relevant pages, and synthesizes an answer with ``wikilink`` citations. Cheaper than expected (~15k tokens) because the synthesis was already done at [[ingest]] time.

## The compounding insight

"Good answers can be filed back into the wiki as new pages... your explorations compound in the knowledge base just like ingested sources do." A query answer worth keeping becomes a synthesis page.

## Cross-references

- Step in [[llm-wiki-pattern]]
- Reads [[index-md]]
- Cheaper than [[rag]] queries because synthesis is pre-done — see [[compilation-vs-retrieval]]

## Open questions

- At what page count does index-first navigation stop working and require [[hybrid-retrieval]]?
