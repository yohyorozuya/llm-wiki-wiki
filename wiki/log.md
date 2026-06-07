# Wiki Log

*Append-only chronological record. Grep `^## \[` to get the timeline.*

## [2026-05-28] ingest | LLM Wiki Expert Briefing (research report)

Seeded the wiki from the research report. Created the source page [[research-report]] and 35 wiki pages: 20 concepts (the pattern, three operations, the architecture files, RAG comparison, two critiques, and the advanced variations), 3 entities ([[andrej-karpathy]], [[tobi-lutke]], [[edra]]), 10 implementations ([[nashsu-llm-wiki]], [[synthadoc]], [[swarmvault]], [[kompl]], [[omegawiki]], [[akbp]], [[expo-llm-wiki]], [[qmd]], [[kb-cli]], [[claude-code]]), and 1 synthesis page ([[this-wiki-is-recursive]]). Typed edges used throughout: implements, created_by, critiques, derived_from, addresses. This is an LLM Wiki about the LLM Wiki pattern — built by the pattern it documents.

## [2026-05-28] lint | post-ingest link check

Ran a link-integrity pass. Found 4 broken references: `[[implementations]]` and `[[synthesis]]` (bucket names, not pages — converted to plain text), `[[wikilink]]` (generic term — converted to code span), and `[[nohmitaina]]` (a real implementation referenced but not yet created). Created the [[nohmitaina]] page (source of the three failure modes and the Dream cycle) and added it to the index. All 36 pages now resolve; zero broken links.

## [2026-05-28] ingest | llm-wiki.md (Karpathy's original gist)

Ingested the foundational primary source ([[karpathy-gist]]) — the actual gist text fetched from the web. This is the compounding test for the meta-wiki, and it worked: the source touched ~15 existing pages (added as a corroborating citation across the core concepts and [[andrej-karpathy]]/[[qmd]]/[[tobi-lutke]]); corrected a contradiction (the gist thread shows [[omegawiki]] is 8 entities / 20 edges and 740+ stars, not the report's "9×9" / ~418 — primary source preferred); revised adoption figures by an order of magnitude (new [[adoption-and-reception]] page: ~33,940 stars vs the report's "5,000+"); and surfaced eight implementations the report missed, captured in [[comment-thread-implementations]] with new pages for [[synto]], [[link-memory]], [[llm-wiki-mcp]], [[llm-wiki-manager]], and [[sqz]]. Also added the [[staleness-problem]] open problem raised in-thread. Updated [[this-wiki-is-recursive]] to record that the compounding test was run for real.

## [2026-05-28] lint | post-second-ingest check

