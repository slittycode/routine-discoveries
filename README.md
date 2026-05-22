# routine-discoveries

Recurring discovery scans for audio/MIR/music tooling.

## Scoring

Sweeps score candidates 1–5 against relevance to **ASA**
(`ableton-sonic-analyzer` — Essentia.js DSP pipeline: mel-spectrograms,
tonal balance, dynamics, loudness). Anything below 3 is dropped.

> **Retired axis (2026-05-22):** earlier sweeps also scored against a second
> target, "Harmonia" (a claimed React/Tonal.js chord-progression/
> reharmonization sibling of ASA). It was verified to be a phantom — no such
> project exists (`github.com/slittycode/harmonia` → 404; full record in ASA
> PR #98 / commit `f8d7add`). Scoring is **ASA-only** from this point. The
> dated sweep docs keep their original scores with inline correction notes.
