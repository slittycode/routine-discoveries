# routine-discoveries

A hub for recurring GitHub discovery sweeps. Each **stream** routinely surfaces and vets repos for
a different purpose; results land on `main` as the single source of truth.

## Streams

- **audio-mir** — audio / MIR / music-theory tooling for the **ASA** and **Harmonia** projects.
  - sweeps: `discoveries/audio-mir-<date>.md` · dedupe: `discoveries/_seen.txt` · shortlist:
    `RECOMMENDATIONS.md` · routine: `routines/audio-mir.md`
- **legaltech-nz** — personal tools a NZ property lawyer (who "vibe-codes") could **fork and build
  from**: document comparison / legal-impact, document understanding, personal productivity, and
  build-your-own-tool foundations. Local-first preferred; licence ignored.
  - sweeps: `discoveries/legaltech-nz-<date>.md` · dedupe: `discoveries/_seen-legaltech-nz.txt` ·
    routine: `routines/legaltech-nz.md`
- **mac-gaming** — tools to run, mod, measure, or tune games on an Apple Silicon Mac (CrossOver/GPTK
  and translation layers, bottle/mod managers, frame/power/latency/display measurement, Rosetta,
  Parallels). Licence ignored.
  - sweeps: `discoveries/mac-gaming-<date>.md` · dedupe: `discoveries/_seen-mac-gaming.txt` ·
    shortlist: `FINDS.md` · routine: `routines/mac-gaming.md`

## Layout

- **`routines/`** — the routine prompt for each stream (the registry of what runs).
- **`discoveries/`** — raw per-sweep vetting records: one dated file per scan with scores and why
  candidates were dropped. Each stream keeps its own `_seen` dedupe list.
- **`RECOMMENDATIONS.md`** — consolidated shortlist for the audio-mir stream (a legaltech-nz one
  will follow once several sweeps accrue).
- **`incorporations/`** — plans for lifting selected discoveries into downstream projects.
- **`baseline/`** — the comprehensive **tech baseline**: every non-trash repo ever surfaced,
  categorized (`music-asa/`, `legal-tech/`) with idea-mining ("what to fork/build") commentary —
  scan it when starting a new project. Broader than `RECOMMENDATIONS.md` (the ≥3 shortlist).

`main` is the single source of truth.
