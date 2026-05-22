# legal-tech / build-your-own-tool foundations

The plumbing: document parsers, diff engines, and desktop/TUI shells you compose into
your own tools. Recency gate dropped here (a stable base is fine). Scores are **fork N /
spark N** plus a `local-first:` flag (see `../README.md`). Provenance:
`discoveries/legaltech-nz-2026-05-21.md`.

The local redliner is `docling` (ingest) → `jsdiff` (sentence diff) → `diff2html`
(render), wrapped in `tauri`. Structure-aware variants live in `wildcard-tangential.md`
(difftastic); the Word-output last mile lives in `document-comparison-redlining.md` (adeu,
Python-Redlines).

## Parsers (ingest)

- **fork 5 / spark 4** · local-first:yes · [docling-project/docling](https://github.com/docling-project/docling) · `Python` · `60.1k★` · `maturity:lib`
  The standout document-parsing engine: turns PDF/DOCX/PPTX into clean structured Markdown/JSON with tables and layout preserved, and runs air-gapped. **Build:** the ingestion layer under everything else — "drop a deed/contract → clean searchable text" that never touches the cloud. _(05-21 · tags: parser, pdf, docx, markdown, air-gapped)_
- **fork 5 / spark 3** · local-first:yes · [jsvine/pdfplumber](https://github.com/jsvine/pdfplumber) · `Python` · `10.3k★` · `maturity:lib`
  Lower-level than Docling: per-character coordinates, rectangles, and precise table extraction with visual debugging. **Build:** fork it to pull exact fields from fixed-layout NZ forms (ADLS/REINZ agreements, LIM reports, rates statements) where positional control beats a blind text dump. _(05-21 · tags: pdf, char-coordinates, tables, fixed-layout, nz-forms)_

## Diff engines + renderers

- **fork 5 / spark 4** · local-first:yes · [kpdecker/jsdiff](https://github.com/kpdecker/jsdiff) · `JavaScript` · `9.1k★` · `maturity:lib`
  Most diff libs work on lines; jsdiff diffs characters, words, **sentences** and JSON — exactly the granularity legal prose needs, all in the browser/Node with no upload. **Build:** the diff-engine half of a complete local "compare two clauses and show the changes" stack. _(05-21 · tags: diff, sentence-level, json, browser, no-upload)_
- **fork 4 / spark 5** · local-first:yes · [rtfpessoa/diff2html](https://github.com/rtfpessoa/diff2html) · `TypeScript` · `3.4k★` · `maturity:lib`
  Renders diffs as polished side-by-side or inline HTML — the developer code-review UI, repurposed to present document changes to a non-technical client or counterparty. **Build:** pair it with jsdiff (engine) for a printable/PDF redline view; the two compose into a full local-first redliner in an afternoon. _(05-21 · tags: diff-render, side-by-side, html, client-facing, pairs-with-jsdiff)_

## Shells

- **fork 5 / spark 3** · local-first:yes · [tauri-apps/tauri](https://github.com/tauri-apps/tauri) · `Rust` · `107k★` · `maturity:lib`
  The desktop shell to wrap any of these tools into a real, distributable, offline app with a tiny footprint. **Build:** a single "matter cockpit" binary combining your parser + diff + notes, with all data staying on your machine. _(05-21 · tags: desktop-shell, rust, webview, offline, distributable)_
- **fork 3 / spark 4** · local-first:yes · [charmbracelet/bubbletea](https://github.com/charmbracelet/bubbletea) · `Go` · `42.6k★` · `maturity:lib`
  A powerful Elm-architecture TUI framework for Go. Dropped 05-21 as a stack choice (Tauri GUI was preferred), but kept here: it's the leading option if you'd rather build terminal tools than a desktop GUI. **Build:** the shell for a keyboard-driven matter/diff TUI if you prefer the terminal over a Tauri window. _(05-21 · tags: tui, go, elm-architecture, terminal, stack-choice)_
