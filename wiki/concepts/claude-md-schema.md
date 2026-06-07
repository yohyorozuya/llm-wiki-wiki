---
type: concept
slug: claude-md-schema
title: The Schema (CLAUDE.md / AGENTS.md)
created: 2026-05-28
updated: 2026-05-28
sources: [research-report, karpathy-gist]
confidence: 5
kind: architecture
---

# The Schema (CLAUDE.md / AGENTS.md)

## Overview

The third layer of the [[llm-wiki-pattern]] and "the key configuration file." It is what turns a generic agent into "a disciplined wiki maintainer rather than a generic chatbot." [[claude-code|Claude Code]] reads CLAUDE.md; Codex reads AGENTS.md; the content describes the same pattern. Co-evolved with the agent over time as the user learns what works for their domain.

## What it isn't

It is the rulebook, not the catalog — it defines *how the agent operates*, and changes rarely. The thing that changes every ingest is [[index-md]]. The schema does not link to pages; it just defines rules.

## Cross-references

- Layer 3 of [[llm-wiki-pattern]]
- Read by [[claude-code]]
- Distinct from [[index-md]]
- Extended by the [[purpose-layer]] (adds "why" to the schema's "how")

## Open questions

- The right size: the report suggests ~1 page, dense, no fluff.
