---
type: implementation
slug: omegawiki
title: OmegaWiki (skyllwt)
created: 2026-05-28
updated: 2026-05-28
sources: [research-report, karpathy-gist, omegawiki-repo]
confidence: 5
creator: skyllwt (Weitong Qian)
license: MIT
stack: [Python, Claude Code]
stars: ~418-768 (varies by listing, May 2026)
category: skill-kit
---

# OmegaWiki (skyllwt)

## Overview

"Karpathy's LLM-Wiki vision, fully realized" [[omegawiki-repo]] — a [[claude-code|Claude Code]]-powered, wiki-centric full-lifecycle AI research platform. Not just a wiki builder: a complete research pipeline (paper ingestion → knowledge graph → gap detection → idea generation → experiment design → paper writing → peer-review response), all centered on "one wiki as the single source of truth." Bilingual EN/中文; MIT.

## The defining idea

"The wiki isn't a side product — it's the state machine. Every skill reads from it, writes back to it, and the knowledge compounds over time. Failed experiments stay as anti-repetition memory so you never re-explore dead ends." It also runs cross-model [[adversarial-review]] via any OpenAI-compatible API, and maintains a `claims/` layer of citable claims (kin to [[claim-level-provenance]]).

## Typed graph — a dated, moving figure

OmegaWiki has the ecosystem's most elaborate [[typed-knowledge-graph]], but its exact size **changed across releases**, which earlier produced an apparent contradiction in this wiki (now resolved via [[omegawiki-repo]]):

- April 13, 2026 — 8 entity types / 9 relationship types / 20 skills
- mid-May 2026 — 8 entities / 20 edges / 26 skills (per author's gist comments)
- current README (late May) — 9 entity types / 9 relationship types / 23 skills

The [[research-report]]'s "9×9" matches the current README; the "8×20" matched a mid-May snapshot. There is no single canonical figure — any number here must be dated. A neat illustration of the [[lossy-summarization-critique]] in miniature.

## Cross-references

- Implements [[llm-wiki-pattern]] (`implements`)
- The canonical [[typed-knowledge-graph]]
- Runs on [[claude-code]]
- Its claims layer relates to [[claim-level-provenance]]; cross-model review is [[adversarial-review]]
- Primary detail and figure reconciliation from [[omegawiki-repo]]

## Open questions

- Counts keep moving with releases; treat every figure as a dated snapshot.
