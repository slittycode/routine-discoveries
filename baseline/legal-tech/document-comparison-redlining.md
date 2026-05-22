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

## Spark-only — kept for the angle

- **fork 2 / spark 4** · local-first:yes · [sen-uni-kn/ContractCheck](https://github.com/sen-uni-kn/ContractCheck) · `Java` · `6★` · `maturity:reference`
  An academic tool that formalises a contract's clause preconditions into first-order logic and runs an SMT solver to find internal contradictions and unexecutable clauses. _(why-kept: spark — single-document consistency is a rare, on-point angle.)_ **Build:** mine the *modelling approach* (not the Java) for a logic-level consistency linter that flags defined-term conflicts and clauses that can never both hold. _(05-21 · tags: smt, first-order-logic, consistency, single-doc, academic)_

## Marginal — kept with a note (dropped on 05-21 for redundancy/overlap)

- **fork 4 / spark 4** · local-first:yes · [JSv4/Python-Redlines](https://github.com/JSv4/Python-Redlines) · `Python` · `108★` · `maturity:lib`
  True Word-grade `.docx` tracked changes via the OpenXML WmlComparer; a solid baseline. Dropped 05-21 as overlapping adeu and adding a .NET dependency, but kept here: it is the canonical OpenXML tracked-changes generator. **Build:** the `.docx` tracked-changes emitter if you want OOXML-native diffing instead of adeu's Markdown round-trip. _(05-21 · tags: docx, ooxml, wmlcomparer, tracked-changes, dotnet-dep)_
- **fork 3 / spark 3** · local-first:yes · [google/diff-match-patch](https://github.com/google/diff-match-patch) · `Python` · `8.1k★` · `maturity:lib` · ⚠ archived 2024
  Battle-tested, multi-language fuzzy diff/patch/match — the canonical char-level diff. Dropped 05-21 (jsdiff covers prose granularity better) and the repo was **archived 2024**, but kept as a reference: it is the textbook fuzzy diff/patch implementation. **Build:** back-pocket fuzzy patch/match logic (relocating an edit after surrounding text moved) that jsdiff doesn't offer. _(05-21 · tags: diff, patch, fuzzy-match, canonical, archived-2024)_
- **fork 4 / spark 4** · local-first:yes · [evolsb/legal-redline-tools](https://github.com/evolsb/legal-redline-tools) · `Python` · `29★` · `maturity:lib`
  Tiny but the most literally on-point: generates real tracked-changes `.docx` + redline PDFs from JSON edits — the exact deliverables lawyers send. Dropped 05-21 only for overlap with the adeu/Python-Redlines cluster. **Build:** the "AI analysis (JSON edits) → Word markup + redline PDF" last mile, bolted onto your model's output. _(05-21 · tags: docx, redline-pdf, json-edits, tracked-changes, last-mile)_
