# FINDS — mac-gaming

Running log for the **mac-gaming** stream: tools that help run, mod, measure, or tune games on an
Apple Silicon Mac (CrossOver/GPTK, mod tooling, frame/power/latency/display measurement, Rosetta,
Parallels). Consolidated shortlist only — raw per-sweep vetting notes (including ruled-out
candidates and why) live in `discoveries/mac-gaming-<date>.md`. Dedupe list:
`discoveries/_seen-mac-gaming.txt`. Licence ignored. Routine: `routines/mac-gaming.md`.

Rig this is scored against: M3 Pro MacBook 18GB, 14" internal + external 4K + external 144Hz QHD,
games via CrossOver (Elden Ring now, modded Skyrim SE via portable MO2 planned), Xbox Series pad
(wired + Bluetooth), Parallels Windows-ARM VM kept around, a custom raw-HID + Metal HUD input
latency tool already in daily use.

---

## 2026-08-15

### 1. DXMT — `3Shain/dxmt` [translation-layer] [d3d11] [active]
Metal-native Direct3D 11/10 (and growing D3D12) translation layer for Wine on macOS — the actual
"Metal descendant" in the DXVK lineage the routine's territory pointed at, not a fork of DXVK's
code but the same niche solved natively for Metal instead of via MoltenVK.
- **Used & maintained:** 1.1k★; 10 commits landed on 2026-08-13 alone (D3D12 indirect
  draw/dispatch work) — this is current, active engineering, not a snapshot. Tagged GitHub
  Releases stopped at v0.80 (2025-04-23, mid MIT→LGPL relicense toward v1.0), so it ships to users
  bundled inside bottle managers rather than via its own release page — a packaging gap, not an
  activity gap.
- **Apple Silicon:** confirmed and primary — per the project wiki, Apple Silicon (macOS 14+) is the
  *primary* supported target and Intel Mac support is explicitly still WIP, the reverse of most of
  this ecosystem. CodeWeavers' own CrossOver 26 changelog lists "DXMT 0.72" alongside D3DMetal
  3.0 — third-party validation from the commercial competitor/beneficiary of the work.
