# swarmclawai/swarmvault — primary repo docs

Source: github.com/swarmclawai/swarmvault (README), swarmvault.ai, awesome-claude-code issue #1539, trendshift. Author: waydelyle. License: MIT. Stars ~399-489 (late May 2026). Language: TypeScript. Fetched late May 2026.

## What it is

"The local-first LLM Wiki, knowledge graph builder, and RAG knowledge base for AI agents. SwarmVault turns docs, code, transcripts, notes, and URLs into a durable markdown wiki plus a local graph you can inspect, query, and hand to agents." Built on Karpathy's pattern; pitched as an Obsidian alternative and durable Claude Code / Codex / OpenClaw memory.

## One-command start

`npm install -g @swarmvaultai/cli`, then `swarmvault demo` creates a sample vault with three sources and opens the interactive graph viewer. No API keys required (built-in heuristic provider; optional Ollama for local embeddings). MCP server: `npx -y @swarmvaultai/cli mcp` over stdio for Claude Code.

## Self-described comparison table (gist/skill listing)

| | Karpathy's Gist | SwarmVault |
| Three-layer architecture | described | implemented |
| Ingest / query / lint | manual | CLI commands |
| One-command setup | — | swarmvault quickstart |
| Typed knowledge graph | — | yes |
| Interactive graph viewer | — | yes |
| Agent-ready context packs | — | yes |
| Agent task ledger | — | yes |
| 30+ input formats | — | yes |
| Code-aware (tree-sitter) | — | yes |

## Knowledge graph (primary detail)

- "Knowledge graph with provenance — every edge traces back to a specific source and claim. Nodes carry freshness, confidence, and community membership."
- God nodes and communities — highest-connectivity bridge nodes identified automatically; graph report pages surface surprising connections with plain-English explanations.
- Contradiction detection — conflicting claims across sources detected automatically and surfaced in the graph report.
- Rich graph CLI: `graph blast <target>` (reverse import impact), `graph status`, `graph stats`, `graph validate --strict` (duplicate ids, dangling refs, confidence bounds, conflicted-edge evidence), `graph cluster --resolution`, `graph export --report` (self-contained HTML) / `--neo4j` (Cypher export), `graph diff` (compare against last committed graph), `graph query` (filter by relation, context group, evidence class, node type, language).
- Code-aware: AST/parser-backed analysis; tree-sitter; captures import edges; SQL adds table/view nodes + read/write/join/reference edges.

## Scope

"Turn books, articles, notes, transcripts, mail exports, calendars, datasets, slide decks, screenshots, URLs, and code into a persistent knowledge vault." Local-first; everything on disk; the desktop viewer reads the same local files the CLI writes (graph.json, report.json, approvals, candidates).
