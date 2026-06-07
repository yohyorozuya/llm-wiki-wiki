---
type: synthesis
slug: this-wiki-is-recursive
title: This Wiki Is a Demonstration of Itself
created: 2026-05-28
updated: 2026-05-28
sources: [research-report, karpathy-gist, omegawiki-repo, gupta-critique, edra-coverage]
confidence: 5
---

# This Wiki Is a Demonstration of Itself

## Overview

This knowledge base is an [[llm-wiki-pattern|LLM Wiki]] *about* the LLM Wiki pattern — built by following the very methodology it documents. It's worth making the recursion explicit because the structure itself teaches the pattern.

## How this wiki embodies the pattern

- **Raw layer**: the [[research-report]] sits immutable in `raw/`. It was never edited during ingestion — only read.
- **The wiki**: every page here was written by an agent performing [[ingest]] on that report, extracting concepts, entities, and implementations into one-idea-per-page markdown.
- **The schema**: a CLAUDE.md defined the entity types (source / concept / entity / implementation / synthesis), the page format, and the linking rules — including the typed edges (`implements`, `created_by`, `critiques`, `derived_from`) you see throughout.
- **The operations**: this base was produced by [[ingest]]; it answers questions via [[query]] (read [[index-md]], drill in); and it can be [[lint]]-ed for orphans and contradictions.

## What a reader should notice

The cross-reference density is the point. The [[three-failure-modes]] page links to the implementations that solve each mode ([[kompl]] for Identity, [[omegawiki]] for Relationship, [[synthadoc]] for scaling). The [[compilation-vs-retrieval]] principle links forward to [[hybrid-retrieval]], which links to the tools that realize it. No single page holds the whole picture — the understanding lives in the relationships between pages. That emergent, navigable structure is exactly what the pattern promises.

## Cross-references

- Demonstrates [[llm-wiki-pattern]]
- Built from [[research-report]]
- Best entry point after [[index-md]]

## The compounding test, run for real

The open question this page originally posed — *what happens when a second source is ingested?* — has now been answered. [[karpathy-gist|Karpathy's actual gist]] was ingested as the second source. It touched ~15 existing pages (adding itself as a corroborating citation), **corrected a contradiction** (it revealed [[omegawiki]] uses 8 entities / 20 edges, not the report's "9×9"), updated the adoption numbers by an order of magnitude (see [[adoption-and-reception]]), and **surfaced eight new implementations** the report had missed ([[comment-thread-implementations]]). That is the pattern working exactly as advertised: the second source didn't just pile on — it enriched, corrected, and compounded.

## What happened across twelve sources

The wiki grew from a 36-page, single-source seed into a 60+ page base built on **twelve real primary sources** — Karpathy's gist, the Synthadoc / nashsu / SwarmVault / Kompl / OmegaWiki / qmd repos, the AKBP / v2 / agentmemory cluster, the Gupta critiques, the press coverage, and the Edra funding reports. Along the way the compounding did real work:

- **Corrected the secondary record from primary sources.** The [[research-report]]'s "9×9" figure for [[omegawiki]] turned out to be a moving target across releases ([[omegawiki-repo]]); its "5,000+ stars" was an order of magnitude low ([[adoption-and-reception]]); and its "enterprise version of the LLM Wiki" framing for [[edra]] was an analogy, not a lineage ([[edra-coverage]]).
- **Surfaced live tensions instead of flattening them.** The [[lossy-summarization-critique]] (Gupta) and its answers ([[adversarial-review]], [[claim-level-provenance]]) sit on linked pages, dated, so the debate is navigable rather than averaged away.
- **Declined to ingest a falsehood.** A low-quality post conflating the pattern with Karpathy's unrelated llm.c project was flagged on [[press-coverage]], not propagated.

## Open questions

- The next sources (more critiques, the remaining implementation repos) would keep testing whether the wiki surfaces contradictions cleanly. So far, it has.
