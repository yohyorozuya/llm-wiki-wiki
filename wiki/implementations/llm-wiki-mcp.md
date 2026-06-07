---
type: implementation
slug: llm-wiki-mcp
title: LLM-WIKI-MCP (Electro-resonance)
created: 2026-05-28
updated: 2026-05-28
sources: [karpathy-gist]
confidence: 3
creator: Electro-resonance
license: (see repo)
stack: [MCP, Ollama, CLI]
category: protocol
---

# LLM-WIKI-MCP (Electro-resonance)

## Overview

An implementation of the [[llm-wiki-pattern]] as an MCP server (rather than only an agent skill or Obsidian workflow), with a CLI for direct interaction. Connects to a configurable local Ollama instance or cloud models, ingests one or more directories, and lets you chat with your files immediately. The author came to it after ~2 years building custom RAG layers, explicitly to try the persistent-compounding-artifact idea.

## What it adds

MCP-server-first design; local Ollama / OpenAI-compatible models; file provenance via timestamps and hashes; incremental re-ingest that skips unchanged files; single-file and directory ingest; and a recursive trick — the system can `/ingest .` to ingest its own documentation and answer questions about itself. The author's framing: "RAG retrieves information, but an LLM-maintained wiki accumulates understanding."

## Cross-references

- Implements [[llm-wiki-pattern]] (`implements`)
- MCP-native like [[qmd]], [[link-memory]]
- Surfaced via [[comment-thread-implementations]]

## Open questions

- None significant.