- **Do:** nothing to install directly — it arrives as a selectable per-bottle backend in Sikarugir
  or the frankea Whisky fork (below). Worth knowing it exists so you can pick it as an alternate
  D3D11 backend to try against D3DMetal if a specific game (Skyrim SE mods often touch D3D11 more
  than Elden Ring's DX12 path) runs better on one than the other.
- **Overlap with your latency tool:** none — pure graphics translation, no measurement surface.

### 2. Sikarugir — `Sikarugir-App/Sikarugir` [bottle-manager] [wine] [active]
GUI Wine-bottle manager (Wineskin → Kegworks → Sikarugir lineage) for wrapping individual Windows
apps/games, with WineD3D/VKD3D/D3DMetal/DXMT/DXVK all selectable per-wrapper.
- **Used & maintained:** 3.5k★, 150 commits, commits as recent as 2026-08-04. Maintained in part by
  Gcenx, who also maintains WineHQ's official macOS Wine builds (`Gcenx/macOS_Wine_builds`) and the
  Homebrew/MacPorts Wine taps — real standing in the upstream Wine-on-Mac community, not a random
  wrapper author. No tagged Releases (rolling `main` via Homebrew tap only) — a changelog-discipline
  gap worth noting, not a maintenance red flag.
- **Apple Silicon:** confirmed, macOS 14+ required — but the README itself notes parts of the stack
  still need Rosetta 2 on Apple Silicon, so "Apple Silicon support" here means "runs," not "runs
  fully native."
- **Do:** not a reason to leave CrossOver, which you're already using and which is the commercial
  upstream this whole ecosystem free-rides on. Worth a look specifically if you ever want to A/B a
  DXMT-backed bottle for Skyrim SE against CrossOver's D3DMetal path, or want a free bottle for a
  one-off non-game Windows app. Take-an-idea, not adopt.
- **Security note surfaced during research:** the repo warns `sikarugir.com` is a squatted,
  unaffiliated domain — GitHub + the official Homebrew tap are the only legitimate sources.
- **Related, ruled in/out:** the original `Whisky-App/Whisky` is **archived** (dead, April 2025) —
  its maintainer said continuing would free-ride on CrossOver's funded Wine work and told users to
  buy CrossOver. The active community fork, `frankea/Whisky` (401★, issues/commits as recent as
  2026-08-12–14), is the real continuation and bundles DXMT + DXVK-over-MoltenVK as backends — a
  reasonable alternative to Sikarugir if you want Whisky's specific UI, but don't use the archived
  original.

### 3. macmon — `vladkens/macmon` [power] [thermal] [active]
Sudoless Rust TUI (+ JSON/Prometheus export) reading the same private power/thermal API
`powermetrics` uses, without needing root.
- **Used & maintained:** 1.8k★; releases v0.8.0–v0.8.2 landed 2026-07-24 through 2026-08-04 — i.e.
  inside the last two weeks. README states explicit M1–M5 support.
- **Apple Silicon:** confirmed recently, not assumed — the M5 mention in the changelog means someone
  validated it against hardware that shipped this cycle, not years-old M1 testing.
- **Do:** use directly. This is the honest, current answer to "power/thermal logging for Apple
  Silicon" — replaces the instinct to reach for `asitop`, which is dead (see below).
- **Overlap with your latency tool:** none — thermal/power, not input timing. Complementary: pair
  macmon's power/thermal log with your latency numbers to see if thermal throttling during a long
  Skyrim session correlates with latency drift.

### 4. mactop — `metaspartan/mactop` [power] [thermal] [menubar] [active]
Go-based alternative to macmon: terminal TUI *and* a `--menubar` mode with live sparklines/gauges,
reading native IOReport/IOKit/SMC APIs directly (also sudoless) rather than the powermetrics-style
API macmon uses, and adding fan RPM readout/control.
- **Used & maintained:** 1.6k★, 599 commits; v2.1.3–v2.1.5 releases landed 2026-05-03 through
  2026-06-14, with changelog entries referencing ANE-bandwidth handling for the macOS 27 beta —
  i.e. actively tracking the current OS beta cycle, not just shipped-and-forgotten.
  Confirms M1 through M5/M5 Pro/Max support.
- **Apple Silicon:** confirmed recently (M5 line explicitly named in changelog).
- **Do:** use instead of macmon if you want an always-visible menu-bar HUD during play rather than a
  terminal you have to keep in view, or if you want fan control alongside monitoring. Functionally
  overlapping with macmon — pick one, they're not both needed.
- **Ruled out from this slot:** `tlkh/asitop` has 4.6k★ (more than both of the above combined) but
  is dead — last commit 2023-01-24, explicitly Monterey-only in its own README, 52 open issues,
  no activity since. High star count here is a trap, not a signal. `exelban/stats` (41.2k★) is the
  most popular macOS menu-bar monitor generally and is actively released, but historically showed
  utilization % rather than true powermetrics-grade wattage (a 2025 feature request had to ask for
  it) — verify current build before treating it as a macmon/mactop substitute; it's a fine
  general system monitor, not built around power data the way these two are.

### 5. BetterDisplay — `waydabber/BetterDisplay` [display] [vrr] [not-actually-open-source]
The de facto tool for macOS display control: refresh-rate menu, HiDPI scaling, VRR-range handling,
multi-display brightness/UI-scale sync — directly relevant to running the 4K panel and the 144Hz
QHD panel together off the M3 Pro.
- **Flag before anything else: this is not actually an open-source repo.** The GitHub repo hosts
  README/docs/DMG release links and a Pro-license upsell ($21.99), but no visible application
  source — it's a distribution and issue-tracker shell around a closed, partly-paid app. Including
  it because it's the honest answer to the display-control gap in this territory, not because it
  clears this routine's usual "read the source" bar.
- **Used & maintained:** 33.2k★, 630 forks, active release cadence (v5.0.x through mid-2025 in what
  I could verify, explicitly listing support through "macOS 27 Golden Gate / macOS 26 Tahoe").
- **Apple Silicon caveat found in its own maintainer discussion:** on Apple Silicon the display
  co-processor (not the OS) negotiates modes from EDID, so BetterDisplay's own maintainer
  recommends pinning your 144Hz panel to a supported flat refresh rate rather than fighting for a
  custom VRR range — relevant to how you actually configure the QHD panel, not just whether the
  tool runs.
- **Do:** use it — there's no genuinely open, equally capable alternative yet (`FreeDisplay` is real
  OSS but has no refresh-rate/VRR row at all in its own feature table; `OpenDisplay` is a promising
  GPL-3.0 clean-room alternative explicitly targeting Apple Silicon but pre-1.0, 8★, VRR support
  unconfirmed — worth a bookmark to revisit, not a recommendation yet).
- **Overlap with your latency tool:** none — display mode/HiDPI control, not input timing.

---

### Nothing good here — stated plainly, not padded

- **Frame timing / frame pacing capture (PresentMon-equivalent):** doesn't exist for macOS. ETW
  tracing has no macOS analogue, and I found no maintained project that captures per-frame present
  timestamps for arbitrary games. Everyone eyeballs Metal HUD (`MTL_HUD_ENABLED=1`) directly, or
  goes without. Genuine gap, not a "you missed it."
