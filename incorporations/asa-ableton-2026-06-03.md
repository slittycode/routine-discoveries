# ASA incorporation plan — asa-ableton companion + analysis backends (2026-06-03)

Drawn from `discoveries/audio-mir-2026-06-03.md`. Sorts that sweep's
ASA-relevant finds into **two kinds of work**, because of one architectural
fact:

> **ASA is a server-side Python/FastAPI app that *emits* Ableton Live 12
> device/parameter/value recommendations as JSON — it does not touch
> Ableton.** (Per `routines/audio-mir.md`; treat ASA's own `CLAUDE.md` as
> authoritative if it disagrees.)

So anything that improves the **analysis** folds *into* the ASA repo
(Part A). Anything that **acts on Ableton** must live in a *separate*
codebase — Live extensions / remote scripts run inside Ableton, not in a
FastAPI backend — and is the seed of a downstream companion program,
`asa-ableton` (Part B). Each track is independent: pick up, pause, or drop
without blocking the others.

Licence convention (as in `asa-2026-05-13.md` / `forking-plans-2026-05-14.md`):
every upstream's licence is **unconfirmed** until verified, and confirming it
is always step one of Definition of done. The discovery stream ignores
licence; incorporation does not.

---

# Part A — fork *into* the current ASA repo (analysis internals)

## Track A1: MSST-WebUI → ASA stem-separation backend

- **Source:** https://github.com/SUC-DriverOld/MSST-WebUI — Python, ~1.2k★,
  created Jul 2024, 14 releases. Licence: **TBD (confirm first).**
- **What to lift:** the **inference** path for the Music-Source-Separation-
  Training models it bundles (MSST / VR / BS-RoFormer ensembles), *not* the
  PySide6 desktop UI. Specifically: model loading, the separation call, and
  its ensemble logic.
- **Why:** ASA's stems stage runs Demucs; these models beat Demucs on most
  stem types, and ensembling lifts quality further. This is a drop-in
  quality win behind ASA's existing stems JSON contract.
- **Approach:** **incorporate as a backend, not a fork.** Add a pluggable
  separator interface in ASA's worker (`demucs` | `msst`), drive MSST's
  inference directly from Python, keep the emitted stems schema unchanged.
  Gate behind a config flag; keep Demucs as the default until A/B clears.
- **Cross-check oracle:** ASA's current **Demucs** output — diff stem SDR /
  artefacts on a fixed reference set before promoting MSST.
- **Definition of done:**
  - [ ] MSST-WebUI licence confirmed; model-weight licences confirmed
        separately (often distinct from the repo licence)
  - [ ] `Separator` interface in ASA with `demucs` + `msst` backends, same
        stems JSON out
  - [ ] A/B harness: SDR + runtime, MSST vs Demucs, on ≥5 reference tracks
  - [ ] Flag-gated; Demucs remains default until results documented
- **Risks:** heavy model weights / VRAM; per-model weight licences may bar
  some models even if the repo is permissive; the project is GUI-first, so
  the scriptable inference surface may need extraction.

## Track A2: MOSS-Audio → ASA Phase-2 interpretation backend (self-hosted)

- **Source:** https://github.com/OpenMOSS/MOSS-Audio — Python, ~520★,
  created Apr 2026; 4B/8B weights on HF/ModelScope; tech report Jun 2026.
  Licence: **TBD — confirm BOTH code and model-weight licences first.**
- **What to lift:** the model itself as a **sidecar service** behind a small
  FastAPI endpoint — fed the same audio + Phase-1 measurement JSON ASA
  already produces — emitting measurement-cited, timestamp-aware
  interpretation. Lift its task decomposition (structure / chord / key /
  tempo reasoning, captioning, time-aware QA), not its repo wholesale.
- **Why:** a self-hostable alternative/supplement to the **Gemini Phase-2
  layer** — offline, no per-call cost, no data leaving the host. Phase 2 is
  already optional and flag-gated (`VITE_ENABLE_PHASE2_GEMINI`), so a second
  provider slots into an existing seam.
