---
type: concept
slug: comment-thread-implementations
title: Comment-Thread Implementations
created: 2026-05-28
updated: 2026-05-28
sources: [karpathy-gist]
confidence: 4
kind: comparison
---

# Comment-Thread Implementations

## Overview

The [[karpathy-gist|gist]]'s comment thread surfaced a wave of implementations the [[research-report|research report]] did not capture — direct evidence of how fast the [[llm-wiki-pattern]] ecosystem grew. This page collects the ones observed in the thread (April–May 2026) so the wiki reflects the primary source, not just the secondary summary.

## Implementations first seen here

- [[synto]] — local-first, Ollama/LM Studio, no vector DB
- [[link-memory]] — source-backed agent memory with MCP tools
- [[llm-wiki-mcp]] — the pattern as an MCP server, with a self-ingesting CLI
- [[llm-wiki-manager]] — full Claude Code skill, 8 operating modes
- [[sqz]] — token-compression tool composable with the workflow
- SciAI Wiki (cnpem) — an arXiv manuscript applying the pattern to science (provenance-preserving scientific memory)
- MindHub (trymindhub.com) — a hosted product wrapping the knowledge-base experience
- FrameCode VibeWork — a documentation/governance framework for AI-assisted dev

## What it demonstrates

This is the [[llm-wiki-pattern]] compounding in the wild: the report captured the major implementations; ingesting the primary gist added a second layer the report missed. The same compounding happened to *this* wiki when the gist was ingested as a second source — see [[this-wiki-is-recursive]].

## Cross-references

- Sourced from [[karpathy-gist]]
- Extends the catalog beyond the report's implementation pages
- Quantified in [[adoption-and-reception]]

## Open questions

- Many of these are early-stage; maturity and longevity vary widely.
