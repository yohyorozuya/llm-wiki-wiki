---
type: implementation
slug: agentmemory
title: agentmemory (rohitg00)
created: 2026-05-28
updated: 2026-05-28
sources: [akbp-v2-agentmemory]
confidence: 3
creator: rohitg00 (Rohit Ghumare)
license: (see repo)
stack: [Node, MCP]
stars: ~10000
category: library
---

# agentmemory (rohitg00)

## Overview

A persistent-memory engine for AI coding agents (~10K stars) — "#1 Persistent memory for AI coding agents based on real-world benchmarks." Not a wiki per se, but the production system whose lessons were distilled into [[llm-wiki-v2]] and the [[akbp]] protocol. It applies the [[llm-wiki-pattern]]'s compile-don't-re-derive insight to the narrower problem of agent session memory.

## Agent-integration surface

A memory server on :3111; one-command wiring (`agentmemory connect claude-code`, also codex/cursor/gemini-cli). Ships an MCP server proxying 53 tools (falling back to 7 locally when no server is reachable), 6 lifecycle hooks (SessionStart, UserPromptSubmit, PreToolUse, PostToolUse, PreCompact, Stop), and 8 skills (/recall, /remember, /session-history, /forget, /recap, /handoff, /commit-context, /commit-history).

## Cross-references

- Applies [[llm-wiki-pattern]] to agent memory (`implements`)
- Its production lessons produced [[llm-wiki-v2]] and [[akbp]]
- MCP-first like [[qmd]], [[swarmvault]], [[link-memory]]

## Open questions

- The line between "agent memory" and "LLM wiki" blurs here — arguably a different-but-adjacent category.
