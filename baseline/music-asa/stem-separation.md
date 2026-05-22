# stem-separation — source separation (ASA's Layer 2)

Stem separation is **current ASA scope**, not hypothetical: L2 runs `torchcrepe`
pitch **on Demucs stems** (PyTorch already in-stack). The 05-20 reanalysis
un-dropped a whole tier of separation repos that earlier sweeps had hedged as
"if ASA ever adds a separation pre-stage." Demucs itself is the spine; the rest
are forks, ports, app-shells, and references. ★ = `incorporations/` plan.

## Cross-domain stub (full entry elsewhere)

- **4/Both** · [rzru/nightingale](https://github.com/rzru/nightingale) · `Rust` · `1.1k★` · `active:2026-03` · `maturity:app`
  Tauri (Rust + React) app doing Demucs/UVR vocal isolation + transcription + pitch scoring + key/tempo shift; the separation half is on-stem-stack. **Full entry in `apps-architecture.md`** (it's primarily a full MIR app). _(surfaced 05-13 · ★ ASA plan: filed-for-later · tags: tauri, demucs, separation, app)_

## Tier 1 — core / fork-and-run

- **5/ASA** · [facebookresearch/demucs](https://github.com/facebookresearch/demucs) · `Python` · `maturity:model`
  Hybrid Transformer Demucs — the state-of-the-art music source-separation model. **ASA's own L2 dependency** (stems feed torchcrepe pitch). **Mine:** the model ASA already runs; the thing to keep current, swap variants of, or speed up (see demucs-next / demucs-mlx). _(surfaced 05-20 (noted as ASA dep) · tags: pytorch, separation, core-dep, model)_

## Tier 2 — strong references / drop-ins

- **4/ASA** · [JeffreyCA/spleeter-web](https://github.com/JeffreyCA/spleeter-web) · `TypeScript/Python` · `544★` · `maturity:app`
  Self-hostable React + Django (+ Celery/Redis + Docker) app for vocal/bass/drums isolation backed by Spleeter, **Demucs**, and BS-RoFormer, with a job queue. **Mine:** React + queue + Docker running Demucs **is ASA's app+queue+L2 shape** (only the web framework differs); a template for a stem-separation stage UI. _(surfaced 05-13 (3), re-scored 3→4 on 05-20 · ★ ASA plan: filed-for-later · tags: react, django, celery, demucs, queue, app)_
- **4/ASA** · [Ryan5453/demucs-next](https://github.com/Ryan5453/demucs-next) · `Python` · `26★` · `maturity:alpha`
  Modernized fork of Demucs (current PyTorch/TorchCodec, Cog REST integration) reporting ~2–3× faster separation at equal-or-better SDR. **Mine:** a direct **L2 speed win** — drop-in faster Demucs with REST packaging; was dropped 05-19 as "thin fork" under the separation-out-of-scope bias. _(surfaced 05-14 (3), re-scored 3→4 on 05-20 · tags: pytorch, demucs-fork, faster, cog-rest)_
- **4/ASA** · [ssmall256/demucs-mlx](https://github.com/ssmall256/demucs-mlx) · `Python` · `maturity:lib`
  Demucs ported to Apple MLX — pip-importable (`from demucs_mlx import Separator`), ~73× realtime on Apple Silicon. **Mine:** ASA is local-first and its users are Mac producers → an **L2 drop-in** for fast on-device separation; was wrongly dropped as "a straight port." _(surfaced 05-13 (dropped), re-scored drop→4 on 05-20 · tags: mlx, apple-silicon, demucs, drop-in, local-first)_
- **4/ASA** · [undef13/splifft](https://github.com/undef13/splifft) · `Python` · `40★` · `created:2025-06` · `maturity:alpha`
  Lightweight Python separation/transcription CLI: BS-/Mel-RoFormer, MDX23C TFC-TDF v3, plus `beat this!`, PESTO pitch, basic-pitch — a registry of 110+ community models, downloaded on demand. **Mine:** the modular "swap separation backend" abstraction (plain data, pure functions, minimal deps) is real now that L2 is in-scope. _(surfaced 05-17 & 05-19 (3), re-scored 3→4 on 05-20 · tags: python, registry, roformer, modular, swap-backend)_

## Tier 3 — references

- **3/ASA** · [crlandsc/moises-light](https://github.com/crlandsc/moises-light) · `Python` · `27★` · `created:2026-03` · `maturity:model`
  Unofficial PyTorch impl of "Moises-Light: Resource-efficient Band-split U-Net" (WASPAA 2025) with RoPE bottleneck from BS-RoFormer; training-only, no weights. **Mine:** a clean modern band-split reference if ASA wants its own separation; otherwise read the paper. _(surfaced 05-13 PM · tags: pytorch, band-split, unet, training-only, no-weights)_
- **3/ASA** · [sweetspotsoundsystem/stemgen-rt](https://github.com/sweetspotsoundsystem/stemgen-rt) · `C++` · `27★` · `created:2026-01` · `maturity:app`
  Real-time HS-TasNet 4-stem separation as a JUCE/VST3/AU plugin at 11.6 ms latency, async inference threading, crossover/gating DSP; model is binary-only. **Mine:** reference for the **plumbing** (async ONNX in a plugin callback, 44.1k constraint), not a model to lift. _(surfaced 05-13 PM · tags: juce, vst, realtime, tasnet, plumbing)_
- **3/ASA** · [asteroid-team/asteroid](https://github.com/asteroid-team/asteroid) · `Python` · `maturity:lib`
  Mature PyTorch audio source-separation toolkit (recipes, models, datasets). **Mine:** a legitimate separation reference now that L2 is in-scope; was wrongly dropped as merely "established." _(surfaced 05-13 PM (dropped), re-scored drop→3 on 05-20 · tags: pytorch, separation-toolkit, established)_
- **3/ASA** · [paladini/voice-separator-demucs](https://github.com/paladini/voice-separator-demucs) · `Python` · `maturity:app`
  FastAPI front in front of Demucs. **Mine:** dropped thrice as "thin," but **FastAPI + Demucs is exactly ASA's L2-as-a-service shape** — a minimal reference for wrapping the separator as an endpoint. _(surfaced 05-17/05-18 (dropped), re-scored drop→3 on 05-20 · tags: fastapi, demucs, l2-as-a-service)_

## Tier 4 — marginal (wrapper / training-only / eval shell)

- **low/ASA** · [flarkflarkflark/STEMwerk-reaper](https://github.com/flarkflarkflark/STEMwerk-reaper) · `Lua` · `maturity:app`
  REAPER plugin: Lua glue calling audio-separator/Demucs from the DAW. **Mine:** thin wrapper — nothing new beyond the DAW integration; logged for completeness. _(surfaced 05-14, dropped repeatedly · tags: reaper, lua, wrapper, thin)_
- **low/ASA** · [crlandsc/torch-l1-snr](https://github.com/crlandsc/torch-l1-snr) · `Python` · `maturity:lib`
  L1-SNR loss functions for **training** separation models. **Mine:** out of scope — **ASA trains nothing** (it runs pretrained Demucs); only relevant if you ever fine-tune. _(surfaced 05-14, dropped · tags: pytorch, training-loss, out-of-scope)_
- **low/ASA** · [sigsep/sigsep-mus-eval](https://github.com/sigsep/sigsep-mus-eval) · `Python` · `maturity:lib`
  The MUSDB / BSS-eval separation-evaluation package (SDR/SIR/SAR). **Mine:** an eval shell — only useful for benchmarking separators, which ASA doesn't do; logged for completeness. _(surfaced 05-21, dropped · tags: eval, musdb, bss-eval, benchmark-only)_
