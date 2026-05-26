# Routine — audio-mir discoveries

Recurring sweep that surfaces newly relevant GitHub repos in audio DSP / MIR / music theory /
music generation for the **ASA** and **Harmonia** projects. One of two streams in this repo
(see `routines/README.md`).

> NOTE: this supersedes two earlier framings. (1) ASA was described as "an in-browser
> Essentia.js library" — that was wrong and biased scoring toward browser/WASM tools; ASA is a
> SERVER-SIDE Python app. (2) Harmonia was described as "a React + Tonal.js chord-progression /
> reharmonization tool" and treated as a discoverable GitHub repo — that was also wrong.
> Harmonia is a single, unpublished local HTML file (vanilla HTML/CSS/JS, zero dependencies;
> hand-rolled music theory + byte-level MIDI writer). There is no `slittycode/harmonia` repo
> (404). The **[Gemini role]** slot below is filled from ASA's own `CLAUDE.md`; Harmonia is
> now described accurately below. When in doubt, treat ASA's own repo and the actual Harmonia
> HTML file as authoritative over this summary.

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
- **Harmonia** — an unpublished, single-file, dependency-free **vanilla HTML/CSS/JS** "Chord
  Progression Studio": hand-rolled music theory (note tables, scale/chord-interval maps, roman
  numerals) and a hand-rolled byte-level MIDI writer — **no React, no Tonal.js, no build, no
  imports**. Features: mood/genre → diatonic progression generation, roman-numeral analysis, SVG
  piano, a **Substitutions** panel (relative minor/major, tritone sub, sus voicings — i.e.
  reharmonization), Web Audio playback, MIDI export. Symbolic-first; one local file, not a repo
  (`github.com/slittycode/harmonia` → 404). Because it has no codebase to "incorporate into" and
  no dependencies to be "stack-compatible with," **discovered repos can only ever be conceptual
  references** (UX ideas, datasets, technique notes) — never code lifts or fork targets.

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

5. Score each 1–5 on relevance to ASA or Harmonia. Drop anything <3. Score against the REAL
   shape of each project:
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
   - **Harmonia is an unpublished, dependency-free, single-file vanilla-JS toy.** It has no
     codebase to incorporate into, no stack to be compatible with, and no consumer beyond its
     author. Score `(H)` purely as **conceptual relevance** to Harmonia's idea space — chord
     progressions, reharmonization, roman numerals, key/scale UI, piano UI, MIDI export, mood/
     genre→progression — and never as stack-fit, "Tonal.js drop-in", "React/Tone.js family", or
     "incorporate into Harmonia's codebase." Don't down-score for being native / C++ / Python /
     Rust either — every Harmonia-relevant repo is reference-only by definition.

6. Append survivors to `discoveries/audio-mir-<YYYY-MM-DD>.md` with sections: ASA-relevant /
   Harmonia-relevant (conceptual) / Both / Tangential but interesting. Two-sentence pitch each,
   link, score.

7. Append surfaced `owner/repo` lines to `_seen.txt`.

8. Commit to branch `claude/discoveries-<YYYY-MM-DD>` and open a PR.

Be direct. Don't pad the pitches. If a repo is a thin wrapper around something I'd already know
about, say so and drop the score. Ignore any licence considerations.
