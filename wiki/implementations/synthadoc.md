---
type: implementation
slug: synthadoc
title: Synthadoc (axoviq-ai)
created: 2026-05-28
updated: 2026-05-28
sources: [research-report, synthadoc-docs]
confidence: 5
creator: axoviq-ai
license: AGPL-3.0
stack: [Python]
stars: ~189
category: engine
---

# Synthadoc (axoviq-ai)

## Overview

The most architecturally sophisticated open-source compilation engine for the [[llm-wiki-pattern]] (AGPL-3.0, Python). Its self-description is almost a restatement of [[compilation-vs-retrieval]]: "Most knowledge-management tools retrieve and summarize at query time. Synthadoc inverts this: it compiles knowledge at ingest time. Every new source enriches and cross-links the entire corpus... The wiki is the artifact" [[synthadoc-docs]]. The Community Edition is the open base of what Axoviq ships to industrial customers.

## Architecture (from primary docs)

An **Orchestrator dispatches parallel IngestAgent, QueryAgent, and LintAgent sub-agents** with cost guards and retry backoff — the three operations of the pattern realized as concurrent agents. A 3-tier lazy-load capability system allows custom skills and hooks via a plug-and-play interface. Unified CLI + RESTful API. Local-first: the server binds only to 127.0.0.1.

On disk, alongside the human-readable `wiki/`, `raw_sources/`, `AGENTS.md`, and `log.md`, sits a `.synthadoc/` directory with `audit.db` (immutable audit trail), `jobs.db`, `cache.db` (LLM response cache), and `embeddings.db` (BM25 + vector index) — the SQLite substrate that answers the [[transactional-overhead-critique]]. Pages carry frontmatter with `status: active | contradicted | archived`, `confidence`, and per-source `sha256` hashes.

## What it adds beyond the base pattern

- The [[routing-layer]] (ROUTING.md branches) and an alias system.
- [[candidates-staging]] (off/threshold/all promotion gates).
- The knowledge-backend / context-pack pattern (token-budgeted excerpts via REST + MCP).
- [[adversarial-review]] (v0.5.0) — a second independent LLM interrogates every compiled page.
- [[claim-level-provenance]] (v0.5.0) — `^[filename:L–L]` markers tracing each paragraph to source lines.
- Per-agent model routing (Opus synthesis, Haiku [[lint]]); eight providers including a free Gemini Flash default and a no-API-key Claude Code mode.

## Cost model

Two-step ingest with cached analysis plus three stacked cache layers means re-ingesting similar sources costs near-zero tokens — addressing the [[ingest]] cost concern. The pitch: if you already pay for Claude Code, "the marginal cost of running a structured personal wiki on top of the same subscription is zero."

## Cross-references

- Implements [[llm-wiki-pattern]] (`implements`)
- Originated the [[routing-layer]], [[candidates-staging]], [[adversarial-review]], [[claim-level-provenance]]
- Its SQLite substrate answers the [[transactional-overhead-critique]]
- Its contradiction-flagging is a direct answer to the [[lossy-summarization-critique]]
- Enterprise/air-gapped framing parallels [[edra]]

## Open questions

- Routing-latency figures are measured on specific hardware; cold-start differs.
