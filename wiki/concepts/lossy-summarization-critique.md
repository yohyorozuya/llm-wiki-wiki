---
type: concept
slug: lossy-summarization-critique
title: The Lossy-Summarization Critique
created: 2026-05-28
updated: 2026-05-28
sources: [research-report, gupta-critique]
confidence: 4
kind: failure-mode
---

# The Lossy-Summarization Critique

## Overview

A precision concern about the [[llm-wiki-pattern]] raised most forcefully by Mehul Gupta [[gupta-critique]], and echoed by Joshi and Nayak. Building the wiki requires summarizing and compressing, and "compression always removes detail." Worse, a mis-synthesis is written into the wiki and persists across all subsequent queries.

Gupta's sharpest framing is the **self-correction argument**: with [[rag]], "the model goes back to the original documents each time. Even if it makes a mistake once, the next query has a chance to correct it because the source is still the same. LLM-Wiki changes that completely" [[gupta-critique]]. Because RAG re-derives from fixed sources, errors are transient; because the wiki caches synthesis, errors are durable.

## Mitigations

- [[lint]] is the load-bearing defense — it catches errors before they spread.
- The [[raw-layer]] stays immutable, so ground truth is always recoverable.
- Provenance-per-claim and confidence tagging flag uncertain content. [[synthadoc]] productized two strong answers: [[adversarial-review]] (a second independent LLM checks each page) and [[claim-level-provenance]] (every paragraph traces to exact source lines).

## Cross-references

- Critiques [[llm-wiki-pattern]] (`critiques`)
- Mitigated by [[lint]] and [[raw-layer]]
- Distinct from the structural [[transactional-overhead-critique]]

## Open questions

- How to verify a wiki without re-reading every source — the open verification problem.
