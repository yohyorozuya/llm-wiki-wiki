---
type: implementation
slug: swarmvault
title: SwarmVault (swarmclawai)
created: 2026-05-28
updated: 2026-05-28
sources: [research-report, swarmvault-repo]
confidence: 5
creator: waydelyle / swarmclawai
license: MIT
stack: [TypeScript]
stars: ~399-489
category: engine
---

# SwarmVault (swarmclawai)

## Overview

The graph-first MIT-licensed engine for the [[llm-wiki-pattern]] (author waydelyle). "The local-first LLM Wiki, knowledge graph builder, and RAG knowledge base for AI agents... turns docs, code, transcripts, notes, and URLs into a durable markdown wiki plus a local graph you can inspect, query, and hand to agents" [[swarmvault-repo]]. Pitched explicitly as an Obsidian alternative and durable Claude Code / Codex / OpenClaw memory.

## One-command start

`npm install -g @swarmvaultai/cli`, then `swarmvault demo` builds a sample vault with three sources and opens the interactive graph viewer — no API keys (built-in heuristic provider; optional Ollama for embeddings). Ships an MCP server (`npx -y @swarmvaultai/cli mcp`) so Claude Code can query, compile, and lint directly.

## The knowledge graph (primary detail)

A [[typed-knowledge-graph]] with full provenance: "every edge traces back to a specific source and claim. Nodes carry freshness, confidence, and community membership." God nodes (highest-connectivity bridges) and communities are detected automatically, and graph report pages surface surprising connections in plain English. A rich graph CLI exposes `graph blast` (reverse-import impact), `graph validate --strict` (duplicate ids, dangling refs, confidence bounds), `graph cluster`, `graph diff` (against last committed graph), and `graph export --neo4j` (Cypher). Code-aware via tree-sitter, including SQL table/view nodes with read/write/join edges.

## What it adds beyond the base pattern

Automatic contradiction detection surfaced in the graph report (an answer to the [[lossy-summarization-critique]]); [[candidates-staging]]; agent-ready context packs; an agent task ledger; 30+ input formats; and a desktop viewer that reads the same on-disk files the CLI writes (no separate data model).

## Cross-references

- Implements [[llm-wiki-pattern]] (`implements`)
- Builds a [[typed-knowledge-graph]] with provenance
- Uses [[candidates-staging]]
- Contradiction detection answers the [[lossy-summarization-critique]]
- MCP + SQLite FTS/embeddings is [[hybrid-retrieval]]
- Answers the [[transactional-overhead-critique]] with graph validation

## Open questions

- Star count varies by listing (~399-489); a moving snapshot.