45 pages, 2 sources. Zero orphans, zero broken links (the only flagged items were inside this log's own prose describing earlier fixes). The OmegaWiki contradiction between the report (9×9, ~418 stars) and the primary gist (8×20, 740+ stars) was resolved in favor of the primary source and recorded on the page itself rather than silently overwritten.

## [2026-05-28] ingest | Synthadoc primary docs

Fetched Synthadoc's actual README/design.md/release notes ([[synthadoc-docs]]) and rewrote [[synthadoc]] with primary detail: the parallel IngestAgent/QueryAgent/LintAgent orchestrator, the `.synthadoc/` SQLite layout, the page frontmatter (status/confidence/sha256), AGPL-3.0, eight providers. Surfaced two genuinely new techniques that advance the field's answer to the precision critiques — created [[adversarial-review]] and [[claim-level-provenance]] and linked them from the [[lossy-summarization-critique]] they mitigate.

## [2026-05-28] ingest | Mehul Gupta critique series

Ingested the most-cited skeptical source ([[gupta-critique]]). Strengthened the [[lossy-summarization-critique]] with Gupta's primary "self-correction argument": RAG errors are transient (fixed sources), wiki errors are durable (cached synthesis). Noted the live tension: [[synthadoc]]'s [[claim-level-provenance]] and [[adversarial-review]] postdate and directly answer this objection — the ecosystem visibly responding to the critique.

## [2026-05-28] ingest | nashsu/llm_wiki primary repo docs

Fetched the nashsu/llm_wiki README + releases ([[nashsu-repo]]) and rewrote [[nashsu-llm-wiki]] with primary detail (v0.4.12; three-column shell; the full feature list; the token-protected local API at 127.0.0.1:19828; `npx skills add`). Surfaced a recurring architectural idea worth its own page — created [[purpose-layer]] (purpose.md, the "why" layer) and linked it from the [[claude-md-schema]] it extends.

## [2026-05-28] ingest | SwarmVault primary repo docs

Fetched the SwarmVault README + skill listings ([[swarmvault-repo]]; author waydelyle, MIT, ~399-489 stars) and rewrote [[swarmvault]] with the real graph CLI (blast/validate/cluster/diff/export --neo4j), the provenance model (every edge → source+claim; nodes carry freshness/confidence/community), god-node + community detection, automatic contradiction detection, and tree-sitter code-awareness. Corroborated [[typed-knowledge-graph]] and the [[lossy-summarization-critique]] mitigation. No new pages needed — pure enrichment of an existing node, which is itself a sign the wiki is maturing.

## [2026-05-28] ingest | Press & analysis coverage

Ingested mainstream/analyst coverage ([[press-coverage]]: VentureBeat, Atlan, Denser.ai). Confirmed the ~400,000-word scale anchor and the "knowledge as compiled code" framing; updated [[andrej-karpathy]] with the Fridman adopter note. Created two new concept pages: [[ephemeral-wiki]] (Fridman's disposable per-task mini-wiki) and [[category-error-critique]] (gnusupport/LudoE11's "is a folder of AI-written markdown really a wiki?" objection). Notably, *declined to ingest a false claim*: one low-quality post conflates the pattern with Karpathy's unrelated llm.c project; flagged on the source page rather than propagated — the [[lint]]/hallucination guard working as intended.

## [2026-05-28] ingest | Kompl primary repo docs

Fetched the Kompl README ([[kompl-repo]]) and enriched [[kompl]] with the real stack (Next.js + Python NLP + n8n + SQLite, Docker, Firecrawl, HuggingFace local model) and the Twitter-bookmark import path. Its "one new source can update 10+ wiki pages" line corroborates the [[ingest]] claim near-verbatim.

## [2026-05-28] ingest | OmegaWiki primary repo docs

Fetched the OmegaWiki README, repo tree, and author gist comments ([[omegawiki-repo]]) and rewrote [[omegawiki]]. Most importantly, RESOLVED the standing contradiction about its typed-graph size: the figures changed across releases (Apr 13: 8 entities/9 edges/20 skills; mid-May: 8/20/26; current README: 9 entities/9 edges/23 skills). Rather than pick one, the page now records the dated progression — both the report's "9×9" and the thread's "8×20" are correct at different times. A clean demonstration of why static figures need dating (the [[lossy-summarization-critique]] in miniature). Surfaced the claims/ layer (kin to [[claim-level-provenance]]) and cross-model [[adversarial-review]].

## [2026-05-28] ingest | AKBP + LLM Wiki v2 + agentmemory (rohitg00)

Ingested a connected cluster ([[akbp-v2-agentmemory]]): enriched [[akbp]] with its real protocol flow and alpha status, and added two new pages — [[llm-wiki-v2]] (Rohit Ghumare's May 23 fork of Karpathy's gist, adding confidence scoring / lifecycle / graphs / hybrid search and an explicit "what makes a wiki rot" focus) and [[agentmemory]] (the ~10k-star agent-memory engine whose production lessons produced v2). v2 `extends` the original gist; AKBP's review-gated writes answer the [[transactional-overhead-critique]].

## [2026-05-28] ingest | qmd primary repo docs

Fetched the qmd README/CHANGELOG/skill ([[qmd-repo]]; @tobilu/qmd v2.0.0) and rewrote [[qmd]] with the exact pipeline parameters — RRF k=60, original-query ×2 weight, the position-aware blend ratios (75/25 → 40/60), and the specific default models (embeddinggemma-300M, Qwen3-Reranker-0.6B, a purpose-fine-tuned qmd-query-expansion-1.7B). Propagated the precise numbers into [[hybrid-retrieval]], which previously had them only approximately. Pure deepening of two existing nodes.

## [2026-05-28] ingest | Edra funding coverage

Ingested March 2026 Edra coverage ([[edra-coverage]]) and refined [[edra]] with primary detail (founders' Palantir FDE background, the $30M/Sequoia round, Living Playbooks, early customers). Corrected an inherited framing: Edra's round closed *before* Karpathy's gist, so it is a *parallel* enterprise product, not one derived from the [[llm-wiki-pattern]] — the report's "enterprise version" is analogy, not lineage. Another instance of using a primary source to correct a secondary one.
