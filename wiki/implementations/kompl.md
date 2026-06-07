---
type: implementation
slug: kompl
title: Kompl (tuirk)
created: 2026-05-28
updated: 2026-05-28
sources: [research-report, kompl-repo]
confidence: 4
creator: tuirk
license: Apache-2.0
stack: [Next.js, Python NLP, n8n, SQLite, Docker]
category: engine
---

# Kompl (tuirk)

## Overview

A Dockerized engine for the [[llm-wiki-pattern]] with bring-your-own Gemini/DeepSeek keys, distinguished by doing NLP work *before* the LLM. Built with Next.js + Python NLP + n8n orchestration + SQLite [[kompl-repo]]; uses Firecrawl for scraping and downloads a local AI model from HuggingFace on first run. Its framing — "one new source can update 10+ wiki pages" — echoes Karpathy's [[ingest]] claim almost verbatim.

## What it adds

NLP-before-LLM (spaCy NER + 4-way keyphrase fanout: RAKE/KeyBERT/TextRank/YAKE); three layers of entity resolution (fuzzy → embedding → LLM disambiguation, collapsing "GPT 4"/"GPT-4"/"gpt4"); comparison pages auto-generated when ≥3 sources disagree; wikilinks injected deterministically by regex rather than by the LLM; an stdio MCP server; Obsidian-compatible export.

## Cross-references

- Implements [[llm-wiki-pattern]] (`implements`)
- Its entity resolution directly attacks the Identity problem in [[three-failure-modes]]
- Primary detail from [[kompl-repo]]

## Open questions

- None significant.
