# Forking / incorporation planning prompt — 2026-05-14

> **Correction (2026-06-09):** The agent prompt below describes Harmonia as "a React
> chord-progression / reharmonization tool built on Tonal.js" and states "Harmonia is
> React + Tonal.js." Both are wrong. Harmonia is a real, unpublished, single-file,
> dependency-free vanilla-JS tool — no React, no Tonal.js, no build. The Harmonia-related
> forking angles in this prompt (stack-fit reasoning, "React + Tonal.js" compatibility
> framing) are therefore inapplicable. Repos tagged for Harmonia remain valid conceptual
> idea references.

A ready-to-paste prompt for a coding agent. It directs the agent to turn
five discoveries into concrete forking / incorporation plans, in the same
shape as `incorporations/asa-2026-05-13.md`.

The five were selected from `discoveries/audio-mir-2026-05-13.md` and
`discoveries/audio-mir-2026-05-14.md`. The existing plan
(`asa-2026-05-13.md`) only covers three ASA tracks from the 05-13 AM pass
and explicitly defers all Harmonia work — so the 05-13 PM pass, the whole
05-14 pass, and every Harmonia candidate are still unplanned. These five
draw from that uncovered ground and none overlaps the three tracks
already planned (openmeters, Partiels, forever-jukebox).

At a glance:

1. **JuzzyDee/audio-analyzer-rs** (5 — ASA + Harmonia) — fork → WASM
   analysis core, or numerical cross-check oracle.
2. **jhartquist/resonators** (4 — ASA) — incorporate the existing WASM
   target as an opt-in DSP backend.
3. **linuxmatters/jivetalking** (4 — ASA) — port the "measure →
   recommend parameters" layer.
4. **ptnghia-j/ChordMiniApp** (5 — Harmonia) — fork-for-reference; opens
   the deferred Harmonia track.
5. **spyroskantarelis/chordonomicon** (4 — Harmonia) — dataset
   incorporation for reharmonization eval.

Everything inside the code block below is the prompt.

