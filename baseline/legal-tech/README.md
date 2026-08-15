# legal-tech — the tech baseline

Tools a **solo NZ property/conveyancing lawyer who vibe-codes** could fork and build from
as **personal** tools (not commercial products). Documents are confidential, so
**local-first / offline** is preferred (local-LLM-capable a plus) — but it's a preference,
not a gate. NZ relevance is a bonus; licence is ignored entirely. He wants both
directly-useful tools and creative seeds. See `../README.md` for the catalog spec.

The thesis from the 05-21 sweep: a complete **local-first contract redliner** assembles
today — `docling` (ingest) → `jsdiff` (sentence diff) → `diff2html` (render), with
`dealfluence/adeu` emitting native Word tracked-changes and `contextgem` doing cited
clause extraction, all wrappable in a `tauri` desktop shell.

## Legend
- **Score = `fork N / spark N`** (each 1–5): **fork** = how readily you could fork it and
  run/extend it as a personal tool; **spark** = whether it teaches a technique or seeds a
  tool you couldn't otherwise build. (This is the legal schema — *not* the music 1–5 scale.)
- **`local-first`** = `yes` (runs fully offline) · `partial` (local core, cloud LLM or
  optional backend) · `no`. A flag, not a gate.
- **`maturity`** = `lib` (import/fork-and-run library) · `app` (runnable application) ·
  `alpha` (early) · `reference` (study-only / academic / notebooks).
- Unknown metadata is omitted, never guessed. Marginal repos (dropped on 05-21 for
  redundancy) are kept with a note on why and what's still mineable. Dead/404 repos live
  in `excluded.md`.

## At-a-glance (every repo)

