# Recommendations

The consolidated, deduped verdict across **every** discovery sweep in
`discoveries/`. Single-source-of-truth shortlist; the dated files remain the raw
per-sweep record. **Re-scored 2026-05-20** under corrected ground truth — see
`discoveries/reanalysis-2026-05-20.md` for old→new deltas and rationale.

> **Comprehensive catalog:** this file is the *shortlist* (≥ 3). For **every** repo ever
> surfaced — including barely-mentioned and dropped-for-redundancy ones — with idea-mining
> ("what to fork/build") commentary, see **`baseline/`**
> (`baseline/music-asa/` and `baseline/legal-tech/`). **Harmonia** is a real but **unpublished
> single local HTML file** (dependency-free vanilla JS — **no React/Tonal.js**; not on GitHub,
> `github.com/slittycode/harmonia` → 404); `(H)` marks a **conceptual reference** for it, not a
> scored/incorporable repo.

Every repo at relevance **≥ 3** is listed; where sweeps disagreed we keep the most
favourable verdict (and now the corrected one). Repos that fell **below 3** in the
re-score are listed under "Downgraded out."

**Legend** — 1–5 relevance to **ASA** = *Ableton Sonic Analyzer*: a **Python
3.11 + FastAPI** backend + **React 19** frontend that measures audio **server-side**
(L1 native **Essentia 2.1b6**; L2 **torchcrepe** pitch on **Demucs** stems) then has
**Gemini** (Phase 2) emit measurement-cited **Ableton Live 12 device/param**
recommendations. `(H)` = **conceptual reference for Harmonia** — a real but
**unpublished**, dependency-free single-file vanilla-JS chord/reharmonization tool with
no repo (not React/Tonal.js; `github.com/slittycode/harmonia` → 404), so `(H)` flags
idea-usefulness, not an incorporation/stack-fit score. `★` = incorporation plan in
`incorporations/`. `⚠` = caveat. `(new)` = surfaced 2026-05-20.

## Top picks (5)

