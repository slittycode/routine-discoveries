# FINDS

Every repo any routine has ever surfaced, appended as it was found. Newest at
top. Nothing here is scored, ranked or filtered — if a sweep looked at it, it
is in this file.

Entry format:

```
## owner/repo
link:      https://github.com/owner/repo
surfaced:  YYYY-MM-DD
what:      one plain sentence
alive:     last commit, contributor count, release cadence
why:       why it's worth attention
tags:      freeform lowercase words, comma-separated
```

`alive:` records whatever liveness signal was available at capture. Entries
migrated from the pre-2026-08 structure carry only the star counts and
created/active dates the old sweeps recorded; their commit, contributor and
release detail was never captured and is marked unrecorded rather than guessed.

Tags are freeform. There is no controlled vocabulary and no list to check
against — write the words that fit the find.

---

## OpenMOSS/MOSS-Music
link:      https://github.com/OpenMOSS/MOSS-Music
surfaced:  2026-05-21
what:      Open 8B music-understanding LMM (MOSS-Audio-Encoder + Qwen3-8B) that takes raw audio and does timestamped lyrics ASR, captioning, structural analysis, chord/key/tempo reasoning and long-form musical Q&A.
alive:     weights on HF/ModelScope with SGLang/Transformers/Gradio inference; commit/contributor/release detail unrecorded
why:       The single most on-point new find for ASA's Gemini layer — it's an open, self-hostable model producing exactly the LLM-interpreted analysis ASA currently gets from Essentia + Gemini, so it's a serious reference (or partial replacement) for that layer and its task decomposition maps straight onto ASA's JSON. Evaluate as a (partial) self-hosted replacement for the Gemini Phase-2 layer; fork its prompt/task structure even if you keep Gemini.
tags:      audio, audio-llm, understanding, lmm, structure, self-hostable

## andreamust/consonance-ACE
link:      https://github.com/andreamust/consonance-ACE
surfaced:  2026-05-21
what:      Audio chord-estimation Conformer that decomposes prediction into separate root / bass / pitch-activation heads with consonance-based label smoothing, shipping a pretrained checkpoint and inference that turns WAV into 170-class timestamped chord `.lab` output.
alive:     ships a pretrained checkpoint; commit/contributor/release detail unrecorded
why:       Directly relevant to ASA's existing chord-detection stage as a modern, theory-informed model you can run server-side, and its timestamped chord stream is exactly the input Harmonia consumes — so it sits across both projects. Run server-side as a modern, theory-informed replacement for the chord stage.
tags:      audio, chord, conformer, ace, lab, model

## geshang777/GaMMA
link:      https://github.com/geshang777/GaMMA
surfaced:  2026-05-21
what:      Research implementation for "joint global-temporal music understanding in large multimodal models" — an audio-LLM aimed at reasoning over both whole-track and time-localized musical structure.
alive:     paper repo rather than a packaged model; commit/contributor/release detail unrecorded
why:       Same direction as ASA's LLM layer and a useful second data point, but it's a paper repo rather than a packaged model, so it's less immediately usable than MOSS-Music. Read for the global+temporal music-understanding architecture; not a drop-in.
tags:      audio, audio-llm, understanding, research, structure

## sivabenepoivediamo/musicplusplus
link:      https://github.com/sivabenepoivediamo/musicplusplus
surfaced:  2026-05-21
what:      Header-only C++ music-theory library using vector-based representations for chords, scales, intervals, voice leading and reharmonization (modal interchange, modulation), with TypeScript and Python SDKs on the roadmap.
alive:     TS/Python SDKs on the roadmap; commit/contributor/release detail unrecorded
why:       The reharmonization/voice-leading coverage is dead-center on Harmonia's domain — but it's C++ today, so it's an algorithm reference (or a future dependency once the planned TS SDK lands), not a Tonal.js drop-in.
tags:      audio, theory, reharmonization, voice-leading, cpp

## fpachet/continuator
link:      https://github.com/fpachet/continuator
surfaced:  2026-05-21
what:      François Pachet's reimplementation of the Continuator: variable-order Markov modeling plus exact finite-chain inference to generate melodic and chord-sequence continuations with guaranteed positional constraints, real-time learning and tiny data needs.
alive:     commit/contributor/release detail unrecorded
why:       For Harmonia it's an interesting non-transformer approach to suggesting or completing progressions under hard constraints (e.g. "keep these anchor chords"); it's Python/symbolic, so it's a technique to borrow rather than code to lift.
tags:      audio, markov, continuation, constraints, symbolic

## comorebi-notes/rechord
link:      https://github.com/comorebi-notes/rechord
surfaced:  2026-05-21
what:      React + Tone.js app for writing and sharing chord progressions.
alive:     still getting commits; a 2017 project; commit/contributor/release detail unrecorded
why:       On Harmonia's exact stack family (React + Tone.js + chords), so it's a usable reference for progression-entry UI and Tone.js playback wiring — but it's a 2017 sharing app with no reharmonization logic, so there's nothing to take on the theory side.
tags:      audio, react, tonejs, progressions, ui

## NeptuneHub/audiomuse-ai-plugin
link:      https://github.com/NeptuneHub/audiomuse-ai-plugin
surfaced:  2026-05-21
what:      Jellyfin sibling of the AudioMuse Navidrome plugin, with the same librosa + ONNX + LLM sonic-analysis architecture.
alive:     commit/contributor/release detail unrecorded
why:       Same architecture as the already-logged NV plugin, no new DSP — dropped on 05-21 for that reason. Only the Jellyfin-side integration glue is worth anything if targeting Jellyfin; architecturally identical to the NV plugin already logged.
tags:      audio, jellyfin, sibling, plugin, redundant

## RowanUnderwood/Synesthesia-AI-Video-Director
link:      https://github.com/RowanUnderwood/Synesthesia-AI-Video-Director
surfaced:  2026-05-21
what:      Audio→LLM→video tool where the LLM writes video prompts from an audio pass.
alive:     commit/contributor/release detail unrecorded
why:       The "audio analysis" is pydub silence detection and the LLM writes *video* prompts; off-domain for ASA. Nothing on the audio-analysis side.
tags:      audio, audio-to-video, off-domain

## ubisoft/ComfyUI-Chord
link:      https://github.com/ubisoft/ComfyUI-Chord
surfaced:  2026-05-21
what:      ComfyUI node wrapping Ubisoft's "Chord" audio model.
alive:     commit/contributor/release detail unrecorded
why:       Generation-side and ComfyUI-bound, off-target for both streams. Nothing transferable beyond awareness of the Chord model.
tags:      audio, comfyui, generation, chord-model

## lorediggia/harmony-lab
link:      https://github.com/lorediggia/harmony-lab
surfaced:  2026-05-21
what:      Minimal Rust scale/chord explorer.
alive:     commit/contributor/release detail unrecorded
why:       Too small and wrong stack for Harmonia. Only useful as a tiny reference for representing scales/chords in Rust if a native harmonic helper is wanted.
tags:      audio, chord, scale, rust

## sepandhaghighi/capo
link:      https://github.com/sepandhaghighi/capo
surfaced:  2026-05-21
what:      Python guitar-chord transposition library.
alive:     commit/contributor/release detail unrecorded
why:       Tonal.js already does transposition for Harmonia. Capo/transpose mapping logic only, if a guitar-specific transpose ever comes up.
tags:      audio, chord, guitar, transpose

## timvancann/chordflow
link:      https://github.com/timvancann/chordflow
surfaced:  2026-05-21
what:      Rust chord-practice TUI.
alive:     commit/contributor/release detail unrecorded
why:       Not analysis or theory tooling. Practice-loop / progression-cycling UX idea only.
tags:      audio, chord, practice, tui, rust

## JJ110112/LiveChord
link:      https://github.com/JJ110112/LiveChord
surfaced:  2026-05-21
what:      Chord-related repo with no README or description to vet against.
alive:     no README at capture; commit/contributor/release detail unrecorded
why:       Skipped on 05-21 because there was nothing to vet. Nothing confirmed — revisit if a README appears.
tags:      audio, chord, unvetted, no-readme

## adamstark/Gist
link:      https://github.com/adamstark/Gist
surfaced:  2026-05-21
what:      Established C++ real-time audio-analysis library (onset, pitch, FFT/MFCC features).
alive:     commit/contributor/release detail unrecorded
why:       Solid, but offers nothing beyond what native Essentia already gives ASA's L1; logged for completeness.
tags:      audio, native, cpp, established, features

## NeptuneHub/AudioMuse-AI-MusicServer
link:      https://github.com/NeptuneHub/AudioMuse-AI-MusicServer
surfaced:  2026-05-21
what:      Integration shell wiring AudioMuse-AI to a music server.
alive:     commit/contributor/release detail unrecorded
why:       No standalone analysis content. Wiring/deployment reference only; the real substance is in AudioMuse-AI.
tags:      audio, integration-shell, music-server, deployment

## sigsep/sigsep-mus-eval
link:      https://github.com/sigsep/sigsep-mus-eval
surfaced:  2026-05-21
what:      The MUSDB / BSS-eval source-separation evaluation package (SDR/SIR/SAR).
alive:     commit/contributor/release detail unrecorded
why:       An eval shell — only useful for benchmarking separators, which ASA doesn't do; logged for completeness.
tags:      audio, eval, musdb, bss-eval, benchmark

## joanroig/midi-to-scaler-chord-sets
link:      https://github.com/joanroig/midi-to-scaler-chord-sets
surfaced:  2026-05-21
what:      Niche MIDI→Scaler chord-set converter.
alive:     commit/contributor/release detail unrecorded
why:       Dropped 05-21 as off-stack. The chord-set data shape if interoperating with Scaler is ever needed.
tags:      audio, chord, midi, scaler

## ManasWolrd/WarpCore
link:      https://github.com/ManasWolrd/WarpCore
surfaced:  2026-05-21
what:      Niche DAW-adjacent tool.
alive:     commit/contributor/release detail unrecorded
why:       Off-stack and under the relevance bar on 05-21. Nothing confirmed.
tags:      audio, niche, daw

## ZaneH/piano-trainer
link:      https://github.com/ZaneH/piano-trainer
surfaced:  2026-05-21
what:      Piano practice / trainer app.
alive:     commit/contributor/release detail unrecorded
why:       Off-stack; dropped 05-21. Practice-UX patterns only.
tags:      audio, piano, practice, ui

## emjjkk/beat-detection
link:      https://github.com/emjjkk/beat-detection
surfaced:  2026-05-21
what:      Small beat-detection repo.
alive:     commit/contributor/release detail unrecorded
why:       Under the quality/star bar on 05-21. Nothing beyond a minimal beat-onset reference; the beat stage is far better served by beat_this.
tags:      audio, beat, onset, minimal

