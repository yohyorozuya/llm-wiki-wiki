# vaults/ — the workshop

This folder holds **bespoke, configured-but-empty LLM wikis** built here via the wizard, then copied out to where each project actually lives.

## What's in here

Each subfolder is a complete, self-contained LLM wiki: its own `.claude/CLAUDE.md`, folder structure, and seeded `index.md` / `log.md`. They are **configured but contain no ingested knowledge** — empty `raw/`, empty wiki buckets. The configuration is bespoke (tailored to a specific purpose), not a generic template.

## Why they live here

1. **Record-keeping.** This vault already holds all the knowledge about the LLM Wiki pattern, so it's the natural registry for the wikis you create from it.
2. **Easier configuration of similar future vaults.** When you need a new vault like one you've built, there's a real, working example sitting right here to clone and adapt — and the agent has both the reference pages and your past vaults as context.

## How to use

1. In this vault, tell Claude: *"build me a vault for &lt;purpose&gt;"* (or *"make one like &lt;existing-vault&gt;"*).
2. The wizard asks a few shaping questions and scaffolds a bespoke vault into `vaults/<slug>/`.
3. When you're ready to actually use it, **copy the subfolder out** to where the project lives (`cp -r vaults/<slug> ~/wherever`).
4. Ingest your real sources *there*. This workshop vault stays clean.

See `registry.md` for everything built so far.
