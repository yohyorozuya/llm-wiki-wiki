---
type: concept
slug: tiered-memory
title: Tiered Memory Architecture
created: 2026-05-28
updated: 2026-05-28
sources: [research-report]
confidence: 4
kind: architecture
---

# Tiered Memory Architecture

## Overview

An advanced variation that mimics human expertise with three tiers: **Facts** (immutable specs, confidence weight 1.5 — "Facts always win"), **Working Memory** (active WIP, recency-weighted), and **Wisdom** (synthesized cache; frequently-referenced lessons "graduate" into Core Wisdom). Pioneered by [[expo-llm-wiki]]; echoed in [[nashsu-llm-wiki]].

## Cross-references

- Variation on [[llm-wiki-pattern]]
- Implemented by [[expo-llm-wiki]]

## Open questions

- How "graduation" thresholds are tuned in practice.