## dealfluence/adeu
link:      https://github.com/dealfluence/adeu
surfaced:  2026-05-21
what:      Flattens a Word doc to Markdown so a model can edit the substance, then projects the edits back as native Word Track Changes.
alive:     82★; Python (+ Node) implementations; commit/contributor/release detail unrecorded
why:       Cleanly separates meaning from formatting. Fork it as the output layer of your legal-impact comparator: a local model decides what should change, adeu emits the redlined `.docx` clients already know how to read. Local-first: yes.
tags:      legal, docx, ooxml, tracked-changes, redline, mcp, local-first

## kipeum86/contract-review-agent
link:      https://github.com/kipeum86/contract-review-agent
surfaced:  2026-05-21
what:      A local-first agent that compares a counterparty draft against your house templates and emits a Word file with tracked-change redlines, internal-vs-external margin comments and negotiation points.
alive:     34★; commit/contributor/release detail unrecorded
why:       The closest thing to your flagship goal already built. Fork it and swap its Claude API call for a local model (Ollama) to go fully offline. Local-first: partial (file processing stays local; cloud LLM by default).
tags:      legal, contract-review, redline, templates, agent, ollama-swap

## houfu/redlines
link:      https://github.com/houfu/redlines
surfaced:  2026-05-21
what:      A small, dependable library that turns two texts into Word-style strike-through/insert markup (HTML, Markdown, JSON, terminal) with change statistics.
alive:     157★; commit/contributor/release detail unrecorded
why:       Use it as the lightweight *display* primitive once your model has identified the substantive deltas. Local-first: yes.
tags:      legal, diff, markdown, display-primitive, change-stats

## sen-uni-kn/ContractCheck
link:      https://github.com/sen-uni-kn/ContractCheck
surfaced:  2026-05-21
what:      An academic tool that formalises a contract's clause preconditions into first-order logic and runs an SMT solver to find internal contradictions and unexecutable clauses.
alive:     6★; Java; commit/contributor/release detail unrecorded
why:       Mine the *modelling approach* (not the Java) to build a logic-level consistency linter that flags defined-term conflicts and clauses that can never both hold. Kept for the angle: single-document consistency is a rare, on-point angle. Local-first: yes.
tags:      legal, smt, first-order-logic, consistency, single-doc, academic

## JSv4/Python-Redlines
link:      https://github.com/JSv4/Python-Redlines
surfaced:  2026-05-21
what:      True Word-grade `.docx` tracked changes via the OpenXML WmlComparer.
alive:     108★; commit/contributor/release detail unrecorded
why:       A solid baseline; dropped on 05-21 as overlapping adeu and adding a .NET dependency, but it is the canonical OpenXML tracked-changes generator. The `.docx` tracked-changes emitter if you want OOXML-native diffing instead of adeu's Markdown round-trip. Local-first: yes.
tags:      legal, docx, ooxml, wmlcomparer, tracked-changes, dotnet-dep

## google/diff-match-patch
link:      https://github.com/google/diff-match-patch
surfaced:  2026-05-21
what:      Battle-tested, multi-language fuzzy diff / patch / match — the canonical char-level diff.
alive:     8.1k★; archived 2024; commit/contributor/release detail unrecorded
why:       Dropped 05-21 (jsdiff covers prose granularity better) and archived 2024, but kept as a reference: it is the textbook fuzzy diff/patch implementation. Back-pocket fuzzy patch/match logic (relocating an edit after surrounding text moved) that jsdiff doesn't offer. Local-first: yes.
tags:      legal, diff, patch, fuzzy-match, canonical, archived

## evolsb/legal-redline-tools
link:      https://github.com/evolsb/legal-redline-tools
surfaced:  2026-05-21
what:      Generates real tracked-changes `.docx` and redline PDFs from JSON edits.
alive:     29★; commit/contributor/release detail unrecorded
why:       Tiny but the most literally on-point: the exact deliverables lawyers send. Dropped 05-21 only for overlap with the adeu / Python-Redlines cluster. The "AI analysis (JSON edits) → Word markup + redline PDF" last mile, bolted onto your model's output. Local-first: yes.
tags:      legal, docx, redline-pdf, json-edits, tracked-changes, last-mile

## Mintplex-Labs/anything-llm
link:      https://github.com/Mintplex-Labs/anything-llm
surfaced:  2026-05-21
what:      A polished, fully-offline "private ChatGPT over your documents" desktop app with workspaces, PDF/DOCX ingestion, source citations and a local vector DB (Ollama/LM Studio).
alive:     60.4k★; commit/contributor/release detail unrecorded
why:       Self-host it day one as your confidential "chat with my matter files" base, then graft clause-extraction prompts onto its workspace model (workspaces map neatly to matters). Local-first: yes.
tags:      legal, rag, offline, ollama, vector-db, workspaces

## shcherbak-ai/contextgem
link:      https://github.com/shcherbak-ai/contextgem
surfaced:  2026-05-21
what:      An LLM extraction framework built around "Aspects" and "Concepts" that returns results with paragraph/sentence-level source references and auto-generated justifications, and can run against a local model.
alive:     1.8k★; commit/contributor/release detail unrecorded
why:       Fork it as your structured clause/defined-term/date extractor — the cite-back-to-source is exactly what trustworthy legal output needs. Local-first: yes.
tags:      legal, extraction, aspects-concepts, citations, local-llm, justifications

## Open-Source-Legal/OpenContracts
link:      https://github.com/Open-Source-Legal/OpenContracts
surfaced:  2026-05-21
what:      A self-hosted document-annotation + knowledge-base platform with vector + full-text search, LLM clause extraction, version control, and agents that compare clauses across many contracts.
alive:     1.3k★; commit/contributor/release detail unrecorded
why:       Heavier to stand up (Docker), but the most complete self-hosted foundation if you want one app for both understanding and cross-document comparison of your private corpus. Local-first: yes.
tags:      legal, annotation, knowledge-base, cross-doc, version-control, docker

## tomasonjo-labs/legal-tech-chat
link:      https://github.com/tomasonjo-labs/legal-tech-chat
surfaced:  2026-05-21
what:      A worked pipeline that extracts structured fields from contracts into a Neo4j knowledge graph and answers questions via a LangGraph agent.
alive:     159★; Jupyter notebooks; commit/contributor/release detail unrecorded
why:       Fork the *pattern* to make your contracts queryable by relationship ("every lease whose rent-review clause references CPI") instead of flat one-doc-at-a-time RAG. Local-first: partial (self-hostable; reference notebooks use cloud LLMs).
tags:      legal, knowledge-graph, neo4j, langgraph, graphrag, notebooks

## curiousily/ragbase
link:      https://github.com/curiousily/ragbase
surfaced:  2026-05-21
what:      A small, fully-local chat-with-PDF skeleton (LangChain + Streamlit + Ollama/Llama 3.1 + Qdrant, with reranking and semantic chunking).
alive:     129★; quiet since 2024; commit/contributor/release detail unrecorded
why:       Dropped 05-21 as superseded by AnythingLLM, and quiet since 2024. Kept as a tinier base to own line-by-line if you want fewer moving parts than AnythingLLM. Local-first: yes.
tags:      legal, rag, local, streamlit, qdrant, minimal

## docling-project/docling
link:      https://github.com/docling-project/docling
surfaced:  2026-05-21
what:      Document-parsing engine that turns PDF/DOCX/PPTX into clean structured Markdown/JSON with tables and layout preserved, and runs air-gapped.
alive:     60.1k★; commit/contributor/release detail unrecorded
why:       The standout parser. Make it the ingestion layer under everything else — "drop a deed/contract → clean searchable text" that never touches the cloud. Local-first: yes.
tags:      legal, parser, pdf, docx, markdown, air-gapped

## jsvine/pdfplumber
link:      https://github.com/jsvine/pdfplumber
surfaced:  2026-05-21
what:      Lower-level than Docling: per-character coordinates, rectangles and precise table extraction with visual debugging.
alive:     10.3k★; commit/contributor/release detail unrecorded
why:       Fork it to pull exact fields from fixed-layout NZ forms (ADLS/REINZ agreements, LIM reports, rates statements) where positional control matters more than a blind text dump. Local-first: yes.
tags:      legal, pdf, char-coordinates, tables, fixed-layout, nz-forms

## kpdecker/jsdiff
link:      https://github.com/kpdecker/jsdiff
surfaced:  2026-05-21
what:      Diff library that works on characters, words, sentences and JSON rather than lines, in the browser or Node with no upload.
alive:     9.1k★; commit/contributor/release detail unrecorded
why:       Exactly the granularity legal prose needs. It's the diff-engine half of a complete local "compare two clauses and show the changes" stack. Local-first: yes.
tags:      legal, diff, sentence-level, json, browser, no-upload

## rtfpessoa/diff2html
link:      https://github.com/rtfpessoa/diff2html
surfaced:  2026-05-21
what:      Renders diffs as polished side-by-side or inline HTML.
alive:     3.4k★; commit/contributor/release detail unrecorded
why:       The developer code-review UI, repurposed to present document changes to a non-technical client or counterparty. Pair it with jsdiff (engine) for a printable/PDF redline view; the two compose into a full local-first redliner in an afternoon. Local-first: yes.
tags:      legal, diff-render, side-by-side, html, client-facing

## tauri-apps/tauri
link:      https://github.com/tauri-apps/tauri
surfaced:  2026-05-21
what:      Desktop shell for wrapping tools into a real, distributable, offline app with a tiny footprint.
alive:     107k★; commit/contributor/release detail unrecorded
why:       Build a single "matter cockpit" binary combining your parser + diff + notes, with all data staying on your machine. Local-first: yes.
tags:      legal, desktop-shell, rust, webview, offline, distributable

## charmbracelet/bubbletea
link:      https://github.com/charmbracelet/bubbletea
surfaced:  2026-05-21
what:      An Elm-architecture TUI framework for Go.
alive:     42.6k★; commit/contributor/release detail unrecorded
why:       Dropped 05-21 as a stack choice (Tauri GUI was preferred), but it's the leading option if you'd rather build terminal tools than a desktop GUI — the shell for a keyboard-driven matter/diff TUI. Local-first: yes.
tags:      legal, tui, go, elm-architecture, terminal

## espanso/espanso
link:      https://github.com/espanso/espanso
surfaced:  2026-05-21
what:      A system-wide text expander driven by plain YAML bundles (with script/shell triggers) that fires in Word, email, anywhere — 100% local.
alive:     13.8k★; commit/contributor/release detail unrecorded
why:       Configure it as your legal snippet & boilerplate library: standard clauses, settlement-statement stock text, email replies, all from your own keystroke triggers. Local-first: yes.
tags:      legal, text-expander, yaml, snippets, boilerplate, system-wide

