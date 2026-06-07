---
type: concept
slug: three-failure-modes
title: The Three Failure Modes (Identity, Level, Relationship)
created: 2026-05-28
updated: 2026-05-28
sources: [research-report]
confidence: 5
kind: failure-mode
---

# The Three Failure Modes (Identity, Level, Relationship)

## Overview

The three problems implementers of the [[llm-wiki-pattern]] consistently hit, articulated cleanly by nowissan of [[nohmitaina]].

1. **Identity** — duplicate pages for the same concept under slightly different names (e.g. "Python" vs "Python 3").
2. **Level** — life-scale themes sitting flat alongside tactical findings; inconsistent granularity.
3. **Relationship** — typed semantics (contradicts, contains, similar) collapsing into a single untyped "related."

## Solutions the field developed

- Typed entities and edges — see [[typed-knowledge-graph]] and [[omegawiki]]'s 9×9 scheme.
- The **Dream cycle** — a background consolidation pass borrowed from sleep-based memory consolidation, emitting events like DuplicateCandidateDetected, ConceptsMerged, ConceptRelationshipTyped ([[nohmitaina]]).
- [[candidates-staging]] with confidence gates so uncertain pages stay out of the live wiki.
- The Identity guard in [[ingest]]: search existing slugs before creating.

## Cross-references

- A distinct *agency* failure is the [[staleness-problem]]
- Surfaced and addressed by [[lint]]
- Named by [[nohmitaina]]
- Solved structurally by [[typed-knowledge-graph]]

## Open questions

- Whether these three are exhaustive, or just the first three the community named.
