---
type: concept
slug: staleness-problem
title: The Staleness / Proactivity Problem
created: 2026-05-28
updated: 2026-05-28
sources: [karpathy-gist]
confidence: 3
kind: failure-mode
---

# The Staleness / Proactivity Problem

## Overview

An open problem raised directly in the [[karpathy-gist|gist]] thread (commenter dtmoura): keeping the wiki from going stale, and getting the agent to *proactively* maintain it during a conversation, is hard. "Just putting a 'remember to update...' in claude.md wont do it." The schema can describe the [[ingest]] and [[lint]] workflows, but reliably triggering them without explicit user prompting is unsolved.

## Relationship to other failure modes

Distinct from the [[three-failure-modes]] (which are about *structure* — Identity, Level, Relationship) and from the [[lossy-summarization-critique]] (about *accuracy*). This is about *agency*: who notices the wiki needs updating, and when. The Dream-cycle idea from [[nohmitaina]] is one structural answer — make maintenance a scheduled background pass rather than something the agent must remember mid-conversation.

## Cross-references

- An open problem for [[llm-wiki-pattern]]
- Partially answered by the Dream cycle in [[nohmitaina]] and [[lint]]
- Surfaced in [[comment-thread-implementations]]'s thread

## Open questions

- Can proactive maintenance be made reliable without becoming annoying or token-expensive?
