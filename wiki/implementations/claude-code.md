---
type: implementation
slug: claude-code
title: Claude Code (the agent harness)
created: 2026-05-28
updated: 2026-05-28
sources: [research-report]
confidence: 5
creator: Anthropic
license: proprietary
category: skill-kit
---

# Claude Code (the agent harness)

## Overview

The most common agent harness for operating an [[llm-wiki-pattern|LLM Wiki]]. A generic coding agent that reads [[claude-md-schema|CLAUDE.md]] on startup and follows it as standing instructions. This is the mechanism by which a generic agent becomes a disciplined wiki maintainer — no special wiki software required. Codex (reading AGENTS.md) plays the same role.

## Cross-references

- Operates the [[llm-wiki-pattern]]
- Reads the [[claude-md-schema]]
- Hosts skill kits like [[omegawiki]]

## Open questions

- Where exactly each tool reads its schema from (root vs .claude/) varies by client.
