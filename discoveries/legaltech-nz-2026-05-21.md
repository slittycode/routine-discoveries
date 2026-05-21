# Legal-tech & personal-tools discoveries (NZ) — 2026-05-21

First sweep of the **legaltech-nz** stream (see `routines/legaltech-nz.md`): GitHub repos a NZ
property/conveyancing lawyer who vibe-codes could **fork and build from** as personal tools. Each
entry carries two 1–5 scores — **fork-and-run fit** (how readily you could fork and run it) and
**creative/spark** (whether it teaches a technique or seeds a tool you couldn't otherwise build);
kept if fork-fit ≥3, or spark ≥4 with a named build. Licence is ignored; local-first is preferred
and verified per repo; NZ relevance is a bonus. All facts were ground-truthed against live GitHub
pages.

20 survivors. The headline: a complete **local-first contract redliner** can be assembled today —
`docling` (ingest) → `jsdiff` (sentence-level diff) → `diff2html` (render), with `dealfluence/adeu`
emitting native Word tracked-changes and `contextgem` doing cited clause extraction.

## Document comparison & legal-impact

### [dealfluence/adeu](https://github.com/dealfluence/adeu) — **fork 5 / spark 5**
Flattens a Word doc to Markdown so a model can edit the *substance*, then projects the edits back as native Word Track Changes — cleanly separating meaning from formatting. Fork it as the output layer of your legal-impact comparator: a local model decides what should change, adeu emits the redlined `.docx` clients already know how to read.
Python (+ Node) · local-first: yes

### [kipeum86/contract-review-agent](https://github.com/kipeum86/contract-review-agent) — **fork 4 / spark 5**
A local-first agent that compares a counterparty draft against your house templates and emits a Word file with tracked-change redlines, internal-vs-external margin comments, and negotiation points — the closest thing to your flagship goal already built. Fork it and swap its Claude API call for a local model (Ollama) to go fully offline.
Python · local-first: partial (file processing stays local; cloud LLM by default)

### [houfu/redlines](https://github.com/houfu/redlines) — **fork 5 / spark 3**
A small, dependable library that turns two texts into Word-style strike-through/insert markup (HTML, Markdown, JSON, terminal) with change statistics. Use it as the lightweight *display* primitive once your model has identified the substantive deltas.
Python · local-first: yes

### [sen-uni-kn/ContractCheck](https://github.com/sen-uni-kn/ContractCheck) — **fork 2 / spark 4**
An academic tool that formalises a contract's clause preconditions into first-order logic and runs an SMT solver to find internal contradictions and unexecutable clauses. Mine the *modelling approach* (not the Java) to build a logic-level consistency linter that flags defined-term conflicts and clauses that can never both hold.
Java · local-first: yes · why-kept: spark (single-document consistency — a rare, on-point angle)

## Document understanding

### [Mintplex-Labs/anything-llm](https://github.com/Mintplex-Labs/anything-llm) — **fork 5 / spark 4**
A polished, fully-offline "private ChatGPT over your documents" desktop app with workspaces, PDF/DOCX ingestion, source citations and a local vector DB (Ollama/LM Studio). Self-host it day one as your confidential "chat with my matter files" base, then graft clause-extraction prompts onto its workspace model (workspaces map neatly to matters).
JavaScript · local-first: yes

### [shcherbak-ai/contextgem](https://github.com/shcherbak-ai/contextgem) — **fork 5 / spark 5**
An LLM extraction framework built around "Aspects" and "Concepts" that returns results with paragraph/sentence-level source references and auto-generated justifications, and can run against a local model. Fork it as your structured clause/defined-term/date extractor — the cite-back-to-source is exactly what trustworthy legal output needs.
Python · local-first: yes

### [Open-Source-Legal/OpenContracts](https://github.com/Open-Source-Legal/OpenContracts) — **fork 4 / spark 5**
A self-hosted document-annotation + knowledge-base platform with vector + full-text search, LLM clause extraction, version control, and agents that compare clauses across many contracts. Heavier to stand up (Docker), but the most complete self-hosted foundation if you want one app for both understanding and cross-document comparison of your private corpus.
Python · local-first: yes

### [tomasonjo-labs/legal-tech-chat](https://github.com/tomasonjo-labs/legal-tech-chat) — **fork 3 / spark 5**
A worked pipeline that extracts structured fields from contracts into a Neo4j knowledge graph and answers questions via a LangGraph agent. Fork the *pattern* to make your contracts queryable by relationship ("every lease whose rent-review clause references CPI") instead of flat one-doc-at-a-time RAG.
Jupyter/Python · local-first: partial (self-hostable; reference notebooks use cloud LLMs)

## Build-your-own-tool foundations

### [docling-project/docling](https://github.com/docling-project/docling) — **fork 5 / spark 4**
The standout document-parsing engine: turns PDF/DOCX/PPTX into clean structured Markdown/JSON with tables and layout preserved, and runs air-gapped. Make it the ingestion layer under everything else — "drop a deed/contract → clean searchable text" that never touches the cloud.
Python · local-first: yes

### [jsvine/pdfplumber](https://github.com/jsvine/pdfplumber) — **fork 5 / spark 3**
Lower-level than Docling: per-character coordinates, rectangles, and precise table extraction with visual debugging. Fork it to pull exact fields from fixed-layout NZ forms (ADLS/REINZ agreements, LIM reports, rates statements) where positional control matters more than a blind text dump.
Python · local-first: yes

### [kpdecker/jsdiff](https://github.com/kpdecker/jsdiff) — **fork 5 / spark 4**
Most diff libs work on lines; jsdiff diffs characters, words, **sentences** and JSON — exactly the granularity legal prose needs, all in the browser/Node with no upload. It's the diff-engine half of a complete local "compare two clauses and show the changes" stack.
JavaScript · local-first: yes

### [rtfpessoa/diff2html](https://github.com/rtfpessoa/diff2html) — **fork 4 / spark 5**
Renders diffs as polished side-by-side or inline HTML — the developer code-review UI, repurposed to present document changes to a non-technical client or counterparty. Pair it with jsdiff (engine) for a printable/PDF redline view; the two compose into a full local-first redliner in an afternoon.
TypeScript · local-first: yes

### [tauri-apps/tauri](https://github.com/tauri-apps/tauri) — **fork 5 / spark 3**
The desktop shell to wrap any of these tools into a real, distributable, offline app with a tiny footprint. Build a single "matter cockpit" binary combining your parser + diff + notes, with all data staying on your machine.
Rust · local-first: yes

## Personal productivity

### [espanso/espanso](https://github.com/espanso/espanso) — **fork 5 / spark 4**
A system-wide text expander driven by plain YAML bundles (with script/shell triggers) that fires in Word, email, anywhere — 100% local. Configure it as your legal snippet & boilerplate library: standard clauses, settlement-statement stock text, email replies, all from your own keystroke triggers.
Rust · local-first: yes

### [TriliumNext/Trilium](https://github.com/TriliumNext/Trilium) — **fork 4 / spark 4**
A hierarchical, *scriptable* personal knowledge base whose notes can run JS, so it doubles as a programmable second brain. Fork it into a precedent/clause library with scripted automations (auto-insert party details, generate a per-matter-type checklist).
TypeScript · local-first: yes

## NZ legal content & data

### [nzpco/PCO-AI-Generating-an-Updated-Act](https://github.com/nzpco/PCO-AI-Generating-an-Updated-Act) — **fork 3 / spark 5**
Official NZ Parliamentary Counsel Office code that takes an amendment Act and applies it to the principal Act from the legislation.govt.nz **XML**, presenting the consolidated result — and it documents running locally with Ollama. NZ gold: fork it as both a worked example of parsing NZ legislation XML and a personal "what does the in-force version actually say?" consolidator. (Sibling official repos worth a look: `nzpco/PCO-AI-Chatbot-for-NZL`, `PCO-AI-Classification-of-Legislation`, `PCO-AI-Plain-Language-Recommendations`.)
TypeScript · local-first: yes

### [isaacus-dev/open-australian-legal-corpus-creator](https://github.com/isaacus-dev/open-australian-legal-corpus-creator) — **fork 3 / spark 4**
The maintained scrapers + assembly pipeline behind the first open corpus of Australian legislation *and* case law. Not NZ, but the closest live Commonwealth template: adapt its per-jurisdiction scraper/normaliser design to build your own offline NZ legislation+caselaw corpus (pointed at legislation.govt.nz XML or NZLII).
Python · local-first: yes

## Wildcard / cross-domain spark

### [Wilfred/difftastic](https://github.com/Wilfred/difftastic) — **fork 3 / spark 5**
A structure-aware (syntax-tree) diff for *code* that ignores reflowed whitespace and shows only real changes — the pattern transfers directly to contracts, where renumbering and reflow hide the true edits. Pair it with a Markdown/tree-sitter grammar to build a clause-level redliner far cleaner than Word's character compare.
Rust · local-first: yes · wildcard (code → prose structural diff)

### [paulfitz/daff](https://github.com/paulfitz/daff) — **fork 4 / spark 5**
Cell-level diff for tabular/CSV data with a visual highlight format — repurpose it for settlement statements, trust-ledger schedules, or rates apportionments where one wrong figure matters. Build a "what changed between two versions of this financial schedule?" viewer that points at the exact cell, not just the row.
Polyglot (JS/Py/Java…) · local-first: yes · wildcard (spreadsheet diff → financial-schedule diff)

## Tangential but interesting

### [excalidraw/excalidraw](https://github.com/excalidraw/excalidraw) — **fork 4 / spark 4**
An embeddable hand-drawn whiteboard component that works offline and autosaves locally. Embed it in your Tauri app to sketch chain-of-title, easements, subdivision layouts or settlement timelines — visual matter mapping with everything stored on your machine.
TypeScript · local-first: partial (offline PWA / embeddable component, no backend)

## Suggested build stacks

- **Local contract redliner (a day's work):** `docling` → `jsdiff` → `diff2html`, fully offline; add `dealfluence/adeu` to emit a Word `.docx` redline.
- **Structure-aware redline (advanced):** `difftastic` + a tree-sitter Markdown grammar for true clause-level diffs.
- **Confidential matter Q&A, day one:** `anything-llm` (self-host); layer `contextgem` for cited clause/term extraction.
- **Private matter cockpit:** `tauri` shell wrapping your redliner + Trilium-style scripted notes + `espanso` snippets, with `excalidraw` embedded for title/flow diagrams.
- **NZ legislation consolidator:** fork `nzpco/PCO-*` to parse legislation.govt.nz XML and apply amendment Acts locally with Ollama.

## Dropped / also evaluated

- `naggie/dstask` — terminal todo with a git-history audit trail; nice matter-tracker reskin, but overlaps Trilium/notes for now.
- `usememos/memos` — clean single-binary quick-capture; redundant with Trilium's capture.
- `curiousily/ragbase` — small, fully-local chat-with-PDF skeleton; superseded by AnythingLLM unless you want a tinier base to own line-by-line (quiet since 2024).
- `JSv4/Python-Redlines` — true Word-grade `.docx` tracked changes via OpenXML WmlComparer; solid baseline, but overlaps adeu and adds a .NET dependency (2024).
- `google/diff-match-patch` — battle-tested fuzzy diff/patch (archived 2024); keep in your back pocket, but jsdiff covers prose granularity better.
- `charmbracelet/bubbletea` — excellent Go TUI framework; only if you prefer terminal tools over a Tauri GUI.
- `evolsb/legal-redline-tools` — tiny (29★) but the most literally on-point: generates real tracked-changes `.docx` + redline PDFs from JSON edits; worth a look as the "AI analysis → Word markup" last mile.
- Excluded (failed verification): `Ansvar-Systems/newzealand-law-mcp` (404 — does not exist) and `spartypkp/open-source-legislation` (dead — infrastructure and data links shut down).

## NZ data sources & APIs worth building on (not repos to fork)

- **legislation.govt.nz** — official NZ legislation, downloadable as **XML** (the format the PCO repos parse); the backbone for any consolidation/search tool.
- **NZLII** (nzlii.org) — NZ case law + legislation for personal research indexing.
- **data.govt.nz** — central catalogue of NZ open datasets.
- **LINZ Data Service (Toitū Te Whenua)** — property/parcel/title cadastral data + APIs.
- **NZBN / Companies Office** — entity lookups for party due-diligence tooling.
