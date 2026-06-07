---
type: concept
slug: raw-layer
title: The Raw Layer (immutable sources)
created: 2026-05-28
updated: 2026-05-28
sources: [research-report, karpathy-gist]
confidence: 5
kind: architecture
---

# The Raw Layer (immutable sources)

## Overview

Layer 1 of the [[llm-wiki-pattern]]: the original sources, kept immutable. "This is your source of truth." Because raw is never modified, the wiki can always be re-compiled from scratch, and any lossy-summarization error (see [[lossy-summarization-critique]]) is recoverable by returning to the source.

## Cross-references

- Layer 1 of [[llm-wiki-pattern]]
- Read by [[ingest]]
- The safety net against [[lossy-summarization-critique]]

## Open questions

- Immutability is a convention enforced by the [[claude-md-schema|schema]], not the filesystem — a misbehaving agent could still overwrite it without OS-level protections.
