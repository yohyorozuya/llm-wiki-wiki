---
type: concept
slug: compilation-vs-retrieval
title: Compilation vs Retrieval
created: 2026-05-28
updated: 2026-05-28
sources: [research-report, karpathy-gist]
confidence: 5
kind: principle
---

# Compilation vs Retrieval

## Overview

The conceptual core of the [[llm-wiki-pattern]]. [[rag|RAG]] retrieves and synthesizes at query time — every question re-derives knowledge from raw chunks. The LLM Wiki front-loads synthesis into [[ingest]], producing a durable artifact. Plaban Nayak's framing: source code vs compiled binary — "you compile once, distribute the artifact, and run it efficiently on demand."

## The key reframing

The wiki is not a layer *before* RAG. The wiki **replaces "the documents"** in the pipeline. RAG cares about retrieval; the wiki cares about *what gets retrieved*. A mature system does both — see [[hybrid-retrieval]].

## Cross-references

- The principle behind [[llm-wiki-pattern]]
- Contrast detailed in [[llm-wiki-vs-rag]]
- Reconciled with retrieval in [[hybrid-retrieval]]

## Open questions

- The compounding bet assumes synthesis quality is high; if the LLM mis-synthesizes, the error compounds too. See [[lossy-summarization-critique]].
