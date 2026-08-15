# legal-tech / document-comparison & redlining

Version / clause / structural diff, contract comparison, and the "AI analysis → Word
markup" last mile — the routine's flagship bucket. Substantive legal *meaning*, not
formatting. Scores are **fork N / spark N** plus a `local-first:` flag (see
`../README.md`). Provenance: `discoveries/legaltech-nz-2026-05-21.md`.

The headline: a complete local-first redliner assembles today — `docling` (ingest) →
`jsdiff` (sentence diff) → `diff2html` (render), with `dealfluence/adeu` emitting native
Word tracked-changes (see `foundations.md` for the engine half).

## Strong — fork-and-run

- **fork 5 / spark 5** · local-first:yes · [dealfluence/adeu](https://github.com/dealfluence/adeu) · `Python` · `82★` · `maturity:app`
  Flattens a Word doc to Markdown so a model can edit the *substance*, then projects the edits back as native Word Track Changes — cleanly separating meaning from formatting (Python + Node implementations). **Build:** the output layer of your legal-impact comparator — a local model decides what should change, adeu emits the redlined `.docx` clients already know how to read. _(05-21 · tags: docx, ooxml, tracked-changes, redline, mcp)_
- **fork 4 / spark 5** · local-first:partial · [kipeum86/contract-review-agent](https://github.com/kipeum86/contract-review-agent) · `Python` · `34★` · `maturity:app`
  A local-first agent that compares a counterparty draft against your house templates and emits a Word file with tracked-change redlines, internal-vs-external margin comments, and negotiation points — the closest thing to the flagship goal already built (file processing stays local; cloud LLM by default). **Build:** fork it and swap its Claude API call for a local model (Ollama) to go fully offline. _(05-21 · tags: contract-review, redline, templates, agent, ollama-swap)_
- **fork 5 / spark 3** · local-first:yes · [houfu/redlines](https://github.com/houfu/redlines) · `Python` · `157★` · `maturity:lib`
  A small, dependable library that turns two texts into Word-style strike-through/insert markup (HTML, Markdown, JSON, terminal) with change statistics. **Build:** the lightweight *display* primitive once your model has identified the substantive deltas. _(05-21 · tags: diff, markdown, display-primitive, change-stats)_
- **fork 5 / spark 5** · local-first:yes · [davidar/pandiff](https://github.com/davidar/pandiff) · `TypeScript` · `maturity:app`
  Pandoc-powered semantic prose diff that ingests anything Pandoc can read (DOCX, PDF, Markdown, HTML, LaTeX, ODT) and writes CriticMarkup, HTML, PDF-via-LaTeX, or DOCX with native Track Changes — already the universal "diff two contracts, emit a Word redline" tool. **Build:** fork it as the engine and skin a Tauri/web UI over it. _(05-27 · tags: pandoc, docx, tracked-changes, universal-diff, cli)_
- **fork 5 / spark 4** · local-first:yes · [JSv4/Docxodus](https://github.com/JSv4/Docxodus) · `C#/TypeScript` · `maturity:lib`
  OpenXML SDK on .NET 8 with WmlComparer-based redlining including move detection and formatting-only-change detection, plus bidirectional DOCX↔HTML conversion, markdown projection for LLM pipelines, a `DocxSession` stateful editor, and distribution as a WASM npm package. The strongest native-grade tracked-changes pipeline you can run without Word installed. **Build:** pair with pandiff (or as adeu's successor) at the output stage. _(05-27, rescored 06-03-v2 · tags: openxml, wmlcomparer, move-detection, wasm, dotnet)_
- **fork 5 / spark 4** · local-first:yes · [UseJunior/safe-docx](https://github.com/UseJunior/safe-docx) · `TypeScript` · `maturity:lib`
  Suite of `docx-primitives` plus a deterministic `docx-comparison` engine (optional MCP wrapper), running entirely locally: surgical text replacement, comment/footnote workflows and revision extraction as structured JSON, ECMA-376 conformant. The cleanest no-AI base for a compare-and-revise tool. **Build:** fork the comparison engine, ignore the MCP layer. _(06-03-v2 · tags: docx, deterministic, comparison-engine, ecma-376, no-ai)_
- **fork 4 / spark 3** · local-first:yes · [JSv4/react-docxodus-viewer](https://github.com/JSv4/react-docxodus-viewer) · `TypeScript` · `maturity:lib`
  Client-side React component that renders DOCX and redlines in the browser via the Docxodus WASM library — no server round-trip, so document content never leaves the machine. **Build:** pair with Docxodus for a complete local-first compare-and-review UI. _(06-03 · tags: react, wasm, docx-viewer, client-side, docxodus-companion)_
- **fork 4 / spark 3** · local-first:yes · [yuch85/word-ai-redliner](https://github.com/yuch85/word-ai-redliner) · `JavaScript` · `maturity:app` · reframed 06-03-v2
  MS Word add-in that applies AI edits back into the document as tracked changes, connecting to local Ollama/vLLM, using the companion `office-word-diff` library's structure-aware diff (token-map → sentence → block fallback). Kept for the **deterministic** diff library it ships; the AI add-in is the reference demo, not the headline (rescored down from 05-27's fork4/spark5 and 06-03-v1's fork5/spark4 once the routine reweighted toward deterministic substance). **Build:** mine the diff library for precise, formatting-preserving DOCX edits; the AI layer is optional. _(05-27, reframed 06-03-v2 · tags: word-addin, ollama, structure-aware-diff, deterministic-core, reframed)_

## Spark-only — kept for the angle

- **fork 2 / spark 4** · local-first:yes · [sen-uni-kn/ContractCheck](https://github.com/sen-uni-kn/ContractCheck) · `Java` · `6★` · `maturity:reference`
  An academic tool that formalises a contract's clause preconditions into first-order logic and runs an SMT solver to find internal contradictions and unexecutable clauses. _(why-kept: spark — single-document consistency is a rare, on-point angle.)_ **Build:** mine the *modelling approach* (not the Java) for a logic-level consistency linter that flags defined-term conflicts and clauses that can never both hold. _(05-21 · tags: smt, first-order-logic, consistency, single-doc, academic)_
- **fork 3 / spark 4** · local-first:yes · [yuch85/office-word-diff](https://github.com/yuch85/office-word-diff) · `JavaScript` · `maturity:lib`
  The structure-aware Word-diff library that powers word-ai-redliner, broken out for reuse: token-map → sentence-diff → block-replace fallbacks, formatting-preserving, Office.js-based. **Build:** lift into other Word-add-in experiments without adopting the full redliner UI. _(05-27 · tags: word-diff, office-js, structure-aware, standalone-lib)_
- **fork 3 / spark 5** · local-first:yes · [AlexAlves87/ContextSafe](https://github.com/AlexAlves87/ContextSafe) · `Python` · `maturity:app`
  100% local PII detection + redaction for PDFs/DOCX/images, with cross-document consistency ("same person always gets the same alias within a project") and three modes: masking, consistent pseudonyms, synthetic-with-invalid-checksums data. Spanish-leaning entity set today, but the architecture is the gold. _(why-kept: spark — the consistent-alias technique is the missing piece for sane cloud-LLM use in an NZ practice.)_ **Build:** an NZ adaptation (IRD numbers, NZBNs, Land Titles references, parcel IDs) as a pre-flight step before any cloud-LLM call. _(05-27 · tags: pii-redaction, consistent-alias, pre-flight, cloud-llm-safety)_

## Marginal — kept with a note (dropped on 05-21 for redundancy/overlap)

- **fork 4 / spark 4** · local-first:yes · [JSv4/Python-Redlines](https://github.com/JSv4/Python-Redlines) · `Python` · `108★` · `maturity:lib`
  True Word-grade `.docx` tracked changes via the OpenXML WmlComparer; a solid baseline. Dropped 05-21 as overlapping adeu and adding a .NET dependency, but kept here: it is the canonical OpenXML tracked-changes generator. **Build:** the `.docx` tracked-changes emitter if you want OOXML-native diffing instead of adeu's Markdown round-trip. _(05-21 · tags: docx, ooxml, wmlcomparer, tracked-changes, dotnet-dep)_
- **fork 3 / spark 3** · local-first:yes · [google/diff-match-patch](https://github.com/google/diff-match-patch) · `Python` · `8.1k★` · `maturity:lib` · ⚠ archived 2024
  Battle-tested, multi-language fuzzy diff/patch/match — the canonical char-level diff. Dropped 05-21 (jsdiff covers prose granularity better) and the repo was **archived 2024**, but kept as a reference: it is the textbook fuzzy diff/patch implementation. **Build:** back-pocket fuzzy patch/match logic (relocating an edit after surrounding text moved) that jsdiff doesn't offer. _(05-21 · tags: diff, patch, fuzzy-match, canonical, archived-2024)_
- **fork 4 / spark 4** · local-first:yes · [evolsb/legal-redline-tools](https://github.com/evolsb/legal-redline-tools) · `Python` · `29★` · `maturity:lib`
  Tiny but the most literally on-point: generates real tracked-changes `.docx` + redline PDFs from JSON edits — the exact deliverables lawyers send. Dropped 05-21 only for overlap with the adeu/Python-Redlines cluster. **Build:** the "AI analysis (JSON edits) → Word markup + redline PDF" last mile, bolted onto your model's output. _(05-21 · tags: docx, redline-pdf, json-edits, tracked-changes, last-mile)_
