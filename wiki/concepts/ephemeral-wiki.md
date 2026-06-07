---
type: concept
slug: ephemeral-wiki
title: The Ephemeral Wiki
created: 2026-05-28
updated: 2026-05-28
sources: [press-coverage]
confidence: 3
kind: principle
---

# The Ephemeral Wiki

## Overview

A variation on the [[llm-wiki-pattern]] described by Lex Fridman (reported in VentureBeat, [[press-coverage]]): rather than only maintaining one durable wiki, you have the system **generate a temporary, focused mini-knowledge-base for a single task**, then discard it. Fridman's example: spinning up a focused mini-wiki to load into an LLM for voice-mode interaction on a 7-10 mile run. He also has the system generate dynamic HTML/JS so he can sort, filter, and tinker with visualizations interactively.

## Why it's interesting

It inverts the usual durability assumption. The main [[llm-wiki-pattern]] bets on *compounding* a permanent artifact; the ephemeral wiki treats compilation as cheap enough to do disposably, per-task. VentureBeat framed this as a future where users "spawn a team of agents to build a custom research environment for a specific task, which then dissolves."

## Cross-references

- A variation on [[llm-wiki-pattern]]
- Reported in [[press-coverage]]
- Contrasts with the compounding-artifact premise of [[compilation-vs-retrieval]]

## Open questions

- If compilation is cheap enough to throw away, when is a durable wiki still worth maintaining?
