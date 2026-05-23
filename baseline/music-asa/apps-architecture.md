# apps-architecture — apps, media-server, similarity & deployment architecture

Full **analysis apps**, media-server integrations, track-to-track similarity, and
the job-queue / worker / deployment shapes ASA needs in hosted mode (Python 3.11 +
FastAPI backend, React 19 frontend, measurement → pitch/note → Gemini-interpretation
queue). ASA is an **app**, so React UIs + API/contract + queue/deployment all count.
Scores are **1–5 relevance** + flag: `ASA` · `H` (Harmonia = conceptual ref) · `Both` ·
`tang`. See `../README.md`; corrected scores follow
`discoveries/reanalysis-2026-05-20.md`.

## Cross-domain (full entry here)

- **4/Both** · [rzru/nightingale](https://github.com/rzru/nightingale) · `Rust` · `1.1k★` · `active:2026-03` · `maturity:app`
  Tauri (Rust + React) karaoke app combining Demucs/UVR vocal isolation, WhisperX/Parakeet-v3 lyric transcription with word timestamps, real-time pitch scoring, and key/tempo shifting. Hits the whole pipeline at once. **Mine:** the local-PyTorch-from-Tauri shape is a template for ASA's local mode; fork the separation + pitch-scoring + key/tempo-shift wiring (the pitch/key logic is also Harmonia-adjacent). _(surfaced 05-13 · ★ ASA plan: filed-for-later · tags: tauri, demucs, transcription, pitch, key-shift)_ — **stub also in `stem-separation.md`.**

## Strong (4–5)

- **5/ASA** · [creightonlinza/forever-jukebox](https://github.com/creightonlinza/forever-jukebox) · `TypeScript/Python` · `24★` · `active:2026-01` · `maturity:app`
  End-to-end Infinite-Jukebox replacement: madmom-beats-lite + Essentia generate beats/segments/sections locally and serve them through a small REST API, replacing Spotify's now-dead Audio Analysis endpoint. **Mine:** the direct precedent for the shape of ASA's **analysis → JSON contract** and a local REST analysis service — fork the API surface and the beat/segment/section schema. _(surfaced 05-13 · ★ ASA plan Track 3 · tags: jukebox, essentia, beats, rest, json-contract)_
- **4/ASA** · [Ircam-Partiels/Partiels](https://github.com/Ircam-Partiels/Partiels) · `C++` · `74★` · `maturity:app`
  IRCAM's Vamp-plugin host wrapping FFT, LPC, transients, F0, formants, and tempo behind a JUCE GUI, with batch CLI and exports to CSV/SDIF/JSON/REAPER/Max/PD. **Mine:** reference for how a serious tool structures multi-track/multi-channel analysis pipelines and result interchange; the SDIF/JSON export schemas are worth lifting for ASA result storage. _(surfaced 05-13 · ★ ASA plan Track 2 · tags: vamp, juce, export, sdif, interchange)_
- **4/ASA** · [Polochon-street/bliss-rs](https://github.com/Polochon-street/bliss-rs) · `Rust` · `159★` · `active:2026-05` · `maturity:lib`
  Native Rust song-analysis library extracting chroma, tempo, and timbral features to compute track-to-track distance for automatic playlists (Spotify-Radio style). **Mine:** the compact feature vector + similarity framing is a clean **"tracks like this"** axis to add server-side; "off-stack" was the old browser bias — Rust is first-class. _(surfaced 05-19 · re-scored 3→4 on 05-20 · tags: rust, similarity, chroma, tempo, playlists)_
- **4/ASA** · [NeptuneHub/AudioMuse-AI](https://github.com/NeptuneHub/AudioMuse-AI) · `Python` · `1.7k★` · `active:2026-05` · `maturity:app`
  The analysis core behind the NV/Jellyfin plugins: **Flask + Redis/RQ workers + PostgreSQL + Docker/K8s**, librosa/ONNX/CLAP, REST + Swagger, and a chat module. Very active. **Mine:** a concrete, working **blueprint for ASA's hosted worker-queue mode** — copy the Flask + RQ + Postgres + container topology and the REST/Swagger surface. _(surfaced 05-20 · tags: flask, redis-rq, postgres, k8s, queue, blueprint)_
- **4/ASA** · [NeptuneHub/AudioMuse-AI-NV-plugin](https://github.com/NeptuneHub/AudioMuse-AI-NV-plugin) · `240★` · `active:2026-01` · `maturity:app`
  Navidrome plugin doing sonic-analysis-based song/artist similarity for instant-mix and radio, backed by a Flask + Worker analysis container. **Mine:** thin client of AudioMuse-AI — the value is the **queue/worker architecture** behind it as a second data point on Essentia/librosa-driven similarity at media-server scale. _(surfaced 05-14 · re-scored 3→4 on 05-20 · tags: navidrome, similarity, flask, worker, plugin)_

## Cross-domain stub (full entry elsewhere)

- **5/Both** · [JuzzyDee/audio-analyzer-rs](https://github.com/JuzzyDee/audio-analyzer-rs) · `Rust` · `21★` · `active:2026-03` · `maturity:app`
  Pure-Rust MCP server extracting ASA's whole L1 MIR stack (K-S key, pitch-class, tonnetz, R128, HPSS, section boundaries) in <2s/track, no Python/FFmpeg — also a full MIR **app**. **Full entry in `chord-key.md`** (harmonic core). _(surfaced 05-14 · tags: rust, mcp, mir-app, key, r128)_

## Marginal — kept with a note (low)

- **low/ASA** · [NeptuneHub/audiomuse-ai-plugin](https://github.com/NeptuneHub/audiomuse-ai-plugin) · `maturity:app`
  Jellyfin sibling of the AudioMuse Navidrome plugin — same librosa+ONNX+LLM sonic-analysis architecture, no new DSP. Dropped 05-21. **Mine:** only the Jellyfin-side integration glue if targeting Jellyfin; architecturally identical to the NV plugin already logged. _(surfaced 05-21 · dropped · tags: jellyfin, sibling, plugin, redundant)_
- **low/ASA** · [NeptuneHub/AudioMuse-AI-MusicServer](https://github.com/NeptuneHub/AudioMuse-AI-MusicServer) · `maturity:app`
  Integration shell wiring AudioMuse-AI to a music server — no standalone analysis content. Dropped 05-21. **Mine:** wiring/deployment reference only; the real substance is in `AudioMuse-AI`. _(surfaced 05-21 · dropped · tags: integration-shell, music-server, deployment)_
- **low/tang** · [snejus/beetcamp](https://github.com/snejus/beetcamp) · `maturity:lib`
  Bandcamp **metadata** autotagger plugin for beets — off-topic (catalog metadata, no audio analysis). Dropped 05-19. **Mine:** nothing for ASA; only relevant if a Bandcamp-import metadata path were ever needed. _(surfaced 05-19 · dropped · tags: bandcamp, metadata, beets, off-topic)_
