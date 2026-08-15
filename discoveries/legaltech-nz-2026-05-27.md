# Legal-tech & personal-tools discoveries (NZ) — 2026-05-27

Second sweep of the **legaltech-nz** stream (see `routines/legaltech-nz.md`):
GitHub repos a NZ property/conveyancing lawyer who vibe-codes could **fork
and build from** as personal tools. Each entry carries two 1–5 scores —
**fork-and-run fit** and **creative / spark potential**; kept if
`fork-fit ≥3` OR (`spark ≥4` AND a named build). Licence is ignored;
local-first is preferred and verified per repo; NZ relevance is a bonus.
All facts ground-truthed against live GitHub pages.

Dedup'd against `discoveries/_seen-legaltech-nz.txt` (29 entries at run
time, all from the 2026-05-21 first sweep).

15 survivors. The headline: this sweep deepens the **redline stack** with
genuinely better building blocks — `pandiff` does prose-aware tracked-
changes-DOCX *for any pandoc-supported input*; `eigenpal/docx-editor` is
the ProseMirror-based, MCP-equipped WYSIWYG that closes the editing loop;
`yuch85/word-ai-redliner` + `office-word-diff` give a working Ollama-
backed Word add-in with structure-aware diff; and `JSv4/Docxodus`
upgrades the same author's already-evaluated `Python-Redlines` into a
cross-platform OOXML / WASM stack. The Phase-1 stack (`adeu` + `jsdiff`
+ `diff2html`) from sweep #1 still wins for a one-day local prototype;
this sweep tells you what to build *next*.

## Document comparison & legal-impact

### [davidar/pandiff](https://github.com/davidar/pandiff) — **fork 5 / spark 5**
Pandoc-powered semantic prose diff that ingests *anything* Pandoc can
read (DOCX, PDF, Markdown, HTML, LaTeX, ODT) and writes CriticMarkup,
HTML, PDF-via-LaTeX, or **DOCX with native Track Changes** — i.e. it's
already the universal "diff two contracts, emit a Word redline" tool you
were going to assemble out of `jsdiff` + `adeu`. Local once installed
(npm + Pandoc), still maintained (v0.8.0, May 2025), and works in CI via
the documented Docker image. Fork it as the engine and skin a Tauri /
web UI over it.
TypeScript · local-first: yes

### [yuch85/word-ai-redliner](https://github.com/yuch85/word-ai-redliner) — **fork 4 / spark 5**
Microsoft Word task-pane add-in that calls an OpenAI-compatible endpoint
(**works against local Ollama / vLLM**) and applies the model's edits as
real Word tracked changes via a cascading token-map → sentence-diff →
block-replace strategy that preserves run-level formatting (bold, font,
colour). The point: the redline lives inside the lawyer's existing Word
session, not a separate app. Fork it, swap the prompt set for your house
clause-by-clause review prompts, point it at Ollama, and you've got
private AI redlining where the document never leaves the laptop.
JavaScript · local-first: yes (with Ollama)

### [yuch85/office-word-diff](https://github.com/yuch85/office-word-diff) — **fork 3 / spark 4**
The structure-aware Word-diff library that powers `word-ai-redliner`,
broken out for reuse: token-map → sentence-diff → block-replace fallbacks,
formatting-preserving, Office.js-based. Worth knowing as a separate
dependency you can lift into other Word-add-in experiments without
adopting the full redliner UI.
JavaScript · local-first: yes

