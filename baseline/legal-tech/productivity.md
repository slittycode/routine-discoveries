# legal-tech / personal productivity

PKM / second-brain, snippet & template libraries, task/matter tracking — local-first
where possible. Scores are **fork N / spark N** plus a `local-first:` flag (see
`../README.md`). Provenance: `discoveries/legaltech-nz-2026-05-21.md`.

## Strong — fork-and-run

- **fork 5 / spark 4** · local-first:yes · [espanso/espanso](https://github.com/espanso/espanso) · `Rust` · `13.8k★` · `maturity:app`
  A system-wide text expander driven by plain YAML bundles (with script/shell triggers) that fires in Word, email, anywhere — 100% local. **Build:** your legal snippet & boilerplate library — standard clauses, settlement-statement stock text, email replies, all from your own keystroke triggers. _(05-21 · tags: text-expander, yaml, snippets, boilerplate, system-wide)_
- **fork 4 / spark 4** · local-first:yes · [TriliumNext/Trilium](https://github.com/TriliumNext/Trilium) · `TypeScript` · `36.1k★` · `maturity:app`
  A hierarchical, *scriptable* personal knowledge base whose notes can run JS, so it doubles as a programmable second brain. **Build:** fork it into a precedent/clause library with scripted automations (auto-insert party details, generate a per-matter-type checklist). _(05-21 · tags: pkm, scriptable, knowledge-base, precedents, automations)_
- **fork 5 / spark 5** · local-first:yes · [basicmachines-co/basic-memory](https://github.com/basicmachines-co/basic-memory) · `Python` · `maturity:app`
  Markdown-on-disk PKM where humans (text editor / Obsidian) and AI (via MCP) read and write the same files — semantic search across notes via local vector embeddings, structured knowledge graph via wikilinks and typed relations, native Claude/Cursor/VS Code integration. Stronger AI integration than Trilium for the same local-first guarantee. **Build:** the right shape for a lawyer's matter notes — the human keeps owning plain-text files, while Claude can read, search, summarise, and update them through tools rather than copy-paste. _(05-27 · tags: pkm, markdown-on-disk, mcp, semantic-search, knowledge-graph)_
- **fork 4 / spark 4** · local-first:yes · [blueberrycongee/Lumina-Note](https://github.com/blueberrycongee/Lumina-Note) · `TypeScript` · `maturity:app`
  Local-first Markdown notes app with live preview, bidirectional wiki-links, an AI assistant, and semantic search — Electron + React + CodeMirror, with built-in PDF reader and second-brain framing. **Build:** a lighter alternative to Trilium if you want one app for matter notes + PDFs side-by-side, with AI on the page. _(05-27 · tags: markdown-notes, wiki-links, ai-assistant, pdf-reader, electron)_
- **fork 4 / spark 4** · local-first:yes · [matzalazar/rhizome](https://github.com/matzalazar/rhizome) · `Python` · `maturity:lib`
  Local-first semantic-backlinks tool for Obsidian/Logseq that embeds notes with a multilingual sentence-transformer via ONNX and writes "## Related Notes" wikilink sections — no cloud API or database. **Build:** fork the embed-and-link engine to auto-surface related matters, precedents or clauses across a note vault entirely offline. _(06-03, rescored 06-03-v2 · tags: semantic-backlinks, onnx, obsidian, offline, no-llm)_
- **fork 5 / spark 3** · local-first:yes · [super-productivity/super-productivity](https://github.com/super-productivity/super-productivity) · `TypeScript` · `20k★` · `maturity:app`
  Mature local-first todo app with integrated timeboxing and time tracking, no AI. **Build:** fork it for personal matter/time tracking without rebuilding the scaffolding — exactly the kind of deterministic personal-productivity tool the AI-leaning v1 routine had filtered out. _(06-03-v2 · tags: todo, timeboxing, time-tracking, no-ai, deterministic)_
- **fork 4 / spark 3** · local-first:yes · [open-agreements/open-agreements](https://github.com/open-agreements/open-agreements) · `TypeScript` · `maturity:app`
  Deterministic template filler (no LLM) that substitutes values into 40+ standard agreement templates (NDAs, SAFEs, NVCA, contractor/employment) and emits signable DOCX, via CLI/MCP. **Build:** fork it as a personal precedent-assembly tool; swap in your own NZ templates. _(06-03-v2 · tags: template-filler, precedent-assembly, deterministic, docx, no-llm)_

## Practice-management shell (application)

- **fork 5 / spark 4** · local-first:yes (self-hosted, your hardware) · [stella/stella](https://github.com/stella/stella) · `TypeScript` · `maturity:app`
  Brand-new (May 2026) open-source legal workspace: **Matters** as the core abstraction (status/deadlines/parties/documents), full-text + versioned document store with access controls, and **Tabular Review** for extracting structured fields across many documents (due-diligence/discovery shape). Bun + Postgres + Redis, self-hostable via `bun run dev`. **Build:** the closest thing to a *personal* practice-management base that's actually open source — a shell your forked tools could live inside. _(05-27 · tags: practice-management, matters, tabular-review, self-hosted, workspace-shell)_

## Marginal — kept with a note (dropped on 05-21 for overlap with Trilium)

- **fork 4 / spark 3** · local-first:yes · [naggie/dstask](https://github.com/naggie/dstask) · `Go` · `1.2k★` · `maturity:app`
  A git-powered terminal todo/note manager — single binary, a markdown note page per task, with a full git-history audit trail. Dropped 05-21 as overlapping Trilium/notes. **Build:** a matter-tracker reskin where every status change is a git commit — useful if an immutable audit trail of who-changed-what matters. _(05-21 · tags: todo, git-audit-trail, cli, single-binary, matter-tracker)_
- **fork 4 / spark 2** · local-first:yes · [usememos/memos](https://github.com/usememos/memos) · `Go` · `59.9k★` · `maturity:app`
  A clean, self-hosted single-binary quick-capture / microblog tool, Markdown-native and SQLite-backed. Dropped 05-21 as redundant with Trilium's capture; kept low-tier for completeness. **Build:** a friction-free quick-capture inbox for matter notes if Trilium feels too heavy for jotting. _(05-21 · tags: quick-capture, markdown, sqlite, self-hosted, redundant)_
