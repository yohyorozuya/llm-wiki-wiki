---
type: implementation
slug: nashsu-llm-wiki
title: nashsu/llm_wiki
created: 2026-05-28
updated: 2026-05-28
sources: [research-report, nashsu-repo]
confidence: 5
creator: nashsu
license: (see repo)
stack: [TypeScript, Tauri]
stars: ~7900
category: desktop-app
---

# nashsu/llm_wiki

## Overview

The most feature-complete desktop implementation of the [[llm-wiki-pattern]] — a cross-platform Tauri app (latest observed v0.4.12). Its README states it plainly: "based on Karpathy's LLM Wiki pattern... We implemented the core ideas as a full desktop application with significant enhancements" [[nashsu-repo]].

## App shell

A three-column layout (Knowledge Tree / File Tree · Chat · Preview) with an icon sidebar switching between Wiki, Sources, Search, Graph, [[lint|Lint]], Review, Deep Research, and Settings. Resizable panels, a real-time Activity panel showing file-by-file [[ingest]] progress, and full state persistence across restarts.

## What it adds beyond the base pattern

- **purpose.md** — a new layer the original [[claude-md-schema|schema]] lacked: "the original has Schema (how the wiki works) but no formal place for why the wiki exists." purpose.md defines goals, key questions, scope, and an evolving thesis, and is read during every ingest and query.
- **Scenario templates** — Research / Reading / Personal Growth / Business / General, each pre-configuring purpose.md and schema.md.
- **Two-Step Chain-of-Thought Ingest** — analyze first, then generate pages, with source traceability and an incremental cache.
- **Multimodal Image Ingestion** — pulls images out of PDFs, captions them with a vision LLM, makes them searchable.
- **4-Signal Knowledge Graph** — direct links, source overlap, Adamic-Adar, and type affinity (a richer [[typed-knowledge-graph]]).
- **Louvain Community Detection** — automatic cluster discovery.
- **Optional vector search via LanceDB** — see [[hybrid-retrieval]].
- **Async Review System** — a [[lint]]-like pass that flags items for human judgment.
- **Local HTTP API + agent skill** — a token-protected JSON API at 127.0.0.1:19828 for hybrid search, file read, graph traversal, and source rescan, plus a one-command agent-skill install (`npx skills add`) into Claude Code / Codex.

## Cross-references

- Implements [[llm-wiki-pattern]] (`implements`)
- Optional LanceDB layer is [[hybrid-retrieval]]
- 4-signal graph is a [[typed-knowledge-graph]]
- Async review is a form of [[lint]]
- purpose.md extends the [[claude-md-schema]]

## Open questions

- Star count (~7.9k) and version move quickly; treat as a late-May 2026 snapshot.