## TriliumNext/Trilium
link:      https://github.com/TriliumNext/Trilium
surfaced:  2026-05-21
what:      A hierarchical, scriptable personal knowledge base whose notes can run JS, so it doubles as a programmable second brain.
alive:     36.1k★; commit/contributor/release detail unrecorded
why:       Fork it into a precedent/clause library with scripted automations (auto-insert party details, generate a per-matter-type checklist). Local-first: yes.
tags:      legal, pkm, scriptable, knowledge-base, precedents, automations

## naggie/dstask
link:      https://github.com/naggie/dstask
surfaced:  2026-05-21
what:      A git-powered terminal todo/note manager — single binary, a markdown note page per task, with a full git-history audit trail.
alive:     1.2k★; commit/contributor/release detail unrecorded
why:       Dropped 05-21 as overlapping Trilium/notes, but it's a nice matter-tracker reskin where every status change is a git commit — useful if an immutable audit trail of who-changed-what matters. Local-first: yes.
tags:      legal, todo, git-audit-trail, cli, single-binary, matter-tracker

## usememos/memos
link:      https://github.com/usememos/memos
surfaced:  2026-05-21
what:      A clean, self-hosted single-binary quick-capture / microblog tool, Markdown-native and SQLite-backed.
alive:     59.9k★; commit/contributor/release detail unrecorded
why:       Dropped 05-21 as redundant with Trilium's capture; kept as a friction-free quick-capture inbox for matter notes if Trilium feels too heavy for jotting. Local-first: yes.
tags:      legal, quick-capture, markdown, sqlite, self-hosted

## nzpco/PCO-AI-Generating-an-Updated-Act
link:      https://github.com/nzpco/PCO-AI-Generating-an-Updated-Act
surfaced:  2026-05-21
what:      Official NZ Parliamentary Counsel Office code that takes an amendment Act and applies it to the principal Act from the legislation.govt.nz XML, presenting the consolidated result.
alive:     1★; documents running locally with Ollama; commit/contributor/release detail unrecorded
why:       NZ gold: fork it as both a worked example of parsing NZ legislation XML and a personal "what does the in-force version actually say?" consolidator. Local-first: yes.
tags:      legal, nz, pco, legislation-xml, consolidation, ollama, official

## isaacus-dev/open-australian-legal-corpus-creator
link:      https://github.com/isaacus-dev/open-australian-legal-corpus-creator
surfaced:  2026-05-21
what:      The maintained scrapers + assembly pipeline behind the first open corpus of Australian legislation and case law.
alive:     120★; commit/contributor/release detail unrecorded
why:       Not NZ, but the closest live Commonwealth template: adapt its per-jurisdiction scraper/normaliser design to build your own offline NZ legislation+caselaw corpus (pointed at legislation.govt.nz XML or NZLII). Local-first: yes.
tags:      legal, corpus, scraper, commonwealth, caselaw, normaliser

## nzpco/PCO-AI-Chatbot-for-NZL
link:      https://github.com/nzpco/PCO-AI-Chatbot-for-NZL
surfaced:  2026-05-21
what:      Official PCO sibling repo: a chatbot over New Zealand legislation.
alive:     2★; commit/contributor/release detail unrecorded
why:       A worked NZ-legislation RAG reference to compare against AnythingLLM-based approaches. Local-first: yes.
tags:      legal, nz, pco, chatbot, legislation, official

## nzpco/PCO-AI-Classification-of-Legislation
link:      https://github.com/nzpco/PCO-AI-Classification-of-Legislation
surfaced:  2026-05-21
what:      Official PCO sibling repo: AI classification of NZ legislation.
alive:     1★; commit/contributor/release detail unrecorded
why:       A reference for tagging/classifying NZ statutory text by topic or type. Local-first: yes.
tags:      legal, nz, pco, classification, legislation, official

## nzpco/PCO-AI-Plain-Language-Recommendations
link:      https://github.com/nzpco/PCO-AI-Plain-Language-Recommendations
surfaced:  2026-05-21
what:      Official PCO sibling repo: plain-language recommendations for legislative drafting.
alive:     3★; commit/contributor/release detail unrecorded
why:       A reference for a "plain-English rewrite" assist over clauses or advice letters. Local-first: yes.
tags:      legal, nz, pco, plain-language, drafting, official

## Wilfred/difftastic
link:      https://github.com/Wilfred/difftastic
surfaced:  2026-05-21
what:      A structure-aware (syntax-tree) diff for code that ignores reflowed whitespace and shows only real changes.
alive:     25.4k★; commit/contributor/release detail unrecorded
why:       The pattern transfers directly to contracts, where renumbering and reflow hide the true edits. Pair it with a Markdown/tree-sitter grammar to build a clause-level redliner far cleaner than Word's character compare. Wildcard: code → prose structural diff. Local-first: yes.
tags:      legal, structural-diff, tree-sitter, code-to-prose, clause-level, wildcard

## paulfitz/daff
link:      https://github.com/paulfitz/daff
surfaced:  2026-05-21
what:      Cell-level diff for tabular/CSV data with a visual highlight format and bindings across many languages.
alive:     905★; commit/contributor/release detail unrecorded
why:       Repurpose it for settlement statements, trust-ledger schedules, or rates apportionments where one wrong figure matters. Build a "what changed between two versions of this financial schedule?" viewer that points at the exact cell, not just the row. Wildcard: spreadsheet diff → financial-schedule diff. Local-first: yes.
tags:      legal, tabular-diff, csv, cell-level, financial-schedules, wildcard

## excalidraw/excalidraw
link:      https://github.com/excalidraw/excalidraw
surfaced:  2026-05-21
what:      An embeddable hand-drawn whiteboard component that works offline and autosaves locally.
alive:     124k★; commit/contributor/release detail unrecorded
why:       Embed it in your Tauri app to sketch chain-of-title, easements, subdivision layouts or settlement timelines — visual matter mapping with everything stored on your machine. Local-first: partial (offline PWA / embeddable component, no backend).
tags:      legal, whiteboard, offline-pwa, embeddable, matter-mapping

## spartypkp/open-source-legislation
link:      https://github.com/spartypkp/open-source-legislation
surfaced:  2026-05-21
what:      Aimed to be open global legislation data in an SQL knowledge-graph format with Python/TypeScript SDKs.
alive:     15★; dead — supporting infrastructure and data links have shut down; the repo page still resolves
why:       Excluded on 05-21 as dead: the bulk-download/SDK promise no longer functions. No live data backend to build on; revisit only if the infra is ever restored.
tags:      legal, legislation, knowledge-graph, dead-infra, scraping

## Ansvar-Systems/newzealand-law-mcp
link:      https://github.com/Ansvar-Systems/newzealand-law-mcp
surfaced:  2026-05-21
what:      Surfaced as a candidate NZ-law MCP server.
alive:     404 / nonexistent — a `repo:Ansvar-Systems/newzealand-law-mcp` lookup returns zero results
why:       Excluded on 05-21: the repository could not be found on GitHub. Nothing to fork.
tags:      legal, nz, mcp, 404, nonexistent

## NeptuneHub/AudioMuse-AI
link:      https://github.com/NeptuneHub/AudioMuse-AI
surfaced:  2026-05-20
what:      The analysis core behind the NV/Jellyfin plugins: Flask + Redis/RQ workers + PostgreSQL + Docker/K8s, librosa/ONNX/CLAP, REST + Swagger, and a chat module.
alive:     1.7k★; very active, active 2026-05; commit/contributor/release detail unrecorded
why:       A concrete, working blueprint for ASA's hosted worker-queue mode — copy the Flask + RQ + Postgres + container topology and the REST/Swagger surface.
tags:      audio, flask, redis-rq, postgres, k8s, queue, blueprint

## libAudioFlux/audioFlux
link:      https://github.com/libAudioFlux/audioFlux
surfaced:  2026-05-20
what:      C-core with Python bindings, pip-installable: mel/MFCC/CQT/chroma/pitch/onset/spectral feature extraction.
alive:     3.3k★; commit/contributor/release detail unrecorded
why:       A serious native, server-side feature-extraction complement to Essentia (no loudness — leave that to Essentia/rsgain) if ASA wants a second backend or to cross-check descriptors.
tags:      audio, native, features, mel, cqt, chroma, complement

## hugohow/mcp-music-analysis
link:      https://github.com/hugohow/mcp-music-analysis
surfaced:  2026-05-20
what:      Python MCP server wrapping librosa (beat/tempo/MFCC/chroma/spectral-centroid/onset) for LLM consumption.
alive:     commit/contributor/release detail unrecorded
why:       The closest analog to "expose ASA's analysis to Gemini as tools" — the most direct reference for ASA's planned MCP surface. Fork the librosa-feature→MCP-tool mapping and adapt it to ASA's richer Essentia/torchcrepe/Demucs JSON.
tags:      audio, mcp, librosa, analysis, llm

## tyiannak/pyAudioAnalysis
link:      https://github.com/tyiannak/pyAudioAnalysis
surfaced:  2026-05-20
what:      Established Python MIR library: MFCC, chroma, segmentation, classification.
alive:     commit/contributor/release detail unrecorded
why:       A native, importable baseline feature/segmentation set to compare Essentia's output against; long-known, nothing novel.
tags:      audio, native, python, features, segmentation, baseline

## audeering/opensmile
link:      https://github.com/audeering/opensmile
surfaced:  2026-05-20
what:      Mature C++ feature toolkit (speech + music) with Python wheels and reference-grade feature sets.
alive:     commit/contributor/release detail unrecorded
why:       Reference feature-set definitions and a second native extractor; speech-leaning, so cherry-pick the music-relevant descriptors.
tags:      audio, native, features, reference-sets, speech

## facebookresearch/demucs
link:      https://github.com/facebookresearch/demucs
surfaced:  2026-05-20
what:      Hybrid Transformer Demucs — the state-of-the-art music source-separation model.
alive:     commit/contributor/release detail unrecorded
why:       ASA's own L2 dependency (stems feed torchcrepe pitch). The model ASA already runs; the thing to keep current, swap variants of, or speed up (see demucs-next / demucs-mlx). Noted and logged for completeness on 05-20.
tags:      audio, pytorch, separation, core-dep, model

## maxrmorrison/torchcrepe
link:      https://github.com/maxrmorrison/torchcrepe
surfaced:  2026-05-20
what:      PyTorch port of the CREPE pitch tracker (per-frame F0 + periodicity/confidence, with decoding and filtering helpers).
alive:     commit/contributor/release detail unrecorded
why:       ASA's own L2 dependency — runs on Demucs stems for note/pitch analysis. Keep current and reuse its periodicity-thresholding/decoding as the reference for the pitch stage. Noted and logged for completeness on 05-20.
tags:      audio, pitch, crepe, f0, pytorch, core-dep

