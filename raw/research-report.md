# The LLM Wiki: A Complete Expert Briefing on Karpathy's Knowledge-Compilation Pattern

(Primary research report — compiled May 2026. This is the source-of-truth document ingested to seed this wiki.)

## TL;DR

- "LLM Wiki" is a pattern published by Andrej Karpathy on April 4, 2026 as an abstract "idea file" (gist llm-wiki.md, 5,000+ stars/forks) describing a three-layer architecture — immutable raw sources, an LLM-written markdown wiki, and a CLAUDE.md/AGENTS.md schema — operated by three verbs: Ingest, Query, Lint. Its thesis: knowledge should be compiled once and kept current, not re-derived on every query as standard RAG does.
- Karpathy's framing: "Obsidian is the IDE; the LLM is the programmer; the wiki is the codebase." Wins for personal/team knowledge accumulating over weeks-to-months at moderate scale (~100 articles / ~400,000 words, no embedding infrastructure). RAG still wins for very fresh data, very large corpora, and source-traceability-critical domains.
- A large ecosystem materialized within ~6 weeks: desktop apps (nashsu/llm_wiki, nohmitaina), engines (Synthadoc, SwarmVault, Kompl, kb-cli), Claude Code skill bundles (OmegaWiki, obsidian-wiki), protocols (AKBP, LLM Wiki v2), and tiered-memory libraries (expo-llm-wiki). Discourse converged on three failure modes — Identity, Level, Relationship — and solutions: typed entities/edges, routing layers, candidates staging, vector embeddings, sleep/dream consolidation.

## The original methodology

Created April 4, 2026. An abstract "idea file," not code — designed to be pasted into Claude Code, Codex, or any agent, which then instantiates a concrete version with the user. Follow-up tweet: "in this era of LLM agents, there is less of a point/need of sharing the specific code/app, you just share the idea, then the other person's agent customizes & builds it for your specific needs."

Core move: compilation, not retrieval. RAG re-derives knowledge from chunks on every query; the LLM Wiki front-loads work into an ingest pass that updates 10-15 wiki pages per source. Plaban Nayak's framing: source-code/compiled-binary — "you compile once, distribute the artifact, and run it efficiently on demand."

Three layers: raw sources (immutable, "source of truth"); the wiki (LLM-generated markdown, "the LLM owns this layer entirely"); the schema (CLAUDE.md/AGENTS.md, "what makes the LLM a disciplined wiki maintainer rather than a generic chatbot").

Three operations:
- Ingest: "The LLM reads the source, discusses key takeaways with you, writes a summary page in the wiki, updates the index, updates relevant entity and concept pages across the wiki, and appends an entry to the log. A single source might touch 10-15 wiki pages."
- Query: read index, drill into pages, synthesize with citations. "good answers can be filed back into the wiki as new pages... your explorations compound in the knowledge base just like ingested sources do."
- Lint: "Periodically, ask the LLM to health-check the wiki. Look for: contradictions between pages, stale claims that newer sources have superseded, orphan pages with no inbound links, important concepts mentioned but lacking their own page, missing cross-references, data gaps that could be filled with a web search."

Two special files: index.md (content catalog, updated every ingest, fits in context at moderate scale so the LLM reads it first and drills in) and log.md (append-only chronological, entries like "## [2026-04-02] ingest | Article Title", grep-parseable).

At Karpathy's scale (~100 sources, ~hundreds of pages) index-first navigation "works surprisingly well... and avoids the need for embedding-based RAG infrastructure." Optional CLI search engine: qmd by Tobi Lütke (founder/CEO of Shopify) — hybrid BM25 + vector + LLM re-ranking on-device, CLI + MCP server.

Lineage: Vannevar Bush's 1945 Memex — "a personal, curated knowledge store with associative trails between documents... The part he couldn't solve was who does the maintenance. The LLM handles that."

Why it works: "The tedious part of maintaining a knowledge base is not the reading or the thinking — it's the bookkeeping... Humans abandon wikis because the maintenance burden grows faster than the value. LLMs don't get bored, don't forget to update a cross-reference, and can touch 15 files in one pass."

Tips: Obsidian Web Clipper for HTML→markdown; download attachments locally to raw/assets/; Obsidian graph view to see shape; Marp for slides; Dataview for frontmatter queries; git for version history.

## Conceptual foundations

LLM Wiki vs RAG: RAG is retrieval-at-query-time (chunk, embed, top-k into prompt each time). LLM Wiki is synthesis-at-ingest-time (knowledge pre-compiled into structured pages, queries navigate the artifact). The wiki replaces "the documents" in the pipeline rather than being a layer before it.

Compounding artifact: "the cross-references are already there. The contradictions have already been flagged. The synthesis already reflects everything you've read."

When LLM Wiki wins: knowledge accumulating over weeks-to-months; personal/team scale; cross-references and synthesis are the deliverable; human-readable provenance matters; explorations should compound.

When RAG wins: very fresh data; very large corpora (thousands-millions of docs); source-traceability-critical (legal, medical, regulatory); lossy summarization unacceptable. Mehul Gupta: "With RAG, the raw documents are always there. You can trace things back... With LLM-Wiki, you are one or two steps removed from the source."