- **Approach:** **incorporate as a backend** behind a `Phase2Provider`
  abstraction (`gemini` | `moss`). Do **not** vendor the model into ASA;
  run it as a service ASA calls. Hold Phase 1 as ground truth — MOSS output
  must cite measurements, never override them (the existing Phase-2 rule).
- **Cross-check oracle:** the existing **Gemini** Phase-2 output — compare
  citation discipline and where each is stronger; and ASA's own Phase-1 JSON
  as the factual backstop both must agree with.
- **Definition of done:**
  - [ ] Code + weight licences confirmed; self-host + derivative use
        explicitly permitted
  - [ ] `Phase2Provider` abstraction with `gemini` + `moss`, same
        recommendation schema (every rec cites measurement(s))
  - [ ] Eval: structure/chord/key reasoning + citation accuracy, MOSS vs
        Gemini, on a fixed set; documented "good enough offline / Gemini
        still wins" split
  - [ ] Runs flag-gated; a run completes without Phase 2 (unchanged)
- **Risks:** model-weight licences for audio LLMs are frequently
  research-only / non-commercial — this can kill the track regardless of
  code licence; serving an 8B model is real infra; hallucination control is
  the whole game (must cite, never invent).

## Reference-only (no fork)

- **M-Igashi/headroom** (Rust, ~28★, Jan 2026; licence TBD) — LUFS /
  true-peak + true-peak-ceiling gain. ASA already measures EBU R128 and
  **analyses, doesn't modify** audio, so gain is out of scope. At most: a
  *reference* for true-peak-ceiling logic ASA's mastering recommendations
  could cite. No code lift planned.
- **BinWang28/audio-ai-hub** (~930★) — a curated list, not code. Use as the
  scouting surface for the Part-A2 roadmap (next MOSS-class models /
  benchmarks). Not a fork.

---

# Part B — `asa-ableton`: the companion program (build-off / Live 12 extension)

A **new repo**, a thin client of ASA's API. It closes the loop from "ASA
recommends" → "it's actually set up in Ableton." Two modes, deliberately
separable:

- **Live mode** — a Control-Surface / Live extension that reads ASA's
  recommendations and nudges devices/parameters in a running Live set.
- **Export mode** — writes a starter `.als` (device chain / project) you
  open, for offline use.

ASA stays a clean analysis service; the Ableton-specific, reverse-
engineered, version-fragile code is quarantined here.

