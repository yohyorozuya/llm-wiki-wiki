---
type: concept
slug: llm-wiki-v2
title: LLM Wiki v2 (rohitg00 fork)
created: 2026-05-28
updated: 2026-05-28
sources: [akbp-v2-agentmemory]
confidence: 3
kind: principle
---

# LLM Wiki v2 (rohitg00 fork)

## Overview

A community successor spec to the [[llm-wiki-pattern]], published by Rohit Ghumare as a fork of [[karpathy-gist|Karpathy's gist]] (May 23, 2026) and "extended with lessons from building [[agentmemory]]." It affirms the original — "Everything in the original still applies... The core insight is correct: stop re-deriving, start compiling. RAG retrieves and forgets. A wiki accumulates and compounds. The three-layer architecture works" — then adds what production exposed: **confidence scoring, lifecycle states, knowledge graphs, and hybrid search**, with an explicit focus on "what separates a wiki that stays useful from one that rots."

## Why it matters

It's the clearest attempt to codify the field's hard-won lessons back into Karpathy's "idea file" format, and it's the basis for the [[akbp]] protocol. Where the original is deliberately abstract, v2 is opinionated about the failure modes ([[three-failure-modes]], [[staleness-problem]]).

## Cross-references

- `extends` the [[llm-wiki-pattern]] / [[karpathy-gist]]
- Basis for [[akbp]]
- Distilled from [[agentmemory]]
- Addresses the [[staleness-problem]] and [[three-failure-modes]]

## Open questions

- Whether a "v2" of an intentionally-abstract idea file gains traction, or fragments it.
