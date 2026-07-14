# ASA incorporation plan — Extensions SDK (2026-07-01)

Drawn from `discoveries/audio-mir-2026-07-01.md`'s headline finding. That sweep left
one explicit open question unresolved — this doc resolves it via WebFetch/WebSearch
research (no GitHub MCP access outside this repo) and updates `asa-ableton-2026-06-03.md`'s
Part B plan accordingly.

> **ASA is a server-side Python/FastAPI app that *emits* Ableton Live 12
> device/parameter/value recommendations as JSON — it does not touch
> Ableton.** (Per `routines/audio-mir.md`; treat ASA's own `CLAUDE.md` as
> authoritative if it disagrees.)

> **Blocker under test**, from `incorporations/asa-2026-05-13.md`, "Out of scope":
> "Desktop shell (`rzru/nightingale`) — template only; no action until ASA goes
> desktop."

Licence convention (as in `asa-2026-05-13.md` / `asa-ableton-2026-06-03.md`): every
upstream's licence — including the Extensions SDK's own public-beta terms of use, not
just the two MCP repos below — is **unconfirmed** until verified; confirming it is
step one of every Definition of done.

## Ground-truth update (this session)

Re-fetched ASA's own `CLAUDE.md`, `CHANGELOG.md`, and `docs/ASA_ABLETON_BOUNDARY.md`
(`slittycode/ableton-sonic-analyzer`, `main` branch) to check for drift since the
07-01 sweep and to answer that sweep's other open question ("not yet confirmed
whether ASA's own team has looked at this"). Two findings:

1. **`asa-ableton` already exists as a real sibling repo**, not just a planned
   companion. Quoted from ASA's `CLAUDE.md`: *"the sibling asa-ableton repo (turns
   ASA recommendations into an openable Live 12 .als starter set)"*, handed off via a
   `phase2-export.v1` envelope (documented in `docs/ASA_ABLETON_BOUNDARY.md`) whose
   `phase2` field carries "the frozen `recommendations.v1` contract." This is
   materially the same shape as the API seam `asa-ableton-2026-06-03.md` proposed
   (`{device, parameter, value, unit, range, cited_measurements[]}`) — it's since been
   built, independent of this incorporation doc. **Track B2 (export-mode `.als`
   writer) is therefore functionally superseded — done, not by `logic2ableton`, but
   by `asa-ableton` itself.** `asa-ableton` is described as "stdlib-only Python,"
   file-coupled to ASA (no runtime dependency between the two).
2. **No awareness of the Extensions SDK found anywhere** in ASA's `CLAUDE.md`,
   `CHANGELOG.md`, or the boundary doc — no mention of "Extensions SDK",
   `@ableton-extensions`, `.ablx`, or any capability beyond the static `.als` export.
   `CHANGELOG.md` does reference the `gluon/AbletonLive12_MIDIRemoteScripts` catalogue
   for Live 12 device/parameter names — i.e. `asa-ableton` already took the
   decompiled-scripts route Track B1 named as its crib, for the export path. As of
   this fetch, ASA's team has not adopted or apparently evaluated the Extensions SDK.
   (`slittycode/asa-ableton` itself 404s publicly — private or not yet public — so
   this couldn't be checked directly against its own source.)

## Part A — Verdict: does the write surface reach device-parameter resolution?

**Yes — confirmed, with one evidentiary caveat (now explained, see follow-up below).**
Ableton's own primary sources (`ableton.github.io/extensions-sdk`,
`ableton.com/en/blog/introducing-extensions-sdk`, `soundonsound.com`'s coverage,
`npmjs.com`, `help.ableton.com`) all returned **HTTP 403** to this session's WebFetch
tool and could not be directly quoted — likely anti-bot protection, not evidence of
anything about the SDK itself. The verdict below rests on three independent,
directly-fetched secondary/derived sources instead, which converge:

