# nashsu/llm_wiki — primary repo docs (README, releases)

Source: github.com/nashsu/llm_wiki (README.md, llm-wiki.md, releases). Fetched late May 2026.

## What it is

"LLM Wiki is a cross-platform desktop application that turns your documents into an organized, interlinked knowledge base — automatically." Explicitly: "This project is based on Karpathy's LLM Wiki pattern... We implemented the core ideas as a full desktop application with significant enhancements." Latest observed release: v0.4.12 (also v0.4.9 seen).

## UI / app shell

- Three-column layout: Knowledge Tree / File Tree (left) + Chat (center) + Preview (right).
- Icon sidebar to switch between: Wiki, Sources, Search, Graph, Lint, Review, Deep Research, Settings.
- Custom resizable panels with min/max constraints; real-time Activity panel showing file-by-file ingest progress.
- All state persisted (conversations, settings, review items, project config survive restarts).

## The purpose.md addition

"The original has Schema (how the wiki works) but no formal place for why the wiki exists. We added purpose.md: defines goals, key questions, research scope, evolving thesis. The LLM reads it during every ingest and query for context."

## Scenario templates

Research, Reading, Personal Growth, Business, General — each pre-configures purpose.md and schema.md.

## Core features

- Two-Step Chain-of-Thought Ingest — LLM analyzes first, then generates wiki pages with source traceability and incremental cache.
- Multimodal Image Ingestion — extracts embedded images from PDFs, generates factual captions with a vision LLM, surfaces them in image-aware search results with lightbox preview and jump-to-source.
- 4-Signal Knowledge Graph — relevance model combining direct links, source overlap, Adamic-Adar, and type affinity.
- Louvain Community Detection — automatic knowledge cluster discovery with cohesion scoring.
- Graph Insights — surprising connections and knowledge gaps with one-click Deep Research.
- Vector Semantic Search — optional embedding-based retrieval via LanceDB, any OpenAI-compatible endpoint.
- Async Review System — LLM flags items for human judgment with predefined actions and pre-generated search queries.
- Chrome Web Clipper — one-click capture with auto-ingest.
- Local HTTP API + AI Agent Skill — built-in 127.0.0.1:19828 token-protected JSON API for hybrid search, file read, graph traversal, source rescan; ready-made agent skill installs into Claude Code / Codex with `npx skills add …`.
