# music-asa / symbolic-theory

Symbolic music, music-theory libraries, datasets, and tokenizers — the
Harmonia-adjacent stream. **Harmonia is real but unpublished** (single local HTML
file, vanilla HTML/CSS/JS, zero deps; see `../README.md`): every `H` repo here is a
**conceptual reference** to Harmonia's idea space (chord/scale/theory/MIDI ideas,
UX, datasets), never a stack-fit or code-lift target — Harmonia has no codebase to
incorporate into. Scores are **1–5 relevance** + flag (`ASA` · `H` · `Both` · `tang`);
corrected scores follow `discoveries/reanalysis-2026-05-20.md` (Harmonia framing
further corrected 2026-05-26).

## Datasets & ingest (4)

- **4/H** · [spyroskantarelis/chordonomicon](https://github.com/spyroskantarelis/chordonomicon) · `143★` · `maturity:reference`
  666K symbolic chord progressions with section labels (verse/chorus/bridge), genre, and release date, encoded as single-chord / triad (root+quality+bass) / tetrad (+extensions) tokens on Hugging Face; RNN/GRU/LSTM baselines published. **Mine:** drop-in training/eval corpus for any reharmonization or progression model, plus a ready benchmark — fork the tokenization scheme and baselines. _(surfaced 05-13 · tags: dataset, chords, progressions, hf)_
- **4/H** · [pianosnake/ireal-reader](https://github.com/pianosnake/ireal-reader) · `JavaScript` · `43★` · `active:2026-05` · `maturity:lib`
  Node module parsing iReal Pro exports into JS objects: title/composer/key/BPM plus a `measures` array of chord-symbol arrays (`['C^7']`, `['Asus','A7susadd3']`), repeats/segnos/codas expanded to linear measures. **Mine:** fork as the ingest path that turns the entire iReal Pro jazz corpus into structured chord progressions with almost no parsing work. _(surfaced 05-19 · tags: ireal, chords, parser, dataset)_
- **4/H** · [vpavlenko/rawl](https://github.com/vpavlenko/rawl) · `TypeScript` · `81★` · `maturity:app`
  React+TS MIDI/MusicXML visualizer color-coding pitch classes ("12 colors") and annotating harmonic language across classical, jazz, chiptune, modal systems. **Mine:** study the piano-roll rendering and the "harmony as flags" annotation model; reuse the 12-color pitch-class palette for any harmonic visualization. _(surfaced 05-13 · tags: visualizer, harmony, pianoroll, midi)_
- **4/H** · [madderscientist/noteDigger](https://github.com/madderscientist/noteDigger) · `JavaScript` · `268★` · `maturity:app`
  "No framework, no library" pure-JS audio→MIDI transcription: optimised real-FFT STFT, CQT, ONNX nnls.js + spectral-clustering note picking, harmonic reduction, beat tracking. (0% ASA-relevant — client-side JS.) **Mine:** the closest spirit-match to Harmonia's own "no framework, no library" stance — read the zero-deps STFT/CQT + nnls note-picking for a feel of what a vanilla-JS audio→MIDI ingest would look like if Harmonia ever added one. Reference, not a fork target. _(surfaced 05-13 PM · tags: transcription, midi, cqt, onnx)_

## Theory tools & visualizers (3)

- **3/H** · [chromatone/chromatone.center](https://github.com/chromatone/chromatone.center) · `146★` · `maturity:app`
  Vue/Vite app on Tonal.js + abcjs + Tone.js + audiomotion-analyzer presenting chords, scales, rhythms, and pitch-color visualisations as PWA "instruments". The earlier "Direct overlap with Harmonia's stack" framing was wrong (Harmonia is vanilla zero-dep JS, not Tonal.js/Vue). **Mine:** conceptual reference for chord/scale visual idioms and a color-coded pitch palette — Harmonia could borrow the *ideas* but not the code (different stack philosophies). _(surfaced 05-13 PM · tags: theory, scales, pwa)_
- **3/H** · [Natooz/MidiTok](https://github.com/Natooz/MidiTok) · `Python` · `870★` · `maturity:lib`
  The canonical MIDI/abc tokenizer: REMI, REMI+, MIDI-Like, TSD, Structured, CPWord, Octuple, MuMIDI, MMM, PerTok; BPE/Unigram/WordPiece training; HF Hub integration; Symusic-backed I/O. **Mine:** the obvious dependency if a consumer ever ingests/produces token sequences — adopt rather than reimplement. Skip if already known. _(surfaced 05-17 · tags: tokenizer, midi, symbolic)_
- **3/H** · [CPJKU/partitura](https://github.com/CPJKU/partitura) · `Python` · `350★` · `maturity:lib`
  Symbolic-score library across MusicXML, MIDI, Humdrum **kern**, and MEI, exposing notes (pitch/duration/voice/staff), parts, time signatures, beat maps. Python — and Harmonia is browser-only — so adoption is moot; what survives is the data-model. **Mine:** reference for richer score import/export than a hand-rolled JS file would naturally support; copy its note/part/timeline model as a conceptual blueprint if Harmonia ever expands beyond its current internal representation. _(surfaced 05-19 · tags: symbolic, musicxml, mei, kern)_
- **3/H** · [sivabenepoivediamo/musicplusplus](https://github.com/sivabenepoivediamo/musicplusplus) · `C++` · `maturity:lib`
  Header-only C++ music-theory library using vector-based representations for chords, scales, intervals, **voice leading**, and **reharmonization** (modal interchange, modulation); TypeScript and Python SDKs on the roadmap. Dead-center on Harmonia's *domain*. **Mine:** algorithm reference for voice-leading + reharmonization — Harmonia is dependency-free vanilla JS, so even the planned TS SDK isn't an "incorporate" target; read the math and reimplement if Harmonia ever wants richer reharmonization than its current Substitutions panel. _(surfaced 05-21 · tags: theory, reharmonization, voice-leading, cpp)_
- **3/H** · [fpachet/continuator](https://github.com/fpachet/continuator) · `Python` · `maturity:lib`
  François Pachet's reimplementation of the Continuator: variable-order Markov modeling + exact finite-chain inference for melodic / chord-sequence continuations with **guaranteed positional constraints**, real-time learning, tiny data needs. **Mine:** borrow the constrained-Markov technique for suggesting/completing progressions under hard anchors ("keep these chords"); a non-transformer alternative worth porting. _(surfaced 05-21 · tags: markov, continuation, constraints, symbolic)_
- **3/H** · [comorebi-notes/rechord](https://github.com/comorebi-notes/rechord) · `maturity:app`
  React + Tone.js app for writing and sharing chord progressions, still getting commits; a 2017 sharing app with no reharmonization logic. The earlier "exact assumed Harmonia stack family" framing was wrong (Harmonia is vanilla zero-dep JS, not React + Tone.js). **Mine:** conceptual reference for progression-entry UI ideas — Harmonia's existing Web Audio playback already covers what Tone.js would; nothing on the theory side. _(surfaced 05-21 · tags: react, tonejs, progressions, ui)_

## Marginal — kept with a note (low)

- **low/H** · [cuthbertLab/music21j](https://github.com/cuthbertLab/music21j) · `JavaScript` · `maturity:lib`
  JS port of music21; well-known, on every music-theory shortlist. **Mine:** browser-side theory primitives (notes, intervals, keys) if a JS theory dep is wanted — adopt, don't reimplement. _(surfaced 05-13 · tags: theory, music21, js)_
- **low/H** · [asigalov61/tegridy-tools](https://github.com/asigalov61/tegridy-tools) · `Python` · `maturity:lib`
  Symbolic-music NLP toolkit from 2020; recent commits but no new direction. **Mine:** grab specific MIDI-processing utilities only; nothing architecturally new. _(surfaced 05-13 · tags: symbolic, midi, nlp)_
- **low/tang** · [sildater/parangonar](https://github.com/sildater/parangonar) · `Python` · `maturity:lib`
  Solid score-to-performance **alignment** library — out of scope (neither stream does symbolic alignment). **Mine:** the alignment algorithms if note-to-performance matching ever becomes a feature. _(surfaced 05-14 · tags: alignment, symbolic, off-use)_
- **low/tang** · [JulienVincenot/MOZLib](https://github.com/JulienVincenot/MOZLib) · `Max/Lisp` · `maturity:lib`
  Max/Lisp computer-aided-composition teaching package; off-stack. **Mine:** CAC technique ideas only. _(surfaced 05-14 · tags: cac, max, lisp)_
- **low/tang** · [Sonata165/PhraseLDM_code](https://github.com/Sonata165/PhraseLDM_code) · `maturity:reference`
  Latent-diffusion full-song symbolic generation (research); mostly a project page, README unreachable. **Mine:** read the paper for phrase-level latent-diffusion ideas; code not packaged. _(surfaced 05-19 · tags: research, diffusion, symbolic)_
- **low/tang** · [astradzhao/music-rfm](https://github.com/astradzhao/music-rfm) · `maturity:reference`
  Recursive-feature-machine steering for autoregressive music generation; interesting paper, narrow utility. **Mine:** the RFM-steering idea only. _(surfaced 05-19 · tags: research, steering, gen)_
- **low/tang** · [ZaneH/piano-trainer](https://github.com/ZaneH/piano-trainer) · `maturity:app`
  Piano practice/trainer app, off-stack. Dropped 05-21. **Mine:** practice-UX patterns only. _(surfaced 05-21 · tags: piano, practice, off-stack)_
- **low/H** · [albertms10/music_notes](https://github.com/albertms10/music_notes) · `Dart` · `maturity:lib`
  Music-theory library in Dart. The earlier "off-stack for a JS Harmonia" rationale is void (Harmonia has no stack to be off — it's a vanilla single-file tool with no deps), but the score holds: not conceptually richer than what Harmonia already hand-rolls. **Mine:** reference for a clean theory type-model (intervals/keys/scales) only. _(surfaced 05-17 · tags: theory, dart, lib)_
- **low/H** · [pedromsantos/vaughan](https://github.com/pedromsantos/vaughan) · `F#` · `maturity:lib`
  Music-theory library in F#; off-stack. **Mine:** functional-style theory modeling reference. _(surfaced 05-17 · tags: theory, fsharp, lib)_
