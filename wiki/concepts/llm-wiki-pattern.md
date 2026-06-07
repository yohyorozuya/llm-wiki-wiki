---
type: concept
slug: llm-wiki-pattern
title: The LLM Wiki Pattern
created: 2026-05-28
updated: 2026-05-28
sources: [research-report, karpathy-gist]
confidence: 5
kind: principle
---

# The LLM Wiki Pattern

## Overview

A methodology [[andrej-karpathy|created_by=Karpathy]] published April 4, 2026 as an abstract "idea file" — a GitHub gist (`llm-wiki.md`, 5,000+ stars/forks) describing how to use an LLM to build and maintain a persistent, interlinked markdown knowledge base. Its central thesis: knowledge should be **compiled once and kept current**, not re-derived on every query the way [[rag]] does. See [[compilation-vs-retrieval]].

Karpathy's slogan: *"Obsidian is the IDE; the LLM is the programmer; the wiki is the codebase."*

It is a methodology, not a product. The gist is designed to be pasted into an agent like [[claude-code]] or Codex, which then instantiates a concrete version with the user.

## The three layers

1. **Raw sources** — immutable inputs. "Source of truth." See [[raw-layer]].
2. **The wiki** — LLM-generated markdown. "The LLM owns this layer entirely."
3. **The schema** — the [[claude-md-schema]] (CLAUDE.md / AGENTS.md) that turns a generic agent into a disciplined wiki maintainer.

## The three operations

- [[ingest]] — read a source, update ~10-15 pages.
- [[query]] — read index, drill in, answer with citations, file answers back.
- [[lint]] — periodic health-check for contradictions, orphans, stale claims.

Plus two special files: [[index-md]] (the catalog) and [[log-md]] (the append-only history).

## Why it works

"The tedious part of maintaining a knowledge base is not the reading or the thinking — it's the bookkeeping. Humans abandon wikis because the maintenance burden grows faster than the value. LLMs don't get bored." The pattern descends conceptually from [[memex]] (1945), whose unsolved problem was *who does the maintenance* — the LLM is the answer.

## Cross-references

- Contrasts with [[rag]] via [[compilation-vs-retrieval]] and [[llm-wiki-vs-rag]]
- Realized by everything under the implementations
- Hits the [[three-failure-modes]] at scale
- Composes with retrieval as [[hybrid-retrieval]]
- Its uptake is covered in [[adoption-and-reception]]
- An unsolved maintenance issue: [[staleness-problem]]
- A disposable variation: the [[ephemeral-wiki]]
- A naming critique: the [[category-error-critique]]
- A community successor spec: [[llm-wiki-v2]]

## Open questions

- Where's the scale ceiling for a pure (no-retrieval) wiki? The report suggests ~hundreds of pages.
- Does it eventually fold into model weights via fine-tuning, as Karpathy hints?
