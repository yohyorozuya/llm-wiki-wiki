# llm-wiki.md (Andrej Karpathy)

Source: https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f
Created: April 4, 2026 16:25. Stars/forks displayed as "5,000+" (capped); search metadata observed up to ~33,940 stars / ~7,226 forks / ~845 comments as of late May 2026.

# LLM Wiki

A pattern for building personal knowledge bases using LLMs.

This is an idea file, it is designed to be copy pasted to your own LLM Agent (e.g. OpenAI Codex, Claude Code, OpenCode / Pi, or etc.). Its goal is to communicate the high level idea, but your agent will build out the specifics in collaboration with you.

## The core idea

Most people's experience with LLMs and documents looks like RAG: you upload a collection of files, the LLM retrieves relevant chunks at query time, and generates an answer. This works, but the LLM is rediscovering knowledge from scratch on every question. There's no accumulation. Ask a subtle question that requires synthesizing five documents, and the LLM has to find and piece together the relevant fragments every time. Nothing is built up. NotebookLM, ChatGPT file uploads, and most RAG systems work this way.

The idea here is different. Instead of just retrieving from raw documents at query time, the LLM incrementally builds and maintains a persistent wiki — a structured, interlinked collection of markdown files that sits between you and the raw sources. When you add a new source, the LLM doesn't just index it for later retrieval. It reads it, extracts the key information, and integrates it into the existing wiki — updating entity pages, revising topic summaries, noting where new data contradicts old claims, strengthening or challenging the evolving synthesis. The knowledge is compiled once and then kept current, not re-derived on every query.

This is the key difference: the wiki is a persistent, compounding artifact. The cross-references are already there. The contradictions have already been flagged. The synthesis already reflects everything you've read.

You never (or rarely) write the wiki yourself — the LLM writes and maintains all of it. You're in charge of sourcing, exploration, and asking the right questions. In practice, I have the LLM agent open on one side and Obsidian open on the other. Obsidian is the IDE; the LLM is the programmer; the wiki is the codebase.

Contexts: Personal (goals, health, psychology); Research (deep on a topic over weeks/months); Reading a book (companion wiki, à la Tolkien Gateway); Business/team (internal wiki fed by Slack, meeting transcripts, project docs, customer calls); Competitive analysis, due diligence, trip planning, course notes, hobby deep-dives.

## Architecture

Three layers:
- Raw sources — curated, immutable source documents. The source of truth.
- The wiki — a directory of LLM-generated markdown. The LLM owns this layer entirely.
- The schema — CLAUDE.md (Claude Code) or AGENTS.md (Codex) telling the LLM the structure, conventions, and workflows. Co-evolved over time.

## Operations

- Ingest. Drop a source in; the LLM reads it, discusses key takeaways, writes a summary page, updates the index, updates relevant entity and concept pages, appends a log entry. A single source might touch 10-15 wiki pages. Karpathy prefers one-at-a-time, supervised; batch is possible.
- Query. Ask questions; the LLM finds relevant pages, reads them, synthesizes an answer with citations. Forms: markdown page, comparison table, Marp slides, matplotlib chart, canvas. Key insight: good answers can be filed back into the wiki as new pages — explorations compound.
- Lint. Periodically health-check: contradictions, stale claims, orphan pages, missing concept pages, missing cross-references, data gaps.

## Indexing and logging

- index.md — content-oriented catalog, one line per page, organized by category, updated every ingest. Read first on query. Works at moderate scale (~100 sources, ~hundreds of pages) without embedding-based RAG.
- log.md — chronological, append-only. Entry prefix like `## [2026-04-02] ingest | Article Title` makes it grep-parseable (`grep "^## \[" log.md | tail -5`).

## Optional: CLI tools

qmd (github.com/tobi/qmd) — local markdown search engine, hybrid BM25/vector search + LLM re-ranking, on-device, CLI + MCP server. Or vibe-code a naive search script.

## Tips and tricks

Obsidian Web Clipper (HTML→markdown); download images locally to raw/assets/ (bind "Download attachments for current file" to a hotkey); Obsidian graph view to see shape; Marp for slides; Dataview for frontmatter queries; the wiki is just a git repo of markdown — version history, branching, collaboration for free.

## Why this works

"The tedious part of maintaining a knowledge base is not the reading or the thinking — it's the bookkeeping... Humans abandon wikis because the maintenance burden grows faster than the value. LLMs don't get bored, don't forget to update a cross-reference, and can touch 15 files in one pass. The wiki stays maintained because the cost of maintenance is near zero." Related in spirit to Vannevar Bush's Memex (1945) — the unsolved part was who does the maintenance; the LLM handles that.

## Note

Intentionally abstract. Describes the idea, not an implementation. Everything is optional and modular. "The document's only job is to communicate the pattern. Your LLM can figure out the rest."

---

## Notable comment-thread implementations (primary observations from the gist thread, April–May 2026)

- ΩmegaWiki (skyllwt) — 740+ stars by May 21; v1.5.0; 26 Claude Code skills; reported as 8 typed entities / 20 typed edges (note: differs from the research report's "9×9" figure); bilingual EN/中文; full paper lifecycle discover→ingest→graph→ideate→experiment→draft→poster→rebuttal.
- sqz (ojuschugh1) — Rust context-compression tool; PreToolUse hook; 24.7% avg / up to 92% dedup token savings; ELv2 license.
- Synto (kytmanov) — v0.2.0; local-first, Ollama/LM Studio, PDF/MD/text ingest, no vector DB, Obsidian-friendly. Successor to obsidian-llm-wiki-local.
- Synthadoc (axoviq-ai / paulmchen) — v0.5.0 adds Adversarial Review (a second independent LLM interrogates each page) and Claim-Level Provenance (^[filename:L–L] citation markers, Source Viewer in Obsidian), plus routing + alias system and candidates staging.
- SciAI Wiki (gschleder / cnpem) — arXiv manuscript (May 18) applying LLM wiki ideas to science; persistent scientific memory with provenance.
- Link (gowtham0992) — v1.2.0; local source-backed memory; plain markdown; MCP tools; SQLite FTS; Homebrew + PyPI.
- llm-wiki-manager (sametbrr) — full Claude Code skill; 8 operating modes; 4 idempotent Python scripts; 8 templates; 9 reference docs.
- LLM-WIKI-MCP (Electro-resonance) — implements the pattern as an MCP server (not just a skill); CLI; local Ollama; file provenance via timestamps + hashes; can ingest its own docs.
- MindHub (pathakutsav) — hosted product (trymindhub.com) wrapping the knowledge-base experience for Anthropic/OpenAI/Gemini models.
- FrameCode VibeWork (Sistema2D) — documentation/governance framework to reduce context loss in AI-assisted dev.

## Commenter-observed open problem

dtmoura: "Preventing the wiki from going stale and ensuring the agents are proactive in adding and maintaining the wiki during the conversation, without a precise prompt, seems to be the problem. Just putting a 'remember to update...' in claude.md wont do it."
