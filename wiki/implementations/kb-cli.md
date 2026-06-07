---
type: implementation
slug: kb-cli
title: kb-cli (mav-rik)
created: 2026-05-28
updated: 2026-05-28
sources: [research-report]
confidence: 3
creator: mav-rik
license: (see repo)
stack: [SQLite, FTS5, sqlite-vec]
category: retrieval
---

# kb-cli (mav-rik)

## Overview

A knowledge-base CLI for AI agents, described in the report as the cleanest minimal [[hybrid-retrieval]] implementation: SQLite + FTS5 + sqlite-vec, local bge-base-en-v1.5 embeddings, BM25 + cosine fused via Reciprocal Rank Fusion. Installs schema into `~/.claude/CLAUDE.md` or `~/.codex/AGENTS.md`.

## Cross-references

- Implements [[hybrid-retrieval]] minimally
- Pairs with [[claude-code]] / Codex via schema install

## Open questions

- None significant.
