---
type: concept
slug: rag
title: RAG (Retrieval-Augmented Generation)
created: 2026-05-28
updated: 2026-05-28
sources: [research-report]
confidence: 5
kind: architecture
---

# RAG (Retrieval-Augmented Generation)

## Overview

The dominant prior paradigm the [[llm-wiki-pattern]] defines itself against. RAG chunks documents, embeds them, retrieves top-k by similarity at query time, and stuffs them into the prompt for on-the-fly synthesis. The knowledge is re-derived every query — "there's no accumulation."

## When RAG still wins

Very fresh data; very large corpora (thousands-to-millions of documents); source-traceability-critical domains (legal, medical, regulatory); cases where lossy summarization is unacceptable. Mehul Gupta: "With RAG, the raw documents are always there. You can trace things back." The report is firm that "RAG is dead" is wrong — the two compose as [[hybrid-retrieval]].

## Cross-references

- Contrasted with the wiki in [[compilation-vs-retrieval]] and [[llm-wiki-vs-rag]]
- Composed with the wiki in [[hybrid-retrieval]]

## Open questions

- Where exactly is the crossover scale at which RAG outperforms a pure wiki? Reportedly ~1000+ pages.
