---
type: source
slug: karpathy-gist
title: llm-wiki.md (Karpathy's original gist)
created: 2026-05-28
updated: 2026-05-28
sources: [karpathy-gist]
confidence: 5
raw_file: karpathy-gist.md
---

# llm-wiki.md (Karpathy's original gist)

## Overview

The foundational primary source for the entire [[llm-wiki-pattern]] — [[andrej-karpathy|Karpathy]]'s "idea file," created April 4, 2026. Where [[research-report|the research report]] was a synthesized secondary summary, this is the verbatim text: the core idea, the three-layer architecture, the three operations, indexing/logging, optional tooling, tips, and the "why this works" rationale. Ingesting it directly corroborates the report and corrects a few details.

## What the primary text confirms

The full quotes now trace to source: "the wiki is a persistent, compounding artifact"; "Obsidian is the IDE; the LLM is the programmer; the wiki is the codebase"; the [[memex|Memex]] lineage ("The part he couldn't solve was who does the maintenance. The LLM handles that"); and the closing note that the document "is intentionally abstract... The document's only job is to communicate the pattern."

## What it corrects or adds vs. the report

- **Scale of adoption** is far larger than the report's "5,000+": the gist's own page caps the display at 5,000+, but late-May search metadata shows roughly 33,940 stars / 7,226 forks / 845 comments. See [[adoption-and-reception]].
- **[[omegawiki|ΩmegaWiki]]'s typed graph** was reported in-thread as 8 entities / 20 edges (mid-May), differing from the report's "9×9". This was later *resolved* by ingesting [[omegawiki-repo]]: the figures changed across releases, so both are right at different dates.
- The live comment thread surfaced **many implementations the report omitted** — see [[comment-thread-implementations]].

## Cross-references

- The primary text behind [[llm-wiki-pattern]]
- Authored by [[andrej-karpathy]]
- Recommends [[qmd]]
- `contradicts` the report's figure on [[omegawiki]]

## Open questions

- The thread keeps growing; this snapshot is late May 2026.