1. **`Ronvaknins/ableton-extensions-skill`** (a public GitHub repo teaching AI coding
   agents to build Extensions, built against "SDK 1.0.0-beta.0 (API version 1.0.0)"),
   `reference/api.md` — its author states this reference is "distilled from" and
   "verified against the actual SDK type definitions" bundled in the SDK release.
   Quoted directly: `Device` has `parameters: DeviceParameter[]`; `DeviceParameter`
   exposes **async `getValue()` / `setValue(v)`** methods — the rest of its fields
   (`name`, `min`, `max`, `defaultValue`, `isQuantized`, `valueItems`) are read-only.
   This is the load-bearing citation: a named, typed, writable device-parameter
   method in the SDK's own object model.
2. **`jasper-zheng/ableton-sdk-mcp`** — its 7 MCP tools are read-oriented
   (`ableton_get_context`, `ableton_get_track`, `ableton_get_device`, etc.), but it
   also exposes `ableton_run_code`: *"Execute JS/TS against the Extensions SDK inside
   Live"* — general code execution against the real SDK, which would reach
   `DeviceParameter.setValue()` even though no tool is individually named for it.
3. **`pnomolos/live-wire`** — its capability table states directly: *"Tweak devices:
   get/set any device parameter by name."* This is the strongest single piece of
   evidence: a shipped, working bridge doing exactly the write ASA would need.

**One nuance, not a contradiction:** `live-wire`'s actual write path routes through a
**Max for Live proxy device** (a `.amxd` on a MIDI track) talking to the classic
LiveAPI/Live Object Model, rather than calling the Extensions SDK's own
`DeviceParameter.setValue()` directly (per its documented architecture: `AI Client ↔
LiveWire Extension (Extension Host) ↕ WebSocket ↔ LiveWire Proxy (.amxd) ↕ LiveAPI ↔
Live`). This could mean the direct-SDK write path had gaps at build time, or — more
likely, given source (1) documents `setValue` explicitly — it's simply the author's
choice to reuse the mature, full-featured M4L/LOM surface rather than the month-old
beta SDK for that specific operation. Either way it doesn't undermine the verdict;
it's a second, independent architecture that *also* reaches device parameters, just
via a different route. Also worth noting: the distilled API reference makes **no
mention of automation envelopes** — only discrete get/set, not time-varying automation
writes. ASA's recommendations are single target values per parameter (not automation
curves), so this limitation likely doesn't block ASA's use case, but it bounds what
"write access" means here.

