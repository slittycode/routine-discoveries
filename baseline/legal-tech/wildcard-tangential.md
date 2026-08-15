# legal-tech / wildcard & tangential

Clever apps from OTHER domains whose pattern transfers to legal work (wildcard), plus
genuinely tangential-but-useful tools. Scores are **fork N / spark N** plus a
`local-first:` flag (see `../README.md`). Provenance:
`discoveries/legaltech-nz-2026-05-21.md`.

## Wildcard — cross-domain pattern transfer

- **fork 3 / spark 5** · local-first:yes · [Wilfred/difftastic](https://github.com/Wilfred/difftastic) · `Rust` · `25.4k★` · `maturity:app`
  A structure-aware (syntax-tree) diff for *code* that ignores reflowed whitespace and shows only real changes — the pattern transfers directly to contracts, where renumbering and reflow hide the true edits. **Build:** pair it with a Markdown/tree-sitter grammar to build a clause-level redliner far cleaner than Word's character compare. _(05-21 · tags: structural-diff, tree-sitter, code-to-prose, clause-level, wildcard)_
- **fork 4 / spark 5** · local-first:yes · [paulfitz/daff](https://github.com/paulfitz/daff) · `Java` · `905★` · `maturity:lib`
  Cell-level diff for tabular/CSV data with a visual highlight format, with bindings across many languages (JS/Python/Java…). **Build:** repurpose it for settlement statements, trust-ledger schedules, or rates apportionments — a "what changed between two versions of this financial schedule?" viewer that points at the exact cell, not just the row. _(05-21 · tags: tabular-diff, csv, cell-level, financial-schedules, wildcard)_
- **fork 3 / spark 5** · local-first:yes (retrieval; LLM is BYO) · [aa0101181514/tw-legal-rag](https://github.com/aa0101181514/tw-legal-rag) · `Python` · `maturity:app`
  Taiwanese-judgment retrieval CLI that packages search hits into a bundle, then runs a bundle-level citation check against the LLM's answer — retrieval-only on the local side, BYO-LLM on the user's side, with structural verification that quoted passages actually exist in the bundle. **Build:** a "retrieve NZLII judgments locally, package, hand to whichever model you trust, verify citations come back from the bundle" CLI is a ~weekend NZ port. _(05-27 · tags: retrieval, citation-verification, byo-llm, nzlii-portable, wildcard)_
- **fork 2 / spark 4** · local-first:yes · [kaicontext/kai](https://github.com/kaicontext/kai) · `Go` · `maturity:app` · why-kept: spark
  Semantic-analysis engine that sits on top of Git and emits "meaningful change" semantic diffs and selective CI plans, language-aware via call graphs. **Build:** treat a contract repo as git-tracked, and let a kai-style engine surface *which clauses changed in meaning between v3 and v4 of this lease* — not just textually, but in terms of obligation structure. Fork the architecture, not the code. _(05-27 · tags: git-native, semantic-diff, obligation-structure, call-graphs, wildcard)_
- **fork 2 / spark 5** · local-first:yes · [cool-japan/legalis](https://github.com/cool-japan/legalis) · `Rust` · `maturity:lib` · why-kept: spark
  Production-grade Rust framework (76 crates, ~1M LOC) that compiles natural-language statutes into machine-verifiable code while architecturally separating deterministic logic (age thresholds, deadlines, income limits) from judicial discretion via a `LegalResult<T>` enum — explicitly LLM-free. **Build:** mine its modelling approach for a small clause-logic checker that flags the computable obligations and deadlines in a deed and marks the genuinely discretionary terms for human judgement. _(06-03, rescored 06-03-v2 · tags: statute-compiler, deterministic-vs-discretion, rust, llm-free, wildcard)_
- **fork 3 / spark 4** · local-first:partial · [Sysmagine/SemanticDiff](https://github.com/Sysmagine/SemanticDiff) · `extension` · `maturity:app` · why-kept: spark
  Programming-language-aware diff with a side-by-side review UI for VS Code/GitHub — the textbook "code-review UI repurposed for prose" wildcard. **Build:** mine its change-classification + review-UI approach to build a clause-change reviewer that hides cosmetic edits and foregrounds substantive ones in a redline. _(06-03-v2 · tags: code-review-ui, change-classification, vs-code, wildcard)_
- **fork 3 / spark 5** · local-first:yes · [Hashevolution/James-RAG-Evol](https://github.com/Hashevolution/James-RAG-Evol) · `Python` · `maturity:app` · why-kept: spark
  Local-first (Ollama) replayable Graph-RAG with an append-only audit log and — crucially — an LLM-free deterministic 4-rule contradiction-arbitration decision tree. **Build:** fork that arbitration engine to build a single-document consistency checker that flags contradictory defined terms, conflicting dates and broken cross-references across a long agreement — deterministically, not by asking an LLM to "spot contradictions." _(06-03, rescored 06-03-v2 · tags: graph-rag, contradiction-arbitration, deterministic, audit-log, wildcard)_

## Tangential — useful, off the core path

- **fork 4 / spark 4** · local-first:partial · [excalidraw/excalidraw](https://github.com/excalidraw/excalidraw) · `TypeScript` · `124k★` · `maturity:app`
  An embeddable hand-drawn whiteboard component that works offline and autosaves locally (offline PWA / embeddable component, no backend). **Build:** embed it in your Tauri app to sketch chain-of-title, easements, subdivision layouts or settlement timelines — visual matter mapping with everything stored on your machine. _(05-21 · tags: whiteboard, offline-pwa, embeddable, matter-mapping, tangential)_