- **Metal HUD logging/parsing over time:** only toggle utilities exist (`timkurvers/metalhud`,
  `Trsvsr/MetalHUDEnabler` — the latter is CrossOver-bottle-aware, editing `cxbottle.conf` directly,
  mildly useful as a convenience toggle but does not log or parse the numbers). One project named
  for parsing (`N2M0/Metal-HUD-Parse`) has 0 stars and reads as a personal script, not a tool.
- **Mod-manager glue for MO2 under Wine/CrossOver:** nothing good exists. MO2's own USVFS doesn't
  work correctly under Wine — tracked in `ModOrganizer2/modorganizer#372`, open since 2018-05-19,
  still open. No Mac-native alternative has real adoption (`limo-app/limo` is a good native Linux
  mod manager with real activity but is Linux-only, no macOS support). Everyone just runs
  `MO2.exe`/Vortex inside the CrossOver bottle and lives with USVFS being occasionally flaky — worth
  knowing that going in on the "heavily modded Skyrim SE" plan, not a tooling gap you can currently
  buy your way out of.
- **SKSE / script-extender tooling for Wine specifically:** nothing dedicated exists, and nothing is
  needed — SKSE, Address Library, and CommonLibSSE are generic Windows infrastructure that just
  needs to run inside a correctly configured bottle (DXVK/DXMT + mSync per community guidance), same
  as on real Windows.
- **Parallels Windows-ARM VM gaming tooling:** nothing exists, and GPU passthrough isn't even a
  possible category on Apple Silicon (no PCIe passthrough at all — Parallels ARM VMs use Apple's own
  closed, paravirtualized Metal-backed graphics). The only OSS in the Parallels GitHub org
  (`prlctl-scripts`, `vagrant-parallels`, the VS Code extension) is CI/dev-provisioning tooling with
  zero gaming relevance. Confirms the general consensus that CrossOver beats Parallels for FPS/
  latency on supported titles, but nobody has built anything to quantify that — if you want the VM
  as a gaming fallback, that stays a manual comparison.
- **Controller HID timing / input latency:** nothing rivals your own raw-HID + Metal HUD tool, and
  nothing is close. The closest GitHub projects (`cakama3a/Polling`, `WyvernIXTL/gamepadla-plus`)
  measure the interval between successive analog-stick position changes while you move the stick in
  a circle — a synthetic proxy for controller responsiveness, not true button-press-to-frame
  latency, and the authors themselves caveat it as "a guide, not an exact measurement." Nothing
  found pairs `IOHIDValueGetTimeStamp`-class kernel timestamps with a rendering-side ground truth the
  way your tool does. Keep it; don't drop it for anything here.
- **Rosetta 2 tuning:** a real, narrow, currently-active niche exists (`Lifeisawful/rosettax87_jit`,
  commits as recent as 2026-08-07; `Gcenx/winerosetta`) but it's specifically x87/AVX instruction
  patching for old DirectX 9 titles (World of Warcraft-era games) crashing under Rosetta, not
  general Rosetta benchmarking or tuning. Elden Ring and Skyrim SE are both DX11/12-era, so this
  isn't currently relevant to you — worth remembering if you ever run something DX9-vintage through
  GPTK. D3DMetal itself is worth a footnote here too: it's Apple's proprietary component (not an
  independent GitHub project) and per `utmapp/d3dmetal-native`'s README it ships **x86_64-only**,
  meaning even on Apple Silicon it runs under Rosetta 2, not natively — a genuine architectural
  wrinkle in the "best" D3D backend, not a tooling gap.

---

## 2026-08-16

One day on from an unusually thorough first sweep, most of the territory is saturated — this round
targeted the one gap 2026-08-15 left open (MO2/Skyrim-on-Mac specifics) plus a light recheck of the
rest. Full vetting notes, including two installer GUIs ruled out as thin/stale, in
`discoveries/mac-gaming-2026-08-16.md`.

