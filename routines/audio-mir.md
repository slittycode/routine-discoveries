# Routine — audio-mir discoveries

Recurring sweep that surfaces newly relevant GitHub repos in audio DSP / MIR / music theory /
music generation for the **ASA** and **Harmonia** projects. One of two streams in this repo
(see `routines/README.md`).

> NOTE: this supersedes an earlier framing that described ASA as "an in-browser Essentia.js
> library." That was wrong and biased scoring toward browser/WASM tools. ASA is a SERVER-SIDE
> Python app. The **[Gemini role]** slot below is now filled from ASA's own `CLAUDE.md`.
>
> CORRECTION (2026-05-24): **Harmonia** was previously mis-described here as "a React + Tonal.js
> chord tool" and assumed to be a discoverable GitHub repo. Both were wrong (owner-verified).
> Harmonia is a real but **unpublished, single-file, dependency-free vanilla HTML/CSS/JS** tool;
> it is **not on GitHub** (`github.com/slittycode/harmonia` → 404). With no repo and no
> dependencies, it is a **conceptual reference only** — never a stack-compatibility or
> GitHub-incorporation target (see the Harmonia bullet and the scoring rubric below).

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
- **Harmonia** — a real but **unpublished, single-file, dependency-free** vanilla HTML/CSS/JS
  "Chord Progression Studio" (owner-confirmed 2026-05-24). It hand-rolls its own music theory
  (note tables, scale/chord-interval maps, roman numerals) and its own byte-level MIDI writer:
  mood/genre → diatonic progression generation, roman-numeral analysis, an SVG piano, a chord
  **Substitutions** panel (relative minor/major, tritone sub, sus voicings = reharmonization),
  Web Audio playback, and MIDI export. Symbolic-first. **No React, no Tonal.js, no imports, no
  build**, and **not on GitHub** (`github.com/slittycode/harmonia` → 404 — it is a local file,
  not a repo with a backlog). Because it has no repo and no dependencies, GitHub incorporation /
  stack-compatibility scoring **does not apply**: candidates can only ever be *conceptual*
  references (a UX, algorithm, or dataset idea). *(The earlier "React + Tonal.js, discoverable
  repo" framing was wrong on both counts.)*

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

5. Score each 1–5 on relevance to **ASA** — the scored GitHub-incorporation target. Drop anything
   <3. Score against the REAL stacks:
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
   - **Harmonia is NOT scored on a stack-compatibility / incorporation axis.** It is an
     unpublished, dependency-free single file with no repo, so "stack-compatible" and "incorporate
     into Harmonia's codebase" are meaningless. Flag a candidate as a *Harmonia conceptual
     reference* only when it offers a genuinely transferable **idea** — a reharmonization /
     voice-leading algorithm, a chord-progression dataset, or a UX pattern — never because of its
     stack. (Harmonia is symbolic-first and ingests no audio, so audio→chord/key tools are not
     Harmonia references.)

6. Append survivors to `discoveries/audio-mir-<YYYY-MM-DD>.md` with sections: ASA-relevant /
   Harmonia (conceptual reference) / Both / Tangential but interesting. Two-sentence pitch each,
   link, score. The score is **ASA-relevance**; a Harmonia item carries an idea note, not a
   stack-fit score.

7. Append surfaced `owner/repo` lines to `_seen.txt`.

8. Commit to branch `claude/discoveries-<YYYY-MM-DD>` and open a PR.

Be direct. Don't pad the pitches. If a repo is a thin wrapper around something I'd already know
about, say so and drop the score. Ignore any licence considerations.
