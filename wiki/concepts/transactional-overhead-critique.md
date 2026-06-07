---
type: concept
slug: transactional-overhead-critique
title: The Transactional-Overhead Critique
created: 2026-05-28
updated: 2026-05-28
sources: [research-report]
confidence: 4
kind: failure-mode
---

# The Transactional-Overhead Critique

## Overview

The sharpest structural critique of the [[llm-wiki-pattern]], from jazzonenl (May 2026). At scale, writes cascade — one change ripples across dozens of links — and LLMs lack referential integrity, so deleting or renaming a page leaves dead links. Keeping the wiki consistent "transforms a simple folder of files into a heavy, ongoing ETL process." Conclusion: "We are on the threshold of a new class of software: AI-Native Databases."

## The community response

[[swarmvault]], [[synthadoc]], [[akbp]], and [[expo-llm-wiki]] all add SQLite or graph substrates underneath the markdown to provide the integrity layer the critique demands.

## Cross-references

- Critiques [[llm-wiki-pattern]] (`critiques`)
- Related precision concern: [[lossy-summarization-critique]]
- Answered structurally by [[hybrid-retrieval]] and SQLite-backed implementations

## Open questions

- Is markdown-as-primary fundamentally wrong for multi-agent/team systems, or just for the largest ones?
