# mac-gaming sweep — 2026-08-15 (first run)

Raw vetting record. Consolidated picks are in `../FINDS.md`; this file is why-dropped detail for
everything seriously looked at. Rig: M3 Pro MacBook 18GB, internal 14" + external 4K + external
144Hz QHD, CrossOver (Elden Ring, planned modded Skyrim SE via portable MO2), Xbox Series pad
wired+Bluetooth, Parallels Windows-ARM VM, custom raw-HID+Metal HUD latency tool already in use.

## Shortlisted → see FINDS.md
`3Shain/dxmt`, `Sikarugir-App/Sikarugir` (+ `frankea/Whisky` as an alternative bottle manager),
`vladkens/macmon`, `metaspartan/mactop`, `waydabber/BetterDisplay` (flagged not actually
open-source).

## Compatibility layers / bottle managers / mod tooling
- `Whisky-App/Whisky` — **archived, dead** (Apr 2025). Maintainer stopped rather than free-ride on
  CrossOver's funded Wine work. Don't recommend the original.
- `frankea/Whisky` — active fork, real continuation, commits/issues through 2026-08-12–14. Listed
  as an alternative to Sikarugir in FINDS.md.
- `Kegworks-App/Kegworks` → renamed `Sikarugir-App/Sikarugir` (Oct 2025 rename, GitHub redirects).
  Shortlisted.
- `MythicApp/Mythic` — 1.4k★ but last code commit ~2026-02-12 (6 months stale), thin/WIP
  Winetricks-arbitrary-app support, name collides with an unrelated red-team C2 tool
  (`its-a-feature/Mythic`). Watch-list only, not shortlisted.
- `MythicApp/Engine` — archived, superseded by `MythicApp/wine` (3★, unadopted). Dropped.
- `doitsujin/dxvk` — 17.8k★, healthy, but Linux/Proton-scoped, no macOS mention. Not directly
  usable; enters this space only via MoltenVK/Gcenx's old port.
- `Gcenx/DXVK-macOS` — 293★, last release 2023-07-23. Superseded by DXMT + D3DMetal/GPTK. Dropped
  as abandoned.
- `KhronosGroup/MoltenVK` — 5.8k★, healthy (v1.4.2-rc1, 2026-07-19), but infrastructure other tools
  build on, not a standalone user tool. Name-checked in FINDS.md, not a separate slot.
- `utmapp/d3dmetal-native` — 12★, niche reimplementation confirming D3DMetal ships x86_64-only
  (Rosetta even on Apple Silicon). Reference point, not a recommendation.
- `ModOrganizer2/modorganizer` — Windows-only; USVFS-under-Wine tracked in open issue #372 (open
  since 2018-05-19, still open). This is the actual blocker for the planned Skyrim SE MO2 setup —
  called out plainly in FINDS.md's "nothing good here" section.
- `limo-app/limo` — 767★, real activity, good native Bethesda-focused mod manager — but Linux-only,
  no macOS support. Dropped for this user, cited as "what a good native alternative looks like."
- `qsniyg/winevfs`, `theodorechapman/win32mac` — Linux-only / 1★-3-commits proof-of-concept
  (Fallout New Vegas only). Not maintained, not general-purpose. Dropped.
- `socram8888/SKSE64LoaderDLL` — generic Windows SKSE loader alternative, not Mac-specific. Not
  shortlisted.
