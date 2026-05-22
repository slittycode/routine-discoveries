# essentia-mir — Essentia ecosystem & native MIR feature extraction

Native (C/C++/Rust/Python), server-side feature extraction — ASA's **Layer 1**.
ASA runs **native Essentia 2.1b6** (Python 3.11-pinned because Essentia wheels
aren't published for 3.12+) for mel, tonal balance, dynamics and loudness. These
are the core dep, its companions, wrappers, and alternative native MIR toolkits.
No credit for browser/WASM/Essentia.js — native is first-class here.

## Tier 1 — core / fork-and-run

- **5/ASA** · [MTG/essentia](https://github.com/MTG/essentia) · `C++/Python` · `maturity:lib`
  The native C++/Python MIR library (spectral, MFCC, YinFFT, key, onset, EBU R128) + the Essentia model zoo — **ASA's own core Phase-1 dependency**. **Mine:** the algorithm reference and upgrade target; lift the exact algos ASA's L1 needs and the pretrained TF model set (genre/mood/danceability). _(surfaced 05-17, re-scored 05-20 · tags: essentia, dsp, core-dep, model-zoo)_
- **5/ASA** · [DarienBrito/EssentiaTD](https://github.com/DarienBrito/EssentiaTD) · `C++` · `91★` · `created:2026-03` · `maturity:lib`
  Five C++ CHOP plugins wrapping Essentia for TouchDesigner: spectrum, mel bands, MFCCs, pitch, key/scale, onset/BPM, and EBU R128 loudness, in realtime and batch modes. **Mine:** the cleanest recent map of which Essentia algorithms cover ASA's tonal-balance/dynamics/loudness brief and how to split realtime vs full-file analysis. _(surfaced 05-14, re-read 4→5 on 05-17 · tags: essentia, mel, loudness, key, onset)_

## Tier 2 — strong references

- **4/ASA** · [WB2024/Essentia-to-Metadata](https://github.com/WB2024/Essentia-to-Metadata) · `Python` · `75★` · `created:2026-02` · `maturity:app`
  Local genre/mood tagger on Essentia's Discogs-Effnet embeddings + Discogs-400 genre CNN + MTG-Jamendo mood classifier, writing tags straight to files. **Mine:** a worked example of running Essentia's pretrained ML models **fully offline** and the per-format tag-writing layer. _(surfaced 05-14, re-read 3→4 on 05-17 · tags: essentia-tf, genre, mood, offline)_
- **4/ASA** · [craiglush/navidrome-mood-plugin](https://github.com/craiglush/navidrome-mood-plugin) · `Go/Python` · `55★` · `created:2026-03` · `maturity:app`
  Navidrome plugin using `essentia-tensorflow` + Discogs-EffNet to score mood/danceability/energy/BPM with genre-aware corrections, auto-building 13 themed playlists; ships a **separate FastAPI analyzer** because *"essentia can't run inside WASM."* **Mine:** that FastAPI-analyzer split directly validates ASA's server-side architecture; the genre-context-boost trick is reusable. _(surfaced 05-14, re-scored 3→4 on 05-20 · tags: essentia-tf, fastapi, mood, validates-arch)_
- **4/ASA** · [libAudioFlux/audioFlux](https://github.com/libAudioFlux/audioFlux) · `C/Python` · `3.3k★` · `maturity:lib`
  C-core + Python bindings, pip-installable: mel/MFCC/CQT/chroma/pitch/onset/spectral. **Mine:** a serious **native, server-side** feature-extraction complement to Essentia (no loudness — leave that to Essentia/rsgain) if ASA wants a second backend or to cross-check descriptors. _(surfaced 05-20 · tags: native, features, mel, cqt, chroma, complement)_
- **4/ASA** · [MTG/gaia](https://github.com/MTG/gaia) · `C++/Python` · `297★` · `active:2026` · `maturity:lib`
  Essentia's own C++/Python companion: similarity measures + SVM classifiers over Essentia descriptors, producing the high-level models Essentia loads to label music. ⚠ **stale — last release 2019.** **Mine:** the upstream answer for "turn low-level descriptors into mood/genre/danceability tags," but prefer essentia-TF embeddings + a vector store; treat as reference. _(surfaced 05-19, re-scored 3→4 on 05-20 · tags: essentia, similarity, classifier, stale-2019, reference)_

## Tier 3 — established native MIR baselines

- **3/ASA** · [tyiannak/pyAudioAnalysis](https://github.com/tyiannak/pyAudioAnalysis) · `Python` · `maturity:lib`
  Established Python MIR: MFCC/chroma/segmentation/classification. **Mine:** a native, importable baseline feature/segmentation set to compare Essentia's output against; long-known, nothing novel. _(surfaced 05-20 · tags: native, python, features, segmentation, baseline)_
- **3/ASA** · [audeering/opensmile](https://github.com/audeering/opensmile) · `C++/Python` · `maturity:lib`
  Mature C++ feature toolkit (speech + music) with Python wheels and reference-grade feature sets. **Mine:** reference feature-set definitions and a second native extractor; speech-leaning, so cherry-pick the music-relevant descriptors. _(surfaced 05-20 · tags: native, features, reference-sets, speech+music)_
- **3/ASA** · [urinieto/msaf](https://github.com/urinieto/msaf) · `Python` · `552★` · `maturity:lib`
  Native Python music-structure-analysis framework: boundary detection / segmentation (verse/chorus/section). **Mine:** ASA's section/structure stage — a from-2014 but legitimate reference for boundary algorithms; was wrongly dropped as "long-known." _(surfaced 05-19, re-scored drop→3 on 05-20 · tags: native, python, structure, segmentation)_

## Tier 4 — marginal (nothing new vs ASA's deps)

- **low/ASA** · [adamstark/Gist](https://github.com/adamstark/Gist) · `C++` · `maturity:lib`
  Established C++ real-time audio-analysis library (onset, pitch, FFT/MFCC features). **Mine:** marginal — solid but offers nothing beyond what native Essentia already gives ASA's L1; logged for completeness. _(surfaced 05-21, dropped · tags: native, c++, established, redundant)_
