---
type: source
slug: swarmvault-repo
title: swarmclawai/swarmvault primary repo docs
created: 2026-05-28
updated: 2026-05-28
sources: [swarmvault-repo]
confidence: 4
raw_file: swarmvault-repo.md
---

# swarmclawai/swarmvault primary repo docs

## Overview

The README and skill listings for [[swarmvault]] (author waydelyle, MIT, ~399-489 stars), fetched from GitHub and swarmvault.ai. Confirms and expands the [[research-report]]'s account of it as the graph-first engine, with the actual CLI surface and the provenance model.

## What it adds

The real graph CLI (`graph blast/validate/cluster/diff/export --neo4j/query`), the explicit provenance model ("every edge traces back to a specific source and claim; nodes carry freshness, confidence, and community membership"), god-node/community detection, automatic contradiction detection surfaced in the graph report, code-awareness via tree-sitter (including SQL table/view nodes), and the self-described comparison table positioning it against the bare gist.

## Cross-references

- Primary source for [[swarmvault]]
- Its provenance edges are a [[typed-knowledge-graph]]
- Contradiction detection answers the [[lossy-summarization-critique]]
- MCP server + hybrid SQLite FTS/embeddings is [[hybrid-retrieval]]

## Open questions

- Star count varies by listing (399 vs 489); a moving target.
