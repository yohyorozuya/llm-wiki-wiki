---
type: source
slug: qmd-repo
title: tobi/qmd primary repo docs
created: 2026-05-28
updated: 2026-05-28
sources: [qmd-repo]
confidence: 5
raw_file: qmd-repo.md
---

# tobi/qmd primary repo docs

## Overview

The README, CHANGELOG, and skill docs for [[qmd]] (@tobilu/qmd v2.0.0), fetched from GitHub. This is the definitive primary source for the [[hybrid-retrieval]] reference pipeline that [[andrej-karpathy|Karpathy]] recommends pairing with the [[llm-wiki-pattern]].

## What it adds (exact parameters)

The full pipeline with real numbers: LLM query expansion into 2 variants → parallel FTS5 BM25 + sqlite-vec → RRF fusion at **k=60** (original query ×2 weight, top-rank bonus +0.05/#1) → top-30 → LLM yes/no rerank with logprob confidence → **position-aware blend** (75/25 RRF-reranker for ranks 1-3, shifting to 40/60 by rank 11+). Default models: embeddinggemma-300M (embed), Qwen3-Reranker-0.6B (rerank), and a purpose-fine-tuned qmd-query-expansion-1.7B (generate). Tree-sitter chunking for code; regex for markdown.

## Notable design rationale

"Built in a single day"; SQLite over Elasticsearch because it's a personal single-binary tool; RRF chosen because it's "parameter-free and handles missing signals gracefully."

## Cross-references

- Primary source for [[qmd]]
- The reference design for [[hybrid-retrieval]]
- Created by [[tobi-lutke]]

## Open questions

- v2.0.0 now; the model defaults will rotate as better small models ship.
