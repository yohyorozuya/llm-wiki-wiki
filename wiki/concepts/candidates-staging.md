---
type: concept
slug: candidates-staging
title: Candidates Staging
created: 2026-05-28
updated: 2026-05-28
sources: [research-report]
confidence: 4
kind: architecture
---

# Candidates Staging

## Overview

A quality gate addressing the Identity failure mode (see [[three-failure-modes]]). New or low-confidence pages land in a `wiki/candidates/` area under an off/threshold/all policy and are excluded from BM25, orphan detection, and contradiction checks until promoted. Promotion is atomic. Implemented in [[synthadoc]] and [[swarmvault]].

## Cross-references

- Addresses Identity in [[three-failure-modes]]
- Implemented by [[synthadoc]] and [[swarmvault]]
- Complements [[lint]]

## Open questions

- Who decides promotion — automated confidence threshold vs human review.
