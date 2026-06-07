# Wiki Index

*Catalog of every page. Updated on every ingest. Start here, then drill in.*

## Best entry points

- [[llm-wiki-pattern]] — the central concept; start here
- [[this-wiki-is-recursive]] — how this wiki demonstrates itself

## Concepts

### Principles & architecture
- [[llm-wiki-pattern]] — the pattern itself
- [[compilation-vs-retrieval]] — the core principle (compile once vs re-derive)
- [[claude-md-schema]] — the schema layer (CLAUDE.md / AGENTS.md)
- [[index-md]] — the catalog file
- [[log-md]] — the chronological log file
- [[raw-layer]] — the immutable source layer
- [[purpose-layer]] — the optional "why" layer (purpose.md)
- [[memex]] — the 1945 ancestor
- [[hybrid-retrieval]] — wiki + BM25 + vector
- [[typed-knowledge-graph]] — typed entities and edges
- [[tiered-memory]] — Facts / Working Memory / Wisdom
- [[ephemeral-wiki]] — disposable per-task mini-wikis
- [[routing-layer]] — branch taxonomy for scale
- [[candidates-staging]] — promotion gates
- [[llm-wiki-v2]] — community successor spec
- [[adversarial-review]] — second-LLM page check
- [[claim-level-provenance]] — paragraph-to-source-line citations

### Operations
- [[ingest]] — read a source, update pages
- [[query]] — read index, drill in, answer
- [[lint]] — periodic health-check

### Comparisons & critiques
- [[rag]] — the prior paradigm
- [[llm-wiki-vs-rag]] — when each wins
- [[three-failure-modes]] — Identity, Level, Relationship
- [[transactional-overhead-critique]] — the referential-integrity problem
- [[lossy-summarization-critique]] — the precision problem
- [[category-error-critique]] — the "is it really a wiki?" critique
- [[staleness-problem]] — the proactivity / agency problem
- [[adoption-and-reception]] — how the pattern was received
- [[comment-thread-implementations]] — tools surfaced in the gist thread

## Entities

- [[andrej-karpathy]] — originator of the pattern
- [[tobi-lutke]] — built qmd
- [[edra]] — the enterprise wedge

## Implementations

### Desktop apps
- [[nashsu-llm-wiki]] — Tauri desktop, ~7.9k stars
- [[nohmitaina]] — macOS editor; named the three failure modes

### Engines
- [[synthadoc]] — routing layer, candidates staging, context packs
- [[swarmvault]] — typed graph, one-command quickstart
- [[kompl]] — NLP-before-LLM, entity resolution

### Skill kits & harnesses
- [[omegawiki]] — 23 Claude Code skills, 9×9 typed graph
- [[claude-code]] — the agent harness

### Protocols & libraries
- [[akbp]] — Agent Knowledge Base Protocol
- [[expo-llm-wiki]] — tiered-memory library
- [[agentmemory]] — persistent agent memory engine (~10k stars)

### Retrieval
- [[qmd]] — local hybrid search (Tobi Lütke)
- [[kb-cli]] — minimal hybrid retrieval
- [[sqz]] — token compression composable with the workflow

### Surfaced in the gist comment thread
- [[synto]] — local-first, Ollama/LM Studio
- [[link-memory]] — source-backed agent memory, MCP
- [[llm-wiki-mcp]] — the pattern as an MCP server
- [[llm-wiki-manager]] — full Claude Code skill

## Sources

- [[research-report]] — the LLM Wiki expert briefing (seed source)
- [[karpathy-gist]] — Karpathy's original llm-wiki.md (primary source)
- [[synthadoc-docs]] — Synthadoc primary documentation
- [[gupta-critique]] — Mehul Gupta's skeptical series
- [[nashsu-repo]] — nashsu/llm_wiki primary repo docs
- [[swarmvault-repo]] — SwarmVault primary repo docs
- [[press-coverage]] — VentureBeat / Atlan / Denser.ai coverage
- [[kompl-repo]] — Kompl primary repo docs
- [[omegawiki-repo]] — OmegaWiki primary repo docs
- [[akbp-v2-agentmemory]] — AKBP / LLM Wiki v2 / agentmemory cluster
- [[qmd-repo]] — qmd primary repo docs
- [[edra-coverage]] — Edra funding coverage

## Synthesis

- [[this-wiki-is-recursive]] — this wiki as a demonstration of the pattern
