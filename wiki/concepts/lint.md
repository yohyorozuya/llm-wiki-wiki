---
type: concept
slug: lint
title: Lint (operation)
created: 2026-05-28
updated: 2026-05-28
sources: [research-report, karpathy-gist]
confidence: 5
kind: operation
---

# Lint (operation)

## Overview

The third operation, and the load-bearing maintenance step of the [[llm-wiki-pattern]]. Periodically, the LLM health-checks the wiki: contradictions between pages, stale claims newer sources superseded, orphan pages with no inbound links, important concepts mentioned but lacking a page, missing cross-references, data gaps. Findings are surfaced, never auto-applied.

## Why it matters

Skipping lint is how a wiki rots. It is the antidote to the [[lossy-summarization-critique|lossy-summarization risk]] — the mechanism that catches a misunderstanding before it propagates across linked pages.

## Cost profile

Chunky (~100-200k tokens over 100 pages) — run weekly, not per-interaction.

## Cross-references

- Step in [[llm-wiki-pattern]]
- Directly addresses the [[three-failure-modes]]
- Mitigates the [[lossy-summarization-critique]]

## Open questions

- Can lint be automated as a nightly background pass? See the Dream cycle under [[three-failure-modes]] and [[nohmitaina]].