**On the blocker, precisely:** what this confirms is that a **host process to act on
Live no longer needs to be a separate desktop shell** — Extensions run inside Live
itself, launched via right-click, no external app to install or keep running. That is
narrower than "the blocker is resolved": `asa-2026-05-13.md`'s bullet is about ASA
itself needing to go desktop, and ASA remains — correctly — a server-side analysis
service with no reason to become one. What changes is that `asa-ableton`'s **Live
mode** (the harder half of Track B, previously blocked on exactly this "no legitimate
host" problem) now has a real, official host: an Extension, not a desktop shell.

### Primary-source follow-up (2026-07-02)

Re-attempted all five blocked URLs directly — still 403 across the board. Tried the
Wayback Machine (unavailable in this environment entirely, not just for these URLs)
and searched for a public GitHub source repo behind `ableton.github.io/extensions-sdk`.
That search resolved the mystery rather than the citation gap: the site is served from
`ableton/ableton.github.io` (a public repo), and its `extensions-sdk/index.md` **is**
directly fetchable via `raw.githubusercontent.com` — and confirms, in Ableton's own
words, that the API reference itself is not public. Quoted from that file: *"The
Extensions SDK is available exclusively in the Live 12.4.5 public beta. It does not
work with any earlier version of Live."* Getting the actual SDK and its documentation
requires three steps stated on that page: join the Ableton Beta Program via
**Centercode**, install Live Beta 12.4.5b3, and **obtain the Extensions SDK along with
its documentation from Centercode** — i.e. the TypeDoc API reference this doc's Part A
wanted to cite directly is gated behind Ableton's beta-program portal, not hosted
anywhere publicly crawlable. The 403s on the blog/press/npm/FAQ pages are most likely
unrelated anti-bot blocking (those aren't beta-gated content), but the one page that
would have settled Part A definitively — the API reference — simply isn't public.

This doesn't change the verdict: it explains, rather than resolves, the evidentiary
gap. The three converging secondary sources in Part A (a third-party reference
explicitly distilled from the SDK's real bundled type definitions, plus two working
community bridges built against the beta SDK, one of which ships live device-parameter
read/write) are very likely the practical ceiling of what's independently verifiable
without joining Ableton's beta program directly. Treat Part A's verdict as
well-corroborated but not primary-source-confirmed, and re-verify against the actual
TypeDoc reference if/when beta access is obtained — don't treat this follow-up as
having closed that gap, only as having explained why it can't be closed from outside
the beta program.

## Part B — Track E1: Ableton Extensions SDK → close the advice-to-applied-change loop

- **Source:** `Ronvaknins/ableton-extensions-skill` (distilled API reference, SDK
  1.0.0-beta.0 / API 1.0.0) · `jasper-zheng/ableton-sdk-mcp` (TypeScript, ~15★) ·
  `pnomolos/live-wire` (JavaScript, ~5★) — all as **architecture references**, not
  code to fork. Primary docs (`ableton.github.io/extensions-sdk`,
  `ableton.com/en/blog/introducing-extensions-sdk`) exist and were cited by the 07-01
  sweep but could not be directly re-verified this session (403s); re-check them
  directly before building, don't rely solely on this doc's secondary sources.
- **What to lift:** the `Device` → `DeviceParameter[]` → `getValue()`/`setValue(v)`
  object-model pattern and the `.ablx` right-click-launch packaging model. Not any
  bridge's code — `ableton-sdk-mcp` and `live-wire` are both read as design
  references (one direct-SDK, one M4L-proxied) for how `asa-ableton`'s own Live-mode
  extension might be structured, particularly the tradeoff between calling
  `DeviceParameter.setValue()` directly vs. proxying through M4L/LOM.
- **Why:** this is the official, Ableton-sanctioned surface Track B1 was written
  *before knowing existed* — it replaces B1's harder path (decompiled Remote Scripts
  as the only crib, "redistribution/vendoring is NOT permitted," "breaks across Live
  versions") with a supported API that Ableton itself maintains. It also gives
  `asa-ableton`'s already-built export-mode work (see Ground-truth update above) a
  natural next mode: apply-in-place, not just generate-a-file.
- **Approach:** **build a minimal Extension in `asa-ableton` as a third consumer of
  its existing `recommendations.v1` contract** (alongside the `.als` exporter),
  reading the same `phase2-export.v1` envelope ASA already emits. Do not touch ASA
  itself — the boundary stays file-coupled per `docs/ASA_ABLETON_BOUNDARY.md`. Map
  each recommendation's `{device, parameter, value}` onto `Device.parameters[]` by
  name, call `setValue(v)`. Keep the decompiled-scripts device/parameter name→range
  map Track B1 already produced (per the Ground-truth update, `asa-ableton`'s
  CHANGELOG already references `gluon/AbletonLive12_MIDIRemoteScripts` for this) as
  the name/range cross-check — the SDK's own `Device`/`DeviceParameter` objects
  should confirm the same names live, closing the loop Track B1 flagged as its
  biggest risk (no ground-truth map without decompiled code).
- **Cross-check oracle:** the Extensions SDK's own bundled TypeDoc API reference
  (inside the SDK release, referenced but not directly fetched this session) — now
  the **primary** oracle, ahead of the decompiled Remote Scripts, which drop to a
  secondary/legacy cross-check now that an official surface exists.
- **Definition of done:**
  - [ ] Extensions SDK public-beta terms of use confirmed to permit this use
        (redistribution of a built `.ablx`, any usage-data implications)
  - [ ] Minimal Extension sets one real device parameter from a mocked
        `recommendations.v1` entry, end-to-end, in a running Live 12 Suite session
  - [ ] Device/parameter names resolved via the SDK's own object model cross-checked
        against `asa-ableton`'s existing decompiled-scripts name→range map — any
        mismatch investigated before trusting either source alone
  - [ ] `incorporations/asa-2026-05-13.md`'s blocker bullet annotated (not rewritten)
        to point at this doc — tracked separately, see below
- **Risks:** **public beta** — API can change before GA; version-pin the beta/Live
  release this is built against. **Licence/redistribution** — "free SDK" is not the
  same as unrestricted redistribution or commercial-use rights for a shipped `.ablx`;
  confirm the beta ToS before shipping anything, same discipline as every other
  upstream in this repo. **Platform gating** — Extensions require **Live 12 Suite**
  specifically (per the 07-01 sweep and corroborated by `live-wire`'s Suite-oriented
  framing); ASA users on Standard/Intro can't run an Extension-based apply path, so
  the `.als`-export mode `asa-ableton` already has remains the only path for them —
  keep both modes, don't retire export-mode. **Evidentiary caveat** — this verdict
  rests on secondary sources; a 2026-07-02 follow-up confirmed the actual API
  reference is gated behind Ableton's Centercode beta program, not publicly
  accessible (see "Primary-source follow-up" above) — re-verify against it directly
  once beta access is available, before writing real code.

## Reconciliation note

`asa-ableton-2026-06-03.md`'s Track B1 (lines ~139–142) speculatively named "the Live
12 'Extensions' SDK" as one of two possible official surfaces, alongside
`federico-pepe/ableton-live-extensions` and `Ableton/ableton.github.io` as reference
crib repos — written before the SDK was known to be real. That speculation is now
**confirmed correct** on the surface question, and **superseded on the specifics**:
the SDK is real, public-beta, and does reach device-parameter writes (this doc's Part
A); the two crib repos it named are superseded by the actual SDK docs and the two
purpose-built MCP bridges found in the 07-01 sweep. Track B2 (the `logic2ableton`-based
`.als` writer) is separately superseded — not by this SDK finding, but by the
discovery (this session) that `asa-ableton` already ships an export-mode writer of its
own. Recommend (as a follow-up, not performed by this doc) adding a one-line dated
pointer at the top of `asa-ableton-2026-06-03.md` — e.g. "Update (2026-07-01): see
`asa-extensions-sdk-2026-07-01.md` — Extensions SDK confirmed real; asa-ableton export
mode already shipped independently" — rather than rewriting that historical doc's
substantive Track B1/B2 content.

## Sequencing

1. ~~Re-verify Part A's verdict directly against `ableton.github.io/extensions-sdk`'s
   official TypeDoc reference~~ — attempted 2026-07-02; the reference itself is
   Centercode-beta-gated, not publicly reachable by any means tried (direct fetch,
   Wayback Machine, source-repo search). **Actual next step:** join Ableton's Beta
   Program and re-verify against the real TypeDoc reference once access is obtained,
   before any build work starts — the secondary-source verdict above should not be
   treated as a substitute for the primary source once accessible.
2. Confirm the Extensions SDK public-beta licence/ToS — gates everything else, same
   as every other track in this repo.
3. Build the minimal one-parameter Extension (Definition of done, item 2) as the
   actual spike — this is the fastest way to convert "the docs say setValue exists"
   into "it works in a real Live 12 Suite session."
4. Only after (3) succeeds, wire it to `asa-ableton`'s real `recommendations.v1`
   output instead of a mock.
5. Annotate `asa-2026-05-13.md`'s blocker bullet (small, independent, can happen any
   time after Part A's verdict is trusted).

## Source

`discoveries/audio-mir-2026-07-01.md` is the source sweep for the SDK finding itself;
treat it as the source of truth for the "headline finding" framing and the two MCP
bridges' original scores. This doc's Ground-truth update section and Part A's verdict
are new research performed for this doc (WebFetch/WebSearch, dated 2026-07-01) and are
not re-descriptions of that sweep. ASA's architecture facts in the Ground-truth update
come directly from `slittycode/ableton-sonic-analyzer`'s own `CLAUDE.md` /
`CHANGELOG.md` / `docs/ASA_ABLETON_BOUNDARY.md` (`main` branch, fetched this session) —
treat ASA's own repo as authoritative if it has since drifted further.

## Scope

Plan only — no implementation. The deliverable is this document, as
`asa-2026-05-13.md` and `asa-ableton-2026-06-03.md` are plans, not implementations.
