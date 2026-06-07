---
type: concept
slug: llm-wiki-vs-rag
title: LLM Wiki vs RAG (when each wins)
created: 2026-05-28
updated: 2026-05-28
sources: [research-report]
confidence: 5
kind: comparison
---

# LLM Wiki vs RAG (when each wins)

## Overview

A decision guide distilled from the report. The [[llm-wiki-pattern]] and [[rag]] answer different questions and win in different regimes.

## LLM Wiki wins

- Knowledge accumulating over weeks-to-months
- Personal/team scale (~100 sources, ~400,000 words)
- When cross-references and synthesis are themselves the deliverable
- When human-readable provenance matters
- When explorations should compound

## RAG wins

- Very fresh data (changes by the hour)
- Very large corpora (thousands+ documents)
- Precision-critical, source-traceable domains (legal, medical)
- When lossy summarization is unacceptable

## Scale thresholds

Under ~100 pages: pure wiki. 100-1000: add BM25. 1000+: add vectors + a [[routing-layer]]. 10000+: a real graph DB — a knowledge product, not a personal wiki.

## Cross-references

- Built on [[compilation-vs-retrieval]]
- The synthesis answer is [[hybrid-retrieval]]
- At enterprise scale, [[edra]] pursues the commercial version of this tradeoff

## Open questions

- The thresholds are rules of thumb from the report, not measured universals.
