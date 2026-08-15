# Legaltech-NZ discoveries — 2026-06-03

Repos a **vibe-coding NZ property/conveyancing lawyer** could **fork and build from**
as PERSONAL tools. Scored on TWO axes 1–5: **fork-and-run fit** and **creative/spark
potential**. Kept if `fork ≥3` OR (`spark ≥4` and it clears the spark bar). Local-first
is recorded as a flag and used only as a tiebreaker; licence ignored entirely. Dedup'd
against `discoveries/_seen-legaltech-nz.txt` (29 entries at time of run).

## 1. Document comparison & legal-impact

### [JSv4/Docxodus](https://github.com/JSv4/Docxodus) — **fork 5 / spark 4**
TypeScript/Python/.NET OpenXML engine (forked from Open-Xml-PowerTools) that generates
tracked-change redlines between two DOCX files with move detection and format-change
identification, plus DOCX↔HTML, a markdown projection for LLM pipelines, and a WASM
build. This is the redline *engine* to build a comparison tool on — fork it and wrap a
UI, or pipe its markdown projection into a local LLM for clause-level impact analysis.
lang: TypeScript/C# · local-first: yes

### [yuch85/word-ai-redliner](https://github.com/yuch85/word-ai-redliner) — **fork 5 / spark 4**
MS Word add-in that applies AI edits back into the document as tracked changes,
connecting to local Ollama or vLLM via a proxy and using the companion `office-word-diff`
library's structure-aware diff (token-map strategy with sentence/block fallbacks); 388
tests, v0.3.0. The most directly forkable "AI redlines, in Word, against a local model"
starting point — exactly the confidential-docs-stay-local workflow he wants.
lang: JavaScript · local-first: yes

### [JSv4/react-docxodus-viewer](https://github.com/JSv4/react-docxodus-viewer) — **fork 4 / spark 3**
Client-side React component that renders DOCX and redlines in the browser via the
Docxodus WASM library — no server round-trip, so document content never leaves the
machine. Pair it with Docxodus to get a complete local-first compare-and-review UI he
can fork as the front end of a personal redlining tool.
lang: TypeScript · local-first: yes

## 2. Document understanding

### [run-llama/liteparse](https://github.com/run-llama/liteparse) — **fork 5 / spark 3**
Standalone OSS document parser (Rust core with Node/Python/WASM bindings) that extracts
text with bounding boxes from PDF/Word/PowerPoint/spreadsheets/images and does selective
Tesseract OCR, all locally (`lit parse document.pdf`). The open, no-cloud ingestion layer
for any of his tools — fork it as the front door that turns a scanned S&P agreement into
clean text for diffing, RAG, or clause extraction.
lang: Rust · local-first: yes

### [Nebutra/MinerU-Skill](https://github.com/Nebutra/MinerU-Skill) — **fork 4 / spark 3**
Zero-dependency CLI (and Claude Code skill) wrapping MinerU to turn PDF/Office/images
into clean Markdown with preserved tables, LaTeX and OCR. A higher-fidelity alternative
ingestion path when layout matters (tables, schedules in a lease) — fork it for the cases
where liteparse's plain text loses the structure.
lang: Python · local-first: partial (runs local VLM/OCR models)

### [gmickel/gno](https://github.com/gmickel/gno) — **fork 5 / spark 4**
Fully-offline local-first document-intelligence engine (Bun/TS) doing hybrid retrieval
(BM25 + embeddings + cross-encoder rerank) with grounded, cited answers over notes, code,
PDFs and Office docs, exposed via CLI, Web UI and MCP, using embedded Qwen models. This is
a near-complete "chat with my matter files, offline, with citations" tool — fork it and
point it at a matter folder.
lang: TypeScript · local-first: yes

## 3. Personal productivity

### [swarmclawai/swarmvault](https://github.com/swarmclawai/swarmvault) — **fork 4 / spark 3**
Local-first "LLM wiki" — a knowledge-graph builder, RAG knowledge base and agent-memory
store positioned as an Obsidian alternative, with an MCP server. Fork it as a personal
matter/precedent knowledge base whose graph links clauses, parties and precedents and
that any local LLM can query.
lang: TypeScript · local-first: yes

