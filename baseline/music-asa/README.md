# music-asa — the tech baseline

The audio / MIR / music-theory / music-gen catalog — the **ASA** and **Harmonia**
streams. **ASA** (`ableton-sonic-analyzer`) is a **server-side Python/FastAPI** app
(React frontend) running **native** Essentia + librosa + torchcrepe + Demucs (PyTorch
in-stack), with a **Gemini Phase-2** layer mapping the deterministic analysis JSON to
Ableton Live 12 device/parameter advice — it is **not** in-browser / WASM / Essentia.js,
so native C/C++/Rust/Python is first-class here. **Harmonia is real but unpublished**
(corrected 2026-05-26): a single local HTML file, vanilla HTML/CSS/JS, zero dependencies,
with hand-rolled music theory and byte-level MIDI writer (mood/genre→progression, roman
numerals, SVG piano, Substitutions panel, Web Audio, MIDI export). `github.com/slittycode/
harmonia` → 404; two earlier framings ("React + Tonal.js repo" and "phantom / does not
exist") are both superseded. Every `H` repo here is kept as a **conceptual reference** to
Harmonia's idea space (chord/key/theory/UI/MIDI ideas) — never a stack-fit or "incorporate
into Harmonia's codebase" candidate, since Harmonia has no codebase to incorporate into.
See `../README.md` for the spec.

## Legend
- **Score = 1–5 relevance** to ASA/Harmonia plus a flag: `ASA` · `H` (Harmonia =
  **conceptual reference only**; unpublished single-file vanilla JS — see header) ·
  `Both` · `tang` (tangential). This is the music schema — *not* the legal
  `fork/spark` scale.
- **`maturity`** = `lib` (import/fork-and-run library) · `app` (runnable application) ·
  `model` (a pretrained model / training code) · `alpha` (early) · `reference`
  (study-only / academic / notebooks).
- Unknown metadata is omitted, never guessed. Marginal repos (dropped on earlier sweeps
  for redundancy/overlap) are kept with a note on why and what's still mineable.
  Dead / 404 / hard off-domain repos live in `excluded.md`.

## At-a-glance (every repo)

| repo | sub-domain | lang | score | maturity |
| --- | --- | --- | --- | --- |
| [adamjmurray/producer-pal](https://github.com/adamjmurray/producer-pal) | ableton-mcp-daw | JavaScript | 4/ASA | app |
| [brightlikethelight/music21-mcp-server](https://github.com/brightlikethelight/music21-mcp-server) | ableton-mcp-daw | Python | 4/ASA | app |
| [hugohow/mcp-music-analysis](https://github.com/hugohow/mcp-music-analysis) | ableton-mcp-daw | Python | 4/ASA | app |
| [jpoindexter/ableton-mcp](https://github.com/jpoindexter/ableton-mcp) | ableton-mcp-daw | Python | 3/ASA | app |
| [bschoepke/ableton-live-mcp](https://github.com/bschoepke/ableton-live-mcp) | ableton-mcp-daw | Python | 3/ASA | app |
| [uisato/ableton-mcp-extended](https://github.com/uisato/ableton-mcp-extended) | ableton-mcp-daw | Python | 3/ASA | app |
| [christopherwxyz/remix-mcp](https://github.com/christopherwxyz/remix-mcp) | ableton-mcp-daw | Rust | 3/ASA | app |
| [williamzujkowski/live-coding-music-mcp](https://github.com/williamzujkowski/live-coding-music-mcp) | ableton-mcp-daw | TypeScript | 3/tang | app |
| [Conceptual-Machines/magda-core](https://github.com/Conceptual-Machines/magda-core) | ableton-mcp-daw | C++ | 3/ASA | app |
| [phones24/ep133-export-to-daw](https://github.com/phones24/ep133-export-to-daw) | ableton-mcp-daw | TypeScript | 3/ASA | app |
| [gluon/Void-LinkAudio](https://github.com/gluon/Void-LinkAudio) | ableton-mcp-daw | — | 3/ASA | app |
| [andremichelle/openDAW](https://github.com/andremichelle/openDAW) | ableton-mcp-daw | TypeScript | 2/ASA | app |
| [gluon/ofxAbletonLinkAudio](https://github.com/gluon/ofxAbletonLinkAudio) | ableton-mcp-daw | — | low/ASA | lib |
| [zsteinkamp/m4l-Knobbler4](https://github.com/zsteinkamp/m4l-Knobbler4) | ableton-mcp-daw | — | low/tang | app |
| [charlesvestal/schwung](https://github.com/charlesvestal/schwung) | ableton-mcp-daw | — | low/tang | app |
| [ManasWolrd/WarpCore](https://github.com/ManasWolrd/WarpCore) | ableton-mcp-daw | — | low/tang | app |
| [dr-schlange/nallely-midi](https://github.com/dr-schlange/nallely-midi) | ableton-mcp-daw | — | low/tang | app |
| [gibber-cc/gibberwocky](https://github.com/gibber-cc/gibberwocky) | ableton-mcp-daw | JavaScript | low/tang | app |
| [creightonlinza/forever-jukebox](https://github.com/creightonlinza/forever-jukebox) | apps-architecture | TypeScript/Python | 5/ASA | app |
| [Ircam-Partiels/Partiels](https://github.com/Ircam-Partiels/Partiels) | apps-architecture | C++ | 4/ASA | app |
| [Polochon-street/bliss-rs](https://github.com/Polochon-street/bliss-rs) | apps-architecture | Rust | 4/ASA | lib |
| [NeptuneHub/AudioMuse-AI](https://github.com/NeptuneHub/AudioMuse-AI) | apps-architecture | Python | 4/ASA | app |
| [NeptuneHub/AudioMuse-AI-NV-plugin](https://github.com/NeptuneHub/AudioMuse-AI-NV-plugin) | apps-architecture | — | 4/ASA | app |
| [rzru/nightingale](https://github.com/rzru/nightingale) | apps-architecture | Rust | 4/Both | app |
| [NeptuneHub/audiomuse-ai-plugin](https://github.com/NeptuneHub/audiomuse-ai-plugin) | apps-architecture | — | low/ASA | app |
| [NeptuneHub/AudioMuse-AI-MusicServer](https://github.com/NeptuneHub/AudioMuse-AI-MusicServer) | apps-architecture | — | low/ASA | app |
| [snejus/beetcamp](https://github.com/snejus/beetcamp) | apps-architecture | — | low/tang | lib |
| [JuzzyDee/audio-analyzer-rs](https://github.com/JuzzyDee/audio-analyzer-rs) | chord-key | Rust | 5/Both | app |
| [dreamrec/LivePilot](https://github.com/dreamrec/LivePilot) | chord-key | Python | 5/Both | app |
| [ptnghia-j/ChordMiniApp](https://github.com/ptnghia-j/ChordMiniApp) | chord-key | TypeScript | 5/H | app |
| [a1ex90/MusicalKeyCNN](https://github.com/a1ex90/MusicalKeyCNN) | chord-key | Python | 4/Both | model |
| [dogayuksel/webKeyFinder](https://github.com/dogayuksel/webKeyFinder) | chord-key | TypeScript | 4/H | app |
| [andreamust/consonance-ACE](https://github.com/andreamust/consonance-ACE) | chord-key | — | 4/Both | model |
| [ifeelvoid/keyfinder](https://github.com/ifeelvoid/keyfinder) | chord-key | Swift | 3/H | app |
| [markwilkins/midi-chord-reader](https://github.com/markwilkins/midi-chord-reader) | chord-key | C++ | 3/H | app |
| [lorediggia/harmony-lab](https://github.com/lorediggia/harmony-lab) | chord-key | Rust | low/H | app |
| [sepandhaghighi/capo](https://github.com/sepandhaghighi/capo) | chord-key | Python | low/tang | lib |
| [timvancann/chordflow](https://github.com/timvancann/chordflow) | chord-key | Rust | low/tang | app |
| [JJ110112/LiveChord](https://github.com/JJ110112/LiveChord) | chord-key | — | low/H | alpha |
| [joanroig/midi-to-scaler-chord-sets](https://github.com/joanroig/midi-to-scaler-chord-sets) | chord-key | — | low/H | lib |
| [MTG/essentia](https://github.com/MTG/essentia) | essentia-mir | C++/Python | 5/ASA | lib |
| [DarienBrito/EssentiaTD](https://github.com/DarienBrito/EssentiaTD) | essentia-mir | C++ | 5/ASA | lib |
| [WB2024/Essentia-to-Metadata](https://github.com/WB2024/Essentia-to-Metadata) | essentia-mir | Python | 4/ASA | app |
| [craiglush/navidrome-mood-plugin](https://github.com/craiglush/navidrome-mood-plugin) | essentia-mir | Go/Python | 4/ASA | app |
| [libAudioFlux/audioFlux](https://github.com/libAudioFlux/audioFlux) | essentia-mir | C/Python | 4/ASA | lib |
| [MTG/gaia](https://github.com/MTG/gaia) | essentia-mir | C++/Python | 4/ASA | lib |
| [tyiannak/pyAudioAnalysis](https://github.com/tyiannak/pyAudioAnalysis) | essentia-mir | Python | 3/ASA | lib |
| [audeering/opensmile](https://github.com/audeering/opensmile) | essentia-mir | C++/Python | 3/ASA | lib |
| [urinieto/msaf](https://github.com/urinieto/msaf) | essentia-mir | Python | 3/ASA | lib |
| [adamstark/Gist](https://github.com/adamstark/Gist) | essentia-mir | C++ | low/ASA | lib |
| [OpenMOSS/MOSS-Music](https://github.com/OpenMOSS/MOSS-Music) | llm-music-generation | — | 5/ASA | model |
| [sanderwood/clamp3](https://github.com/sanderwood/clamp3) | llm-music-generation | Python | 4/ASA | model |
| [marcus/good-composer](https://github.com/marcus/good-composer) | llm-music-generation | JavaScript | 4/ASA | app |
| [geshang777/GaMMA](https://github.com/geshang777/GaMMA) | llm-music-generation | — | 3/ASA | reference |
| [innermost47/ai-dj](https://github.com/innermost47/ai-dj) | llm-music-generation | Python | 3/ASA | app |
| [prabal-rje/latentscore](https://github.com/prabal-rje/latentscore) | llm-music-generation | Python | 3/tang | app |
| [ace-step/ACE-Step-1.5](https://github.com/ace-step/ACE-Step-1.5) | llm-music-generation | — | low/tang | model |
| [fspecii/ace-step-ui](https://github.com/fspecii/ace-step-ui) | llm-music-generation | — | low/tang | app |
| [HeartMuLa/heartlib](https://github.com/HeartMuLa/heartlib) | llm-music-generation | — | low/tang | lib |
| [ubisoft/ComfyUI-Chord](https://github.com/ubisoft/ComfyUI-Chord) | llm-music-generation | — | low/tang | app |
| [RowanUnderwood/Synesthesia-AI-Video-Director](https://github.com/RowanUnderwood/Synesthesia-AI-Video-Director) | llm-music-generation | — | low/tang | app |
| [simonholliday/subsequence](https://github.com/simonholliday/subsequence) | llm-music-generation | — | low/tang | app |
| [scragnog/HOT-Step-CPP](https://github.com/scragnog/HOT-Step-CPP) | llm-music-generation | — | low/tang | app |
| [rsxdalv/TTS-WebUI](https://github.com/rsxdalv/TTS-WebUI) | llm-music-generation | — | low/tang | app |
| [httpsworldview/openmeters](https://github.com/httpsworldview/openmeters) | loudness-dynamics-dsp | Rust | 4/ASA | app |
| [complexlogic/rsgain](https://github.com/complexlogic/rsgain) | loudness-dynamics-dsp | C++ | 4/ASA | app |
| [linuxmatters/jivetalking](https://github.com/linuxmatters/jivetalking) | loudness-dynamics-dsp | Go | 4/ASA | app |
| [Angel2mp3/AudioAuditor](https://github.com/Angel2mp3/AudioAuditor) | loudness-dynamics-dsp | C# | 4/ASA | app |
| [openclaw/songsee](https://github.com/openclaw/songsee) | loudness-dynamics-dsp | Go | 4/ASA | app |
| [wavey-ai/mel-spec](https://github.com/wavey-ai/mel-spec) | loudness-dynamics-dsp | Rust | 4/ASA | lib |
| [bananaofhappiness/soundscope](https://github.com/bananaofhappiness/soundscope) | loudness-dynamics-dsp | Rust | 3/ASA | app |
| [matteospanio/torchfx](https://github.com/matteospanio/torchfx) | loudness-dynamics-dsp | Python | 3/ASA | lib |
| [jhartquist/resonators](https://github.com/jhartquist/resonators) | loudness-dynamics-dsp | Rust | 3/ASA | lib |
| [mhartzel/freelcs](https://github.com/mhartzel/freelcs) | loudness-dynamics-dsp | Python | 3/ASA | app |
| [Boof2015/astra](https://github.com/Boof2015/astra) | loudness-dynamics-dsp | TypeScript/C++ | 3/ASA | app |
| [casantosmu/audiodeck](https://github.com/casantosmu/audiodeck) | loudness-dynamics-dsp | TypeScript/Go | 3/ASA | app |
| [WeebLabs/DSPi](https://github.com/WeebLabs/DSPi) | loudness-dynamics-dsp | — | low/ASA | reference |
| [maxrmorrison/torchcrepe](https://github.com/maxrmorrison/torchcrepe) | pitch-beat-tempo | Python | 5/ASA | lib |
| [CPJKU/beat_this](https://github.com/CPJKU/beat_this) | pitch-beat-tempo | Python | 4/ASA | model |
| [openvpi/GAME](https://github.com/openvpi/GAME) | pitch-beat-tempo | Python | 3/tang | model |
| [JorenSix/Olaf](https://github.com/JorenSix/Olaf) | pitch-beat-tempo | C | 2/tang | lib |
| [k2-fsa/sherpa-onnx](https://github.com/k2-fsa/sherpa-onnx) | pitch-beat-tempo | — | low/tang | lib |
| [lunashia/o-m_beatmap_trainer](https://github.com/lunashia/o-m_beatmap_trainer) | pitch-beat-tempo | — | low/tang | alpha |
| [emjjkk/beat-detection](https://github.com/emjjkk/beat-detection) | pitch-beat-tempo | — | low/tang | alpha |
| [facebookresearch/demucs](https://github.com/facebookresearch/demucs) | stem-separation | Python | 5/ASA | model |
| [JeffreyCA/spleeter-web](https://github.com/JeffreyCA/spleeter-web) | stem-separation | TypeScript/Python | 4/ASA | app |
| [Ryan5453/demucs-next](https://github.com/Ryan5453/demucs-next) | stem-separation | Python | 4/ASA | alpha |
| [ssmall256/demucs-mlx](https://github.com/ssmall256/demucs-mlx) | stem-separation | Python | 4/ASA | lib |
| [undef13/splifft](https://github.com/undef13/splifft) | stem-separation | Python | 4/ASA | alpha |
| [crlandsc/moises-light](https://github.com/crlandsc/moises-light) | stem-separation | Python | 3/ASA | model |
| [sweetspotsoundsystem/stemgen-rt](https://github.com/sweetspotsoundsystem/stemgen-rt) | stem-separation | C++ | 3/ASA | app |
| [asteroid-team/asteroid](https://github.com/asteroid-team/asteroid) | stem-separation | Python | 3/ASA | lib |
| [paladini/voice-separator-demucs](https://github.com/paladini/voice-separator-demucs) | stem-separation | Python | 3/ASA | app |
| [flarkflarkflark/STEMwerk-reaper](https://github.com/flarkflarkflark/STEMwerk-reaper) | stem-separation | Lua | low/ASA | app |
| [crlandsc/torch-l1-snr](https://github.com/crlandsc/torch-l1-snr) | stem-separation | Python | low/ASA | lib |
| [sigsep/sigsep-mus-eval](https://github.com/sigsep/sigsep-mus-eval) | stem-separation | Python | low/ASA | lib |
| [spyroskantarelis/chordonomicon](https://github.com/spyroskantarelis/chordonomicon) | symbolic-theory | — | 4/H | reference |
| [pianosnake/ireal-reader](https://github.com/pianosnake/ireal-reader) | symbolic-theory | JavaScript | 4/H | lib |
| [vpavlenko/rawl](https://github.com/vpavlenko/rawl) | symbolic-theory | TypeScript | 4/H | app |
| [madderscientist/noteDigger](https://github.com/madderscientist/noteDigger) | symbolic-theory | JavaScript | 4/H | app |
| [chromatone/chromatone.center](https://github.com/chromatone/chromatone.center) | symbolic-theory | — | 3/H | app |
| [Natooz/MidiTok](https://github.com/Natooz/MidiTok) | symbolic-theory | Python | 3/H | lib |
| [CPJKU/partitura](https://github.com/CPJKU/partitura) | symbolic-theory | Python | 3/H | lib |
| [sivabenepoivediamo/musicplusplus](https://github.com/sivabenepoivediamo/musicplusplus) | symbolic-theory | C++ | 3/H | lib |
| [fpachet/continuator](https://github.com/fpachet/continuator) | symbolic-theory | Python | 3/H | lib |
| [comorebi-notes/rechord](https://github.com/comorebi-notes/rechord) | symbolic-theory | — | 3/H | app |
| [cuthbertLab/music21j](https://github.com/cuthbertLab/music21j) | symbolic-theory | JavaScript | low/H | lib |
| [asigalov61/tegridy-tools](https://github.com/asigalov61/tegridy-tools) | symbolic-theory | Python | low/H | lib |
| [sildater/parangonar](https://github.com/sildater/parangonar) | symbolic-theory | Python | low/tang | lib |
| [JulienVincenot/MOZLib](https://github.com/JulienVincenot/MOZLib) | symbolic-theory | Max/Lisp | low/tang | lib |
| [Sonata165/PhraseLDM_code](https://github.com/Sonata165/PhraseLDM_code) | symbolic-theory | — | low/tang | reference |
| [astradzhao/music-rfm](https://github.com/astradzhao/music-rfm) | symbolic-theory | — | low/tang | reference |
| [ZaneH/piano-trainer](https://github.com/ZaneH/piano-trainer) | symbolic-theory | — | low/tang | app |
| [albertms10/music_notes](https://github.com/albertms10/music_notes) | symbolic-theory | Dart | low/H | lib |
| [pedromsantos/vaughan](https://github.com/pedromsantos/vaughan) | symbolic-theory | F# | low/H | lib |
| [daniel-c-silva/SynthBridge](https://github.com/daniel-c-silva/SynthBridge) | excluded | — | excluded | — |
| [FoxNoseTech/diarize](https://github.com/FoxNoseTech/diarize) | excluded | — | excluded | — |
| [ModernMube/OwnAudioSharp](https://github.com/ModernMube/OwnAudioSharp) | excluded | — | excluded | — |
| [Asvarox/allkaraoke](https://github.com/Asvarox/allkaraoke) | excluded | — | excluded | — |
| [Rezonality/zing](https://github.com/Rezonality/zing) | excluded | — | excluded | — |
| [BillyDM/awesome-audio-dsp](https://github.com/BillyDM/awesome-audio-dsp) | excluded | — | excluded | — |
| [EmulationAI/awesome-large-audio-models](https://github.com/EmulationAI/awesome-large-audio-models) | excluded | — | excluded | — |
| [Yuan-ManX/audio-development-tools](https://github.com/Yuan-ManX/audio-development-tools) | excluded | — | excluded | — |
| [pettarin/awesome-python-audio-research](https://github.com/pettarin/awesome-python-audio-research) | excluded | — | excluded | — |

## Sub-domain files
- **`essentia-mir.md`** — the Essentia ecosystem & native MIR feature extraction (ASA's Layer 1): core dep, companions, wrappers, and alternative native MIR toolkits.
- **`loudness-dynamics-dsp.md`** — loudness/R128, true-peak, LRA, dynamic-range; native DSP filters; and mel/spectrogram/visualization surfaces (ASA's Phase-1 loudness + dynamics stage).
- **`stem-separation.md`** — source separation (ASA's Layer 2): Demucs + forks/ports/app-shells and other separation models/toolkits.
- **`pitch-beat-tempo.md`** — pitch (torchcrepe on stems), beat/tempo estimation, and audio fingerprinting/identification on the margins.
- **`chord-key.md`** — chord and key detection (audio→chord, audio→key) and the harmonic-core MIR feeding ASA's tonal stage and Harmonia's idea space (Harmonia = unpublished single-file vanilla JS; see header).
- **`symbolic-theory.md`** — symbolic music, music-theory libraries, datasets, and tokenizers — the Harmonia-adjacent stream (conceptual references only).
- **`ableton-mcp-daw.md`** — Ableton / MCP / DAW plumbing and the agentic surface that lets an LLM read or drive a DAW (the "apply the Phase-2 recommendation in Live" companion).
- **`llm-music-generation.md`** — LLM-for-music, audio-LLM understanding, and music generation — the model layer adjacent to ASA's Gemini Phase-2 interpreter and Phase-3 audition generation.
- **`apps-architecture.md`** — full analysis apps, media-server integrations, track-to-track similarity, and the job-queue/worker/deployment shapes ASA needs in hosted mode.
- **`excluded.md`** — dead / 404 / hard off-domain repos and awesome-lists, recorded for completeness, flagged not-worth-chasing.
