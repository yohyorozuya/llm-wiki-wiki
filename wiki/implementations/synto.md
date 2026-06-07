---
type: implementation
slug: synto
title: Synto (kytmanov)
created: 2026-05-28
updated: 2026-05-28
sources: [karpathy-gist]
confidence: 3
creator: kytmanov
license: (see repo)
stack: [local LLM, Ollama, LM Studio]
category: engine
---

# Synto (kytmanov)

## Overview

A local-first implementation of the [[llm-wiki-pattern]] (v0.2.0 as of May 2026), successor to the same author's earlier obsidian-llm-wiki-local. Runs the full ingest → compile → query → synthesize pipeline on local models via Ollama or LM Studio, with no vector DB and no cloud required. `synto add` imports PDFs, Markdown, and text, converting them to clean Obsidian-compatible markdown.

## What it adds

Strong local-first/private posture; PDF import; duplicate detection (an Identity-mode mitigation, see [[three-failure-modes]]); source-type prompts; semantic cache; lineage tracking.

## Cross-references

- Implements [[llm-wiki-pattern]] (`implements`)
- Surfaced via [[karpathy-gist]]'s comment thread, see [[comment-thread-implementations]]
- Duplicate detection addresses Identity in [[three-failure-modes]]

## Open questions

- Maturity is early (v0.2.0).