## Yuan-ManX/audio-development-tools
link:      https://github.com/Yuan-ManX/audio-development-tools
surfaced:  2026-05-20
what:      An awesome-list of audio development tools.
alive:     commit/contributor/release detail unrecorded
why:       Awesome-list, not a tool. Logged for completeness.
tags:      audio, awesome-list

## pettarin/awesome-python-audio-research
link:      https://github.com/pettarin/awesome-python-audio-research
surfaced:  2026-05-20
what:      An awesome-list of Python audio research tooling.
alive:     commit/contributor/release detail unrecorded
why:       Awesome-list, not a tool. Logged for completeness.
tags:      audio, awesome-list, python

## CPJKU/beat_this
link:      https://github.com/CPJKU/beat_this
surfaced:  2026-05-19
what:      Official ISMIR-2024 beat/downbeat tracker ("Beat This!") that drops the traditional DBN post-processing step in favour of a transformer with a shift-tolerant loss, shipping CLI + Python API and `.beats` export.
alive:     286★; created 2024, active 2026-05; commit/contributor/release detail unrecorded
why:       A current, accurate drop-in for ASA's tempo/beat stage that's lighter to wire up than madmom — fork the inference path and the `.beats` schema.
tags:      audio, beat, downbeat, tempo, transformer, ismir2024

## Polochon-street/bliss-rs
link:      https://github.com/Polochon-street/bliss-rs
surfaced:  2026-05-19
what:      Rust song-analysis library that extracts chroma, tempo and timbral features to compute track-to-track distance for automatic playlists (Spotify-Radio style).
alive:     159★; active 2026-05; commit/contributor/release detail unrecorded
why:       The compact feature vector and similarity framing are a clean reference if ASA grows a "tracks like this" axis, server-side. Calling it "off-stack" was the old browser bias — Rust is first-class.
tags:      audio, rust, similarity, chroma, tempo, playlists

## MTG/gaia
link:      https://github.com/MTG/gaia
surfaced:  2026-05-19
what:      Essentia's own C++/Python companion: similarity measures and SVM classifiers over Essentia descriptors, producing the high-level models Essentia loads to label music.
alive:     297★; still pushed in 2026 but last release 2019; commit/contributor/release detail unrecorded
why:       The upstream answer for "turn my low-level descriptors into mood/genre/danceability tags." Stale — prefer essentia-TF embeddings + a vector store; treat as reference. The original drop rationale was literally "C++/AGPL and not browser-friendly," which was the bias.
tags:      audio, essentia, similarity, classifier, stale, reference

## pianosnake/ireal-reader
link:      https://github.com/pianosnake/ireal-reader
surfaced:  2026-05-19
what:      Node module that parses iReal Pro exports into JS objects: title/composer/key/BPM plus a `measures` array of chord-symbol arrays, with repeats/segnos/codas expanded to linear measures.
alive:     43★; active 2026-05; commit/contributor/release detail unrecorded
why:       A direct ingest path for Harmonia — the entire iReal Pro jazz corpus becomes structured chord progressions with almost no parsing work.
tags:      audio, ireal, chords, parser, dataset

## CPJKU/partitura
link:      https://github.com/CPJKU/partitura
surfaced:  2026-05-19
what:      Python library for symbolic scores across MusicXML, MIDI, Humdrum kern and MEI, exposing notes (pitch/duration/voice/staff), parts, time signatures and beat maps.
alive:     350★; pushed 2026-05; commit/contributor/release detail unrecorded
why:       Off-stack (Python, not JS) but the cleanest reference for a complete symbolic data model if Harmonia ever needs richer score import/export than Tonal.js + MusicXML. Copy its note/part/timeline model.
tags:      audio, symbolic, musicxml, mei, kern

## a1ex90/MusicalKeyCNN
link:      https://github.com/a1ex90/MusicalKeyCNN
surfaced:  2026-05-19
what:      CQT-spectrogram CNN (after Korzeniowski & Widmer) for key estimation with pitch-shift augmentation, trained on GiantSteps, outputting Camelot-wheel labels at ~73.5% MIREX-weighted.
alive:     50★; created 2025-06; commit/contributor/release detail unrecorded
why:       Competitive with Mixed In Key. Full preprocessing/training/eval code, not a wrapper: a key signal both for ASA's tonal analysis and for grounding Harmonia's reharmonization in a detected key. Reuse the pitch-shift augmentation recipe.
tags:      audio, key, cnn, cqt, camelot, model

## christopherwxyz/remix-mcp
link:      https://github.com/christopherwxyz/remix-mcp
surfaced:  2026-05-19
what:      Rust Ableton-control MCP with 266 tools over OSC — control-only, no analysis despite the name.
alive:     266★; commit/contributor/release detail unrecorded
why:       Originally dropped as "more Ableton MCP / Link plumbing"; on-theme for ASA's Ableton+LLM control surface. A Rust reference for an OSC-based Ableton control layer if ASA's companion wants a native (non-M4L) write path.
tags:      audio, ableton, mcp, osc, rust

## urinieto/msaf
link:      https://github.com/urinieto/msaf
surfaced:  2026-05-19
what:      Native Python music-structure-analysis framework: boundary detection and segmentation (verse/chorus/section).
alive:     552★; from 2014; commit/contributor/release detail unrecorded
why:       ASA's section/structure stage — a legitimate reference for boundary algorithms; was wrongly dropped as "long-known, not newly relevant."
tags:      audio, native, python, structure, segmentation

## Sonata165/PhraseLDM_code
link:      https://github.com/Sonata165/PhraseLDM_code
surfaced:  2026-05-19
what:      Latent-diffusion full-song symbolic generation (research).
alive:     mostly a project page, README unreachable at capture; commit/contributor/release detail unrecorded
why:       Niche research; read the paper for phrase-level latent-diffusion ideas, code not packaged.
tags:      audio, research, diffusion, symbolic

## lunashia/o-m_beatmap_trainer
link:      https://github.com/lunashia/o-m_beatmap_trainer
surfaced:  2026-05-19
what:      osu!mania next-event beatmap trainer.
alive:     commit/contributor/release detail unrecorded
why:       The README never exposes the audio-feature layer and it's game-specific. Nothing usable — the rhythm-game beatmap framing is the only (off-target) idea.
tags:      audio, beatmap, osu, game-specific

## astradzhao/music-rfm
link:      https://github.com/astradzhao/music-rfm
surfaced:  2026-05-19
what:      Recursive-feature-machine steering for autoregressive music generation.
alive:     commit/contributor/release detail unrecorded
why:       Interesting paper, narrow utility for either project. The RFM-steering idea only.
tags:      audio, research, steering, generation

## Rezonality/zing
link:      https://github.com/Rezonality/zing
surfaced:  2026-05-19
what:      GUI audio-I/O toolkit.
alive:     commit/contributor/release detail unrecorded
why:       Not MIR; re-checked on 05-20 and stays dropped.
tags:      audio, audio-io, gui, off-domain

## snejus/beetcamp
link:      https://github.com/snejus/beetcamp
surfaced:  2026-05-19
what:      Bandcamp metadata autotagger plugin for beets.
alive:     commit/contributor/release detail unrecorded
why:       Off-topic — catalog metadata, no audio analysis. Only relevant if a Bandcamp-import metadata path were ever needed.
tags:      audio, bandcamp, metadata, beets, off-topic

## dogayuksel/webKeyFinder
link:      https://github.com/dogayuksel/webKeyFinder
surfaced:  2026-05-18
what:      libKeyFinder (C++) compiled to WASM via Emscripten, fed by an AudioWorkletProcessor and Web Workers, wrapped in Preact.
alive:     35★; pushed 2026-03; commit/contributor/release detail unrecorded
why:       The cleanest current template for the exact plumbing Harmonia would need to add audio→key: WASM DSP in a worker, worklet pulling PCM, all in-browser. For ASA the real nugget is the underlying native libKeyFinder (run it server-side, skip the WASM).
tags:      audio, key, wasm, libkeyfinder, worklet

## brightlikethelight/music21-mcp-server
link:      https://github.com/brightlikethelight/music21-mcp-server
surfaced:  2026-05-18
what:      FastMCP server exposing 13 music21 tools — Roman numerals, cadence detection, voice leading, harmonization, counterpoint — plus HTTP/CLI mirrors for when MCP itself misbehaves.
alive:     22★; commit/contributor/release detail unrecorded
why:       Worth a look as the "music theory through an LLM" surface, but read the author's own "40-50% MCP production success rate" caveat before treating it as load-bearing. A FastMCP server exposing analysis/theory tools to an LLM *is* ASA's MCP-tool pattern — copy the tool-wrapping pattern and the HTTP/CLI fallback design.
tags:      audio, mcp, music21, theory, fastmcp

## casantosmu/audiodeck
link:      https://github.com/casantosmu/audiodeck
surfaced:  2026-05-18
what:      Self-hostable web spectrogram analyzer (Go server, browser-side render) aimed at sniffing out fake-lossless files via frequency-cutoff artifacts.
alive:     109★; created 2025-09; commit/contributor/release detail unrecorded
why:       Analysis itself is shallow, but the "thin Go shim + client-side spectrogram" topology is a clean shape to mimic if ASA grows a library-scan UI. The Go server-side analysis justifies it; the browser render is incidental.
tags:      audio, go, spectrogram, fake-lossless, server-side, library-scan

## ifeelvoid/keyfinder
link:      https://github.com/ifeelvoid/keyfinder
surfaced:  2026-05-18
what:      Native macOS app + VST/AU that detects key (Camelot), BPM and renders waveforms via a custom Krumhansl-Schmuckler engine (16k-point FFT, bass weighting), sharing one Swift `KeyFinderEngine` package across app and plugin.
alive:     45★; created 2026-03; commit/contributor/release detail unrecorded
why:       Off-stack (Swift/macOS) but a tidy worked example of a from-scratch K-S key detector and the app↔plugin shared-engine split. First pass called it "a thin product, off-stack."
tags:      audio, key, krumhansl, swift, vst

## MTG/essentia
link:      https://github.com/MTG/essentia
surfaced:  2026-05-17
what:      The native C++/Python MIR library (spectral, MFCC, YinFFT, key, onset, EBU R128) plus the Essentia model zoo.
alive:     commit/contributor/release detail unrecorded
why:       ASA's own core Phase-1 dependency. Dropped twice — as "the parent C++ library; ASA already depends on Essentia.js downstream" and "ASA's own upstream" — which was the flagship bias casualty: ASA's actual core dep is native Essentia 2.1b6, this library. The algorithm reference and upgrade target; lift the exact algos L1 needs and the pretrained TF model set (genre/mood/danceability).
tags:      audio, essentia, dsp, core-dep, model-zoo

