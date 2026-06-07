---
type: implementation
slug: akbp
title: AKBP — Agent Knowledge Base Protocol (rohitg00)
created: 2026-05-28
updated: 2026-05-28
sources: [research-report, akbp-v2-agentmemory]
confidence: 4
creator: rohitg00
license: (see repo)
stack: [Python]
category: protocol
---

# AKBP — Agent Knowledge Base Protocol (rohitg00)

## Overview

An attempt to turn the [[llm-wiki-pattern]] into a formal protocol rather than an app by Rohit Ghumare: "a protocol surface for agent runtimes... a local-first, file-backed knowledge base that agents can read, write, verify, export, and carry across tools" [[akbp-v2-agentmemory]]. Based on the [[llm-wiki-v2]] spec. Reference implementation: a Python CLI, a newline-delimited JSON tool server, JSON schemas for requests/responses/records, and conformance tests (still alpha). Adds typed claims, source hashes, lifecycle relations, and review-gated writes. Tagline: "Stop re-deriving, start compiling."

Its protocol flow makes the [[ingest]] loop explicit and safe: evidence registered as sources → durable claims proposed → writes previewed and reviewed → approved artifacts stored as files → local indexes rebuilt → next session gets cited context. The review gate is a direct answer to the [[transactional-overhead-critique]].

## Cross-references

- Implements [[llm-wiki-pattern]] (`implements`) as a protocol
- Adds the integrity layer demanded by the [[transactional-overhead-critique]]
- Shares the typed-claims idea with [[typed-knowledge-graph]]

## Open questions

- Whether a shared protocol gains adoption across the fragmented ecosystem.
