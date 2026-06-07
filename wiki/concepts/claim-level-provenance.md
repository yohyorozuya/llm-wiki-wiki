---
type: concept
slug: claim-level-provenance
title: Claim-Level Provenance
created: 2026-05-28
updated: 2026-05-28
sources: [synthadoc-docs]
confidence: 4
kind: principle
---

# Claim-Level Provenance

## Overview

A technique from [[synthadoc]] (v0.5.0): during [[ingest]], **every compiled paragraph receives a `^[filename:L–L]` citation marker** tracing it back to the exact source lines. In Obsidian the markers render as chips; one click opens a Source Viewer (with PDF page resolution). Full provenance is queryable via CLI and HTTP API.

## Why it matters

This is the most direct answer the ecosystem has produced to the report's central worry about the [[llm-wiki-pattern]]: that you end up "one or two steps removed from the source" (the [[lossy-summarization-critique]]). With claim-level provenance, every sentence is one click from the raw lines it came from — recovering the source-traceability that [[rag]] keeps and the naive wiki loses.

## Cross-references

- Directly mitigates the [[lossy-summarization-critique]]
- Restores the traceability advantage [[rag]] has over a naive wiki
- Introduced by [[synthadoc]]; pairs with [[adversarial-review]]
- A richer form of the [[raw-layer]]'s immutability guarantee

## Open questions

- Line-level markers are brittle if the raw source is later re-formatted.