## dreamrec/LivePilot
link:      https://github.com/dreamrec/LivePilot
surfaced:  2026-05-17
what:      The most ambitious Ableton-MCP so far: 465 tools / 56 domains, a 5,264-device atlas, an optional M4L spectral-perception bridge (9-band FFT, RMS/peak, Krumhansl-Schmuckler key, pitch, FluCoMa mel/chroma/onset), VST/AU/AAX corpus discovery, and 12 "creative engines" with before/after measurement.
alive:     21★; Python; active 2026-03; commit/contributor/release detail unrecorded
why:       Sits across both projects: the in-DAW analysis bridge is ASA-adjacent and the Krumhansl-Schmuckler key + chroma path is Harmonia-adjacent. The closest existing analog to *all* of ASA — Ableton MCP + an analysis bridge + a measure→act→measure loop. It was later dropped as "more Ableton plumbing," a direct artifact of not knowing ASA is Ableton+analysis+LLM. The K-S-key + chroma bridge is the harmonic nugget to fork.
tags:      audio, ableton, mcp, key, chroma, agentic

## wavey-ai/mel-spec
link:      https://github.com/wavey-ai/mel-spec
surfaced:  2026-05-17
what:      Rust mel/STFT primitives aligned with Whisper/librosa/PyTorch, plus a Sobel-edge-detection VAD that reuses the same mel tensor, and an 8-bit TGA interchange format for shipping quantized mel spectrograms between processes.
alive:     89★; created 2023, pushed within the 05-17 window; benchmarked ~476× realtime on M1; commit/contributor/release detail unrecorded
why:       The TGA mel-image interchange and WASM path (used by their Hush in-browser Whisper) are directly applicable if a wire format for mel data is wanted — though for ASA the WASM/TGA credit is irrelevant and the native Rust mel/STFT primitives are the squarely Phase-1 value. A fast, embeddable mel extractor.
tags:      audio, rust, mel, stft, native

## undef13/splifft
link:      https://github.com/undef13/splifft
surfaced:  2026-05-17
what:      Lightweight Python separation/transcription CLI: BS-Roformer (incl. HyperACE/Large Inst variants), Mel-Roformer, MDX23C TFC-TDF v3, plus `beat this!` (no-DBN beat tracking), PESTO pitch, basic-pitch polyphonic, with a registry of 110+ community models downloaded on demand.
alive:     40★; created 2025-06; pre-alpha; commit/contributor/release detail unrecorded
why:       Clean "swap separation backend" abstraction if ASA grows a pre-stage; modular dataclass/Pydantic design over zfturbo's MSST. The "plain data, pure functions, minimal deps" design and the model registry are the useful bits — real now that L2 is in scope, not hypothetical.
tags:      audio, python, registry, roformer, modular, swap-backend

## Boof2015/astra
link:      https://github.com/Boof2015/astra
surfaced:  2026-05-17
what:      Electron + native C++ DSP audiophile player: 10-band parametric EQ with live frequency-response, seven realtime visualizers on a customizable rack, gapless bit-perfect output (WASAPI Exclusive / CoreAudio HAL / ALSA hw), Dolby Atmos decode.
alive:     247★; created 2026-01; commit/contributor/release detail unrecorded
why:       The decoupled analysis-path-vs-output-path architecture and the visualizer rack UX are both directly cribbable for ASA.
tags:      audio, electron, cpp, eq, visualizer-rack, architecture

## markwilkins/midi-chord-reader
link:      https://github.com/markwilkins/midi-chord-reader
surfaced:  2026-05-17
what:      JUCE/C++ DAW plugin that names chords from a MIDI track during playback — normalises to a single octave while preserving the bass note, generates slash inversions (`Am/C`), filters 2nd/4th/6th passing tones, uses the lowest three notes for quality.
alive:     22★; commit/contributor/release detail unrecorded
why:       Tiny but a useful reference heuristic if Harmonia ever wants "given these MIDI notes, name the chord" outside its Tonal.js path.
tags:      audio, chord, midi, juce, heuristic

## Natooz/MidiTok
link:      https://github.com/Natooz/MidiTok
surfaced:  2026-05-17
what:      The canonical MIDI/abc tokenizer library: REMI, REMI+, MIDI-Like, TSD, Structured, CPWord, Octuple, MuMIDI, MMM, PerTok; BPE/Unigram/WordPiece training; HF Hub integration; Symusic-backed I/O.
alive:     870★; commit/contributor/release detail unrecorded
why:       Well-known to anyone in symbolic music gen — included only because it's the obvious dependency if Harmonia ever ingests/produces token sequences. Adopt rather than reimplement. Skip if you already know it.
tags:      audio, tokenizer, midi, symbolic

## bschoepke/ableton-live-mcp
link:      https://github.com/bschoepke/ableton-live-mcp
surfaced:  2026-05-17
what:      General-purpose Ableton MCP whose bet is "let the agent `eval` arbitrary Python inside Ableton, with a few hot-path tools for latency/reliability."
alive:     184★; Python; created 2026-05; active 2026-05; latency-tuned via Codex's `/goal`; commit/contributor/release detail unrecorded
why:       Different philosophy from producer-pal (curated tools); worth a read for the trade-off, but the third Ableton-MCP on the seen list — diminishing returns. The latency hot-path tooling is the reusable bit.
tags:      audio, ableton, mcp, eval, latency

## phones24/ep133-export-to-daw
link:      https://github.com/phones24/ep133-export-to-daw
surfaced:  2026-05-17
what:      PWA that reads `.pak` backups (or talks live over WebMIDI) from Teenage Engineering EP-133/EP-1320/EP-40 and exports Ableton Live projects, DAWproject archives, REAPER projects and MIDI — including sample envelopes and stretch modes.
alive:     88★; TypeScript; commit/contributor/release detail unrecorded
why:       Hardware-bound but the WebMIDI → DAWproject pipeline is reusable plumbing if Harmonia ever round-trips to a DAW, or if ASA ever round-trips its recommendations into a project file.
tags:      audio, webmidi, dawproject, ableton, export

## gluon/Void-LinkAudio
link:      https://github.com/gluon/Void-LinkAudio
surfaced:  2026-05-17
what:      Umbrella project for sample-accurate beat-synced audio over LAN between Max, TouchDesigner, VCV Rack, openFrameworks and Live 12.4+; v0.3 adds Linux ARM64/x86_64 for VCV and Pure Data.
alive:     25–40★ (recorded inconsistently across sweeps); active 2026-04; commit/contributor/release detail unrecorded
why:       Same author as the already-logged `gluon/ofxAbletonLinkAudio` (the openFrameworks sub-addon) — worth swapping the seen entry for if you only want the top-level project. Reference for sample-accurate inter-app audio transport if ASA ever needs to pull live audio from Ableton over the network rather than from a file.
tags:      audio, ableton-link, lan, audio-transport

## Conceptual-Machines/magda-core
link:      https://github.com/Conceptual-Machines/magda-core
surfaced:  2026-05-17
what:      AI-first DAW on C++20/JUCE/Tracktion Engine: natural-language chat generates a custom DSL that mutates the session, hybrid audio+MIDI tracks, 16 LFOs + 16 macros per device, nestable parallel racks, juce-llm + llama.cpp for local inference.
alive:     124★; C++; created 2026-01; commit/contributor/release detail unrecorded
why:       Tangential to both ASA and Harmonia but the cleanest "AI as a first-class DAW citizen" reference around — interesting precedent if either project ever sprouts an agentic surface. Study the NL→DSL→session-edit loop; the DSL-as-LLM-target design is the transferable idea.
tags:      audio, daw, juce, nl-dsl, agentic

## andremichelle/openDAW
link:      https://github.com/andremichelle/openDAW
surfaced:  2026-05-17
what:      Web-based DAW, AGPL, deliberately framework-light (Tauri/PWA wrapping wanted), with no MIR or analysis surface — pure composition.
alive:     1.6k★; created 2025-02; commit/contributor/release detail unrecorded
why:       The web-audio engineering and the project's "no SignUp / no Tracking" ethos are useful references for browser-first tools. A browser-bias survivor otherwise: ASA isn't a web DAW. Web-audio engine architecture only, if a browser front ever matters.
tags:      audio, web-daw, webaudio, agpl

## mhartzel/freelcs
link:      https://github.com/mhartzel/freelcs
surfaced:  2026-05-17
what:      Hotfolder-driven EBU R128 loudness-correction server (Python, Docker, mono → 5.1, per-stream).
alive:     25★; repo started 2012 but still pushed in 2026; README unreachable at one point; commit/contributor/release detail unrecorded
why:       Dropped twice as "not newly relevant" and "old, jivetalking already covers measure-then-correct," then kept: old code, but the drop-in/processed-out pipeline shape and the visual loudness-history output are a useful reference for ASA's loudness stage UX and topology.
tags:      audio, python, r128, docker, loudness-server, old

## uisato/ableton-mcp-extended
link:      https://github.com/uisato/ableton-mcp-extended
surfaced:  2026-05-17
what:      Extended Ableton MCP with parallel TCP + UDP servers (UDP for low-latency real-time control), ElevenLabs TTS for in-session narration/voice samples, and a custom-controller framework.
alive:     203★; Python; commit/contributor/release detail unrecorded
why:       First dropped as "yet another Ableton MCP fork with too much overlap," then kept: same family as producer-pal / bschoepke's ableton-live-mcp, but the UDP path and the controller-extension scaffold are the differentiators. Lift the UDP low-latency control path if a Live companion ever needs realtime parameter moves.
tags:      audio, ableton, mcp, udp, tts

## paladini/voice-separator-demucs
link:      https://github.com/paladini/voice-separator-demucs
surfaced:  2026-05-17
what:      FastAPI front in front of Demucs.
alive:     commit/contributor/release detail unrecorded
why:       Dropped three times as "a thin Demucs wrapper / same shape as a dozen others" — but FastAPI + Demucs is exactly ASA's L2-as-a-service shape. A minimal reference for wrapping the separator as an endpoint.
tags:      audio, fastapi, demucs, service

## scragnog/HOT-Step-CPP
link:      https://github.com/scragnog/HOT-Step-CPP
surfaced:  2026-05-17
what:      UI shim over `acestep.cpp`.
alive:     commit/contributor/release detail unrecorded
why:       ACE-Step is already on the seen list. Nothing beyond the ACE-Step model itself.
tags:      audio, ui-shim, acestep, cpp