### [JSv4/Docxodus](https://github.com/JSv4/Docxodus) — **fork 4 / spark 5**
Successor-grade rewrite of `JSv4/Python-Redlines` (already evaluated in
sweep #1): OpenXML SDK on .NET 8 with **WmlComparer-based redlining
including move detection and formatting-only-change detection**, plus
bidirectional DOCX↔HTML conversion, markdown projection for LLM
pipelines, a `DocxSession` stateful editor, and — crucially —
distribution as a WASM npm package (`react-docxodus-viewer` is the
companion React component). The same engine in browser, Node, or .NET;
the strongest native-grade tracked-changes pipeline you can run without
Word installed. Pair with `pandiff` (or as `adeu`'s successor) at the
output stage.
C# (+ TS/WASM) · local-first: yes

### [AlexAlves87/ContextSafe](https://github.com/AlexAlves87/ContextSafe) — **fork 3 / spark 5**
100% local PII detection + redaction for PDFs / DOCX / images, with
**cross-document consistency** ("same person always gets the same alias
within a project") and three modes: masking, consistent pseudonyms,
synthetic-with-invalid-checksums data. Spanish-leaning entity set today
(DNI / NIG / ECLI), but the architecture is the gold: build an NZ
adaptation (IRD numbers, NZBNs, Land Titles references, parcel IDs) and
use it as a pre-flight step before any cloud-LLM call, so confidential
matter docs can use cloud models without leaking client identity.
Python · local-first: yes · why-kept: spark (the consistent-alias
technique is the missing piece for sane cloud-LLM use in a NZ practice)

## Document understanding

### [run-llama/liteparse](https://github.com/run-llama/liteparse) — **fork 4 / spark 4**
LlamaIndex's *offline* PDF parser: Rust + PDFium for fast text +
**bounding-box** extraction, selective Tesseract OCR, JSON/text output,
and per-page screenshots for LLM agents — explicitly "no cloud
dependencies." Sits next to (not on top of) `docling`: Docling is the
generalist, Liteparse is the fast-and-light specialist. Fork it when
you need positional control (fixed-layout NZ forms — ADLS/REINZ
agreements, LIM reports, rates statements) without the heavier model
stack.
Rust · local-first: yes

### [ocrmypdf/OCRmyPDF](https://github.com/ocrmypdf/OCRmyPDF) — **fork 5 / spark 3**
Well-known but missing from sweep #1 — Tesseract-backed OCR layer that
makes scanned PDFs searchable in place. Run it across the matter folder
once and your entire historical archive becomes greppable, RAG-able,
diff-able. Foundational plumbing for everything downstream; not exciting
on its own, but the cheapest single quality-of-life upgrade in the
stack.
Python · local-first: yes

## Build-your-own-tool foundations

### [eigenpal/docx-editor](https://github.com/eigenpal/docx-editor) — **fork 5 / spark 4**
Open-source WYSIWYG DOCX editor library (React + Vue + Nuxt adapters,
ProseMirror engine) that produces "canonical OOXML" with tracked
changes, and ships a companion `@eigenpal/docx-editor-agents` Agent SDK
+ chat UI with **MCP server support**. Fork it as the editing half of
your matter cockpit — drop a contract in, model proposes edits via MCP,
edits land as native Word tracked changes the client opens in Word
without complaint.
TypeScript · local-first: yes

### [bzsanti/oxidizePdf](https://github.com/bzsanti/oxidizePdf) — **fork 4 / spark 4**
Pure-Rust PDF library aimed at RAG: **structure-aware chunking**,
table / text extraction, signatures, encryption, no ML or C deps.
The chunking primitive is the interesting bit — most PDF libraries leave
chunking to the caller, which is where legal RAG tends to go wrong
(splitting mid-clause, breaking defined-term context). Fork it as the
ingest-and-chunk layer feeding a local RAG over your archive.
Rust · local-first: yes

## Personal productivity

### [basicmachines-co/basic-memory](https://github.com/basicmachines-co/basic-memory) — **fork 5 / spark 5**
Markdown-on-disk PKM where humans (text editor / Obsidian) **and AI
(via MCP)** read and write the same files — semantic search across notes
via local vector embeddings, structured knowledge graph via wikilinks and
typed relations, native Claude / Cursor / VS Code integration. This is
the right shape for a lawyer's matter notes: the human keeps owning
plain-text files, while Claude can read, search, summarise, and update
them through tools rather than copy-paste. Stronger AI integration than
Trilium for the same local-first guarantee.
Python · local-first: yes

### [blueberrycongee/Lumina-Note](https://github.com/blueberrycongee/Lumina-Note) — **fork 4 / spark 4**
Local-first Markdown notes app with live preview, bidirectional
wiki-links, an AI assistant, and semantic search — Electron + React +
CodeMirror, with built-in PDF reader and second-brain framing. A
lighter alternative to Trilium if you want one app for matter notes +
PDFs side-by-side, with AI on the page.
TypeScript · local-first: yes

## Applications (open-source legal workspace)

### [stella/stella](https://github.com/stella/stella) — **fork 5 / spark 4**
Brand-new (May 2026) open-source legal workspace: **Matters** as the
core abstraction (status / deadlines / parties / documents), full-text +
versioned document store with access controls, and **Tabular Review**
for extracting structured fields across many documents (due-diligence /
discovery shape). TypeScript + Bun + Postgres + Redis, self-hostable via
`bun run dev`, hosted preview at `my.stll.app`. The closest thing to a
*personal* practice-management base that's actually open source —
ideal as the shell your forked tools live inside.
TypeScript · local-first: yes (self-hosted, your hardware)

## NZ legal content & data

### [nzpco/PCO-AI-Chatbot-for-NZL](https://github.com/nzpco/PCO-AI-Chatbot-for-NZL) — **fork 3 / spark 4**
Official NZ Parliamentary Counsel Office prototype: a chatbot grounded
in the live New Zealand Legislation corpus. Sibling to the already-
shortlisted `PCO-AI-Generating-an-Updated-Act`. Fork it as a worked
example of "RAG over `legislation.govt.nz` XML, with Ollama at the
back" — and as the closest official template for a personal "ask the
Act" tool over the statutes you actually practise under.
Python · local-first: yes

### [nzpco/PCO-AI-Plain-Language-Recommendations](https://github.com/nzpco/PCO-AI-Plain-Language-Recommendations) — **fork 3 / spark 4**
Companion official PCO repo: TypeScript implementation that suggests
plain-language rewrites of statutory text. Less directly useful for
contract work, but the **statute-aware prompting and evaluation
scaffolding** is the genuinely transferable piece for any "rewrite this
clause in plain English for the client" tool. Useful as a second NZ-
official template to mine alongside the chatbot and the consolidator.
TypeScript · local-first: yes

## Wildcard / cross-domain spark

### [aa0101181514/tw-legal-rag](https://github.com/aa0101181514/tw-legal-rag) — **fork 3 / spark 5**
Taiwanese-judgment retrieval CLI that packages search hits into a
bundle, then runs a *bundle-level citation check* against the LLM's
answer — i.e. retrieval-only on the local side, BYO-LLM on the user's
side, with structural verification that quoted passages actually exist
in the bundle. The pattern is the unlock: a "retrieve NZLII judgments
locally, package, hand to whichever model the lawyer trusts, verify
citations come back from the bundle" CLI is a ~weekend NZ port.
Python · local-first: yes (retrieval; LLM is BYO)

### [kaicontext/kai](https://github.com/kaicontext/kai) — **fork 2 / spark 4**
Semantic-analysis engine that sits *on top of Git* and emits
"meaningful change" semantic diffs and selective CI plans, language-
aware via call graphs. The transferable idea: treat a contract repo as
git-tracked, and let a kai-style engine surface *which clauses changed
in meaning between v3 and v4 of this lease* — not just textually, but
in terms of obligation structure. Fork the architecture (Go), not the
code.
Go · local-first: yes · why-kept: spark (commit-level
semantic-change tooling is the right model for clause-history review)

## Tangential but interesting

Nothing else cleared the bar this sweep.

## Suggested build stacks (additions to sweep #1's list)

- **Replace the redline engine:** swap sweep-1's `jsdiff` + `adeu`
  for `pandiff` (one tool, broader input formats, native Word
  tracked-change output). For programmatic / non-Word output, swap
  `Python-Redlines` for `Docxodus` (move detection, formatting-only
  detection, .NET *or* WASM).
- **Confidential cloud-LLM use:** drop `ContextSafe` (NZ-adapted) in
  front of any cloud LLM call to give consistent client aliases across
  a matter — the missing pre-flight step.
- **In-Word redline (no separate app):** install `word-ai-redliner` as
  a Word add-in, point it at Ollama.
- **AI-collaborated matter notes:** run `basic-memory` as the
  Markdown-on-disk PKM, give Claude / Cursor MCP access to the matter
  folder, keep plain-text ownership.
- **Personal practice cockpit:** self-host `stella/stella` as the shell
  (Matters / docs / tabular review) and wire the redliner and
  matter-Q&A above it.

## Dropped / also evaluated

Document-comparison / redline:

- `JSv4/react-docxodus-viewer` — folded into the `Docxodus` entry (it
  *is* the Docxodus viewer).
- `surrealdb/dmp` — Rust port of `google/diff-match-patch` (already in
  `_seen` and effectively superseded by `jsdiff` for prose); useful only
  if you specifically want Rust.
- `afnanenayet/diffsitter`, `trailofbits/graphtage` — tree-sitter
  AST diff and tree-like-format semantic diff; both well-known. The
  active legal-prose analogue (`Wilfred/difftastic`) is already in
  `_seen` as a wildcard; these don't add a different angle.
- `pandoc-based prose diff` competitors `loilo/diffr`,
  `HarshK97/diffmantic.nvim`, `simonbs/TextDiffing`, `tombcato/smart-ticker`,
  `cdacamar/gap` — all UI-level diff visualisers; off-direction for a
  redliner.
- `kappapiana/anonymize` — anonymises authorship metadata in ODT / DOCX
  (track-change author lines), not content; useful sometimes, but
  narrower than `ContextSafe`.
- `kipeum86/legal-agent-orchestrator` — Claude-Code-hosted multi-agent
  legal workflow; cloud-first and US-flavoured, fork-fit too low for a
  personal NZ tool. (Same author as the already-shortlisted
  `contract-review-agent`.)
- `agentmail-to/agentmail-examples`, `alexanderatallah/redline`,
  `dejuknow/md-redline`, `rdegges/redline`, `Balchandar/Architect-Studio-X`,
  `jamesaphoenix/diff-core`, `he-yufeng/PromptDiff`, `krfantasy/alsdiff`,
  `roastedroot/chicory-redline`, `andrew/json-schema-diff`,
  `consi/ymldiff` — all use the word "redline" / "semantic diff" for
  unrelated coding / agent / schema / prompt / config / Ableton-set
  workflows; off-domain for legal prose.

Document understanding / parsing:

- `superdoc-dev/superdoc` — real-time collaborative DOCX/PDF editor
  (Harbour-stack); strong, but the editing piece is better served by
  `eigenpal/docx-editor` (which has the MCP + agent SDK).
- `apache/poi` — Java OOXML library; off-stack for vibe-coding (Java).
- `EvotecIT/OfficeIMO` — .NET DOCX/XLSX library; off-stack.
- `onizet/html2openxml` — HTML→OOXML converter; narrow piece.
- `freelawproject/doctor` — document-conversion microservice; off-target
  for personal use.
- `Picovoice/pico-cookbook`, `software-mansion/react-native-executorch`,
  `SakuraMathcraft/LaTeXSnipper`, `D1firehail/AdeptiScanner-GI`,
  `WallBreaker2/op`, `hgmzhn/manga-translator-ui`,
  `bpwhelan/GameSentenceMiner`, `ritesh-1918/HELPDESK.AI`,
  `TaewoooPark/PAIDEIA` — surfaced for "OCR / PDF / docx", but each is
  off-domain (on-device voice / RN AI / math LaTeX / game inventory /
  Win32 screen-OCR / comic translation / Japanese sentence mining /
  helpdesk / exam prep).
- `Zettlr/Zettlr` — Pandoc-aware Markdown publishing workbench; closer
  to a Pandoc writing tool than a legal-prose comparator. Useful for
  drafting research memos, but redundant next to Trilium / Lumina-Note.
- `paperless-ngx/paperless-ngx` — well-known self-hosted document
  management; the right answer if you actually want a *DMS* with OCR
  search, but heavier than a personal-tool scope. Keep on the radar.
- `superdoc-dev/superdoc`, `eigenpal/docx-editor` — overlap; kept the
  one with native MCP / agent SDK.

Legal-domain apps / orchestration:

- `open-agreements/open-agreements` — generates signable DOCX from
  legal-template fills (NDA / SAFE etc.); narrow templates, US-flavoured.
- `saidsurucu/yargi-mcp` — MCP server over Turkish legal databases;
  jurisdiction-specific.
- `TeoMastro/GreekLegislationRag`, `nuuuwan/lk_legal_docs`,
  `Samix2026/saudi-legal-ai-framework`, `FutureRootsDE/legal-audit-de`,
  `hueyy/lacuna-db` — each is a jurisdiction-specific RAG / dataset /
  audit tool (Greece / Sri Lanka / KSA / Germany / Singapore); pattern
  is interesting but the spark slot is already filled by `tw-legal-rag`.
- `LegalRabbit-AI/legalrabbit-docx-claude-plugin`,
  `NEU-ZHA/legal-ai-skills`, `fedec65/bettercallclaude` — Claude
  Cowork / Code plugin bundles; not stand-alone tools to fork.
- `alea-institute/FOLIO` — legal-ontology OWL graph; reference data,
  not personal tooling.
- `param20h/PDF-Assistant-RAG` — generic PDF RAG demo; superseded by
  AnythingLLM (in `_seen`) + `contextgem`.

NZ-tagged:

- `openlawnz/openlawnz-browser-extension` — 2018 stub, 4★, attaches
  OpenLaw NZ data inside `legislation.govt.nz`; barely-maintained, but
  the OpenLaw NZ org is worth following for live NZ caselaw data.
- `digitalaotearoa/legaleligibility` — Gov Zero Aotearoa benefits-
  eligibility expert system; off-domain for property work.
- `AltisLegal/AltisLegal` — Conveyancing Central API resource from 2015;
  dead, but flagged as the only NZ-region conveyancing-API artefact
  surfaced.

PKM / notes (the local-first cluster is now well-saturated by `Trilium`,
`espanso`, `basic-memory`, `Lumina-Note`):

- `memex-lab/memex` — local-first AI journal (timeline / photo / voice
  cards); journaling rather than matter notes.
- `kuku-mom/kuku` — Tauri Markdown workspace with AI + encrypted sync;
  promising but newer / quieter than Lumina-Note.
- `myICOR/myPKA` — Claude-Code-oriented Markdown PKM; methodology-heavy,
  less plug-and-play.
- `egroup-labs/kept` — search/archive AI conversations across providers;
  the chat-history use case is real but narrow.
- `tiddly-gittly/TidGi-Desktop`, `tiddly-gittly/TidGi-Mobile` —
  TiddlyWiki-based; aesthetic mismatch with the rest of the stack.
- `revezone/revezone` — Excalidraw + tldraw + notion-like; superseded
  by sweep #1's `excalidraw/excalidraw` + `Trilium` pairing.
- `liuyingxuvka/Khaos-Brain`, `jshph/enzyme`, `kahz12/Grimore-MD`,
  `sysid/bkmr`, `winstonkoh87/Athena-Public`, `jetyu/NoteWizard`,
  `CLSherrod/crm-markdown` — small / experimental local-first PKM
  variants; none add a new technique over the kept ones.

Excluded as off-domain / search noise:

- `gambiarras/legal-iptv`, `LaQuay/TDTChannels`,
  `Oliveira3d/free-ip-stresser-booter`,
  `techenthusiast167/D4rk_Intel-OSINT-Investigative-Toolkit`,
  `openlibrecommunity/olcrtc` — "legal" used in non-legaltech senses.
- All the PCOS / PCOD / PCOR health-app results that surface against the
  literal `PCO-AI` query (different domain entirely).
- The crack/keygen listings (`Abbyy-Finereader-Crack-*`,
  `Nitro-PDF-Pro-Crack-*`, `Remo-Repair-Crack-*`,
  `Stellar-Data-Recovery-Pro-2026`, `Kernel-File-Repair-Toolkit-Crack-*`,
  `CorelDRAW-Graphics-Suite` prokill-*, `FineReader-Pro-OCR-Edition`,
  `Recuva-Professional-Crack-*`, `prokill-werewolfbb9/*`) — pirated-
  software listings; excluded per routine.