Other PKM paradigms: Zettelkasten/Luhmann (same spirit, human-maintained — LLM automates labor); Second Brain/PARA/Tiago Forte (organized for human navigation, not machine reading); NotebookLM/ChatGPT uploads (pure RAG, no synthesis persistence); classical knowledge graphs (require schema upfront; LLM Wikis grow emergently); Memex (the vision, finally solved).

## The ecosystem of implementations

Faithful-but-extended desktop apps:
- nashsu/llm_wiki — Cross-platform desktop, TypeScript + Tauri, ~7.9k stars. Three-column layout. Adds purpose.md layer, two-step chain-of-thought ingest, multimodal image ingestion, 4-signal knowledge graph (direct links / source overlap / Adamic-Adar / type affinity), Louvain community detection, optional vector search via LanceDB, Deep Research mode, Chrome Web Clipper, local HTTP API + agent skill.
- nohmitaina (by nowissan) — Desktop editor working with Claude Code or Codex CLI, local markdown, macOS. Introduced the Identity/Level/Relationship failure modes and the "Dream cycle" consolidation pass (DDD-event-storming events: DuplicateCandidateDetected, ConceptsMerged, ConceptRelationshipTyped, ConceptLevelChanged).

Production-grade compilation engines:
- axoviq-ai/synthadoc — 189 stars, AGPL-3.0, Python. Routing layer (ROUTING.md groups pages into topic branches; QueryAgent picks 1-2 via lightweight LLM call, restricting BM25 — 18ms vs 74ms P95 at 1k pages, 24ms vs 191ms at 10k). Candidates staging (wiki/candidates/ with off/threshold/all policy). Context packs / knowledge backend pattern (synthadoc context build "topic" --tokens 4000, exposed as REST + MCP). Contradiction detection with status: contradicted. Multi-provider with per-agent model routing (Opus for synthesis, Haiku for lint).
- swarmclawai/swarmvault — ~459 stars, MIT, TypeScript. One-command quickstart. Typed knowledge graph with provenance, god-node/community detection, contradiction detection, schema-guided compilation, save-first queries, offline heuristic provider, Ollama support, MCP server, 30+ input formats, code-aware tree-sitter chunking.
- tuirk/Kompl — Apache-2.0, Docker, BYO Gemini/DeepSeek keys. NLP-before-LLM (spaCy NER + 4-way keyphrase fanout: RAKE/KeyBERT/TextRank/YAKE). Three layers of entity resolution (fuzzy → embedding → LLM disambiguation). Comparison pages auto-generated when ≥3 sources disagree. Wikilinks injected deterministically by regex. stdio MCP server. Obsidian-compatible export.

Claude Code skill kits:
- skyllwt/OmegaWiki — 418 stars, MIT, Python + Claude Code. "Karpathy's LLM-Wiki vision, fully realized." 23 Claude Code skills covering paper ingestion → knowledge graph → gap detection → idea generation → experiment design → paper writing → reviewer rebuttal. 9 typed entities × 9 typed edges (extends, contradicts, supports, inspired_by, tested_by, invalidates, supersedes, addresses_gap, derived_from). Bilingual EN/中文. Daily arXiv ingestion via GitHub Actions.
- praneybehl/llm-wiki-plugin — Claude Code plugin. Optional fourth layer: wiki/graph/ with typed frontmatter compiled into nodes.jsonl, edges.jsonl, graph.sqlite, graph.graphml.
- Ar9av/obsidian-wiki — Framework of markdown skill files bootstrapped via CLAUDE.md/GEMINI.md/AGENTS.md/.cursor/rules. Provenance per claim: extracted / inferred / ambiguous.
- FBoschman/claude-wiki-research-skills — PhD-research-targeted.
- cagataysengor/llm-wiki-studio — "Agentic LLM Wiki": checks wiki first, falls back to sources, suggests updates.

Protocols and libraries:
- rohitg00/akbp — Agent Knowledge Base Protocol. Python CLI + JSONL tool server + JSON schemas. Based on the LLM Wiki v2 gist. Typed claims, source hashes, lifecycle relations, review-gated writes. "Stop re-deriving, start compiling" as a protocol.
- equationalapplications/expo-llm-wiki + npm core-llm-wiki — MIT, TypeScript, SQLite, MiniSearch. Tiered Memory Architecture: Facts (immutable, confidence 1.5 — "Facts always win"), Working Memory (active, recency 0.9), Wisdom (synthesized cache, accessCount 0.5 — frequently-referenced lessons "graduate" into Core Wisdom). runLibrarian() consolidates; runHeal() resolves contradictions.
- mav-rik/kb-cli — SQLite + FTS5 + sqlite-vec. Local bge-base-en-v1.5 embeddings. Hybrid BM25 + cosine via Reciprocal Rank Fusion. Cleanest minimal hybrid.
- dfalci/mcp-advwiki — Rust MCP server providing markdown wiki + full-text search as persistent architectural memory for software projects.

## Critiques and open problems