## zsteinkamp/m4l-Knobbler4
link:      https://github.com/zsteinkamp/m4l-Knobbler4
surfaced:  2026-05-17
what:      Max-for-Live OSC parameter-control surface for tablets.
alive:     commit/contributor/release detail unrecorded
why:       A tool, not a platform, with no MIR/theory content. OSC-control surface wiring only, if a hardware/tablet control idea ever surfaces.
tags:      audio, m4l, osc, control

## simonholliday/subsequence
link:      https://github.com/simonholliday/subsequence
surfaced:  2026-05-17
what:      Generative MIDI sequencer.
alive:     commit/contributor/release detail unrecorded
why:       Not analysis. Generative-sequencer UX ideas only.
tags:      audio, midi, sequencer, generative

## dr-schlange/nallely-midi
link:      https://github.com/dr-schlange/nallely-midi
surfaced:  2026-05-17
what:      MIDI router / sequencer.
alive:     commit/contributor/release detail unrecorded
why:       Not analysis. MIDI-routing patterns only, if inter-device MIDI plumbing is ever needed.
tags:      audio, midi, router

## albertms10/music_notes
link:      https://github.com/albertms10/music_notes
surfaced:  2026-05-17
what:      Music-theory library in Dart.
alive:     commit/contributor/release detail unrecorded
why:       Off-stack for a JS Harmonia. Reference for a clean theory type-model (intervals/keys/scales).
tags:      audio, theory, dart

## pedromsantos/vaughan
link:      https://github.com/pedromsantos/vaughan
surfaced:  2026-05-17
what:      Music-theory library in F#.
alive:     commit/contributor/release detail unrecorded
why:       Off-stack. Functional-style theory modeling reference.
tags:      audio, theory, fsharp

## k2-fsa/sherpa-onnx
link:      https://github.com/k2-fsa/sherpa-onnx
surfaced:  2026-05-17
what:      Primarily a speech toolkit (ASR/TTS/speaker-diarization) on the ONNX runtime, with many language bindings.
alive:     commit/contributor/release detail unrecorded
why:       The music angle is marginal. Only if ASA ever needs on-device ASR (e.g. lyric transcription) — the ONNX deployment plumbing, not anything music-MIR.
tags:      audio, speech, asr, onnx

## rsxdalv/TTS-WebUI
link:      https://github.com/rsxdalv/TTS-WebUI
surfaced:  2026-05-17
what:      Generation/TTS WebUI.
alive:     commit/contributor/release detail unrecorded
why:       No analysis surface. Multi-model WebUI scaffolding only.
tags:      audio, tts, webui, generation

## JuzzyDee/audio-analyzer-rs
link:      https://github.com/JuzzyDee/audio-analyzer-rs
surfaced:  2026-05-14
what:      Pure-Rust MCP server that extracts the whole MIR stack — spectral centroid/bandwidth/rolloff/flatness, Krumhansl-Schmuckler key detection, pitch-class distribution, tonnetz, MFCCs, EBU R128 LUFS/true-peak/LRA, crest factor, HPSS, stereo field and section boundaries — in under 2s per track with no Python or FFmpeg.
alive:     21★; created 2026-03; commit/contributor/release detail unrecorded
why:       It's essentially ASA's entire feature set in one dependency-free crate, and the key / pitch-class / tonnetz outputs feed Harmonia's harmonic analysis too. Lift the dependency-free K-S key + pitch-class + tonnetz code as a server-side harmonic core, and the MCP tool surface as the "expose analysis to an LLM" pattern.
tags:      audio, rust, mcp, key, tonnetz, r128, mir-app

## openclaw/songsee
link:      https://github.com/openclaw/songsee
surfaced:  2026-05-14
what:      Go CLI that renders 9 frequency-domain views — spectrogram, mel, chroma, HPSS, self-similarity, loudness, tempogram, MFCC, spectral flux — from any ffmpeg-readable file with no Python deps.
alive:     59★; created 2026-01; commit/contributor/release detail unrecorded
why:       ASA needs almost exactly this set of mel/loudness/tonal visuals; the native-Go FFT pipeline and the grid-combining output are worth studying.
tags:      audio, go, spectrogram, mel, chroma, hpss, tempogram, viz

## DarienBrito/EssentiaTD
link:      https://github.com/DarienBrito/EssentiaTD
surfaced:  2026-05-14
what:      Five C++ CHOP plugins wrapping Essentia for TouchDesigner: spectrum, mel bands, MFCCs, pitch, key/scale, onset/BPM and EBU R128 loudness, in both realtime and batch modes.
alive:     91★; created 2026-03; commit/contributor/release detail unrecorded
why:       It's the cleanest recent map of which Essentia algorithms cover ASA's tonal-balance / dynamics / loudness brief and how to split realtime vs full-file analysis.
tags:      audio, essentia, mel, loudness, key, onset

## jhartquist/resonators
link:      https://github.com/jhartquist/resonators
surfaced:  2026-05-14
what:      Rust implementation of the Resonate algorithm — a fixed-memory, per-sample alternative to FFT/CQT for low-latency spectral analysis — with Python and WebAssembly bindings.
alive:     86★; created 2026-04; commit/contributor/release detail unrecorded
why:       The WASM target makes it a plausible drop-in for a browser DSP stage wanting sharper per-bin time-frequency tradeoffs than a stock STFT — though ASA has no browser DSP, so that rationale is void; what's left is the Rust→PyO3 per-sample spectral angle, niche next to Essentia.
tags:      audio, rust, per-sample, spectral, pyo3

## Angel2mp3/AudioAuditor
link:      https://github.com/Angel2mp3/AudioAuditor
surfaced:  2026-05-14
what:      Windows app that flags fake-lossless upsampling, digital clipping, MQA and AI-generated audio, plus dynamic-range and true-peak (4× oversampled) measurement and a log-frequency spectrogram viewer.
alive:     70★; C#; created 2026-03; commit/contributor/release detail unrecorded
why:       The dynamics + true-peak + spectral-ceiling logic overlaps ASA's dynamics stage directly; it's C#/Windows so treat it as reference, not reuse. The "diagnose-then-recommend" shape is the transferable part.
tags:      audio, dynamics, true-peak, clipping, fake-lossless, reference

## WB2024/Essentia-to-Metadata
link:      https://github.com/WB2024/Essentia-to-Metadata
surfaced:  2026-05-14
what:      Local genre/mood tagger built on Essentia's Discogs-Effnet embeddings, Discogs-400 genre CNN and MTG-Jamendo mood classifier, writing tags straight to files.
alive:     75★; created 2026-02; commit/contributor/release detail unrecorded
why:       Relevant as a worked example of running Essentia's pretrained ML models fully offline — it's classification, not the tonal/loudness analysis ASA centers on, though the per-format tag-writing layer matters more than the first pitch implied.
tags:      audio, essentia-tf, genre, mood, offline

## craiglush/navidrome-mood-plugin
link:      https://github.com/craiglush/navidrome-mood-plugin
surfaced:  2026-05-14
what:      Navidrome plugin using essentia-tensorflow + Discogs-EffNet to score mood, danceability, energy and BPM with genre-aware corrections, then auto-building 13 themed playlists.
alive:     55★; created 2026-03; commit/contributor/release detail unrecorded
why:       Useful as a reference for Essentia-TF embeddings and the genre-context-boost trick; it's a media-server plugin, not a DSP library. It ships a separate FastAPI analyzer *because "essentia can't run inside WASM"* — which directly validates ASA's server-side architecture.
tags:      audio, essentia-tf, fastapi, mood, validates-arch

## NeptuneHub/AudioMuse-AI-NV-plugin
link:      https://github.com/NeptuneHub/AudioMuse-AI-NV-plugin
surfaced:  2026-05-14
what:      Navidrome plugin doing sonic-analysis-based song/artist similarity for instant-mix and radio features, backed by a Flask + Worker analysis container.
alive:     240★; created 2026-01; commit/contributor/release detail unrecorded
why:       Thinner on disclosed DSP detail than the mood plugin — included as a second data point on Essentia-driven similarity architecture; drop if similarity isn't a use case you're chasing. The real value is the Flask + Redis/RQ workers + PostgreSQL + Docker/K8s queue architecture of its core, a blueprint for ASA's hosted mode.
tags:      audio, navidrome, similarity, flask, worker, plugin

## marcus/good-composer
link:      https://github.com/marcus/good-composer
surfaced:  2026-05-14
what:      Streams MIDI from an LLM (Ollama or OpenRouter) over WebSocket with a custom piano-roll that draws notes as they generate; FastAPI backend, Tone.js frontend.
alive:     33★; created 2025-12; commit/contributor/release detail unrecorded
why:       No music-theory library involved — relevant to Harmonia only as a pattern for real-time MIDI playback and progressive piano-roll rendering, not for reharm logic. But FastAPI + WebSocket streaming + React + LLM is ASA's exact stack pattern for streaming Phase-2 output to the UI.
tags:      audio, llm, streaming, fastapi, websocket

## Ryan5453/demucs-next
link:      https://github.com/Ryan5453/demucs-next
surfaced:  2026-05-14
what:      Modernized fork of Demucs (current PyTorch/TorchCodec, Cog REST integration) reporting ~2–3× faster separation at equal-or-better SDR.
alive:     26★; alpha; commit/contributor/release detail unrecorded
why:       Only relevant if ASA adds a stem-separation pre-stage; it's a straight speed/packaging refresh of a model you'd already reach for — except separation is current L2 scope, which makes it a direct speed win with REST packaging.
tags:      audio, pytorch, demucs-fork, faster, cog-rest

## flarkflarkflark/STEMwerk-reaper
link:      https://github.com/flarkflarkflark/STEMwerk-reaper
surfaced:  2026-05-14
what:      REAPER plugin: Lua glue calling audio-separator/Demucs from the DAW.
alive:     commit/contributor/release detail unrecorded
why:       A thin wrapper around audio-separator/Demucs; nothing new beyond the DAW integration. Logged for completeness.
tags:      audio, reaper, lua, wrapper, thin

## crlandsc/torch-l1-snr
link:      https://github.com/crlandsc/torch-l1-snr
surfaced:  2026-05-14
what:      L1-SNR loss functions for training separation models.
alive:     commit/contributor/release detail unrecorded
why:       Neither ASA nor Harmonia trains models — ASA runs pretrained Demucs. Only relevant if you ever fine-tune.
tags:      audio, pytorch, training-loss, out-of-scope

## sildater/parangonar
link:      https://github.com/sildater/parangonar
surfaced:  2026-05-14
what:      Score-to-performance alignment library.
alive:     commit/contributor/release detail unrecorded
why:       Solid, but neither project does symbolic alignment. The alignment algorithms if note-to-performance matching ever becomes a feature.
tags:      audio, alignment, symbolic

