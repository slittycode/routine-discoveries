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
- **fork 4 / spark 4** · local-first:yes · [bzsanti/oxidizePdf](https://github.com/bzsanti/oxidizePdf) · `Rust` · `maturity:lib`
  Pure-Rust PDF library aimed at RAG: structure-aware chunking, table/text extraction, signatures, encryption, no ML or C deps. The chunking primitive is the interesting bit — most PDF libraries leave chunking to the caller, which is where legal RAG tends to go wrong (splitting mid-clause, breaking defined-term context). **Build:** fork it as the ingest-and-chunk layer feeding a local RAG over your archive. _(05-27 · tags: pdf, rust, structure-aware-chunking, rag, no-c-deps)_

## Conversion

- **fork 4 / spark 3** · local-first:yes · [kreuzberg-dev/html-to-markdown](https://github.com/kreuzberg-dev/html-to-markdown) · `Rust-backed` · `maturity:lib`
  Fast, CommonMark-compliant HTML→Markdown converter from the Kreuzberg document-intelligence team. **Build:** the clean conversion primitive for web-clipping legislation, case-law pages or council/LINZ portals into Markdown other tools can ingest — a small, dependable building block rather than an app. _(06-03, rescored 06-03-v2 · tags: html-to-markdown, commonmark, web-clipping, conversion-primitive)_

## Diff engines + renderers

- **fork 5 / spark 4** · local-first:yes · [kpdecker/jsdiff](https://github.com/kpdecker/jsdiff) · `JavaScript` · `9.1k★` · `maturity:lib`
  Most diff libs work on lines; jsdiff diffs characters, words, **sentences** and JSON — exactly the granularity legal prose needs, all in the browser/Node with no upload. **Build:** the diff-engine half of a complete local "compare two clauses and show the changes" stack. _(05-21 · tags: diff, sentence-level, json, browser, no-upload)_
- **fork 4 / spark 5** · local-first:yes · [rtfpessoa/diff2html](https://github.com/rtfpessoa/diff2html) · `TypeScript` · `3.4k★` · `maturity:lib`
  Renders diffs as polished side-by-side or inline HTML — the developer code-review UI, repurposed to present document changes to a non-technical client or counterparty. **Build:** pair it with jsdiff (engine) for a printable/PDF redline view; the two compose into a full local-first redliner in an afternoon. _(05-21 · tags: diff-render, side-by-side, html, client-facing, pairs-with-jsdiff)_
- **fork 4 / spark 5** · local-first:yes · [trailofbits/graphtage](https://github.com/trailofbits/graphtage) · `Python` · `2.5k★` · `maturity:lib`
  Semantic-diff library and CLI for tree-like files (JSON/XML/HTML/YAML/CSV) that compares structure, not text. **Build:** the foundation for clause-level legal-impact diffing — convert two agreements to HTML/XML (Docxodus) and graphtage the trees to see real structural changes, not line noise. _(06-03-v2 · tags: structural-diff, tree-diff, json-xml, semantic-diff)_
- **fork 4 / spark 4** · local-first:yes · [afnanenayet/diffsitter](https://github.com/afnanenayet/diffsitter) · `Rust` · `2.4k★` · `maturity:app`
  Tree-sitter-based AST difftool producing meaningful semantic diffs. **Build:** a second technique for structure-aware comparison — mine its tree-sitter approach for diffing parsed document structure rather than raw text. _(reconsidered 06-03-v2 — the 05-27 sweep had dismissed this exact repo as adding "no different angle" over difftastic; the 06-03-v2 deterministic-first re-run independently kept it. Treating v2 as authoritative: it's the later, more-informed verdict. · tags: tree-sitter, ast-diff, structural, reversed-verdict)_

## Editors (WYSIWYG DOCX)

- **fork 5 / spark 4** · local-first:yes · [eigenpal/docx-editor](https://github.com/eigenpal/docx-editor) · `TypeScript` · `maturity:lib`
  Open-source WYSIWYG DOCX editor library (React + Vue + Nuxt adapters, ProseMirror engine) that produces "canonical OOXML" with tracked changes, and ships a companion `@eigenpal/docx-editor-agents` Agent SDK + chat UI with MCP server support. **Build:** the editing half of a matter cockpit — drop a contract in, model proposes edits via MCP, edits land as native Word tracked changes the client opens in Word without complaint. _(05-27 · tags: wysiwyg, prosemirror, mcp, tracked-changes, editor-lib)_
- **fork 5 / spark 4** · local-first:yes · [superdoc-dev/superdoc](https://github.com/superdoc-dev/superdoc) · `TypeScript` · `700★` · `maturity:lib`
  Self-hosted, framework-agnostic in-browser editor for real OOXML DOCX with genuine tracked changes and comments (Yjs collaboration), zero servers/AI required. **Build:** the editing/redline UI shell to build a personal review tool on — embed it, no rich-text approximation. _(reconsidered 06-03-v2 — the 05-27 sweep had dropped this exact repo as redundant with eigenpal/docx-editor; the 06-03-v2 deterministic-first re-run independently kept it for being zero-server/zero-AI. Treating v2 as authoritative. · tags: ooxml, browser-editor, yjs, zero-ai, reversed-verdict)_

## Shells

- **fork 5 / spark 3** · local-first:yes · [tauri-apps/tauri](https://github.com/tauri-apps/tauri) · `Rust` · `107k★` · `maturity:lib`
  The desktop shell to wrap any of these tools into a real, distributable, offline app with a tiny footprint. **Build:** a single "matter cockpit" binary combining your parser + diff + notes, with all data staying on your machine. _(05-21 · tags: desktop-shell, rust, webview, offline, distributable)_
- **fork 3 / spark 4** · local-first:yes · [charmbracelet/bubbletea](https://github.com/charmbracelet/bubbletea) · `Go` · `42.6k★` · `maturity:lib`
  A powerful Elm-architecture TUI framework for Go. Dropped 05-21 as a stack choice (Tauri GUI was preferred), but kept here: it's the leading option if you'd rather build terminal tools than a desktop GUI. **Build:** the shell for a keyboard-driven matter/diff TUI if you prefer the terminal over a Tauri window. _(05-21 · tags: tui, go, elm-architecture, terminal, stack-choice)_
