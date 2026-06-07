# tuirk/Kompl — primary repo docs (README)

Source: github.com/tuirk/Kompl. Fetched late May 2026.

## What it is

"Knowledge compiler — turns scattered links, files, and bookmarks into a living wiki that compounds with every new source." "Most tools save your stuff and forget about it. Kompl reads it, extracts the knowledge, and compiles it into an interlinked wiki, automatically. One new source can update 10+ wiki pages. Cross-references, contradictions, and synthesis are built at ingest time, not re-discovered on every query."

## Stack & deployment

Built with Next.js, Python NLP, n8n orchestration, and SQLite. Runs locally via Docker (Docker Desktop or Engine + Compose v2). Node.js >= 24 for the kompl CLI. Outbound calls limited to your own API keys: Gemini and/or DeepSeek for compilation, Firecrawl for scraping, plus the URLs you choose to ingest. First start 5-10 min (builds ~2GB images, downloads a local AI model from HuggingFace); subsequent starts ~15s.

## Setup

`git clone https://github.com/tuirk/Kompl.git kompl && cd kompl && node setup.js` — creates config, asks for the two API keys, installs the kompl CLI, starts the stack. Onboarding wizard at http://localhost:3000 walks through first sources: paste a URL, drop a PDF, or import a Twitter bookmark export.

## Page types

Entity pages, concept pages, comparisons, and source summaries, wikilinked together.
