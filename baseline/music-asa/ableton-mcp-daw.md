# music-asa / ableton-mcp-daw

Ableton / MCP / DAW plumbing and the agentic surface — the tools that let an LLM
read or drive a DAW, plus the Link/export/session-edit plumbing around them. This is
**on-theme for ASA**: ASA is a server-side Python/FastAPI + Gemini app whose whole
point is measurement-cited **Ableton Live 12** advice, so an "apply the recommendation
in Live" companion (MCP/M4L) is a natural extension. Scores are **1–5 relevance** +
flag: `ASA` · `H` (Harmonia = **conceptual reference**, vanilla-JS single-file, unpublished;
prior "React+Tonal.js" description was wrong — see `../README.md`) · `Both` · `tang`.
Corrected scores follow `discoveries/reanalysis-2026-05-20.md` (native + LLM/MCP +
Ableton tooling are first-class; browser/WASM credit removed).

## Cross-domain (stub — full entry in `chord-key.md`)

- **5/Both** · [dreamrec/LivePilot](https://github.com/dreamrec/LivePilot) · `Python` · `21★` · `active:2026-03` · `maturity:app`
  Most ambitious Ableton-MCP (465 tools / 56 domains, 5,264-device atlas, M4L spectral + **Krumhansl-Schmuckler key** bridge, measure→act→measure loop). The closest existing analog to *all* of ASA. **Full entry + Mine: in `chord-key.md`** (filed there as harmonic-core). _(surfaced 05-17 · re-scored 4→5 on 05-20)_

## Strong (4)

- **4/ASA** · [adamjmurray/producer-pal](https://github.com/adamjmurray/producer-pal) · `JavaScript` · `143★` · `active:2026-05` · `maturity:app`
  Max-for-Live device + MCP server letting Claude/**Gemini**/ChatGPT/Ollama drive an Ableton Live session in natural language; the cleanest current M4L↔MCP example. ASA *is* Ableton+Gemini, so this is the "apply the Phase-2 recommendation in Live" companion (was mis-filed "tangential" pre-05-20). **Mine:** fork the M4L↔MCP bridge wholesale as ASA's write-side — the device/parameter tool surface is exactly how Gemini's measurement-cited advice would land in a live set. _(surfaced 05-13 · re-scored 3→4 on 05-20 · tags: ableton, mcp, m4l, gemini)_
- **4/ASA** · [brightlikethelight/music21-mcp-server](https://github.com/brightlikethelight/music21-mcp-server) · `Python` · `22★` · `maturity:app`
  FastMCP server exposing 13 music21 tools — Roman numerals, cadence detection, voice leading, harmonization, counterpoint — with HTTP/CLI mirrors for when MCP misbehaves (author flags a candid "40-50% MCP production success rate"). A FastMCP server exposing analysis/theory tools to an LLM *is* ASA's MCP-tool pattern. **Mine:** copy the FastMCP-tool-wrapping pattern (and the HTTP/CLI fallback design) as the template for exposing ASA's analysis JSON to Gemini as callable tools. _(surfaced 05-18 · re-scored 3→4 on 05-20 · tags: mcp, music21, theory, fastmcp)_
- **4/ASA** · [hugohow/mcp-music-analysis](https://github.com/hugohow/mcp-music-analysis) · `Python` · `maturity:app`
  Python MCP server wrapping librosa (beat/tempo/MFCC/chroma/spectral-centroid/onset) for LLM consumption — the closest analog to "expose ASA's analysis to Gemini as tools." Net-new in the 05-20 corrected sweep. **Mine:** the most direct reference for ASA's planned MCP surface — fork the librosa-feature→MCP-tool mapping and adapt it to ASA's richer Essentia/torchcrepe/Demucs JSON. _(surfaced 05-20 · tags: mcp, librosa, analysis, llm)_

## Useful references (3)

- **3/ASA** · [jpoindexter/ableton-mcp](https://github.com/jpoindexter/ableton-mcp) · `Python` · `maturity:app`
  Python Ableton MCP with 200+ tools, Gemini-capable; on-theme for ASA's Ableton+LLM surface. Originally dropped (05-13) as "thinner than producer-pal," un-dropped on 05-20. **Mine:** a second, broader Ableton-MCP tool inventory to compare against producer-pal when deciding ASA's write-side tool granularity. _(surfaced 05-13 · re-scored drop→3 on 05-20 · tags: ableton, mcp, gemini)_
- **3/ASA** · [bschoepke/ableton-live-mcp](https://github.com/bschoepke/ableton-live-mcp) · `Python` · `184★` · `active:2026-05` · `maturity:app`
  General-purpose Ableton MCP whose bet is "let the agent `eval` arbitrary Python inside Ableton," with a few hot-path tools for latency/reliability (latency-tuned via Codex `/goal`). A different philosophy from producer-pal's curated tools. **Mine:** read it for the eval-everything vs curated-tools trade-off before fixing ASA's tool surface; the latency hot-path tooling is the reusable bit. _(surfaced 05-17 · tags: ableton, mcp, eval, latency)_
- **3/ASA** · [uisato/ableton-mcp-extended](https://github.com/uisato/ableton-mcp-extended) · `Python` · `203★` · `maturity:app`
  Extended Ableton MCP with parallel **TCP + UDP** servers (UDP for low-latency realtime control), ElevenLabs TTS for in-session narration, and a custom-controller framework. **Mine:** lift the UDP low-latency control path and the controller-extension scaffold if ASA's Live companion ever needs realtime (not request/response) parameter moves. _(surfaced 05-18 · tags: ableton, mcp, udp, tts)_
- **3/ASA** · [christopherwxyz/remix-mcp](https://github.com/christopherwxyz/remix-mcp) · `Rust` · `266★` · `maturity:app`
  Rust Ableton-control MCP (266 tools, OSC) — control-only, **no analysis** despite the name (verified 05-20). On-theme for ASA's Ableton+LLM control surface. **Mine:** a Rust reference for an OSC-based Ableton control layer if ASA's companion wants a native (non-M4L) write path. _(surfaced 05-20 · re-scored drop→3 on 05-20 · tags: ableton, mcp, osc, rust)_
- **3/tang** · [williamzujkowski/live-coding-music-mcp](https://github.com/williamzujkowski/live-coding-music-mcp) · `TypeScript` · `200★` · `active:2025-08` · `maturity:app`
  MCP server exposing Strudel.cc to Claude/Anthropic clients for live-coded pattern generation. Same MCP-in-the-DAW family as producer-pal but on the browser-pattern (generation) side, not analysis. **Mine:** reference only for the "LLM-driven pattern" channel idea; nothing on the analysis path. _(surfaced 05-13 PM · tags: mcp, strudel, livecoding, generation)_
- **3/ASA** · [Conceptual-Machines/magda-core](https://github.com/Conceptual-Machines/magda-core) · `C++` · `124★` · `active:2026-01` · `maturity:app`
  AI-first DAW on C++20/JUCE/Tracktion Engine: natural-language chat generates a custom DSL that mutates the session, hybrid audio+MIDI tracks, 16 LFOs + 16 macros per device, nestable parallel racks, juce-llm + llama.cpp for local inference. The cleanest "AI as a first-class DAW citizen" reference around. **Mine:** study the NL→DSL→session-edit loop as the precedent for ASA growing an agentic edit surface; the DSL-as-LLM-target design is the transferable idea. _(surfaced 05-17 · tags: daw, juce, nl-dsl, agentic)_
- **3/ASA** · [phones24/ep133-export-to-daw](https://github.com/phones24/ep133-export-to-daw) · `TypeScript` · `88★` · `maturity:app`
  PWA reading `.pak` backups (or live over WebMIDI) from Teenage Engineering EP-133/EP-1320/EP-40 and exporting Ableton Live, DAWproject, REAPER, and MIDI — incl. sample envelopes and stretch modes. **Mine:** the WebMIDI→DAWproject/Live-project export pipeline is reusable plumbing if ASA ever round-trips its recommendations into a project file. _(surfaced 05-17 · tags: webmidi, dawproject, ableton, export)_
- **3/ASA** · [gluon/Void-LinkAudio](https://github.com/gluon/Void-LinkAudio) · `25★` · `active:2026-04` · `maturity:app`
  Umbrella project for sample-accurate beat-synced audio over LAN between Max, TouchDesigner, VCV Rack, openFrameworks, and Live 12.4+; v0.3 adds Linux ARM64/x86_64 for VCV and Pure Data. **Mine:** reference for sample-accurate inter-app audio transport if ASA ever needs to pull live audio from Ableton over the network rather than from a file. _(surfaced 05-17 · tags: ableton-link, lan, audio-transport)_

## Marginal — kept with a note (low / 2)

- **2/ASA** · [andremichelle/openDAW](https://github.com/andremichelle/openDAW) · `TypeScript` · `1.6k★` · `active:2025-02` · `maturity:app`
  Framework-light web DAW (AGPL, "no SignUp / no Tracking"), explicitly with **no MIR or analysis surface** — pure composition. A browser-bias survivor: ASA isn't a web DAW (downgraded 3→2 on 05-20). **Mine:** web-audio engine architecture only, if a browser front ever matters; nothing on the analysis side. _(surfaced 05-17 · re-scored 3→2 on 05-20 · tags: web-daw, webaudio, agpl)_
- **low/ASA** · [gluon/ofxAbletonLinkAudio](https://github.com/gluon/ofxAbletonLinkAudio) · `maturity:lib`
  The openFrameworks sub-addon, superseded by the umbrella `gluon/Void-LinkAudio` above. **Mine:** nothing beyond Void-LinkAudio — use the umbrella project instead. _(surfaced 05-13 · tags: ableton-link, openframeworks, superseded)_
- **low/tang** · [zsteinkamp/m4l-Knobbler4](https://github.com/zsteinkamp/m4l-Knobbler4) · `maturity:app`
  Max-for-Live OSC parameter-control surface for tablets — a tool, not a platform, with no MIR/theory content. **Mine:** OSC-control surface wiring only, if a hardware/tablet control idea ever surfaces. _(surfaced 05-17 · tags: m4l, osc, control)_
- **low/tang** · [charlesvestal/schwung](https://github.com/charlesvestal/schwung) · `maturity:app`
  Ableton Move firmware shim, specific to one piece of hardware. Dropped 05-13. **Mine:** nothing transferable — hardware-specific. _(surfaced 05-13 · tags: ableton-move, hardware, shim)_
- **low/tang** · [ManasWolrd/WarpCore](https://github.com/ManasWolrd/WarpCore) · `maturity:app`
  Niche tool, off-stack and under the relevance bar; dropped 05-21. **Mine:** nothing confirmed. _(surfaced 05-21 · tags: niche)_
- **low/tang** · [dr-schlange/nallely-midi](https://github.com/dr-schlange/nallely-midi) · `maturity:app`
  MIDI router/sequencer — not analysis. Dropped 05-17. **Mine:** MIDI-routing patterns only, if inter-device MIDI plumbing is ever needed. _(surfaced 05-17 · tags: midi, router)_
- **low/tang** · [gibber-cc/gibberwocky](https://github.com/gibber-cc/gibberwocky) · `JavaScript` · `maturity:app`
  Browser live-coding environment that sequences/modulates Ableton Live and Max from JS (2015; recently touched but not newly relevant — dropped 05-13 PM). **Mine:** the live-code→Ableton/Max control-mapping idea only; superseded by the newer MCP/M4L tools above. _(surfaced 05-13 PM · tags: livecoding, ableton, max, browser)_
