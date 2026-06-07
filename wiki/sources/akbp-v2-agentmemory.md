---
type: source
slug: akbp-v2-agentmemory
title: AKBP, LLM Wiki v2, and agentmemory (rohitg00)
created: 2026-05-28
updated: 2026-05-28
sources: [akbp-v2-agentmemory]
confidence: 4
raw_file: akbp-v2-agentmemory.md
---

# AKBP, LLM Wiki v2, and agentmemory (rohitg00)

## Overview

A connected cluster of primary sources from Rohit Ghumare: the **LLM Wiki v2** gist (a fork of Karpathy's, May 23 2026), the **AKBP** protocol repo, and **agentmemory** (the ~10K-star production memory engine whose lessons informed v2). Ingesting this both enriches [[akbp]] and introduces two genuinely new entities: the [[llm-wiki-v2]] spec and the [[agentmemory]] implementation.

## What it adds

LLM Wiki v2's explicit "what breaks at scale" framing ("what separates a wiki that stays useful from one that rots"), AKBP's protocol flow (evidence → proposed claims → reviewed writes → file storage → rebuilt indexes → cited next session), and agentmemory's concrete agent-integration surface (MCP server, 53 tools, 6 lifecycle hooks, 8 skills).

## Cross-references

- Primary source for [[akbp]], [[llm-wiki-v2]], [[agentmemory]]
- v2 `extends` the [[karpathy-gist|original gist]]
- AKBP's review-gated writes answer the [[transactional-overhead-critique]]

## Open questions

- AKBP is explicitly alpha; adoption beyond the reference implementation is unproven.
