# Synthadoc — primary docs (axoviq-ai)

Sources: github.com/axoviq-ai/synthadoc (README, docs/design.md, user-quick-start-guide, releases), DEV Community posts by paulmchen, gist thread comments. Fetched late May 2026.

## What it is

"A domain-agnostic LLM knowledge compilation engine. It reads raw source documents and uses an LLM to synthesize them into a persistent structured wiki. Knowledge is compiled at ingest time — not at query time." Open source under AGPL-3.0. Community Edition is the open base of what Axoviq ships to industrial customers.

## Core positioning (verbatim themes)

- "Most knowledge-management tools retrieve and summarize at query time. Synthadoc inverts this: it compiles knowledge at ingest time. Every new source enriches and cross-links the entire corpus, not just appends a new chunk. The wiki is the artifact."
- "Contradictions are caught, not blended. When two sources disagree, Synthadoc flags the page — RAG silently averages both claims."
- "The artifact outlives the tool. Close the server, open the wiki folder in any Markdown editor — the knowledge is all there, human-readable, no proprietary format."
- "Pre-compiled structured knowledge beats query-time synthesis for contradiction detection, graph traversal, and offline access."

## Architecture

- Orchestrator dispatches parallel IngestAgent, QueryAgent, LintAgent sub-agents with cost guards and retry backoff.
- 3-tier lazy-load capability system; custom skills and hooks via plug-and-play interface.
- Unified interface via CLI and RESTful endpoints: ingestion, querying, automated linting, security auditing, job orchestration.
- Local-first — server binds only to 127.0.0.1. Obsidian-native — pages are valid Obsidian notes with [[wikilinks]], YAML frontmatter, Dataview compatibility.

## On-disk layout

```
my-wiki/
  wiki/              compiled Markdown pages
  raw_sources/       original source documents
  hooks/             wiki-specific hook scripts
  AGENTS.md          LLM instructions for this domain
  log.md             human-readable activity log
  .synthadoc/
    config.toml      per-project configuration
    audit.db         immutable audit trail
    jobs.db          job queue
    cache.db         LLM response cache
    embeddings.db    BM25 + vector search index
    logs/            rotating JSON-lines operational log + OpenTelemetry traces
```

## Page frontmatter (example)

```
title: Alan Turing
tags: [computer-science, cryptography, turing-test]
status: active        # active | contradicted | archived
confidence: high      # high | medium | low
created: '2026-04-10'
sources:
  - file: turing-biography.pdf
    hash: sha256:abc123…
    ingested: '2026-04-10'
```

## Cost model

Two-step ingest with cached analysis means repeated ingest of similar sources costs near-zero tokens; three cache layers stack. "If you are already using Claude Code or Opencode daily, the marginal cost of running a structured personal wiki on top of the same subscription is zero."

## Providers

Eight providers including Gemini Flash (default, free tier), DeepSeek (very low cost), Claude Code, Opencode. `provider = "claude-code"` works with no API key if you already have Claude Code.

## Version history (observed)

- v0.3.0 — knowledge gap detection hardening; DeepSeek provider; YouTube/any-content ingest.
- v0.5.0 — Adversarial Review (a second independent LLM interrogates every compiled page for overreach, unsupported generalizations, contradictions; you appoint the judge in config.toml, different provider/family recommended); Claim-Level Provenance (every compiled paragraph gets a ^[filename:L–L] citation marker tracing to exact source lines; Obsidian renders markers as chips opening a Source Viewer with PDF page resolution); routing + alias system; candidates staging; redesigned Obsidian plugin.

## Enterprise framing

"Synthadoc acts as a domain-specific knowledge base within a larger multi-agent autonomous system — ingesting operational knowledge, protecting proprietary data behind a local service boundary, and exposing it to other agents through a clean HTTP API without ever externalising the raw corpus. This is a hard requirement in regulated industries where sensitive knowledge must remain air-gapped."
