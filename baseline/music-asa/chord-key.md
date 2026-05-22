# music-asa / chord-key

Chord and key detection — audio→chord, audio→key, and the harmonic-core MIR that
feeds ASA's tonal stage and is conceptually relevant to Harmonia. Scores are **1–5
relevance** to ASA plus a flag: `ASA` · `H` · `Both` · `tang`. `H` = **conceptual
reference for Harmonia** — a real but **unpublished**, dependency-free single-file
vanilla-JS chord/reharmonization tool with no repo, so `H` flags idea-usefulness, not
an incorporation/stack-fit score. See `../README.md` for the spec; corrected scores
follow `discoveries/reanalysis-2026-05-20.md`.

## Cross-domain (full entry here — harmonic-core)

- **5/Both** · [JuzzyDee/audio-analyzer-rs](https://github.com/JuzzyDee/audio-analyzer-rs) · `Rust` · `21★` · `active:2026-03` · `maturity:app`
  Pure-Rust MCP server extracting the whole MIR stack — spectral centroid/bandwidth/rolloff/flatness, **Krumhansl-Schmuckler key**, **pitch-class distribution**, **tonnetz**, MFCCs, EBU R128 LUFS/true-peak/LRA, crest factor, HPSS, stereo field, section boundaries — in <2s/track with no Python or FFmpeg. **Mine:** lift the dependency-free K-S key + pitch-class + tonnetz code as a server-side harmonic core, and the MCP tool surface as the "expose analysis to an LLM" pattern; the whole crate is effectively ASA's L1 in one dependency. _(surfaced 05-14 · tags: rust, mcp, key, tonnetz, r128)_ — **stub also in `apps-architecture.md`.**
- **5/Both** · [dreamrec/LivePilot](https://github.com/dreamrec/LivePilot) · `Python` · `21★` · `active:2026-03` · `maturity:app`
  The most ambitious Ableton-MCP so far: 465 tools / 56 domains, a 5,264-device atlas, an optional M4L spectral-perception bridge (9-band FFT, RMS/peak, **Krumhansl-Schmuckler key**, pitch, FluCoMa mel/chroma/onset), VST/AU/AAX corpus discovery, and 12 "creative engines" with before/after measurement. **Mine:** the K-S-key + chroma bridge is the harmonic nugget to fork; the measure→act→measure loop is the end-to-end template for an analysis+Ableton+LLM app. _(surfaced 05-17 · re-scored 4→5 on 05-20 · tags: ableton, mcp, key, chroma, agentic)_ — **stub also in `ableton-mcp-daw.md`.**

## Strong (4–5)

- **5/H** · [ptnghia-j/ChordMiniApp](https://github.com/ptnghia-j/ChordMiniApp) · `TypeScript` · `282★` · `maturity:app`
  Next.js + Flask app: chord recognition (Chord-CNN-LSTM, BTC-SL/PL from ISMIR2019), beat tracking (Beat-Transformer + madmom), lyrics (Music.ai + LRClib), sheet via OpenSheetMusicDisplay with chord-db guitar diagrams. The closest public neighbour to a Harmonia product surface. **Mine:** study its UX choices (chord/beat/lyric/sheet layout) before designing any chord-display UI; the Flask chord-recognition service is a forkable audio→chord backend. _(surfaced 05-13 · tags: chord, beat, lyrics, sheet, nextjs)_
- **4/Both** · [a1ex90/MusicalKeyCNN](https://github.com/a1ex90/MusicalKeyCNN) · `Python` · `50★` · `active:2025-06` · `maturity:model`
  CQT-spectrogram CNN (after Korzeniowski & Widmer) for key estimation with pitch-shift augmentation, trained on GiantSteps, outputting Camelot-wheel labels at ~73.5% MIREX-weighted (competitive with Mixed In Key). Full preprocessing/training/eval code, not a wrapper. **Mine:** fork the CQT-CNN as a server-side key detector for ASA's tonal stage and to ground reharmonization in a detected key; reuse the pitch-shift augmentation recipe. _(surfaced 05-19 · tags: key, cnn, cqt, camelot)_
- **4/H** · [dogayuksel/webKeyFinder](https://github.com/dogayuksel/webKeyFinder) · `TypeScript` · `35★` · `active:2026-03` · `maturity:app`
  libKeyFinder (C++) compiled to WASM via Emscripten, fed by an AudioWorkletProcessor + Web Workers, wrapped in Preact. The cleanest current template for in-browser audio→key plumbing. **Mine:** for a browser consumer, fork the worklet→worker→WASM wiring wholesale; for ASA the real nugget is the underlying native **libKeyFinder** (run it server-side, skip the WASM). _(surfaced 05-18 · tags: key, wasm, libkeyfinder, worklet)_
- **4/Both** · [andreamust/consonance-ACE](https://github.com/andreamust/consonance-ACE) · `maturity:model`
  Audio chord-estimation Conformer that splits prediction into separate root / bass / pitch-activation heads with consonance-based label smoothing; ships a pretrained checkpoint and inference turning WAV into 170-class timestamped chord `.lab` output. **Mine:** run server-side as a modern, theory-informed replacement for ASA's chord stage; its timestamped chord stream is the kind of input a chord/reharmonization tool consumes. _(surfaced 05-21 · tags: chord, conformer, ace, lab)_

## Useful references (3)

- **3/H** · [ifeelvoid/keyfinder](https://github.com/ifeelvoid/keyfinder) · `Swift` · `45★` · `active:2026-03` · `maturity:app`
  Native macOS app + VST/AU detecting key (Camelot), BPM, and waveforms via a custom **Krumhansl-Schmuckler** engine (16k-point FFT, bass weighting), sharing one Swift `KeyFinderEngine` package across app and plugin. Off-stack (Swift) but a tidy from-scratch K-S worked example. **Mine:** read the K-S implementation (FFT size, bass-weighting) and copy the app↔plugin shared-engine split if you ever ship both. _(surfaced 05-19 · tags: key, krumhansl, swift, vst)_
- **3/H** · [markwilkins/midi-chord-reader](https://github.com/markwilkins/midi-chord-reader) · `C++` · `22★` · `maturity:app`
  JUCE/C++ DAW plugin naming chords from a MIDI track during playback — normalises to one octave while preserving bass, generates slash inversions (`Am/C`), filters 2nd/4th/6th passing tones, uses the lowest three notes for quality. **Mine:** lift the chord-naming heuristics (octave-normalise + slash inversion + passing-tone filter) for any "given these MIDI notes, name the chord" path. _(surfaced 05-17 · tags: chord, midi, juce, heuristic)_

## Marginal — kept with a note (low)

- **low/H** · [lorediggia/harmony-lab](https://github.com/lorediggia/harmony-lab) · `Rust` · `maturity:app`
  Minimal Rust scale/chord explorer. Dropped 05-21 as too small. **Mine:** only as a tiny reference for representing scales/chords in Rust if a native harmonic helper is wanted. _(surfaced 05-21 · tags: chord, scale, rust)_
- **low/tang** · [sepandhaghighi/capo](https://github.com/sepandhaghighi/capo) · `Python` · `maturity:lib`
  Python guitar-chord transposition. Dropped 05-21 (chord transposition is trivial to implement directly). **Mine:** capo/transpose mapping logic only, if a guitar-specific transpose ever comes up. _(surfaced 05-21 · tags: chord, guitar, transpose)_
- **low/tang** · [timvancann/chordflow](https://github.com/timvancann/chordflow) · `Rust` · `maturity:app`
  Rust chord-practice TUI — not analysis or theory tooling. Dropped 05-21. **Mine:** practice-loop / progression-cycling UX idea only. _(surfaced 05-21 · tags: chord, practice, tui)_
- **low/H** · [JJ110112/LiveChord](https://github.com/JJ110112/LiveChord) · `maturity:alpha`
  No README/description to vet against; skipped 05-21. **Mine:** nothing confirmed — revisit if a README appears. _(surfaced 05-21 · tags: chord)_
- **low/H** · [joanroig/midi-to-scaler-chord-sets](https://github.com/joanroig/midi-to-scaler-chord-sets) · `maturity:lib`
  Niche MIDI→Scaler chord-set converter. Dropped 05-21 (off-stack). **Mine:** the chord-set data shape if interoperating with Scaler is ever needed. _(surfaced 05-21 · tags: chord, midi, scaler)_