- **5** · [creightonlinza/forever-jukebox](https://github.com/creightonlinza/forever-jukebox) — madmom + Essentia → REST analysis JSON; the analysis→contract precedent. _(★ ASA Track 3)_
- **5** · [DarienBrito/EssentiaTD](https://github.com/DarienBrito/EssentiaTD) — Essentia plugins enumerating exactly ASA's L1 algorithms (mel/MFCC/YinFFT/key/onset/R128).
- **5** · [MTG/essentia](https://github.com/MTG/essentia) — **ASA's own core native dependency**; algorithm + model-zoo + upgrade reference. _(was wrongly dropped)_
- **5** · [dreamrec/LivePilot](https://github.com/dreamrec/LivePilot) — Ableton MCP **+** spectral/K-S-key/mel-chroma analysis bridge **+** measure→act→measure loop; closest analog to ASA end-to-end. _(both)_
- **5** · [JuzzyDee/audio-analyzer-rs](https://github.com/JuzzyDee/audio-analyzer-rs) — pure-Rust MCP with ASA's whole L1 MIR stack (K-S key, pitch-class, tonnetz, R128). _(both)_
- **5** · [OpenMOSS/MOSS-Music](https://github.com/OpenMOSS/MOSS-Music) — open 8B audio-LLM (lyrics ASR, structure, chord/key/tempo, captioning, Q&A); closest open self-hostable analogue of ASA's Essentia+Gemini layer. _(05-21)_
- **5** · [ptnghia-j/ChordMiniApp](https://github.com/ptnghia-j/ChordMiniApp) — chord recognition + beat + lyrics + sheet render; closest neighbour to Harmonia. _(H)_

## ASA — Phase 1: native DSP, loudness, MIR features

- **5** · [MTG/essentia](https://github.com/MTG/essentia) — the native C++/Python MIR library ASA runs; + the Essentia model zoo.
- **4** · [httpsworldview/openmeters](https://github.com/httpsworldview/openmeters) — Rust BS.1770-5 LUFS/true-peak + spectral-reassignment. _(★ ASA Track 1)_
- **4** · [complexlogic/rsgain](https://github.com/complexlogic/rsgain) — native C++ EBU R128 + true-peak + ReplayGain 2.0 (603★). _(was wrongly dropped)_
- **4** · [linuxmatters/jivetalking](https://github.com/linuxmatters/jivetalking) — measure-then-choose-params EBU R128 pipeline = ASA's Phase1→Phase2 logic.
- **4** · [Angel2mp3/AudioAuditor](https://github.com/Angel2mp3/AudioAuditor) — clipping/fake-lossless detection + dynamic-range & true-peak (diagnose-then-recommend).
- **4** · [Ircam-Partiels/Partiels](https://github.com/Ircam-Partiels/Partiels) — Vamp host; CSV/SDIF/JSON export schemas (result interchange). _(★ ASA Track 2)_
- **4** · [openclaw/songsee](https://github.com/openclaw/songsee) — native Go renderer of ASA's exact view catalog (mel/chroma/HPSS/tempogram/MFCC…).
- **4** · [wavey-ai/mel-spec](https://github.com/wavey-ai/mel-spec) — native Rust mel/STFT primitives (WASM/TGA-interchange credit dropped; native is the value).
- **4** · [CPJKU/beat_this](https://github.com/CPJKU/beat_this) — ISMIR-2024 transformer beat/downbeat; lighter to wire than madmom.
- **4** · [WB2024/Essentia-to-Metadata](https://github.com/WB2024/Essentia-to-Metadata) — fully-offline Essentia-TF genre/mood models in Python (ASA's native-model pattern).
- **4** · [craiglush/navidrome-mood-plugin](https://github.com/craiglush/navidrome-mood-plugin) — FastAPI `essentia-tensorflow` analyzer; *"essentia can't run in WASM"* validates ASA arch. _(↑)_
- **4** · [MTG/gaia](https://github.com/MTG/gaia) ⚠ — native C++/Python Essentia similarity/classifier companion. ⚠ stale (2019) — reference / prefer essentia-TF embeddings + vector store. _(↑)_
- **4** · [libAudioFlux/audioFlux](https://github.com/libAudioFlux/audioFlux) — C-core + Python feature extraction (mel/MFCC/CQT/chroma/pitch); native Essentia complement. _(new)_
- **4** · [sanderwood/clamp3](https://github.com/sanderwood/clamp3) — multimodal (text/score/audio/MIDI) embeddings + retrieval for reference-matching.
- **4** · [Polochon-street/bliss-rs](https://github.com/Polochon-street/bliss-rs) — native Rust chroma/tempo/timbre similarity vectors ("tracks-like-this" axis). _(↑)_
- **3** · [bananaofhappiness/soundscope](https://github.com/bananaofhappiness/soundscope) — Rust LUFS/true-peak/FFT; BS.1770 numerical cross-check.
- **3** · [matteospanio/torchfx](https://github.com/matteospanio/torchfx) — PyTorch-native composable/differentiable DSP filters (server-side batch potential).
- **3** · [jhartquist/resonators](https://github.com/jhartquist/resonators) — Rust per-sample spectral analysis (Python bindings; WASM rationale void). _(↓)_
- **3** · [urinieto/msaf](https://github.com/urinieto/msaf) — native Python music-structure analysis (boundaries/segmentation) = ASA's section stage. _(was wrongly dropped)_
- **3** · [mhartzel/freelcs](https://github.com/mhartzel/freelcs) — Python+Docker EBU R128 loudness server; loudness-stage UX/topology reference.
- **3** · [casantosmu/audiodeck](https://github.com/casantosmu/audiodeck) — Go server-side spectrogram fake-lossless scanner; library-scan shape.
- **3** · [tyiannak/pyAudioAnalysis](https://github.com/tyiannak/pyAudioAnalysis) — established Python MIR (MFCC/chroma/segmentation/classification). _(new)_
- **3** · [audeering/opensmile](https://github.com/audeering/opensmile) — mature C++ feature toolkit + Python wheels. _(new)_

## ASA — Layer 2: stem separation + pitch (current pipeline)

- **4** · [JeffreyCA/spleeter-web](https://github.com/JeffreyCA/spleeter-web) — React + Django + Celery/Redis + Docker running **Demucs** = ASA's app+queue+L2 shape. _(↑ · ★ filed-for-later)_
- **4** · [Ryan5453/demucs-next](https://github.com/Ryan5453/demucs-next) — faster modern Demucs fork; direct L2 speed win. _(↑)_
- **4** · [ssmall256/demucs-mlx](https://github.com/ssmall256/demucs-mlx) — pip-importable Apple-Silicon Demucs; L2 drop-in for Mac users. _(was wrongly dropped)_
- **4** · [undef13/splifft](https://github.com/undef13/splifft) — modular separation/transcription + 110-model registry ("swap separation backend"). _(↑)_
- **3** · [crlandsc/moises-light](https://github.com/crlandsc/moises-light) — band-split U-Net reference.
- **3** · [sweetspotsoundsystem/stemgen-rt](https://github.com/sweetspotsoundsystem/stemgen-rt) — real-time 4-stem JUCE/VST plumbing.
- **3** · [asteroid-team/asteroid](https://github.com/asteroid-team/asteroid) — mature PyTorch separation toolkit. _(was wrongly dropped)_
- **3** · [paladini/voice-separator-demucs](https://github.com/paladini/voice-separator-demucs) — FastAPI + Demucs = ASA's L2-as-a-service shape. _(was wrongly dropped)_
- **3** · [openvpi/GAME](https://github.com/openvpi/GAME) — singing-voice→MIDI diffusion (pitch adjacent; ASA uses torchcrepe).

## ASA — LLM / MCP / Ableton (Phase 2–3)

- **5** · [dreamrec/LivePilot](https://github.com/dreamrec/LivePilot) — Ableton MCP + analysis bridge + before/after measurement; the end-to-end analog. _(both · ↑)_
- **5** · [OpenMOSS/MOSS-Music](https://github.com/OpenMOSS/MOSS-Music) — open 8B audio-LLM emitting ASA-shaped analysis (structure/chord/key/tempo/Q&A); reference or partial replacement for the Gemini layer. _(05-21)_
- **4** · [adamjmurray/producer-pal](https://github.com/adamjmurray/producer-pal) — M4L + MCP + **Gemini** Ableton control; "apply the recommendation in Live" companion. _(↑)_
- **4** · [hugohow/mcp-music-analysis](https://github.com/hugohow/mcp-music-analysis) — Python MCP wrapping librosa for LLMs; the analysis-as-MCP-tools template. _(new)_
- **4** · [brightlikethelight/music21-mcp-server](https://github.com/brightlikethelight/music21-mcp-server) — FastMCP exposing theory/analysis tools to an LLM (also `(H)`). _(↑)_
- **3** · [jpoindexter/ableton-mcp](https://github.com/jpoindexter/ableton-mcp) — Python Ableton MCP (Gemini-capable). _(was wrongly dropped)_
- **3** · [bschoepke/ableton-live-mcp](https://github.com/bschoepke/ableton-live-mcp) — agent-`eval` Ableton MCP (latency-tuned).
- **3** · [uisato/ableton-mcp-extended](https://github.com/uisato/ableton-mcp-extended) — TCP+UDP Ableton MCP + ElevenLabs TTS. _(both)_
- **3** · [christopherwxyz/remix-mcp](https://github.com/christopherwxyz/remix-mcp) — Rust Ableton-control MCP (OSC, 266 tools). _(was wrongly dropped)_
- **3** · [williamzujkowski/live-coding-music-mcp](https://github.com/williamzujkowski/live-coding-music-mcp) — Strudel.cc over MCP (+ analysis + optional Gemini).
- **3** · [Conceptual-Machines/magda-core](https://github.com/Conceptual-Machines/magda-core) — AI-first JUCE DAW; NL→DSL session edits (agentic-surface reference).
- **3** · [geshang777/GaMMA](https://github.com/geshang777/GaMMA) — research audio-LLM for joint global/temporal music understanding; second data point for the LLM layer (paper repo, not packaged). _(05-21)_
- **3** · [innermost47/ai-dj](https://github.com/innermost47/ai-dj) — server-side Stable Audio Open loop generator; Phase-3 audition-sample reference. _(was wrongly dropped)_
- **3** · [prabal-rje/latentscore](https://github.com/prabal-rje/latentscore) — retrieval-based ambient generation (Phase-3 retrieval-gen angle).

## ASA — app & deployment architecture

- **4** · [NeptuneHub/AudioMuse-AI](https://github.com/NeptuneHub/AudioMuse-AI) — Flask + Redis/RQ workers + PostgreSQL + Docker/K8s analysis app; ASA hosted-mode blueprint. _(new)_
- **4** · [NeptuneHub/AudioMuse-AI-NV-plugin](https://github.com/NeptuneHub/AudioMuse-AI-NV-plugin) — thin client of the above; its queue arch is the value. _(↑)_
- **4** · [marcus/good-composer](https://github.com/marcus/good-composer) — FastAPI + WebSocket streaming + React + LLM = ASA's stack pattern. _(↑)_
- **3** · [Boof2015/astra](https://github.com/Boof2015/astra) — Electron player; decoupled analysis/output paths + visualizer-rack UX.

## Harmonia — conceptual references (idea-only)

- **5** · [ptnghia-j/ChordMiniApp](https://github.com/ptnghia-j/ChordMiniApp) — chord recognition + beat + lyrics + OpenSheetMusicDisplay.
- **4** · [spyroskantarelis/chordonomicon](https://github.com/spyroskantarelis/chordonomicon) — 666K section-labelled chord progressions dataset.
- **4** · [vpavlenko/rawl](https://github.com/vpavlenko/rawl) — pitch-class-coloured MIDI/MusicXML harmony visualizer.
- **4** · [madderscientist/noteDigger](https://github.com/madderscientist/noteDigger) — zero-deps pure-JS audio→MIDI (Harmonia-only; not ASA-relevant).
- **4** · [dogayuksel/webKeyFinder](https://github.com/dogayuksel/webKeyFinder) — libKeyFinder→WASM in AudioWorklet/workers (native libKeyFinder is the ASA nugget).
- **4** · [pianosnake/ireal-reader](https://github.com/pianosnake/ireal-reader) — iReal Pro charts → structured chord-symbol JSON.
- **3** · [chromatone/chromatone.center](https://github.com/chromatone/chromatone.center) — Tonal.js + abcjs chord/scale/pitch-colour PWA.
- **3** · [markwilkins/midi-chord-reader](https://github.com/markwilkins/midi-chord-reader) — JUCE plugin: name chords from MIDI.
- **3** · [Natooz/MidiTok](https://github.com/Natooz/MidiTok) — canonical MIDI/abc tokenizer.
- **3** · [CPJKU/partitura](https://github.com/CPJKU/partitura) — symbolic score model (MusicXML/MIDI/kern/MEI).
- **3** · [sivabenepoivediamo/musicplusplus](https://github.com/sivabenepoivediamo/musicplusplus) — header-only C++ theory lib (voice leading, reharm via modal interchange); TS/Python SDKs planned — algorithm reference. _(05-21)_
- **3** · [fpachet/continuator](https://github.com/fpachet/continuator) — Pachet's constrainable variable-order Markov continuator; chord/melody completion under hard anchor constraints (technique to borrow). _(05-21)_
- **3** · [comorebi-notes/rechord](https://github.com/comorebi-notes/rechord) — React + Tone.js chord-progression entry/playback app (UI/playback reference; no reharm logic). _(05-21)_

## Relevant to both

- **5** · [JuzzyDee/audio-analyzer-rs](https://github.com/JuzzyDee/audio-analyzer-rs) — pure-Rust MCP; full MIR stack + an LLM tool surface.
- **5** · [dreamrec/LivePilot](https://github.com/dreamrec/LivePilot) — Ableton + analysis + agentic measurement loop.
- **4** · [rzru/nightingale](https://github.com/rzru/nightingale) — Tauri: Demucs separation + transcription + pitch scoring + key/tempo shift. _(★ filed-for-later)_
- **4** · [a1ex90/MusicalKeyCNN](https://github.com/a1ex90/MusicalKeyCNN) — CQT-CNN key estimation + Camelot output (tonal signal for both).
- **4** · [andreamust/consonance-ACE](https://github.com/andreamust/consonance-ACE) — Conformer audio chord-estimation (root/bass/pitch heads), pretrained, WAV→170-class timestamped `.lab`; modern server-side model for ASA's chord stage. _(05-21)_
- **3** · [ifeelvoid/keyfinder](https://github.com/ifeelvoid/keyfinder) — from-scratch K-S key/BPM (Swift; worked-example reference).

## Tangential / plumbing (kept at 3)

- **3** · [phones24/ep133-export-to-daw](https://github.com/phones24/ep133-export-to-daw) — WebMIDI → DAWproject/REAPER/MIDI export.
- **3** · [gluon/Void-LinkAudio](https://github.com/gluon/Void-LinkAudio) — sample-accurate beat-synced audio over LAN (umbrella for the old `ofxAbletonLinkAudio`).

## Net-new this re-score (2026-05-20)

`MTG/essentia` (5), `NeptuneHub/AudioMuse-AI` (4), `libAudioFlux/audioFlux` (4),
`hugohow/mcp-music-analysis` (4), `tyiannak/pyAudioAnalysis` (3),
`audeering/opensmile` (3). **Leads (unverified):** vbarreiratt FantasticEar MCP,
Estratto (Rust). **ASA's own deps, for reference:** `facebookresearch/demucs`,
`maxrmorrison/torchcrepe`, Gemini API.

## Downgraded out (now < 3)

- [andremichelle/openDAW](https://github.com/andremichelle/openDAW) 3→**2** — credited as a "browser-first" reference with no analysis surface; ASA isn't a web DAW.
- [JorenSix/Olaf](https://github.com/JorenSix/Olaf) 3→**2** — in-browser fingerprinting; audio identification isn't an ASA use case. _(was ★ filed-for-later — withdrawn)_

## Corrections & divergent vetting

The framing flip (browser-Essentia.js → native server-side Essentia + Demucs +
torchcrepe + Gemini/Ableton) is the source of every delta; full table in
`discoveries/reanalysis-2026-05-20.md`. Headlines: **up** — LivePilot 4→5,
producer-pal/spleeter-web/navidrome-mood/gaia/bliss-rs/splifft/demucs-next/
good-composer/music21-mcp/AudioMuse-NV 3→4; **un-dropped** — MTG/essentia→5,
rsgain/demucs-mlx→4, msaf/asteroid/voice-separator-demucs/jpoindexter-ableton-mcp/
remix-mcp/ai-dj→3; **down/out** — resonators 4→3, openDAW & Olaf →2.

Pre-existing divergences retained from the prior consolidation (now superseded where
re-scored): EssentiaTD 4→5 and Essentia-to-Metadata 3→4 (already applied in 05-17);
wavey-ai/mel-spec 4 vs 3; freelcs/uisato/ifeelvoid kept-vs-dropped across sweeps —
all resolved to the corrected scores above.

**2026-05-21 sweep folded in (2026-05-22):** the six ≥3 survivors from
`discoveries/audio-mir-2026-05-21.md` — MOSS-Music (5), consonance-ACE (4), GaMMA (3),
musicplusplus (3), continuator (3), rechord (3) — were previously only in `baseline/`
and the dated sweep; now added above so the shortlist again lists every repo ≥3. They
were already scored under the corrected server-side framing.