- "Mortar" (named in the routine's own territory list) — **could not find it under any phrasing.**
  Treated as unverified/possibly non-existent rather than guessed at.

## Measurement: frame timing, Metal HUD, power/thermal, controller latency, display
- No PresentMon-equivalent exists for macOS (no ETW analogue). Stated plainly in FINDS.md.
- `timkurvers/metalhud` (8★), `Trsvsr/MetalHUDEnabler` (62★, CrossOver-bottle-aware) — toggle-only,
  no logging/parsing. `N2M0/Metal-HUD-Parse` — 0★, reads as a personal script. None shortlisted.
- `tlkh/asitop` — 4.6k★ but dead since 2023-01-24, Monterey-only per its own README. High star count
  is a trap; explicitly called out as such in FINDS.md.
- `SuperKenVery/asitop`, `kianwoon/asitop` — revival forks, no independent evidence of currency
  found. Not shortlisted.
- `op06072/NeoAsitop` — 100★, sudoless, but only tested through M1 Ultra per its own docs. Weaker
  than macmon/mactop.
- `FluidInference/fluidtop` — 66★, 112 commits, real asitop-replacement effort, M1–M4 claimed but no
  M5 mention yet, much smaller community than macmon/mactop. Not shortlisted, worth a re-check next
  sweep.
- `exelban/stats` — 41.2k★, the most popular general macOS menu-bar monitor, actively released, but
  historically utilization-% not true wattage (2025 feature request had to ask for power metrics) —
  noted as a caveat in FINDS.md rather than a straight recommendation.
- `pqrs-org/osx-hid-inspector` — 36★, genuinely active (commits within days), but descriptor/property
  inspection only, no timing capture. Not a latency tool. Not shortlisted (not what's needed here).
- `pqrs-org/Karabiner-Elements` — 22.6k★, dominant remapper, actively maintained (macOS 26 Tahoe
  support) — relevant as "the" remapper if remapping is ever needed, not a measurement tool. Not
  shortlisted (out of scope for this sweep's need).
- `cakama3a/Polling`, `WyvernIXTL/gamepadla-plus`, `mrb0y/Gamepadla` — measure analog-stick jitter
  interval, not press-to-frame latency; explicitly caveated by their own authors as "a guide, not an
  exact measurement." Confirmed nothing here rivals the user's own tool.
- `teamfinalmouse/xlat`, `stenyak/inputLagTimer`, `maziac/lagmeter`, `gromeck/LatencyMeasure`,
  `t0msk/InputLagTester` — hardware-firmware or camera/photodiode-based, not macOS-HID-native, no
  Metal HUD pairing. Different technique entirely. Dropped.
- `rhunecke/HIDTester` — 19★, confirms Apple Silicon, but a visual diagnostic (axis/deadzone), not a
  latency benchmark. Dropped.
- `xsyetopz/OpenJoystickDriver`, SDL2 tester repos (`mikyll`, `dkosmari`, `General-Arcade`) —
  mapping/visualization only, no latency measurement. Dropped.
- `360Controller/360Controller` — 6.7k★ but explicitly no Apple Silicon/Big Sur+ support per its own
  README (Dec 2020). Confirmed dead for this hardware; also confirms the actual current answer
  (Bluetooth Xbox controllers post-Aug-2016 are natively supported by macOS, no driver needed).
- `waydabber/BetterDisplay` — 33.2k★, de facto standard, shortlisted with an explicit "not actually
  open source" flag (repo hosts docs/releases/paid-upsell only, no app source visible).
- `huberdf/FreeDisplay` — 85★, genuinely open, but no refresh-rate/VRR row in its own feature table.
  Not a substitute for BetterDisplay on the axis that matters here.
- `aquitaine/OpenDisplay` — 8★, GPL-3.0, pre-1.0, explicitly targets Apple Silicon, no confirmed VRR
  yet. Worth a re-check next sweep, not shortlisted now.
- `MonitorControl/MonitorControl` — DDC brightness/volume only, no refresh-rate/VRR capability at
  all. Not relevant to the actual need. Dropped.

## Rosetta 2 / Parallels
- `Lifeisawful/rosettax87_jit` — active (commits through 2026-08-07), real x87/AVX patching for old
  DX9 titles (WoW-era), not relevant to Elden Ring/Skyrim SE (DX11/12). Noted, not shortlisted.
- `Lifeisawful/rosettax87` (archived), `WineAndAqua/rosettax87` (dead link, 404) — dead ends,
  flagged so they're not chased again.
- `Gcenx/winerosetta` — established, maintained by a credible name (Gcenx), same DX9/WoW niche.
  Noted, not shortlisted (not relevant to current games).
- `espetro/wowplay` — brand new (2026-06), 0★, own README admits crashes/WIP. Watch-list only.
- `FFRI/ProjectChampollion` — archived RE research on Rosetta internals, no gaming tooling. Not a
  tool, background reading only.
- `diewland/py-rosetta2-vs-arm` — 1★, dormant since ~2020. Dropped.
- Parallels org repos (`prlctl-scripts`, `vagrant-parallels`, `parallels-vscode-extension`,
  `packer-examples`) — real, maintained, but CI/dev-provisioning, zero gaming relevance. Dropped.
- `rbourgeat/mac-m1-game-list` — the one project that directly matched "Parallels as gaming
  fallback" framing, but archived 2026-01-12, stale. Not shortlisted; noted as a dead pointer.
- `pkoistin/prlkey`, `atahan99/simple-parallels`, `JulyIghor/prltype`, `Starefossen/prlctl-usb` —
  tiny/unproven prlctl wrappers (0–4★), none gaming-framed, none with real adoption. Dropped.
- GPU passthrough tooling: **not a possible category on Apple Silicon** — no PCIe passthrough
  exists at all; Parallels ARM VMs use Apple's own closed paravirtualized graphics. Stated plainly.
- Several "Parallels Desktop 2026 free/cracked" repos surfaced in search — spam/piracy, explicitly
  excluded, not linked.

## Other
- `Alia-Traces/MetalBench`, `philipturner/metal-benchmarks` — GPU microarchitecture benchmarking,
  not per-frame game timing capture. Not relevant to the frame-pacing gap. Dropped.
