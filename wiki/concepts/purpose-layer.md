---
type: concept
slug: purpose-layer
title: The Purpose Layer (purpose.md)
created: 2026-05-28
updated: 2026-05-28
sources: [nashsu-repo]
confidence: 3
kind: architecture
---

# The Purpose Layer (purpose.md)

## Overview

A proposed fourth layer for the [[llm-wiki-pattern]], introduced by [[nashsu-llm-wiki]]. The observation: Karpathy's original three layers cover *how* the wiki works (the [[claude-md-schema|schema]]), *what's in it* ([[index-md]]), and the *sources* ([[raw-layer]]) — but there's "no formal place for why the wiki exists." purpose.md fills that gap, defining goals, key questions, research scope, and an evolving thesis, and is read by the LLM during every [[ingest]] and [[query]] for context.

## Why it helps

It gives the agent a stable sense of intent, so synthesis and gap-detection are oriented toward the user's actual goal rather than just accumulating facts. It pairs naturally with scenario templates (Research, Reading, Personal Growth, Business, General).

## Cross-references

- Extends the [[claude-md-schema]] (adds "why" to its "how")
- Introduced by [[nashsu-llm-wiki]]
- Informs [[ingest]] and [[query]]

## Open questions

- Whether a separate file is better than a "purpose" section inside the schema — a convention question the ecosystem hasn't settled.
