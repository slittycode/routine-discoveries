# Routine — audio-mir discoveries

Recurring sweep that surfaces newly relevant GitHub repos in audio DSP / MIR / music theory /
music generation for the **ASA** and **Harmonia** projects. One of two streams in this repo
(see `routines/README.md`).

> NOTE: this supersedes an earlier framing that described ASA as "an in-browser Essentia.js
> library." That was wrong and biased scoring toward browser/WASM tools. ASA is a SERVER-SIDE
> Python app. The **[Gemini role]** slot below is now filled from ASA's own `CLAUDE.md`;
> **Harmonia** is described from ASA's own incorporations doc and is still NOT verified against
> Harmonia's own `CLAUDE.md`. When in doubt, read those repos and treat them as authoritative
> over this summary.

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
- **Harmonia** — a React chord-progression / reharmonization tool on Tonal.js. Symbolic-first (not
  audio-first); license assumed MIT but unconfirmed. *(Per ASA's own
  `incorporations/forking-plans-2026-05-14.md`, which flags Harmonia's license as "Assumed MIT
  (confirm — out of repo)" — NOT verified against Harmonia's own CLAUDE.md, which is out of scope
  from this ASA-scoped session.)*

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

5. Score each 1–5 on relevance to ASA or Harmonia. Drop anything <3. Score against the REAL stacks:
   - ASA runs server-side on NATIVE Essentia (Python/C++). Native C/C++/Rust/Python audio
     libraries are FIRST-CLASS (a Rust crate is a PyO3 extension or sidecar; a C++ lib is a native
     dependency). Do NOT penalise "native / not browser-friendly."
   - Do NOT award relevance for "in-browser", "WASM", "Essentia.js", or "client-side", and ignore
     bundle-size / cold-start — these are irrelevant to ASA and were a past framing error.
   - The Essentia ecosystem (Essentia, gaia, Essentia models, host/wrapper references) is directly
     relevant to ASA.
   - ASA has a Gemini/LLM layer: LLM-/agent-driven *analysis*, natural-language music interfaces,
     MCP servers, and prompt-to-analysis tooling are genuinely ASA-relevant — NOT merely
     "tangential". BUT ASA's Phase 1 is deterministic DSP/MIR and is the ground truth: native
     audio / DSP / MIR libraries and chord / key / beat / loudness / structure models are the
     PRIORITY. Do NOT inflate a repo just because it has an LLM / agent / MCP. A generic
     music-LLM chat or MCP wrapper that adds no new DSP/MIR or analysis capability is a thin
     wrapper — tangential at most. Music *generation* models count only when they feed analysis
     or Harmonia reharmonization; a pure text-to-music generator is off-target.
   - ASA is an application: REST/API contract design, React analysis UIs, and job/queue patterns
     count.
   - Score Harmonia against its real stack (verify via CLAUDE.md).

6. Append survivors to `discoveries/audio-mir-<YYYY-MM-DD>.md` with sections: ASA-relevant /
   Harmonia-relevant / Both / Tangential but interesting. Two-sentence pitch each, link, score.

7. Append surfaced `owner/repo` lines to `_seen.txt`.

8. Commit to branch `claude/discoveries-<YYYY-MM-DD>` and open a PR.

Be direct. Don't pad the pitches. If a repo is a thin wrapper around something I'd already know
about, say so and drop the score. Ignore any licence considerations.

Keep the sweep DSP/MIR-led: at most about a third of survivors should be AI-first (music-LLM /
agent / MCP / generation). The rest should be native analysis, DSP, MIR, or music-theory tooling.
If you can't fill that third with genuinely ASA-relevant analysis-LLM work, ship fewer survivors
rather than padding with generation models or MCP wrappers.
