# Routine — audio-mir discoveries

Recurring sweep that surfaces newly relevant GitHub repos in audio DSP / MIR / music theory /
music generation for the **ASA** and **Harmonia** projects. One of two streams in this repo
(see `routines/README.md`).

> NOTE: this supersedes an earlier framing that described ASA as "an in-browser Essentia.js
> library." That was wrong and biased scoring toward browser/WASM tools. ASA is a SERVER-SIDE
> Python app. The **[Gemini role]** slot below is now filled from ASA's own `CLAUDE.md`.
>
> NOTE (Harmonia corrected 2026-05-25): earlier versions of this routine described Harmonia as
> "a React chord-progression / reharmonization tool on Tonal.js" and treated it as a discoverable
> GitHub sibling to score candidates against. Both were wrong. The owner verified the real artifact
> directly: Harmonia is a **real but unpublished, single local HTML file** — vanilla HTML/CSS/JS
> with **zero dependencies** (no React, no Tonal.js, no build). It is **not on GitHub**
> (`github.com/slittycode/harmonia` → 404) and has no `CLAUDE.md` to verify against. Because it has
> no repo and no dependencies, GitHub "incorporation" / stack-compatibility scoring does not apply;
> candidates can only ever be **conceptual references** (UX or dataset ideas). Harmonia is therefore
> **demoted from a scored discovery target to a conceptual-reference axis** — see Projects and step 5.
> **Owner decision flagged:** confirm whether Harmonia should remain even a conceptual axis here or
> be dropped from this routine entirely (it is an unpublished personal toy with no backlog).

## Projects (verify against each repo's CLAUDE.md; this is a convenience copy)
- **ASA** — a SERVER-SIDE Python (FastAPI) backend + React frontend application. Audio analysis
  runs server-side via native libraries (Essentia primary, plus librosa, torchcrepe, Demucs) and
  Gemini (LLM) for **Phase 2 interpretation (Layer 3)** — turning the deterministic Phase 1 DSP
  measurements into specific, measurement-cited Ableton Live 12 device/parameter/value
  recommendations, never overriding the measured values (Phase 1 is ground truth; every
  recommendation cites the measurement(s) that justify it). Phase 2 is optional and flag-gated
  (`VITE_ENABLE_PHASE2_GEMINI`); a run completes without it. It already emits a large analysis
  JSON (spectral features, chroma/HPCP, key, chords, genre, EBU R128 loudness/true-peak/LRA,
  BPM/beats/rhythm, structure, stems, melody). It is an APP, not a library: NO Essentia.js, NO
  client-side/in-browser DSP, NO WASM. PyTorch is already in the stack.
- **Harmonia** — a **real but unpublished, single-file** chord-progression / reharmonization tool:
  **vanilla HTML/CSS/JS with zero dependencies**. It hand-rolls its own music theory (note tables,
  scale/chord-interval maps, roman numerals) and its own byte-level MIDI writer — **no React, no
  Tonal.js, no imports, no build**. Features: mood/genre → diatonic progression generation,
  roman-numeral analysis, an SVG piano, a chord **Substitutions** panel (relative minor/major,
  tritone sub, sus voicings — i.e. reharmonization), Web Audio playback, and MIDI export.
  Symbolic-first (not audio-first). It is **not on GitHub** (`github.com/slittycode/harmonia` → 404)
  — no repo, no dependencies, no backlog. Consequence for scoring: there is no codebase to fork into
  and no stack to be "compatible" with, so Harmonia is **not a scored incorporation target** —
  candidates relate to it only as **conceptual references** (a UX idea, or a dataset/algorithm idea
  for whoever later works on the file).

## Workflow

1. Read `discoveries/_seen.txt` (dedupe list, one `owner/repo` per line; absent = empty). SEPARATE
   from the legaltech-nz stream's `_seen-legaltech-nz.txt` — never mix.

2. Search GitHub, filtered to created:>2025-01-01 OR pushed in the last ~14 days, stars > 20:
   - "essentia" OR "music information retrieval"
   - "mel spectrogram" OR "audio feature extraction"
   - "chord progression" OR "music theory" language:JavaScript OR TypeScript
   - "stem separation" OR "demucs" OR "source separation"
   - "loudness" OR "LUFS" OR "EBU R128"
   - "ableton" OR "max for live" with code activity
   - "music generation" OR "symbolic music"
   - "music" AND ("MCP" OR "LLM" OR "agent")   # ASA has a Gemini layer

3. Drop any candidate already in `_seen.txt`.

4. For the rest (cap at 15), pull: description, stars, last commit date, README (~200 words),
   primary language.

5. Score each 1–5 on **ASA-incorporation relevance** (drop anything <3). Harmonia is **not scored**:
   instead, tag a candidate `H-ref` if it is a useful **conceptual reference** for Harmonia (chord /
   progression / reharmonization / theory-UX or dataset ideas). Score ASA against the REAL stack:
   - ASA runs server-side on NATIVE Essentia (Python/C++). Native C/C++/Rust/Python audio
     libraries are FIRST-CLASS (a Rust crate is a PyO3 extension or sidecar; a C++ lib is a native
     dependency). Do NOT penalise "native / not browser-friendly."
   - Do NOT award relevance for "in-browser", "WASM", "Essentia.js", or "client-side", and ignore
     bundle-size / cold-start — these are irrelevant to ASA and were a past framing error.
   - The Essentia ecosystem (Essentia, gaia, Essentia models, host/wrapper references) is directly
     relevant to ASA.
   - ASA has a Gemini/LLM layer: LLM-/agent-driven analysis, natural-language music interfaces, MCP
     servers, and prompt-to-analysis tooling are genuinely ASA-relevant — NOT merely "tangential".
   - ASA is an application: REST/API contract design, React analysis UIs, and job/queue patterns
     count.
   - Harmonia has no repo and no dependencies — do NOT score stack-fit or "incorporate into
     Harmonia's codebase." Only mark `H-ref` for conceptual relevance (idea-mining), never as a
     fork or dependency target.

6. Append survivors to `discoveries/audio-mir-<YYYY-MM-DD>.md` with sections: ASA-relevant /
   Harmonia conceptual references (idea-mining only) / Tangential but interesting. Two-sentence
   pitch each, link, and ASA score (`H-ref` items carry a conceptual note, not a 1–5 stack score).

7. Append surfaced `owner/repo` lines to `_seen.txt`.

8. Commit to branch `claude/discoveries-<YYYY-MM-DD>` and open a PR.

Be direct. Don't pad the pitches. If a repo is a thin wrapper around something I'd already know
about, say so and drop the score. Ignore any licence considerations.
