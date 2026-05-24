# music-asa / llm-music-generation

LLM-for-music, audio-LLM understanding, and music generation — the model layer
adjacent to ASA's **Gemini Phase-2 interpreter** (which maps the deterministic
Phase-1 analysis JSON to Ableton device/parameter advice) and its **Phase-3** on-demand
audition-sample generation. Scores are **1–5 ASA-relevance** + flag: `ASA` · `H`
(Harmonia = real but unpublished, dependency-free single-file vanilla-JS tool — conceptual
idea-only tag; see `../README.md`) · `Both` · `tang`. Corrected scores
follow `discoveries/reanalysis-2026-05-20.md` — LLM/music tooling is on-theme because
ASA *is* an LLM app; pure text-to-music gen models stay low unless they touch the
analysis/interpretation or Phase-3 audition path.

## Strong (4–5)

- **5/ASA** · [OpenMOSS/MOSS-Music](https://github.com/OpenMOSS/MOSS-Music) · `maturity:model`
  Open 8B music-understanding LMM (MOSS-Audio-Encoder + Qwen3-8B; weights on HF/ModelScope, SGLang/Transformers/Gradio inference) taking raw audio and doing timestamped lyrics ASR, captioning, intro/verse/chorus structural analysis, chord/key/tempo reasoning, and long-form musical Q&A. The single most on-point new find for ASA's Gemini layer — a self-hostable model producing exactly the LLM-interpreted analysis ASA gets from Essentia+Gemini. **Mine:** evaluate as a (partial) self-hosted replacement for the Gemini Phase-2 layer; its task decomposition maps straight onto ASA's analysis JSON, so fork its prompt/task structure even if you keep Gemini. _(surfaced 05-21 · tags: audio-llm, understanding, lmm, structure)_
- **4/ASA** · [sanderwood/clamp3](https://github.com/sanderwood/clamp3) · `Python` · `239★` · `active:2025-02` · `maturity:model`
  ACL 2025 framework contrastively aligning text, sheet music, audio (via MERT features), MIDI, and images into one 27-language embedding space — CLAP but multi-modal — with retrieval primitives (find-tracks-like-this, prompt-to-track). **Mine:** drop in the audio-side feature extractor + retrieval primitives ahead of any tagging/similarity reach in ASA; the shared embedding space is the "tracks like this / prompt to track" axis. _(surfaced 05-13 PM · tags: embeddings, multimodal, retrieval, clap)_
- **4/ASA** · [marcus/good-composer](https://github.com/marcus/good-composer) · `JavaScript` · `33★` · `active:2025-12` · `maturity:app`
  Streams MIDI from an LLM (Ollama / OpenRouter) over WebSocket and plays it live with a Tone.js piano-roll as it generates; FastAPI backend, Tone.js frontend. **FastAPI + WebSocket streaming + React + LLM is ASA's exact stack pattern** for streaming Phase-2 output to the UI (no music-theory lib involved). **Mine:** fork the FastAPI-WebSocket-streaming + progressive piano-roll wiring as the template for streaming ASA's Gemini recommendations to the React frontend as they generate. _(surfaced 05-14 · re-scored 3→4 on 05-20 · tags: llm, streaming, fastapi, websocket)_

## Useful references (3)

- **3/ASA** · [geshang777/GaMMA](https://github.com/geshang777/GaMMA) · `maturity:reference`
  Research implementation for "joint global-temporal music understanding in large multimodal models" — an audio-LLM reasoning over both whole-track and time-localized musical structure. Same direction as ASA's LLM layer; a paper repo rather than a packaged model, so less immediately usable than MOSS-Music. **Mine:** read for the global+temporal music-understanding architecture as a second data point for ASA's interpretation layer; not a drop-in. _(surfaced 05-21 · tags: audio-llm, understanding, research, structure)_
- **3/ASA** · [innermost47/ai-dj](https://github.com/innermost47/ai-dj) · `Python` · `maturity:app`
  Server-side Python (Stable Audio Open) loop-generator VST, now *OBSIDIAN-Neural*. Originally dropped (05-13) as "pure generation, no analysis," un-dropped on 05-20 because **ASA Phase-3 = on-demand audition-sample generation** — this is a Phase-3 plumbing reference. **Mine:** fork the Stable-Audio-Open loop-generation server as a starting point for ASA's Phase-3 audition-sample generator. _(surfaced 05-13 · re-scored drop→3 on 05-20 · tags: generation, stable-audio, phase3, vst)_
- **3/tang** · [prabal-rje/latentscore](https://github.com/prabal-rje/latentscore) · `Python` · `36★` · `maturity:app`
  Retrieval-based ambient generation: a sentence-transformer (or LAION-CLAP) embeds a prompt, cosine-matches against ~10k pre-computed synth configs, and drives a real-time CPU synth — no GPU, ~2s latency. "Music as configuration retrieval," not a generative model. **Mine:** the prompt→embed→nearest-config→synth pattern is a cheap, no-GPU template for a Phase-3 audition path if ASA wants config-retrieval rather than neural generation. _(surfaced 05-13 · tags: retrieval, ambient, clap, synth)_

## Marginal — kept with a note (low)

- **low/tang** · [ace-step/ACE-Step-1.5](https://github.com/ace-step/ACE-Step-1.5) · `maturity:model`
  Large text-to-music generation model; well-known and orthogonal to ASA's analysis/interpretation core. Dropped 05-13 PM. **Mine:** only as the upstream model if ASA's Phase-3 ever wants full-track gen rather than short auditions. _(surfaced 05-13 PM · tags: text-to-music, generation, known)_
- **low/tang** · [fspecii/ace-step-ui](https://github.com/fspecii/ace-step-ui) · `maturity:app`
  UI over ACE-Step; generation-side, no analysis. Dropped 05-13 PM. **Mine:** UI patterns for driving a gen model only. _(surfaced 05-13 PM · tags: ui, acestep, generation)_
- **low/tang** · [HeartMuLa/heartlib](https://github.com/HeartMuLa/heartlib) · `maturity:lib`
  Music-generation library; well-known/orthogonal to ASA. Dropped 05-13 PM. **Mine:** nothing specific to ASA's analysis path. _(surfaced 05-13 PM · tags: generation, known)_
- **low/tang** · [ubisoft/ComfyUI-Chord](https://github.com/ubisoft/ComfyUI-Chord) · `maturity:app`
  ComfyUI node wrapping Ubisoft's "Chord" audio model — generation-side and ComfyUI-bound, off-target for both streams. Dropped 05-21. **Mine:** nothing transferable beyond awareness of the Chord model. _(surfaced 05-21 · tags: comfyui, generation, chord-model)_
- **low/tang** · [RowanUnderwood/Synesthesia-AI-Video-Director](https://github.com/RowanUnderwood/Synesthesia-AI-Video-Director) · `maturity:app`
  Audio→LLM→video tool, but the "audio analysis" is pydub silence detection and the LLM writes *video* prompts — off-domain for ASA. Dropped 05-21. **Mine:** nothing on the audio-analysis side. _(surfaced 05-21 · tags: audio-to-video, off-domain)_
- **low/tang** · [simonholliday/subsequence](https://github.com/simonholliday/subsequence) · `maturity:app`
  Generative MIDI sequencer — not analysis. Dropped 05-17. **Mine:** generative-sequencer UX ideas only. _(surfaced 05-17 · tags: midi, sequencer, generative)_
- **low/tang** · [scragnog/HOT-Step-CPP](https://github.com/scragnog/HOT-Step-CPP) · `maturity:app`
  UI shim over `acestep.cpp`; ACE-Step is already covered. Dropped 05-17. **Mine:** nothing beyond the ACE-Step model itself. _(surfaced 05-17 · tags: ui-shim, acestep, cpp)_
- **low/tang** · [rsxdalv/TTS-WebUI](https://github.com/rsxdalv/TTS-WebUI) · `maturity:app`
  Generation/TTS WebUI with no analysis surface. Dropped 05-17. **Mine:** multi-model WebUI scaffolding only; nothing for ASA's analysis path. _(surfaced 05-17 · tags: tts, webui, generation)_
