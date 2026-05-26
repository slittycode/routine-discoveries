# pitch-beat-tempo — pitch, beat, tempo & fingerprinting

ASA's **pitch** path (Layer 2: `torchcrepe` on Demucs stems) plus beat/tempo
estimation for the analysis JSON and audio-fingerprinting/identification on the
margins. Pitch and beat are **current ASA scope**, not hypothetical. Native
C/C++/Rust/Python and PyTorch models are first-class — no browser/WASM credit.
Scores are **1–5 relevance** + flag: `ASA` · `H` (Harmonia = **conceptual reference
only**, unpublished single-file vanilla JS) · `Both` · `tang`. See `../README.md`;
corrected scores follow `discoveries/reanalysis-2026-05-20.md` (Harmonia framing
further corrected 2026-05-26).

## Core dependency (5)

- **5/ASA** · [maxrmorrison/torchcrepe](https://github.com/maxrmorrison/torchcrepe) · `Python` · `maturity:lib`
  PyTorch port of the CREPE pitch tracker (per-frame F0 + periodicity/confidence, with decoding and filtering helpers). **ASA's own L2 dependency** — runs on Demucs stems for note/pitch analysis. **Mine:** the model ASA already calls; keep current and reuse its periodicity-thresholding/decoding as the reference for ASA's pitch stage. _(surfaced 05-20 (noted as ASA dep) · tags: pitch, crepe, f0, pytorch, core-dep)_

## Strong (4)

- **4/ASA** · [CPJKU/beat_this](https://github.com/CPJKU/beat_this) · `Python` · `286★` · `active:2026-05` · `maturity:model`
  Official ISMIR-2024 beat/downbeat tracker ("Beat This!") that drops the traditional DBN post-processing for a transformer with a shift-tolerant loss; ships CLI + Python API and `.beats` export. **Mine:** a current, accurate **drop-in for ASA's tempo/beat stage** that's lighter to wire up than madmom — fork the inference path and the `.beats` schema. _(surfaced 05-19 · tags: beat, downbeat, tempo, transformer, ismir2024)_

## Tangential — useful technique / off-core (2–3)

- **3/tang** · [openvpi/GAME](https://github.com/openvpi/GAME) · `Python` · `161★` · `maturity:model`
  Singing-voice → MIDI transcription via D3PM (structured denoising diffusion) with adaptive boundary extraction; ONNX-exportable, Python 3.12, PyTorch Lightning. Pitch-adjacent (ASA uses torchcrepe, not transcription). **Mine:** if a sung-input → note path is ever wanted, the F0 + boundary outputs are the upstream; otherwise a technique reference for diffusion-based transcription. _(surfaced 05-13 · tags: singing, midi, diffusion, onnx, transcription)_
- **2/tang** · [JorenSix/Olaf](https://github.com/JorenSix/Olaf) · `C` · `396★` · `active:2026` · `maturity:lib`
  Portable acoustic **fingerprinting** in C with WASM and ESP32 targets (created 2020, still pushed). **Mine:** clean reference *if* you ever need audio identification or cross-take alignment — but strip the in-browser novelty and identification isn't an ASA use case (downgraded 3→2 on 05-20, the ★ filed-for-later plan was withdrawn). _(surfaced 05-13 · re-scored 3→2 on 05-20 · tags: fingerprinting, c, identification, off-use)_

## Marginal — kept with a note (low)

- **low/tang** · [k2-fsa/sherpa-onnx](https://github.com/k2-fsa/sherpa-onnx) · `maturity:lib`
  Primarily a **speech** toolkit (ASR/TTS/speaker-diarization, ONNX runtime, many language bindings); the music angle is marginal. Dropped 05-17. **Mine:** only if ASA ever needs on-device ASR (e.g. lyric transcription) — the ONNX deployment plumbing, not anything music-MIR. _(surfaced 05-17 · dropped · tags: speech, asr, onnx, marginal-music)_
- **low/tang** · [lunashia/o-m_beatmap_trainer](https://github.com/lunashia/o-m_beatmap_trainer) · `maturity:alpha`
  osu!mania next-event trainer; the README never exposes the audio-feature layer and it's game-specific. Dropped 05-19. **Mine:** nothing usable for ASA — the rhythm-game beatmap framing is the only (off-target) idea. _(surfaced 05-19 · dropped · tags: beatmap, osu, game-specific, off-stack)_
- **low/tang** · [emjjkk/beat-detection](https://github.com/emjjkk/beat-detection) · `maturity:alpha`
  Niche beat-detection repo, under the quality/star bar. Dropped 05-21. **Mine:** nothing beyond a minimal beat-onset reference; ASA's beat stage is far better served by beat_this. _(surfaced 05-21 · dropped · tags: beat, niche, sub-bar)_
