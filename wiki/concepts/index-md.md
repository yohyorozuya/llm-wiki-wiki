---
type: concept
slug: index-md
title: index.md (the catalog)
created: 2026-05-28
updated: 2026-05-28
sources: [research-report, karpathy-gist]
confidence: 5
kind: architecture
---

# index.md (the catalog)

## Overview

The content catalog of an [[llm-wiki-pattern|LLM Wiki]] — a list of every page with a one-line summary, updated on every [[ingest]]. At moderate scale it fits in a context window, so the agent reads it first during [[query]] and drills in. This is what makes index-first navigation work without [[rag]] infrastructure.

## Distinct from the schema

index.md is the library catalog (what's in the system right now); [[claude-md-schema|CLAUDE.md]] is the constitution (how the system works). The catalog changes constantly; the constitution rarely.

## Cross-references

- Updated by [[ingest]]
- Read first by [[query]]
- Companion to [[log-md]]

## Open questions

- When the catalog outgrows the context window, you need a [[routing-layer]].