## JulienVincenot/MOZLib
link:      https://github.com/JulienVincenot/MOZLib
surfaced:  2026-05-14
what:      Max/Lisp computer-aided-composition teaching package.
alive:     commit/contributor/release detail unrecorded
why:       Off-stack for both. CAC technique ideas only.
tags:      audio, cac, max, lisp

## creightonlinza/forever-jukebox
link:      https://github.com/creightonlinza/forever-jukebox
surfaced:  2026-05-13
what:      End-to-end Infinite-Jukebox replacement: madmom-beats-lite + Essentia generate beats/segments/sections locally and serve them through a small REST API, replacing Spotify's now-dead Audio Analysis endpoint.
alive:     24★; TypeScript+Python; created 2026-01; commit/contributor/release detail unrecorded
why:       Direct reference for the shape of ASA's analysis → JSON contract, and a local REST analysis service — fork the API surface and the beat/segment/section schema.
tags:      audio, jukebox, essentia, beats, rest, json-contract

## httpsworldview/openmeters
link:      https://github.com/httpsworldview/openmeters
surfaced:  2026-05-13
what:      Linux audio metering in Rust: short-term/momentary LUFS to ITU-R BS.1770-5, true peak, A-weighted spectrum, spectrogram with spectral reassignment for sharp time-frequency resolution, oscilloscope, goniometer.
alive:     135★; created 2025-10; commit/contributor/release detail unrecorded
why:       The reassignment trick and the exact BS.1770 revision are worth lifting; UI is wgpu/Iced.
tags:      audio, rust, lufs, bs1770, true-peak, spectral-reassignment

## Ircam-Partiels/Partiels
link:      https://github.com/Ircam-Partiels/Partiels
surfaced:  2026-05-13
what:      IRCAM's Vamp-plugin host wrapping FFT, LPC, transients, F0, formants and tempo behind a JUCE GUI, with batch CLI and exports to CSV/SDIF/JSON/REAPER/Max/PD.
alive:     74★; C++; commit/contributor/release detail unrecorded
why:       Useful as a reference for how a serious analysis tool structures multi-track, multi-channel pipelines and result interchange — and the SDIF export format is worth a look for ASA result storage.
tags:      audio, vamp, juce, export, sdif, interchange

## bananaofhappiness/soundscope
link:      https://github.com/bananaofhappiness/soundscope
surfaced:  2026-05-13
what:      Rust TUI loudness analyzer: LUFS + true peak + FFT spectrum + min-max-decimated waveform on files or live mic.
alive:     174★; commit/contributor/release detail unrecorded
why:       Smaller scope than openmeters and CLI-only; mostly useful as a second BS.1770 implementation to cross-check against.
tags:      audio, rust, tui, lufs, true-peak, cross-check

## JeffreyCA/spleeter-web
link:      https://github.com/JeffreyCA/spleeter-web
surfaced:  2026-05-13
what:      Self-hostable React + Django app (Celery/Redis + Docker) for vocal/bass/drums isolation backed by Spleeter, Demucs and BS-RoFormer, with a job queue.
alive:     544★; pushed within the 05-13 window but the project itself is from 2019; commit/contributor/release detail unrecorded
why:       Not a new idea, but the React front for queueing/running stem jobs is a useful pattern if ASA grows a stem-separation stage. React + queue + Docker running Demucs *is* ASA's app+queue+L2 shape — only the web framework differs.
tags:      audio, react, django, celery, demucs, queue

## ptnghia-j/ChordMiniApp
link:      https://github.com/ptnghia-j/ChordMiniApp
surfaced:  2026-05-13
what:      Next.js + Flask app that does chord recognition (Chord-CNN-LSTM, BTC-SL/PL from ISMIR2019), beat tracking (Beat-Transformer + madmom), lyrics (Music.ai + LRClib), and renders sheet via OpenSheetMusicDisplay with chord-db guitar diagrams.
alive:     282★; TypeScript; commit/contributor/release detail unrecorded
why:       This is the closest public neighbor to Harmonia's product surface; read its UX choices before adding new ones. The Flask chord-recognition service is a forkable audio→chord backend.
tags:      audio, chord, beat, lyrics, sheet, nextjs

## spyroskantarelis/chordonomicon
link:      https://github.com/spyroskantarelis/chordonomicon
surfaced:  2026-05-13
what:      666K symbolic chord progressions with section labels (verse/chorus/bridge), genre and release date, encoded as single chord / triad (root+quality+bass) / tetrad (+extensions) tokens on Hugging Face.
alive:     143★; commit/contributor/release detail unrecorded
why:       Drop-in training/eval set for any reharmonization model and a benchmark with RNN/GRU/LSTM baselines already published — fork the tokenization scheme and baselines.
tags:      audio, dataset, chords, progressions, hf

## vpavlenko/rawl
link:      https://github.com/vpavlenko/rawl
surfaced:  2026-05-13
what:      React+TS MIDI/MusicXML visualizer that color-codes pitch classes ("12 colors") and annotates harmonic language across classical, jazz, chiptune and modal systems.
alive:     81★; commit/contributor/release detail unrecorded
why:       Worth studying for piano-roll rendering and pedagogically motivated harmony annotations; the "harmony as flags" framing is a Harmonia-adjacent take. Reuse the 12-color pitch-class palette for any harmonic visualization.
tags:      audio, visualizer, harmony, pianoroll, midi

## rzru/nightingale
link:      https://github.com/rzru/nightingale
surfaced:  2026-05-13
what:      Tauri (Rust + React) karaoke app combining Demucs/UVR vocal isolation, WhisperX/Parakeet-v3 lyric transcription with word timestamps, real-time pitch scoring, and key/tempo shifting.
alive:     1.1k★; created 2026-03, active 2026-03; commit/contributor/release detail unrecorded
why:       Hits both projects: the local-PyTorch-from-Tauri shape is a template for ASA, and the pitch-scoring/key-shift logic is adjacent to Harmonia's note-domain code.
tags:      audio, tauri, demucs, transcription, pitch, key-shift

## openvpi/GAME
link:      https://github.com/openvpi/GAME
surfaced:  2026-05-13
what:      Singing-voice → MIDI transcription via D3PM (structured denoising diffusion) with adaptive boundary extraction; ONNX-exportable, Python 3.12, PyTorch Lightning.
alive:     161★; commit/contributor/release detail unrecorded
why:       Not on-stack, but if Harmonia ever ingests sung input the F0 + boundary outputs would be the upstream; otherwise a technique reference for diffusion-based transcription.
tags:      audio, singing, midi, diffusion, onnx, transcription

## adamjmurray/producer-pal
link:      https://github.com/adamjmurray/producer-pal
surfaced:  2026-05-13
what:      Max-for-Live device + MCP server letting Claude/Gemini/ChatGPT/Ollama drive an Ableton Live session through natural language.
alive:     143★; JavaScript; active 2026-05; commit/contributor/release detail unrecorded
why:       Not directly ASA/Harmonia, but it's the cleanest current example of M4L ↔ MCP plumbing if either project ever wants a DAW-side companion. ASA *is* Ableton+Gemini, so it's really the "apply the Phase-2 recommendation in Live" companion — fork the M4L↔MCP bridge wholesale as the write-side.
tags:      audio, ableton, mcp, m4l, gemini

## prabal-rje/latentscore
link:      https://github.com/prabal-rje/latentscore
surfaced:  2026-05-13
what:      Retrieval-based ambient music generation: a sentence-transformer (or LAION-CLAP) embeds a prompt, cosine-matches against ~10k pre-computed synth configs, and drives a real-time CPU synth — no GPU, ~2s latency.
alive:     36★; Python; commit/contributor/release detail unrecorded
why:       Interesting as a "music as configuration retrieval" pattern; not a generative model in the usual sense. A cheap, no-GPU template for an audition path that wants config retrieval rather than neural generation.
tags:      audio, retrieval, ambient, clap, synth

## JorenSix/Olaf
link:      https://github.com/JorenSix/Olaf
surfaced:  2026-05-13
what:      Portable acoustic fingerprinting in C with WASM and ESP32 targets.
alive:     396★; created 2020 but still actively pushed in 2026; commit/contributor/release detail unrecorded
why:       Tangential to ASA's core but a clean reference if you ever need audio identification or cross-take alignment in-browser. Strip the in-browser novelty, though, and audio identification isn't an ASA use case.
tags:      audio, fingerprinting, c, identification

## innermost47/ai-dj
link:      https://github.com/innermost47/ai-dj
surfaced:  2026-05-13
what:      Server-side Python (Stable Audio Open) loop-generator VST, now renamed OBSIDIAN-Neural.
alive:     commit/contributor/release detail unrecorded
why:       Originally dropped as "pure generation, no analysis or theory overlap," then un-dropped because ASA Phase-3 is on-demand audition-sample generation — this is a Phase-3 plumbing reference. Fork the Stable-Audio-Open loop-generation server as a starting point.
tags:      audio, generation, stable-audio, vst

## sanderwood/clamp3
link:      https://github.com/sanderwood/clamp3
surfaced:  2026-05-13
what:      ACL 2025 framework that contrastively aligns text, sheet music, audio (via MERT features), MIDI and images into one 27-language embedding space — CLAP but multi-modal.
alive:     239★; Python; created 2025-02, active 2025-02; commit/contributor/release detail unrecorded
why:       The value is the audio-side feature extractor and the retrieval primitives (find tracks-like-this, prompt-to-track) — drop in ahead of any reach for tagging/similarity.
tags:      audio, embeddings, multimodal, retrieval, clap

## linuxmatters/jivetalking
link:      https://github.com/linuxmatters/jivetalking
surfaced:  2026-05-13
what:      Go CLI that measures a recording's integrated LUFS, true peak, LRA (EBU R128), noise floor and spectral signature, then picks per-pass filter params from that — adaptive de-essing, gating, comp, two-stage R128 normalisation to -16 LUFS.
alive:     71★; created 2025-11; commit/contributor/release detail unrecorded
why:       The "measure first, then choose parameters" pipeline is exactly what ASA's loudness + dynamics stage should output as recommendations. Model the recommendation output on it.
tags:      audio, go, r128, adaptive-params, measure-then-choose

## crlandsc/moises-light
link:      https://github.com/crlandsc/moises-light
surfaced:  2026-05-13
what:      Unofficial PyTorch implementation of "Moises-Light: Resource-efficient Band-split U-Net" (WASPAA 2025) with RoPE bottleneck borrowed from BS-RoFormer.
alive:     27★; created 2026-03; training-only, no weights; commit/contributor/release detail unrecorded
why:       Useful as a clean modern band-split reference if ASA ever adds a separation pre-stage; otherwise read the paper.
tags:      audio, pytorch, band-split, unet, training-only

