# skyllwt/OmegaWiki — primary repo docs (README, CLAUDE.md, SourcePulse, gist comments)

Source: github.com/skyllwt/OmegaWiki (README, repo tree), SourcePulse, awesome-claude-code issue #1764, gist thread comments. Author: skyllwt (Weitong Qian). License: MIT. Python. ~418-768 stars depending on listing/date. Fetched late May 2026.

## What it is

"Karpathy's LLM-Wiki vision, fully realized — wiki-centric full-lifecycle AI research platform powered by Claude Code." Not just a wiki builder: "a complete research lifecycle platform: from paper ingestion → knowledge graph → gap detection → idea generation → experiment design → paper writing → peer review response. All driven by [23] Claude Code skills, all centered on one wiki as the single source of truth."

## Architecture (from repo tree)

```
OmegaWiki/
  CLAUDE.md                 # Runtime schema & rules
  wiki/
    papers/                 # structured paper summaries
    concepts/               # cross-paper technical concepts
    topics/                 # research direction maps
    people/                 # researcher profiles
    ideas/                  # research ideas (with lifecycle)
    experiments/            # experiment records
    methods/                # reusable cross-paper method entities
    claims/                 # citable claims (claim layer)
    Summary/                # domain-wide surveys
    foundations/            # background knowledge (terminal pages)
    outputs/                # generated artifacts
    graph/                  # auto-generated: edges, context, gaps
    index.md
    log.md
  raw/
    papers/ discovered/ tmp/ notes/ web/
  tools/                    # deterministic Python
```

## Typed graph — figures evolved across versions (IMPORTANT for reconciliation)

- April 13, 2026 gist comment (early): "structured knowledge base with 8 entity types" + "9 relationship types connecting everything (supports, contradicts, tested_by...)" + "20 Claude Code skills."
- May 18-21 gist comments: "8 typed entities · 20 typed edges," 26 Claude Code skills, v1.4.0→v1.5.0, 680→740+ stars.
- Current README / SourcePulse (late May): "9 entity types (e.g., Paper, Concept, Idea, Experiment) and 9 relationship types (e.g., supports, contradicts, inspired_by)"; "23 Claude Code skills."
- awesome-claude-code issue: "25 skills (.claude/skills/)."

So the entity/edge/skill counts are a MOVING TARGET that changed across releases. There is no single correct "N×M"; the figure depends on the version. The research report's "9×9" matches the current README; the "8×20" matches a mid-May snapshot.

## Key design idea

"The wiki isn't a side product — it's the state machine. Every skill reads from it, writes back to it, and the knowledge compounds over time. Failed experiments stay as anti-repetition memory so you never re-explore dead ends." Supports cross-model adversarial review using any OpenAI-compatible API. Bilingual EN/中文.

## Install

git clone; npm install -g @anthropic-ai/claude-code; claude login; ./setup.sh (or setup.ps1). Python 3.9-3.10+, Node 18+. Place papers in raw/papers/, run claude then /init <topic>. Optional keys: Semantic Scholar, OpenAI-compatible LLMs.
