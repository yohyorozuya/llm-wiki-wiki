---
type: implementation
slug: link-memory
title: Link (gowtham0992)
created: 2026-05-28
updated: 2026-05-28
sources: [karpathy-gist]
confidence: 3
creator: gowtham0992
license: (see repo)
stack: [Python, SQLite, MCP]
category: library
---

# Link (gowtham0992)

## Overview

Local, source-backed memory for LLM agents (v1.2.0, May 2026) built on the [[llm-wiki-pattern]]. Stores agent memory as plain Markdown; raw sources become a source-backed wiki; explicit "remember this" requests become reviewable agent memory. MCP tools let Codex, Claude, Cursor, Kiro, VS Code, and Copilot query that memory without dumping the whole wiki into context.

## What it adds

A clean split between ingested-source knowledge and explicitly-remembered agent memory; SQLite FTS search; bounded graph/query payloads for larger local wikis; Homebrew + PyPI distribution; a local /health page with repair commands for interrupted writes.

## Cross-references

- Implements [[llm-wiki-pattern]] (`implements`)
- Surfaced via [[comment-thread-implementations]]
- MCP-first, like [[qmd]] and [[llm-wiki-mcp]]

## Open questions

- None significant.
