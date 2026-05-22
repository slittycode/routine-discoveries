# loudness-dynamics-dsp — loudness/R128, true-peak, DSP filters, spectrogram/viz

ASA's Phase-1 **loudness + dynamics** stage and the spectrogram/visualization
surface that backs its analysis JSON. EBU R128 / ITU-R BS.1770 LUFS, true-peak,
LRA, dynamic-range; native DSP filters; and mel/spectral renderers. ASA measures
server-side then (Phase 2) Gemini turns the numbers into Ableton device/param
advice — so "measure first, then choose parameters" pipelines are gold here.
★ = has an `incorporations/` plan.

## Tier 1 — strong references / fork-and-run

- **4/ASA** · [httpsworldview/openmeters](https://github.com/httpsworldview/openmeters) · `Rust` · `135★` · `created:2025-10` · `maturity:app`
  Linux audio metering in Rust: short-term/momentary LUFS to **ITU-R BS.1770-5**, true peak, A-weighted spectrum, spectrogram with **spectral reassignment**, oscilloscope, goniometer (wgpu/Iced UI). **Mine:** lift the reassignment trick and the exact BS.1770 revision into ASA's loudness/dynamics stage. _(surfaced 05-13 · ★ ASA plan Track 1 · tags: rust, lufs, bs1770, true-peak, spectral-reassignment)_
- **4/ASA** · [complexlogic/rsgain](https://github.com/complexlogic/rsgain) · `C++` · `603★` · `active:2026` · `maturity:app`
  Native C++ EBU R128 + true-peak + **ReplayGain 2.0** CLI. **Mine:** a Phase-1 loudness reference in the same role as openmeters/soundscope — a clean, fast native R128/true-peak implementation to cross-check; was wrongly dropped as "off-stack/in-browser." _(surfaced 05-13, re-scored drop→4 on 05-20 · tags: native, c++, r128, true-peak, replaygain)_
- **4/ASA** · [linuxmatters/jivetalking](https://github.com/linuxmatters/jivetalking) · `Go` · `71★` · `created:2025-11` · `maturity:app`
  Go CLI that measures integrated LUFS, true peak, LRA (EBU R128), noise floor and spectral signature, then **picks per-pass filter params** from that — adaptive de-essing, gating, comp, two-stage R128 normalisation to -16 LUFS. **Mine:** the "measure first, then choose parameters" pipeline is exactly ASA's Phase1→Phase2 logic; model the recommendation output on it. _(surfaced 05-13 PM · tags: go, r128, adaptive-params, measure-then-choose)_
- **4/ASA** · [Angel2mp3/AudioAuditor](https://github.com/Angel2mp3/AudioAuditor) · `C#` · `70★` · `created:2026-03` · `maturity:app`
  Windows app flagging fake-lossless upsampling, digital clipping, MQA, and AI-generated audio, plus dynamic-range and true-peak (4× oversampled) measurement and a log-frequency spectrogram viewer. **Mine:** the dynamics + true-peak + spectral-ceiling "diagnose-then-recommend" logic overlaps ASA's dynamics stage directly; C#/Windows so reference, not reuse. _(surfaced 05-14 · tags: dynamics, true-peak, clipping, fake-lossless, reference)_
- **4/ASA** · [openclaw/songsee](https://github.com/openclaw/songsee) · `Go` · `59★` · `created:2026-01` · `maturity:app`
  Go CLI rendering 9 frequency-domain views — spectrogram, mel, chroma, HPSS, self-similarity, loudness, tempogram, MFCC, spectral flux — from any ffmpeg-readable file with no Python deps. **Mine:** ASA needs almost exactly this view catalog; study the native-Go FFT pipeline and the grid-combining output. _(surfaced 05-14 · tags: go, spectrogram, mel, chroma, hpss, tempogram, viz)_
- **4/ASA** · [wavey-ai/mel-spec](https://github.com/wavey-ai/mel-spec) · `Rust` · `89★` · `created:2023` · `maturity:lib`
  Rust mel/STFT primitives aligned with Whisper/librosa/PyTorch, a Sobel-edge VAD reusing the same mel tensor, and an 8-bit TGA interchange for shipping quantized mel spectrograms between processes. **Mine:** the **native Rust mel/STFT primitives** are squarely Phase-1 (the WASM/TGA-interchange credit is irrelevant to ASA); a fast embeddable mel extractor. _(surfaced 05-17 (4), re-surfaced 05-19 (3), held 4 on 05-20 · tags: rust, mel, stft, native)_

## Tier 2 — useful references

- **3/ASA** · [bananaofhappiness/soundscope](https://github.com/bananaofhappiness/soundscope) · `Rust` · `174★` · `maturity:app`
  Rust TUI loudness analyzer: LUFS + true peak + FFT spectrum + min-max-decimated waveform on files or live mic. **Mine:** a second BS.1770 implementation to numerically cross-check ASA's loudness numbers; smaller scope than openmeters, CLI-only. _(surfaced 05-13 · ★ oracle (numerical cross-check) · tags: rust, tui, lufs, true-peak, cross-check)_
- **3/ASA** · [matteospanio/torchfx](https://github.com/matteospanio/torchfx) · `Python` · `131★` · `created:2025-03` · `maturity:lib`
  PyTorch-native audio DSP — filters as `nn.Module`s, composable with `|`/`+`, differentiable, GPU; only a couple shipped (LoButterworth, ParametricEQ). **Mine:** the pattern for batching ASA's analysis filters on GPU server-side if it ever does a bulk pass; no MIR/loudness in-box. _(surfaced 05-13 PM · tags: pytorch, dsp, filters, gpu, server-side)_
- **3/ASA** · [jhartquist/resonators](https://github.com/jhartquist/resonators) · `Rust` · `86★` · `created:2026-04` · `maturity:lib`
  Rust implementation of the Resonate algorithm — fixed-memory, per-sample alternative to FFT/CQT for low-latency spectral analysis — with Python and WASM bindings. **Mine:** the Rust→PyO3 per-sample spectral angle (the WASM/browser-DSP rationale is **void** for ASA); niche vs Essentia. _(surfaced 05-14 (4), re-scored 4→3 on 05-20 · tags: rust, per-sample, spectral, pyo3, wasm-credit-void)_
- **3/ASA** · [mhartzel/freelcs](https://github.com/mhartzel/freelcs) · `Python` · `25★` · `active:2026` · `maturity:app`
  Hotfolder-driven EBU R128 loudness-correction server (Python, Docker, mono→5.1, per-stream); repo from 2012, still pushed. **Mine:** the drop-in/processed-out pipeline shape and the visual loudness-history output are a reference for ASA's loudness-stage UX/topology; old code. _(surfaced 05-18 (kept 3); dropped 05-17 & 05-19 as "not newly relevant" · tags: python, r128, docker, loudness-server, old-2012)_
- **3/ASA** · [Boof2015/astra](https://github.com/Boof2015/astra) · `TypeScript/C++` · `247★` · `created:2026-01` · `maturity:app`
  Electron + native C++ DSP audiophile player: 10-band parametric EQ with live frequency-response, seven realtime visualizers on a customizable rack, gapless bit-perfect output (WASAPI/CoreAudio/ALSA), Dolby Atmos decode. **Mine:** the decoupled analysis-path-vs-output-path architecture and the visualizer-rack UX are directly cribbable. _(surfaced 05-17 · tags: electron, c++, eq, visualizer-rack, analysis/output-split)_
- **3/ASA** · [casantosmu/audiodeck](https://github.com/casantosmu/audiodeck) · `TypeScript/Go` · `109★` · `created:2025-09` · `maturity:app`
  Self-hostable web spectrogram analyzer (Go server, browser-side render) sniffing out fake-lossless files via frequency-cutoff artifacts. **Mine:** the **Go server-side analysis** + thin-shim + client-render topology is a clean shape for an ASA library-scan UI (browser render is incidental); analysis itself is shallow. _(surfaced 05-18 · tags: go, spectrogram, fake-lossless, server-side, library-scan)_

## Tier 4 — marginal

- **low/ASA** · [WeebLabs/DSPi](https://github.com/WeebLabs/DSPi) · `maturity:reference`
  RP2040 audio-DSP firmware. **Mine:** hardware-only (microcontroller firmware); off ASA's server-side software stack — logged for completeness, not worth chasing. _(surfaced 05-13, dropped · tags: hardware, rp2040, firmware, off-stack)_
