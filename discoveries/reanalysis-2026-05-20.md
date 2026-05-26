# Re-analysis — 2026-05-20

> **Follow-up correction (2026-05-26):** this re-analysis fixed ASA's description but **held
> Harmonia's `(H)` scores under an unverified "React + Tonal.js browser app" assumption**
> (see *"Could not reach ground truth"* / *"genuinely is a React/Tonal.js browser app"*
> below). That assumption is **wrong**. Harmonia is a **single, unpublished local HTML
> file**: vanilla HTML/CSS/JS, **zero dependencies**, hand-rolled music theory + byte-level
> MIDI writer; `github.com/slittycode/harmonia` → 404. So the browser/native correction
> *does* apply to Harmonia after all (its "browser-ness" was just a wrong assumption);
> Harmonia has no codebase or stack to be compatible with. `(H)` scores below should be read
> as **conceptual** chord/theory idea references only, not stack-fit or code-lift targets.
> This file is left intact as the audit trail.

Every prior sweep (05-13, 05-14, 05-17, 05-18, 05-19) scored repos against a
**wrong** description of ASA — *"Essentia.js DSP pipeline … in-browser"* — which
biased scores toward browser/WASM/client-side tools and penalised native
C/C++/Rust/Python. This re-scores the whole back-catalogue under corrected ground
truth and updates `RECOMMENDATIONS.md`. **The dated sweep files are left intact as
the record;** all corrections live here and in `RECOMMENDATIONS.md`.

## Ground truth (read from the real repo, authoritative)

**ASA = "Ableton Sonic Analyzer"** (`slittycode/ableton-sonic-analyzer`, public;
archived Python predecessor `slittycode/sonic-analyzer`). From its
`CLAUDE.md`/`README.md`:

> "ASA helps intermediate Ableton Live 12 producers answer 'how do I make
> something that sounds like this?' by running deterministic DSP measurements
> (Phase 1) and feeding them to an AI interpreter (Phase 2) that produces
> specific, measurement-cited Ableton device recommendations."

