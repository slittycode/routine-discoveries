# Recommendations

The consolidated, deduped verdict across **every** discovery sweep in
`discoveries/`. This is the single-source-of-truth shortlist; the dated
files under `discoveries/` remain the raw per-sweep vetting record (full
write-ups, scores, and why things were dropped).

Every repo that cleared the bar (relevance **≥ 3**) in *any* sweep is
listed here — when sweeps disagreed, the entry shows the most favourable
verdict and the divergence is logged at the bottom (we keep things in
rather than drop them).

**Legend** — score is 1–5 relevance to **ASA** (Essentia.js DSP:
mel-spectrograms, tonal balance, dynamics, loudness) and/or **Harmonia**
(Tonal.js chord-progression / reharmonization). `★` = has an
incorporation plan in `incorporations/`. The date marks the sweep that
surfaced it.

## Top picks (5/5)

- **5** · [creightonlinza/forever-jukebox](https://github.com/creightonlinza/forever-jukebox) — local Infinite-Jukebox; madmom + Essentia → REST analysis JSON. _(05-13 · ★ ASA plan Track 3)_
- **5** · [DarienBrito/EssentiaTD](https://github.com/DarienBrito/EssentiaTD) — Essentia CHOPs for TouchDesigner; cleanest map of ASA-relevant algorithms. _(05-14)_
- **5** · [ptnghia-j/ChordMiniApp](https://github.com/ptnghia-j/ChordMiniApp) — chord recognition + beat tracking + lyrics + sheet render; closest neighbour to Harmonia. _(05-13)_
- **5** · [JuzzyDee/audio-analyzer-rs](https://github.com/JuzzyDee/audio-analyzer-rs) — pure-Rust MCP with the whole MIR stack incl. K-S key, pitch-class, tonnetz. _(05-14 · both)_

## ASA — DSP, loudness, MIR features

- **5** · [creightonlinza/forever-jukebox](https://github.com/creightonlinza/forever-jukebox) — local Infinite-Jukebox; analysis → JSON contract. _(05-13 · ★ ASA plan Track 3)_
- **5** · [DarienBrito/EssentiaTD](https://github.com/DarienBrito/EssentiaTD) — Essentia CHOPs (spectrum/mel/MFCC/key/onset/R128). _(05-14)_
- **4** · [httpsworldview/openmeters](https://github.com/httpsworldview/openmeters) — Rust BS.1770-5 LUFS/true-peak + spectral-reassignment spectrogram. _(05-13 · ★ ASA plan Track 1)_
- **4** · [Ircam-Partiels/Partiels](https://github.com/Ircam-Partiels/Partiels) — IRCAM Vamp host; CSV/SDIF/JSON export schemas. _(05-13 · ★ ASA plan Track 2)_
- **4** · [sanderwood/clamp3](https://github.com/sanderwood/clamp3) — multimodal (text/score/audio/MIDI) contrastive embeddings + retrieval. _(05-13 PM)_
- **4** · [linuxmatters/jivetalking](https://github.com/linuxmatters/jivetalking) — measure-then-choose-params EBU R128 loudness pipeline. _(05-13 PM)_
- **4** · [openclaw/songsee](https://github.com/openclaw/songsee) — Go CLI: 9 frequency-domain views (mel/chroma/HPSS/tempogram/MFCC…). _(05-14)_
- **4** · [jhartquist/resonators](https://github.com/jhartquist/resonators) — Resonate per-sample spectral analysis with WASM bindings. _(05-14)_
- **4** · [Angel2mp3/AudioAuditor](https://github.com/Angel2mp3/AudioAuditor) — fake-lossless / clipping detection + dynamic-range & true-peak. _(05-14)_
- **4** · [WB2024/Essentia-to-Metadata](https://github.com/WB2024/Essentia-to-Metadata) — fully-offline Essentia ML genre/mood tagging. _(05-14)_
- **4** · [wavey-ai/mel-spec](https://github.com/wavey-ai/mel-spec) — Rust mel/STFT primitives + WASM mel-image interchange. _(05-17)_
- **4** · [CPJKU/beat_this](https://github.com/CPJKU/beat_this) — ISMIR-2024 transformer beat/downbeat tracker (no DBN post-proc). _(05-19)_
- **3** · [bananaofhappiness/soundscope](https://github.com/bananaofhappiness/soundscope) — Rust TUI LUFS/true-peak/FFT; BS.1770 numerical cross-check. _(05-13)_
- **3** · [JeffreyCA/spleeter-web](https://github.com/JeffreyCA/spleeter-web) — React/Django stem-separation app. _(05-13 · ★ ASA plan: filed for later)_
- **3** · [crlandsc/moises-light](https://github.com/crlandsc/moises-light) — band-split U-Net reference implementation. _(05-13 PM)_
- **3** · [sweetspotsoundsystem/stemgen-rt](https://github.com/sweetspotsoundsystem/stemgen-rt) — real-time 4-stem JUCE/VST plugin plumbing. _(05-13 PM)_
- **3** · [matteospanio/torchfx](https://github.com/matteospanio/torchfx) — PyTorch-native composable/differentiable DSP filters. _(05-13 PM)_
- **3** · [craiglush/navidrome-mood-plugin](https://github.com/craiglush/navidrome-mood-plugin) — Essentia-TF mood/danceability/energy/BPM tagging. _(05-14)_
- **3** · [NeptuneHub/AudioMuse-AI-NV-plugin](https://github.com/NeptuneHub/AudioMuse-AI-NV-plugin) — Essentia-driven song/artist similarity. _(05-14)_
- **3** · [undef13/splifft](https://github.com/undef13/splifft) — modular separation/transcription CLI; 110+ model registry. _(05-17)_
- **3** · [Boof2015/astra](https://github.com/Boof2015/astra) — Electron audiophile player; analysis/output split + visualizer rack UX. _(05-17)_
- **3** · [casantosmu/audiodeck](https://github.com/casantosmu/audiodeck) — Go + browser spectrogram fake-lossless library scanner. _(05-18)_
- **3** · [mhartzel/freelcs](https://github.com/mhartzel/freelcs) — EBU R128 hotfolder loudness-correction server. _(05-18)_
- **3** · [Polochon-street/bliss-rs](https://github.com/Polochon-street/bliss-rs) — chroma/tempo/timbre similarity feature vectors. _(05-19)_
- **3** · [MTG/gaia](https://github.com/MTG/gaia) — Essentia's similarity/classifier companion (high-level models). _(05-19)_

## Harmonia — chords, key, theory

- **5** · [ptnghia-j/ChordMiniApp](https://github.com/ptnghia-j/ChordMiniApp) — chord recognition + beat + lyrics + OpenSheetMusicDisplay. _(05-13)_
- **4** · [spyroskantarelis/chordonomicon](https://github.com/spyroskantarelis/chordonomicon) — 666K section-labelled chord progressions dataset. _(05-13)_
- **4** · [vpavlenko/rawl](https://github.com/vpavlenko/rawl) — pitch-class-coloured MIDI/MusicXML harmony visualizer. _(05-13)_
- **4** · [madderscientist/noteDigger](https://github.com/madderscientist/noteDigger) — zero-deps pure-JS audio→MIDI (FFT/CQT/ONNX). _(05-13 PM)_
- **4** · [dogayuksel/webKeyFinder](https://github.com/dogayuksel/webKeyFinder) — libKeyFinder→WASM in AudioWorklet + workers (Preact). _(05-18)_
- **4** · [pianosnake/ireal-reader](https://github.com/pianosnake/ireal-reader) — iReal Pro charts → structured chord-symbol JSON. _(05-19)_
- **3** · [chromatone/chromatone.center](https://github.com/chromatone/chromatone.center) — Tonal.js + abcjs chord/scale/pitch-colour PWA. _(05-13 PM)_
- **3** · [marcus/good-composer](https://github.com/marcus/good-composer) — streaming LLM→MIDI with live Tone.js piano-roll. _(05-14)_
- **3** · [markwilkins/midi-chord-reader](https://github.com/markwilkins/midi-chord-reader) — JUCE plugin: name chords from MIDI (slash inversions, passing-tone filter). _(05-17)_
- **3** · [Natooz/MidiTok](https://github.com/Natooz/MidiTok) — canonical MIDI/abc tokenizer library. _(05-17)_
- **3** · [brightlikethelight/music21-mcp-server](https://github.com/brightlikethelight/music21-mcp-server) — music21 theory tools (Roman numerals, cadences, voice-leading) over MCP. _(05-18)_
- **3** · [CPJKU/partitura](https://github.com/CPJKU/partitura) — symbolic score model (MusicXML/MIDI/kern/MEI). _(05-19)_

## Relevant to both

- **5** · [JuzzyDee/audio-analyzer-rs](https://github.com/JuzzyDee/audio-analyzer-rs) — pure-Rust MCP; full MIR stack incl. K-S key, pitch-class, tonnetz, R128. _(05-14)_
- **4** · [rzru/nightingale](https://github.com/rzru/nightingale) — Tauri karaoke: separation + transcription + pitch scoring + key/tempo shift. _(05-13 · ★ ASA plan: filed for later)_
- **4** · [dreamrec/LivePilot](https://github.com/dreamrec/LivePilot) — large Ableton-MCP with spectral + Krumhansl-Schmuckler key bridge. _(05-17)_
- **4** · [a1ex90/MusicalKeyCNN](https://github.com/a1ex90/MusicalKeyCNN) — CQT-CNN key estimation with Camelot-wheel output. _(05-19)_
- **3** · [uisato/ableton-mcp-extended](https://github.com/uisato/ableton-mcp-extended) — TCP+UDP Ableton MCP with ElevenLabs TTS. _(05-18)_
- **3** · [ifeelvoid/keyfinder](https://github.com/ifeelvoid/keyfinder) — from-scratch Krumhansl-Schmuckler key/BPM detector (Swift app + VST). _(05-19)_

## Tangential / tooling / DAW + MCP

- **3** · [adamjmurray/producer-pal](https://github.com/adamjmurray/producer-pal) — Max-for-Live + MCP Ableton control (cleanest M4L↔MCP example). _(05-13)_
- **3** · [openvpi/GAME](https://github.com/openvpi/GAME) — singing-voice→MIDI via structured-denoising diffusion. _(05-13)_
- **3** · [prabal-rje/latentscore](https://github.com/prabal-rje/latentscore) — retrieval-based ambient generation (no-GPU, ~2s). _(05-13)_
- **3** · [JorenSix/Olaf](https://github.com/JorenSix/Olaf) — portable acoustic fingerprinting (C, WASM, ESP32). _(05-13 · ★ ASA plan: filed for later)_
- **3** · [williamzujkowski/live-coding-music-mcp](https://github.com/williamzujkowski/live-coding-music-mcp) — Strudel.cc live-coding over MCP. _(05-13 PM)_
- **3** · [Ryan5453/demucs-next](https://github.com/Ryan5453/demucs-next) — modernized, faster Demucs fork. _(05-14)_
- **3** · [bschoepke/ableton-live-mcp](https://github.com/bschoepke/ableton-live-mcp) — Ableton MCP betting on agent-`eval` of arbitrary Python. _(05-17)_
- **3** · [phones24/ep133-export-to-daw](https://github.com/phones24/ep133-export-to-daw) — EP-133 → DAWproject/REAPER/MIDI via WebMIDI. _(05-17)_
- **3** · [gluon/Void-LinkAudio](https://github.com/gluon/Void-LinkAudio) — sample-accurate beat-synced audio over LAN (Max/TD/VCV/oF/Live). _(05-17)_
- **3** · [Conceptual-Machines/magda-core](https://github.com/Conceptual-Machines/magda-core) — AI-first JUCE/Tracktion DAW; NL→DSL session edits. _(05-17)_
- **3** · [andremichelle/openDAW](https://github.com/andremichelle/openDAW) — framework-light web DAW (browser-first reference). _(05-17)_

## Notes on divergent vetting

Where independent sweeps disagreed, the listing above keeps the most
favourable verdict (per the "keep included" rule). For the record:

- **DarienBrito/EssentiaTD** — 4 (05-14), re-read up to **5** in the 05-17 note.
- **WB2024/Essentia-to-Metadata** — 3 (05-14), re-read up to **4** in the 05-17 note.
- **wavey-ai/mel-spec** — **4** (05-17), re-surfaced at 3 in the 05-19 sweep.
- **undef13/splifft** — 3 in both 05-17 and 05-19.
- **marcus/good-composer** — 3 in both 05-14 and 05-19.
- **mhartzel/freelcs** — dropped in 05-17, kept at **3** in 05-18, dropped again in 05-19.
- **uisato/ableton-mcp-extended** — dropped in 05-17, kept at **3** in 05-18.
- **ifeelvoid/keyfinder** — dropped in 05-18, kept at **3** in 05-19.
- **Ryan5453/demucs-next** — kept at **3** in 05-14, dropped in 05-19.
