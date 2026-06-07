# tobi/qmd — primary repo docs (README, CHANGELOG, package.json, skill)

Source: github.com/tobi/qmd. Package @tobilu/qmd v2.0.0. "Query Markup Documents — On-device hybrid search for markdown files with BM25, vector search, and LLM reranking." Author: Tobi Lütke. Fetched late May 2026.

## Origin

"Built in a single day for searching personal markdown notes, journals, and meeting transcripts." Chose SQLite over Elasticsearch "because QMD is a personal tool — single binary, no server dependencies." sqlite-vec for vectors ("in-process, no external vector database"). RRF "is parameter-free and handles missing signals gracefully." Originally Ollama for embeddings/reranking/query-expansion; replaced with node-llama-cpp in 0.6.0.

## The pipeline (verbatim from README diagram)

```
Query ──► LLM Expansion ──► [Original, Variant 1, Variant 2]
            │
   ┌────────┴────────┐
   ▼                 ▼
 FTS (BM25)      Vector Search
   │                 │
   ▼                 ▼
 Ranked List     Ranked List
   └────────┬────────┘
            ▼
   RRF Fusion (k=60)
   Original query ×2 weight
   Top-rank bonus: +0.05/#1, +0.02/#2-3
            │
            ▼
   Top 30 candidates
            │
            ▼
   LLM Re-ranking (yes/no + logprob confidence)
            │
            ▼
   Position-Aware Blend
   Rank 1-3:  75% RRF / 25% reranker
   Rank 4-10: 60% RRF / 40% reranker
   Rank 11+:  40% RRF / 60% reranker
            │
            ▼
   Final Results
```

## Default models (src/llm.ts, HuggingFace URIs)

- Embed: embeddinggemma-300M-Q8_0.gguf
- Rerank: Qwen3-Reranker-0.6B-Q8_0.gguf
- Generate (query expansion): tobil/qmd-query-expansion-1.7B (a model Lütke fine-tuned for this)

## Chunking

Markdown uses regex chunking; for code (.ts/.tsx/.js/.jsx/.py/.go/.rs) it parses with tree-sitter and merges AST-derived break points (`--chunk-strategy auto`).

## CLI

qmd add, qmd embed, qmd search (BM25), qmd vsearch (vector), qmd query (full pipeline), qmd get, qmd collection add, qmd update. Also an MCP server. Skill guidance: "Use BM25 when you know names, exact terms, titles, identifiers, or code symbols... Do not overuse semantic search. If you know exact titles or terms, BM25 is faster and often better."