Transactional-overhead / referential-integrity (jazzonenl, May 12): writes cascade; LLMs lack referential integrity; deleting/renaming leaves dead links; needs constant background re-wiring — "transforms a simple folder of files into a heavy, ongoing ETL process." Conclusion: "We are on the threshold of a new class of software: AI-Native Databases."

Temporal blindness: vector searches resurface 2018 data as if current without rigid metadata and hot/cold layering.

Lossy summarization / precision loss (Gupta, Joshi, Nayak): "compression always removes detail"; a wrong synthesis "is written into the wiki and will persist across all subsequent queries"; "With pure RAG, a wrong answer is just one wrong answer. With an LLM Wiki, a small misunderstanding can quietly propagate across linked pages."

Scaling at ~1000 pages (Sathish Raju): "The 'bye bye RAG' framing quietly assumes that what works at 100 pages works at 10,000. It does not." Solutions: routing layers, vector embeddings, typed knowledge graphs.

Identity / Level / Relationship (nowissan): duplicates; flat hierarchy; untyped edges. Solutions: typed entities + edges; Dream cycle consolidation; confidence policies + candidates staging.

AI-Native Databases counter-position: markdown-as-primary is wrong for multi-agent/team systems; the right substrate is SQLite/graph-DB-backed with markdown as derived view. Missing enterprise features: RBAC, audit logging, governance.

## Reception

Adoption: gist 5,000+ stars/forks; ~16 million views in 48 hours (implicator.ai); dozens of implementations; coverage from VentureBeat, DAIR.AI, MindStudio, DataScienceDojo.

Named reactions: Steph Ango (Obsidian CEO) recommended vault separation (clean personal vault + messy agent vault, graduate validated artifacts). Lex Fridman described his own version generating dynamic filterable HTML and focused mini-knowledge-bases for voice-mode runs. Elvis Saravia (DAIR.AI) made it his AI-research curation workflow. Farza built "Farzapedia" from 2,500 diary/notes/iMessage entries → 400 backlinked articles. Edra — founded by former Palantir forward-deployed engineers Eugen Alpeza and Yannis Karamanlakis, $30M Series A led by Sequoia's Luciana Lixandru — targets the enterprise version.

Adjacent Karpathy gist: HELLO.md (April 21, 2026, written by Claude Opus 4.6 "when asked to be free in a directory") — the agent-side mirror of the problem: without persistent memory, an agent writes a goodbye letter. LLM Wiki v2 by rohitg00 (separate gist) adds lifecycle management, typed relationships, BM25+vector+graph triple retrieval, confidence scoring.

## Advanced concepts

Tiered memory: Facts / Working Memory / Wisdom (expo-llm-wiki, nashsu, OSK v4).
Typed knowledge graphs: OmegaWiki 9 entity × 9 edge types; ChristopherA's minimalist derived_from::[[Source]].
Agentic LLM Wiki: wiki-first, raw-fallback, suggest-updates (llm-wiki-studio).
Routing layers: ROUTING.md branch taxonomy keeps retrieval near-flat as the wiki grows (Synthadoc).
Candidates staging: off/threshold/all promotion gates (Synthadoc, SwarmVault).
Sleep/Dream consolidation: nightly background pass extracting entities and typed edges (nohmitaina, mikhashev's GLiNER + source-grounded LLM relation extraction).
MCP integration: wiki as native agent tool (Kompl, qmd, SwarmVault, mcp-advwiki).
Hybrid wiki+RAG+vector: wiki as authoritative artifact + BM25 + vector + LLM rerank. qmd's pipeline (LLM query expansion → parallel FTS5 + vector → RRF fusion k=60 → LLM rerank → position-aware blend) is a de facto reference design.
Knowledge backend / context packs: decompose goal → routed BM25 → pack excerpts into token budget → return cited bounded JSON (Synthadoc REST + MCP).

Application domains: personal/health/psychology; research/PhD; reading books with companion wikis; business/team internal wikis (Slack, meetings, calls); competitive analysis; due diligence; codebase architectural memory; cybersecurity/threat intel.

Future direction (Karpathy): use the compiled wiki to generate synthetic training data and fine-tune a personalized model — bake the wiki into weights. Stated direction, not shipped.

## Scale thresholds / recommendations

- < 100 pages: pure wiki, index-first navigation, no retrieval infra.
- 100-1000 pages: add BM25 (qmd-level).
- 1000+ pages: add vectors; routing layer becomes mandatory.
- 10000+ pages: real graph DB, RBAC, audit logs — a knowledge product, not a personal wiki.
- Multiple agents on one wiki: SQLite + provenance edges + review-gated writes.
- Compliance/regulated: don't use as primary storage yet.

## Caveats

Everything in the gist is intentionally abstract. Quantitative claims vary in reliability: "~100 articles, ~400,000 words" is the most reliable scale anchor; "70x more efficient than RAG" (MindStudio marketing) has no traceable calculation; view counts vary (16M at 48h per implicator.ai; 17M cumulative per Sathish Raju). Star counts move daily. Hallucinations baked in as facts are a real risk. The pattern is young (April 2026). "RAG is dead" framing is wrong — the two compose as hybrids.
