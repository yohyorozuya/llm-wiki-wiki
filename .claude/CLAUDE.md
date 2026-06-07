# CLAUDE.md — LLM Wiki Knowledge Base

## Purpose

This vault has **two roles**:

1. **Reference** — it captures everything about **the LLM Wiki pattern** (Karpathy's April 2026 methodology). It is, deliberately, an LLM Wiki *about* LLM Wikis: a working demonstration of the pattern it documents. Success = anyone reading it comes away an LLM Wiki expert.
2. **Workshop** — it is the place where new, bespoke LLM wikis are **configured** for the user's projects and use cases. New vaults are built here via the wizard (see "The New-Vault Wizard" below), grounded in the reference's own hard-won lessons, then copied out elsewhere to actually be used.

The reference *informs* the workshop: every schema choice the wizard makes (entity types, typed edges, failure-mode guards, scale provisions) is justified by the pages in `wiki/`.

## Dual-mode operation

Default to **reference mode** — answer questions, maintain `wiki/`, ingest sources about the LLM Wiki pattern.

Switch to **workshop mode** when the user asks to build / configure / scaffold a new vault (triggers like "build me a vault for…", "let's configure a wiki for…", "new vault", "I have a project…"). In workshop mode, follow "The New-Vault Wizard" below. When unsure which mode applies, ask.

## Layers

- `raw/` — immutable sources: the research report, Karpathy's gist, implementation repos, critiques, tutorials. Never modify.
- `wiki/` — LLM-owned markdown pages (the reference). You own this layer.
- `vaults/` — the workshop output: a collection of bespoke, configured-but-empty LLM wikis the user builds here and copies out elsewhere. See "The New-Vault Wizard." Each subfolder is a complete, self-contained vault.
- `.claude/CLAUDE.md` — this rulebook.

## Entity types and buckets

- **source** → `wiki/sources/` — one summary page per ingested source (the report, each cited primary source).
- **concept** → `wiki/concepts/` — ideas, mechanisms, operations (ingest, query, lint, compilation, the three failure modes, hybrid retrieval, etc.).
- **entity** → `wiki/entities/` — people and orgs (Karpathy, Tobi Lütke, Vannevar Bush, Edra, etc.).
- **implementation** → `wiki/implementations/` — the ecosystem tools (nashsu/llm_wiki, Synthadoc, SwarmVault, Kompl, OmegaWiki, AKBP, expo-llm-wiki, qmd, etc.).
- **synthesis** → `wiki/synthesis/` — comparisons, framings, and answers filed back from queries.

## Page format

```yaml
---
type: source | concept | entity | implementation | synthesis
slug: kebab-case-slug
title: Human Readable Title
created: YYYY-MM-DD
updated: YYYY-MM-DD
sources: [source-slug-1, source-slug-2]
confidence: 1-5
---
```

Type-specific frontmatter:

- **implementation** — `creator: name/handle`, `license: MIT | AGPL-3.0 | …`, `stack: [lang, framework]`, `stars: approx`, `category: desktop-app | engine | skill-kit | protocol | library | retrieval`.
- **entity** — `role: who they are`, `affiliation: org`.
- **concept** — `kind: operation | architecture | failure-mode | principle | comparison`.

Body order (skip what doesn't apply):

```
Overview        — 1-2 paragraphs.
Sections        — type-appropriate detail.
Cross-references — bulleted [[wikilinks]] with a short "why".
Open questions  — unresolved threads.
```

## Linking rules

- Wrap entity/concept/implementation names in `[[wikilinks]]` on first mention per section.
- Cite every factual claim with a `[[source]]` wikilink or frontmatter `sources:` entry.
- Typed edges with `[[target|type=X]]`:
  - `implements` — implementation → the pattern/concept it realizes
  - `extends` — builds on another idea
  - `contradicts` / `critiques` — disagreement
  - `derived_from` — lineage (e.g. pattern derived_from Memex)
  - `addresses` — a solution addressing a failure mode
  - `created_by` — implementation/concept → person

## Ingest workflow

1. Read the source.
2. Write a source summary in `wiki/sources/<slug>.md` (frontmatter `raw_file:` → the file in `raw/`).
3. Identify touched pages via `wiki/index.md`; extend surgically.
4. Create new concept/entity/implementation pages, applying the Identity guard.
5. Update `wiki/index.md`.
6. Append to `wiki/log.md`: `## [YYYY-MM-DD] ingest | <title>` + 1-3 sentences.

## Query / Lint / Failure-mode guards

- **Query**: read index first, drill into 3-5 pages, answer with `[[wikilink]]` citations, offer to file substantive answers to `wiki/synthesis/`.
- **Lint**: orphans, contradictions, stale claims, missing concepts, unsourced claims, identity duplicates. Surface as findings; never auto-apply.
- **Identity**: search existing slugs before creating; extend near-matches.
- **Level**: keep granularity consistent — a concept page is one idea; an implementation page is one tool.
- **Relationship**: prefer typed edges.
- **Hallucination**: never assert a claim without a source. The report and its cited sources are the ground truth here.

---

# The New-Vault Wizard (workshop mode)

When the user wants a new LLM wiki, act as a wizard: hold a short, guided conversation, then scaffold a **bespoke, fully-configured but knowledge-empty** vault into `vaults/<slug>/`. The user will later copy that folder out to where the project lives and ingest real sources *there* — never here. This vault stays a clean workshop + registry.

## Cardinal rules

1. **Configure, don't fill.** Build the structure, the CLAUDE.md, the index/log seeds, the README. Do **not** ingest sources, do **not** write knowledge pages. Leave `raw/` and the wiki buckets empty (only seed files: index.md, log.md, and folder READMEs).
2. **Bespoke, not generic.** This is not a template stamp. Tailor entity types, edges, workflows, and scale provisions to the specific use case the user describes. Two research vaults for different topics should differ.
3. **Ground every choice in the reference.** Justify schema decisions by pointing to the relevant `wiki/` pages (e.g. "I'm giving you typed edges because of [[three-failure-modes]] → Relationship; I'm adding a routing note because of [[routing-layer]] and the scale thresholds in [[llm-wiki-vs-rag]]"). Read those pages if needed before deciding.
4. **One question at a time.** Don't fire a wall of questions. Converse.
5. **Register it.** After building, add the new vault to `vaults/registry.md`.

## Step 1 — Elicit (the shaping questions)

Ask these, adapting to what the user already told you (skip what's answered). One at a time:

1. **Purpose** — what is this wiki *for*? What's the domain/topic? (drives everything)
2. **Use-case shape** — which family does it resemble? (research / book companion / business-team / personal / project / competitive-analysis / other). Use this only to seed sensible defaults, then customize.
3. **Entity types** — propose a tailored set based on the purpose, and let the user adjust. Examples by family:
   - research → `paper`, `concept`, `method`, `researcher`, `idea`, `experiment`
   - book companion → `character`, `theme`, `chapter`, `place`, `event`, `term`
   - business/team → `project`, `decision`, `person`, `meeting`, `customer`, `process`
   - personal → `goal`, `habit`, `insight`, `person`, `event`, `resource`
   - project → `component`, `decision`, `task`, `person`, `dependency`, `concept`
   Always include `source` (every vault needs source summary pages).
4. **Audience / candor** — private-only, or will polished outputs be exported? (affects how candid wiki pages are, and whether to add an `outputs/` or exports area)
5. **Sources** — what will get ingested? (text/paste, PDFs/docs, conversations, web clips, transcripts) — affects ingest workflow notes.
6. **Scale expectation** — rough source count over time. Map to provisions using [[llm-wiki-vs-rag]] thresholds:
   - < ~100 sources → pure index-first navigation, no retrieval infra. Note it.
   - ~100–1000 → note that BM25 search ([[qmd]]) will help later.
   - 1000+ → note that vectors + a [[routing-layer]] will become necessary; consider [[candidates-staging]].
7. **Special needs** — any of: a [[purpose-layer|purpose.md]] (an evolving "why" file — good for research/personal), version snapshots (good when exporting deliverables), typed-edge emphasis, [[claim-level-provenance]]-style citation rigor (good for precision-critical domains).

Summarize the resulting design back to the user and confirm before scaffolding.

## Step 2 — Scaffold

Create under `vaults/<slug>/` (slug = kebab-case of the purpose):

```
vaults/<slug>/
├── .claude/CLAUDE.md     ← the bespoke rulebook (see Step 3)
├── README.md             ← what this vault is, how to use it, "copy me out" note
├── raw/                  ← empty except a README explaining what to drop here
│   └── README.md
└── wiki/
    ├── index.md          ← seeded catalog with the chosen buckets, all empty
    ├── log.md            ← seeded, with a single "[date] configured | <purpose>" line
    └── <one folder per entity type>/   ← empty (sources/, plus the chosen types)
```

Add optional pieces only if elicited: `purpose.md` (at vault root or wiki/), an `outputs/` or `resumes-archive`-style export folder, etc.

Keep all knowledge buckets empty. The log's only entry records that the vault was *configured* (not ingested).

## Step 3 — Write the bespoke CLAUDE.md

The generated vault's CLAUDE.md is the real deliverable. It must be self-contained (it will be copied away from here, so it cannot rely on this reference being present). Include:

- **Purpose** — the specific domain, in the user's words.
- **Layers** — raw / wiki / schema (+ purpose.md or outputs if added).
- **Entity types and buckets** — the tailored set, each with a one-line definition and its folder.
- **Page format** — frontmatter (type/slug/title/created/updated/sources/confidence) + type-specific fields appropriate to the domain; body order (Overview / sections / cross-references / open questions).
- **Linking rules** — wikilinks + a **typed-edge vocabulary chosen for this domain** (this is the cure for the Relationship failure mode; pick edges that matter here, e.g. research: `extends/contradicts/supports/tested_by/derived_from`; business: `depends_on/decided_by/supersedes/owned_by`).
- **Ingest / Query / Lint workflows** — the standard three, adapted (e.g. conversation-ingest if the user feeds chats; discuss-before-write if memory vs source may disagree).
- **Failure-mode guards** — Identity (search before creating), Level (granularity rule with domain examples), Relationship (use typed edges), Hallucination (cite or mark unsourced).
- **Scale note** — what to add and when, per the user's scale answer.
- **Git discipline** — commit after ingests/exports.

Bake in the lessons but do **not** include a "[CUSTOMIZE ME]" block — the customization happens here, now, through this conversation. The copied-out vault should be ready to ingest immediately.

## Step 4 — Register

Append a row to `vaults/registry.md`: date, slug, purpose, use-case family, entity types, scale tier, and any special features. This is both record-keeping and a menu for cloning similar vaults later ("build me one like `diffusion-research` but for a different topic" → read that vault's CLAUDE.md as the starting point and adapt).

## Cloning an existing vault

If the user says "make one like <existing vault>", read that vault's `.claude/CLAUDE.md` and README, propose it as the starting point, and run the wizard from there — changing only what the new purpose requires. Faster than starting cold, and a key reason the vaults live here together.
