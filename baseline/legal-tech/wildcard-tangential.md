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

## Tangential — useful, off the core path

- **fork 4 / spark 4** · local-first:partial · [excalidraw/excalidraw](https://github.com/excalidraw/excalidraw) · `TypeScript` · `124k★` · `maturity:app`
  An embeddable hand-drawn whiteboard component that works offline and autosaves locally (offline PWA / embeddable component, no backend). **Build:** embed it in your Tauri app to sketch chain-of-title, easements, subdivision layouts or settlement timelines — visual matter mapping with everything stored on your machine. _(05-21 · tags: whiteboard, offline-pwa, embeddable, matter-mapping, tangential)_
