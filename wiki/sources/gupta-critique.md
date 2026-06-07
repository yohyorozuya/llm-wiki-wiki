---
type: source
slug: gupta-critique
title: Mehul Gupta — LLM Wiki critique & explainer series
created: 2026-05-28
updated: 2026-05-28
sources: [gupta-critique]
confidence: 4
raw_file: gupta-critique.md
---

# Mehul Gupta — LLM Wiki critique & explainer series

## Overview

A series of April 2026 Medium posts (Data Science in Your Pocket) by Mehul Gupta — the most-cited skeptical voice on the [[llm-wiki-pattern]]. The headline piece, "Andrej Karpathy's LLM Wiki is a Bad Idea," is the primary source behind the [[lossy-summarization-critique]]. Ingesting it directly sharpens that page with the exact argument.

## The core argument (primary)

"With RAG, the model goes back to the original documents each time. Even if it makes a mistake once, the next query has a chance to correct it because the source is still the same. LLM-Wiki changes that completely" — an error written into a wiki page persists and gets reused. Also: the DIY assembly is "exactly the 'hacky collection of scripts' [Karpathy] wanted to move beyond."

## The tension this creates in the wiki

Gupta's self-correction argument is the strongest form of the [[lossy-summarization-critique]]. Notably, [[synthadoc]]'s [[claim-level-provenance]] and [[adversarial-review]] are precise counters that postdate the critique — the ecosystem responding to exactly this objection.

## Cross-references

- Primary source for the [[lossy-summarization-critique]]
- In tension with [[claim-level-provenance]] and [[adversarial-review]]
- Also explains the pattern plainly (the compiler analogy behind [[compilation-vs-retrieval]])

## Open questions

- Gupta concedes the idea is "powerful"; the critique is about reliability at scale, not the concept itself.
