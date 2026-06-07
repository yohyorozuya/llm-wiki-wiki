---
type: implementation
slug: sqz
title: sqz (ojuschugh1)
created: 2026-05-28
updated: 2026-05-28
sources: [karpathy-gist]
confidence: 3
creator: ojuschugh1
license: Elastic License 2.0
stack: [Rust]
category: retrieval
---

# sqz (ojuschugh1)

## Overview

Not a wiki itself, but a token-compression tool heavily promoted in the [[karpathy-gist|gist]] thread and composable with the [[llm-wiki-pattern]] workflow. A single Rust binary that installs a PreToolUse hook to compress command output before it reaches the LLM. Reported savings: 24.7% average reduction across 3,003 compressions, up to 92% on repeated file reads via a dedup cache that returns a 13-token reference for repeat content.

## Relevance to the pattern

Addresses the token-cost concern around heavy [[ingest]] and [[lint]] passes — the operations that make the pattern expensive. Complements rather than implements the wiki.

## Cross-references

- Composes with [[llm-wiki-pattern]] for cost control
- Surfaced via [[comment-thread-implementations]]

## Open questions

- Savings figures are the author's self-reported benchmarks.
