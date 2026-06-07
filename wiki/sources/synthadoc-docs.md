---
type: source
slug: synthadoc-docs
title: Synthadoc primary docs (README, design.md, releases)
created: 2026-05-28
updated: 2026-05-28
sources: [synthadoc-docs]
confidence: 4
raw_file: synthadoc-docs.md
---

# Synthadoc primary docs (README, design.md, releases)

## Overview

Primary documentation for [[synthadoc]] fetched directly from its GitHub repo and the author's DEV Community posts — the README, `docs/design.md`, the quick-start guide, and release notes through v0.5.0. Ingesting it substantially deepened the [[synthadoc]] page beyond what the [[research-report]] captured, and corroborated several core concepts with primary wording.

## What it adds

The real architecture (parallel IngestAgent/QueryAgent/LintAgent sub-agents under an orchestrator), the actual on-disk layout (the `.synthadoc/` directory with audit.db, jobs.db, cache.db, embeddings.db), the page frontmatter format (status: active|contradicted|archived; confidence; per-source sha256 hashes), the AGPL-3.0 license, the eight providers, and the v0.5.0 features (Adversarial Review, Claim-Level Provenance).

## Corroborations

Synthadoc's own framing of [[compilation-vs-retrieval]] is almost verbatim the report's: "it compiles knowledge at ingest time... The wiki is the artifact." And on contradictions: "Contradictions are caught, not blended... RAG silently averages both claims" — a sharper statement of the [[lossy-summarization-critique]]'s mitigation.

## Cross-references

- Deepens [[synthadoc]]
- Corroborates [[compilation-vs-retrieval]] and [[hybrid-retrieval]]
- Introduces [[adversarial-review]] and [[claim-level-provenance]]

## Open questions

- Versions move fast; v0.5.0 is the latest observed.
