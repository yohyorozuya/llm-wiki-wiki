---
type: concept
slug: adversarial-review
title: Adversarial Review
created: 2026-05-28
updated: 2026-05-28
sources: [synthadoc-docs]
confidence: 4
kind: principle
---

# Adversarial Review

## Overview

A technique introduced by [[synthadoc]] (v0.5.0) that directly attacks the [[lossy-summarization-critique]]: after a page is compiled, **a second, independent LLM interrogates it** for overreach, unsupported generalizations, and contradictions. The reviewing model is deliberately a different provider or model family (configured by the user) so its failure modes don't correlate with the writer's. Warnings surface in a lint tab, in page frontmatter, and in the audit trail.

## Why it matters

The biggest risk of the [[llm-wiki-pattern]] is that a mis-synthesis gets written once and silently propagates. Adversarial review is a structural check against that — a second opinion baked into the compile step rather than relying on the user to catch errors during [[lint]].

## Cross-references

- Mitigates the [[lossy-summarization-critique]]
- Introduced by [[synthadoc]]
- Complements [[lint]] and [[claim-level-provenance]]

## Open questions

- Cost: it roughly doubles the per-page LLM spend at ingest.