## sweetspotsoundsystem/stemgen-rt
link:      https://github.com/sweetspotsoundsystem/stemgen-rt
surfaced:  2026-05-13
what:      Real-time HS-TasNet 4-stem separation as a JUCE/VST3/AU plugin at 11.6 ms latency, with async inference threading and crossover/gating DSP polish.
alive:     27★; created 2026-01; inference model is binary-only; commit/contributor/release detail unrecorded
why:       Reference for the *plumbing* (async ONNX in a plugin callback, 44.1k constraint) rather than a model to lift.
tags:      audio, juce, vst, realtime, tasnet, plumbing

## matteospanio/torchfx
link:      https://github.com/matteospanio/torchfx
surfaced:  2026-05-13
what:      PyTorch-native audio DSP — filters as `nn.Module`s, composable with `|`/`+`, differentiable, GPU.
alive:     131★; created 2025-03; only a couple of filters shipped (LoButterworth, ParametricEQ); commit/contributor/release detail unrecorded
why:       The appeal is the pattern for batching ASA's analysis filters on GPU if it ever moves off Essentia for a bulk pass. No MIR/loudness in-box.
tags:      audio, pytorch, dsp, filters, gpu, server-side

## madderscientist/noteDigger
link:      https://github.com/madderscientist/noteDigger
surfaced:  2026-05-13
what:      "No framework, no library" pure-JS audio-to-MIDI transcription: optimised real-FFT STFT, CQT, ONNX nnls.js + spectral-clustering for note picking, plus harmonic reduction and beat tracking.
alive:     268★; pushed within the 05-13 window; commit/contributor/release detail unrecorded
why:       The closest reference for the analysis half of a browser-native Harmonia ingest path — and the deliberate zero-deps constraint is instructive for bundle size. (0% ASA-relevant, being client-side JS.)
tags:      audio, transcription, midi, cqt, onnx

## chromatone/chromatone.center
link:      https://github.com/chromatone/chromatone.center
surfaced:  2026-05-13
what:      Vue/Vite app on top of Tonal.js + abcjs + Tone.js + audiomotion-analyzer presenting chords, scales, rhythms and pitch-color visualisations as PWA "instruments".
alive:     146★; started 2021 but actively pushed; commit/contributor/release detail unrecorded
why:       Direct overlap with Harmonia's stack; worth pillaging for chord/scale visual idioms and the color-coded pitch palette.
tags:      audio, theory, tonaljs, scales, pwa

## williamzujkowski/live-coding-music-mcp
link:      https://github.com/williamzujkowski/live-coding-music-mcp
surfaced:  2026-05-13
what:      MCP server exposing Strudel.cc to Claude/Anthropic clients for live-coded pattern generation.
alive:     200★; TypeScript; created 2025-08; commit/contributor/release detail unrecorded
why:       Same MCP-in-the-DAW family as producer-pal but on the browser-pattern side; included mainly as a second data point if Harmonia ever wants an LLM-driven "reharm-as-pattern" channel. Nothing on the analysis path.
tags:      audio, mcp, strudel, livecoding, generation

## complexlogic/rsgain
link:      https://github.com/complexlogic/rsgain
surfaced:  2026-05-13
what:      Native C++ EBU R128 + true-peak + ReplayGain 2.0 CLI.
alive:     603★; active 2026; commit/contributor/release detail unrecorded
why:       Dropped verbatim for being "off-stack for ASA's in-browser/in-pipeline scope," which was the bias — it's a Phase-1 loudness reference in the same role as openmeters/soundscope, a clean fast native R128/true-peak implementation to cross-check against.
tags:      audio, native, cpp, r128, true-peak, replaygain

## ssmall256/demucs-mlx
link:      https://github.com/ssmall256/demucs-mlx
surfaced:  2026-05-13
what:      Demucs ported to Apple MLX — pip-importable (`from demucs_mlx import Separator`), ~73× realtime on Apple Silicon.
alive:     commit/contributor/release detail unrecorded
why:       Dropped as "a straight port of a known model" — but ASA is local-first and its users are Mac producers, so it's an L2 drop-in for fast on-device separation.
tags:      audio, mlx, apple-silicon, demucs, drop-in, local-first

## jpoindexter/ableton-mcp
link:      https://github.com/jpoindexter/ableton-mcp
surfaced:  2026-05-13
what:      Python Ableton MCP with 200+ tools, Gemini-capable.
alive:     commit/contributor/release detail unrecorded
why:       Dropped as "another Ableton-via-MCP take, thinner than the already-logged producer-pal," then un-dropped as on-theme for ASA's Ableton+LLM surface. A second, broader Ableton-MCP tool inventory to compare against producer-pal when deciding write-side tool granularity.
tags:      audio, ableton, mcp, gemini

## asteroid-team/asteroid
link:      https://github.com/asteroid-team/asteroid
surfaced:  2026-05-13
what:      Mature PyTorch audio source-separation toolkit (recipes, models, datasets).
alive:     commit/contributor/release detail unrecorded
why:       Dropped merely as "established" — but separation is L2 in-scope, so a mature PyTorch separation toolkit is a legitimate reference.
tags:      audio, pytorch, separation-toolkit, established

## gluon/ofxAbletonLinkAudio
link:      https://github.com/gluon/ofxAbletonLinkAudio
surfaced:  2026-05-13
what:      openFrameworks addon for Ableton Link Audio streaming.
alive:     superseded by the umbrella `gluon/Void-LinkAudio`; commit/contributor/release detail unrecorded
why:       Tangential plumbing, and superseded — use the umbrella project instead.
tags:      audio, ableton-link, openframeworks, superseded

## gibber-cc/gibberwocky
link:      https://github.com/gibber-cc/gibberwocky
surfaced:  2026-05-13
what:      Browser live-coding environment that sequences and modulates Ableton Live and Max from JS.
alive:     2015 project, recently touched; commit/contributor/release detail unrecorded
why:       Recently touched but not "newly relevant." The live-code→Ableton/Max control-mapping idea only; superseded by the newer MCP/M4L tools.
tags:      audio, livecoding, ableton, max, browser

## charlesvestal/schwung
link:      https://github.com/charlesvestal/schwung
surfaced:  2026-05-13
what:      Ableton Move firmware shim.
alive:     commit/contributor/release detail unrecorded
why:       Specific to one piece of hardware. Nothing transferable.
tags:      audio, ableton-move, hardware, shim

## cuthbertLab/music21j
link:      https://github.com/cuthbertLab/music21j
surfaced:  2026-05-13
what:      JS port of music21.
alive:     commit/contributor/release detail unrecorded
why:       Well-known, on every music-theory shortlist already. Browser-side theory primitives (notes, intervals, keys) if a JS theory dep is wanted — adopt, don't reimplement.
tags:      audio, theory, music21, js

## asigalov61/tegridy-tools
link:      https://github.com/asigalov61/tegridy-tools
surfaced:  2026-05-13
what:      Symbolic-music NLP toolkit from 2020.
alive:     recent commits but no new direction; commit/contributor/release detail unrecorded
why:       Grab specific MIDI-processing utilities only; nothing architecturally new.
tags:      audio, symbolic, midi, nlp

## ace-step/ACE-Step-1.5
link:      https://github.com/ace-step/ACE-Step-1.5
surfaced:  2026-05-13
what:      Large text-to-music generation model.
alive:     commit/contributor/release detail unrecorded
why:       Well-known and orthogonal to both projects. Only as the upstream model if Phase-3 ever wants full-track gen rather than short auditions.
tags:      audio, text-to-music, generation, known

## fspecii/ace-step-ui
link:      https://github.com/fspecii/ace-step-ui
surfaced:  2026-05-13
what:      UI over ACE-Step.
alive:     commit/contributor/release detail unrecorded
why:       Generation-side, no analysis. UI patterns for driving a gen model only.
tags:      audio, ui, acestep, generation

## HeartMuLa/heartlib
link:      https://github.com/HeartMuLa/heartlib
surfaced:  2026-05-13
what:      Music-generation library.
alive:     commit/contributor/release detail unrecorded
why:       Well-known and orthogonal to both projects. Nothing specific to the analysis path.
tags:      audio, generation, known

## daniel-c-silva/SynthBridge
link:      https://github.com/daniel-c-silva/SynthBridge
surfaced:  2026-05-13
what:      NumPy sine-wave synth behind a Flask endpoint.
alive:     commit/contributor/release detail unrecorded
why:       Thin — its "reharmonization" is just chord playback, with no analysis or theory.
tags:      audio, synth, flask, thin

## FoxNoseTech/diarize
link:      https://github.com/FoxNoseTech/diarize
surfaced:  2026-05-13
what:      Speech diarization tool.
alive:     commit/contributor/release detail unrecorded
why:       Speech diarization, not music.
tags:      audio, speech, diarization, off-domain

## ModernMube/OwnAudioSharp
link:      https://github.com/ModernMube/OwnAudioSharp
surfaced:  2026-05-13
what:      C#/.NET audio library.
alive:     commit/contributor/release detail unrecorded
why:       C# only; off ASA's Python stack. (Reasoning corrected later: a stack mismatch, not a native penalty.)
tags:      audio, csharp, dotnet, off-stack

## Asvarox/allkaraoke
link:      https://github.com/Asvarox/allkaraoke
surfaced:  2026-05-13
what:      Browser karaoke with pitch detection.
alive:     2022 project; commit/contributor/release detail unrecorded
why:       The README doesn't expose the analysis layer and it's a 2022 project.
tags:      audio, karaoke, browser, pitch

## WeebLabs/DSPi
link:      https://github.com/WeebLabs/DSPi
surfaced:  2026-05-13
what:      RP2040 audio-DSP firmware.
alive:     commit/contributor/release detail unrecorded
why:       Hardware-only (microcontroller firmware); off a server-side software stack. Logged for completeness.
tags:      audio, hardware, rp2040, firmware

## BillyDM/awesome-audio-dsp
link:      https://github.com/BillyDM/awesome-audio-dsp
surfaced:  2026-05-13
what:      An awesome-list of audio DSP resources.
alive:     commit/contributor/release detail unrecorded
why:       Awesome-list, already on most people's radar — not a tool. Evaluated on 05-13 but never logged until the 05-20 pass.
tags:      audio, awesome-list, dsp

## EmulationAI/awesome-large-audio-models
link:      https://github.com/EmulationAI/awesome-large-audio-models
surfaced:  2026-05-13
what:      An awesome-list of large audio models.
alive:     commit/contributor/release detail unrecorded
why:       Awesome-list, already on most people's radar — not a tool. Evaluated on 05-13 but never logged until the 05-20 pass.
tags:      audio, awesome-list, models