```
You are a coding agent working in the `routine-discoveries` repository.
Your task: turn five selected discoveries into five concrete forking /
incorporation plans, and commit them as one markdown file.

### Background

`routine-discoveries` records recurring discovery scans for audio / MIR /
music tooling, each repo scored 1-5 against two in-house projects:

- ASA — an Essentia.js DSP pipeline: mel-spectrograms, tonal balance,
  dynamics, loudness. Library-shaped, runs in-browser (Essentia.js / WASM).
- Harmonia — a React chord-progression / reharmonization tool built on
  Tonal.js.

### Read first, in this order

1. `discoveries/audio-mir-2026-05-13.md` — scan passes one and two (AM + PM).
2. `discoveries/audio-mir-2026-05-14.md` — scan pass three.
3. `incorporations/asa-2026-05-13.md` — the template. Your five plans must
   follow this track structure. It already plans three tracks — openmeters,
   Partiels, forever-jukebox — do not re-cover those.
4. `discoveries/_seen.txt` — the dedup list.

The discovery docs are the source of truth for what each upstream does.
For how to incorporate it, you must open the actual upstream repository
and read its README, license, and public API / schema / dataset surface.

### The five upstreams to plan

1. JuzzyDee/audio-analyzer-rs — score 5 — serves ASA + Harmonia.
   Pure-Rust MCP server that extracts the whole MIR stack (spectral
   centroid / bandwidth / rolloff / flatness, Krumhansl-Schmuckler key
   detection, pitch-class distribution, tonnetz, MFCCs, EBU R128 LUFS /
   true-peak / LRA, crest factor, HPSS, stereo field, section boundaries)
   in under 2 s per track, with no Python or FFmpeg.
   Why selected: the highest-leverage single repo in the discovery set —
   the doc calls it "essentially ASA's entire feature set in one
   dependency-free crate," and its key / pitch-class / tonnetz outputs
   also feed Harmonia.
   Angle to evaluate: fork → compile to WASM as ASA's analysis core,
   versus use it purely as a numerical cross-check oracle for the existing
   Essentia.js pipeline. Resolve which — and whether the Harmonia-facing
   outputs justify a shared core.

2. jhartquist/resonators — score 4 — serves ASA.
   Rust implementation of the Resonate algorithm — a fixed-memory,
   per-sample alternative to FFT / CQT for low-latency spectral analysis —
   shipping Python and WebAssembly bindings.
   Why selected: it already ships a WASM target, making it a rare
   near-drop-in for ASA's in-browser DSP stage, with sharper per-bin
   time-frequency tradeoffs than a stock STFT.
   Angle to evaluate: incorporate the published WASM target as an opt-in
   DSP backend, versus fork to extend it. Cross-reference plan 1 — both
   are Rust → WASM, and ASA shouldn't end up carrying two unrelated Rust
   toolchains if one core can serve both.

3. linuxmatters/jivetalking — score 4 — serves ASA.
   Go CLI that measures a recording's integrated LUFS, true peak, LRA
   (EBU R128), noise floor, and spectral signature, then picks per-pass
   filter parameters from those measurements (adaptive de-essing, gating,
   compression, two-stage R128 normalization).
   Why selected: the doc says its "measure first, then choose parameters"
   pipeline is "exactly what ASA's loudness + dynamics stage should output
   as recommendations." This is the recommendation layer — distinct from
   the measurement layer already covered by openmeters in Track 1 of the
   template.
   Angle to evaluate: port the adaptive-parameter-selection logic (Go →
   ASA's JS / WASM). Decide where its measurement inputs come from —
   openmeters' Track 1 output, or plan 1's analyzer — so this plan
   composes with what's already planned rather than duplicating
   measurement.

4. ptnghia-j/ChordMiniApp — score 5 — serves Harmonia.
   Next.js + Flask app doing chord recognition (Chord-CNN-LSTM,
   BTC-SL/PL), beat tracking (Beat-Transformer + madmom), lyrics, sheet
   rendering via OpenSheetMusicDisplay, and chord-db guitar diagrams.
   Why selected: the doc calls it "the closest public neighbor to
   Harmonia's product surface." The existing incorporation plan explicitly
   deferred all Harmonia work ("separate evaluation, not ASA's problem") —
   this plan opens that track.
   Angle to evaluate: fork-for-reference / UX + architecture
   incorporation. The stacks differ (Next.js + Flask versus React +
   Tonal.js) — go through its UX and architecture choices and classify
   each adopt / adapt / reject.

5. spyroskantarelis/chordonomicon — score 4 — serves Harmonia.
   666K symbolic chord progressions with section labels (verse / chorus /
   bridge), genre, and release date, encoded as single-chord / triad /
   tetrad tokens on Hugging Face, with published RNN / GRU / LSTM
   baselines.
   Why selected: a dataset incorporation — deliberately a different kind
   of plan than the other four — and "a drop-in training / eval set for
   any reharmonization model," giving Harmonia a real benchmark.
   Angle to evaluate: how Harmonia consumes the tokenizations and section
   labels; what an evaluation harness against the published baselines
   looks like; and the licensing / attribution terms of the Hugging Face
   dataset.

Considered but not selected (a bench for later batches): songsee,
EssentiaTD, AudioAuditor, clamp3 (ASA-leaning); rawl, noteDigger,
chromatone.center (Harmonia-leaning). All viable — held back so this batch
stays at five and stays diverse in plan-type. Don't re-litigate the
selection, but if exploration shows one of the five is a dead end, pull
its replacement from here.

### What each plan must contain

Mirror the track structure of `incorporations/asa-2026-05-13.md`:

- Source — URL, language, stars, creation date, and License. Check the
  real repo. If you cannot confirm the license, write "TBD" and make
  confirming it the first checklist item under Definition of done.
- What to lift — specific: code / algorithm / schema / dataset / UX
  patterns. Name modules or files where you can.
- Why — the precise gap in ASA or Harmonia this fills.
- Approach — choose one and justify it with stack-fit reasoning: fork;
  port (lift the math, reimplement on-stack); incorporate as a dependency
  (consume a published WASM / npm / HF artifact); or reference-only. ASA
  is in-browser JS / WASM; Harmonia is React + Tonal.js. A Rust / Go / C++
  upstream almost always means port-the-math or compile-to-WASM — not
  adopt-the-stack.
- Cross-check oracle — if another discovered repo can validate the result
  numerically or structurally, name it (e.g. a second LUFS implementation,
  a second key detector).
- Definition of done — a concrete, testable checklist.
- Risks — honest, including license risk and stack-fit risk.

### Constraints

- Every upstream's license is unconfirmed until you verify it. No plan may
  assume a code lift is permitted — license confirmation is always step
  one.
- Don't copy wholesale. Where a plan adopts an external contract, schema,
  dataset encoding, or UX, classify each piece adopt / adapt / reject with
  a one-line rationale (the discipline used in Track 3 of the template).
- Each plan must be independent — it can be picked up, paused, or dropped
  without blocking the others.
- Dedup against `_seen.txt` and against the three tracks already in
  `asa-2026-05-13.md`.
- Two of the five (audio-analyzer-rs, resonators) are both Rust → WASM
  answers to ASA's in-browser constraint — have those two plans reference
  each other where they overlap.

### Output

- Write one file: `incorporations/forking-plans-2026-05-14.md`.
- One section per upstream, in the structure above, in the order listed.
- Close with a Sequencing section: recommended pickup priority by ROI,
  one line of reasoning each (see the template's closing section).
- Add a Source note pointing back to the discovery docs.
- Commit the file with a descriptive message and open a pull request.

### Scope

Plan only — do not implement any incorporation. The deliverable is the
plan document, exactly as `asa-2026-05-13.md` is a plan and not an
implementation. If, while reading an upstream, you find one of the five is
a dead end (abandoned, unsuitable license, mischaracterized in the
discovery doc), say so in its section and note what you'd pick instead
from the "considered but not selected" bench — don't silently swap it.
```