- **Backend** Python **3.11** + **FastAPI** (pinned to 3.11 because *"Essentia
  2.1b6 wheels aren't published for 3.12+"*). **Frontend** **React 19** + Vite + TS.
- **Three server-side layers:** **L1** native **Essentia 2.1b6** (mel, tonal
  balance, dynamics, loudness) → **L2** **`torchcrepe` pitch on `Demucs` stems** →
  **L3 / Phase 2** **Gemini** turns the Phase-1 JSON into measurement-cited
  **Ableton Live 12 device + parameter** recommendations (`live12_device_catalog.json`;
  large audio via the Gemini Files API; *"Phase 2 never overrides Phase 1"*).
- **Deployment:** local (SQLite + in-process workers) and hosted (worker-process
  separation; queue: measurement → pitch/note → interpretation). Phase 3 = on-demand
  audition-sample generation. **No MCP today**, but deeply Ableton-centric.

This resolves the brief's `[FILL IN]`: **Gemini is the Phase-2 interpreter** mapping
measurements → grounded Ableton device/param advice.

**Harmonia:** no repo exists under the account and ASA never references it. **Could
not reach ground truth** — I treat the brief's description ("React chord-progression/
reharmonization on Tonal.js") as an unverified assumption and **hold** all Harmonia
`(H)` scores. The browser/native correction barely applies to Harmonia anyway (it
genuinely *is* a React/Tonal.js browser app).

## Two systematic errors (not one)

1. **Browser/native bias** (the brief's premise). Native C/C++/Rust/Python tools
   were dropped/down-scored "off-stack because native / not browser-friendly." ASA
   is a **native, server-side Python app** — native is *first-class*.
2. **Pipeline ignorance.** The sweeps didn't know ASA's real pipeline, so they filed
   **stem separation** and **pitch** as *future/out-of-scope* ("if ASA adds a stem
   pre-stage"). They're **current L2 dependencies (Demucs + torchcrepe)** — every
   such hedge was wrong.

**Meta-finding:** the prior *discovery* was thorough. A fresh pass over the
under-explored categories (native MIR, Essentia ecosystem, LLM/MCP) mostly
re-surfaced repos already in `_seen.txt`. So the corrections are dominated by
**re-scores and un-drops**, with only a handful of genuine net-new finds.

Corrected rubric: native = first-class; drop all browser/WASM/bundle-size/cold-start
credit; the **Essentia ecosystem** (Essentia, gaia, models, wrappers) is core;
**LLM/MCP music tooling is on-theme** (ASA *is* an LLM app), doubly so for **Ableton**
tooling; ASA is an **app** so React UIs + API/contract + job/queue/deployment count;
**separation/pitch are in-scope**; licence ignored.

---

## Table 1 — SCORE CHANGES (previously surviving repos)

| Repo | Old → New | Reason |
|---|---|---|
| [dreamrec/LivePilot](https://github.com/dreamrec/LivePilot) | 4 → **5** | The closest existing analog to *all* of ASA: Ableton MCP (465 tools/5,264-device atlas) **+** an M4L analysis bridge (9-band FFT, K-S key, pitch, FluCoMa mel/chroma/onset) **+** a measure→act→measure loop. Was later dropped (05-19) as "more Ableton plumbing" — a direct artifact of not knowing ASA is Ableton+analysis+LLM. |
| [JeffreyCA/spleeter-web](https://github.com/JeffreyCA/spleeter-web) | 3 → **4** | React + Django + Celery/Redis + Docker running **Demucs** = ASA's app+queue+L2 shape (only the web framework differs). |
| [craiglush/navidrome-mood-plugin](https://github.com/craiglush/navidrome-mood-plugin) | 3 → **4** | Ships a **separate FastAPI analyzer** running `essentia-tensorflow` *because "essentia can't run inside WASM"* — directly validates ASA's server-side architecture. |
| [NeptuneHub/AudioMuse-AI-NV-plugin](https://github.com/NeptuneHub/AudioMuse-AI-NV-plugin) | 3 → **4** | Value is its core's **Flask + Redis/RQ workers + PostgreSQL + Docker/K8s** queue architecture (see net-new `AudioMuse-AI`) — a blueprint for ASA's hosted mode. |
| [undef13/splifft](https://github.com/undef13/splifft) | 3 → **4** | Modular separation/transcription toolkit + 110-model registry. L2 is **current scope**, so "swap separation backend" is real, not hypothetical. |
| [Polochon-street/bliss-rs](https://github.com/Polochon-street/bliss-rs) | 3 → **4** | Native **Rust** chroma/tempo/timbre similarity vectors; "off-stack" was the bias. A clean "tracks-like-this" axis, server-side. |
| [MTG/gaia](https://github.com/MTG/gaia) | 3 → **4 ⚠** | Native C++/**Python** similarity+classifier companion to Essentia; dropped-rationale was literally *"C++/AGPL and not browser-friendly."* ⚠ stale (last release 2019) — reference / prefer `essentia-tensorflow` embeddings + a vector store. |
| [adamjmurray/producer-pal](https://github.com/adamjmurray/producer-pal) | 3 → **4** | M4L + MCP + **Gemini** driving Ableton devices/params. ASA *is* Ableton+Gemini → the "apply the recommendation in Live" companion. Was mis-filed "tangential." |
| [marcus/good-composer](https://github.com/marcus/good-composer) | 3 → **4** | **FastAPI + WebSocket streaming + React + LLM** = ASA's exact stack pattern for streaming Phase-2 output to the UI. |
| [brightlikethelight/music21-mcp-server](https://github.com/brightlikethelight/music21-mcp-server) | 3 → **4** | A FastMCP server exposing analysis/theory tools to an LLM **is** ASA's MCP-tool pattern (and serves Harmonia's theory). |
| [Ryan5453/demucs-next](https://github.com/Ryan5453/demucs-next) | 3 → **4** | Faster modern Demucs fork; a direct **L2** speed win. Dropped in 05-19 as a "thin fork" — the separation-is-out-of-scope bias. |

## Table 2 — WRONGLY DROPPED → RECONSIDER

| Repo | Old → New | Why it was wrongly dropped |
|---|---|---|
| [MTG/essentia](https://github.com/MTG/essentia) | drop → **5** | Dropped (05-17) as *"the parent C++ library; ASA already depends on Essentia.js downstream"* and (05-19) *"ASA's own upstream."* **ASA's actual core dep is native Essentia 2.1b6 — this library.** The flagship bias casualty; belongs on the shortlist as the algorithm/model/upgrade reference. |
| [complexlogic/rsgain](https://github.com/complexlogic/rsgain) | drop → **4** | Dropped (05-13) verbatim for *"off-stack for ASA's in-browser/in-pipeline scope."* Native **C++ EBU R128 + true-peak + ReplayGain 2.0** (603★, active) — a Phase-1 loudness reference, same role as openmeters/soundscope. |
| [ssmall256/demucs-mlx](https://github.com/ssmall256/demucs-mlx) | drop → **4** | Dropped as "a straight port." It's a **pip-importable, Apple-Silicon Demucs** (`from demucs_mlx import Separator`, ~73× realtime). ASA is local-first and its users are Mac producers → an L2 **drop-in**. |
| [urinieto/msaf](https://github.com/urinieto/msaf) | drop → **3** | Dropped (05-19) as "long-known." Native **Python music-structure analysis** (boundaries/segmentation, 552★) = ASA's section/structure stage. |
| [asteroid-team/asteroid](https://github.com/asteroid-team/asteroid) | drop → **3** | Dropped as "established." Separation is now **L2 in-scope**; a mature PyTorch separation toolkit is a legitimate reference. |
| [paladini/voice-separator-demucs](https://github.com/paladini/voice-separator-demucs) | drop → **3** | Dropped thrice as "thin FastAPI front in front of Demucs" — but **FastAPI + Demucs is ASA's L2-as-a-service shape**. |
| [jpoindexter/ableton-mcp](https://github.com/jpoindexter/ableton-mcp) | drop → **3** | Python Ableton MCP (200+ tools, Gemini-capable); on-theme for ASA's Ableton+LLM surface. |
| [christopherwxyz/remix-mcp](https://github.com/christopherwxyz/remix-mcp) | drop → **3** | Rust Ableton-control MCP (266 tools, OSC); on-theme (control-only, no analysis despite the name). |
| [innermost47/ai-dj](https://github.com/innermost47/ai-dj) (now *OBSIDIAN-Neural*) | drop → **3** | Dropped as "pure generation." ASA **Phase 3 = on-demand audition-sample generation**; this is a server-side Python (Stable Audio Open) loop generator — a Phase-3 plumbing reference. |

## Table 3 — OVER-VALUED FOR BROWSER/WASM → DOWNGRADE

| Repo | Old → New | What evaporated |
|---|---|---|
| [jhartquist/resonators](https://github.com/jhartquist/resonators) | 4 → **3** | Pitch was *"the WASM target makes it a drop-in for a browser DSP stage."* ASA has no browser DSP. Kept at 3 only for the Rust→PyO3 per-sample angle (niche vs Essentia). |
| [andremichelle/openDAW](https://github.com/andremichelle/openDAW) | 3 → **2** | Kept (05-17) as a *"browser-first"* reference with explicitly *"no MIR or analysis surface."* A pure browser-bias survivor — ASA isn't a web DAW. |
| [JorenSix/Olaf](https://github.com/JorenSix/Olaf) | 3 → **2** | Valued as a "clean reference … in-browser" fingerprinter (WASM/ESP32). Strip the browser novelty and audio identification isn't an ASA use case. |

**Reasoning corrected, score held** (not downgrades): `noteDigger` 4 — its
"zero-deps / bundle size" praise is void and it's 0% relevant to ASA (client-side
JS), but the score stands as a **Harmonia** (browser) item. `wavey-ai/mel-spec` 4 —
the WASM/TGA-interchange credit is irrelevant, but the **native Rust mel/STFT
primitives** are squarely Phase-1, so it holds. `dogayuksel/webKeyFinder` 4 (H) —
WASM is fine for a browser Harmonia; the ASA-relevant nugget is the underlying native
**libKeyFinder**. `casantosmu/audiodeck` 3 — browser render is incidental; the **Go
server-side analysis** justifies it.

---

## Step 4 — Fresh discovery (corrected framing), deduped vs `_seen.txt`

The prior sweeps already covered the Essentia ecosystem (essentia, gaia) and the
Ableton-MCP / MCP-analysis families (producer-pal, ableton-mcp, bschoepke, uisato,
LivePilot, music21-mcp-server, audio-analyzer-rs, live-coding-music-mcp). The
**genuinely net-new** survivors:

| Repo | Score | What / why ASA-relevant |
|---|---|---|
| [libAudioFlux/audioFlux](https://github.com/libAudioFlux/audioFlux) | **4** | C-core + Python bindings, pip-installable; mel/MFCC/CQT/chroma/pitch/onset/spectral. Serious **native, server-side** feature-extraction complement to Essentia (no loudness — Essentia/rsgain cover that). 3.3k★. |
| [hugohow/mcp-music-analysis](https://github.com/hugohow/mcp-music-analysis) | **4** | Python **MCP server** wrapping librosa (beat/tempo/MFCC/chroma/centroid/onset) for LLM consumption — the closest analog to "expose ASA's analysis to Gemini as tools." |
| [NeptuneHub/AudioMuse-AI](https://github.com/NeptuneHub/AudioMuse-AI) | **4** | The analysis core behind the in-corpus NV-plugin: **Flask + Redis/RQ workers + PostgreSQL + Docker/K8s**, librosa/ONNX/CLAP, REST+Swagger, a chat module. 1.7k★, very active — a concrete blueprint for ASA's hosted worker-queue mode. |
| [tyiannak/pyAudioAnalysis](https://github.com/tyiannak/pyAudioAnalysis) | **3** | Established Python MIR (MFCC/chroma/segmentation/classification); native, importable baseline. |
| [audeering/opensmile](https://github.com/audeering/opensmile) | **3** | Mature C++ feature toolkit (speech+music) with Python wheels; reference-grade feature sets. |

**Leads (unverified — chase next sweep, NOT added to `_seen.txt`):** vbarreiratt
*"FantasticEar / Advanced Music Analysis"* MCP (librosa, updated May 2026; repo
returned 403 via aggregator); **Estratto** (Rust audio-feature library; owner/URL
unresolved).

**Noted + added to `_seen.txt` for completeness:** ASA's own L2 deps
[facebookresearch/demucs](https://github.com/facebookresearch/demucs) and
[maxrmorrison/torchcrepe](https://github.com/maxrmorrison/torchcrepe) (maximally
relevant by definition); low-signal awesome-lists `BillyDM/awesome-audio-dsp` &
`EmulationAI/awesome-large-audio-models` (evaluated 05-13 AM but never logged),
`Yuan-ManX/audio-development-tools`, `pettarin/awesome-python-audio-research`.

---

## Assumptions & limits

- **Harmonia is unverified** (no repo found; absent from ASA). Its `(H)` scores are
  held and flagged. If a Harmonia repo exists elsewhere, re-run.
- ASA facts are from its public `CLAUDE.md`/`README.md`, treated as authoritative
  over the brief's summary (per instructions). The `[FILL IN]` for Gemini is
  resolved above.
- Re-fetched (web, 2026-05-20) every repo whose verdict moved or that was dropped
  for native/browser reasons, to avoid trusting the old browser-biased blurbs.
- `Rezonality/zing` (GUI audio-I/O toolkit, not MIR) and `christopherwxyz/remix-mcp`
  (verified: Ableton control, no analysis) were checked; zing stays dropped.
- Two leads excluded from `_seen.txt` because I couldn't confirm their canonical
  slug — listing a wrong slug would pollute dedup.

## Full re-scored inventory (corpus + net-new)

`→` change · `=` held · `(H)` Harmonia · `drop` below threshold.

**5 (S):** forever-jukebox =, EssentiaTD =, ChordMiniApp = (H), audio-analyzer-rs =,
dreamrec/LivePilot 4→5, **MTG/essentia drop→5**.
**4 (A):** openmeters =, Partiels =, clamp3 =, jivetalking =, songsee =,
AudioAuditor =, WB2024/Essentia-to-Metadata =, wavey-ai/mel-spec =, CPJKU/beat_this =,
chordonomicon = (H), rawl = (H), noteDigger = (H), dogayuksel/webKeyFinder = (H),
pianosnake/ireal-reader = (H), nightingale =, a1ex90/MusicalKeyCNN =,
spleeter-web 3→4, navidrome-mood-plugin 3→4, AudioMuse-AI-NV-plugin 3→4,
undef13/splifft 3→4, Polochon-street/bliss-rs 3→4, MTG/gaia 3→4 ⚠, producer-pal 3→4,
good-composer 3→4, brightlikethelight/music21-mcp-server 3→4, Ryan5453/demucs-next 3→4,
rsgain drop→4, demucs-mlx drop→4, **audioFlux (new)**, **hugohow/mcp-music-analysis
(new)**, **NeptuneHub/AudioMuse-AI (new)**.
**3 (B):** soundscope =, moises-light =, stemgen-rt =, torchfx =, Boof2015/astra =,
casantosmu/audiodeck =, mhartzel/freelcs =, chromatone.center = (H),
markwilkins/midi-chord-reader = (H), Natooz/MidiTok = (H), CPJKU/partitura = (H),
uisato/ableton-mcp-extended =, ifeelvoid/keyfinder =, GAME =, latentscore =,
live-coding-music-mcp =, bschoepke/ableton-live-mcp =, phones24/ep133-export-to-daw =,
gluon/Void-LinkAudio =, Conceptual-Machines/magda-core =, asteroid drop→3,
urinieto/msaf drop→3, paladini/voice-separator-demucs drop→3, jpoindexter/ableton-mcp
drop→3, christopherwxyz/remix-mcp drop→3, innermost47/ai-dj drop→3,
**pyAudioAnalysis (new)**, **opensmile (new)**.
**2 / drop:** resonators 4→3, andremichelle/openDAW 3→2, Olaf 3→2; held drop —
SynthBridge, schwung, diarize, OwnAudioSharp (C#/.NET off ASA's Python stack —
reasoning corrected, *not* a native penalty), ACE-Step-1.5, ace-step-ui, heartlib,
allkaraoke, music21j, tegridy-tools, gibberwocky, DSPi, ofxAbletonLinkAudio (umbrella
`Void-LinkAudio` kept at 3), STEMwerk-reaper, torch-l1-snr, parangonar (symbolic
alignment — out of scope, not browser-related), MOZLib, m4l-Knobbler4,
Sonata165/PhraseLDM_code, lunashia/o-m_beatmap_trainer, astradzhao/music-rfm,
Rezonality/zing, snejus/beetcamp.