### 1. Anna Plays Skyrim's macOS modding guide — `skyrim.annathepiper.org/wiki/...` [not-a-repo] [skyrim] [canonical-guide]
Personal wiki, not a GitHub repo — flagged as such — but it's the closest thing to a canonical
answer to the exact question your "portable MO2" plan depends on.
- **What it says, load-bearing for your plan:** on Apple Silicon, **MO2 runs in CrossOver but not in
  a Parallels Windows-ARM VM; Vortex is the reverse** (works in the VM, not in CrossOver). That's not
  "CrossOver is better," it's "CrossOver is the only combination that works at all" — validates your
  portable-MO2-via-CrossOver plan over the alternative of using the Parallels VM you already keep
  around. Also notes Parallels throttles VM RAM to 8GB unless you're on the yearly (not one-time)
  licence tier, relevant only if you reconsider the VM route for a big load order.
  - **Wabbajack caveat:** the Wabbajack *installer app* itself doesn't run cleanly in CrossOver
    (Nexus login breaks on a Webview dependency) — so if you use a Wabbajack-built modlist, expect to
    generate/update it elsewhere and run the resulting portable-MO2 output inside CrossOver, not run
    Wabbajack itself in the bottle.
- **Confidence caveat:** `skyrim.annathepiper.org` was blocked by this session's egress proxy on
  direct fetch, so this is reconstructed from search snippets, not a full read — treat as one
  well-informed source pending a direct re-check, not fully confirmed.
- **Do:** read it before you start the Skyrim SE modding project — it directly shapes which tool
  (CrossOver vs. the Parallels VM) you point MO2 at.
- **Overlap with your latency tool:** none.

### 2. Tuxborn — `Omni-guides/Tuxborn` [modlist] [wabbajack] [skyrim] [active]
A Wabbajack-format Skyrim SE modlist tuned for Steam Deck / lower-spec-PC performance (Legacy of the
Dragonborn, BFCO combat overhaul, NPC/quest content) — a config repo, not executable tooling, counted
because it's a real answer in the gap 2026-08-15 flagged as unsolved.
- **Used & maintained:** 99★, 262 commits, commits as recent as 2026-07-15.
- **Apple Silicon:** not claimed by the repo itself (it's Steam-Deck/Linux-framed), but the
  annathepiper guide above documents someone running it on a Mac specifically. A Steam-Deck-safe
  modlist is a reasonable proxy for Wine/CrossOver-safe, since both avoid the same class of
  Windows-only INI/driver hacks — reasoning, not a guarantee.
- **Correction (flagged in PR review, verified):** "survives the Mac path" overstated it — the
  annathepiper guide marks the Mac process **experimental**, and Tuxborn's bundled Community Shaders
  1.2.1 (vs. the current 1.3) breaks grass/sky rendering under CrossOver unless you disable it. A
  working install can reportedly be copied over from a Steam Deck and then only needs CrossOver to
  run — but "runs" still means "runs with a known graphics bug you have to work around," not a clean
  pass.
- **Do:** worth considering as a curated starting load order for the "heavily modded Skyrim SE" plan
  instead of building one from scratch — but go in expecting to disable Community Shaders (or accept
  broken grass/sky) as a known first fix, not a smooth out-of-the-box run. Take-an-idea / evaluate,
  not a blind adopt.
- **Overlap with your latency tool:** none.

### 3. Apple's `game-porting-toolkit` repo — correction, not what it was first filed as [not-the-toolkit] [background-infra]
**Correction (flagged in PR review, verified against the repo's own Overview):** the 2026-08-16
draft of this entry mischaracterized `apple/game-porting-toolkit` as the GPTK translation-layer
upstream. It isn't. The repo's own README says it contains AI **agent skills** (Metal 4/MetalFX/
shader-compilation domain modules for coding-assistant porting workflows), **Metal-cpp**, and code
samples — not the Wine-based toolkit itself. GPTK 4 (the actual evaluation environment /
Metal Shader Converter you'd need for translation work) is listed as a prerequisite you download
**separately** from `developer.apple.com/games/game-porting-toolkit/`, and that download isn't a
GitHub repo at all.
- **Corrected finding:** there is no GitHub upstream for GPTK itself to point to — the tool DXMT/
  Sikarugir/Whisky-family projects build config around isn't on GitHub; it's a direct Apple Developer
  download. Worth knowing as a "doesn't exist as a repo" fact in its own right, not a tool to use.
- **Do:** nothing — not a find, not a footnote worth installing. Left in `_seen-mac-gaming.txt` only
  so a future sweep doesn't re-surface and re-misidentify the same repo.
- **Ruled out alongside the original (mis)investigation, findings still stand:** `installaware/AGPT`,
  a once-popular free GUI installer wrapping the real GPTK download (542★), is **stale** — last
  commit 2025-01-06, 19+ months old against a fast-moving stack (D3DMetal/DXMT).
  `Porting-Kit-Wrapper-Suite` / `vitor251093/porting-kit-releases` ("Porting Kit") is exactly the
  thin-Wineskin-wrapper pattern this routine is skeptical of by default — 16★, reads as a releases
  dump with no clear link to maintained source. Neither recommended over CrossOver.
- **Overlap with your latency tool:** none.
