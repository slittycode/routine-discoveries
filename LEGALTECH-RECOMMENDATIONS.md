# Legaltech-NZ Recommendations

The consolidated, deduped verdict across **every** legaltech-nz discovery sweep in
`discoveries/`. Single-source-of-truth shortlist; the dated files remain the raw
per-sweep record. This is the legaltech-nz equivalent of `RECOMMENDATIONS.md` (the
audio-mir shortlist) — kept as a **separate file** because the two streams use
incompatible scoring schemes (see Legend) and every other layer of this repo already
keeps them apart (`_seen*.txt`, `routines/*.md`, `baseline/music-asa/` vs
`baseline/legal-tech/`).

> **Comprehensive catalog:** this file is the *shortlist* (repos that cleared the
> routine's keep bar). For **every** repo ever surfaced — including dropped and
> redundant ones — with idea-mining ("what to fork/build") commentary, see
> **`baseline/legal-tech/`**.

Every repo the routine kept (`fork-fit ≥3` **OR** `spark ≥4` with a named build) is
listed below. Where the 2026-06-03-v2 re-run rescored or reversed an earlier verdict,
v2's verdict is kept as the later, more-informed pass — see the footer for the deltas.

**Legend** — **fork N / spark N** (each 1–5): who this is for — a **vibe-coding NZ
property/conveyancing lawyer** who wants **personal** tools (not commercial products),
not a firm or product team. **fork** = how readily he could fork it and run/extend it
as a personal tool; **spark** = whether it teaches a technique or seeds a tool he
couldn't otherwise build. This is the **legal schema** — *not* the music 1–5 scale
used in `RECOMMENDATIONS.md`. `local-first` = `yes` (fully offline) · `partial`
(local core, cloud LLM or optional backend) · `no` — a flag, not a gate. Licence is
never a consideration. NZ relevance is a bonus, not a requirement.

## Document comparison & legal-impact

- **fork 5 / spark 5** · local-first:yes · [dealfluence/adeu](https://github.com/dealfluence/adeu) — flattens a Word doc to Markdown for a model to edit, then projects edits back as native Word Track Changes. _(05-21)_
- **fork 5 / spark 5** · local-first:yes · [davidar/pandiff](https://github.com/davidar/pandiff) — Pandoc-powered semantic prose diff (any Pandoc input) writing native Word Track Changes; the universal "diff two contracts, emit a redline" tool. _(05-27)_
- **fork 5 / spark 4** · local-first:yes · [JSv4/Docxodus](https://github.com/JSv4/Docxodus) — OpenXML WmlComparer redlining with move detection, DOCX↔HTML, markdown projection, WASM build. _(05-27, rescored 06-03-v2)_
- **fork 5 / spark 4** · local-first:yes · [UseJunior/safe-docx](https://github.com/UseJunior/safe-docx) — deterministic `docx-comparison` engine + primitives, no AI required. _(06-03-v2, new)_
- **fork 4 / spark 5** · local-first:partial · [kipeum86/contract-review-agent](https://github.com/kipeum86/contract-review-agent) — compares a counterparty draft against house templates, emits tracked-change redlines + margin comments. _(05-21)_
- **fork 4 / spark 3** · local-first:yes · [JSv4/react-docxodus-viewer](https://github.com/JSv4/react-docxodus-viewer) — client-side React DOCX/redline renderer via the Docxodus WASM library. _(06-03)_
- **fork 4 / spark 3** · local-first:yes · [yuch85/word-ai-redliner](https://github.com/yuch85/word-ai-redliner) — Word add-in kept for its deterministic `office-word-diff` core; the AI layer is optional. _(05-27, reframed 06-03-v2)_
- **fork 5 / spark 3** · local-first:yes · [houfu/redlines](https://github.com/houfu/redlines) — lightweight library turning two texts into Word-style strike-through/insert markup. _(05-21)_
- **fork 3 / spark 4** · local-first:yes · [yuch85/office-word-diff](https://github.com/yuch85/office-word-diff) — the structure-aware Word-diff library underlying word-ai-redliner, usable standalone. _(05-27)_
- **fork 3 / spark 5** · local-first:yes · [AlexAlves87/ContextSafe](https://github.com/AlexAlves87/ContextSafe) — local PII detection/redaction with cross-document consistent aliasing. _(05-27, spark-only)_
- **fork 2 / spark 4** · local-first:yes · [sen-uni-kn/ContractCheck](https://github.com/sen-uni-kn/ContractCheck) — formalises clause preconditions into first-order logic, runs an SMT solver for internal contradictions. _(05-21, spark-only)_

## Document understanding

- **fork 5 / spark 4** · local-first:yes · [Mintplex-Labs/anything-llm](https://github.com/Mintplex-Labs/anything-llm) — fully-offline "private ChatGPT over your documents" with workspaces and local vector DB. _(05-21)_
- **fork 5 / spark 5** · local-first:yes · [shcherbak-ai/contextgem](https://github.com/shcherbak-ai/contextgem) — LLM extraction framework returning results with paragraph/sentence-level source citations. _(05-21)_
- **fork 5 / spark 3** · local-first:yes · [run-llama/liteparse](https://github.com/run-llama/liteparse) — offline Rust PDF parser with bounding-box extraction and selective OCR, no cloud dependencies. _(05-27, rescored 06-03-v2)_
- **fork 5 / spark 3** · local-first:yes · [ocrmypdf/OCRmyPDF](https://github.com/ocrmypdf/OCRmyPDF) — Tesseract OCR layer making scanned PDFs searchable in place. _(05-27)_
- **fork 5 / spark 4** · local-first:yes · [gmickel/gno](https://github.com/gmickel/gno) — offline hybrid-retrieval document-intelligence engine with grounded, cited answers; AI-first but kept for a real deterministic core. _(06-03, rescored 06-03-v2)_
- **fork 4 / spark 5** · local-first:yes · [Open-Source-Legal/OpenContracts](https://github.com/Open-Source-Legal/OpenContracts) — self-hosted document-annotation + knowledge-base platform with cross-contract clause comparison. _(05-21)_
- **fork 4 / spark 3** · local-first:partial · [Nebutra/MinerU-Skill](https://github.com/Nebutra/MinerU-Skill) — zero-dependency CLI wrapping MinerU for layout-preserving PDF/Office→Markdown. _(06-03-v2)_
- **fork 3 / spark 5** · local-first:partial · [tomasonjo-labs/legal-tech-chat](https://github.com/tomasonjo-labs/legal-tech-chat) — extracts contract fields into a Neo4j knowledge graph, queried via a LangGraph agent. _(05-21)_

## Build-your-own-tool foundations

- **fork 5 / spark 4** · local-first:yes · [docling-project/docling](https://github.com/docling-project/docling) — the standout document-parsing engine, PDF/DOCX/PPTX→structured Markdown/JSON, air-gapped. _(05-21)_
- **fork 5 / spark 4** · local-first:yes · [kpdecker/jsdiff](https://github.com/kpdecker/jsdiff) — character/word/sentence/JSON diff granularity, browser/Node, no upload. _(05-21)_
- **fork 5 / spark 4** · local-first:yes · [eigenpal/docx-editor](https://github.com/eigenpal/docx-editor) — WYSIWYG DOCX editor library (ProseMirror) producing canonical OOXML with tracked changes + MCP agent SDK. _(05-27)_
- **fork 5 / spark 4** · local-first:yes · [superdoc-dev/superdoc](https://github.com/superdoc-dev/superdoc) — self-hosted in-browser OOXML editor with genuine tracked changes, zero servers/AI required. _(06-03-v2, reversed from a 05-27 drop)_
- **fork 5 / spark 3** · local-first:yes · [jsvine/pdfplumber](https://github.com/jsvine/pdfplumber) — per-character coordinates, precise table extraction with visual debugging. _(05-21)_
- **fork 5 / spark 3** · local-first:yes · [tauri-apps/tauri](https://github.com/tauri-apps/tauri) — the desktop shell to wrap any of these tools into a real offline app. _(05-21)_
- **fork 4 / spark 5** · local-first:yes · [rtfpessoa/diff2html](https://github.com/rtfpessoa/diff2html) — renders diffs as polished side-by-side/inline HTML for non-technical clients. _(05-21)_
- **fork 4 / spark 5** · local-first:yes · [trailofbits/graphtage](https://github.com/trailofbits/graphtage) — semantic-diff library/CLI for tree-like files, compares structure not text. _(06-03-v2, new)_
- **fork 4 / spark 4** · local-first:yes · [bzsanti/oxidizePdf](https://github.com/bzsanti/oxidizePdf) — pure-Rust PDF library with structure-aware chunking for RAG, no ML/C deps. _(05-27)_
- **fork 4 / spark 4** · local-first:yes · [afnanenayet/diffsitter](https://github.com/afnanenayet/diffsitter) — tree-sitter AST difftool for semantic diffs. _(06-03-v2, reversed from a 05-27 drop)_
- **fork 4 / spark 3** · local-first:yes · [kreuzberg-dev/html-to-markdown](https://github.com/kreuzberg-dev/html-to-markdown) — fast CommonMark-compliant HTML→Markdown for web-clipping legislation/case-law pages. _(06-03-v2)_

## Personal productivity

- **fork 5 / spark 5** · local-first:yes · [basicmachines-co/basic-memory](https://github.com/basicmachines-co/basic-memory) — Markdown-on-disk PKM where humans and AI (via MCP) read/write the same files. _(05-27)_
- **fork 5 / spark 4** · local-first:yes · [stella/stella](https://github.com/stella/stella) — open-source legal workspace: Matters, versioned document store, Tabular Review. _(05-27)_
- **fork 5 / spark 4** · local-first:yes · [espanso/espanso](https://github.com/espanso/espanso) — system-wide text expander for a legal snippet & boilerplate library. _(05-21)_
- **fork 5 / spark 3** · local-first:yes · [super-productivity/super-productivity](https://github.com/super-productivity/super-productivity) — mature local-first todo app with timeboxing and time tracking, no AI. _(06-03-v2, new)_
- **fork 4 / spark 4** · local-first:yes · [TriliumNext/Trilium](https://github.com/TriliumNext/Trilium) — hierarchical, scriptable PKM whose notes can run JS. _(05-21)_
- **fork 4 / spark 4** · local-first:yes · [blueberrycongee/Lumina-Note](https://github.com/blueberrycongee/Lumina-Note) — local-first Markdown notes with live preview, wiki-links, built-in PDF reader. _(05-27)_
- **fork 4 / spark 4** · local-first:yes · [matzalazar/rhizome](https://github.com/matzalazar/rhizome) — local-first semantic backlinks for Obsidian/Logseq via ONNX embeddings, no LLM. _(06-03-v2)_
- **fork 4 / spark 3** · local-first:yes · [open-agreements/open-agreements](https://github.com/open-agreements/open-agreements) — deterministic template filler (no LLM) for 40+ standard agreement templates. _(06-03-v2, new)_

## NZ legal content & data

- **fork 5 / spark 4** · local-first:yes · [russellbrenner/auslaw-mcp](https://github.com/russellbrenner/auslaw-mcp) — MCP server for AU/NZ legal research: AustLII case-law search, OCR, AGLC4 citation formatting. _(06-03, rescored 06-03-v2)_
- **fork 5 / spark 3** · local-first:yes · [edithatogo/nz-legislation](https://github.com/edithatogo/nz-legislation) — CLI/MCP server over the official PCO legislation.govt.nz API. _(06-03, rescored 06-03-v2)_
- **fork 3 / spark 5** · local-first:yes · [nzpco/PCO-AI-Generating-an-Updated-Act](https://github.com/nzpco/PCO-AI-Generating-an-Updated-Act) — official PCO code consolidating amendment Acts against the principal Act from legislation.govt.nz XML. _(05-21)_
- **fork 3 / spark 4** · local-first:yes · [isaacus-dev/open-australian-legal-corpus-creator](https://github.com/isaacus-dev/open-australian-legal-corpus-creator) — scraper/assembly pipeline behind the open Australian legislation+case-law corpus; closest Commonwealth template. _(05-21)_
- **fork 3 / spark 4** · local-first:yes · [nzpco/PCO-AI-Chatbot-for-NZL](https://github.com/nzpco/PCO-AI-Chatbot-for-NZL) — official PCO chatbot grounded in the live NZ Legislation corpus. _(05-27)_
- **fork 3 / spark 4** · local-first:yes · [nzpco/PCO-AI-Plain-Language-Recommendations](https://github.com/nzpco/PCO-AI-Plain-Language-Recommendations) — official PCO plain-language rewrite suggestions for statutory text. _(05-27)_
- **fork 3 / spark 3** · local-first:yes · [thecolab-ai/.skills](https://github.com/thecolab-ai/.skills) — community AI "skills" wrapping NZ open-data access (LINZ, Stats NZ). _(06-03, rescored 06-03-v2)_

## Tangential but interesting

- **fork 4 / spark 4** · local-first:partial · [excalidraw/excalidraw](https://github.com/excalidraw/excalidraw) — embeddable hand-drawn whiteboard, offline PWA; visual matter mapping (chain-of-title, easements). _(05-21)_

## Wildcard / cross-domain spark

- **fork 4 / spark 5** · local-first:yes · [paulfitz/daff](https://github.com/paulfitz/daff) — cell-level diff for tabular/CSV data; repurposed for settlement statements and trust-ledger schedules. _(05-21)_
- **fork 3 / spark 5** · local-first:yes · [Wilfred/difftastic](https://github.com/Wilfred/difftastic) — structure-aware syntax-tree diff for code, pattern transfers to contract redlining. _(05-21)_
- **fork 3 / spark 5** · local-first:yes (retrieval; LLM is BYO) · [aa0101181514/tw-legal-rag](https://github.com/aa0101181514/tw-legal-rag) — judgment-retrieval CLI with bundle-level citation verification. _(05-27)_
- **fork 3 / spark 5** · local-first:yes · [Hashevolution/James-RAG-Evol](https://github.com/Hashevolution/James-RAG-Evol) — Graph-RAG with an LLM-free deterministic contradiction-arbitration engine. _(06-03, rescored 06-03-v2, spark-only)_
- **fork 3 / spark 4** · local-first:partial · [Sysmagine/SemanticDiff](https://github.com/Sysmagine/SemanticDiff) — code-review-UI-for-prose wildcard; change-classification pattern for hiding cosmetic redline noise. _(06-03-v2, new, spark-only)_
- **fork 2 / spark 5** · local-first:yes · [cool-japan/legalis](https://github.com/cool-japan/legalis) — Rust framework compiling statutes to code, separating deterministic logic from judicial discretion. _(06-03, rescored 06-03-v2, spark-only)_
- **fork 2 / spark 4** · local-first:yes · [kaicontext/kai](https://github.com/kaicontext/kai) — semantic-change engine over Git; model for clause-history/obligation-structure review. _(05-27, spark-only)_

## Sweeps folded in

**2026-05-21 (first sweep):** 20 survivors, headlined by the local-first contract
redliner thesis (`docling` → `jsdiff` → `diff2html`, with `adeu` and `contextgem`).

**2026-05-27 (second sweep):** 15 survivors deepening the redline stack (`pandiff`,
`eigenpal/docx-editor`, `word-ai-redliner`/`office-word-diff`, `Docxodus`) plus the
first productivity and NZ-official-sibling entries.

**2026-06-03 / 06-03-v2 (third sweep, deterministic-first re-run):** v1 scored 20
repos under the original AI-permissive routine; the routine was then revised
("AI is optional, not the point" — deterministic tooling prioritised, AI-first share
capped) and re-run same-day as v2. **v2 is treated as authoritative** for every
overlapping repo. Deltas from v1→v2:
- **Dropped** (AI-first padders, failed the revised cap/thin-wrapper rule):
  `swarmclawai/swarmvault`, `myICOR/myPKA` — not folded in above.
- **Reframed:** `yuch85/word-ai-redliner` kept for its deterministic `office-word-diff`
  core (fork4/spark3), not the AI add-in.
- **Newly surfaced** by the deterministic-first queries (invisible to v1's AI-heavy
  query set): `UseJunior/safe-docx`, `superdoc-dev/superdoc`,
  `trailofbits/graphtage`, `afnanenayet/diffsitter`, `super-productivity`,
  `open-agreements`, `Sysmagine/SemanticDiff`.
- Two of the newly-surfaced repos (`afnanenayet/diffsitter`, `superdoc-dev/superdoc`)
  had actually been evaluated and *dropped* by the 05-27 sweep for apparent redundancy
  with `difftastic` and `eigenpal/docx-editor` respectively — the deterministic-first
  re-run independently kept both. Treated as reversed verdicts, v2 authoritative.

**Catch-up consolidation (2026-07-01):** all of the above were already merged to
`main` as raw dated sweep files and `_seen-legaltech-nz.txt` entries (via PR #28→#31),
but had never been folded into `baseline/legal-tech/` (frozen at the 05-21 sweep since
`b24b196`) or given a shortlist file — despite `README.md` promising one "once several
sweeps accrue." This file and the `baseline/legal-tech/` updates that accompany it
are that catch-up.
