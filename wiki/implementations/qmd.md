---
type: implementation
slug: qmd
title: qmd (Tobi Lütke)
created: 2026-05-28
updated: 2026-05-28
sources: [research-report, karpathy-gist, qmd-repo]
confidence: 5
creator: tobi-lutke
license: (see repo)
stack: [TypeScript, node-llama-cpp, sqlite-vec, GGUF]
category: retrieval
---

# qmd (Tobi Lütke)

## Overview

A local markdown search engine by [[tobi-lutke|Tobi Lütke]] (package `@tobilu/qmd`, v2.0.0) that [[andrej-karpathy|Karpathy]] recommends pairing with the [[llm-wiki-pattern]]. Not a wiki itself — a retrieval layer you point at any markdown folder. "Built in a single day," deliberately a single binary with no server dependencies (SQLite over Elasticsearch; sqlite-vec over an external vector DB). Its pipeline is the de facto reference design for [[hybrid-retrieval]] [[qmd-repo]].

## The pipeline (exact)

LLM query expansion into 2 variants → parallel FTS5 BM25 + sqlite-vec vector search → **Reciprocal Rank Fusion at k=60** (original query weighted ×2; top-rank bonus +0.05 for #1) → top-30 candidates → LLM yes/no re-ranking with logprob confidence → **position-aware blend** (ranks 1-3: 75% RRF / 25% reranker; ranks 4-10: 60/40; ranks 11+: 40/60). RRF was chosen because it is "parameter-free and handles missing signals gracefully."

## Default models

embeddinggemma-300M (embed), Qwen3-Reranker-0.6B (rerank), and a purpose-fine-tuned qmd-query-expansion-1.7B (generate) — all GGUF via node-llama-cpp (replacing the original Ollama backend in 0.6.0). Code files are chunked with tree-sitter (AST break points); markdown uses regex chunking.

## CLI + MCP

`qmd add/embed/search/vsearch/query/get`, plus an MCP server so the LLM can use it as a native tool. Skill guidance is explicit that BM25 (`qmd search`) is often better than semantic search when you know exact terms — a useful corrective to vector-search overuse.

## Cross-references

- Created by [[tobi-lutke]] (`created_by`)
- The reference implementation of [[hybrid-retrieval]]
- Recommended for [[llm-wiki-pattern]] at moderate scale
- Primary detail from [[qmd-repo]]

## Open questions

- Model defaults will rotate as better small models ship.
