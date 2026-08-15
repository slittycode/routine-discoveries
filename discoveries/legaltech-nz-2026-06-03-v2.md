# Legaltech-NZ discoveries — 2026-06-03 (v2: deterministic-first re-run)

Re-run of the 2026-06-03 sweep under the **revised** `routines/legaltech-nz.md` (AI is
optional, not the point; deterministic tooling prioritised; ≤~1/3 of survivors may be
AI-first; LLM/RAG wrappers treated as thin unless they add deterministic substance).
Keep `legaltech-nz-2026-06-03.md` (v1) for side-by-side comparison.

**What changed vs v1**
- **Dropped (AI-first padders, now fail the cap / thin-wrapper rule):** `swarmclawai/swarmvault`
  (generic local "LLM wiki" / agent memory), `myICOR/myPKA` (AI-PKM methodology; the non-AI
  part is just markdown files).
- **Reframed:** `yuch85/word-ai-redliner` is kept for its DETERMINISTIC `office-word-diff`
  structure-aware diff; the AI add-in is the reference demo, not the headline.
- **Newly surfaced** by the deterministic-first queries (these were invisible to v1's
  AI-heavy query set): `UseJunior/safe-docx`, `superdoc-dev/superdoc`,
  `trailofbits/graphtage`, `afnanenayet/diffsitter`, `super-productivity`,
  `open-agreements`, `Sysmagine/SemanticDiff`.
- **AI-first share:** v1 ≈ 5/15 → v2 ≈ 2/20 (gno, word-ai-redliner). Deterministic-led.

## 1. Document comparison & legal-impact

### [UseJunior/safe-docx](https://github.com/UseJunior/safe-docx) — **fork 5 / spark 4** · NEW
TypeScript suite of `docx-primitives` + a **deterministic** `docx-comparison` engine (plus an
optional MCP wrapper), running entirely locally with no document content leaving the machine;
does surgical text replacement, comment/footnote workflows and revision extraction as
structured JSON, with ECMA-376 conformance and NDA/partnership/LOI fixtures. The cleanest
no-AI base for a compare-and-revise tool — fork the comparison engine, ignore the MCP layer.
lang: TypeScript · local-first: yes

### [JSv4/Docxodus](https://github.com/JSv4/Docxodus) — **fork 5 / spark 4**
OpenXML tracked-change engine (TS/Python/.NET, WASM build) generating redlines between two
DOCX with move detection and format-change ID, plus DOCX↔HTML and a markdown projection. The
redline engine to build a comparison tool on; pairs with safe-docx (editing) and graphtage
(structural diff of the HTML/XML form).
lang: TypeScript/C# · local-first: yes

### [yuch85/word-ai-redliner](https://github.com/yuch85/word-ai-redliner) — **fork 4 / spark 3** · reframed
Kept for the **deterministic** `office-word-diff` library it ships (structure-aware diff:
token-map → sentence → block fallback); the Word add-in that drives it from local Ollama is the
reference demo. Mine the diff library for precise, formatting-preserving DOCX edits; the AI
layer is optional.
lang: JavaScript · local-first: yes

### [JSv4/react-docxodus-viewer](https://github.com/JSv4/react-docxodus-viewer) — **fork 4 / spark 3**
Client-side React DOCX + redline rendering via the Docxodus WASM library — no server round-trip.
The local-first front end for a Docxodus-based review tool.
lang: TypeScript · local-first: yes

## 2. Document understanding

### [run-llama/liteparse](https://github.com/run-llama/liteparse) — **fork 5 / spark 3**
Standalone OSS parser (Rust core; Node/Python/WASM bindings) extracting text with bounding boxes
from PDF/Office/images plus selective Tesseract OCR, all local. The no-cloud ingestion front door
for any of his tools.
lang: Rust · local-first: yes

### [Nebutra/MinerU-Skill](https://github.com/Nebutra/MinerU-Skill) — **fork 4 / spark 3**
Zero-dependency CLI wrapping MinerU to turn PDF/Office/images into clean Markdown with preserved
tables, LaTeX and OCR — the higher-fidelity path when layout matters (schedules in a lease).
lang: Python · local-first: partial (local VLM/OCR models)

### [gmickel/gno](https://github.com/gmickel/gno) — **fork 5 / spark 4** · AI-first
Kept despite the LLM layer because the engine is **real and deterministic**: offline hybrid
retrieval (BM25 + embeddings + cross-encoder rerank) over notes/PDFs/Office, with grounded cited
answers, CLI/WebUI/MCP, embedded Qwen. "Chat with my matter files, offline, with citations."
lang: TypeScript · local-first: yes

## 3. Personal productivity

### [super-productivity/super-productivity](https://github.com/super-productivity/super-productivity) — **fork 5 / spark 3** · NEW
Mature local-first todo app with integrated timeboxing and **time tracking** (20k★, Electron/web,
no AI). Exactly the kind of deterministic personal-productivity tool v1's AI-leaning routine
filtered out — fork it for personal matter/time tracking without rebuilding the scaffolding.
lang: TypeScript · local-first: yes

### [matzalazar/rhizome](https://github.com/matzalazar/rhizome) — **fork 4 / spark 4**
Local-first semantic backlinks for Obsidian/Logseq via an ONNX sentence-transformer (embeddings,
**no LLM**), writing "## Related Notes" wikilinks. Fork the embed-and-link engine to auto-surface
related matters/precedents/clauses offline.
lang: Python · local-first: yes