**The API seam (do this first, it gates both modes):** freeze a versioned
`recommendations` contract on ASA's side — each entry `{device, parameter,
value, unit, range, cited_measurements[]}`. `asa-ableton` consumes only that.
This is the same adopt/adapt/reject schema discipline as Track 2 of
`asa-2026-05-13.md`, applied to ASA's *output* rather than a third-party's.

## Track B1: AbletonLive12_MIDIRemoteScripts → Live-mode reference

- **Source:** https://github.com/gluon/AbletonLive12_MIDIRemoteScripts —
  Python, ~150★, created Apr 2024; unofficial collection of Live 12.4
  remote scripts + a Live Object Model docs site (Live 9–12). Licence:
  **effectively none — decompiled proprietary Ableton code. Treat as
  read-only; redistribution/vendoring is NOT permitted.**
- **What to lift:** **knowledge, not code** — real device names, parameter
  names/ranges, and the Control-Surface framework patterns (how a script
  binds to the Live API, listens, and sets parameters). The LOM docs site is
  the durable artefact.
- **Why:** ASA names Live 12 devices/parameters/values; B1 is how
  `asa-ableton` maps those names onto the actual Live API surface so it can
  *apply* them. Without a ground-truth name/range map, the recommendations
  can't be actuated.
- **Approach:** **reference-only.** Build the extension against Ableton's
  **official** surface — the Control Surface remote-script API and/or the
  Live 12 "Extensions" SDK (cf. `federico-pepe/ableton-live-extensions`,
  `Ableton/ableton.github.io`) — using this repo as a crib for names and
  patterns. Do **not** fork or ship its files. Capture the device/parameter
  name→range map you derive as your own data file.
- **Cross-check oracle:** the **official** Live API docs / Extensions SDK —
  any name/range you take from the decompiled scripts must verify against
  the official API before you depend on it.
- **Definition of done:**
  - [ ] Confirmed: no Ableton code is copied/redistributed into
        `asa-ableton` (legal risk closed)
  - [ ] Own device/parameter name→range map, verified against the official
        API, covering the devices ASA recommends
  - [ ] Minimal Live extension that sets one device parameter from a mocked
        ASA recommendation, end to end
  - [ ] Version-pinned to Live 12.x with a documented "breaks across Live
        versions" warning
- **Risks:** **highest in this doc.** Decompiled proprietary code →
  redistribution is off the table; remote scripts are unofficial and break
  across Live releases; Ableton's official extensibility is limited, so some
  recommendations may be un-actuatable and have to degrade to "instructions"
  rather than applied changes.

## Track B2: logic2ableton → Export-mode (.als writer) base

- **Source:** https://github.com/Evilander/logic2ableton — Python (~82%) +
  TS, ~35★, created Feb 2026, PyPI, v2.0.3. Licence: **TBD (confirm first).**
- **What to lift:** its **`.als` writing** code path — how it constructs a
  valid Ableton set (tracks, tempo, time signatures, devices) and its VST3
  plugin-suggestion reporting. The Logic-reading half is irrelevant; the
  Ableton-*emitting* half is the asset.
- **Why:** Export mode needs to turn an ASA analysis + recommendations into
  an openable `.als` (a starter device chain / project). logic2ableton is a
  working, recent precedent for generating valid `.als` — far cheaper than
  reverse-engineering the format from scratch.
- **Approach:** **fork-or-port the `.als` writer** (stack-compatible — it's
  Python, like ASA's worker). If the licence permits, fork the writer module
  into `asa-ableton`; otherwise port the `.als`-construction logic. Map
  ASA's `{device, parameter, value}` entries onto the device representation
  it already emits.
- **Cross-check oracle:** **round-trip in Ableton** — every generated `.als`
  must open in Live 12 without repair, with parameters reading back at the
  recommended values; and Track B1's name→range map as the parameter source
  of truth (the two B-tracks share it).
- **Definition of done:**
  - [ ] logic2ableton licence confirmed; fork-vs-port decided on that basis
  - [ ] `.als` generated from a sample ASA analysis opens cleanly in Live 12
  - [ ] ≥3 recommended device params verified reading back correctly in Live
  - [ ] Export mode runs headless (no Ableton required to *generate*)
- **Risks:** the `.als` format is undocumented and version-sensitive —
  generation may lag Live updates; small-author repo, so maturity/maintenance
  risk; licence may force a port rather than a fork.

---

## Sequencing

No required order. Recommended pickup priority by ROI:

1. **API seam (Part B intro)** — cheapest, gates both B tracks; freeze ASA's
   `recommendations` schema first.
2. **Track A1 (MSST stems)** — well-defined, testable, user-visible quality
   win, fully inside ASA.
3. **Track B2 (`.als` export)** — actuates recommendations with the *lowest*
   legal/version risk (file generation, no live Ableton, no decompiled code).
   The pragmatic first "Ableton extension type thing."
4. **Track A2 (MOSS Phase-2)** — high value but gated on weight-licence +
   infra; do the licence check before any build.
5. **Track B1 (live extension)** — highest reward, highest risk; only after
   B2 proves the name→range map and the API seam in a safe context.

## Source

Per-repo blurbs, ★, language, dates, and scores live in
`discoveries/audio-mir-2026-06-03.md` (PR #28). Treat that as the source of
truth for "what each upstream does"; this doc condenses and plans, it does
not re-describe. ASA's architecture here follows `routines/audio-mir.md` —
verify against ASA's own `CLAUDE.md`, which is authoritative and out of this
repo's scope.

## Scope

Plan only — no implementation. The deliverable is this document, as
`asa-2026-05-13.md` is a plan, not an implementation.
</content>
