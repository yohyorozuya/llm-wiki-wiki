# AKBP + LLM Wiki v2 + agentmemory (Rohit Ghumare / rohitg00)

Sources: github.com/rohitg00/akbp, gist rohitg00/2067ab416f7bbe447c1977edaaa681e2 (LLM Wiki v2, forked from karpathy/llm-wiki.md May 23 2026), github.com/rohitg00/agentmemory. Fetched late May 2026.

## LLM Wiki v2 (the gist)

"LLM Wiki v2 — extending Karpathy's LLM Wiki pattern with lessons from building agentmemory (10K stars), a persistent memory engine for AI coding agents." Forked from karpathy/llm-wiki.md on May 23, 2026. "Everything in the original still applies. This document adds what we learned running the pattern in production: what breaks at scale, what's missing, and what separates a wiki that stays useful from one that rots. The core insight is correct: stop re-deriving, start compiling. RAG retrieves and forgets. A wiki accumulates and compounds. The three-layer architecture (raw sources, wiki, schema) works." Adds confidence scoring, lifecycle, knowledge graphs, and hybrid search.

## AKBP — Agent Knowledge Base Protocol

"AKBP turns the LLM Wiki pattern into a protocol surface for agent runtimes. It is a local-first, file-backed knowledge base that agents can read, write, verify, export, and carry across tools. The idea comes from the same insight behind LLM Wiki v2: stop re-deriving, start compiling."

Adds "the machinery a repo needs when that pattern becomes operational: typed claims, source hashes, lifecycle relations, review-gated writes, JSONL tool calls, schemas, and conformance tests." Reference implementation: a Python CLI; a newline-delimited JSON tool server for agent integrations; JSON schemas for requests/responses/records/method parameters. Still alpha.

Flow: "agent runtime reads project context -> evidence is registered as sources -> durable claims are proposed from notes or transcripts -> writes are previewed and reviewed -> approved claims, pages, sources, and relations are stored as files -> local indexes are rebuilt from source-of-truth artifacts -> the next agent session receives cited context instead of guesswork." Goal: "not to replace model context, repository instructions, tool protocols, vector databases, or second-brain tools. AKBP gives those systems a portable knowledge substrate they can share."

## agentmemory (the implementation behind the lessons)

"#1 Persistent memory for AI coding agents based on real-world benchmarks." npm install -g @agentmemory/agentmemory; server on :3111; `agentmemory connect claude-code` (also codex, cursor, gemini-cli). MCP server proxying 53 tools when connected (falls back to 7 local). 6 lifecycle hooks (SessionStart, UserPromptSubmit, PreToolUse, PostToolUse, PreCompact, Stop), 8 skills (/recall, /remember, /session-history, /forget, /recap, /handoff, /commit-context, /commit-history). ~10K stars. Author: Rohit Ghumare (15K+ stars across 270+ repos).