| repo | sub-domain | lang | fork/spark | maturity |
| --- | --- | --- | --- | --- |
| [dealfluence/adeu](https://github.com/dealfluence/adeu) | comparison-redlining | Python | 5/5 | app |
| [kipeum86/contract-review-agent](https://github.com/kipeum86/contract-review-agent) | comparison-redlining | Python | 4/5 | app |
| [houfu/redlines](https://github.com/houfu/redlines) | comparison-redlining | Python | 5/3 | lib |
| [sen-uni-kn/ContractCheck](https://github.com/sen-uni-kn/ContractCheck) | comparison-redlining | Java | 2/4 | reference |
| [JSv4/Python-Redlines](https://github.com/JSv4/Python-Redlines) | comparison-redlining | Python | 4/4 | lib |
| [google/diff-match-patch](https://github.com/google/diff-match-patch) | comparison-redlining | Python | 3/3 | lib (archived 2024) |
| [evolsb/legal-redline-tools](https://github.com/evolsb/legal-redline-tools) | comparison-redlining | Python | 4/4 | lib |
| [davidar/pandiff](https://github.com/davidar/pandiff) | comparison-redlining | TypeScript | 5/5 | app |
| [JSv4/Docxodus](https://github.com/JSv4/Docxodus) | comparison-redlining | C#/TypeScript | 5/4 | lib |
| [UseJunior/safe-docx](https://github.com/UseJunior/safe-docx) | comparison-redlining | TypeScript | 5/4 | lib |
| [JSv4/react-docxodus-viewer](https://github.com/JSv4/react-docxodus-viewer) | comparison-redlining | TypeScript | 4/3 | lib |
| [yuch85/word-ai-redliner](https://github.com/yuch85/word-ai-redliner) | comparison-redlining | JavaScript | 4/3 | app |
| [yuch85/office-word-diff](https://github.com/yuch85/office-word-diff) | comparison-redlining | JavaScript | 3/4 | lib |
| [AlexAlves87/ContextSafe](https://github.com/AlexAlves87/ContextSafe) | comparison-redlining | Python | 3/5 | app |
| [Mintplex-Labs/anything-llm](https://github.com/Mintplex-Labs/anything-llm) | understanding-rag | JavaScript | 5/4 | app |
| [shcherbak-ai/contextgem](https://github.com/shcherbak-ai/contextgem) | understanding-rag | Python | 5/5 | lib |
| [Open-Source-Legal/OpenContracts](https://github.com/Open-Source-Legal/OpenContracts) | understanding-rag | Python | 4/5 | app |
| [tomasonjo-labs/legal-tech-chat](https://github.com/tomasonjo-labs/legal-tech-chat) | understanding-rag | Jupyter | 3/5 | reference |
| [curiousily/ragbase](https://github.com/curiousily/ragbase) | understanding-rag | Python | 3/3 | reference |
| [run-llama/liteparse](https://github.com/run-llama/liteparse) | understanding-rag | Rust | 5/3 | lib |
| [ocrmypdf/OCRmyPDF](https://github.com/ocrmypdf/OCRmyPDF) | understanding-rag | Python | 5/3 | app |
| [gmickel/gno](https://github.com/gmickel/gno) | understanding-rag | TypeScript | 5/4 | app |
| [Nebutra/MinerU-Skill](https://github.com/Nebutra/MinerU-Skill) | understanding-rag | Python | 4/3 | app |
| [docling-project/docling](https://github.com/docling-project/docling) | foundations | Python | 5/4 | lib |
| [jsvine/pdfplumber](https://github.com/jsvine/pdfplumber) | foundations | Python | 5/3 | lib |
| [bzsanti/oxidizePdf](https://github.com/bzsanti/oxidizePdf) | foundations | Rust | 4/4 | lib |
| [kreuzberg-dev/html-to-markdown](https://github.com/kreuzberg-dev/html-to-markdown) | foundations | Rust-backed | 4/3 | lib |
| [kpdecker/jsdiff](https://github.com/kpdecker/jsdiff) | foundations | JavaScript | 5/4 | lib |
| [rtfpessoa/diff2html](https://github.com/rtfpessoa/diff2html) | foundations | TypeScript | 4/5 | lib |
| [trailofbits/graphtage](https://github.com/trailofbits/graphtage) | foundations | Python | 4/5 | lib |
| [afnanenayet/diffsitter](https://github.com/afnanenayet/diffsitter) | foundations | Rust | 4/4 | app |
| [eigenpal/docx-editor](https://github.com/eigenpal/docx-editor) | foundations | TypeScript | 5/4 | lib |
| [superdoc-dev/superdoc](https://github.com/superdoc-dev/superdoc) | foundations | TypeScript | 5/4 | lib |
| [tauri-apps/tauri](https://github.com/tauri-apps/tauri) | foundations | Rust | 5/3 | lib |
| [charmbracelet/bubbletea](https://github.com/charmbracelet/bubbletea) | foundations | Go | 3/4 | lib |
| [espanso/espanso](https://github.com/espanso/espanso) | productivity | Rust | 5/4 | app |
| [TriliumNext/Trilium](https://github.com/TriliumNext/Trilium) | productivity | TypeScript | 4/4 | app |
| [basicmachines-co/basic-memory](https://github.com/basicmachines-co/basic-memory) | productivity | Python | 5/5 | app |
| [blueberrycongee/Lumina-Note](https://github.com/blueberrycongee/Lumina-Note) | productivity | TypeScript | 4/4 | app |
| [matzalazar/rhizome](https://github.com/matzalazar/rhizome) | productivity | Python | 4/4 | lib |
| [super-productivity/super-productivity](https://github.com/super-productivity/super-productivity) | productivity | TypeScript | 5/3 | app |
| [open-agreements/open-agreements](https://github.com/open-agreements/open-agreements) | productivity | TypeScript | 4/3 | app |
| [stella/stella](https://github.com/stella/stella) | productivity | TypeScript | 5/4 | app |
| [naggie/dstask](https://github.com/naggie/dstask) | productivity | Go | 4/3 | app |
| [usememos/memos](https://github.com/usememos/memos) | productivity | Go | 4/2 | app |
| [nzpco/PCO-AI-Generating-an-Updated-Act](https://github.com/nzpco/PCO-AI-Generating-an-Updated-Act) | nz-legal-content | TypeScript | 3/5 | reference |
| [isaacus-dev/open-australian-legal-corpus-creator](https://github.com/isaacus-dev/open-australian-legal-corpus-creator) | nz-legal-content | Python | 3/4 | lib |
| [russellbrenner/auslaw-mcp](https://github.com/russellbrenner/auslaw-mcp) | nz-legal-content | TypeScript | 5/4 | app |
| [edithatogo/nz-legislation](https://github.com/edithatogo/nz-legislation) | nz-legal-content | TypeScript | 5/3 | app |
| [thecolab-ai/.skills](https://github.com/thecolab-ai/.skills) | nz-legal-content | Python | 3/3 | lib |
| [nzpco/PCO-AI-Chatbot-for-NZL](https://github.com/nzpco/PCO-AI-Chatbot-for-NZL) | nz-legal-content | Python | 3/4 | reference |
| [nzpco/PCO-AI-Classification-of-Legislation](https://github.com/nzpco/PCO-AI-Classification-of-Legislation) | nz-legal-content | Python | — (sibling) | reference |
| [nzpco/PCO-AI-Plain-Language-Recommendations](https://github.com/nzpco/PCO-AI-Plain-Language-Recommendations) | nz-legal-content | TypeScript | 3/4 | reference |
| [Wilfred/difftastic](https://github.com/Wilfred/difftastic) | wildcard-tangential | Rust | 3/5 | app |
| [paulfitz/daff](https://github.com/paulfitz/daff) | wildcard-tangential | Java | 4/5 | lib |
| [aa0101181514/tw-legal-rag](https://github.com/aa0101181514/tw-legal-rag) | wildcard-tangential | Python | 3/5 | app |
| [kaicontext/kai](https://github.com/kaicontext/kai) | wildcard-tangential | Go | 2/4 | app |
| [cool-japan/legalis](https://github.com/cool-japan/legalis) | wildcard-tangential | Rust | 2/5 | lib |
| [Sysmagine/SemanticDiff](https://github.com/Sysmagine/SemanticDiff) | wildcard-tangential | extension | 3/4 | app |
| [Hashevolution/James-RAG-Evol](https://github.com/Hashevolution/James-RAG-Evol) | wildcard-tangential | Python | 3/5 | app |
| [excalidraw/excalidraw](https://github.com/excalidraw/excalidraw) | wildcard-tangential | TypeScript | 4/4 | app |
| [spartypkp/open-source-legislation](https://github.com/spartypkp/open-source-legislation) | excluded | Python | dead | — |
| Ansvar-Systems/newzealand-law-mcp | excluded | — | 404 | — |

## Sub-domain files
- **`document-comparison-redlining.md`** — version/clause/structural diff, contract comparison, and the AI-analysis → Word-markup last mile.
- **`document-understanding-rag.md`** — PDF/DOCX understanding, chat-with-documents (RAG), cited clause/term extraction.
- **`foundations.md`** — build-your-own plumbing: document parsers, diff engines + renderers, desktop/TUI shells.
- **`productivity.md`** — PKM / second-brain, snippets & templates, matter/task tracking.
- **`nz-legal-content.md`** — NZ-specific legislation tooling (PCO) + Commonwealth corpus templates.
- **`wildcard-tangential.md`** — cross-domain pattern transfer (structural & tabular diff) + tangential tools (offline whiteboard).
- **`excluded.md`** — dead / 404 repos, recorded with reason, flagged not-worth-chasing.
