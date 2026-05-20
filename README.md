# routine-discoveries

Recurring discovery scans for audio/MIR/music tooling, scored against two
projects: **ASA** (Essentia.js DSP pipeline) and **Harmonia** (Tonal.js
chord-progression / reharmonization).

## Layout

- **[`RECOMMENDATIONS.md`](RECOMMENDATIONS.md)** — the consolidated,
  deduped shortlist across every sweep. Start here.
- **`discoveries/`** — the raw per-sweep vetting record: one dated file
  per scan with full write-ups, 1–5 scores, and why candidates were
  dropped. `_seen.txt` is the master de-dup list of everything evaluated.
- **`incorporations/`** — plans for actually lifting selected discoveries
  into the downstream projects.

`main` is the single source of truth: discoveries, the vetting balance
behind each, and the recommendation list all live here.