### [myICOR/myPKA](https://github.com/myICOR/myPKA) — **fork 4 / spark 3**
"AI personal knowledge assistance in a folder" — plain-Markdown PKM, any LLM, designed to
stay yours forever (209★). Low-ceremony base for a personal notes/precedent system that's
just files on disk (so it's trivially backed up and grep-able) with an AI layer on top.
lang: Python · local-first: yes

### [matzalazar/rhizome](https://github.com/matzalazar/rhizome) — **fork 4 / spark 4**
Local-first semantic-backlinks tool for Obsidian/Logseq that embeds notes with a
multilingual sentence-transformer via ONNX and writes "## Related Notes" wikilink sections
— no cloud API or database. Fork the embed-and-link engine to auto-surface related matters,
precedents or clauses across his note vault entirely offline.
lang: Python · local-first: yes

## 4. Build-your-own-tool foundations

### [kreuzberg-dev/html-to-markdown](https://github.com/kreuzberg-dev/html-to-markdown) — **fork 4 / spark 3**
Fast, CommonMark-compliant HTML→Markdown converter from the Kreuzberg document-intelligence
team (750★). The clean conversion primitive for web-clipping legislation, case-law pages or
council/LINZ portals into Markdown his other tools can ingest — a small, dependable building
block rather than an app.
lang: HTML/Rust-backed · local-first: yes

## 5. NZ legal content & data

### [russellbrenner/auslaw-mcp](https://github.com/russellbrenner/auslaw-mcp) — **fork 5 / spark 4**
MCP server for Australian **and New Zealand** legal research: searches AustLII for case law
and legislation, retrieves full-text judgments with paragraph numbers preserved, OCRs scanned
PDFs (Tesseract), extracts neutral citations and formats to AGLC4; runs locally via npm/Docker.
The most on-point NZ find — fork it to give a local AI assistant grounded NZ/AU case-law and
legislation lookup.
lang: TypeScript · local-first: yes

### [edithatogo/nz-legislation](https://github.com/edithatogo/nz-legislation) — **fork 5 / spark 3**
CLI **and** MCP server that searches, retrieves and cites NZ Acts, bills, regulations and
instruments straight from the Parliamentary Counsel Office's legislation.govt.nz API
(TypeScript, 43+ tests, v1.2.0). Drop-in NZ-legislation access for any personal tool — fork
it as the statutory-lookup backbone (e.g. pulling the current Property Law Act / Unit Titles
Act sections into a drafting assistant).
lang: TypeScript · local-first: yes (queries the official PCO API)

### [thecolab-ai/.skills](https://github.com/thecolab-ai/.skills) — **fork 3 / spark 3**
Community-contributed AI "skills" for NZ public data — LINZ, Stats NZ, Auckland Transport,
weather and more. Mine it for ready-made access patterns to NZ open datasets (LINZ titles/
parcels are directly property-relevant) and fork the skills he needs into his own agent.
lang: Python · local-first: yes

## 7. Wildcard / cross-domain spark

### [cool-japan/legalis](https://github.com/cool-japan/legalis) — **fork 2 / spark 5**
Production-grade Rust framework (76 crates, ~1M LOC) that compiles natural-language statutes
into machine-verifiable code while *architecturally* separating deterministic logic (age
thresholds, deadlines, income limits) from judicial discretion via a `LegalResult<T>` enum —
"not everything should be computable." I'd mine its modelling approach to build a small
clause-logic checker that flags the computable obligations and deadlines in a deed and marks
the genuinely discretionary terms for human judgement.
lang: Rust · local-first: yes · why-kept: spark

### [Hashevolution/James-RAG-Evol](https://github.com/Hashevolution/James-RAG-Evol) — **fork 3 / spark 5**
Local-first (Ollama) replayable Graph-RAG with an append-only audit log and — crucially — an
LLM-free **deterministic 4-rule contradiction-arbitration** decision tree; research-grade,
v0.4.1. I'd fork that arbitration engine to build a single-document consistency checker that
flags contradictory defined terms, conflicting dates and broken cross-references across a long
agreement — deterministically, not by asking an LLM to "spot contradictions."
lang: Python · local-first: yes · why-kept: spark

---

## NZ data sources & APIs worth building on
- **legislation.govt.nz (PCO API)** — Acts, bills, regulations, instruments (see
  `edithatogo/nz-legislation` for a working client).
- **NZLII / AustLII** — NZ case law and legislation full text (see `russellbrenner/auslaw-mcp`).
- **LINZ Data Service** — titles, parcels, survey data (directly property/conveyancing-relevant).
- **data.govt.nz · Stats NZ** — open datasets; `thecolab-ai/.skills` has ready access patterns.
</content>
