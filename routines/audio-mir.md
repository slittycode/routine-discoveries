# Routine — audio-mir discoveries

Recurring sweep that surfaces newly relevant GitHub repos in audio DSP / MIR /
music theory / music generation / LLM-assisted music tooling for the **ASA**
project. One of two streams in this repo (see `routines/README.md`).

> Framing history: an earlier version called ASA "an in-browser Essentia.js library"
> and scored a second target, "Harmonia." Both were wrong. ASA is a SERVER-SIDE
> Python app (below). **Harmonia is a phantom** — no such repo
> (`github.com/slittycode/harmonia` → 404; confirmed ASA PR #98 / `f8d7add`) — and is
> NOT a scoring target. Repos once scored "Harmonia-relevant" survive only if they
> help ASA (its chord/key stage or its React UI). Historical `(H)` entries are kept in
> `baseline/` and `RECOMMENDATIONS.md` for reference, not re-scored here.

## Project: ASA  (verify against its CLAUDE.md; this copy can drift)

ASA = **Ableton Sonic Analyzer** (`slittycode/ableton-sonic-analyzer`, public). A
local-first **Python 3.11 + FastAPI** backend + **React 19** frontend that answers
"how do I make something that sounds like this?" for **Ableton Live 12** producers.
All audio analysis runs **server-side on native libraries** — NO Essentia.js, NO
client-side/in-browser DSP, NO WASM. Pipeline:

- **Layer 1 — native Essentia 2.1b6:** deterministic measurements (mel/spectral,
  chroma/HPCP, tonal balance, dynamics, EBU R128 loudness/true-peak/LRA, key, chords,
  genre, BPM/beats, structure).
- **Layer 2 — `Demucs` stem separation + `torchcrepe` pitch/melody** (librosa +
  PyTorch already in the stack). **Stem separation and pitch are CURRENT scope, not
  hypothetical.**
- **Phase 2 / Layer 3 — Gemini (LLM):** interprets the Phase-1 JSON into specific,
  measurement-cited **Ableton Live 12 device / parameter / value** recommendations
  (never overrides measured values; large audio via the Gemini Files API). Optional,
  flag-gated (`VITE_ENABLE_PHASE2_GEMINI`); a run completes without it.

ASA is an **application** (REST/API contract, React analysis UI, local SQLite +
hosted worker-queue mode) that already emits a large analysis JSON.

**Read ground truth FIRST.** GitHub MCP here is scoped to `routine-discoveries`, so
read ASA's `CLAUDE.md`/`README.md` via the public web (WebFetch on
`slittycode/ableton-sonic-analyzer`) and treat it as authoritative over this summary.

## Workflow

1. Read `discoveries/_seen.txt` (dedupe list, one `owner/repo` per line; absent =
   empty). This is the audio-mir list — SEPARATE from `_seen-legaltech-nz.txt`; never
   mix.

2. Search GitHub, filtered to created:>2025-01-01 OR pushed in the last ~14 days,
   stars > 20:
   - "essentia" OR "gaia" OR "music information retrieval" OR "essentia models" OR "music audio tagging"  # incl. Essentia ecosystem
   - "mel spectrogram" OR "audio feature extraction"
   - "chord recognition" OR "key detection" OR "audio chord estimation"  # ASA chord/key stage
   - "stem separation" OR "demucs" OR "source separation"                # ASA Layer 2
   - "pitch detection" OR "torchcrepe" OR "beat tracking" OR "tempo"     # ASA Layer 2 / rhythm
   - "loudness" OR "LUFS" OR "EBU R128"
   - "ableton" OR "max for live" OR "ableton mcp"                        # ASA targets Live 12
   - "music generation" OR "symbolic music"                             # Phase-3 audition gen
   - "music" AND ("MCP" OR "LLM" OR "agent")                            # ASA's Gemini layer
   - "audio language model" OR "music understanding"                     # audio-LLM models (e.g. MOSS-Music)
   - "audio analysis" AND ("FastAPI" OR "Celery" OR "worker queue" OR "React")  # ASA app/queue/UI shape

3. Drop any candidate already in `_seen.txt`.

4. For the rest (cap ~10–15; back-to-back sweeps yield little — expect 0–3 net-new,
   don't pad to a cap), pull: description, stars, last commit date, README (~200
   words), primary language.

5. Score each 1–5 on **ASA** relevance. Drop anything <3. Score against the REAL stack:
   - Native C/C++/Rust/Python audio libraries are **first-class** (a Rust crate is a
     PyO3 extension or sidecar; a C++ lib is a native dependency). Do NOT penalise
     "native / not browser-friendly."
   - Native libraries that DON'T bind to a Python backend (Go, C#/.NET, Swift, …) are
     NOT penalised either — score them as algorithm/architecture **references** (cap
     ~4) on their DSP/app design, not as drop-in deps (matches the `maturity: reference`
     convention in `baseline/`).
   - Do NOT award relevance for "in-browser", "WASM", "Essentia.js", or "client-side";
     ignore bundle-size / cold-start. (Past framing error.)
   - The **Essentia ecosystem** (Essentia, gaia, Essentia pretrained models,
     host/wrapper projects as references) is directly relevant.
   - **Layer 2 is current scope:** stem separation (Demucs & forks), pitch/melody
     (torchcrepe & alternatives), and beat/tempo tooling count — not "future."
   - **Ableton is core:** ASA targets Ableton Live 12 and emits Ableton device/param
     recs, so Ableton / Max-for-Live / Ableton-MCP tooling is core ASA relevance, not
     "tangential."
   - **LLM/agent layer:** audio-LLMs, LLM-/agent-driven analysis, natural-language
     music interfaces, MCP servers, and prompt-to-analysis tooling are ASA-relevant.
   - **ASA is an app:** REST/API contract design, React analysis UIs, and
     job/queue/server-deployment patterns count.
   - Chord/key repos score on ASA relevance (they feed ASA's chord/key detection
     stage), flagged `ASA`. **Symbolic / MIDI / score-theory libraries drop regardless
     of language** — a native C++ theory lib is NOT rescued by "native is first-class" —
     unless they directly serve ASA's audio chord/key stage or its React UI. There is
     no Harmonia axis any more.

6. Append survivors to `discoveries/audio-mir-<YYYY-MM-DD>.md`, sections:
   **ASA-relevant** / **Tangential but interesting**, plus a **Dropped** list with
   one-line reasons. Two-sentence pitch each, with link, score, and flag — `ASA` or
   `tang` only (the `(H)` and `Both` flags are retired; a chord/key repo that helps ASA
   is flagged `ASA`).

7. Append every surfaced `owner/repo` line (survivors AND drops) to `_seen.txt`.

8. Commit to branch `claude/discoveries-<YYYY-MM-DD>` and open a PR into `main`. Fold
   each ≥3 survivor into `RECOMMENDATIONS.md` and add every non-trash repo to the
   matching `baseline/music-asa/` sub-domain file (essentia-mir · loudness-dynamics-dsp
   · stem-separation · pitch-beat-tempo · chord-key · ableton-mcp-daw ·
   llm-music-generation · apps-architecture · symbolic-theory · excluded).

Be direct. Don't pad pitches. If a repo is a thin wrapper around something already
known (or already in `_seen.txt`), say so and drop it. Ignore licence considerations.