### [open-agreements/open-agreements](https://github.com/open-agreements/open-agreements) — **fork 4 / spark 3** · NEW
**Deterministic** template filler (no LLM) that substitutes values into 40+ standard agreement
templates (NDAs, SAFEs, NVCA, contractor/employment) and emits signable DOCX, via CLI/MCP. Fork it
as a personal precedent-assembly tool; swap in his own NZ templates.
lang: TypeScript · local-first: yes

## 4. Build-your-own-tool foundations

### [trailofbits/graphtage](https://github.com/trailofbits/graphtage) — **fork 4 / spark 5** · NEW
Semantic-diff library and CLI for tree-like files (JSON/XML/HTML/YAML/CSV) that compares
**structure, not text** (2.5k★, Python). The foundation for clause-level legal-impact diffing:
convert two agreements to HTML/XML (Docxodus) and graphtage the trees to see real structural
changes, not line noise.
lang: Python · local-first: yes

### [afnanenayet/diffsitter](https://github.com/afnanenayet/diffsitter) — **fork 4 / spark 4** · NEW
Tree-sitter-based AST difftool producing meaningful semantic diffs (2.4k★, Rust). A second
technique for structure-aware comparison — mine its tree-sitter approach for diffing parsed
document structure rather than raw text.
lang: Rust · local-first: yes

### [superdoc-dev/superdoc](https://github.com/superdoc-dev/superdoc) — **fork 5 / spark 4** · NEW
Self-hosted, framework-agnostic in-browser editor for **real OOXML DOCX** with genuine tracked
changes and comments (Yjs collaboration), zero servers/AI required (700★). The editing/redline UI
shell to build a personal review tool on — embed it, no rich-text approximation.
lang: TypeScript · local-first: yes

### [kreuzberg-dev/html-to-markdown](https://github.com/kreuzberg-dev/html-to-markdown) — **fork 4 / spark 3**
Fast CommonMark-compliant HTML→Markdown (Rust-backed Kreuzberg ecosystem, 750★). The conversion
primitive for web-clipping legislation/case-law/LINZ pages into Markdown his tools can ingest.
lang: HTML/Rust-backed · local-first: yes

## 5. NZ legal content & data

### [russellbrenner/auslaw-mcp](https://github.com/russellbrenner/auslaw-mcp) — **fork 5 / spark 4**
MCP server for AU **and NZ** legal research: AustLII case-law/legislation search, full-text
judgments with paragraph numbers, Tesseract OCR for scanned PDFs, neutral-citation + AGLC4
formatting; runs locally. The substance (search/retrieval/OCR/citation) is deterministic and
useful without any AI.
lang: TypeScript · local-first: yes

### [edithatogo/nz-legislation](https://github.com/edithatogo/nz-legislation) — **fork 5 / spark 3**
CLI **and** MCP that searches/retrieves/cites NZ Acts, bills and regulations from the PCO
legislation.govt.nz API (TS, 43+ tests). Drop-in NZ-legislation access — fork it as the statutory
lookup backbone (Property Law Act / Unit Titles Act sections into a drafting tool).
lang: TypeScript · local-first: yes (official PCO API)

### [thecolab-ai/.skills](https://github.com/thecolab-ai/.skills) — **fork 3 / spark 3**
Community AI "skills" wrapping deterministic NZ open-data access (LINZ, Stats NZ, Auckland
Transport). Mine the LINZ titles/parcels access patterns (directly property-relevant) regardless
of the AI packaging.
lang: Python · local-first: yes

## 7. Wildcard / cross-domain spark

### [cool-japan/legalis](https://github.com/cool-japan/legalis) — **fork 2 / spark 5** · why-kept: spark
Production-grade Rust framework (76 crates) that compiles statutes into machine-verifiable code,
architecturally separating deterministic logic (deadlines, thresholds) from judicial discretion via
`LegalResult<T>` — explicitly LLM-free. I'd mine it to build a clause-logic checker that flags the
computable obligations/deadlines in a deed and marks the discretionary terms for human judgement.
lang: Rust · local-first: yes

### [Sysmagine/SemanticDiff](https://github.com/Sysmagine/SemanticDiff) — **fork 3 / spark 4** · NEW
Programming-language-aware diff with a side-by-side review UI for VS Code/GitHub — the textbook
"code-review UI repurposed for prose" wildcard. I'd mine its change-classification + review-UI
approach to build a clause-change reviewer that hides cosmetic edits and foregrounds substantive
ones in a redline.
lang: (extension) · local-first: partial · why-kept: spark

### [Hashevolution/James-RAG-Evol](https://github.com/Hashevolution/James-RAG-Evol) — **fork 3 / spark 5** · why-kept: spark
Local-first Graph-RAG whose standout is an **LLM-free deterministic 4-rule contradiction-arbitration**
engine. I'd fork that engine to build a single-document consistency checker that flags contradictory
defined terms, conflicting dates and broken cross-references across a long agreement — deterministically.
lang: Python · local-first: yes

---

Evaluated this re-run but cut for redundancy (added to `_seen-legaltech-nz.txt`):
**docMentis/docmentis-udoc-viewer** (WASM PDF/DOCX viewer — overlaps superdoc + react-docxodus-viewer);
**kako-jun/diffx** (structured-data semantic diff — overlaps graphtage). Excluded keyword-spam/pirated:
`ERDOGAN064/FineReader-Pro-OCR-Edition`.

## NZ data sources & APIs worth building on
- **legislation.govt.nz (PCO API)** — Acts/bills/regulations (`edithatogo/nz-legislation`).
- **NZLII / AustLII** — NZ case law + legislation (`russellbrenner/auslaw-mcp`).
- **LINZ Data Service** — titles, parcels, survey (property/conveyancing-relevant).
- **data.govt.nz · Stats NZ** — open datasets (`thecolab-ai/.skills` has access patterns).
</content>
