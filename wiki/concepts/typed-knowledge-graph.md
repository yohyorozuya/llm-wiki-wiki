---
type: concept
slug: typed-knowledge-graph
title: Typed Knowledge Graph
created: 2026-05-28
updated: 2026-05-28
sources: [research-report]
confidence: 4
kind: architecture
---

# Typed Knowledge Graph

## Overview

The leading structural answer to the Relationship failure mode (see [[three-failure-modes]]). Instead of generic "related" links, pages connect via typed entities and typed edges. [[omegawiki]]'s canonical scheme: 9 entity types × 9 edge types (extends, contradicts, supports, inspired_by, tested_by, invalidates, supersedes, addresses_gap, derived_from).

## Cross-references

- Addresses the Relationship problem in [[three-failure-modes]]
- Fullest implementation in [[omegawiki]]
- Also in [[swarmvault]] (provenance edges) and [[kompl]] (entity resolution)

## Open questions

- The tradeoff between expressive typed schemas and the friction they add to ingest.
