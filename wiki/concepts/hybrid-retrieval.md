---
type: concept
slug: hybrid-retrieval
title: Hybrid Retrieval (wiki + BM25 + vector)
created: 2026-05-28
updated: 2026-05-28
sources: [research-report, qmd-repo]
confidence: 4
kind: architecture
---

# Hybrid Retrieval (wiki + BM25 + vector)

## Overview

What production implementations converge on past a few hundred pages: keep the wiki as the authoritative artifact, but index the **wiki pages** (not the raw documents) with BM25 + vector embeddings + an LLM reranker. This is the reconciliation of [[compilation-vs-retrieval]] — the wiki is *what gets retrieved*, retrieval is *how*.

## The reference pipeline (qmd)

[[qmd]]'s design has become a de facto standard, and its parameters are now documented from primary source [[qmd-repo]]: LLM query expansion into 2 variants → parallel FTS5 BM25 + sqlite-vec → Reciprocal Rank Fusion at **k=60** (original query ×2 weight) → top-30 → LLM yes/no reranking with logprob confidence → a **position-aware blend** that trusts RRF more for top ranks (75/25 at ranks 1-3) and the reranker more for the tail (40/60 at ranks 11+).

## The inversion

Classical [[rag]] embeds `raw/`. Hybrid embeds `wiki/`. Wiki pages are small, semantically clean, one-concept units — they produce far better vectors than arbitrary raw chunks.

## Cross-references

- Reconciles [[llm-wiki-pattern]] and [[rag]]
- Implemented by [[kb-cli]], [[synthadoc]], [[nashsu-llm-wiki]], and [[qmd]]
- Made scalable by the [[routing-layer]]

## Open questions

- At what scale does even hybrid retrieval need a true graph database underneath?
