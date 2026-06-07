---
type: concept
slug: routing-layer
title: Routing Layer
created: 2026-05-28
updated: 2026-05-28
sources: [research-report]
confidence: 4
kind: architecture
---

# Routing Layer

## Overview

A scaling technique from [[synthadoc]]: a ROUTING.md groups pages into named topic branches; a QueryAgent picks 1-2 relevant branches via a lightweight LLM call, restricting BM25 search to those branches. Keeps retrieval latency near-flat as the wiki grows (measured 18ms vs 74ms P95 at 1k pages; 24ms vs 191ms at 10k). Becomes effectively mandatory past ~1000 pages.

## Cross-references

- Makes [[hybrid-retrieval]] scale
- Implemented by [[synthadoc]]
- Answers the scaling concern in [[llm-wiki-vs-rag]]

## Open questions

- Branch taxonomy maintenance becomes its own bookkeeping problem at very large scale.
