# baseline — the tech baseline

A categorized catalog of **every repo ever surfaced** by this repo's discovery sweeps — even the
barely-mentioned and the previously-dropped — recorded with honest, idea-oriented commentary. The
point is forward use: when you have a product idea, point opus at the relevant file(s) here and ask
it to find repos / techniques to **fork or build from**. This is the research-done-in-advance layer.

## How to use it
- Each category has an `<category>/README.md` opening with an **at-a-glance table** (repo · sub-domain ·
  lang · score · maturity). Scan that first, then open only the relevant sub-domain file.
- Example asks: *"scan `baseline/music-asa/chord-key.md` for a local chord/key detector I could fork"*,
  *"scan `baseline/legal-tech/` for a local-first document-diff foundation"*.

## Categories
- **`music-asa/`** — audio / MIR / music-theory / music-gen repos (the ASA + Harmonia streams).
- **`legal-tech/`** — tools a solo NZ property lawyer who vibe-codes could fork and build from.

## Inclusion bar
Record **everything that isn't complete trash.** Repos previously dropped for *redundancy/overlap*
are kept, with commentary saying why they're marginal and what's still mineable. Only **dead /
404 / nonexistent** repos (and a few hard off-domain ones) are shunted to each category's
`excluded.md` — still recorded, so the catalog is complete, but flagged not-worth-chasing.

## Entry format
```
- **<score/flags>** · [owner/repo](https://github.com/owner/repo) · `lang` · `N★` · `active:YYYY-MM` · `maturity:lib|app|model|alpha|reference`
  <what it is — 1 dense line: concrete features>. **Mine:** <what you'd fork / learn / build from it>. _(surfaced MM-DD · ★<plan-ref> · tags: a, b, c)_
```
- **Score schema is per stream** (not unified): music = **1–5 relevance** to ASA/Harmonia plus a flag
  (`ASA` / `H` / `Both` / `tang`); legal = **`fork N / spark N`** plus a `local-first:` flag.
- `maturity` answers fork-and-run vs study-only. Unknown metadata fields are omitted, never guessed.
- Cross-domain repos get a full entry in their primary sub-domain file and a one-line stub-with-link
  in the secondary file, so they're findable from both.

## Framing (authoritative — supersedes older docs)
- **ASA** = `ableton-sonic-analyzer`: a **server-side Python/FastAPI** app (React frontend) running
  **native** Essentia + librosa + torchcrepe + Demucs (PyTorch in-stack) and a **Gemini Phase-2**
  layer that maps the deterministic analysis JSON to Ableton Live 12 device/parameter
  recommendations. It is **not** in-browser / WASM / Essentia.js — native C/C++/Rust/Python is
  first-class. (Authoritative: `routines/audio-mir.md`. The old "Essentia.js" wording elsewhere is wrong.)
- **Harmonia** = a **real, unpublished, single-file** vanilla-JS chord/reharmonization tool:
  mood/genre → diatonic progressions, roman-numeral analysis, SVG piano, substitutions panel
  (relative minor/major, tritone sub, sus voicings), Web Audio playback, MIDI export. No React,
  no Tonal.js, no dependencies, no build, no GitHub repo (`github.com/slittycode/harmonia` →
  404). Earlier sweeps mis-described it as "React + Tonal.js"; ASA PR #98 / `f8d7add` confirmed
  the 404 but overshot by calling it a "phantom / does not exist" — it exists, it's just
  unpublished. Repos formerly scored "Harmonia-relevant" are kept as **conceptual chord /
  theory / UX idea references** — mineable for inspiration, not validated for stack-fit.

## Provenance
Per-repo write-ups originate in the dated sweeps under `discoveries/` and the consolidated
`RECOMMENDATIONS.md`; each entry tags its surfacing date(s). The dated sweeps remain the immutable
record — this catalog condenses and re-frames, it doesn't replace them. `★` marks a repo that also
has an `incorporations/` fork/port plan.
