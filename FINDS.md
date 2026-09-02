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

## anaximan/tuxborn_111
link:      https://github.com/anaximan/tuxborn_111
surfaced:  2026-08-16
what:      A fork or mirror of the Tuxborn Skyrim SE modlist.
alive:     no independent activity signal found beyond the parent
why:       Not a separate find from Omni-guides/Tuxborn.
tags:      mac-gaming, skyrim, modlist, fork, redundant

## xsyetopz/OpenJoystickDriver
link:      https://github.com/xsyetopz/OpenJoystickDriver
surfaced:  2026-08-15
what:      Joystick driver / mapping utility.
alive:     commit/contributor/release detail unrecorded
why:       Mapping/visualization only, no latency measurement. Dropped.
tags:      mac-gaming, controller, driver, mapping, not-latency

## WyvernIXTL/gamepadla-plus
link:      https://github.com/WyvernIXTL/gamepadla-plus
surfaced:  2026-08-15
what:      Gamepad latency/polling measurement tool.
alive:     commit/contributor/release detail unrecorded
why:       Measures analog-stick jitter interval, not press-to-frame latency; explicitly caveated by its own authors as a guide rather than an exact measurement.
tags:      mac-gaming, controller, polling-rate, latency-proxy, not-a-substitute

## WineAndAqua/rosettax87
link:      https://github.com/WineAndAqua/rosettax87
surfaced:  2026-08-15
what:      Rosetta 2 x87 patching work.
alive:     dead link, 404
why:       A dead end, flagged so it isn't chased again.
tags:      mac-gaming, rosetta, 404, dead-end

## Whisky-App/Whisky
link:      https://github.com/Whisky-App/Whisky
surfaced:  2026-08-15
what:      The original native macOS Wine wrapper for running Windows games on Apple Silicon.
alive:     archived, dead since April 2025
why:       The maintainer stopped rather than free-ride on CrossOver's funded Wine work, and told users to buy CrossOver. Don't recommend the original — superseded by the active community fork frankea/Whisky.
tags:      mac-gaming, wine, archived, dead, superseded

## whisky-app/whisky
link:      https://github.com/whisky-app/whisky
surfaced:  2026-08-15
what:      The original Whisky macOS Wine wrapper, under its lowercase org path.
alive:     archived April 2025, no longer maintained
why:       Archived and superseded by frankea/Whisky. Recorded separately from `Whisky-App/Whisky` because both spellings were surfaced and logged during the sweeps; they are the same project.
tags:      mac-gaming, wine, archived, dead, superseded, duplicate-spelling

## waydabber/BetterDisplay
link:      https://github.com/waydabber/BetterDisplay
surfaced:  2026-08-15
what:      The de facto tool for macOS display control: refresh-rate menu, HiDPI scaling, VRR-range handling, multi-display brightness and UI-scale sync.
alive:     33.2k★, 630 forks, active release cadence (v5.0.x through mid-2025 as verified), explicitly listing support through "macOS 27 Golden Gate / macOS 26 Tahoe"
why:       Flag before anything else: this is **not actually an open-source repo**. The GitHub repo hosts README/docs/DMG release links and a Pro-license upsell ($21.99), but no visible application source — it's a distribution and issue-tracker shell around a closed, partly-paid app. Included because it's the honest answer to the display-control gap, not because it clears the routine's usual "read the source" bar. Directly relevant to running the 4K panel and the 144Hz QHD panel together off the M3 Pro. Apple Silicon caveat from its own maintainer discussion: the display co-processor (not the OS) negotiates modes from EDID, so the maintainer recommends pinning the 144Hz panel to a supported flat refresh rate rather than fighting for a custom VRR range. Use it — there's no genuinely open, equally capable alternative yet.
tags:      mac-gaming, display, vrr, refresh-rate, hidpi, not-open-source, closed-source

## vladkens/macmon
link:      https://github.com/vladkens/macmon
surfaced:  2026-08-15
what:      Sudoless Rust TUI (plus JSON/Prometheus export) reading the same private power/thermal API `powermetrics` uses, without needing root.
alive:     1.8k★; releases v0.8.0–v0.8.2 landed 2026-07-24 through 2026-08-04; README states explicit M1–M5 support
why:       Apple Silicon support confirmed recently, not assumed — the M5 mention in the changelog means someone validated it against hardware that shipped this cycle, not years-old M1 testing. Use directly: this is the honest, current answer to "power/thermal logging for Apple Silicon" and replaces the instinct to reach for asitop, which is dead. No overlap with the raw-HID latency tool, but complementary — pair macmon's power/thermal log with the latency numbers to see whether thermal throttling during a long Skyrim session correlates with latency drift.
tags:      mac-gaming, power, thermal, tui, rust, apple-silicon, monitoring, active

## vitor251093/porting-kit-releases
link:      https://github.com/vitor251093/porting-kit-releases
surfaced:  2026-08-15
what:      Releases repo for "Porting Kit", a Wineskin-based GUI wrapper suite with a large pre-made game/app catalog.
alive:     16★; reads as a single-commit releases dump with no visible link back to real source; activity/maintenance couldn't be established
why:       Ruled out as exactly the thin-wrapper pattern the routine warns about. Not pursued further, not recommended over CrossOver.
tags:      mac-gaming, gptk, wineskin, wrapper, thin, ruled-out

## utmapp/d3dmetal-native
link:      https://github.com/utmapp/d3dmetal-native
surfaced:  2026-08-15
what:      Niche reimplementation work around Apple's D3DMetal component.
alive:     12★
why:       Confirms D3DMetal ships x86_64-only, meaning even on Apple Silicon it runs under Rosetta 2 rather than natively — a genuine architectural wrinkle in the "best" D3D backend. A reference point, not a recommendation.
tags:      mac-gaming, d3dmetal, rosetta, reference, architecture-note

## Trsvsr/MetalHUDEnabler
link:      https://github.com/Trsvsr/MetalHUDEnabler
surfaced:  2026-08-15
what:      CrossOver-bottle-aware toggle for Apple's Metal performance HUD, editing `cxbottle.conf` directly.
alive:     62★
why:       Mildly useful as a convenience toggle, but it does not log or parse the numbers.
tags:      mac-gaming, metal-hud, crossover, toggle, convenience

## todbot/mac-hid-dump
link:      https://github.com/todbot/mac-hid-dump
surfaced:  2026-08-15
what:      Command-line HID report dumper for macOS.
alive:     no liveness data recorded at capture
why:       Surfaced in the HID/input-latency search and logged to the dedupe list; a dump/inspection utility rather than a latency benchmark, in the same class as the other HID tools that were dropped.
tags:      mac-gaming, hid, dump, diagnostic, not-latency

## tlkh/asitop
link:      https://github.com/tlkh/asitop
surfaced:  2026-08-15
what:      Apple Silicon power/thermal monitor, the widely-cited one.
alive:     4.6k★ but dead — last commit 2023-01-24, explicitly Monterey-only in its own README, 52 open issues, no activity since
why:       High star count here is a trap, not a signal — more stars than macmon and mactop combined, and dead. Explicitly called out as such rather than recommended.
tags:      mac-gaming, power, thermal, dead, star-trap, monterey-only

## timkurvers/metalhud
link:      https://github.com/timkurvers/metalhud
surfaced:  2026-08-15
what:      Toggle utility for Apple's Metal performance HUD.
alive:     8★
why:       Toggle-only, no logging or parsing. Metal HUD logging/parsing over time doesn't exist as a maintained tool.
tags:      mac-gaming, metal-hud, toggle, measurement-gap

## theodorechapman/win32mac
link:      https://github.com/theodorechapman/win32mac
surfaced:  2026-08-15
what:      Proof-of-concept Win32 compatibility work for macOS.
alive:     1★, 3 commits
why:       A proof-of-concept covering Fallout New Vegas only. Not maintained, not general-purpose. Dropped.
tags:      mac-gaming, win32, proof-of-concept, unmaintained

## teamfinalmouse/xlat
link:      https://github.com/teamfinalmouse/xlat
surfaced:  2026-08-15
what:      Hardware-firmware input-latency measurement rig.
alive:     commit/contributor/release detail unrecorded
why:       Hardware-firmware based, not macOS-HID-native, no Metal HUD pairing. A different technique entirely. Dropped.
tags:      mac-gaming, latency, hardware, firmware, different-technique

## t0msk/InputLagTester
link:      https://github.com/t0msk/InputLagTester
surfaced:  2026-08-15
what:      Input-lag testing tool.
alive:     commit/contributor/release detail unrecorded
why:       Hardware-firmware or camera/photodiode based, not macOS-HID-native, no Metal HUD pairing. A different technique entirely. Dropped.
tags:      mac-gaming, latency, hardware, different-technique

## SuperKenVery/asitop
link:      https://github.com/SuperKenVery/asitop
surfaced:  2026-08-15
what:      Revival fork of asitop.
alive:     no independent evidence of currency found
why:       A revival fork with no independent evidence of currency. Not shortlisted.
tags:      mac-gaming, power, thermal, fork, unverified

## stenyak/inputLagTimer
link:      https://github.com/stenyak/inputLagTimer
surfaced:  2026-08-15
what:      Camera/photodiode-based input-latency measurement tool.
alive:     commit/contributor/release detail unrecorded
why:       Camera/photodiode-based, not macOS-HID-native, no Metal HUD pairing. A different technique entirely. Dropped.
tags:      mac-gaming, latency, camera, photodiode, different-technique

## Starefossen/prlctl-usb
link:      https://github.com/Starefossen/prlctl-usb
surfaced:  2026-08-15
what:      USB helper for the Parallels `prlctl` tool.
alive:     0–4★ range, no real adoption
why:       Tiny and unproven, not gaming-framed. Dropped.
tags:      mac-gaming, parallels, prlctl, usb, tiny, unproven

## socram8888/SKSE64LoaderDLL
link:      https://github.com/socram8888/SKSE64LoaderDLL
surfaced:  2026-08-15
what:      Generic Windows SKSE loader alternative.
alive:     commit/contributor/release detail unrecorded
why:       Not Mac-specific. Nothing dedicated exists for SKSE under Wine, and nothing is needed — SKSE, Address Library and CommonLibSSE are generic Windows infrastructure that just needs to run inside a correctly configured bottle, same as on real Windows.
tags:      mac-gaming, skyrim, skse, windows, not-mac-specific

## Sikarugir-App/Sikarugir
link:      https://github.com/Sikarugir-App/Sikarugir
surfaced:  2026-08-15
what:      GUI Wine-bottle manager (Wineskin → Kegworks → Sikarugir lineage) for wrapping individual Windows apps and games, with WineD3D/VKD3D/D3DMetal/DXMT/DXVK all selectable per-wrapper.
alive:     3.5k★, 150 commits, commits as recent as 2026-08-04. No tagged Releases (rolling `main` via Homebrew tap only) — a changelog-discipline gap, not a maintenance red flag
why:       Maintained in part by Gcenx, who also maintains WineHQ's official macOS Wine builds and the Homebrew/MacPorts Wine taps — real standing in the upstream Wine-on-Mac community, not a random wrapper author. Apple Silicon confirmed, macOS 14+ required, but the README notes parts of the stack still need Rosetta 2, so "Apple Silicon support" means "runs," not "runs fully native." Not a reason to leave CrossOver, which is the commercial upstream this whole ecosystem free-rides on. Worth a look specifically to A/B a DXMT-backed bottle for Skyrim SE against CrossOver's D3DMetal path, or for a free bottle for a one-off non-game Windows app. Take-an-idea, not adopt. Security note: the repo warns `sikarugir.com` is a squatted, unaffiliated domain — GitHub and the official Homebrew tap are the only legitimate sources.
tags:      mac-gaming, bottle-manager, wine, apple-silicon, dxmt, gcenx, active

## sasobhabha/Brandywine
link:      https://github.com/sasobhabha/Brandywine
surfaced:  2026-08-15
what:      A fork of Whisky, the macOS Wine wrapper.
alive:     thinner activity than frankea's fork; commit/contributor/release detail unrecorded
why:       Thinner activity than frankea/Whisky and redundant with it.
tags:      general, mac-gaming, wine, whisky-fork, redundant

## rotki/rotki
link:      https://github.com/rotki/rotki
surfaced:  2026-08-15
what:      Self-hosted portfolio and accounting tool.
alive:     no liveness data recorded at capture
why:       Strong self-hosted portfolio tool but crypto/tax-focused; ghostfolio is the closer fit for general share holdings.
tags:      general, portfolio, crypto, tax, self-hosted

## rhunecke/HIDTester
link:      https://github.com/rhunecke/HIDTester
surfaced:  2026-08-15
what:      HID controller test utility.
alive:     19★; confirms Apple Silicon
why:       A visual diagnostic (axis/deadzone), not a latency benchmark. Dropped.
tags:      mac-gaming, hid, diagnostic, apple-silicon, not-latency

## rbourgeat/mac-m1-game-list
link:      https://github.com/rbourgeat/mac-m1-game-list
surfaced:  2026-08-15
what:      A list of games and how they run on Apple Silicon Macs.
alive:     archived 2026-01-12, stale
why:       The one project that directly matched the "Parallels as gaming fallback" framing, but archived and stale. Not shortlisted; noted as a dead pointer.
tags:      mac-gaming, game-list, parallels, archived, dead-pointer

## qsniyg/winevfs
link:      https://github.com/qsniyg/winevfs
surfaced:  2026-08-15
what:      Virtual filesystem layer for Wine.
alive:     Linux-only; not maintained
why:       Linux-only and not general-purpose. Dropped.
tags:      mac-gaming, wine, vfs, linux-only, unmaintained

## pqrs-org/osx-hid-inspector
link:      https://github.com/pqrs-org/osx-hid-inspector
surfaced:  2026-08-15
what:      macOS HID descriptor and property inspector.
alive:     36★, genuinely active — commits within days of the sweep
why:       Descriptor/property inspection only, no timing capture. Not a latency tool, so not what's needed here.
tags:      mac-gaming, hid, inspector, no-timing, active

## pqrs-org/Karabiner-Elements
link:      https://github.com/pqrs-org/Karabiner-Elements
surfaced:  2026-08-15
what:      The dominant macOS keyboard/input remapper.
alive:     22.6k★, actively maintained with macOS 26 Tahoe support
why:       Relevant as "the" remapper if remapping is ever needed, but not a measurement tool — out of scope for this sweep's need.
tags:      mac-gaming, hid, remapper, input, out-of-scope, active

## pkoistin/prlkey
link:      https://github.com/pkoistin/prlkey
surfaced:  2026-08-15
what:      Small `prlctl` wrapper utility for Parallels.
alive:     0–4★ range, no real adoption
why:       Tiny and unproven, not gaming-framed. Dropped.
tags:      mac-gaming, parallels, prlctl, tiny, unproven

## philipturner/metal-benchmarks
link:      https://github.com/philipturner/metal-benchmarks
surfaced:  2026-08-15
what:      Apple GPU microarchitecture benchmarks.
alive:     commit/contributor/release detail unrecorded
why:       GPU microarchitecture benchmarking, not per-frame game timing capture. Not relevant to the frame-pacing gap. Dropped.
tags:      mac-gaming, metal, gpu, microarchitecture, benchmark

## Parallels/vagrant-parallels
link:      https://github.com/Parallels/vagrant-parallels
surfaced:  2026-08-15
what:      Vagrant provider for Parallels Desktop.
alive:     real, maintained
why:       CI/dev-provisioning tooling with zero gaming relevance. Dropped.
tags:      mac-gaming, parallels, vagrant, provisioning, no-gaming-relevance

## Parallels/prlctl-scripts
link:      https://github.com/Parallels/prlctl-scripts
surfaced:  2026-08-15
what:      Scripts for the Parallels `prlctl` command-line tool.
alive:     real, maintained
why:       CI/dev-provisioning tooling with zero gaming relevance. Dropped.
tags:      mac-gaming, parallels, provisioning, ci, no-gaming-relevance

## Parallels/parallels-vscode-extension
link:      https://github.com/Parallels/parallels-vscode-extension
surfaced:  2026-08-15
what:      VS Code extension for Parallels Desktop.
alive:     real, maintained
why:       CI/dev-provisioning tooling with zero gaming relevance. Dropped.
tags:      mac-gaming, parallels, vscode, tooling, no-gaming-relevance

## Parallels/packer-examples
link:      https://github.com/Parallels/packer-examples
surfaced:  2026-08-15
what:      Packer build examples for Parallels Desktop.
alive:     real, maintained
why:       CI/dev-provisioning tooling with zero gaming relevance. Dropped.
tags:      mac-gaming, parallels, packer, provisioning, no-gaming-relevance

## op06072/NeoAsitop
link:      https://github.com/op06072/NeoAsitop
surfaced:  2026-08-15
what:      Sudoless Apple Silicon power/thermal monitor in the asitop lineage.
alive:     100★; only tested through M1 Ultra per its own docs
why:       Sudoless, but weaker than macmon/mactop on hardware coverage.
tags:      mac-gaming, power, thermal, sudoless, limited-hardware

## Omni-guides/Tuxborn
link:      https://github.com/Omni-guides/Tuxborn
surfaced:  2026-08-15
what:      A Wabbajack-format Skyrim SE modlist tuned for Steam Deck / lower-spec-PC performance targets (Legacy of the Dragonborn, BFCO combat overhaul, NPC/quest content) — a config repo, not executable tooling.
alive:     99★, 262 commits, commits as recent as 2026-07-15 — active
why:       Counted because it's a real answer in the gap the 08-15 sweep flagged as unsolved. No macOS mention in the repo's own README (it's Steam-Deck/Linux-framed), but the annathepiper guide documents someone running it on a Mac specifically, and a Steam-Deck-safe modlist is a reasonable proxy for Wine/CrossOver-safe since both avoid the same class of Windows-only INI/driver hacks — reasoning, not a guarantee. Correction flagged in PR review and verified: "survives the Mac path" overstated it — the guide marks the Mac process **experimental**, and Tuxborn's bundled Community Shaders 1.2.1 (vs the current 1.3) breaks grass/sky rendering under CrossOver unless disabled. A working install can reportedly be copied over from a Steam Deck and then only needs CrossOver to run — but "runs" still means "runs with a known graphics bug you have to work around," not a clean pass. Worth considering as a curated starting load order instead of building one from scratch, expecting to disable Community Shaders as a known first fix.
tags:      mac-gaming, skyrim, modlist, wabbajack, crossover, experimental, config-repo

## N2M0/Metal-HUD-Parse
link:      https://github.com/N2M0/Metal-HUD-Parse
surfaced:  2026-08-15
what:      Project named for parsing Metal HUD output.
alive:     0★
why:       Reads as a personal script, not a tool. The closest thing to Metal HUD parsing that exists, which is the point: there isn't one.
tags:      mac-gaming, metal-hud, parsing, personal-script, measurement-gap

## MythicApp/wine
link:      https://github.com/MythicApp/wine
surfaced:  2026-08-15
what:      Wine build maintained for the Mythic macOS game launcher; successor to MythicApp/Engine.
alive:     3★, unadopted
why:       Supersedes the archived Engine repo but has seen no adoption.
tags:      mac-gaming, wine, unadopted, launcher

## MythicApp/Engine
link:      https://github.com/MythicApp/Engine
surfaced:  2026-08-15
what:      The engine component behind the Mythic macOS game launcher.
alive:     archived; superseded by MythicApp/wine
why:       Archived and superseded.
tags:      mac-gaming, archived, superseded, launcher

## mrb0y/Gamepadla
link:      https://github.com/mrb0y/Gamepadla
surfaced:  2026-08-15
what:      Gamepad latency/polling measurement tool.
alive:     commit/contributor/release detail unrecorded
why:       Measures analog-stick jitter interval, not press-to-frame latency; explicitly caveated by its own authors as a guide rather than an exact measurement.
tags:      mac-gaming, controller, polling-rate, latency-proxy, not-a-substitute

## MonitorControl/MonitorControl
link:      https://github.com/MonitorControl/MonitorControl
surfaced:  2026-08-15
what:      macOS DDC brightness and volume control.
alive:     commit/contributor/release detail unrecorded
why:       DDC brightness/volume only, no refresh-rate or VRR capability at all. Not relevant to the actual need. Dropped.
tags:      mac-gaming, display, ddc, brightness, not-relevant

## ModOrganizer2/modorganizer
link:      https://github.com/ModOrganizer2/modorganizer
surfaced:  2026-08-15
what:      Mod Organizer 2, the Windows mod manager for Bethesda games.
alive:     Windows-only; USVFS-under-Wine tracked in open issue #372, open since 2018-05-19 and still open with no new activity as of 2026-08-16
why:       This is the actual blocker for the planned Skyrim SE MO2 setup. MO2's own USVFS doesn't work correctly under Wine, and no Mac-native alternative has real adoption. Everyone just runs MO2.exe inside the CrossOver bottle and lives with USVFS being occasionally flaky — worth knowing going in on the heavily-modded Skyrim SE plan, not a tooling gap you can currently buy your way out of.
tags:      mac-gaming, skyrim, mod-manager, usvfs, wine, blocker, windows-only

## mikyll/SDL2-Controller-Tester
link:      https://github.com/mikyll/SDL2-Controller-Tester
surfaced:  2026-08-15
what:      SDL2-based controller test utility.
alive:     no liveness data recorded at capture
why:       Mapping/visualization only, no latency measurement. Dropped.
tags:      mac-gaming, controller, sdl2, mapping, not-latency

## metaspartan/mactop
link:      https://github.com/metaspartan/mactop
surfaced:  2026-08-15
what:      Go-based alternative to macmon: terminal TUI plus a `--menubar` mode with live sparklines/gauges, reading native IOReport/IOKit/SMC APIs directly (also sudoless), and adding fan RPM readout and control.
alive:     1.6k★, 599 commits; v2.1.3–v2.1.5 releases landed 2026-05-03 through 2026-06-14, with changelog entries referencing ANE-bandwidth handling for the macOS 27 beta — actively tracking the current OS beta cycle. Confirms M1 through M5/M5 Pro/Max
why:       Use instead of macmon if you want an always-visible menu-bar HUD during play rather than a terminal you have to keep in view, or if you want fan control alongside monitoring. Functionally overlapping with macmon — pick one, they're not both needed.
tags:      mac-gaming, power, thermal, menubar, go, apple-silicon, fan-control, active

## maziac/lagmeter
link:      https://github.com/maziac/lagmeter
surfaced:  2026-08-15
what:      Hardware-based input-lag measurement tool.
alive:     commit/contributor/release detail unrecorded
why:       Hardware-firmware based, not macOS-HID-native, no Metal HUD pairing. A different technique entirely. Dropped.
tags:      mac-gaming, latency, hardware, different-technique

## limo-app/limo
link:      https://github.com/limo-app/limo
surfaced:  2026-08-15
what:      Native Bethesda-focused mod manager.
alive:     767★, real activity
why:       A good native mod manager — but Linux-only, no macOS support. Dropped for this rig, cited as "what a good native alternative looks like."
tags:      mac-gaming, mod-manager, linux-only, bethesda, reference

## Lifeisawful/rosettax87_jit
link:      https://github.com/Lifeisawful/rosettax87_jit
surfaced:  2026-08-15
what:      x87/AVX instruction patching for old DirectX 9 titles crashing under Rosetta 2.
alive:     active — commits through 2026-08-07
why:       A real, narrow, currently-active niche, but specifically for World-of-Warcraft-era DX9 titles. Elden Ring and Skyrim SE are both DX11/12-era, so it isn't currently relevant — worth remembering if you ever run something DX9-vintage through GPTK.
tags:      mac-gaming, rosetta, x87, dx9, niche, active

## Lifeisawful/rosettax87
link:      https://github.com/Lifeisawful/rosettax87
surfaced:  2026-08-15
what:      Rosetta 2 x87 patching work, the predecessor to rosettax87_jit.
alive:     archived
why:       A dead end, flagged so it isn't chased again.
tags:      mac-gaming, rosetta, x87, archived, dead-end

## leonewt0n/Bourbon
link:      https://github.com/leonewt0n/Bourbon
surfaced:  2026-08-15
what:      A fork of Whisky, the macOS Wine wrapper.
alive:     thinner activity than frankea's fork; commit/contributor/release detail unrecorded
why:       Thinner activity than frankea/Whisky and redundant with it.
tags:      general, mac-gaming, wine, whisky-fork, redundant

## kianwoon/asitop
link:      https://github.com/kianwoon/asitop
surfaced:  2026-08-15
what:      Revival fork of asitop.
alive:     no independent evidence of currency found
why:       A revival fork with no independent evidence of currency. Not shortlisted.
tags:      mac-gaming, power, thermal, fork, unverified

## KhronosGroup/MoltenVK
link:      https://github.com/KhronosGroup/MoltenVK
surfaced:  2026-08-15
what:      Vulkan implementation layered over Apple's Metal.
alive:     5.8k★, healthy (v1.4.2-rc1, 2026-07-19)
why:       Infrastructure other tools build on, not a standalone user tool. Name-checked rather than given a slot of its own.
tags:      mac-gaming, vulkan, metal, infrastructure, khronos

## Kegworks-App/Kegworks
link:      https://github.com/Kegworks-App/Kegworks
surfaced:  2026-08-15
what:      Wine-bottle manager, the previous name in the Wineskin → Kegworks → Sikarugir lineage.
alive:     renamed to Sikarugir-App/Sikarugir in Oct 2025; GitHub redirects
why:       Renamed rather than abandoned — the live project is Sikarugir, which is shortlisted.
tags:      mac-gaming, bottle-manager, wine, renamed, redirect

## JulyIghor/prltype
link:      https://github.com/JulyIghor/prltype
surfaced:  2026-08-15
what:      Small `prlctl` wrapper utility for Parallels.
alive:     0–4★ range, no real adoption
why:       Tiny and unproven, not gaming-framed. Dropped.
tags:      mac-gaming, parallels, prlctl, tiny, unproven

## its-a-feature/Mythic
link:      https://github.com/its-a-feature/Mythic
surfaced:  2026-08-15
what:      A red-team command-and-control framework, unrelated to the macOS game launcher of the same name.
alive:     commit/contributor/release detail unrecorded
why:       Surfaced only as a name collision: `MythicApp/Mythic` (the macOS GPTK game launcher) shares its name with this unrelated red-team C2 tool, which was noted as a reason the launcher's name is confusing to search for. Logged so the collision is on record, not as a find in this domain.
tags:      mac-gaming, name-collision, security, c2, not-a-find

## installaware/AGPT
link:      https://github.com/installaware/AGPT
surfaced:  2026-08-15
what:      Free, point-and-click installer GUI for Apple's Game Porting Toolkit, from InstallAware, with notarized builds.
alive:     542★; last commit 2025-01-06 — 19+ months old as of the sweep
why:       Ruled out as stale: the underlying stack it wraps (D3DMetal, DXMT) has moved fast enough in that window that an installer frozen at that point is a real risk, not a nitpick. Not recommended over CrossOver.
tags:      mac-gaming, gptk, installer, gui, stale, ruled-out

## imichaelnorris/Bourbon
link:      https://github.com/imichaelnorris/Bourbon
surfaced:  2026-08-15
what:      A fork of Whisky, the macOS Wine wrapper.
alive:     thinner activity than frankea's fork; commit/contributor/release detail unrecorded
why:       Thinner activity than frankea/Whisky and redundant with it.
tags:      general, mac-gaming, wine, whisky-fork, redundant

## huberdf/FreeDisplay
link:      https://github.com/huberdf/FreeDisplay
surfaced:  2026-08-15
what:      Open-source macOS display-control utility.
alive:     85★, genuinely open
why:       Genuinely open source, but has no refresh-rate/VRR row in its own feature table — not a substitute for BetterDisplay on the axis that matters here.
tags:      mac-gaming, display, open-source, no-vrr, limited

## guilhermearaujo/xboxonecontrollerenabler
link:      https://github.com/guilhermearaujo/xboxonecontrollerenabler
surfaced:  2026-08-15
what:      Xbox One controller enabler for macOS.
alive:     no liveness data recorded at capture
why:       Surfaced in the controller search and logged to the dedupe list; superseded by macOS's native support for Bluetooth Xbox controllers made after August 2016, which needs no driver.
tags:      mac-gaming, controller, xbox, driver, superseded

## gromeck/LatencyMeasure
link:      https://github.com/gromeck/LatencyMeasure
surfaced:  2026-08-15
what:      Hardware-based latency measurement tool.
alive:     commit/contributor/release detail unrecorded
why:       Hardware-firmware based, not macOS-HID-native, no Metal HUD pairing. A different technique entirely. Dropped.
tags:      mac-gaming, latency, hardware, different-technique

## General-Arcade/sdl2-gamepad-tool
link:      https://github.com/General-Arcade/sdl2-gamepad-tool
surfaced:  2026-08-15
what:      SDL2-based gamepad mapping tool.
alive:     no liveness data recorded at capture
why:       Mapping/visualization only, no latency measurement. Dropped.
tags:      mac-gaming, controller, sdl2, mapping, not-latency

## Gcenx/winerosetta
link:      https://github.com/Gcenx/winerosetta
surfaced:  2026-08-15
what:      Rosetta-related Wine tooling for old DirectX 9 titles.
alive:     established, maintained by Gcenx — a credible name in Wine-on-Mac
why:       The same DX9/WoW niche as rosettax87. Noted, not shortlisted — not relevant to the current games.
tags:      mac-gaming, rosetta, wine, dx9, gcenx, niche

## Gcenx/macports-wine
link:      https://github.com/Gcenx/macports-wine
surfaced:  2026-08-15
what:      MacPorts Wine packaging for macOS, maintained by Gcenx.
alive:     no liveness data recorded at capture
why:       Part of the Gcenx Wine-on-Mac infrastructure named as evidence of upstream standing.
tags:      mac-gaming, wine, macports, packaging, gcenx, infrastructure

## Gcenx/macOS_Wine_builds
link:      https://github.com/Gcenx/macOS_Wine_builds
surfaced:  2026-08-15
what:      WineHQ's official macOS Wine builds, maintained by Gcenx.
alive:     commit/contributor/release detail unrecorded
why:       Named as evidence of Gcenx's real standing in the upstream Wine-on-Mac community — the same maintainer behind Sikarugir and the Homebrew/MacPorts Wine taps. Infrastructure rather than a user-facing tool.
tags:      mac-gaming, wine, builds, gcenx, infrastructure, upstream

## Gcenx/homebrew-wine
link:      https://github.com/Gcenx/homebrew-wine
surfaced:  2026-08-15
what:      Homebrew tap for Wine on macOS, maintained by Gcenx.
alive:     no liveness data recorded at capture
why:       Part of the Gcenx Wine-on-Mac infrastructure named as evidence of upstream standing; the legitimate distribution channel for Sikarugir alongside GitHub.
tags:      mac-gaming, wine, homebrew, tap, gcenx, infrastructure

## Gcenx/DXVK-macOS
link:      https://github.com/Gcenx/DXVK-macOS
surfaced:  2026-08-15
what:      macOS port of DXVK.
alive:     293★, last release 2023-07-23
why:       Superseded by DXMT and D3DMetal/GPTK. Dropped as abandoned.
tags:      mac-gaming, translation-layer, dxvk, macos, abandoned

## frankea/Whisky
link:      https://github.com/frankea/Whisky
surfaced:  2026-08-15
what:      Actively maintained community continuation of Whisky, a native macOS Wine wrapper for running Windows games and apps on Apple Silicon.
alive:     401★, 28 forks, 11 open issues under active triage, pushed 2026-08-13; issues/commits as recent as 2026-08-12–14
why:       Exists specifically because the original `whisky-app/whisky` was archived (April 2025) and the maintainer picked up the backlog. Ships DXMT (a Metal-native DX12 backend) and Game Porting Toolkit integration — genuinely newer engineering than what CrossOver ships. Sits right next to CrossOver in the same problem space: a free, Apple-Silicon-native alternative worth A/B-ing against whatever CrossOver is currently doing for specific titles, especially anything CrossOver runs poorly. First move: install it alongside CrossOver, pick one game that currently runs suboptimally, and compare DXMT vs CrossOver's D3DMetal backend on FPS/stability. The real continuation of Whisky — don't use the archived original.
tags:      general, mac-gaming, wine, crossover, apple-silicon, dxmt, bottle-manager

## FluidInference/fluidtop
link:      https://github.com/FluidInference/fluidtop
surfaced:  2026-08-15
what:      Apple Silicon power/thermal monitor, a real asitop-replacement effort.
alive:     66★, 112 commits; M1–M4 claimed but no M5 mention yet; much smaller community than macmon/mactop
why:       A genuine replacement effort but a much smaller community than macmon/mactop. Not shortlisted, worth a re-check next sweep.
tags:      mac-gaming, power, thermal, asitop-replacement, recheck

## FFRI/ProjectChampollion
link:      https://github.com/FFRI/ProjectChampollion
surfaced:  2026-08-15
what:      Reverse-engineering research on Rosetta 2 internals.
alive:     archived
why:       No gaming tooling — not a tool, background reading only.
tags:      mac-gaming, rosetta, reverse-engineering, research, archived

## exelban/stats
link:      https://github.com/exelban/stats
surfaced:  2026-08-15
what:      The most popular general macOS menu-bar system monitor.
alive:     41.2k★, actively released
why:       Historically showed utilization % rather than true powermetrics-grade wattage — a 2025 feature request had to ask for power metrics. Verify the current build before treating it as a macmon/mactop substitute; it's a fine general system monitor, not built around power data the way those two are. Noted as a caveat rather than a straight recommendation.
tags:      mac-gaming, system-monitor, menubar, power, caveat, popular

## espetro/wowplay
link:      https://github.com/espetro/wowplay
surfaced:  2026-08-15
what:      World of Warcraft on macOS launcher/tooling.
alive:     brand new (2026-06), 0★; own README admits crashes/WIP
why:       Watch-list only.
tags:      mac-gaming, wow, dx9, wip, watch-list

## doitsujin/dxvk
link:      https://github.com/doitsujin/dxvk
surfaced:  2026-08-15
what:      Vulkan-based D3D9/10/11 translation layer.
alive:     17.8k★, healthy
why:       Linux/Proton-scoped, no macOS mention. Not directly usable; enters this space only via MoltenVK or Gcenx's old port.
tags:      mac-gaming, translation-layer, vulkan, linux, proton, upstream

## dkosmari/SDL2-Game-Controller-Test
link:      https://github.com/dkosmari/SDL2-Game-Controller-Test
surfaced:  2026-08-15
what:      SDL2-based controller test utility.
alive:     no liveness data recorded at capture
why:       Mapping/visualization only, no latency measurement. Dropped.
tags:      mac-gaming, controller, sdl2, mapping, not-latency

## diewland/py-rosetta2-vs-arm
link:      https://github.com/diewland/py-rosetta2-vs-arm
surfaced:  2026-08-15
what:      Rosetta 2 vs native ARM benchmarking scripts in Python.
alive:     1★, dormant since ~2020
why:       Dropped.
tags:      mac-gaming, rosetta, benchmark, dormant

## charmbracelet/crush
link:      https://github.com/charmbracelet/crush
surfaced:  2026-08-15
what:      Charm's own terminal AI coding agent (Go, Bubbletea-based) — a direct sibling to the opencode fork already in progress, built by the team behind the TUI libraries (Bubbletea/Lipgloss/Glamour) that also power nom.
alive:     27,382★, 2,158 forks, 630 open issues under active work, pushed 2026-08-14; built by a well-resourced, long-running OSS shop
why:       Not a fork target (different stack — Go/Bubbletea vs the opencode fork's TS/Bun), but the closest actively-developed sibling project to study for UX and agent-loop decisions. Its underlying TUI libraries are also exactly what would polish the terminal news reader. First move: run crush on one real task for a day, note anywhere its TUI/agent-loop choices diverge from the opencode fork's, and flag anything worth backporting.
tags:      general, coding-agent, terminal, tui, go, bubbletea, sibling-project

## cakama3a/Polling
link:      https://github.com/cakama3a/Polling
surfaced:  2026-08-15
what:      Controller polling-rate measurement tool.
alive:     commit/contributor/release detail unrecorded
why:       Measures the interval between successive analog-stick position changes while you move the stick in a circle — a synthetic proxy for controller responsiveness, not true button-press-to-frame latency, and the authors themselves caveat it as "a guide, not an exact measurement." Confirmed nothing here rivals the existing raw-HID + Metal HUD tool.
tags:      mac-gaming, controller, polling-rate, latency-proxy, not-a-substitute

## atahan99/simple-parallels
link:      https://github.com/atahan99/simple-parallels
surfaced:  2026-08-15
what:      Small `prlctl` wrapper utility for Parallels.
alive:     0–4★ range, no real adoption
why:       Tiny and unproven, not gaming-framed. Dropped.
tags:      mac-gaming, parallels, prlctl, tiny, unproven

## AryaLabsHQ/bunli
link:      https://github.com/AryaLabsHQ/bunli
surfaced:  2026-08-15
what:      Bun-native CLI framework.
alive:     95★ / 5 forks — too early to call proven adoption
why:       On-theme (explicit Bun user) but too early to call proven adoption yet. Worth a re-check in a future sweep; was not added to the dedupe list as a firm pass since the verdict may change.
tags:      general, bun, cli, framework, early, recheck

## aquitaine/OpenDisplay
link:      https://github.com/aquitaine/OpenDisplay
surfaced:  2026-08-15
what:      GPL-3.0 clean-room macOS display-control alternative explicitly targeting Apple Silicon.
alive:     8★, pre-1.0, VRR support unconfirmed
why:       A promising genuinely-open alternative to BetterDisplay, but pre-1.0 with VRR unconfirmed. Worth a bookmark to revisit and a re-check next sweep, not a recommendation yet.
tags:      mac-gaming, display, open-source, apple-silicon, pre-1.0, recheck

## apple/game-porting-toolkit
link:      https://github.com/apple/game-porting-toolkit
surfaced:  2026-08-15
what:      Apple repo containing AI agent skills (Metal 4 / MetalFX / shader-compilation domain modules for coding-assistant porting workflows), Metal-cpp, and code samples.
alive:     commit/contributor/release detail unrecorded
why:       Misidentified on first pass and corrected after PR #44 review: this repo is **not** the GPTK translation-layer toolkit. GPTK 4 itself (the actual Wine-based evaluation environment / Metal Shader Converter) is listed as a prerequisite downloaded separately from developer.apple.com — not a GitHub repo at all. Corrected finding: there is no GitHub upstream for GPTK to point to; the tool the DXMT/Sikarugir/Whisky-family projects build config around is an Apple-Developer-portal-only download. Worth knowing as a "doesn't exist as a repo" fact in its own right. Kept in the dedupe list only so a future sweep doesn't re-surface and re-misidentify it.
tags:      mac-gaming, apple, gptk, metal, correction, not-the-toolkit, background

## Alia-Traces/MetalBench
link:      https://github.com/Alia-Traces/MetalBench
surfaced:  2026-08-15
what:      Metal GPU benchmarking tool.
alive:     commit/contributor/release detail unrecorded
why:       GPU microarchitecture benchmarking, not per-frame game timing capture. Not relevant to the frame-pacing gap. Dropped.
tags:      mac-gaming, metal, gpu, benchmark, not-frame-timing

## akemin-dayo/IOKitHIDKeyboardTester
link:      https://github.com/akemin-dayo/IOKitHIDKeyboardTester
surfaced:  2026-08-15
what:      IOKit HID keyboard test utility for macOS.
alive:     no liveness data recorded at capture
why:       Surfaced in the HID/input-latency search and logged to the dedupe list; a diagnostic rather than a latency benchmark, in the same class as the other HID testers that were dropped.
tags:      mac-gaming, hid, keyboard, diagnostic, not-latency

## 3Shain/dxmt
link:      https://github.com/3Shain/dxmt
surfaced:  2026-08-15
what:      Metal-native Direct3D 11/10 (and growing D3D12) translation layer for Wine on macOS.
alive:     1.1k★; 10 commits landed on 2026-08-13 alone (D3D12 indirect draw/dispatch work) — current, active engineering, not a snapshot. Tagged GitHub Releases stopped at v0.80 (2025-04-23, mid MIT→LGPL relicense toward v1.0), so it ships bundled inside bottle managers rather than via its own release page — a packaging gap, not an activity gap. Issue #151 ("DXMT 1.0 Release Plan", opened 2026-04-21) confirms active roadmap planning
why:       The actual "Metal descendant" in the DXVK lineage — not a fork of DXVK's code but the same niche solved natively for Metal instead of via MoltenVK. Apple Silicon (macOS 14+) is the *primary* supported target and Intel Mac support is explicitly still WIP, the reverse of most of this ecosystem. CodeWeavers' own CrossOver 26 changelog lists "DXMT 0.72" alongside D3DMetal 3.0 — third-party validation from the commercial beneficiary of the work. Nothing to install directly: it arrives as a selectable per-bottle backend in Sikarugir or the frankea Whisky fork. Worth knowing it exists so you can pick it as an alternate D3D11 backend to try against D3DMetal. No overlap with the raw-HID latency tool — pure graphics translation, no measurement surface.
tags:      mac-gaming, translation-layer, d3d11, metal, wine, apple-silicon, active

## 360Controller/360Controller
link:      https://github.com/360Controller/360Controller
surfaced:  2026-08-15
what:      Xbox 360/One controller driver for macOS.
alive:     6.7k★ but explicitly no Apple Silicon / Big Sur+ support per its own README (Dec 2020)
why:       Confirmed dead for this hardware. Also confirms the actual current answer: Bluetooth Xbox controllers made after August 2016 are natively supported by macOS, no driver needed.
tags:      mac-gaming, controller, driver, dead, no-apple-silicon

## wealthfolio/wealthfolio
link:      https://github.com/wealthfolio/wealthfolio
surfaced:  2026-08-13
what:      A private, local-first investment tracker — Rust/Tauri backend with a React/TypeScript frontend, SQLite via Diesel, that pulls in your holdings and shows real performance (twr/mwr, allocation, fees) without shipping your portfolio to anyone's cloud.
alive:     8.6k★, 3,485 commits, 319 open issues / 54 open PRs; commits landed same-day as the sweep (Aug 9–13 2026) covering SnapTrade brokerage sync, currency-gain fixes and a Japanese locale — multiple contributors, not a solo drip-feed; AGPL-3.0
why:       You said you hold shares you don't understand as well as you should — this is a tool that makes you actually look at them, and it's built in exactly your hobby stack (Rust + TypeScript, Tauri). It's a legitimate "read the source to learn Tauri properly" project as much as a thing to run. First move: `git clone` and run it locally against a read-only export of your holdings before connecting anything live.
tags:      general, investing, portfolio, local-first, rust, tauri, typescript

## ratatui/ratatui
link:      https://github.com/ratatui/ratatui
surfaced:  2026-08-13
what:      The standard Rust crate for building terminal UIs — layout, widgets, styling, input handling — the thing most serious Rust TUI apps (yazi, gitui, bottom, and others) are built on top of.
alive:     22.2k★, 2,307 commits, 148 open issues / 77 open PRs; organized as a workspace of maintained sub-crates (ratatui-core, ratatui-crossterm, ratatui-widgets)
why:       If any part of you wants to build the terminal news reader (or anything else you're gaming/CrossOver/terminal-adjacent about) in Rust rather than TS, this is the foundation everyone else already standardized on — you'd be building on well-trodden ground instead of reinventing input handling and layout. It's itself a survival story worth knowing: forked from the abandoned `tui-rs` and kept alive by a team rather than one person. First move: work through the official tutorial app once, then decide whether porting your news reader's rendering layer to it beats staying in TS/Bun.
tags:      general, rust, tui, terminal, widgets, foundation

## newsboat/newsboat
link:      https://github.com/newsboat/newsboat
surfaced:  2026-08-13
what:      The venerable terminal RSS/Atom reader (successor to Newsbeuter) — vim-style keybindings, macros, podcast queueing, scriptable filters, nothing but a terminal and a feed list.
alive:     3.9k★, 8,951 commits, 389 open issues, 16 open PRs, CI green on GitHub Actions + Cirrus CI; over a decade of continuous maintenance
why:       You have a half-finished terminal news reader of your own. Newsboat is worth having installed regardless (it's just a good reader), but it's also the reference implementation for the hard parts you'll hit — feed parsing edge cases, macro/filter syntax, offline caching. "Old and quietly maintained beats new and exciting." First move: install it, live with it for a week to find what you actually miss from it — that's your spec.
tags:      general, rss, terminal, tui, news-reader, cpp, reference

## MythicApp/Mythic
link:      https://github.com/MythicApp/Mythic
surfaced:  2026-08-13
what:      macOS GPTK-based game launcher, CrossOver-adjacent.
alive:     1.4k★ but last code commit ~2026-02-12 — six months stale as of the sweep; one source reported the sole maintainer had paused development
why:       A real project, but not solid enough today: thin/WIP Winetricks-arbitrary-app support, and the name collides with an unrelated red-team C2 tool (`its-a-feature/Mythic`). Watch-list only, not shortlisted. Deliberately not added to the general dedupe list at the time — the whole point of a recheck is that a future sweep needs to be able to find it again.
tags:      general, mac-gaming, launcher, gptk, stale, recheck

## karakeep-app/karakeep
link:      https://github.com/karakeep-app/karakeep
surfaced:  2026-08-13
what:      A self-hosted "bookmark everything" app — links, notes, screenshots — with AI-based auto-tagging, full-text + semantic search, and full-page archiving so saved pages don't rot when the source does.
alive:     28.3k–28,356★, 1,434 forks, 597–678 open issues and 80 open PRs, weekly-cadence releases through July 2026, pushed 2026-08-13; formerly "Hoarder," renamed and still shipping; AGPL-3.0, Docker, Ollama-capable
why:       You read a lot and keep more notes than you use — that's usually a retrieval problem, not a note-taking one. Karakeep's pitch is specifically "save now, find it again later without re-organizing," which is a lower-friction fit than another PKM tool, and local models mean tagging doesn't require sending your reading list to OpenAI. First move: stand it up in Docker with local search only (skip the AI tagging at first), point your browser extension at it for a week, and see whether full-text search alone already beats your save-and-forget habit.
tags:      general, bookmarks, notes, self-hosted, search, ollama, archiving

## guyfedwards/nom
link:      https://github.com/guyfedwards/nom
surfaced:  2026-08-13
what:      A terminal RSS/Atom reader (Go, Bubbletea TUI) with local sync and Miniflux/FreshRSS backend support, and markdown-rendered reading via Glow.
alive:     738–739★, 52 forks, 23 contributors, v3.0/v3.3.0 released this year (2026-03-19), pushed 2026-07-08, 33 open issues under active work; 11 distinct authors across its last 10 commits
why:       This is the exact project already half-built (a terminal news reader) — a working, maintained implementation of the same idea, so it's a direct comparison point rather than a tangent. A much smaller codebase than newsboat that's easier to read end-to-end in an afternoon and steal ideas from for a Bun/TS build. First move: run it for a week against real feeds and note which design choices (backend abstraction, keybindings, read-later state) are worth stealing outright vs deliberately doing differently.
tags:      general, rss, terminal, tui, go, bubbletea, news-reader

## ghostfolio/ghostfolio
link:      https://github.com/ghostfolio/ghostfolio
surfaced:  2026-08-13
what:      Open-source, self-hosted wealth-management dashboard (Angular + NestJS + Prisma) that aggregates holdings across brokers and exchanges into one view.
alive:     9.1k–9,127★, 1,271 forks, pushed 2026-08-14 (day of the sweep); active discussions, hundreds of open issues under triage, official Docker images, running continuously since 2021 — long past any spike
why:       The equivalent of wealthfolio in server form, if you'd rather have a self-hosted web dashboard than a local desktop app. Matches "hold some shares not understood as well as they should be" almost exactly — it exists to turn scattered holdings into allocation/performance/fee breakdowns without handing the data to another SaaS. First move: try the hosted demo/sandbox mode, then import one account's real holdings via CSV and see if the views clarify anything the broker's own app doesn't.
tags:      general, investing, portfolio, self-hosted, angular, nestjs, dashboard

## YutoTerashima/hms-harmful-brain-activity-classification
link:      https://github.com/YutoTerashima/hms-harmful-brain-activity-classification
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## XTERMINATORAPPS/Ableton-Extensions-Python-SDK
link:      https://github.com/XTERMINATORAPPS/Ableton-Extensions-Python-SDK
surfaced:  2026-07-01
what:      Hobbyist Ableton Extensions-SDK project from the ecosystem that sprang up in the SDK's first month.
alive:     created 2026-06, mostly 0–25★ cohort; commit/contributor/release detail unrecorded
why:       Part of the ~45-repo Extensions-SDK hobbyist flood: individually hobby-scale MIDI/notation/sample utilities, real evidence the SDK ecosystem is alive, but none is a DSP-analysis tool worth a separate writeup. Logged in bulk so the next sweep doesn't re-triage them; the SDK itself is the actual finding, not any one extension.
tags:      audio, ableton, extensions-sdk, hobbyist, ecosystem

## wuritz/trueclip
link:      https://github.com/wuritz/trueclip
surfaced:  2026-07-01
what:      Hobbyist Ableton Extensions-SDK project from the ecosystem that sprang up in the SDK's first month.
alive:     created 2026-06, mostly 0–25★ cohort; commit/contributor/release detail unrecorded
why:       Part of the ~45-repo Extensions-SDK hobbyist flood: individually hobby-scale MIDI/notation/sample utilities, real evidence the SDK ecosystem is alive, but none is a DSP-analysis tool worth a separate writeup. Logged in bulk so the next sweep doesn't re-triage them; the SDK itself is the actual finding, not any one extension.
tags:      audio, ableton, extensions-sdk, hobbyist, clips

## wolf-plugins/wolf-spectrum
link:      https://github.com/wolf-plugins/wolf-spectrum
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## withpica/pica-ableton-extension
link:      https://github.com/withpica/pica-ableton-extension
surfaced:  2026-07-01
what:      Hobbyist Ableton Extensions-SDK project from the ecosystem that sprang up in the SDK's first month.
alive:     created 2026-06, mostly 0–25★ cohort; commit/contributor/release detail unrecorded
why:       Part of the ~45-repo Extensions-SDK hobbyist flood: individually hobby-scale MIDI/notation/sample utilities, real evidence the SDK ecosystem is alive, but none is a DSP-analysis tool worth a separate writeup. Logged in bulk so the next sweep doesn't re-triage them; the SDK itself is the actual finding, not any one extension.
tags:      audio, ableton, extensions-sdk, hobbyist, ecosystem

## Wilooper/Lyrica
link:      https://github.com/Wilooper/Lyrica
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## vishalshar/Audio-Classification-using-CNN-MLP
link:      https://github.com/vishalshar/Audio-Classification-using-CNN-MLP
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## usbhaius0001-cpu/Ableton-Live-Glide-Latency-Optimizer
link:      https://github.com/usbhaius0001-cpu/Ableton-Live-Glide-Latency-Optimizer
surfaced:  2026-07-01
what:      Repo presenting itself as an Ableton Live latency optimizer.
alive:     152 stars in 3 days; topics include `activation-tools`; commit/contributor/release detail unrecorded
why:       The pattern matches cracked-software SEO bait, not a real tool. Flagged, not linked as a recommendation.
tags:      audio, ableton, seo-bait, suspicious, not-a-tool

## TuneNN/TuneNN
link:      https://github.com/TuneNN/TuneNN
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## tp7/Sushi
link:      https://github.com/tp7/Sushi
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## TomSchimansky/GuitarTuner
link:      https://github.com/TomSchimansky/GuitarTuner
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## svc-develop-team/so-vits-svc
link:      https://github.com/svc-develop-team/so-vits-svc
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## subtraktive/ableton-extensions
link:      https://github.com/subtraktive/ableton-extensions
surfaced:  2026-07-01
what:      Hobbyist Ableton Extensions-SDK project from the ecosystem that sprang up in the SDK's first month.
alive:     created 2026-06, mostly 0–25★ cohort; commit/contributor/release detail unrecorded
why:       Part of the ~45-repo Extensions-SDK hobbyist flood: individually hobby-scale MIDI/notation/sample utilities, real evidence the SDK ecosystem is alive, but none is a DSP-analysis tool worth a separate writeup. Logged in bulk so the next sweep doesn't re-triage them; the SDK itself is the actual finding, not any one extension.
tags:      audio, ableton, extensions-sdk, hobbyist, ecosystem

## stackswithans/akkorder
link:      https://github.com/stackswithans/akkorder
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## spectregrams/spectre
link:      https://github.com/spectregrams/spectre
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## source-separation/tutorial
link:      https://github.com/source-separation/tutorial
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## skulldxss/Ableton-Live-12-Desktop
link:      https://github.com/skulldxss/Ableton-Live-12-Desktop
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## sevagh/xumx-sliCQ
link:      https://github.com/sevagh/xumx-sliCQ
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## seanghay/vocal
link:      https://github.com/seanghay/vocal
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## seanghay/uvr-mdx-infer
link:      https://github.com/seanghay/uvr-mdx-infer
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## schonkopf/soundscape_IR
link:      https://github.com/schonkopf/soundscape_IR
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## Saganaki22/ComfyUI-AudioSR
link:      https://github.com/Saganaki22/ComfyUI-AudioSR
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## saarsena/theory-aide
link:      https://github.com/saarsena/theory-aide
surfaced:  2026-07-01
what:      Hobbyist Ableton Extensions-SDK project from the ecosystem that sprang up in the SDK's first month.
alive:     created 2026-06, mostly 0–25★ cohort; commit/contributor/release detail unrecorded
why:       Part of the ~45-repo Extensions-SDK hobbyist flood: individually hobby-scale MIDI/notation/sample utilities, real evidence the SDK ecosystem is alive, but none is a DSP-analysis tool worth a separate writeup. Logged in bulk so the next sweep doesn't re-triage them; the SDK itself is the actual finding, not any one extension.
tags:      audio, ableton, extensions-sdk, hobbyist, theory

## saarsena/melodic_generator
link:      https://github.com/saarsena/melodic_generator
surfaced:  2026-07-01
what:      Hobbyist Ableton Extensions-SDK project from the ecosystem that sprang up in the SDK's first month.
alive:     created 2026-06, mostly 0–25★ cohort; commit/contributor/release detail unrecorded
why:       Part of the ~45-repo Extensions-SDK hobbyist flood: individually hobby-scale MIDI/notation/sample utilities, real evidence the SDK ecosystem is alive, but none is a DSP-analysis tool worth a separate writeup. Logged in bulk so the next sweep doesn't re-triage them; the SDK itself is the actual finding, not any one extension.
tags:      audio, ableton, extensions-sdk, hobbyist, midi

## RVC-Project/Retrieval-based-Voice-Conversion-WebUI
link:      https://github.com/RVC-Project/Retrieval-based-Voice-Conversion-WebUI
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## Ronvaknins/ableton-extensions-skill
link:      https://github.com/Ronvaknins/ableton-extensions-skill
surfaced:  2026-07-01
what:      Hobbyist Ableton Extensions-SDK project from the ecosystem that sprang up in the SDK's first month.
alive:     created 2026-06, mostly 0–25★ cohort; commit/contributor/release detail unrecorded
why:       Part of the ~45-repo Extensions-SDK hobbyist flood: individually hobby-scale MIDI/notation/sample utilities, real evidence the SDK ecosystem is alive, but none is a DSP-analysis tool worth a separate writeup. Logged in bulk so the next sweep doesn't re-triage them; the SDK itself is the actual finding, not any one extension.
tags:      audio, ableton, extensions-sdk, hobbyist, ecosystem

## robclouth/noise-canvas
link:      https://github.com/robclouth/noise-canvas
surfaced:  2026-07-01
what:      Hobbyist Ableton Extensions-SDK project from the ecosystem that sprang up in the SDK's first month.
alive:     created 2026-06, mostly 0–25★ cohort; commit/contributor/release detail unrecorded
why:       Part of the ~45-repo Extensions-SDK hobbyist flood: individually hobby-scale MIDI/notation/sample utilities, real evidence the SDK ecosystem is alive, but none is a DSP-analysis tool worth a separate writeup. Logged in bulk so the next sweep doesn't re-triage them; the SDK itself is the actual finding, not any one extension.
tags:      audio, ableton, extensions-sdk, hobbyist, ecosystem

## rnheroes/react-native-pitchy
link:      https://github.com/rnheroes/react-native-pitchy
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## ramonsesma/live-studio
link:      https://github.com/ramonsesma/live-studio
surfaced:  2026-07-01
what:      Hobbyist Ableton Extensions-SDK project from the ecosystem that sprang up in the SDK's first month.
alive:     created 2026-06, mostly 0–25★ cohort; commit/contributor/release detail unrecorded
why:       Part of the ~45-repo Extensions-SDK hobbyist flood: individually hobby-scale MIDI/notation/sample utilities, real evidence the SDK ecosystem is alive, but none is a DSP-analysis tool worth a separate writeup. Logged in bulk so the next sweep doesn't re-triage them; the SDK itself is the actual finding, not any one extension.
tags:      audio, ableton, extensions-sdk, hobbyist, ecosystem

## rakuri255/UltraSinger
link:      https://github.com/rakuri255/UltraSinger
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## pnomolos/live-wire
link:      https://github.com/pnomolos/live-wire
surfaced:  2026-07-01
what:      "MCP bridge for Ableton Live — control Live from Claude or any MCP client via a Max for Live proxy and the Ableton Extensions platform."
alive:     created within the Extensions SDK's first month, three days apart from ableton-sdk-mcp; commit/contributor/release detail unrecorded
why:       A second, independent implementation of the same MCP-over-Extensions-SDK idea as ableton-sdk-mcp. Two unrelated bridges appearing in the SDK's first month is a converging pattern, not a one-off — worth tracking as a precedent for however ASA eventually closes the advice-to-applied-change loop.
tags:      audio, ableton, extensions-sdk, mcp, m4l, bridge

## pnomolos/ableton-extensions-public
link:      https://github.com/pnomolos/ableton-extensions-public
surfaced:  2026-07-01
what:      Hobbyist Ableton Extensions-SDK project from the ecosystem that sprang up in the SDK's first month.
alive:     created 2026-06, mostly 0–25★ cohort; commit/contributor/release detail unrecorded
why:       Part of the ~45-repo Extensions-SDK hobbyist flood: individually hobby-scale MIDI/notation/sample utilities, real evidence the SDK ecosystem is alive, but none is a DSP-analysis tool worth a separate writeup. Logged in bulk so the next sweep doesn't re-triage them; the SDK itself is the actual finding, not any one extension.
tags:      audio, ableton, extensions-sdk, hobbyist, ecosystem

## pmelchior/scarlet
link:      https://github.com/pmelchior/scarlet
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## philipperemy/very-deep-convnets-raw-waveforms
link:      https://github.com/philipperemy/very-deep-convnets-raw-waveforms
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## paradigmn/ultrastar_pitch
link:      https://github.com/paradigmn/ultrastar_pitch
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## opensensorhub/osh-js
link:      https://github.com/opensensorhub/osh-js
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## NurMarvin/ableton-kick-tuner
link:      https://github.com/NurMarvin/ableton-kick-tuner
surfaced:  2026-07-01
what:      Hobbyist Ableton Extensions-SDK project from the ecosystem that sprang up in the SDK's first month.
alive:     created 2026-06, mostly 0–25★ cohort; commit/contributor/release detail unrecorded
why:       Part of the ~45-repo Extensions-SDK hobbyist flood: individually hobby-scale MIDI/notation/sample utilities, real evidence the SDK ecosystem is alive, but none is a DSP-analysis tool worth a separate writeup. Logged in bulk so the next sweep doesn't re-triage them; the SDK itself is the actual finding, not any one extension.
tags:      audio, ableton, extensions-sdk, hobbyist, tuning

## nils-werner/mdct
link:      https://github.com/nils-werner/mdct
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## muhammad-ahmed-ghani/svoice_demo
link:      https://github.com/muhammad-ahmed-ghani/svoice_demo
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## MTG/essentia.js
link:      https://github.com/MTG/essentia.js
surfaced:  2026-07-01
what:      The WASM/JavaScript build of Essentia for the browser.
alive:     849★; still active; commit/contributor/release detail unrecorded
why:       Explicitly off-stack per the audio-mir routine's standing correction: ASA is native Essentia, confirmed again on this run via its CLAUDE.md — not Essentia.js/WASM as the default path. Logged so it stops resurfacing as a "new" find. The one WASM exception ASA does have (`loudness-spectro-wasm`) is a bespoke in-house package, not this library.
tags:      audio, essentia, wasm, browser, off-stack

## MTG/da-tacos
link:      https://github.com/MTG/da-tacos
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## Mocha-Yuan/MoChord
link:      https://github.com/Mocha-Yuan/MoChord
surfaced:  2026-07-01
what:      AI-assisted guitar workspace: chord voicings, real-time tuner pitch detection, tabs, staff notation and playback (Tauri/React).
alive:     active 2026-06; commit/contributor/release detail unrecorded
why:       Guitar/tab-specific UI, not audio-file analysis — nothing for ASA's pipeline, but a fresh real-time-pitch-detection UX reference if Harmonia's substitutions panel ever grows a tuner/practice view.
tags:      audio, chord, guitar, tuner, tauri, react, ui

## MLAB-project/pysdr
link:      https://github.com/MLAB-project/pysdr
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## Minichain/EversongApp
link:      https://github.com/Minichain/EversongApp
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## mfcc64/youtube-musical-spectrum
link:      https://github.com/mfcc64/youtube-musical-spectrum
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## mfcc64/mpv-scripts
link:      https://github.com/mfcc64/mpv-scripts
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## meil-brcas-org/soundscape_IR
link:      https://github.com/meil-brcas-org/soundscape_IR
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## maum-ai/voicefilter
link:      https://github.com/maum-ai/voicefilter
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## Matt54/SwiftTuner
link:      https://github.com/Matt54/SwiftTuner
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## markusschloesser/MackieC4_P3
link:      https://github.com/markusschloesser/MackieC4_P3
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## maRce10/warbleR
link:      https://github.com/maRce10/warbleR
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## Maboroshy/Max-for-Live-Devices
link:      https://github.com/Maboroshy/Max-for-Live-Devices
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## m-kortas/Sound-based-bird-species-detection
link:      https://github.com/m-kortas/Sound-based-bird-species-detection
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## little-scale/little-scale-ableton-sdk-extensions
link:      https://github.com/little-scale/little-scale-ableton-sdk-extensions
surfaced:  2026-07-01
what:      Hobbyist Ableton Extensions-SDK project from the ecosystem that sprang up in the SDK's first month.
alive:     created 2026-06, mostly 0–25★ cohort; commit/contributor/release detail unrecorded
why:       Part of the ~45-repo Extensions-SDK hobbyist flood: individually hobby-scale MIDI/notation/sample utilities, real evidence the SDK ecosystem is alive, but none is a DSP-analysis tool worth a separate writeup. Logged in bulk so the next sweep doesn't re-triage them; the SDK itself is the actual finding, not any one extension.
tags:      audio, ableton, extensions-sdk, hobbyist, ecosystem

## libraz/bpm-detector
link:      https://github.com/libraz/bpm-detector
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## krantiparida/awesome-audio-visual
link:      https://github.com/krantiparida/awesome-audio-visual
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## Kory111111111111111111/yt-dlp-for-ableton
link:      https://github.com/Kory111111111111111111/yt-dlp-for-ableton
surfaced:  2026-07-01
what:      Hobbyist Ableton Extensions-SDK project from the ecosystem that sprang up in the SDK's first month.
alive:     created 2026-06, mostly 0–25★ cohort; commit/contributor/release detail unrecorded
why:       Part of the ~45-repo Extensions-SDK hobbyist flood: individually hobby-scale MIDI/notation/sample utilities, real evidence the SDK ecosystem is alive, but none is a DSP-analysis tool worth a separate writeup. Logged in bulk so the next sweep doesn't re-triage them; the SDK itself is the actual finding, not any one extension.
tags:      audio, ableton, extensions-sdk, hobbyist, ecosystem

## keunwoochoi/kapre
link:      https://github.com/keunwoochoi/kapre
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## kennethreitz/ableton-pytheory
link:      https://github.com/kennethreitz/ableton-pytheory
surfaced:  2026-07-01
what:      Hobbyist Ableton Extensions-SDK project from the ecosystem that sprang up in the SDK's first month.
alive:     created 2026-06, mostly 0–25★ cohort; commit/contributor/release detail unrecorded
why:       Part of the ~45-repo Extensions-SDK hobbyist flood: individually hobby-scale MIDI/notation/sample utilities, real evidence the SDK ecosystem is alive, but none is a DSP-analysis tool worth a separate writeup. Logged in bulk so the next sweep doesn't re-triage them; the SDK itself is the actual finding, not any one extension.
tags:      audio, ableton, extensions-sdk, hobbyist, theory

## kawana77b/midi-bpm-shift
link:      https://github.com/kawana77b/midi-bpm-shift
surfaced:  2026-07-01
what:      Hobbyist Ableton Extensions-SDK project from the ecosystem that sprang up in the SDK's first month.
alive:     created 2026-06, mostly 0–25★ cohort; commit/contributor/release detail unrecorded
why:       Part of the ~45-repo Extensions-SDK hobbyist flood: individually hobby-scale MIDI/notation/sample utilities, real evidence the SDK ecosystem is alive, but none is a DSP-analysis tool worth a separate writeup. Logged in bulk so the next sweep doesn't re-triage them; the SDK itself is the actual finding, not any one extension.
tags:      audio, ableton, extensions-sdk, hobbyist, midi, bpm

## JuliaDSP/DSP.jl
link:      https://github.com/JuliaDSP/DSP.jl
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## juanmartin/ClipSync
link:      https://github.com/juanmartin/ClipSync
surfaced:  2026-07-01
what:      Hobbyist Ableton Extensions-SDK project from the ecosystem that sprang up in the SDK's first month.
alive:     created 2026-06, mostly 0–25★ cohort; commit/contributor/release detail unrecorded
why:       Part of the ~45-repo Extensions-SDK hobbyist flood: individually hobby-scale MIDI/notation/sample utilities, real evidence the SDK ecosystem is alive, but none is a DSP-analysis tool worth a separate writeup. Logged in bulk so the next sweep doesn't re-triage them; the SDK itself is the actual finding, not any one extension.
tags:      audio, ableton, extensions-sdk, hobbyist, clips

## jonasfasching/ableton-extensions-sdk
link:      https://github.com/jonasfasching/ableton-extensions-sdk
surfaced:  2026-07-01
what:      Hobbyist Ableton Extensions-SDK project from the ecosystem that sprang up in the SDK's first month.
alive:     created 2026-06, mostly 0–25★ cohort; commit/contributor/release detail unrecorded
why:       Part of the ~45-repo Extensions-SDK hobbyist flood: individually hobby-scale MIDI/notation/sample utilities, real evidence the SDK ecosystem is alive, but none is a DSP-analysis tool worth a separate writeup. Logged in bulk so the next sweep doesn't re-triage them; the SDK itself is the actual finding, not any one extension.
tags:      audio, ableton, extensions-sdk, hobbyist, ecosystem

## jasper-zheng/ableton-sdk-mcp
link:      https://github.com/jasper-zheng/ableton-sdk-mcp
surfaced:  2026-07-01
what:      MCP server letting an LLM issue Ableton Extensions-SDK commands against a running Live set via TypeScript.
alive:     created within the Extensions SDK's first month (SDK beta opened 2026-06-02); commit/contributor/release detail unrecorded
why:       First public proof that "LLM reads a JSON analysis, decides what to change" — ASA's own Gemini-layer pattern — can be wired straight into Live instead of stopping at advice text. Read the tool-call surface it exposes before building ASA's own. Repo contents were unread at capture (GitHub access was search-only that session — flagged, not fabricated).
tags:      audio, ableton, extensions-sdk, mcp, llm, typescript

## jamiebullock/LibXtract
link:      https://github.com/jamiebullock/LibXtract
surfaced:  2026-07-01
what:      Long-standing portable C library of audio feature-extraction functions.
alive:     from 2012, not actively growing; commit/contributor/release detail unrecorded
why:       Not new and not actively growing, but a lighter-weight native alternative to specific Essentia extractors if a narrow feature is ever worth decoupling from the full Essentia dependency.
tags:      audio, native, c, features, lightweight

## isaacsight/kernel
link:      https://github.com/isaacsight/kernel
surfaced:  2026-07-01
what:      Hobbyist Ableton Extensions-SDK project from the ecosystem that sprang up in the SDK's first month.
alive:     created 2026-06, mostly 0–25★ cohort; commit/contributor/release detail unrecorded
why:       Part of the ~45-repo Extensions-SDK hobbyist flood: individually hobby-scale MIDI/notation/sample utilities, real evidence the SDK ecosystem is alive, but none is a DSP-analysis tool worth a separate writeup. Logged in bulk so the next sweep doesn't re-triage them; the SDK itself is the actual finding, not any one extension.
tags:      audio, ableton, extensions-sdk, hobbyist, ecosystem

## ImiteDev/ReverseVerb
link:      https://github.com/ImiteDev/ReverseVerb
surfaced:  2026-07-01
what:      "One-click reverse reverb swell for Ableton Live 12 (Extensions SDK). Offline DSP, right-click an audio clip."
alive:     created within the Extensions SDK's first month; commit/contributor/release detail unrecorded
why:       Small, but a concrete end-to-end reference for "packaged offline DSP as a Live Extension" — build, package, clip-level processing — the shape ASA's own recommendations could ship as if the Extensions-SDK spike pans out.
tags:      audio, ableton, extensions-sdk, offline-dsp, reverb

## hueypeard/akstretch
link:      https://github.com/hueypeard/akstretch
surfaced:  2026-07-01
what:      Hobbyist Ableton Extensions-SDK project from the ecosystem that sprang up in the SDK's first month.
alive:     created 2026-06, mostly 0–25★ cohort; commit/contributor/release detail unrecorded
why:       Part of the ~45-repo Extensions-SDK hobbyist flood: individually hobby-scale MIDI/notation/sample utilities, real evidence the SDK ecosystem is alive, but none is a DSP-analysis tool worth a separate writeup. Logged in bulk so the next sweep doesn't re-triage them; the SDK itself is the actual finding, not any one extension.
tags:      audio, ableton, extensions-sdk, hobbyist, timestretch

## himynameisfuego/SiTraNo
link:      https://github.com/himynameisfuego/SiTraNo
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## higedance/pictLense
link:      https://github.com/higedance/pictLense
surfaced:  2026-07-01
what:      Hobbyist Ableton Extensions-SDK project from the ecosystem that sprang up in the SDK's first month.
alive:     created 2026-06, mostly 0–25★ cohort; commit/contributor/release detail unrecorded
why:       Part of the ~45-repo Extensions-SDK hobbyist flood: individually hobby-scale MIDI/notation/sample utilities, real evidence the SDK ecosystem is alive, but none is a DSP-analysis tool worth a separate writeup. Logged in bulk so the next sweep doesn't re-triage them; the SDK itself is the actual finding, not any one extension.
tags:      audio, ableton, extensions-sdk, hobbyist, ecosystem

## google/speaker-id
link:      https://github.com/google/speaker-id
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## GianlucaPaolocci/Sound-classification-on-Raspberry-Pi-with-Tensorflow
link:      https://github.com/GianlucaPaolocci/Sound-classification-on-Raspberry-Pi-with-Tensorflow
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## fumiama/Retrieval-based-Voice-Conversion-WebUI
link:      https://github.com/fumiama/Retrieval-based-Voice-Conversion-WebUI
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## Frenzyz/neural-midi
link:      https://github.com/Frenzyz/neural-midi
surfaced:  2026-07-01
what:      Hobbyist Ableton Extensions-SDK project from the ecosystem that sprang up in the SDK's first month.
alive:     created 2026-06, mostly 0–25★ cohort; commit/contributor/release detail unrecorded
why:       Part of the ~45-repo Extensions-SDK hobbyist flood: individually hobby-scale MIDI/notation/sample utilities, real evidence the SDK ecosystem is alive, but none is a DSP-analysis tool worth a separate writeup. Logged in bulk so the next sweep doesn't re-triage them; the SDK itself is the actual finding, not any one extension.
tags:      audio, ableton, extensions-sdk, hobbyist, midi

## fgnt/pb_bss
link:      https://github.com/fgnt/pb_bss
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## FelixNgFender/mu2mi
link:      https://github.com/FelixNgFender/mu2mi
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## endolith/waveform-analysis
link:      https://github.com/endolith/waveform-analysis
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## edkashinsky/reaper-reableton-scripts
link:      https://github.com/edkashinsky/reaper-reableton-scripts
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## Eden-Kramer-Lab/spectral_connectivity
link:      https://github.com/Eden-Kramer-Lab/spectral_connectivity
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## echogarden-project/echogarden
link:      https://github.com/echogarden-project/echogarden
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## dsego/strobe-tuner
link:      https://github.com/dsego/strobe-tuner
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## dnvsfn/ableton-pocket-operations
link:      https://github.com/dnvsfn/ableton-pocket-operations
surfaced:  2026-07-01
what:      Hobbyist Ableton Extensions-SDK project from the ecosystem that sprang up in the SDK's first month.
alive:     created 2026-06, mostly 0–25★ cohort; commit/contributor/release detail unrecorded
why:       Part of the ~45-repo Extensions-SDK hobbyist flood: individually hobby-scale MIDI/notation/sample utilities, real evidence the SDK ecosystem is alive, but none is a DSP-analysis tool worth a separate writeup. Logged in bulk so the next sweep doesn't re-triage them; the SDK itself is the actual finding, not any one extension.
tags:      audio, ableton, extensions-sdk, hobbyist, ecosystem

## dnvsfn/ableton-midnight-tools
link:      https://github.com/dnvsfn/ableton-midnight-tools
surfaced:  2026-07-01
what:      Hobbyist Ableton Extensions-SDK project from the ecosystem that sprang up in the SDK's first month.
alive:     created 2026-06, mostly 0–25★ cohort; commit/contributor/release detail unrecorded
why:       Part of the ~45-repo Extensions-SDK hobbyist flood: individually hobby-scale MIDI/notation/sample utilities, real evidence the SDK ecosystem is alive, but none is a DSP-analysis tool worth a separate writeup. Logged in bulk so the next sweep doesn't re-triage them; the SDK itself is the actual finding, not any one extension.
tags:      audio, ableton, extensions-sdk, hobbyist, ecosystem

## derrickward/ChordRecGen
link:      https://github.com/derrickward/ChordRecGen
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## davidmartinrius/speech-dataset-generator
link:      https://github.com/davidmartinrius/speech-dataset-generator
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## danthompson41/Ableton-Extensions
link:      https://github.com/danthompson41/Ableton-Extensions
surfaced:  2026-07-01
what:      Hobbyist Ableton Extensions-SDK project from the ecosystem that sprang up in the SDK's first month.
alive:     created 2026-06, mostly 0–25★ cohort; commit/contributor/release detail unrecorded
why:       Part of the ~45-repo Extensions-SDK hobbyist flood: individually hobby-scale MIDI/notation/sample utilities, real evidence the SDK ecosystem is alive, but none is a DSP-analysis tool worth a separate writeup. Logged in bulk so the next sweep doesn't re-triage them; the SDK itself is the actual finding, not any one extension.
tags:      audio, ableton, extensions-sdk, hobbyist, ecosystem

## d00mfish/BPM-to-OSC
link:      https://github.com/d00mfish/BPM-to-OSC
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## christofw/pitchclass_mctc
link:      https://github.com/christofw/pitchclass_mctc
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## chris-arsenault/ableton-extensions
link:      https://github.com/chris-arsenault/ableton-extensions
surfaced:  2026-07-01
what:      Hobbyist Ableton Extensions-SDK project from the ecosystem that sprang up in the SDK's first month.
alive:     created 2026-06, mostly 0–25★ cohort; commit/contributor/release detail unrecorded
why:       Part of the ~45-repo Extensions-SDK hobbyist flood: individually hobby-scale MIDI/notation/sample utilities, real evidence the SDK ecosystem is alive, but none is a DSP-analysis tool worth a separate writeup. Logged in bulk so the next sweep doesn't re-triage them; the SDK itself is the actual finding, not any one extension.
tags:      audio, ableton, extensions-sdk, hobbyist, ecosystem

## charlesvestal/extending-move
link:      https://github.com/charlesvestal/extending-move
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## BrokenSource/ShaderFlow
link:      https://github.com/BrokenSource/ShaderFlow
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## borel119/Beat-Inspector
link:      https://github.com/borel119/Beat-Inspector
surfaced:  2026-07-01
what:      "A Beat Detective–style non-warping audio quantizer for Ableton Live."
alive:     created within the Extensions SDK's first month; commit/contributor/release detail unrecorded
why:       Timing correction, not analysis — adjacent rather than on-target for ASA's measurement layer — but another concrete example of audio-domain DSP shipped as an Extension.
tags:      audio, ableton, extensions-sdk, quantize, timing

## Boostem/SuperBeatMakerRPG-Ableton-Extension
link:      https://github.com/Boostem/SuperBeatMakerRPG-Ableton-Extension
surfaced:  2026-07-01
what:      Hobbyist Ableton Extensions-SDK project from the ecosystem that sprang up in the SDK's first month.
alive:     created 2026-06, mostly 0–25★ cohort; commit/contributor/release detail unrecorded
why:       Part of the ~45-repo Extensions-SDK hobbyist flood: individually hobby-scale MIDI/notation/sample utilities, real evidence the SDK ecosystem is alive, but none is a DSP-analysis tool worth a separate writeup. Logged in bulk so the next sweep doesn't re-triage them; the SDK itself is the actual finding, not any one extension.
tags:      audio, ableton, extensions-sdk, hobbyist, ecosystem

## bbye98/minim
link:      https://github.com/bbye98/minim
surfaced:  2026-07-01
what:      Metadata/tagging API wrapper.
alive:     commit/contributor/release detail unrecorded
why:       Neither DSP nor pipeline-relevant.
tags:      audio, metadata, api-wrapper, off-domain

## bassDaddyDevices/midi-daddy
link:      https://github.com/bassDaddyDevices/midi-daddy
surfaced:  2026-07-01
what:      Hobbyist Ableton Extensions-SDK project from the ecosystem that sprang up in the SDK's first month.
alive:     created 2026-06, mostly 0–25★ cohort; commit/contributor/release detail unrecorded
why:       Part of the ~45-repo Extensions-SDK hobbyist flood: individually hobby-scale MIDI/notation/sample utilities, real evidence the SDK ecosystem is alive, but none is a DSP-analysis tool worth a separate writeup. Logged in bulk so the next sweep doesn't re-triage them; the SDK itself is the actual finding, not any one extension.
tags:      audio, ableton, extensions-sdk, hobbyist, midi

## ava-gunn/minilogue-viewer
link:      https://github.com/ava-gunn/minilogue-viewer
surfaced:  2026-07-01
what:      Hobbyist Ableton Extensions-SDK project from the ecosystem that sprang up in the SDK's first month.
alive:     created 2026-06, mostly 0–25★ cohort; commit/contributor/release detail unrecorded
why:       Part of the ~45-repo Extensions-SDK hobbyist flood: individually hobby-scale MIDI/notation/sample utilities, real evidence the SDK ecosystem is alive, but none is a DSP-analysis tool worth a separate writeup. Logged in bulk so the next sweep doesn't re-triage them; the SDK itself is the actual finding, not any one extension.
tags:      audio, ableton, extensions-sdk, hobbyist, synth

## Austin-Imbastari/yoink
link:      https://github.com/Austin-Imbastari/yoink
surfaced:  2026-07-01
what:      Hobbyist Ableton Extensions-SDK project from the ecosystem that sprang up in the SDK's first month.
alive:     created 2026-06, mostly 0–25★ cohort; commit/contributor/release detail unrecorded
why:       Part of the ~45-repo Extensions-SDK hobbyist flood: individually hobby-scale MIDI/notation/sample utilities, real evidence the SDK ecosystem is alive, but none is a DSP-analysis tool worth a separate writeup. Logged in bulk so the next sweep doesn't re-triage them; the SDK itself is the actual finding, not any one extension.
tags:      audio, ableton, extensions-sdk, hobbyist, ecosystem

## audiomyweb/musslin-ableton-extensions-lab
link:      https://github.com/audiomyweb/musslin-ableton-extensions-lab
surfaced:  2026-07-01
what:      Hobbyist Ableton Extensions-SDK project from the ecosystem that sprang up in the SDK's first month.
alive:     created 2026-06, mostly 0–25★ cohort; commit/contributor/release detail unrecorded
why:       Part of the ~45-repo Extensions-SDK hobbyist flood: individually hobby-scale MIDI/notation/sample utilities, real evidence the SDK ecosystem is alive, but none is a DSP-analysis tool worth a separate writeup. Logged in bulk so the next sweep doesn't re-triage them; the SDK itself is the actual finding, not any one extension.
tags:      audio, ableton, extensions-sdk, hobbyist, ecosystem

## arulandu/chordy
link:      https://github.com/arulandu/chordy
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## ArminJo/Arduino-FrequencyDetector
link:      https://github.com/ArminJo/Arduino-FrequencyDetector
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## ankrypht/AudioScape
link:      https://github.com/ankrypht/AudioScape
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## alperensumeroglu/ai-clips-maker
link:      https://github.com/alperensumeroglu/ai-clips-maker
surfaced:  2026-07-01
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the audio-mir dedupe list on 2026-07-01 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      audio, dedupe-only, no-commentary, unassessed

## aker-dev/ableton-extension-skill
link:      https://github.com/aker-dev/ableton-extension-skill
surfaced:  2026-07-01
what:      Hobbyist Ableton Extensions-SDK project from the ecosystem that sprang up in the SDK's first month.
alive:     created 2026-06, mostly 0–25★ cohort; commit/contributor/release detail unrecorded
why:       Part of the ~45-repo Extensions-SDK hobbyist flood: individually hobby-scale MIDI/notation/sample utilities, real evidence the SDK ecosystem is alive, but none is a DSP-analysis tool worth a separate writeup. Logged in bulk so the next sweep doesn't re-triage them; the SDK itself is the actual finding, not any one extension.
tags:      audio, ableton, extensions-sdk, hobbyist, ecosystem

## adamjmurray/ableton-extensions-experiments
link:      https://github.com/adamjmurray/ableton-extensions-experiments
surfaced:  2026-07-01
what:      Hobbyist Ableton Extensions-SDK project from the ecosystem that sprang up in the SDK's first month.
alive:     created 2026-06, mostly 0–25★ cohort; commit/contributor/release detail unrecorded
why:       Part of the ~45-repo Extensions-SDK hobbyist flood: individually hobby-scale MIDI/notation/sample utilities, real evidence the SDK ecosystem is alive, but none is a DSP-analysis tool worth a separate writeup. Logged in bulk so the next sweep doesn't re-triage them; the SDK itself is the actual finding, not any one extension. Same author as producer-pal.
tags:      audio, ableton, extensions-sdk, hobbyist, ecosystem

## 23atomist/the-fnk
link:      https://github.com/23atomist/the-fnk
surfaced:  2026-07-01
what:      Hobbyist Ableton Extensions-SDK project from the ecosystem that sprang up in the SDK's first month.
alive:     created 2026-06, mostly 0–25★ cohort; commit/contributor/release detail unrecorded
why:       Part of the ~45-repo Extensions-SDK hobbyist flood: individually hobby-scale MIDI/notation/sample utilities, real evidence the SDK ecosystem is alive, but none is a DSP-analysis tool worth a separate writeup. Logged in bulk so the next sweep doesn't re-triage them; the SDK itself is the actual finding, not any one extension.
tags:      audio, ableton, extensions-sdk, hobbyist, ecosystem

## zafarrafii/Zaf-Python
link:      https://github.com/zafarrafii/Zaf-Python
surfaced:  2026-06-23
what:      Educational Jupyter notebooks for STFT, mel and chromagram.
alive:     commit/contributor/release detail unrecorded
why:       Reference material only.
tags:      audio, educational, stft, mel, chroma, notebooks

## worldveil/dejavu
link:      https://github.com/worldveil/dejavu
surfaced:  2026-06-23
what:      Audio fingerprinting in Python.
alive:     unmaintained; commit/contributor/release detail unrecorded
why:       Unmaintained and off-domain.
tags:      audio, fingerprinting, python, unmaintained

## tinytag/tinytag
link:      https://github.com/tinytag/tinytag
surfaced:  2026-06-23
what:      Audio file metadata reader.
alive:     commit/contributor/release detail unrecorded
why:       Not DSP/MIR.
tags:      audio, metadata, tags, off-domain

## samim23/polymath
link:      https://github.com/samim23/polymath
surfaced:  2026-06-23
what:      End-user ML tool to segment music libraries into samples.
alive:     commit/contributor/release detail unrecorded
why:       Overlaps ASA's features but is an app, not a library.
tags:      audio, segmentation, samples, app

## Samik081/beets-beatport4
link:      https://github.com/Samik081/beets-beatport4
surfaced:  2026-06-23
what:      Beatport metadata plugin for beets.
alive:     commit/contributor/release detail unrecorded
why:       Off-domain.
tags:      audio, metadata, beets, plugin, off-domain

## salu133445/muspy
link:      https://github.com/salu133445/muspy
surfaced:  2026-06-23
what:      Symbolic music toolkit.
alive:     commit/contributor/release detail unrecorded
why:       No audio DSP.
tags:      audio, symbolic, toolkit

## openvpi/SOME
link:      https://github.com/openvpi/SOME
surfaced:  2026-06-23
what:      Singing-Oriented MIDI Extractor: converts an isolated vocal track to quantized note-on/note-off MIDI with velocity estimates.
alive:     695★; Python/PyTorch; commit/contributor/release detail unrecorded
why:       In ASA's pipeline, Demucs produces the vocal stem and torchcrepe produces continuous F0; SOME bridges the gap to note-level MIDI segments, filling the melody transcription output that ASA doesn't currently produce.
tags:      audio, singing, midi, transcription, pytorch, melody

## MusicMoveArr/Datasets
link:      https://github.com/MusicMoveArr/Datasets
surfaced:  2026-06-23
what:      Music data / metadata datasets.
alive:     commit/contributor/release detail unrecorded
why:       Off-domain.
tags:      audio, metadata, dataset, off-domain

## MTG/mtg-jamendo-dataset
link:      https://github.com/MTG/mtg-jamendo-dataset
surfaced:  2026-06-23
what:      MTG's tagged music dataset.
alive:     commit/contributor/release detail unrecorded
why:       Training data, not a library.
tags:      audio, dataset, tagging, training-data

## misya11p/amt-apc
link:      https://github.com/misya11p/amt-apc
surfaced:  2026-06-23
what:      Fine-tuned automatic-music-transcription model for piano cover generation.
alive:     commit/contributor/release detail unrecorded
why:       Too niche.
tags:      audio, transcription, piano, niche

## mir-dataset-loaders/mirdata
link:      https://github.com/mir-dataset-loaders/mirdata
surfaced:  2026-06-23
what:      Python loaders for standard MIR research datasets (key/chord/beat ground-truth annotations).
alive:     commit/contributor/release detail unrecorded
why:       Standardized MIR dataset loader — useful for training/benchmarking but not ASA's analysis pipeline. Revisited on 07-01: not a runtime dependency, but the closest ready-made oracle set if ASA ever wants to benchmark its chord/key/beat stages against labelled data rather than only cross-checking against other tools (as the openmeters/soundscope loudness track already does).
tags:      audio, dataset, loaders, benchmark, ground-truth, oracle

## marcobn/musicntwrk
link:      https://github.com/marcobn/musicntwrk
surfaced:  2026-06-23
what:      Network analysis of musical pitch spaces.
alive:     commit/contributor/release detail unrecorded
why:       Research-only, no analysis pipeline relevance.
tags:      audio, research, network-analysis, pitch-space

## KAIST-MACLab/PyTSMod
link:      https://github.com/KAIST-MACLab/PyTSMod
surfaced:  2026-06-23
what:      Time-scale modification library.
alive:     commit/contributor/release detail unrecorded
why:       Time-scale modification only; off-domain for both projects.
tags:      audio, time-stretch, tsm, off-domain

## iver56/audiomentations
link:      https://github.com/iver56/audiomentations
surfaced:  2026-06-23
what:      Audio augmentation library for ML training.
alive:     commit/contributor/release detail unrecorded
why:       Not directly relevant to ASA's inference pipeline.
tags:      audio, augmentation, training, ml

## ina-foss/inaSpeechSegmenter
link:      https://github.com/ina-foss/inaSpeechSegmenter
surfaced:  2026-06-23
what:      Speech/music/noise segmentation.
alive:     commit/contributor/release detail unrecorded
why:       Speech-domain, not music analysis.
tags:      audio, speech, segmentation, off-domain

## dodiku/MixingBear
link:      https://github.com/dodiku/MixingBear
surfaced:  2026-06-23
what:      Beat-mixing app.
alive:     last real development 2018, stale; commit/contributor/release detail unrecorded
why:       Stale.
tags:      audio, beat-mixing, app, stale

## dodiku/AudioOwl
link:      https://github.com/dodiku/AudioOwl
surfaced:  2026-06-23
what:      RNN-based audio analysis app.
alive:     last real development 2018, stale; commit/contributor/release detail unrecorded
why:       Stale.
tags:      audio, rnn, analysis, stale

## cemfi/meico
link:      https://github.com/cemfi/meico
surfaced:  2026-06-23
what:      MEI/MIDI/WAV format converter.
alive:     commit/contributor/release detail unrecorded
why:       Off-domain.
tags:      audio, mei, midi, converter, off-domain

## carlosholivan/musicaiz
link:      https://github.com/carlosholivan/musicaiz
surfaced:  2026-06-23
what:      Symbolic music analysis framework.
alive:     commit/contributor/release detail unrecorded
why:       Audio-first features absent.
tags:      audio, symbolic, analysis-framework

## betmoar/tracklistify
link:      https://github.com/betmoar/tracklistify
surfaced:  2026-06-23
what:      DJ mix track identification via fingerprinting.
alive:     commit/contributor/release detail unrecorded
why:       Off-domain for ASA.
tags:      audio, fingerprinting, dj, identification

## aubio/aubio
link:      https://github.com/aubio/aubio
surfaced:  2026-06-23
what:      C/Python library for onset detection, pitch tracking, beat induction and tempo estimation.
alive:     3712★; commit/contributor/release detail unrecorded
why:       The standard alternative algorithm family alongside Essentia. Uses YIN pitch and its own HFC/HWD onset detectors, which have different bias/variance profiles from Essentia's equivalents. Was not in the dedupe list despite being a foundational tool; worth logging as a validation baseline for any ASA feature where the Essentia result looks suspect.
tags:      audio, native, c, onset, pitch, beat, tempo, baseline

## Anjok07/ultimatevocalremovergui
link:      https://github.com/Anjok07/ultimatevocalremovergui
surfaced:  2026-06-23
what:      UVR desktop GUI for vocal/stem removal.
alive:     commit/contributor/release detail unrecorded
why:       Demucs already covers ASA's separation needs, and this is an app not a library.
tags:      audio, separation, uvr, gui, app

## alexanderlerch/pyACA
link:      https://github.com/alexanderlerch/pyACA
surfaced:  2026-06-23
what:      Acoustic feature extraction reference implementation accompanying "An Introduction to Audio Content Analysis".
alive:     commit/contributor/release detail unrecorded
why:       Covered by Essentia/librosa in ASA's stack.
tags:      audio, features, reference, python, textbook

## adamstark/BTrack
link:      https://github.com/adamstark/BTrack
surfaced:  2026-06-23
what:      Real-time C++ beat tracker.
alive:     commit/contributor/release detail unrecorded
why:       beat_this already handles this better.
tags:      audio, beat, cpp, realtime

## tlecomte/friture
link:      https://github.com/tlecomte/friture
surfaced:  2026-06-16
what:      Desktop real-time spectrogram app.
alive:     commit/contributor/release detail unrecorded
why:       Different use case from ASA's canvas-based offline spectrogram.
tags:      audio, spectrogram, realtime, desktop-app

## SuperKogito/spafe
link:      https://github.com/SuperKogito/spafe
surfaced:  2026-06-16
what:      Acoustic feature extraction reference implementation.
alive:     commit/contributor/release detail unrecorded
why:       Covered by Essentia/librosa in ASA's stack.
tags:      audio, features, reference, python

## steven-ahfu/suno-to-ableton
link:      https://github.com/steven-ahfu/suno-to-ableton
surfaced:  2026-06-16
what:      Imports Suno-generated tracks into Ableton Live.
alive:     commit/contributor/release detail unrecorded
why:       Ableton tooling/workflow; doesn't touch audio analysis.
tags:      audio, ableton, suno, import

## stemrollerapp/stemroller
link:      https://github.com/stemrollerapp/stemroller
surfaced:  2026-06-16
what:      Desktop UI wrapper around Demucs stem separation.
alive:     commit/contributor/release detail unrecorded
why:       Demucs UI wrapper; no new DSP vs. what ASA already uses.
tags:      audio, separation, demucs, ui-wrapper

## spotify/basic-pitch
link:      https://github.com/spotify/basic-pitch
surfaced:  2026-06-16
what:      Spotify's polyphonic audio-to-MIDI converter with pitch-bend detection: a lightweight TF/CoreML model producing note events with onset, offset, pitch confidence and pitch bend from any audio file.
alive:     5179★; actively maintained; commit/contributor/release detail unrecorded
why:       ASA currently produces chords, beats and structure but no MIDI — basic-pitch fills that gap directly, and MIDI is the native currency of Ableton's clip/piano-roll workflow. It's the most direct bridge between Phase 1 measurements and actionable Ableton reconstruction advice.
tags:      audio, transcription, midi, polyphonic, pitch-bend, spotify

## sevagh/free-music-demixer
link:      https://github.com/sevagh/free-music-demixer
surfaced:  2026-06-16
what:      Browser-based Demucs demixing UI.
alive:     commit/contributor/release detail unrecorded
why:       Demucs UI wrapper; no new DSP vs. what ASA already uses.
tags:      audio, separation, demucs, browser, ui-wrapper

## Robert-K/splicerr
link:      https://github.com/Robert-K/splicerr
surfaced:  2026-06-16
what:      Splice sample-download utility.
alive:     commit/contributor/release detail unrecorded
why:       Ableton tooling/workflow; doesn't touch audio analysis.
tags:      audio, samples, splice, utility

## pruizlezcano/legato
link:      https://github.com/pruizlezcano/legato
surfaced:  2026-06-16
what:      Project manager for DAW sessions.
alive:     commit/contributor/release detail unrecorded
why:       Ableton tooling/workflow; doesn't touch audio analysis.
tags:      audio, daw, project-manager

## patryk-ku/spek-rs
link:      https://github.com/patryk-ku/spek-rs
surfaced:  2026-06-16
what:      Spectrum viewer in Rust.
alive:     commit/contributor/release detail unrecorded
why:       No library surface.
tags:      audio, rust, spectrum, viewer

## otonomee/streamstem
link:      https://github.com/otonomee/streamstem
surfaced:  2026-06-16
what:      UI wrapper around Demucs stem separation.
alive:     commit/contributor/release detail unrecorded
why:       Demucs UI wrapper; no new DSP vs. what ASA already uses.
tags:      audio, separation, demucs, ui-wrapper

## olilarkin/librosa.cpp
link:      https://github.com/olilarkin/librosa.cpp
surfaced:  2026-06-16
what:      C++17 port of librosa (mel spectrogram, beat tracking, pitch detection) with Swift Package Manager support and a WASM build.
alive:     47★; created 2026-04; commit/contributor/release detail unrecorded
why:       Marginal now — ASA uses Python librosa natively — but it's the closest reference if ASA ever needs a native-performance sidecar for spectral features (e.g. an Ableton Extension or Max for Live device that mirrors ASA's analysis).
tags:      audio, cpp, librosa-port, mel, beat, pitch, sidecar

## nussl/nussl
link:      https://github.com/nussl/nussl
surfaced:  2026-06-16
what:      Northwestern University source-separation library.
alive:     archived; no longer maintained; commit/contributor/release detail unrecorded
why:       Archived and no longer maintained.
tags:      audio, separation, archived, unmaintained

## Myuuiii/DAWPresence
link:      https://github.com/Myuuiii/DAWPresence
surfaced:  2026-06-16
what:      Discord Rich Presence integration for DAWs.
alive:     commit/contributor/release detail unrecorded
why:       Ableton tooling/workflow; doesn't touch audio analysis.
tags:      audio, daw, discord, presence

## Music-and-Culture-Technology-Lab/omnizart
link:      https://github.com/Music-and-Culture-Technology-Lab/omnizart
surfaced:  2026-06-16
what:      Python library for omniscient music transcription — piano, guitar, bass, drums, chords, beats, vocal melody — each a separate neural model, all callable via a shared CLI or Python API.
alive:     1912–1915★; Python/TF2; actively maintained through 2026; installable as a Python package; commit/contributor/release detail unrecorded
why:       Where basic-pitch gives polyphonic MIDI and all-in-one gives structure, omnizart adds instrument-specific transcription (drum hits, guitar tabs, bass lines) that ASA's current Demucs-based stem separation doesn't attempt. Its chord + beat modules parallel ASA's pipeline and can cross-validate. Plugin for completing the transcription→recommendation pipeline, and a realistic near-term action.
tags:      audio, transcription, midi, multi-instrument, chord, beat, tensorflow

## mjhydri/BeatNet
link:      https://github.com/mjhydri/BeatNet
surfaced:  2026-06-16
what:      Real-time joint beat, downbeat, tempo and meter tracker using CRNN + particle filtering (ISMIR 2021).
alive:     496★; Python/PyTorch; commit/contributor/release detail unrecorded
why:       The key addition over beat_this is meter detection (2/4, 3/4, 4/4) — which ASA doesn't currently emit but which directly informs Ableton's grid-snapping and clip warp recommendations. Could slot in as a post-beat step or parallel run alongside beat_this.
tags:      audio, beat, downbeat, meter, tempo, crnn, realtime

## mjhydri/1D-StateSpace
link:      https://github.com/mjhydri/1D-StateSpace
surfaced:  2026-06-16
what:      State-space beat/downbeat tracking (the earlier paper from BeatNet's author).
alive:     commit/contributor/release detail unrecorded
why:       Covered adequately by BeatNet — same author, earlier paper.
tags:      audio, beat, downbeat, state-space, superseded

## mir-aidj/all-in-one
link:      https://github.com/mir-aidj/all-in-one
surfaced:  2026-06-16
what:      Single-inference music structure analyzer that jointly estimates beats, downbeats, section boundaries (verse/chorus/bridge labels), chords and key from one PyTorch model pass.
alive:     784–788★; Python/PyTorch; actively maintained 2026; commit/contributor/release detail unrecorded
why:       ASA currently runs msaf, Essentia and beat_this separately for these tasks; all-in-one would replace or validate all of them with a unified, ISMIR-published model (ISMIR 2023). The multi-task framing also means cross-task consistency that sequential pipelines can't guarantee. It maps directly onto five of ASA's existing output fields at once, and is a source of section-boundary ground truth, which ASA currently leaves to a separate segmentation step.
tags:      audio, structure, beat, downbeat, chord, key, pytorch, ismir2023

## madisonrickert/ablevsep
link:      https://github.com/madisonrickert/ablevsep
surfaced:  2026-06-16
what:      Ableton Extension that sends a clip to MVSEP's hosted stem-separation models and returns stems inside Live.
alive:     created within the Extensions SDK's first month; commit/contributor/release detail unrecorded
why:       Conceptually overlaps ASA's own Demucs stem stage (cloud-model-in, stems-out) and is a concrete precedent for delivering a stem result as an in-DAW action instead of a download link.
tags:      audio, ableton, extensions-sdk, stem-separation, in-daw

## madisonrickert/ableton-sheet-music-extension
link:      https://github.com/madisonrickert/ableton-sheet-music-extension
surfaced:  2026-06-16
what:      Hobbyist Ableton Extensions-SDK project from the ecosystem that sprang up in the SDK's first month.
alive:     created 2026-06, mostly 0–25★ cohort; commit/contributor/release detail unrecorded
why:       Part of the ~45-repo Extensions-SDK hobbyist flood: individually hobby-scale MIDI/notation/sample utilities, real evidence the SDK ecosystem is alive, but none is a DSP-analysis tool worth a separate writeup. Logged in bulk so the next sweep doesn't re-triage them; the SDK itself is the actual finding, not any one extension.
tags:      audio, ableton, extensions-sdk, hobbyist, sheet-music

## luizen/als-tools
link:      https://github.com/luizen/als-tools
surfaced:  2026-06-16
what:      Tooling for reading and manipulating Ableton Live Set (`.als`) files.
alive:     commit/contributor/release detail unrecorded
why:       Ableton tooling/workflow; doesn't touch audio analysis.
tags:      audio, ableton, als, project-files

## ldrolez/clyphx-live11
link:      https://github.com/ldrolez/clyphx-live11
surfaced:  2026-06-16
what:      Mature ClyphX macro/scripting suite for Ableton Live.
alive:     from 2020, real and used; commit/contributor/release detail unrecorded
why:       Remote-Scripts paradigm, not the Extensions-SDK or DSP-analysis paradigm ASA needs — off-target.
tags:      audio, ableton, remote-scripts, macros

## lars76/swift-f0
link:      https://github.com/lars76/swift-f0
surfaced:  2026-06-16
what:      Fast, accurate F0 (fundamental frequency) detector using a lightweight CNN, with ONNX export for inference without PyTorch.
alive:     166★; created 2025; commit/contributor/release detail unrecorded
why:       ASA uses torchcrepe for melody/F0; swift-f0 is a lighter alternative with competitive accuracy and a smaller runtime footprint, useful if torchcrepe becomes a bottleneck or if ASA needs to run F0 in a lighter deployment.
tags:      audio, pitch, f0, cnn, onnx, lightweight

## kwatcharasupat/query-bandit
link:      https://github.com/kwatcharasupat/query-bandit
surfaced:  2026-06-16
what:      Query-conditioned stem separation that goes beyond the fixed 4-stem (vocals/drums/bass/other) schema — pass a text or audio query and the model extracts that custom stem.
alive:     100★; ISMIR 2024; commit/contributor/release detail unrecorded
why:       ASA uses Demucs's fixed schema; Banquet's query-based approach would let ASA isolate e.g. "lead synth" or "room reverb tail" — information that maps directly to per-element Ableton reconstruction advice.
tags:      audio, separation, query-conditioned, ismir2024, stems

## KinWaiCheuk/nnAudio
link:      https://github.com/KinWaiCheuk/nnAudio
surfaced:  2026-06-16
what:      PyTorch 1D convolution network layers that compute mel spectrograms, CQT, STFT and other time-frequency representations entirely on GPU, as `nn.Module` layers that live in the computation graph.
alive:     1126★; commit/contributor/release detail unrecorded
why:       ASA is already PyTorch; replacing librosa's CPU-bound spectrogram math with nnAudio means spectrogram computation benefits from GPU batching and can be differentiated through. Especially relevant to the canvas-based mel spectrogram and any future model that takes raw mel input.
tags:      audio, pytorch, gpu, mel, cqt, stft, differentiable

## junyuchen-cjy/DTTNet-Pytorch
link:      https://github.com/junyuchen-cjy/DTTNet-Pytorch
surfaced:  2026-06-16
what:      PyTorch implementation of the DTTNet source-separation model.
alive:     commit/contributor/release detail unrecorded
why:       Deferred in favour of query-bandit's practical flexibility.
tags:      audio, separation, dttnet, pytorch

## hqrrr/PerceptoMap
link:      https://github.com/hqrrr/PerceptoMap
surfaced:  2026-06-16
what:      VST3 plugin doing psychoacoustic mel/MFCC display.
alive:     commit/contributor/release detail unrecorded
why:       Off-stack.
tags:      audio, vst3, psychoacoustic, mel, mfcc, plugin

## hidingwill/AbletonBridge
link:      https://github.com/hidingwill/AbletonBridge
surfaced:  2026-06-16
what:      Hobbyist Ableton Extensions-SDK project from the ecosystem that sprang up in the SDK's first month.
alive:     created 2026-06, mostly 0–25★ cohort; commit/contributor/release detail unrecorded
why:       Part of the ~45-repo Extensions-SDK hobbyist flood: individually hobby-scale MIDI/notation/sample utilities, real evidence the SDK ecosystem is alive, but none is a DSP-analysis tool worth a separate writeup. Logged in bulk so the next sweep doesn't re-triage them; the SDK itself is the actual finding, not any one extension.
tags:      audio, ableton, extensions-sdk, hobbyist, ecosystem

## FunAudioLLM/SenseVoice
link:      https://github.com/FunAudioLLM/SenseVoice
surfaced:  2026-06-16
what:      Speech+audio understanding model: ASR + emotion recognition + audio event detection across 50+ languages, 15× faster than Whisper.
alive:     8588★; commit/contributor/release detail unrecorded
why:       Not music-specific (it flags speech emotion and sound events, not musical key or chords), but its audio-event-detection head (dog bark, siren, applause, etc.) is directly relevant to ASA's LLM interpretation layer if the project ever wants to classify non-musical content within a track or identify intro/outro texture events.
tags:      audio, asr, event-detection, emotion, speech, understanding

## Eomys/MoSQITo
link:      https://github.com/Eomys/MoSQITo
surfaced:  2026-06-16
what:      Psychoacoustic sound-quality metrics (roughness, fluctuation strength).
alive:     commit/contributor/release detail unrecorded
why:       Niche and not in ASA's analysis scope.
tags:      audio, psychoacoustic, sound-quality, metrics

## cycfi/q
link:      https://github.com/cycfi/q
surfaced:  2026-06-16
what:      C++20 DSP library with pitch tracking (MIDI-linked oscillators), effects and a signal-processing DSL based on function composition.
alive:     1394★; commit/contributor/release detail unrecorded
why:       Off-stack for ASA's Python backend but a strong C++ DSP reference if ASA ever gains a native sidecar (e.g. an Ableton Extension that runs local inference). Pitch tracking and onset algorithms are readable reference implementations.
tags:      audio, cpp, dsp, pitch, dsl, sidecar

## CPJKU/madmom
link:      https://github.com/CPJKU/madmom
surfaced:  2026-06-16
what:      Python audio signal processing library from the JKU research group: RNN/CNN beat/downbeat tracking, onset detection, key estimation and chord recognition, many with pre-trained neural models.
alive:     1660–1663★; Python/Cython, Cython-optimized for throughput; commit/contributor/release detail unrecorded
why:       CPJKU also makes beat_this (already in ASA's stack); madmom is the older, broader library and its chord HMM and onset models complement what Essentia provides. Direct peer/alternative for ASA's temporal analysis — the upstream codebase from which beat_this and partitura were later factored out. Since ASA already depends on two CPJKU repos, madmom is the natural next layer for any feature where a second algorithm opinion would improve robustness.
tags:      audio, beat, downbeat, onset, key, chord, cython, upstream

## cjbayron/autochord
link:      https://github.com/cjbayron/autochord
surfaced:  2026-06-16
what:      Automatic chord recognition (ISMIR 2021 Late-Breaking Demo): CRNN producing timestamped Harte-notation chord labels from audio.
alive:     161★; commit/contributor/release detail unrecorded
why:       Complements ASA's existing chord detection; consonance-ACE (already logged) is the stronger modern model, but autochord is a simpler drop-in for testing chord pipelines.
tags:      audio, chord, crnn, harte, ismir2021

## bencodec/BBenCut
link:      https://github.com/bencodec/BBenCut
surfaced:  2026-06-16
what:      Hobbyist Ableton Extensions-SDK project from the ecosystem that sprang up in the SDK's first month.
alive:     created 2026-06, mostly 0–25★ cohort; commit/contributor/release detail unrecorded
why:       Part of the ~45-repo Extensions-SDK hobbyist flood: individually hobby-scale MIDI/notation/sample utilities, real evidence the SDK ecosystem is alive, but none is a DSP-analysis tool worth a separate writeup. Logged in bulk so the next sweep doesn't re-triage them; the SDK itself is the actual finding, not any one extension.
tags:      audio, ableton, extensions-sdk, hobbyist, ecosystem

## ascpixi/splicedd
link:      https://github.com/ascpixi/splicedd
surfaced:  2026-06-16
what:      Splice sample-download utility.
alive:     commit/contributor/release detail unrecorded
why:       Ableton tooling/workflow; doesn't touch audio analysis.
tags:      audio, samples, splice, utility

## amydevs/AbletonLiveThemeConverter
link:      https://github.com/amydevs/AbletonLiveThemeConverter
surfaced:  2026-06-16
what:      Converter for Ableton Live theme files.
alive:     commit/contributor/release detail unrecorded
why:       Ableton tooling/workflow; doesn't touch audio analysis.
tags:      audio, ableton, themes, utility

## amanteur/SCNet-PyTorch
link:      https://github.com/amanteur/SCNet-PyTorch
surfaced:  2026-06-16
what:      PyTorch implementation of the SCNet source-separation model.
alive:     commit/contributor/release detail unrecorded
why:       Deferred in favour of query-bandit's practical flexibility.
tags:      audio, separation, scnet, pytorch

## amanteur/BandSplitRNN-PyTorch
link:      https://github.com/amanteur/BandSplitRNN-PyTorch
surfaced:  2026-06-16
what:      PyTorch implementation of the Band-Split RNN source-separation model.
alive:     commit/contributor/release detail unrecorded
why:       Deferred in favour of query-bandit's practical flexibility.
tags:      audio, separation, band-split, rnn, pytorch

## aiXander/Realtime_PyAudio_FFT
link:      https://github.com/aiXander/Realtime_PyAudio_FFT
surfaced:  2026-06-16
what:      Streams audio features over OSC in real time.
alive:     commit/contributor/release detail unrecorded
why:       A readable reference for streaming extraction but not a library ASA would import.
tags:      audio, realtime, fft, osc, streaming

## Vasallo94/ObsidianRAG
link:      https://github.com/Vasallo94/ObsidianRAG
surfaced:  2026-06-10
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the legaltech-nz dedupe list on 2026-06-10 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      legal, dedupe-only, no-commentary, unassessed

## raphasouthall/neurostack
link:      https://github.com/raphasouthall/neurostack
surfaced:  2026-06-10
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the legaltech-nz dedupe list on 2026-06-10 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      legal, dedupe-only, no-commentary, unassessed

## Papyrine/MsOfficeDiff
link:      https://github.com/Papyrine/MsOfficeDiff
surfaced:  2026-06-10
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the legaltech-nz dedupe list on 2026-06-10 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      legal, dedupe-only, no-commentary, unassessed

## DuckTapeKiller/ollama-pi-chat
link:      https://github.com/DuckTapeKiller/ollama-pi-chat
surfaced:  2026-06-10
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the legaltech-nz dedupe list on 2026-06-10 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      legal, dedupe-only, no-commentary, unassessed

## arthurpanhku/DocSentinel
link:      https://github.com/arthurpanhku/DocSentinel
surfaced:  2026-06-10
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the legaltech-nz dedupe list on 2026-06-10 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      legal, dedupe-only, no-commentary, unassessed

## apg6390/myLocalKb
link:      https://github.com/apg6390/myLocalKb
surfaced:  2026-06-10
what:      Surfaced by a sweep and recorded in the dedupe list; no description was written down at capture.
alive:     no liveness data recorded at capture
why:       Logged to the legaltech-nz dedupe list on 2026-06-10 so it would not resurface, but the sweep wrote no commentary for it. Carried across so the record stays complete — the absence of a write-up is the only thing known about it, and is not a judgement on the repo. Re-triage from scratch if it comes up again.
tags:      legal, dedupe-only, no-commentary, unassessed

## svsdval/video2midi
link:      https://github.com/svsdval/video2midi
surfaced:  2026-06-04
what:      Synthesia-video→MIDI converter by frame-by-frame computer vision on a keyboard overlay.
alive:     356★; Python; commit/contributor/release detail unrecorded
why:       MIDI *output*, but the input is video CV, not audio DSP/MIR — off-pipeline for ASA.
tags:      audio, midi, computer-vision, video, off-pipeline

## supercollider/supercollider
link:      https://github.com/supercollider/supercollider
surfaced:  2026-06-04
what:      Venerable audio server / language / IDE for synthesis and algorithmic composition.
alive:     6.6k★; C++; commit/contributor/release detail unrecorded
why:       ASA does analysis, not synthesis; famous but off-target.
tags:      audio, synthesis, livecoding, cpp, off-target

## stephenhandley/DrumMachinePatterns
link:      https://github.com/stephenhandley/DrumMachinePatterns
surfaced:  2026-06-04
what:      Static dataset of the "200/260 Drum Machine Patterns" books as JS data.
alive:     JS; commit/contributor/release detail unrecorded
why:       Symbolic drum data, no analysis or chord theory.
tags:      audio, drums, dataset, symbolic, js

## spite/WebAudioExtension
link:      https://github.com/spite/WebAudioExtension
surfaced:  2026-06-04
what:      Chrome DevTools panel for visualising Web Audio API routing graphs.
alive:     dormant since 2015; JS; commit/contributor/release detail unrecorded
why:       A browser-dev debug tool, not MIR/analysis.
tags:      audio, webaudio, devtools, browser, dormant

## slittycode/routine-discoveries
link:      https://github.com/slittycode/routine-discoveries
surfaced:  2026-06-04
what:      This very repository — the discovery log itself.
alive:     commit/contributor/release detail unrecorded
why:       Appeared in the hand-supplied starred list and was noted as out of stream, not evaluated.
tags:      meta, self-reference, out-of-stream

## RyoK3N/Akai_MPC_25
link:      https://github.com/RyoK3N/Akai_MPC_25
surfaced:  2026-06-04
what:      Live MIDI-controller and MP3/YouTube playback rig.
alive:     1★; Python; commit/contributor/release detail unrecorded
why:       Performance tooling, no MIR.
tags:      audio, midi, controller, performance

## pbakaus/impeccable
link:      https://github.com/pbakaus/impeccable
surfaced:  2026-06-04
what:      A design-language for AI harnesses.
alive:     commit/contributor/release detail unrecorded
why:       Not audio at all — surfaced in the hand-supplied starred batch and noted as out of stream, not evaluated.
tags:      design, ai-harness, out-of-stream, not-audio

## Omodaka9375/MIDIfren
link:      https://github.com/Omodaka9375/MIDIfren
surfaced:  2026-06-04
what:      Pure-Python audio→MIDI processor (CLI and web UI) doing stem separation (vocals/melody/drums/bass), BPM detection, grid quantization, pitch-bend detection, and silence trim/normalise across wav/mp3/flac.
alive:     commit/contributor/release detail unrecorded
why:       Sits squarely on ASA's server-side stack and covers several stages ASA already runs (stems, BPM, melody→MIDI), so it's a concrete reference for the audio→symbolic conversion ASA's JSON stops short of emitting.
tags:      audio, midi, stems, bpm, quantize, python, transcription

## meyda/meyda
link:      https://github.com/meyda/meyda
surfaced:  2026-06-04
what:      JavaScript audio feature extraction library.
alive:     commit/contributor/release detail unrecorded
why:       Wrong stack — ASA is server-side Python.
tags:      audio, js, features, off-stack

## justinsalamon/audio_to_midi_melodia
link:      https://github.com/justinsalamon/audio_to_midi_melodia
surfaced:  2026-06-04
what:      Melody-extraction→MIDI tool built on the classic Melodia pitch-contour algorithm plus a note-segmentation pass (also exports JAMS).
alive:     Python 2.7, last touched 2019; leans on the proprietary Melodia Vamp plugin; commit/contributor/release detail unrecorded
why:       A foundational MIR reference for the melody→note-segmentation step, but it's algorithm/lineage reading, not liftable code (ASA already does melody via torchcrepe).
tags:      audio, melody, midi, melodia, segmentation, lineage

## jonas-nothnagel/drum-beat-extractor
link:      https://github.com/jonas-nothnagel/drum-beat-extractor
surfaced:  2026-06-04
what:      Single-script Python tool that extracts MIDI drum patterns from audio files.
alive:     3★; one script, minimal docs; commit/contributor/release detail unrecorded
why:       On-stack and on-topic for ASA's rhythm/onset side, but thin — worth a skim as a compact onset→MIDI recipe rather than a dependency, and clearly outclassed by MiDiMe/MIDIfren.
tags:      audio, drums, onset, midi, python, thin

## jdez23/MiDiMe
link:      https://github.com/jdez23/MiDiMe
surfaced:  2026-06-04
what:      Full-stack drum-pattern extractor: a Django backend runs Demucs v4 stem separation (with a frequency-band fallback) + onset detection + grid quantization, and a React frontend shows waveforms and an editable step sequencer before MIDI export.
alive:     updated 2026-04; explicitly "no client-side audio processing"; commit/contributor/release detail unrecorded
why:       Almost a scale model of ASA's own architecture (server-side Python analysis on Demucs + a React UI), so it's the most useful reference in the batch for the analysis-job → React-visualisation contract, even if the MIR itself is narrower than ASA's.
tags:      audio, demucs, onset, quantize, midi, django, react, architecture

## gvellut/dmp_midi
link:      https://github.com/gvellut/dmp_midi
surfaced:  2026-06-04
what:      Static converter of the "200/260 Drum Machine Patterns" books into MIDI.
alive:     54★; Python; commit/contributor/release detail unrecorded
why:       Symbolic drum data, no analysis or chord theory.
tags:      audio, drums, midi, dataset, symbolic

## echolevel/Acid-Injector
link:      https://github.com/echolevel/Acid-Injector
surfaced:  2026-06-04
what:      In-browser converter of STING M4L MIDI clips to Behringer Synthtribe `.seq` / `.syx` sysex for a TD-3.
alive:     JS; commit/contributor/release detail unrecorded
why:       Niche hardware-format plumbing; neither analysis nor chords.
tags:      audio, sysex, hardware, midi, niche

## danryland/groove-ai
link:      https://github.com/danryland/groove-ai
surfaced:  2026-06-04
what:      GPT-3.5 generates drum grooves with MIDI export.
alive:     Vue / cloud Supabase stack; commit/contributor/release detail unrecorded
why:       ASA's LLM layer interprets measured analysis into Ableton recommendations; this is prompt→generation, the opposite direction, and on a cloud Vue/Supabase stack.
tags:      audio, generation, drums, midi, llm, vue

## AxelCurso/youtube2midi
link:      https://github.com/AxelCurso/youtube2midi
surfaced:  2026-06-04
what:      YouTube-audio→MIDI wrapper.
alive:     1★; thin, undocumented; commit/contributor/release detail unrecorded
why:       Nothing to learn next to MIDIfren.
tags:      audio, midi, youtube, wrapper, thin

## XIAODUOLU/Midra
link:      https://github.com/XIAODUOLU/Midra
surfaced:  2026-06-03
what:      Niche prompt-to-MIDI / controllable-generation research repo.
alive:     commit/contributor/release detail unrecorded
why:       Off-target for ASA analysis and Harmonia reharmonization.
tags:      audio, generation, midi, research, niche

## UseJunior/safe-docx
link:      https://github.com/UseJunior/safe-docx
surfaced:  2026-06-03
what:      TypeScript suite of `docx-primitives` plus a deterministic `docx-comparison` engine (with an optional MCP wrapper) doing surgical text replacement, comment/footnote workflows and revision extraction as structured JSON, with ECMA-376 conformance and NDA/partnership/LOI fixtures.
alive:     runs entirely locally, no document content leaving the machine; commit/contributor/release detail unrecorded
why:       The cleanest no-AI base for a compare-and-revise tool — fork the comparison engine, ignore the MCP layer. Newly surfaced by the deterministic-first queries that v1's AI-heavy query set couldn't see. Local-first: yes.
tags:      legal, docx, ooxml, deterministic, comparison, ecma-376, typescript

## thecolab-ai/.skills
link:      https://github.com/thecolab-ai/.skills
surfaced:  2026-06-03
what:      Community-contributed AI "skills" for NZ public data — LINZ, Stats NZ, Auckland Transport, weather and more.
alive:     commit/contributor/release detail unrecorded
why:       Mine it for ready-made access patterns to NZ open datasets (LINZ titles/parcels are directly property-relevant) and fork the skills he needs into his own agent — the underlying access is deterministic regardless of the AI packaging. Local-first: yes.
tags:      legal, nz, linz, open-data, skills, stats-nz

## Sysmagine/SemanticDiff
link:      https://github.com/Sysmagine/SemanticDiff
surfaced:  2026-06-03
what:      Programming-language-aware diff with a side-by-side review UI for VS Code/GitHub.
alive:     an editor/host extension; commit/contributor/release detail unrecorded
why:       The textbook "code-review UI repurposed for prose" wildcard. Mine its change-classification + review-UI approach to build a clause-change reviewer that hides cosmetic edits and foregrounds substantive ones in a redline. Kept for the angle. Local-first: partial.
tags:      legal, semantic-diff, review-ui, change-classification, wildcard

## swarmclawai/swarmvault
link:      https://github.com/swarmclawai/swarmvault
surfaced:  2026-06-03
what:      Local-first "LLM wiki" — a knowledge-graph builder, RAG knowledge base and agent-memory store positioned as an Obsidian alternative, with an MCP server.
alive:     commit/contributor/release detail unrecorded
why:       Fork it as a personal matter/precedent knowledge base whose graph links clauses, parties and precedents and that any local LLM can query. Dropped on the deterministic-first re-run as a generic AI-first "LLM wiki" / agent memory failing the AI-share cap and thin-wrapper rule. Local-first: yes.
tags:      legal, knowledge-graph, rag, pkm, mcp, agent-memory

## super-productivity/super-productivity
link:      https://github.com/super-productivity/super-productivity
surfaced:  2026-06-03
what:      Mature local-first todo app with integrated timeboxing and time tracking.
alive:     20k★; Electron/web; no AI; commit/contributor/release detail unrecorded
why:       Exactly the kind of deterministic personal-productivity tool v1's AI-leaning routine filtered out — fork it for personal matter/time tracking without rebuilding the scaffolding. Local-first: yes.
tags:      legal, todo, time-tracking, timeboxing, electron, deterministic

## SNU-LIST/chi-separation
link:      https://github.com/SNU-LIST/chi-separation
surfaced:  2026-06-03
what:      Magnetic-susceptibility "source separation" for MRI.
alive:     commit/contributor/release detail unrecorded
why:       Surfaced on the source-separation keyword; off-domain.
tags:      audio, false-positive, mri, off-domain

## russellbrenner/auslaw-mcp
link:      https://github.com/russellbrenner/auslaw-mcp
surfaced:  2026-06-03
what:      MCP server for Australian and New Zealand legal research: searches AustLII for case law and legislation, retrieves full-text judgments with paragraph numbers preserved, OCRs scanned PDFs (Tesseract), extracts neutral citations and formats to AGLC4.
alive:     runs locally via npm/Docker; commit/contributor/release detail unrecorded
why:       The most on-point NZ find — fork it to give a local AI assistant grounded NZ/AU case-law and legislation lookup. The substance (search/retrieval/OCR/citation) is deterministic and useful without any AI. Local-first: yes.
tags:      legal, nz, australia, austlii, case-law, mcp, ocr, citations

## OpenMOSS/MOSS-Audio
link:      https://github.com/OpenMOSS/MOSS-Audio
surfaced:  2026-06-03
what:      Open-source audio-understanding foundation model (4B/8B, Instruct + Thinking variants) covering music understanding, audio captioning, time-aware QA and multi-hop reasoning over audio.
alive:     weights on HF/ModelScope; runs via `infer.py` / Gradio / SGLang; commit/contributor/release detail unrecorded
why:       The broader sibling of MOSS-Music and the same story for ASA's Gemini layer: a self-hostable model that produces exactly the kind of LLM-interpreted, timestamp-aligned analysis ASA currently outsources to Gemini, so it's a serious reference (or partial in-house replacement) for that layer.
tags:      audio, audio-llm, understanding, foundation-model, captioning, self-hostable

## olilarkin/paulstretch-for-live
link:      https://github.com/olilarkin/paulstretch-for-live
surfaced:  2026-06-03
what:      Paulstretch extreme time-stretching packaged for Ableton Live.
alive:     commit/contributor/release detail unrecorded
why:       Ableton tooling/workflow; doesn't touch audio analysis. Dropped again in the 06-03 sweep as "too thin" and re-confirmed on 07-01.
tags:      audio, ableton, timestretch, paulstretch

## Nebutra/MinerU-Skill
link:      https://github.com/Nebutra/MinerU-Skill
surfaced:  2026-06-03
what:      Zero-dependency CLI (and Claude Code skill) wrapping MinerU to turn PDF/Office/images into clean Markdown with preserved tables, LaTeX and OCR.
alive:     commit/contributor/release detail unrecorded
why:       A higher-fidelity alternative ingestion path when layout matters (tables, schedules in a lease) — fork it for the cases where liteparse's plain text loses the structure. Local-first: partial (runs local VLM/OCR models).
tags:      legal, parser, pdf, markdown, tables, ocr, mineru

## Metacreation-Lab/MIDI-GPT
link:      https://github.com/Metacreation-Lab/MIDI-GPT
surfaced:  2026-06-03
what:      GPT-2 for symbolic music generation.
alive:     commit/contributor/release detail unrecorded
why:       Generation-only, not analysis.
tags:      audio, symbolic, generation, gpt

## matzalazar/rhizome
link:      https://github.com/matzalazar/rhizome
surfaced:  2026-06-03
what:      Local-first semantic-backlinks tool for Obsidian/Logseq that embeds notes with a multilingual sentence-transformer via ONNX and writes "## Related Notes" wikilink sections — no cloud API, no database, no LLM.
alive:     commit/contributor/release detail unrecorded
why:       Fork the embed-and-link engine to auto-surface related matters, precedents or clauses across his note vault entirely offline. Local-first: yes.
tags:      legal, embeddings, backlinks, obsidian, onnx, offline

## kreuzberg-dev/html-to-markdown
link:      https://github.com/kreuzberg-dev/html-to-markdown
surfaced:  2026-06-03
what:      Fast, CommonMark-compliant HTML→Markdown converter from the Kreuzberg document-intelligence team.
alive:     750★; Rust-backed; commit/contributor/release detail unrecorded
why:       The clean conversion primitive for web-clipping legislation, case-law pages or council/LINZ portals into Markdown his other tools can ingest — a small, dependable building block rather than an app. Local-first: yes.
tags:      legal, html, markdown, converter, primitive, rust

## kako-jun/diffx
link:      https://github.com/kako-jun/diffx
surfaced:  2026-06-03
what:      Structured-data semantic diff tool.
alive:     commit/contributor/release detail unrecorded
why:       Cut for redundancy on the deterministic-first re-run — overlaps graphtage.
tags:      legal, semantic-diff, structured-data, redundant

## Hashevolution/James-RAG-Evol
link:      https://github.com/Hashevolution/James-RAG-Evol
surfaced:  2026-06-03
what:      Local-first (Ollama) replayable Graph-RAG with an append-only audit log and an LLM-free deterministic 4-rule contradiction-arbitration decision tree.
alive:     research-grade; v0.4.1; commit/contributor/release detail unrecorded
why:       Fork that arbitration engine to build a single-document consistency checker that flags contradictory defined terms, conflicting dates and broken cross-references across a long agreement — deterministically, not by asking an LLM to "spot contradictions." Kept for the angle. Local-first: yes.
tags:      legal, graph-rag, contradiction, deterministic, audit-log, consistency, wildcard

## Griffinfloexalt/Suno-AI-Pro-cracked
link:      https://github.com/Griffinfloexalt/Suno-AI-Pro-cracked
surfaced:  2026-06-03
what:      Listing presenting itself as cracked Suno AI Pro.
alive:     commit/contributor/release detail unrecorded
why:       Excluded as keyword-spam / pirated-software listing, not a real repo.
tags:      audio, keyword-spam, pirated, excluded

## gmickel/gno
link:      https://github.com/gmickel/gno
surfaced:  2026-06-03
what:      Fully-offline local-first document-intelligence engine (Bun/TS) doing hybrid retrieval (BM25 + embeddings + cross-encoder rerank) with grounded, cited answers over notes, code, PDFs and Office docs, exposed via CLI, Web UI and MCP, using embedded Qwen models.
alive:     commit/contributor/release detail unrecorded
why:       A near-complete "chat with my matter files, offline, with citations" tool — fork it and point it at a matter folder. Kept on the deterministic-first re-run despite the LLM layer because the engine is real and deterministic. Local-first: yes.
tags:      legal, rag, offline, hybrid-retrieval, bm25, citations, qwen

## federico-pepe/ableton-live-extensions
link:      https://github.com/federico-pepe/ableton-live-extensions
surfaced:  2026-06-03
what:      Ableton Live Extensions collection.
alive:     commit/contributor/release detail unrecorded
why:       Ableton tooling/workflow; doesn't touch audio analysis. Dropped in the 06-03 sweep as "not analysis" and re-confirmed on 07-01.
tags:      audio, ableton, extensions-sdk, workflow

## Evilander/logic2ableton
link:      https://github.com/Evilander/logic2ableton
surfaced:  2026-06-03
what:      Reverse-engineered converter that reads Logic projects and reconstructs Ableton `.als` sets (audio placement, tempo, time signatures, MIDI), and the reverse, with VST3 plugin suggestions emitted in the conversion report.
alive:     Python + a TS desktop app; PyPI-packaged; v2.0.3; commit/contributor/release detail unrecorded
why:       For ASA the value is the working `.als`-writing code path: if ASA ever wants to emit a starter Live set or device chain from its recommendations, this is a concrete model for producing a valid `.als`.
tags:      audio, ableton, als, logic, converter, project-files

## ERDOGAN064/FineReader-Pro-OCR-Edition
link:      https://github.com/ERDOGAN064/FineReader-Pro-OCR-Edition
surfaced:  2026-06-03
what:      Listing presenting itself as ABBYY FineReader Pro OCR Edition.
alive:     commit/contributor/release detail unrecorded
why:       Excluded as keyword-spam / pirated-software listing.
tags:      legal, pirated, keyword-spam, excluded

## edithatogo/nz-legislation
link:      https://github.com/edithatogo/nz-legislation
surfaced:  2026-06-03
what:      CLI and MCP server that searches, retrieves and cites NZ Acts, bills, regulations and instruments straight from the Parliamentary Counsel Office's legislation.govt.nz API.
alive:     TypeScript; 43+ tests; v1.2.0; commit/contributor/release detail unrecorded
why:       Drop-in NZ-legislation access for any personal tool — fork it as the statutory-lookup backbone (e.g. pulling the current Property Law Act / Unit Titles Act sections into a drafting assistant). Local-first: yes (queries the official PCO API).
tags:      legal, nz, legislation, pco, mcp, cli, statutes

## e531538342049/FL-Product-Version-Full-2
link:      https://github.com/e531538342049/FL-Product-Version-Full-2
surfaced:  2026-06-03
what:      Listing presenting itself as a full FL Studio product version.
alive:     commit/contributor/release detail unrecorded
why:       Excluded as keyword-spam / pirated-software listing, not a real repo.
tags:      audio, keyword-spam, pirated, excluded

## docMentis/docmentis-udoc-viewer
link:      https://github.com/docMentis/docmentis-udoc-viewer
surfaced:  2026-06-03
what:      WASM PDF/DOCX viewer.
alive:     commit/contributor/release detail unrecorded
why:       Cut for redundancy on the deterministic-first re-run — overlaps superdoc and react-docxodus-viewer.
tags:      legal, viewer, wasm, pdf, docx, redundant

## cool-japan/legalis
link:      https://github.com/cool-japan/legalis
surfaced:  2026-06-03
what:      Production-grade Rust framework (76 crates, ~1M LOC) that compiles natural-language statutes into machine-verifiable code, architecturally separating deterministic logic (age thresholds, deadlines, income limits) from judicial discretion via a `LegalResult<T>` enum — "not everything should be computable."
alive:     explicitly LLM-free; commit/contributor/release detail unrecorded
why:       Mine its modelling approach to build a small clause-logic checker that flags the computable obligations and deadlines in a deed and marks the genuinely discretionary terms for human judgement. Kept for the angle. Local-first: yes.
tags:      legal, rust, statutes, formal-methods, deterministic, discretion, wildcard

## BinWang28/audio-ai-hub
link:      https://github.com/BinWang28/audio-ai-hub
surfaced:  2026-06-03
what:      Curated, weekly-refreshed hub of audio-AI papers, open models, benchmarks and datasets across audio LLMs, music understanding/generation and speech (121 entries, 11 categories).
alive:     weekly-refreshed; commit/contributor/release detail unrecorded
why:       Not code to fork, but the most efficient single scouting surface for ASA's Gemini-layer roadmap — it's where MOSS-Audio-class models and music-understanding benchmarks surface first.
tags:      audio, curated-hub, audio-llm, benchmarks, datasets, scouting

## Zettlr/Zettlr
link:      https://github.com/Zettlr/Zettlr
surfaced:  2026-05-27
what:      Pandoc-aware Markdown publishing workbench.
alive:     commit/contributor/release detail unrecorded
why:       Closer to a Pandoc writing tool than a legal-prose comparator. Useful for drafting research memos, but redundant next to Trilium / Lumina-Note.
tags:      legal, markdown, pandoc, writing, redundant

## yuch85/word-ai-redliner
link:      https://github.com/yuch85/word-ai-redliner
surfaced:  2026-05-27
what:      MS Word add-in that applies AI edits back into the document as tracked changes, connecting to local Ollama or vLLM via a proxy, using the companion `office-word-diff` library's structure-aware diff (token-map strategy with sentence/block fallbacks).
alive:     388 tests; v0.3.0; commit/contributor/release detail unrecorded
why:       The most directly forkable "AI redlines, in Word, against a local model" starting point — exactly the confidential-docs-stay-local workflow he wants. Reframed on the deterministic-first re-run: kept for the deterministic `office-word-diff` library it ships, with the Word add-in as the reference demo rather than the headline. Mine the diff library for precise, formatting-preserving DOCX edits; the AI layer is optional. Local-first: yes.
tags:      legal, docx, tracked-changes, word-addin, ollama, structure-aware-diff

## yuch85/office-word-diff
link:      https://github.com/yuch85/office-word-diff
surfaced:  2026-05-27
what:      The structure-aware Word-diff library that powers word-ai-redliner, broken out for reuse: token-map → sentence-diff → block-replace fallbacks, formatting-preserving, Office.js-based.
alive:     commit/contributor/release detail unrecorded
why:       Worth knowing as a separate dependency you can lift into other Word-add-in experiments without adopting the full redliner UI. Local-first: yes.
tags:      legal, docx, diff, office-js, formatting-preserving, library

## Yikai-Liao/symusic
link:      https://github.com/Yikai-Liao/symusic
surfaced:  2026-05-27
what:      Fast C++/Python symbolic-MIDI toolkit.
alive:     commit/contributor/release detail unrecorded
why:       MIDI-processing not harmonic analysis; offers no Harmonia UX/algorithm idea, and adds nothing over ASA's existing pipeline.
tags:      audio, symbolic, midi, toolkit, cpp

## winstonkoh87/Athena-Public
link:      https://github.com/winstonkoh87/Athena-Public
surfaced:  2026-05-27
what:      Small / experimental local-first PKM variant.
alive:     commit/contributor/release detail unrecorded
why:       Adds no new technique over the kept PKM tools.
tags:      legal, pkm, experimental, local-first

## WildKeeperPlaza/Ableton-Crack-2026
link:      https://github.com/WildKeeperPlaza/Ableton-Crack-2026
surfaced:  2026-05-27
what:      Listing presenting itself as an Ableton crack.
alive:     commit/contributor/release detail unrecorded
why:       Pirated-software listing; excluded.
tags:      audio, pirated, keyword-spam, excluded

## WallBreaker2/op
link:      https://github.com/WallBreaker2/op
surfaced:  2026-05-27
what:      Win32 screen-OCR tool.
alive:     commit/contributor/release detail unrecorded
why:       Surfaced for "OCR" but off-domain (screen OCR).
tags:      legal, false-positive, ocr, win32, off-domain

## trailofbits/graphtage
link:      https://github.com/trailofbits/graphtage
surfaced:  2026-05-27
what:      Semantic-diff library and CLI for tree-like files (JSON/XML/HTML/YAML/CSV) that compares structure, not text.
alive:     2.5k★; Python; commit/contributor/release detail unrecorded
why:       The foundation for clause-level legal-impact diffing: convert two agreements to HTML/XML (Docxodus) and graphtage the trees to see real structural changes, not line noise. Local-first: yes.
tags:      legal, structural-diff, tree-diff, xml, html, semantic

## tonaljs/tonal
link:      https://github.com/tonaljs/tonal
surfaced:  2026-05-27
what:      JavaScript music-theory library (notes, intervals, chords, scales, keys).
alive:     commit/contributor/release detail unrecorded
why:       Harmonia's notional base library; logged for completeness only.
tags:      audio, theory, js, tonaljs, chords, scales

## tombcato/smart-ticker
link:      https://github.com/tombcato/smart-ticker
surfaced:  2026-05-27
what:      Diff/ticker visualisation tool.
alive:     commit/contributor/release detail unrecorded
why:       UI-level diff visualiser; off-direction for a redliner.
tags:      legal, diff, visualiser, ui

## tiddly-gittly/TidGi-Mobile
link:      https://github.com/tiddly-gittly/TidGi-Mobile
surfaced:  2026-05-27
what:      TiddlyWiki-based mobile knowledge base.
alive:     commit/contributor/release detail unrecorded
why:       Aesthetic mismatch with the rest of the stack.
tags:      legal, pkm, tiddlywiki, mobile

## tiddly-gittly/TidGi-Desktop
link:      https://github.com/tiddly-gittly/TidGi-Desktop
surfaced:  2026-05-27
what:      TiddlyWiki-based desktop knowledge base.
alive:     commit/contributor/release detail unrecorded
why:       Aesthetic mismatch with the rest of the stack.
tags:      legal, pkm, tiddlywiki, desktop

## TeoMastro/GreekLegislationRag
link:      https://github.com/TeoMastro/GreekLegislationRag
surfaced:  2026-05-27
what:      RAG over Greek legislation.
alive:     commit/contributor/release detail unrecorded
why:       Jurisdiction-specific RAG / dataset / audit tool; the pattern is interesting but the spark slot is already filled by tw-legal-rag.
tags:      legal, rag, greece, jurisdiction-specific

## techenthusiast167/D4rk_Intel-OSINT-Investigative-Toolkit
link:      https://github.com/techenthusiast167/D4rk_Intel-OSINT-Investigative-Toolkit
surfaced:  2026-05-27
what:      OSINT investigative toolkit surfaced by the "legal" keyword.
alive:     commit/contributor/release detail unrecorded
why:       Excluded as off-domain search noise.
tags:      legal, false-positive, osint, off-domain

## TaewoooPark/PAIDEIA
link:      https://github.com/TaewoooPark/PAIDEIA
surfaced:  2026-05-27
what:      Exam-preparation application.
alive:     commit/contributor/release detail unrecorded
why:       Surfaced for "OCR / PDF / docx" but off-domain (exam prep).
tags:      legal, false-positive, exam-prep, off-domain

## sysid/bkmr
link:      https://github.com/sysid/bkmr
surfaced:  2026-05-27
what:      Small / experimental local-first bookmark/knowledge tool.
alive:     commit/contributor/release detail unrecorded
why:       Adds no new technique over the kept PKM tools.
tags:      legal, pkm, bookmarks, experimental

## surrealdb/dmp
link:      https://github.com/surrealdb/dmp
surfaced:  2026-05-27
what:      Rust port of google/diff-match-patch.
alive:     commit/contributor/release detail unrecorded
why:       Already effectively superseded by jsdiff for prose; useful only if you specifically want Rust.
tags:      legal, diff, rust, port, diff-match-patch

## superdoc-dev/superdoc
link:      https://github.com/superdoc-dev/superdoc
surfaced:  2026-05-27
what:      Self-hosted, framework-agnostic in-browser editor for real OOXML DOCX with genuine tracked changes and comments (Yjs collaboration), zero servers or AI required.
alive:     700★; TypeScript; commit/contributor/release detail unrecorded
why:       The editing/redline UI shell to build a personal review tool on — embed it, no rich-text approximation. Local-first: yes.
tags:      legal, docx, editor, tracked-changes, ooxml, yjs, browser

## SUC-DriverOld/MSST-WebUI
link:      https://github.com/SUC-DriverOld/MSST-WebUI
surfaced:  2026-05-27
what:      WebUI bundling Music-Source-Separation-Training models plus UVR, with ensemble modes and a built-in SOME MIDI extractor.
alive:     1.2k★; Python; 14 releases; commit/contributor/release detail unrecorded
why:       The canonical hub for the current best-in-class separators (MSST/VR models, BS-RoFormer et al.) that beat plain Demucs, so it's the obvious place to shop for an upgrade to ASA's stems stage — the inference is scriptable even though the front end is a PySide6 desktop app rather than a server backend.
tags:      audio, separation, msst, uvr, roformer, ensemble, midi

## stella/stella
link:      https://github.com/stella/stella
surfaced:  2026-05-27
what:      Open-source legal workspace with Matters as the core abstraction (status / deadlines / parties / documents), a full-text + versioned document store with access controls, and Tabular Review for extracting structured fields across many documents.
alive:     brand-new, 2026-05; TypeScript + Bun + Postgres + Redis; self-hostable via `bun run dev`; hosted preview at my.stll.app; commit/contributor/release detail unrecorded
why:       The closest thing to a *personal* practice-management base that's actually open source — ideal as the shell your forked tools live inside. Local-first: yes (self-hosted, your hardware).
tags:      legal, practice-management, matters, document-store, tabular-review, self-hosted

## software-mansion/react-native-executorch
link:      https://github.com/software-mansion/react-native-executorch
surfaced:  2026-05-27
what:      React Native on-device AI runtime.
alive:     commit/contributor/release detail unrecorded
why:       Surfaced for "OCR / PDF / docx" but off-domain (React Native AI).
tags:      legal, false-positive, react-native, on-device, off-domain

## SnowComplete9/Ableton-Live-12
link:      https://github.com/SnowComplete9/Ableton-Live-12
surfaced:  2026-05-27
what:      Listing presenting itself as Ableton Live 12.
alive:     commit/contributor/release detail unrecorded
why:       Pirated-software listing; excluded.
tags:      audio, pirated, keyword-spam, excluded

## simonbs/TextDiffing
link:      https://github.com/simonbs/TextDiffing
surfaced:  2026-05-27
what:      Text-diffing library / visualiser.
alive:     commit/contributor/release detail unrecorded
why:       UI-level diff visualiser; off-direction for a redliner.
tags:      legal, diff, text, visualiser, ui

## scribbletune/scribbletune
link:      https://github.com/scribbletune/scribbletune
surfaced:  2026-05-27
what:      JavaScript library for generating musical patterns and MIDI clips in code.
alive:     commit/contributor/release detail unrecorded
why:       Ableton tooling/workflow; doesn't touch audio analysis. Re-surfaced by the 06-16 and 07-01 keyword searches and confirmed still correctly dropped.
tags:      audio, js, midi, patterns, generation

## Samix2026/saudi-legal-ai-framework
link:      https://github.com/Samix2026/saudi-legal-ai-framework
surfaced:  2026-05-27
what:      Saudi legal AI framework.
alive:     commit/contributor/release detail unrecorded
why:       Jurisdiction-specific RAG / dataset / audit tool; the pattern is interesting but the spark slot is already filled by tw-legal-rag.
tags:      legal, rag, saudi-arabia, jurisdiction-specific

## SakuraMathcraft/LaTeXSnipper
link:      https://github.com/SakuraMathcraft/LaTeXSnipper
surfaced:  2026-05-27
what:      Math-to-LaTeX snipping tool.
alive:     commit/contributor/release detail unrecorded
why:       Surfaced for "OCR" but off-domain (math LaTeX).
tags:      legal, false-positive, latex, ocr, off-domain

## saidsurucu/yargi-mcp
link:      https://github.com/saidsurucu/yargi-mcp
surfaced:  2026-05-27
what:      MCP server over Turkish legal databases.
alive:     commit/contributor/release detail unrecorded
why:       Jurisdiction-specific.
tags:      legal, mcp, turkey, jurisdiction-specific

## run-llama/liteparse
link:      https://github.com/run-llama/liteparse
surfaced:  2026-05-27
what:      Standalone OSS document parser (Rust core with Node/Python/WASM bindings) that extracts text with bounding boxes from PDF/Word/PowerPoint/spreadsheets/images and does selective Tesseract OCR, all locally.
alive:     commit/contributor/release detail unrecorded
why:       The open, no-cloud ingestion layer for any of his tools — fork it as the front door that turns a scanned S&P agreement into clean text for diffing, RAG, or clause extraction. Local-first: yes.
tags:      legal, parser, pdf, ocr, bounding-boxes, rust, ingestion

## roastedroot/chicory-redline
link:      https://github.com/roastedroot/chicory-redline
surfaced:  2026-05-27
what:      A "redline"-named project outside the legal-prose domain.
alive:     commit/contributor/release detail unrecorded
why:       Uses the word "redline" for an unrelated coding workflow; off-domain for legal prose.
tags:      legal, false-positive, naming-collision, off-domain

## ritesh-1918/HELPDESK.AI
link:      https://github.com/ritesh-1918/HELPDESK.AI
surfaced:  2026-05-27
what:      Helpdesk AI application.
alive:     commit/contributor/release detail unrecorded
why:       Surfaced for "OCR / PDF / docx" but off-domain (helpdesk).
tags:      legal, false-positive, helpdesk, off-domain

## revezone/revezone
link:      https://github.com/revezone/revezone
surfaced:  2026-05-27
what:      Excalidraw + tldraw + Notion-like local workspace.
alive:     commit/contributor/release detail unrecorded
why:       Superseded by the excalidraw + Trilium pairing from the first sweep.
tags:      legal, pkm, whiteboard, excalidraw, superseded

## rdegges/redline
link:      https://github.com/rdegges/redline
surfaced:  2026-05-27
what:      A "redline"-named project outside the legal-prose domain.
alive:     commit/contributor/release detail unrecorded
why:       Uses the word "redline" for an unrelated workflow; off-domain for legal prose.
tags:      legal, false-positive, naming-collision, off-domain

## PortPhoenixVoid/VirtualDJ-cracked
link:      https://github.com/PortPhoenixVoid/VirtualDJ-cracked
surfaced:  2026-05-27
what:      Listing presenting itself as cracked VirtualDJ.
alive:     commit/contributor/release detail unrecorded
why:       Pirated-software listing; excluded.
tags:      audio, pirated, keyword-spam, excluded

## Picovoice/pico-cookbook
link:      https://github.com/Picovoice/pico-cookbook
surfaced:  2026-05-27
what:      On-device voice AI recipes.
alive:     commit/contributor/release detail unrecorded
why:       Surfaced for "OCR / PDF / docx" but off-domain (on-device voice).
tags:      legal, false-positive, voice, on-device, off-domain

## param20h/PDF-Assistant-RAG
link:      https://github.com/param20h/PDF-Assistant-RAG
surfaced:  2026-05-27
what:      Generic PDF RAG demo.
alive:     commit/contributor/release detail unrecorded
why:       Superseded by AnythingLLM plus contextgem.
tags:      legal, rag, pdf, demo, superseded

## paperless-ngx/paperless-ngx
link:      https://github.com/paperless-ngx/paperless-ngx
surfaced:  2026-05-27
what:      Well-known self-hosted document management system with OCR search.
alive:     commit/contributor/release detail unrecorded
why:       The right answer if you actually want a *DMS* with OCR search, but heavier than a personal-tool scope. Keep on the radar.
tags:      legal, dms, ocr, self-hosted, document-management

## openlibrecommunity/olcrtc
link:      https://github.com/openlibrecommunity/olcrtc
surfaced:  2026-05-27
what:      Project surfaced by the "legal" keyword in a non-legaltech sense.
alive:     commit/contributor/release detail unrecorded
why:       Excluded as off-domain search noise.
tags:      legal, false-positive, off-domain

## openlawnz/openlawnz-browser-extension
link:      https://github.com/openlawnz/openlawnz-browser-extension
surfaced:  2026-05-27
what:      Browser extension that attaches OpenLaw NZ data inside legislation.govt.nz.
alive:     2018 stub; 4★; barely maintained; commit/contributor/release detail unrecorded
why:       Barely-maintained, but the OpenLaw NZ org is worth following for live NZ caselaw data.
tags:      legal, nz, openlaw, browser-extension, caselaw, stale

## open-agreements/open-agreements
link:      https://github.com/open-agreements/open-agreements
surfaced:  2026-05-27
what:      Deterministic template filler (no LLM) that substitutes values into 40+ standard agreement templates (NDAs, SAFEs, NVCA, contractor/employment) and emits signable DOCX, via CLI/MCP.
alive:     commit/contributor/release detail unrecorded
why:       Fork it as a personal precedent-assembly tool; swap in his own NZ templates. Local-first: yes.
tags:      legal, templates, docx, precedents, deterministic, assembly

## onizet/html2openxml
link:      https://github.com/onizet/html2openxml
surfaced:  2026-05-27
what:      HTML→OOXML converter.
alive:     commit/contributor/release detail unrecorded
why:       Narrow piece.
tags:      legal, html, ooxml, converter, narrow

## Oliveira3d/free-ip-stresser-booter
link:      https://github.com/Oliveira3d/free-ip-stresser-booter
surfaced:  2026-05-27
what:      IP stresser/booter listing surfaced by the "legal" keyword.
alive:     commit/contributor/release detail unrecorded
why:       Excluded as off-domain search noise.
tags:      legal, false-positive, off-domain, excluded

## Oh-Sheet-Team/oh-sheet
link:      https://github.com/Oh-Sheet-Team/oh-sheet
surfaced:  2026-05-27
what:      Audio→piano sheet music via Basic Pitch plus RL-trained engraving; a FastAPI + Flutter sheet-music app.
alive:     commit/contributor/release detail unrecorded
why:       Generation / arrangement direction, not analysis.
tags:      audio, sheet-music, transcription, engraving, fastapi, flutter

## ocrmypdf/OCRmyPDF
link:      https://github.com/ocrmypdf/OCRmyPDF
surfaced:  2026-05-27
what:      Tesseract-backed OCR layer that makes scanned PDFs searchable in place.
alive:     commit/contributor/release detail unrecorded
why:       Well-known but missing from the first sweep. Run it across the matter folder once and your entire historical archive becomes greppable, RAG-able, diff-able. Foundational plumbing for everything downstream; not exciting on its own, but the cheapest single quality-of-life upgrade in the stack. Local-first: yes.
tags:      legal, ocr, pdf, tesseract, searchable, plumbing

## nzpco/PCO-AI-Plain-Language-Recommendations
link:      https://github.com/nzpco/PCO-AI-Plain-Language-Recommendations
surfaced:  2026-05-27
what:      Official PCO sibling repo: plain-language recommendations for legislative drafting.
alive:     3★; commit/contributor/release detail unrecorded
why:       A reference for a "plain-English rewrite" assist over clauses or advice letters. Local-first: yes.
tags:      legal, nz, pco, plain-language, drafting, official

## nuuuwan/lk_legal_docs
link:      https://github.com/nuuuwan/lk_legal_docs
surfaced:  2026-05-27
what:      Sri Lankan legal-document dataset / tooling.
alive:     commit/contributor/release detail unrecorded
why:       Jurisdiction-specific RAG / dataset / audit tool; the pattern is interesting but the spark slot is already filled by tw-legal-rag.
tags:      legal, dataset, sri-lanka, jurisdiction-specific

## NEU-ZHA/legal-ai-skills
link:      https://github.com/NEU-ZHA/legal-ai-skills
surfaced:  2026-05-27
what:      Legal AI skills bundle.
alive:     commit/contributor/release detail unrecorded
why:       A Claude Cowork / Code plugin bundle; not a stand-alone tool to fork.
tags:      legal, skills, claude-plugin, bundle

## myICOR/myPKA
link:      https://github.com/myICOR/myPKA
surfaced:  2026-05-27
what:      "AI personal knowledge assistance in a folder" — plain-Markdown PKM, any LLM, designed to stay yours forever.
alive:     209★; commit/contributor/release detail unrecorded
why:       A low-ceremony base for a personal notes/precedent system that's just files on disk (so it's trivially backed up and grep-able) with an AI layer on top. Dropped on the deterministic-first re-run as AI-PKM methodology whose non-AI part is just markdown files. Local-first: yes.
tags:      legal, pkm, markdown, local-llm, notes

## musicinformationretrieval/musicinformationretrieval.com
link:      https://github.com/musicinformationretrieval/musicinformationretrieval.com
surfaced:  2026-05-27
what:      Educational MIR Jupyter notebooks / instructional site.
alive:     commit/contributor/release detail unrecorded
why:       Not a library. Re-surfaced by the 07-01 keyword search and confirmed still correctly dropped, no new information.
tags:      audio, educational, notebooks, mir

## memex-lab/memex
link:      https://github.com/memex-lab/memex
surfaced:  2026-05-27
what:      Local-first AI journal (timeline / photo / voice cards).
alive:     commit/contributor/release detail unrecorded
why:       Journaling rather than matter notes.
tags:      legal, pkm, journal, local-first

## MCERQUA/OpenVoiceUI
link:      https://github.com/MCERQUA/OpenVoiceUI
surfaced:  2026-05-27
what:      Voice-assistant UI with TTS/STT/LLM.
alive:     commit/contributor/release detail unrecorded
why:       "Music generation" is one button on the canvas, not an analysis tool.
tags:      audio, voice-ui, tts, stt, off-domain

## magenta/mt3
link:      https://github.com/magenta/mt3
surfaced:  2026-05-27
what:      Google Magenta's multi-task multi-track transcription transformer (WAV → tokenised note events across multiple instruments simultaneously).
alive:     research code rather than a packaged service; commit/contributor/release detail unrecorded
why:       The canonical modern AMT reference and a useful upgrade path for ASA's melody / torchcrepe-based note-extraction stage — particularly for polyphonic inputs where pitch tracking alone undersells what's on the stems.
tags:      audio, transcription, amt, transformer, magenta, polyphonic

## M-Igashi/headroom
link:      https://github.com/M-Igashi/headroom
surfaced:  2026-05-27
what:      Rust CLI that measures integrated LUFS and true peak and applies limiter-free gain to a uniform true-peak ceiling, with a companion Camelot-key→BPM playlist sorter.
alive:     v2.0.0, 2026-05; commit/contributor/release detail unrecorded
why:       Native and clean, it overlaps ASA's existing EBU R128 measurement, so its real interest is the true-peak-ceiling normalization logic ASA's mastering-recommendation layer could cite — borderline, kept as a native reference rather than a new capability.
tags:      audio, rust, lufs, true-peak, normalization, camelot

## loilo/diffr
link:      https://github.com/loilo/diffr
surfaced:  2026-05-27
what:      UI-level diff visualiser.
alive:     commit/contributor/release detail unrecorded
why:       Off-direction for a redliner.
tags:      legal, diff, visualiser, ui

## LiZhuoming-lab/seemusic
link:      https://github.com/LiZhuoming-lab/seemusic
surfaced:  2026-05-27
what:      Local-only Streamlit workspace that runs spectral analysis (RMS, spectral centroid, novelty curves) side-by-side with music21-driven symbolic analysis (MusicXML / MIDI / Kern → harmony, cadence, thematic recurrence) for musicology research.
alive:     commit/contributor/release detail unrecorded
why:       The interesting bit for ASA isn't the code (it's a thin Streamlit app) but the UX pattern — "DSP measurement on the left, theory-level reading on the right, both pointing at the same timeline" is the same shape ASA's Phase-1-JSON + Phase-2-Gemini output wants to surface to the user.
tags:      audio, streamlit, music21, spectral, symbolic, ux-pattern

## liuyingxuvka/Khaos-Brain
link:      https://github.com/liuyingxuvka/Khaos-Brain
surfaced:  2026-05-27
what:      Small / experimental local-first PKM variant.
alive:     commit/contributor/release detail unrecorded
why:       Adds no new technique over the kept PKM tools.
tags:      legal, pkm, experimental, local-first

## LegalRabbit-AI/legalrabbit-docx-claude-plugin
link:      https://github.com/LegalRabbit-AI/legalrabbit-docx-claude-plugin
surfaced:  2026-05-27
what:      Claude plugin bundle for DOCX legal work.
alive:     commit/contributor/release detail unrecorded
why:       A Claude Cowork / Code plugin bundle; not a stand-alone tool to fork.
tags:      legal, claude-plugin, docx, bundle

## LaQuay/TDTChannels
link:      https://github.com/LaQuay/TDTChannels
surfaced:  2026-05-27
what:      TV/radio channel listings project surfaced by the "legal" keyword.
alive:     commit/contributor/release detail unrecorded
why:       Excluded as off-domain search noise.
tags:      legal, false-positive, tv-channels, off-domain

## kuku-mom/kuku
link:      https://github.com/kuku-mom/kuku
surfaced:  2026-05-27
what:      Tauri Markdown workspace with AI and encrypted sync.
alive:     newer / quieter than Lumina-Note; commit/contributor/release detail unrecorded
why:       Promising but newer and quieter than Lumina-Note.
tags:      legal, pkm, markdown, tauri, encrypted-sync

## krfantasy/alsdiff
link:      https://github.com/krfantasy/alsdiff
surfaced:  2026-05-27
what:      Diff tool for Ableton Live Set (`.als`) files.
alive:     commit/contributor/release detail unrecorded
why:       Uses "diff" for an unrelated Ableton-set workflow; off-domain for legal prose.
tags:      legal, false-positive, ableton, als, diff, off-domain

## kipeum86/legal-agent-orchestrator
link:      https://github.com/kipeum86/legal-agent-orchestrator
surfaced:  2026-05-27
what:      Claude-Code-hosted multi-agent legal workflow.
alive:     commit/contributor/release detail unrecorded
why:       Cloud-first and US-flavoured, fork-fit too low for a personal NZ tool. Same author as the already-shortlisted contract-review-agent.
tags:      legal, agents, orchestration, cloud-first, us-centric

## kappapiana/anonymize
link:      https://github.com/kappapiana/anonymize
surfaced:  2026-05-27
what:      Anonymises authorship metadata in ODT / DOCX (track-change author lines), not content.
alive:     commit/contributor/release detail unrecorded
why:       Useful sometimes, but narrower than ContextSafe.
tags:      legal, anonymize, metadata, docx, odt, narrow

## kaicontext/kai
link:      https://github.com/kaicontext/kai
surfaced:  2026-05-27
what:      Semantic-analysis engine that sits on top of Git and emits "meaningful change" semantic diffs and selective CI plans, language-aware via call graphs.
alive:     Go; commit/contributor/release detail unrecorded
why:       The transferable idea: treat a contract repo as git-tracked, and let a kai-style engine surface *which clauses changed in meaning between v3 and v4 of this lease* — not just textually, but in terms of obligation structure. Fork the architecture, not the code. Kept for the angle — commit-level semantic-change tooling is the right model for clause-history review. Local-first: yes.
tags:      legal, semantic-diff, git, change-analysis, clause-history, wildcard

## kahz12/Grimore-MD
link:      https://github.com/kahz12/Grimore-MD
surfaced:  2026-05-27
what:      Small / experimental local-first Markdown PKM variant.
alive:     commit/contributor/release detail unrecorded
why:       Adds no new technique over the kept PKM tools.
tags:      legal, pkm, markdown, experimental

## JSv4/react-docxodus-viewer
link:      https://github.com/JSv4/react-docxodus-viewer
surfaced:  2026-05-27
what:      Client-side React component that renders DOCX and redlines in the browser via the Docxodus WASM library — no server round-trip.
alive:     commit/contributor/release detail unrecorded
why:       Document content never leaves the machine. Pair it with Docxodus to get a complete local-first compare-and-review UI he can fork as the front end of a personal redlining tool. Local-first: yes.
tags:      legal, docx, react, wasm, viewer, redline, client-side

## JSv4/Docxodus
link:      https://github.com/JSv4/Docxodus
surfaced:  2026-05-27
what:      TypeScript/Python/.NET OpenXML engine (forked from Open-Xml-PowerTools) that generates tracked-change redlines between two DOCX files with move detection and format-change identification, plus DOCX↔HTML, a markdown projection for LLM pipelines, and a WASM build.
alive:     commit/contributor/release detail unrecorded
why:       This is the redline *engine* to build a comparison tool on — fork it and wrap a UI, or pipe its markdown projection into a local LLM for clause-level impact analysis. Pairs with safe-docx (editing) and graphtage (structural diff of the HTML/XML form). Local-first: yes.
tags:      legal, docx, ooxml, tracked-changes, redline, wasm, engine

## jshph/enzyme
link:      https://github.com/jshph/enzyme
surfaced:  2026-05-27
what:      Small / experimental local-first PKM variant.
alive:     commit/contributor/release detail unrecorded
why:       Adds no new technique over the kept PKM tools.
tags:      legal, pkm, experimental, local-first

## jetyu/NoteWizard
link:      https://github.com/jetyu/NoteWizard
surfaced:  2026-05-27
what:      Small / experimental local-first notes app.
alive:     commit/contributor/release detail unrecorded
why:       Adds no new technique over the kept PKM tools.
tags:      legal, pkm, notes, experimental

## jamesaphoenix/diff-core
link:      https://github.com/jamesaphoenix/diff-core
surfaced:  2026-05-27
what:      A generic diff library outside the legal-prose domain.
alive:     commit/contributor/release detail unrecorded
why:       Uses "semantic diff" for an unrelated coding workflow; off-domain for legal prose.
tags:      legal, false-positive, diff, off-domain

## IrtezaAsadRizvi/ai-megalist
link:      https://github.com/IrtezaAsadRizvi/ai-megalist
surfaced:  2026-05-27
what:      Curated index of 200+ AI tools.
alive:     commit/contributor/release detail unrecorded
why:       Index, not code.
tags:      audio, index, list, ai-tools

## hueyy/lacuna-db
link:      https://github.com/hueyy/lacuna-db
surfaced:  2026-05-27
what:      Singapore legal database tooling.
alive:     commit/contributor/release detail unrecorded
why:       Jurisdiction-specific RAG / dataset / audit tool; the pattern is interesting but the spark slot is already filled by tw-legal-rag.
tags:      legal, database, singapore, jurisdiction-specific

## hgmzhn/manga-translator-ui
link:      https://github.com/hgmzhn/manga-translator-ui
surfaced:  2026-05-27
what:      Comic/manga translation UI.
alive:     commit/contributor/release detail unrecorded
why:       Surfaced for "OCR" but off-domain (comic translation).
tags:      legal, false-positive, ocr, manga, off-domain

## he-yufeng/PromptDiff
link:      https://github.com/he-yufeng/PromptDiff
surfaced:  2026-05-27
what:      Diff tooling for LLM prompts.
alive:     commit/contributor/release detail unrecorded
why:       Uses "semantic diff" for an unrelated prompt workflow; off-domain for legal prose.
tags:      legal, false-positive, prompts, diff, off-domain

## hdavid/Launchpad95
link:      https://github.com/hdavid/Launchpad95
surfaced:  2026-05-27
what:      Ableton Live Remote Script for the Novation Launchpad.
alive:     commit/contributor/release detail unrecorded
why:       Ableton tooling/workflow; doesn't touch audio analysis.
tags:      audio, ableton, remote-script, launchpad, controller

## HarshK97/diffmantic.nvim
link:      https://github.com/HarshK97/diffmantic.nvim
surfaced:  2026-05-27
what:      Neovim diff-visualisation plugin.
alive:     commit/contributor/release detail unrecorded
why:       UI-level diff visualiser; off-direction for a redliner.
tags:      legal, diff, neovim, visualiser, ui

## gochendong/suno-api
link:      https://github.com/gochendong/suno-api
surfaced:  2026-05-27
what:      Cloud Suno API wrapper.
alive:     commit/contributor/release detail unrecorded
why:       Off-target.
tags:      audio, suno, api-wrapper, generation

## gluon/AbletonLive12_MIDIRemoteScripts
link:      https://github.com/gluon/AbletonLive12_MIDIRemoteScripts
surfaced:  2026-05-27
what:      Unofficial collection of the Ableton Live 12.4 MIDI Remote Scripts (Python) with an accompanying Live Object Model documentation site spanning Live 9–12.
alive:     commit/contributor/release detail unrecorded
why:       ASA's Phase 2 emits Live 12 device/parameter/value recommendations, so this is a useful reference for real device-control mappings and parameter-naming patterns — but it's a controller-script collection, not a complete built-in-device API, so treat it as a naming/structure crib rather than ground truth.
tags:      audio, ableton, remote-scripts, lom, device-params, reference

## gambiarras/legal-iptv
link:      https://github.com/gambiarras/legal-iptv
surfaced:  2026-05-27
what:      IPTV listing project using "legal" in a non-legaltech sense.
alive:     commit/contributor/release detail unrecorded
why:       Excluded as off-domain search noise.
tags:      legal, false-positive, iptv, off-domain

## FutureRootsDE/legal-audit-de
link:      https://github.com/FutureRootsDE/legal-audit-de
surfaced:  2026-05-27
what:      German legal-audit tool.
alive:     commit/contributor/release detail unrecorded
why:       Jurisdiction-specific RAG / dataset / audit tool; the pattern is interesting but the spark slot is already filled by tw-legal-rag.
tags:      legal, audit, germany, jurisdiction-specific

## freelawproject/doctor
link:      https://github.com/freelawproject/doctor
surfaced:  2026-05-27
what:      Document-conversion microservice.
alive:     commit/contributor/release detail unrecorded
why:       Off-target for personal use.
tags:      legal, conversion, microservice, off-target

## fedec65/bettercallclaude
link:      https://github.com/fedec65/bettercallclaude
surfaced:  2026-05-27
what:      Claude-oriented legal assistant bundle.
alive:     commit/contributor/release detail unrecorded
why:       A Claude Cowork / Code plugin bundle; not a stand-alone tool to fork.
tags:      legal, claude-plugin, bundle

## EvotecIT/OfficeIMO
link:      https://github.com/EvotecIT/OfficeIMO
surfaced:  2026-05-27
what:      .NET DOCX/XLSX library.
alive:     commit/contributor/release detail unrecorded
why:       Off-stack.
tags:      legal, dotnet, docx, xlsx, off-stack

## eigenpal/docx-editor
link:      https://github.com/eigenpal/docx-editor
surfaced:  2026-05-27
what:      Open-source WYSIWYG DOCX editor library (React + Vue + Nuxt adapters, ProseMirror engine) that produces "canonical OOXML" with tracked changes, shipping a companion `@eigenpal/docx-editor-agents` Agent SDK + chat UI with MCP server support.
alive:     commit/contributor/release detail unrecorded
why:       Fork it as the editing half of your matter cockpit — drop a contract in, model proposes edits via MCP, edits land as native Word tracked changes the client opens in Word without complaint. Kept over superdoc for having the native MCP / agent SDK. Local-first: yes.
tags:      legal, docx, editor, prosemirror, ooxml, tracked-changes, mcp

## egroup-labs/kept
link:      https://github.com/egroup-labs/kept
surfaced:  2026-05-27
what:      Search and archive AI conversations across providers.
alive:     commit/contributor/release detail unrecorded
why:       The chat-history use case is real but narrow.
tags:      legal, archive, chat-history, search, narrow

## digitalaotearoa/legaleligibility
link:      https://github.com/digitalaotearoa/legaleligibility
surfaced:  2026-05-27
what:      Gov Zero Aotearoa benefits-eligibility expert system.
alive:     commit/contributor/release detail unrecorded
why:       Off-domain for property work.
tags:      legal, nz, eligibility, expert-system, off-domain

## dejuknow/md-redline
link:      https://github.com/dejuknow/md-redline
surfaced:  2026-05-27
what:      A "redline"-named Markdown project outside the legal-prose domain.
alive:     commit/contributor/release detail unrecorded
why:       Uses the word "redline" for an unrelated workflow; off-domain for legal prose.
tags:      legal, false-positive, naming-collision, markdown, off-domain

## davidar/pandiff
link:      https://github.com/davidar/pandiff
surfaced:  2026-05-27
what:      Pandoc-powered semantic prose diff that ingests anything Pandoc can read (DOCX, PDF, Markdown, HTML, LaTeX, ODT) and writes CriticMarkup, HTML, PDF-via-LaTeX, or DOCX with native Track Changes.
alive:     v0.8.0, 2025-05; still maintained; works in CI via the documented Docker image; commit/contributor/release detail unrecorded
why:       It's already the universal "diff two contracts, emit a Word redline" tool you were going to assemble out of jsdiff + adeu. Local once installed (npm + Pandoc). Fork it as the engine and skin a Tauri / web UI over it. Local-first: yes.
tags:      legal, pandoc, prose-diff, docx, tracked-changes, criticmarkup, engine

## D1firehail/AdeptiScanner-GI
link:      https://github.com/D1firehail/AdeptiScanner-GI
surfaced:  2026-05-27
what:      Game-inventory scanner for Genshin Impact.
alive:     commit/contributor/release detail unrecorded
why:       Surfaced for "OCR" but off-domain (game inventory).
tags:      legal, false-positive, ocr, game, off-domain

## Curated-Awesome-Lists/awesome-ai-music-generation
link:      https://github.com/Curated-Awesome-Lists/awesome-ai-music-generation
surfaced:  2026-05-27
what:      An awesome-list of AI music generation resources.
alive:     commit/contributor/release detail unrecorded
why:       Awesome-list, index-only.
tags:      audio, awesome-list, generation, index

## cucuwritescode/conformer-acr
link:      https://github.com/cucuwritescode/conformer-acr
surfaced:  2026-05-27
what:      Conformer audio chord-recognition studentship code.
alive:     14★, under the sweep's 20-star bar; commit/contributor/release detail unrecorded
why:       Same lane as consonance-ACE, already logged.
tags:      audio, chord, conformer, research

## consi/ymldiff
link:      https://github.com/consi/ymldiff
surfaced:  2026-05-27
what:      YAML diff tool.
alive:     commit/contributor/release detail unrecorded
why:       Uses "semantic diff" for an unrelated config workflow; off-domain for legal prose.
tags:      legal, false-positive, yaml, diff, off-domain

## CLSherrod/crm-markdown
link:      https://github.com/CLSherrod/crm-markdown
surfaced:  2026-05-27
what:      Markdown-based CRM.
alive:     commit/contributor/release detail unrecorded
why:       Adds no new technique over the kept PKM tools.
tags:      legal, crm, markdown, experimental

## Chz1Y/Steerable-music-transformer
link:      https://github.com/Chz1Y/Steerable-music-transformer
surfaced:  2026-05-27
what:      Niche controllable-generation research repo (steerable music transformer).
alive:     commit/contributor/release detail unrecorded
why:       Off-target for ASA analysis and Harmonia reharmonization.
tags:      audio, generation, transformer, research, niche

## cdacamar/gap
link:      https://github.com/cdacamar/gap
surfaced:  2026-05-27
what:      Diff-visualisation tool.
alive:     commit/contributor/release detail unrecorded
why:       UI-level diff visualiser; off-direction for a redliner.
tags:      legal, diff, visualiser, ui

## bzsanti/oxidizePdf
link:      https://github.com/bzsanti/oxidizePdf
surfaced:  2026-05-27
what:      Pure-Rust PDF library aimed at RAG: structure-aware chunking, table / text extraction, signatures, encryption, no ML or C dependencies.
alive:     commit/contributor/release detail unrecorded
why:       The chunking primitive is the interesting bit — most PDF libraries leave chunking to the caller, which is where legal RAG tends to go wrong (splitting mid-clause, breaking defined-term context). Fork it as the ingest-and-chunk layer feeding a local RAG over your archive. Local-first: yes.
tags:      legal, pdf, rust, chunking, rag, tables, extraction

## bpwhelan/GameSentenceMiner
link:      https://github.com/bpwhelan/GameSentenceMiner
surfaced:  2026-05-27
what:      Japanese sentence-mining tool for games.
alive:     commit/contributor/release detail unrecorded
why:       Surfaced for "OCR" but off-domain (language learning).
tags:      legal, false-positive, ocr, language-learning, off-domain

## blueberrycongee/Lumina-Note
link:      https://github.com/blueberrycongee/Lumina-Note
surfaced:  2026-05-27
what:      Local-first Markdown notes app with live preview, bidirectional wiki-links, an AI assistant and semantic search — Electron + React + CodeMirror, with a built-in PDF reader and second-brain framing.
alive:     commit/contributor/release detail unrecorded
why:       A lighter alternative to Trilium if you want one app for matter notes + PDFs side-by-side, with AI on the page. Local-first: yes.
tags:      legal, notes, markdown, wiki-links, pdf-reader, electron

## basicmachines-co/basic-memory
link:      https://github.com/basicmachines-co/basic-memory
surfaced:  2026-05-27
what:      Markdown-on-disk PKM where humans (text editor / Obsidian) and AI (via MCP) read and write the same files — semantic search across notes via local vector embeddings, structured knowledge graph via wikilinks and typed relations, native Claude / Cursor / VS Code integration.
alive:     commit/contributor/release detail unrecorded
why:       The right shape for a lawyer's matter notes: the human keeps owning plain-text files, while Claude can read, search, summarise and update them through tools rather than copy-paste. Stronger AI integration than Trilium for the same local-first guarantee. Local-first: yes.
tags:      legal, pkm, markdown, mcp, knowledge-graph, embeddings, notes

## Balchandar/Architect-Studio-X
link:      https://github.com/Balchandar/Architect-Studio-X
surfaced:  2026-05-27
what:      A "redline"/"semantic diff"-tagged project outside the legal-prose domain.
alive:     commit/contributor/release detail unrecorded
why:       Uses the word "redline" / "semantic diff" for an unrelated workflow; off-domain for legal prose.
tags:      legal, false-positive, naming-collision, off-domain

## AzureTellerTell/Serato-DJ-Pro
link:      https://github.com/AzureTellerTell/Serato-DJ-Pro
surfaced:  2026-05-27
what:      Listing presenting itself as Serato DJ Pro.
alive:     commit/contributor/release detail unrecorded
why:       Pirated-software listing; excluded.
tags:      audio, pirated, keyword-spam, excluded

## apache/poi
link:      https://github.com/apache/poi
surfaced:  2026-05-27
what:      Java OOXML library.
alive:     commit/contributor/release detail unrecorded
why:       Off-stack for vibe-coding (Java).
tags:      legal, java, ooxml, off-stack

## AndyWeasley2004/BACHI_Chord_Recognition
link:      https://github.com/AndyWeasley2004/BACHI_Chord_Recognition
surfaced:  2026-05-27
what:      ICASSP 2026 symbolic chord-recognition paper code.
alive:     11★, under the sweep's 20-star bar; commit/contributor/release detail unrecorded
why:       Symbolic-input (not audio), so it would compete with the already-shortlisted consonance-ACE rather than fill a gap.
tags:      audio, chord, symbolic, research, icassp

## andrew/json-schema-diff
link:      https://github.com/andrew/json-schema-diff
surfaced:  2026-05-27
what:      JSON Schema diff tool.
alive:     commit/contributor/release detail unrecorded
why:       Uses "semantic diff" for an unrelated schema workflow; off-domain for legal prose.
tags:      legal, false-positive, json-schema, diff, off-domain

## AltisLegal/AltisLegal
link:      https://github.com/AltisLegal/AltisLegal
surfaced:  2026-05-27
what:      Conveyancing Central API resource from 2015.
alive:     dead; commit/contributor/release detail unrecorded
why:       Dead, but flagged as the only NZ-region conveyancing-API artefact surfaced.
tags:      legal, nz, conveyancing, api, dead

## alexanderatallah/redline
link:      https://github.com/alexanderatallah/redline
surfaced:  2026-05-27
what:      A "redline"-named project outside the legal-prose domain.
alive:     commit/contributor/release detail unrecorded
why:       Uses the word "redline" for an unrelated workflow; off-domain for legal prose.
tags:      legal, false-positive, naming-collision, off-domain

## AlexAlves87/ContextSafe
link:      https://github.com/AlexAlves87/ContextSafe
surfaced:  2026-05-27
what:      100% local PII detection and redaction for PDFs / DOCX / images, with cross-document consistency ("same person always gets the same alias within a project") and three modes: masking, consistent pseudonyms, synthetic-with-invalid-checksums data.
alive:     Spanish-leaning entity set today (DNI / NIG / ECLI); commit/contributor/release detail unrecorded
why:       The architecture is the gold: build an NZ adaptation (IRD numbers, NZBNs, Land Titles references, parcel IDs) and use it as a pre-flight step before any cloud-LLM call, so confidential matter docs can use cloud models without leaking client identity. Kept for the angle — the consistent-alias technique is the missing piece for sane cloud-LLM use in a NZ practice. Local-first: yes.
tags:      legal, pii, redaction, pseudonyms, cross-document, preflight, nz-adaptable

## alea-institute/FOLIO
link:      https://github.com/alea-institute/FOLIO
surfaced:  2026-05-27
what:      Legal-ontology OWL graph.
alive:     commit/contributor/release detail unrecorded
why:       Reference data, not personal tooling.
tags:      legal, ontology, owl, reference-data

## agentmail-to/agentmail-examples
link:      https://github.com/agentmail-to/agentmail-examples
surfaced:  2026-05-27
what:      Agent email examples repo.
alive:     commit/contributor/release detail unrecorded
why:       Uses the word "redline" / "semantic diff" for unrelated coding / agent workflows; off-domain for legal prose.
tags:      legal, false-positive, agents, email, off-domain

## aftabrehan/jarvis-ai
link:      https://github.com/aftabrehan/jarvis-ai
surfaced:  2026-05-27
what:      Generic Next.js "AI tools SaaS" template.
alive:     archived; commit/contributor/release detail unrecorded
why:       Music-generation is one Replicate endpoint, not real music tooling.
tags:      audio, saas-template, nextjs, archived, off-domain

## afnanenayet/diffsitter
link:      https://github.com/afnanenayet/diffsitter
surfaced:  2026-05-27
what:      Tree-sitter-based AST difftool producing meaningful semantic diffs.
alive:     2.4k★; Rust; commit/contributor/release detail unrecorded
why:       A second technique for structure-aware comparison — mine its tree-sitter approach for diffing parsed document structure rather than raw text. Local-first: yes.
tags:      legal, structural-diff, tree-sitter, ast, rust, semantic

## affige/genmusic_demo_list
link:      https://github.com/affige/genmusic_demo_list
surfaced:  2026-05-27
what:      List of generative-music demo websites.
alive:     commit/contributor/release detail unrecorded
why:       Index, not code.
tags:      audio, index, generative, list

## Ableton/link
link:      https://github.com/Ableton/link
surfaced:  2026-05-27
what:      Official Ableton Link C++ tempo-sync library.
alive:     commit/contributor/release detail unrecorded
why:       Foundational but already implicit in the other Ableton entries; not analysis tooling.
tags:      audio, ableton, link, sync, cpp

## aa0101181514/tw-legal-rag
link:      https://github.com/aa0101181514/tw-legal-rag
surfaced:  2026-05-27
what:      Taiwanese-judgment retrieval CLI that packages search hits into a bundle, then runs a bundle-level citation check against the LLM's answer — retrieval-only on the local side, BYO-LLM on the user's side, with structural verification that quoted passages actually exist in the bundle.
alive:     commit/contributor/release detail unrecorded
why:       The pattern is the unlock: a "retrieve NZLII judgments locally, package, hand to whichever model the lawyer trusts, verify citations come back from the bundle" CLI is a ~weekend NZ port. Local-first: yes (retrieval; LLM is BYO).
tags:      legal, rag, citation-check, retrieval, byo-llm, judgments, wildcard

## ZaneH/piano-trainer
link:      https://github.com/ZaneH/piano-trainer
surfaced:  2026-05-21
what:      Piano practice / trainer app.
alive:     commit/contributor/release detail unrecorded
why:       Off-stack; dropped 05-21. Practice-UX patterns only.
tags:      audio, piano, practice, ui

## Wilfred/difftastic
link:      https://github.com/Wilfred/difftastic
surfaced:  2026-05-21
what:      A structure-aware (syntax-tree) diff for code that ignores reflowed whitespace and shows only real changes.
alive:     25.4k★; commit/contributor/release detail unrecorded
why:       The pattern transfers directly to contracts, where renumbering and reflow hide the true edits. Pair it with a Markdown/tree-sitter grammar to build a clause-level redliner far cleaner than Word's character compare. Wildcard: code → prose structural diff. Local-first: yes.
tags:      legal, structural-diff, tree-sitter, code-to-prose, clause-level, wildcard

## usememos/memos
link:      https://github.com/usememos/memos
surfaced:  2026-05-21
what:      A clean, self-hosted single-binary quick-capture / microblog tool, Markdown-native and SQLite-backed.
alive:     59.9k★; commit/contributor/release detail unrecorded
why:       Dropped 05-21 as redundant with Trilium's capture; kept as a friction-free quick-capture inbox for matter notes if Trilium feels too heavy for jotting. Local-first: yes.
tags:      legal, quick-capture, markdown, sqlite, self-hosted

## ubisoft/ComfyUI-Chord
link:      https://github.com/ubisoft/ComfyUI-Chord
surfaced:  2026-05-21
what:      ComfyUI node wrapping Ubisoft's "Chord" audio model.
alive:     commit/contributor/release detail unrecorded
why:       Generation-side and ComfyUI-bound, off-target for both streams. Nothing transferable beyond awareness of the Chord model.
tags:      audio, comfyui, generation, chord-model

## TriliumNext/Trilium
link:      https://github.com/TriliumNext/Trilium
surfaced:  2026-05-21
what:      A hierarchical, scriptable personal knowledge base whose notes can run JS, so it doubles as a programmable second brain.
alive:     36.1k★; commit/contributor/release detail unrecorded
why:       Fork it into a precedent/clause library with scripted automations (auto-insert party details, generate a per-matter-type checklist). Local-first: yes.
tags:      legal, pkm, scriptable, knowledge-base, precedents, automations

## tomasonjo-labs/legal-tech-chat
link:      https://github.com/tomasonjo-labs/legal-tech-chat
surfaced:  2026-05-21
what:      A worked pipeline that extracts structured fields from contracts into a Neo4j knowledge graph and answers questions via a LangGraph agent.
alive:     159★; Jupyter notebooks; commit/contributor/release detail unrecorded
why:       Fork the *pattern* to make your contracts queryable by relationship ("every lease whose rent-review clause references CPI") instead of flat one-doc-at-a-time RAG. Local-first: partial (self-hostable; reference notebooks use cloud LLMs).
tags:      legal, knowledge-graph, neo4j, langgraph, graphrag, notebooks

## timvancann/chordflow
link:      https://github.com/timvancann/chordflow
surfaced:  2026-05-21
what:      Rust chord-practice TUI.
alive:     commit/contributor/release detail unrecorded
why:       Not analysis or theory tooling. Practice-loop / progression-cycling UX idea only.
tags:      audio, chord, practice, tui, rust

## tauri-apps/tauri
link:      https://github.com/tauri-apps/tauri
surfaced:  2026-05-21
what:      Desktop shell for wrapping tools into a real, distributable, offline app with a tiny footprint.
alive:     107k★; commit/contributor/release detail unrecorded
why:       Build a single "matter cockpit" binary combining your parser + diff + notes, with all data staying on your machine. Local-first: yes.
tags:      legal, desktop-shell, rust, webview, offline, distributable

## spartypkp/open-source-legislation
link:      https://github.com/spartypkp/open-source-legislation
surfaced:  2026-05-21
what:      Aimed to be open global legislation data in an SQL knowledge-graph format with Python/TypeScript SDKs.
alive:     15★; dead — supporting infrastructure and data links have shut down; the repo page still resolves
why:       Excluded on 05-21 as dead: the bulk-download/SDK promise no longer functions. No live data backend to build on; revisit only if the infra is ever restored.
tags:      legal, legislation, knowledge-graph, dead-infra, scraping

## sivabenepoivediamo/musicplusplus
link:      https://github.com/sivabenepoivediamo/musicplusplus
surfaced:  2026-05-21
what:      Header-only C++ music-theory library using vector-based representations for chords, scales, intervals, voice leading and reharmonization (modal interchange, modulation), with TypeScript and Python SDKs on the roadmap.
alive:     TS/Python SDKs on the roadmap; commit/contributor/release detail unrecorded
why:       The reharmonization/voice-leading coverage is dead-center on Harmonia's domain — but it's C++ today, so it's an algorithm reference (or a future dependency once the planned TS SDK lands), not a Tonal.js drop-in.
tags:      audio, theory, reharmonization, voice-leading, cpp

## sigsep/sigsep-mus-eval
link:      https://github.com/sigsep/sigsep-mus-eval
surfaced:  2026-05-21
what:      The MUSDB / BSS-eval source-separation evaluation package (SDR/SIR/SAR).
alive:     commit/contributor/release detail unrecorded
why:       An eval shell — only useful for benchmarking separators, which ASA doesn't do; logged for completeness.
tags:      audio, eval, musdb, bss-eval, benchmark

## shcherbak-ai/contextgem
link:      https://github.com/shcherbak-ai/contextgem
surfaced:  2026-05-21
what:      An LLM extraction framework built around "Aspects" and "Concepts" that returns results with paragraph/sentence-level source references and auto-generated justifications, and can run against a local model.
alive:     1.8k★; commit/contributor/release detail unrecorded
why:       Fork it as your structured clause/defined-term/date extractor — the cite-back-to-source is exactly what trustworthy legal output needs. Local-first: yes.
tags:      legal, extraction, aspects-concepts, citations, local-llm, justifications

## sepandhaghighi/capo
link:      https://github.com/sepandhaghighi/capo
surfaced:  2026-05-21
what:      Python guitar-chord transposition library.
alive:     commit/contributor/release detail unrecorded
why:       Tonal.js already does transposition for Harmonia. Capo/transpose mapping logic only, if a guitar-specific transpose ever comes up.
tags:      audio, chord, guitar, transpose

## sen-uni-kn/ContractCheck
link:      https://github.com/sen-uni-kn/ContractCheck
surfaced:  2026-05-21
what:      An academic tool that formalises a contract's clause preconditions into first-order logic and runs an SMT solver to find internal contradictions and unexecutable clauses.
alive:     6★; Java; commit/contributor/release detail unrecorded
why:       Mine the *modelling approach* (not the Java) to build a logic-level consistency linter that flags defined-term conflicts and clauses that can never both hold. Kept for the angle: single-document consistency is a rare, on-point angle. Local-first: yes.
tags:      legal, smt, first-order-logic, consistency, single-doc, academic

## rtfpessoa/diff2html
link:      https://github.com/rtfpessoa/diff2html
surfaced:  2026-05-21
what:      Renders diffs as polished side-by-side or inline HTML.
alive:     3.4k★; commit/contributor/release detail unrecorded
why:       The developer code-review UI, repurposed to present document changes to a non-technical client or counterparty. Pair it with jsdiff (engine) for a printable/PDF redline view; the two compose into a full local-first redliner in an afternoon. Local-first: yes.
tags:      legal, diff-render, side-by-side, html, client-facing

## RowanUnderwood/Synesthesia-AI-Video-Director
link:      https://github.com/RowanUnderwood/Synesthesia-AI-Video-Director
surfaced:  2026-05-21
what:      Audio→LLM→video tool where the LLM writes video prompts from an audio pass.
alive:     commit/contributor/release detail unrecorded
why:       The "audio analysis" is pydub silence detection and the LLM writes *video* prompts; off-domain for ASA. Nothing on the audio-analysis side.
tags:      audio, audio-to-video, off-domain

## paulfitz/daff
link:      https://github.com/paulfitz/daff
surfaced:  2026-05-21
what:      Cell-level diff for tabular/CSV data with a visual highlight format and bindings across many languages.
alive:     905★; commit/contributor/release detail unrecorded
why:       Repurpose it for settlement statements, trust-ledger schedules, or rates apportionments where one wrong figure matters. Build a "what changed between two versions of this financial schedule?" viewer that points at the exact cell, not just the row. Wildcard: spreadsheet diff → financial-schedule diff. Local-first: yes.
tags:      legal, tabular-diff, csv, cell-level, financial-schedules, wildcard

## OpenMOSS/MOSS-Music
link:      https://github.com/OpenMOSS/MOSS-Music
surfaced:  2026-05-21
what:      Open 8B music-understanding LMM (MOSS-Audio-Encoder + Qwen3-8B) that takes raw audio and does timestamped lyrics ASR, captioning, structural analysis, chord/key/tempo reasoning and long-form musical Q&A.
alive:     weights on HF/ModelScope with SGLang/Transformers/Gradio inference; commit/contributor/release detail unrecorded
why:       The single most on-point new find for ASA's Gemini layer — it's an open, self-hostable model producing exactly the LLM-interpreted analysis ASA currently gets from Essentia + Gemini, so it's a serious reference (or partial replacement) for that layer and its task decomposition maps straight onto ASA's JSON. Evaluate as a (partial) self-hosted replacement for the Gemini Phase-2 layer; fork its prompt/task structure even if you keep Gemini.
tags:      audio, audio-llm, understanding, lmm, structure, self-hostable

## Open-Source-Legal/OpenContracts
link:      https://github.com/Open-Source-Legal/OpenContracts
surfaced:  2026-05-21
what:      A self-hosted document-annotation + knowledge-base platform with vector + full-text search, LLM clause extraction, version control, and agents that compare clauses across many contracts.
alive:     1.3k★; commit/contributor/release detail unrecorded
why:       Heavier to stand up (Docker), but the most complete self-hosted foundation if you want one app for both understanding and cross-document comparison of your private corpus. Local-first: yes.
tags:      legal, annotation, knowledge-base, cross-doc, version-control, docker

## nzpco/PCO-AI-Generating-an-Updated-Act
link:      https://github.com/nzpco/PCO-AI-Generating-an-Updated-Act
surfaced:  2026-05-21
what:      Official NZ Parliamentary Counsel Office code that takes an amendment Act and applies it to the principal Act from the legislation.govt.nz XML, presenting the consolidated result.
alive:     1★; documents running locally with Ollama; commit/contributor/release detail unrecorded
why:       NZ gold: fork it as both a worked example of parsing NZ legislation XML and a personal "what does the in-force version actually say?" consolidator. Local-first: yes.
tags:      legal, nz, pco, legislation-xml, consolidation, ollama, official

## nzpco/PCO-AI-Classification-of-Legislation
link:      https://github.com/nzpco/PCO-AI-Classification-of-Legislation
surfaced:  2026-05-21
what:      Official PCO sibling repo: AI classification of NZ legislation.
alive:     1★; commit/contributor/release detail unrecorded
why:       A reference for tagging/classifying NZ statutory text by topic or type. Local-first: yes.
tags:      legal, nz, pco, classification, legislation, official

## nzpco/PCO-AI-Chatbot-for-NZL
link:      https://github.com/nzpco/PCO-AI-Chatbot-for-NZL
surfaced:  2026-05-21
what:      Official PCO sibling repo: a chatbot over New Zealand legislation.
alive:     2★; commit/contributor/release detail unrecorded
why:       A worked NZ-legislation RAG reference to compare against AnythingLLM-based approaches. Local-first: yes.
tags:      legal, nz, pco, chatbot, legislation, official

## NeptuneHub/audiomuse-ai-plugin
link:      https://github.com/NeptuneHub/audiomuse-ai-plugin
surfaced:  2026-05-21
what:      Jellyfin sibling of the AudioMuse Navidrome plugin, with the same librosa + ONNX + LLM sonic-analysis architecture.
alive:     commit/contributor/release detail unrecorded
why:       Same architecture as the already-logged NV plugin, no new DSP — dropped on 05-21 for that reason. Only the Jellyfin-side integration glue is worth anything if targeting Jellyfin; architecturally identical to the NV plugin already logged.
tags:      audio, jellyfin, sibling, plugin, redundant

## NeptuneHub/AudioMuse-AI-MusicServer
link:      https://github.com/NeptuneHub/AudioMuse-AI-MusicServer
surfaced:  2026-05-21
what:      Integration shell wiring AudioMuse-AI to a music server.
alive:     commit/contributor/release detail unrecorded
why:       No standalone analysis content. Wiring/deployment reference only; the real substance is in AudioMuse-AI.
tags:      audio, integration-shell, music-server, deployment

## naggie/dstask
link:      https://github.com/naggie/dstask
surfaced:  2026-05-21
what:      A git-powered terminal todo/note manager — single binary, a markdown note page per task, with a full git-history audit trail.
alive:     1.2k★; commit/contributor/release detail unrecorded
why:       Dropped 05-21 as overlapping Trilium/notes, but it's a nice matter-tracker reskin where every status change is a git commit — useful if an immutable audit trail of who-changed-what matters. Local-first: yes.
tags:      legal, todo, git-audit-trail, cli, single-binary, matter-tracker

## Mintplex-Labs/anything-llm
link:      https://github.com/Mintplex-Labs/anything-llm
surfaced:  2026-05-21
what:      A polished, fully-offline "private ChatGPT over your documents" desktop app with workspaces, PDF/DOCX ingestion, source citations and a local vector DB (Ollama/LM Studio).
alive:     60.4k★; commit/contributor/release detail unrecorded
why:       Self-host it day one as your confidential "chat with my matter files" base, then graft clause-extraction prompts onto its workspace model (workspaces map neatly to matters). Local-first: yes.
tags:      legal, rag, offline, ollama, vector-db, workspaces

## ManasWolrd/WarpCore
link:      https://github.com/ManasWolrd/WarpCore
surfaced:  2026-05-21
what:      Niche DAW-adjacent tool.
alive:     commit/contributor/release detail unrecorded
why:       Off-stack and under the relevance bar on 05-21. Nothing confirmed.
tags:      audio, niche, daw

## lorediggia/harmony-lab
link:      https://github.com/lorediggia/harmony-lab
surfaced:  2026-05-21
what:      Minimal Rust scale/chord explorer.
alive:     commit/contributor/release detail unrecorded
why:       Too small and wrong stack for Harmonia. Only useful as a tiny reference for representing scales/chords in Rust if a native harmonic helper is wanted.
tags:      audio, chord, scale, rust

## kpdecker/jsdiff
link:      https://github.com/kpdecker/jsdiff
surfaced:  2026-05-21
what:      Diff library that works on characters, words, sentences and JSON rather than lines, in the browser or Node with no upload.
alive:     9.1k★; commit/contributor/release detail unrecorded
why:       Exactly the granularity legal prose needs. It's the diff-engine half of a complete local "compare two clauses and show the changes" stack. Local-first: yes.
tags:      legal, diff, sentence-level, json, browser, no-upload

## kipeum86/contract-review-agent
link:      https://github.com/kipeum86/contract-review-agent
surfaced:  2026-05-21
what:      A local-first agent that compares a counterparty draft against your house templates and emits a Word file with tracked-change redlines, internal-vs-external margin comments and negotiation points.
alive:     34★; commit/contributor/release detail unrecorded
why:       The closest thing to your flagship goal already built. Fork it and swap its Claude API call for a local model (Ollama) to go fully offline. Local-first: partial (file processing stays local; cloud LLM by default).
tags:      legal, contract-review, redline, templates, agent, ollama-swap

## jsvine/pdfplumber
link:      https://github.com/jsvine/pdfplumber
surfaced:  2026-05-21
what:      Lower-level than Docling: per-character coordinates, rectangles and precise table extraction with visual debugging.
alive:     10.3k★; commit/contributor/release detail unrecorded
why:       Fork it to pull exact fields from fixed-layout NZ forms (ADLS/REINZ agreements, LIM reports, rates statements) where positional control matters more than a blind text dump. Local-first: yes.
tags:      legal, pdf, char-coordinates, tables, fixed-layout, nz-forms

## JSv4/Python-Redlines
link:      https://github.com/JSv4/Python-Redlines
surfaced:  2026-05-21
what:      True Word-grade `.docx` tracked changes via the OpenXML WmlComparer.
alive:     108★; commit/contributor/release detail unrecorded
why:       A solid baseline; dropped on 05-21 as overlapping adeu and adding a .NET dependency, but it is the canonical OpenXML tracked-changes generator. The `.docx` tracked-changes emitter if you want OOXML-native diffing instead of adeu's Markdown round-trip. Local-first: yes.
tags:      legal, docx, ooxml, wmlcomparer, tracked-changes, dotnet-dep

## joanroig/midi-to-scaler-chord-sets
link:      https://github.com/joanroig/midi-to-scaler-chord-sets
surfaced:  2026-05-21
what:      Niche MIDI→Scaler chord-set converter.
alive:     commit/contributor/release detail unrecorded
why:       Dropped 05-21 as off-stack. The chord-set data shape if interoperating with Scaler is ever needed.
tags:      audio, chord, midi, scaler

## JJ110112/LiveChord
link:      https://github.com/JJ110112/LiveChord
surfaced:  2026-05-21
what:      Chord-related repo with no README or description to vet against.
alive:     no README at capture; commit/contributor/release detail unrecorded
why:       Skipped on 05-21 because there was nothing to vet. Nothing confirmed — revisit if a README appears.
tags:      audio, chord, unvetted, no-readme

## isaacus-dev/open-australian-legal-corpus-creator
link:      https://github.com/isaacus-dev/open-australian-legal-corpus-creator
surfaced:  2026-05-21
what:      The maintained scrapers + assembly pipeline behind the first open corpus of Australian legislation and case law.
alive:     120★; commit/contributor/release detail unrecorded
why:       Not NZ, but the closest live Commonwealth template: adapt its per-jurisdiction scraper/normaliser design to build your own offline NZ legislation+caselaw corpus (pointed at legislation.govt.nz XML or NZLII). Local-first: yes.
tags:      legal, corpus, scraper, commonwealth, caselaw, normaliser

## houfu/redlines
link:      https://github.com/houfu/redlines
surfaced:  2026-05-21
what:      A small, dependable library that turns two texts into Word-style strike-through/insert markup (HTML, Markdown, JSON, terminal) with change statistics.
alive:     157★; commit/contributor/release detail unrecorded
why:       Use it as the lightweight *display* primitive once your model has identified the substantive deltas. Local-first: yes.
tags:      legal, diff, markdown, display-primitive, change-stats

## google/diff-match-patch
link:      https://github.com/google/diff-match-patch
surfaced:  2026-05-21
what:      Battle-tested, multi-language fuzzy diff / patch / match — the canonical char-level diff.
alive:     8.1k★; archived 2024; commit/contributor/release detail unrecorded
why:       Dropped 05-21 (jsdiff covers prose granularity better) and archived 2024, but kept as a reference: it is the textbook fuzzy diff/patch implementation. Back-pocket fuzzy patch/match logic (relocating an edit after surrounding text moved) that jsdiff doesn't offer. Local-first: yes.
tags:      legal, diff, patch, fuzzy-match, canonical, archived

## geshang777/GaMMA
link:      https://github.com/geshang777/GaMMA
surfaced:  2026-05-21
what:      Research implementation for "joint global-temporal music understanding in large multimodal models" — an audio-LLM aimed at reasoning over both whole-track and time-localized musical structure.
alive:     paper repo rather than a packaged model; commit/contributor/release detail unrecorded
why:       Same direction as ASA's LLM layer and a useful second data point, but it's a paper repo rather than a packaged model, so it's less immediately usable than MOSS-Music. Read for the global+temporal music-understanding architecture; not a drop-in.
tags:      audio, audio-llm, understanding, research, structure

## fpachet/continuator
link:      https://github.com/fpachet/continuator
surfaced:  2026-05-21
what:      François Pachet's reimplementation of the Continuator: variable-order Markov modeling plus exact finite-chain inference to generate melodic and chord-sequence continuations with guaranteed positional constraints, real-time learning and tiny data needs.
alive:     commit/contributor/release detail unrecorded
why:       For Harmonia it's an interesting non-transformer approach to suggesting or completing progressions under hard constraints (e.g. "keep these anchor chords"); it's Python/symbolic, so it's a technique to borrow rather than code to lift.
tags:      audio, markov, continuation, constraints, symbolic

## excalidraw/excalidraw
link:      https://github.com/excalidraw/excalidraw
surfaced:  2026-05-21
what:      An embeddable hand-drawn whiteboard component that works offline and autosaves locally.
alive:     124k★; commit/contributor/release detail unrecorded
why:       Embed it in your Tauri app to sketch chain-of-title, easements, subdivision layouts or settlement timelines — visual matter mapping with everything stored on your machine. Local-first: partial (offline PWA / embeddable component, no backend).
tags:      legal, whiteboard, offline-pwa, embeddable, matter-mapping

## evolsb/legal-redline-tools
link:      https://github.com/evolsb/legal-redline-tools
surfaced:  2026-05-21
what:      Generates real tracked-changes `.docx` and redline PDFs from JSON edits.
alive:     29★; commit/contributor/release detail unrecorded
why:       Tiny but the most literally on-point: the exact deliverables lawyers send. Dropped 05-21 only for overlap with the adeu / Python-Redlines cluster. The "AI analysis (JSON edits) → Word markup + redline PDF" last mile, bolted onto your model's output. Local-first: yes.
tags:      legal, docx, redline-pdf, json-edits, tracked-changes, last-mile

## espanso/espanso
link:      https://github.com/espanso/espanso
surfaced:  2026-05-21
what:      A system-wide text expander driven by plain YAML bundles (with script/shell triggers) that fires in Word, email, anywhere — 100% local.
alive:     13.8k★; commit/contributor/release detail unrecorded
why:       Configure it as your legal snippet & boilerplate library: standard clauses, settlement-statement stock text, email replies, all from your own keystroke triggers. Local-first: yes.
tags:      legal, text-expander, yaml, snippets, boilerplate, system-wide

## emjjkk/beat-detection
link:      https://github.com/emjjkk/beat-detection
surfaced:  2026-05-21
what:      Small beat-detection repo.
alive:     commit/contributor/release detail unrecorded
why:       Under the quality/star bar on 05-21. Nothing beyond a minimal beat-onset reference; the beat stage is far better served by beat_this.
tags:      audio, beat, onset, minimal

## docling-project/docling
link:      https://github.com/docling-project/docling
surfaced:  2026-05-21
what:      Document-parsing engine that turns PDF/DOCX/PPTX into clean structured Markdown/JSON with tables and layout preserved, and runs air-gapped.
alive:     60.1k★; commit/contributor/release detail unrecorded
why:       The standout parser. Make it the ingestion layer under everything else — "drop a deed/contract → clean searchable text" that never touches the cloud. Local-first: yes.
tags:      legal, parser, pdf, docx, markdown, air-gapped

## dealfluence/adeu
link:      https://github.com/dealfluence/adeu
surfaced:  2026-05-21
what:      Flattens a Word doc to Markdown so a model can edit the substance, then projects the edits back as native Word Track Changes.
alive:     82★; Python (+ Node) implementations; commit/contributor/release detail unrecorded
why:       Cleanly separates meaning from formatting. Fork it as the output layer of your legal-impact comparator: a local model decides what should change, adeu emits the redlined `.docx` clients already know how to read. Local-first: yes.
tags:      legal, docx, ooxml, tracked-changes, redline, mcp, local-first

## curiousily/ragbase
link:      https://github.com/curiousily/ragbase
surfaced:  2026-05-21
what:      A small, fully-local chat-with-PDF skeleton (LangChain + Streamlit + Ollama/Llama 3.1 + Qdrant, with reranking and semantic chunking).
alive:     129★; quiet since 2024; commit/contributor/release detail unrecorded
why:       Dropped 05-21 as superseded by AnythingLLM, and quiet since 2024. Kept as a tinier base to own line-by-line if you want fewer moving parts than AnythingLLM. Local-first: yes.
tags:      legal, rag, local, streamlit, qdrant, minimal

## comorebi-notes/rechord
link:      https://github.com/comorebi-notes/rechord
surfaced:  2026-05-21
what:      React + Tone.js app for writing and sharing chord progressions.
alive:     still getting commits; a 2017 project; commit/contributor/release detail unrecorded
why:       On Harmonia's exact stack family (React + Tone.js + chords), so it's a usable reference for progression-entry UI and Tone.js playback wiring — but it's a 2017 sharing app with no reharmonization logic, so there's nothing to take on the theory side.
tags:      audio, react, tonejs, progressions, ui

## charmbracelet/bubbletea
link:      https://github.com/charmbracelet/bubbletea
surfaced:  2026-05-21
what:      An Elm-architecture TUI framework for Go.
alive:     42.6k★; commit/contributor/release detail unrecorded
why:       Dropped 05-21 as a stack choice (Tauri GUI was preferred), but it's the leading option if you'd rather build terminal tools than a desktop GUI — the shell for a keyboard-driven matter/diff TUI. Local-first: yes.
tags:      legal, tui, go, elm-architecture, terminal

## Ansvar-Systems/newzealand-law-mcp
link:      https://github.com/Ansvar-Systems/newzealand-law-mcp
surfaced:  2026-05-21
what:      Surfaced as a candidate NZ-law MCP server.
alive:     404 / nonexistent — a `repo:Ansvar-Systems/newzealand-law-mcp` lookup returns zero results
why:       Excluded on 05-21: the repository could not be found on GitHub. Nothing to fork.
tags:      legal, nz, mcp, 404, nonexistent

## andreamust/consonance-ACE
link:      https://github.com/andreamust/consonance-ACE
surfaced:  2026-05-21
what:      Audio chord-estimation Conformer that decomposes prediction into separate root / bass / pitch-activation heads with consonance-based label smoothing, shipping a pretrained checkpoint and inference that turns WAV into 170-class timestamped chord `.lab` output.
alive:     ships a pretrained checkpoint; commit/contributor/release detail unrecorded
why:       Directly relevant to ASA's existing chord-detection stage as a modern, theory-informed model you can run server-side, and its timestamped chord stream is exactly the input Harmonia consumes — so it sits across both projects. Run server-side as a modern, theory-informed replacement for the chord stage.
tags:      audio, chord, conformer, ace, lab, model

## adamstark/Gist
link:      https://github.com/adamstark/Gist
surfaced:  2026-05-21
what:      Established C++ real-time audio-analysis library (onset, pitch, FFT/MFCC features).
alive:     commit/contributor/release detail unrecorded
why:       Solid, but offers nothing beyond what native Essentia already gives ASA's L1; logged for completeness.
tags:      audio, native, cpp, established, features

## Yuan-ManX/audio-development-tools
link:      https://github.com/Yuan-ManX/audio-development-tools
surfaced:  2026-05-20
what:      An awesome-list of audio development tools.
alive:     commit/contributor/release detail unrecorded
why:       Awesome-list, not a tool. Logged for completeness.
tags:      audio, awesome-list

## tyiannak/pyAudioAnalysis
link:      https://github.com/tyiannak/pyAudioAnalysis
surfaced:  2026-05-20
what:      Established Python MIR library: MFCC, chroma, segmentation, classification.
alive:     commit/contributor/release detail unrecorded
why:       A native, importable baseline feature/segmentation set to compare Essentia's output against; long-known, nothing novel.
tags:      audio, native, python, features, segmentation, baseline

## pettarin/awesome-python-audio-research
link:      https://github.com/pettarin/awesome-python-audio-research
surfaced:  2026-05-20
what:      An awesome-list of Python audio research tooling.
alive:     commit/contributor/release detail unrecorded
why:       Awesome-list, not a tool. Logged for completeness.
tags:      audio, awesome-list, python

## NeptuneHub/AudioMuse-AI
link:      https://github.com/NeptuneHub/AudioMuse-AI
surfaced:  2026-05-20
what:      The analysis core behind the NV/Jellyfin plugins: Flask + Redis/RQ workers + PostgreSQL + Docker/K8s, librosa/ONNX/CLAP, REST + Swagger, and a chat module.
alive:     1.7k★; very active, active 2026-05; commit/contributor/release detail unrecorded
why:       A concrete, working blueprint for ASA's hosted worker-queue mode — copy the Flask + RQ + Postgres + container topology and the REST/Swagger surface.
tags:      audio, flask, redis-rq, postgres, k8s, queue, blueprint

## maxrmorrison/torchcrepe
link:      https://github.com/maxrmorrison/torchcrepe
surfaced:  2026-05-20
what:      PyTorch port of the CREPE pitch tracker (per-frame F0 + periodicity/confidence, with decoding and filtering helpers).
alive:     commit/contributor/release detail unrecorded
why:       ASA's own L2 dependency — runs on Demucs stems for note/pitch analysis. Keep current and reuse its periodicity-thresholding/decoding as the reference for the pitch stage. Noted and logged for completeness on 05-20.
tags:      audio, pitch, crepe, f0, pytorch, core-dep

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

## facebookresearch/demucs
link:      https://github.com/facebookresearch/demucs
surfaced:  2026-05-20
what:      Hybrid Transformer Demucs — the state-of-the-art music source-separation model.
alive:     commit/contributor/release detail unrecorded
why:       ASA's own L2 dependency (stems feed torchcrepe pitch). The model ASA already runs; the thing to keep current, swap variants of, or speed up (see demucs-next / demucs-mlx). Noted and logged for completeness on 05-20.
tags:      audio, pytorch, separation, core-dep, model

## audeering/opensmile
link:      https://github.com/audeering/opensmile
surfaced:  2026-05-20
what:      Mature C++ feature toolkit (speech + music) with Python wheels and reference-grade feature sets.
alive:     commit/contributor/release detail unrecorded
why:       Reference feature-set definitions and a second native extractor; speech-leaning, so cherry-pick the music-relevant descriptors.
tags:      audio, native, features, reference-sets, speech

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

## snejus/beetcamp
link:      https://github.com/snejus/beetcamp
surfaced:  2026-05-19
what:      Bandcamp metadata autotagger plugin for beets.
alive:     commit/contributor/release detail unrecorded
why:       Off-topic — catalog metadata, no audio analysis. Only relevant if a Bandcamp-import metadata path were ever needed.
tags:      audio, bandcamp, metadata, beets, off-topic

## Rezonality/zing
link:      https://github.com/Rezonality/zing
surfaced:  2026-05-19
what:      GUI audio-I/O toolkit.
alive:     commit/contributor/release detail unrecorded
why:       Not MIR; re-checked on 05-20 and stays dropped.
tags:      audio, audio-io, gui, off-domain

## Polochon-street/bliss-rs
link:      https://github.com/Polochon-street/bliss-rs
surfaced:  2026-05-19
what:      Rust song-analysis library that extracts chroma, tempo and timbral features to compute track-to-track distance for automatic playlists (Spotify-Radio style).
alive:     159★; active 2026-05; commit/contributor/release detail unrecorded
why:       The compact feature vector and similarity framing are a clean reference if ASA grows a "tracks like this" axis, server-side. Calling it "off-stack" was the old browser bias — Rust is first-class.
tags:      audio, rust, similarity, chroma, tempo, playlists

## pianosnake/ireal-reader
link:      https://github.com/pianosnake/ireal-reader
surfaced:  2026-05-19
what:      Node module that parses iReal Pro exports into JS objects: title/composer/key/BPM plus a `measures` array of chord-symbol arrays, with repeats/segnos/codas expanded to linear measures.
alive:     43★; active 2026-05; commit/contributor/release detail unrecorded
why:       A direct ingest path for Harmonia — the entire iReal Pro jazz corpus becomes structured chord progressions with almost no parsing work.
tags:      audio, ireal, chords, parser, dataset

## MTG/gaia
link:      https://github.com/MTG/gaia
surfaced:  2026-05-19
what:      Essentia's own C++/Python companion: similarity measures and SVM classifiers over Essentia descriptors, producing the high-level models Essentia loads to label music.
alive:     297★; still pushed in 2026 but last release 2019; commit/contributor/release detail unrecorded
why:       The upstream answer for "turn my low-level descriptors into mood/genre/danceability tags." Stale — prefer essentia-TF embeddings + a vector store; treat as reference. The original drop rationale was literally "C++/AGPL and not browser-friendly," which was the bias.
tags:      audio, essentia, similarity, classifier, stale, reference

## lunashia/o-m_beatmap_trainer
link:      https://github.com/lunashia/o-m_beatmap_trainer
surfaced:  2026-05-19
what:      osu!mania next-event beatmap trainer.
alive:     commit/contributor/release detail unrecorded
why:       The README never exposes the audio-feature layer and it's game-specific. Nothing usable — the rhythm-game beatmap framing is the only (off-target) idea.
tags:      audio, beatmap, osu, game-specific

## CPJKU/partitura
link:      https://github.com/CPJKU/partitura
surfaced:  2026-05-19
what:      Python library for symbolic scores across MusicXML, MIDI, Humdrum kern and MEI, exposing notes (pitch/duration/voice/staff), parts, time signatures and beat maps.
alive:     350★; pushed 2026-05; commit/contributor/release detail unrecorded
why:       Off-stack (Python, not JS) but the cleanest reference for a complete symbolic data model if Harmonia ever needs richer score import/export than Tonal.js + MusicXML. Copy its note/part/timeline model.
tags:      audio, symbolic, musicxml, mei, kern

## CPJKU/beat_this
link:      https://github.com/CPJKU/beat_this
surfaced:  2026-05-19
what:      Official ISMIR-2024 beat/downbeat tracker ("Beat This!") that drops the traditional DBN post-processing step in favour of a transformer with a shift-tolerant loss, shipping CLI + Python API and `.beats` export.
alive:     286★; created 2024, active 2026-05; commit/contributor/release detail unrecorded
why:       A current, accurate drop-in for ASA's tempo/beat stage that's lighter to wire up than madmom — fork the inference path and the `.beats` schema.
tags:      audio, beat, downbeat, tempo, transformer, ismir2024

## christopherwxyz/remix-mcp
link:      https://github.com/christopherwxyz/remix-mcp
surfaced:  2026-05-19
what:      Rust Ableton-control MCP with 266 tools over OSC — control-only, no analysis despite the name.
alive:     266★; commit/contributor/release detail unrecorded
why:       Originally dropped as "more Ableton MCP / Link plumbing"; on-theme for ASA's Ableton+LLM control surface. A Rust reference for an OSC-based Ableton control layer if ASA's companion wants a native (non-M4L) write path.
tags:      audio, ableton, mcp, osc, rust

## astradzhao/music-rfm
link:      https://github.com/astradzhao/music-rfm
surfaced:  2026-05-19
what:      Recursive-feature-machine steering for autoregressive music generation.
alive:     commit/contributor/release detail unrecorded
why:       Interesting paper, narrow utility for either project. The RFM-steering idea only.
tags:      audio, research, steering, generation

## a1ex90/MusicalKeyCNN
link:      https://github.com/a1ex90/MusicalKeyCNN
surfaced:  2026-05-19
what:      CQT-spectrogram CNN (after Korzeniowski & Widmer) for key estimation with pitch-shift augmentation, trained on GiantSteps, outputting Camelot-wheel labels at ~73.5% MIREX-weighted.
alive:     50★; created 2025-06; commit/contributor/release detail unrecorded
why:       Competitive with Mixed In Key. Full preprocessing/training/eval code, not a wrapper: a key signal both for ASA's tonal analysis and for grounding Harmonia's reharmonization in a detected key. Reuse the pitch-shift augmentation recipe.
tags:      audio, key, cnn, cqt, camelot, model

## ifeelvoid/keyfinder
link:      https://github.com/ifeelvoid/keyfinder
surfaced:  2026-05-18
what:      Native macOS app + VST/AU that detects key (Camelot), BPM and renders waveforms via a custom Krumhansl-Schmuckler engine (16k-point FFT, bass weighting), sharing one Swift `KeyFinderEngine` package across app and plugin.
alive:     45★; created 2026-03; commit/contributor/release detail unrecorded
why:       Off-stack (Swift/macOS) but a tidy worked example of a from-scratch K-S key detector and the app↔plugin shared-engine split. First pass called it "a thin product, off-stack."
tags:      audio, key, krumhansl, swift, vst

## dogayuksel/webKeyFinder
link:      https://github.com/dogayuksel/webKeyFinder
surfaced:  2026-05-18
what:      libKeyFinder (C++) compiled to WASM via Emscripten, fed by an AudioWorkletProcessor and Web Workers, wrapped in Preact.
alive:     35★; pushed 2026-03; commit/contributor/release detail unrecorded
why:       The cleanest current template for the exact plumbing Harmonia would need to add audio→key: WASM DSP in a worker, worklet pulling PCM, all in-browser. For ASA the real nugget is the underlying native libKeyFinder (run it server-side, skip the WASM).
tags:      audio, key, wasm, libkeyfinder, worklet

## casantosmu/audiodeck
link:      https://github.com/casantosmu/audiodeck
surfaced:  2026-05-18
what:      Self-hostable web spectrogram analyzer (Go server, browser-side render) aimed at sniffing out fake-lossless files via frequency-cutoff artifacts.
alive:     109★; created 2025-09; commit/contributor/release detail unrecorded
why:       Analysis itself is shallow, but the "thin Go shim + client-side spectrogram" topology is a clean shape to mimic if ASA grows a library-scan UI. The Go server-side analysis justifies it; the browser render is incidental.
tags:      audio, go, spectrogram, fake-lossless, server-side, library-scan

## brightlikethelight/music21-mcp-server
link:      https://github.com/brightlikethelight/music21-mcp-server
surfaced:  2026-05-18
what:      FastMCP server exposing 13 music21 tools — Roman numerals, cadence detection, voice leading, harmonization, counterpoint — plus HTTP/CLI mirrors for when MCP itself misbehaves.
alive:     22★; commit/contributor/release detail unrecorded
why:       Worth a look as the "music theory through an LLM" surface, but read the author's own "40-50% MCP production success rate" caveat before treating it as load-bearing. A FastMCP server exposing analysis/theory tools to an LLM *is* ASA's MCP-tool pattern — copy the tool-wrapping pattern and the HTTP/CLI fallback design.
tags:      audio, mcp, music21, theory, fastmcp

## zsteinkamp/m4l-Knobbler4
link:      https://github.com/zsteinkamp/m4l-Knobbler4
surfaced:  2026-05-17
what:      Max-for-Live OSC parameter-control surface for tablets.
alive:     commit/contributor/release detail unrecorded
why:       A tool, not a platform, with no MIR/theory content. OSC-control surface wiring only, if a hardware/tablet control idea ever surfaces.
tags:      audio, m4l, osc, control

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

## uisato/ableton-mcp-extended
link:      https://github.com/uisato/ableton-mcp-extended
surfaced:  2026-05-17
what:      Extended Ableton MCP with parallel TCP + UDP servers (UDP for low-latency real-time control), ElevenLabs TTS for in-session narration/voice samples, and a custom-controller framework.
alive:     203★; Python; commit/contributor/release detail unrecorded
why:       First dropped as "yet another Ableton MCP fork with too much overlap," then kept: same family as producer-pal / bschoepke's ableton-live-mcp, but the UDP path and the controller-extension scaffold are the differentiators. Lift the UDP low-latency control path if a Live companion ever needs realtime parameter moves.
tags:      audio, ableton, mcp, udp, tts

## simonholliday/subsequence
link:      https://github.com/simonholliday/subsequence
surfaced:  2026-05-17
what:      Generative MIDI sequencer.
alive:     commit/contributor/release detail unrecorded
why:       Not analysis. Generative-sequencer UX ideas only.
tags:      audio, midi, sequencer, generative

## scragnog/HOT-Step-CPP
link:      https://github.com/scragnog/HOT-Step-CPP
surfaced:  2026-05-17
what:      UI shim over `acestep.cpp`.
alive:     commit/contributor/release detail unrecorded
why:       ACE-Step is already on the seen list. Nothing beyond the ACE-Step model itself.
tags:      audio, ui-shim, acestep, cpp

## rsxdalv/TTS-WebUI
link:      https://github.com/rsxdalv/TTS-WebUI
surfaced:  2026-05-17
what:      Generation/TTS WebUI.
alive:     commit/contributor/release detail unrecorded
why:       No analysis surface. Multi-model WebUI scaffolding only.
tags:      audio, tts, webui, generation

## phones24/ep133-export-to-daw
link:      https://github.com/phones24/ep133-export-to-daw
surfaced:  2026-05-17
what:      PWA that reads `.pak` backups (or talks live over WebMIDI) from Teenage Engineering EP-133/EP-1320/EP-40 and exports Ableton Live projects, DAWproject archives, REAPER projects and MIDI — including sample envelopes and stretch modes.
alive:     88★; TypeScript; commit/contributor/release detail unrecorded
why:       Hardware-bound but the WebMIDI → DAWproject pipeline is reusable plumbing if Harmonia ever round-trips to a DAW, or if ASA ever round-trips its recommendations into a project file.
tags:      audio, webmidi, dawproject, ableton, export

## pedromsantos/vaughan
link:      https://github.com/pedromsantos/vaughan
surfaced:  2026-05-17
what:      Music-theory library in F#.
alive:     commit/contributor/release detail unrecorded
why:       Off-stack. Functional-style theory modeling reference.
tags:      audio, theory, fsharp

## paladini/voice-separator-demucs
link:      https://github.com/paladini/voice-separator-demucs
surfaced:  2026-05-17
what:      FastAPI front in front of Demucs.
alive:     commit/contributor/release detail unrecorded
why:       Dropped three times as "a thin Demucs wrapper / same shape as a dozen others" — but FastAPI + Demucs is exactly ASA's L2-as-a-service shape. A minimal reference for wrapping the separator as an endpoint.
tags:      audio, fastapi, demucs, service

## Natooz/MidiTok
link:      https://github.com/Natooz/MidiTok
surfaced:  2026-05-17
what:      The canonical MIDI/abc tokenizer library: REMI, REMI+, MIDI-Like, TSD, Structured, CPWord, Octuple, MuMIDI, MMM, PerTok; BPE/Unigram/WordPiece training; HF Hub integration; Symusic-backed I/O.
alive:     870★; commit/contributor/release detail unrecorded
why:       Well-known to anyone in symbolic music gen — included only because it's the obvious dependency if Harmonia ever ingests/produces token sequences. Adopt rather than reimplement. Skip if you already know it.
tags:      audio, tokenizer, midi, symbolic

## MTG/essentia
link:      https://github.com/MTG/essentia
surfaced:  2026-05-17
what:      The native C++/Python MIR library (spectral, MFCC, YinFFT, key, onset, EBU R128) plus the Essentia model zoo.
alive:     commit/contributor/release detail unrecorded
why:       ASA's own core Phase-1 dependency. Dropped twice — as "the parent C++ library; ASA already depends on Essentia.js downstream" and "ASA's own upstream" — which was the flagship bias casualty: ASA's actual core dep is native Essentia 2.1b6, this library. The algorithm reference and upgrade target; lift the exact algos L1 needs and the pretrained TF model set (genre/mood/danceability).
tags:      audio, essentia, dsp, core-dep, model-zoo

## mhartzel/freelcs
link:      https://github.com/mhartzel/freelcs
surfaced:  2026-05-17
what:      Hotfolder-driven EBU R128 loudness-correction server (Python, Docker, mono → 5.1, per-stream).
alive:     25★; repo started 2012 but still pushed in 2026; README unreachable at one point; commit/contributor/release detail unrecorded
why:       Dropped twice as "not newly relevant" and "old, jivetalking already covers measure-then-correct," then kept: old code, but the drop-in/processed-out pipeline shape and the visual loudness-history output are a useful reference for ASA's loudness stage UX and topology.
tags:      audio, python, r128, docker, loudness-server, old

## markwilkins/midi-chord-reader
link:      https://github.com/markwilkins/midi-chord-reader
surfaced:  2026-05-17
what:      JUCE/C++ DAW plugin that names chords from a MIDI track during playback — normalises to a single octave while preserving the bass note, generates slash inversions (`Am/C`), filters 2nd/4th/6th passing tones, uses the lowest three notes for quality.
alive:     22★; commit/contributor/release detail unrecorded
why:       Tiny but a useful reference heuristic if Harmonia ever wants "given these MIDI notes, name the chord" outside its Tonal.js path.
tags:      audio, chord, midi, juce, heuristic

## k2-fsa/sherpa-onnx
link:      https://github.com/k2-fsa/sherpa-onnx
surfaced:  2026-05-17
what:      Primarily a speech toolkit (ASR/TTS/speaker-diarization) on the ONNX runtime, with many language bindings.
alive:     commit/contributor/release detail unrecorded
why:       The music angle is marginal. Only if ASA ever needs on-device ASR (e.g. lyric transcription) — the ONNX deployment plumbing, not anything music-MIR.
tags:      audio, speech, asr, onnx

## gluon/Void-LinkAudio
link:      https://github.com/gluon/Void-LinkAudio
surfaced:  2026-05-17
what:      Umbrella project for sample-accurate beat-synced audio over LAN between Max, TouchDesigner, VCV Rack, openFrameworks and Live 12.4+; v0.3 adds Linux ARM64/x86_64 for VCV and Pure Data.
alive:     25–40★ (recorded inconsistently across sweeps); active 2026-04; commit/contributor/release detail unrecorded
why:       Same author as the already-logged `gluon/ofxAbletonLinkAudio` (the openFrameworks sub-addon) — worth swapping the seen entry for if you only want the top-level project. Reference for sample-accurate inter-app audio transport if ASA ever needs to pull live audio from Ableton over the network rather than from a file.
tags:      audio, ableton-link, lan, audio-transport

## dreamrec/LivePilot
link:      https://github.com/dreamrec/LivePilot
surfaced:  2026-05-17
what:      The most ambitious Ableton-MCP so far: 465 tools / 56 domains, a 5,264-device atlas, an optional M4L spectral-perception bridge (9-band FFT, RMS/peak, Krumhansl-Schmuckler key, pitch, FluCoMa mel/chroma/onset), VST/AU/AAX corpus discovery, and 12 "creative engines" with before/after measurement.
alive:     21★; Python; active 2026-03; commit/contributor/release detail unrecorded
why:       Sits across both projects: the in-DAW analysis bridge is ASA-adjacent and the Krumhansl-Schmuckler key + chroma path is Harmonia-adjacent. The closest existing analog to *all* of ASA — Ableton MCP + an analysis bridge + a measure→act→measure loop. It was later dropped as "more Ableton plumbing," a direct artifact of not knowing ASA is Ableton+analysis+LLM. The K-S-key + chroma bridge is the harmonic nugget to fork.
tags:      audio, ableton, mcp, key, chroma, agentic

## dr-schlange/nallely-midi
link:      https://github.com/dr-schlange/nallely-midi
surfaced:  2026-05-17
what:      MIDI router / sequencer.
alive:     commit/contributor/release detail unrecorded
why:       Not analysis. MIDI-routing patterns only, if inter-device MIDI plumbing is ever needed.
tags:      audio, midi, router

## Conceptual-Machines/magda-core
link:      https://github.com/Conceptual-Machines/magda-core
surfaced:  2026-05-17
what:      AI-first DAW on C++20/JUCE/Tracktion Engine: natural-language chat generates a custom DSL that mutates the session, hybrid audio+MIDI tracks, 16 LFOs + 16 macros per device, nestable parallel racks, juce-llm + llama.cpp for local inference.
alive:     124★; C++; created 2026-01; commit/contributor/release detail unrecorded
why:       Tangential to both ASA and Harmonia but the cleanest "AI as a first-class DAW citizen" reference around — interesting precedent if either project ever sprouts an agentic surface. Study the NL→DSL→session-edit loop; the DSL-as-LLM-target design is the transferable idea.
tags:      audio, daw, juce, nl-dsl, agentic

## bschoepke/ableton-live-mcp
link:      https://github.com/bschoepke/ableton-live-mcp
surfaced:  2026-05-17
what:      General-purpose Ableton MCP whose bet is "let the agent `eval` arbitrary Python inside Ableton, with a few hot-path tools for latency/reliability."
alive:     184★; Python; created 2026-05; active 2026-05; latency-tuned via Codex's `/goal`; commit/contributor/release detail unrecorded
why:       Different philosophy from producer-pal (curated tools); worth a read for the trade-off, but the third Ableton-MCP on the seen list — diminishing returns. The latency hot-path tooling is the reusable bit.
tags:      audio, ableton, mcp, eval, latency

## Boof2015/astra
link:      https://github.com/Boof2015/astra
surfaced:  2026-05-17
what:      Electron + native C++ DSP audiophile player: 10-band parametric EQ with live frequency-response, seven realtime visualizers on a customizable rack, gapless bit-perfect output (WASAPI Exclusive / CoreAudio HAL / ALSA hw), Dolby Atmos decode.
alive:     247★; created 2026-01; commit/contributor/release detail unrecorded
why:       The decoupled analysis-path-vs-output-path architecture and the visualizer rack UX are both directly cribbable for ASA.
tags:      audio, electron, cpp, eq, visualizer-rack, architecture

## andremichelle/openDAW
link:      https://github.com/andremichelle/openDAW
surfaced:  2026-05-17
what:      Web-based DAW, AGPL, deliberately framework-light (Tauri/PWA wrapping wanted), with no MIR or analysis surface — pure composition.
alive:     1.6k★; created 2025-02; commit/contributor/release detail unrecorded
why:       The web-audio engineering and the project's "no SignUp / no Tracking" ethos are useful references for browser-first tools. A browser-bias survivor otherwise: ASA isn't a web DAW. Web-audio engine architecture only, if a browser front ever matters.
tags:      audio, web-daw, webaudio, agpl

## albertms10/music_notes
link:      https://github.com/albertms10/music_notes
surfaced:  2026-05-17
what:      Music-theory library in Dart.
alive:     commit/contributor/release detail unrecorded
why:       Off-stack for a JS Harmonia. Reference for a clean theory type-model (intervals/keys/scales).
tags:      audio, theory, dart

## WB2024/Essentia-to-Metadata
link:      https://github.com/WB2024/Essentia-to-Metadata
surfaced:  2026-05-14
what:      Local genre/mood tagger built on Essentia's Discogs-Effnet embeddings, Discogs-400 genre CNN and MTG-Jamendo mood classifier, writing tags straight to files.
alive:     75★; created 2026-02; commit/contributor/release detail unrecorded
why:       Relevant as a worked example of running Essentia's pretrained ML models fully offline — it's classification, not the tonal/loudness analysis ASA centers on, though the per-format tag-writing layer matters more than the first pitch implied.
tags:      audio, essentia-tf, genre, mood, offline

## sildater/parangonar
link:      https://github.com/sildater/parangonar
surfaced:  2026-05-14
what:      Score-to-performance alignment library.
alive:     commit/contributor/release detail unrecorded
why:       Solid, but neither project does symbolic alignment. The alignment algorithms if note-to-performance matching ever becomes a feature.
tags:      audio, alignment, symbolic

## Ryan5453/demucs-next
link:      https://github.com/Ryan5453/demucs-next
surfaced:  2026-05-14
what:      Modernized fork of Demucs (current PyTorch/TorchCodec, Cog REST integration) reporting ~2–3× faster separation at equal-or-better SDR.
alive:     26★; alpha; commit/contributor/release detail unrecorded
why:       Only relevant if ASA adds a stem-separation pre-stage; it's a straight speed/packaging refresh of a model you'd already reach for — except separation is current L2 scope, which makes it a direct speed win with REST packaging.
tags:      audio, pytorch, demucs-fork, faster, cog-rest

## openclaw/songsee
link:      https://github.com/openclaw/songsee
surfaced:  2026-05-14
what:      Go CLI that renders 9 frequency-domain views — spectrogram, mel, chroma, HPSS, self-similarity, loudness, tempogram, MFCC, spectral flux — from any ffmpeg-readable file with no Python deps.
alive:     59★; created 2026-01; commit/contributor/release detail unrecorded
why:       ASA needs almost exactly this set of mel/loudness/tonal visuals; the native-Go FFT pipeline and the grid-combining output are worth studying.
tags:      audio, go, spectrogram, mel, chroma, hpss, tempogram, viz

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

## JuzzyDee/audio-analyzer-rs
link:      https://github.com/JuzzyDee/audio-analyzer-rs
surfaced:  2026-05-14
what:      Pure-Rust MCP server that extracts the whole MIR stack — spectral centroid/bandwidth/rolloff/flatness, Krumhansl-Schmuckler key detection, pitch-class distribution, tonnetz, MFCCs, EBU R128 LUFS/true-peak/LRA, crest factor, HPSS, stereo field and section boundaries — in under 2s per track with no Python or FFmpeg.
alive:     21★; created 2026-03; commit/contributor/release detail unrecorded
why:       It's essentially ASA's entire feature set in one dependency-free crate, and the key / pitch-class / tonnetz outputs feed Harmonia's harmonic analysis too. Lift the dependency-free K-S key + pitch-class + tonnetz code as a server-side harmonic core, and the MCP tool surface as the "expose analysis to an LLM" pattern.
tags:      audio, rust, mcp, key, tonnetz, r128, mir-app

## JulienVincenot/MOZLib
link:      https://github.com/JulienVincenot/MOZLib
surfaced:  2026-05-14
what:      Max/Lisp computer-aided-composition teaching package.
alive:     commit/contributor/release detail unrecorded
why:       Off-stack for both. CAC technique ideas only.
tags:      audio, cac, max, lisp

## jhartquist/resonators
link:      https://github.com/jhartquist/resonators
surfaced:  2026-05-14
what:      Rust implementation of the Resonate algorithm — a fixed-memory, per-sample alternative to FFT/CQT for low-latency spectral analysis — with Python and WebAssembly bindings.
alive:     86★; created 2026-04; commit/contributor/release detail unrecorded
why:       The WASM target makes it a plausible drop-in for a browser DSP stage wanting sharper per-bin time-frequency tradeoffs than a stock STFT — though ASA has no browser DSP, so that rationale is void; what's left is the Rust→PyO3 per-sample spectral angle, niche next to Essentia.
tags:      audio, rust, per-sample, spectral, pyo3

## flarkflarkflark/STEMwerk-reaper
link:      https://github.com/flarkflarkflark/STEMwerk-reaper
surfaced:  2026-05-14
what:      REAPER plugin: Lua glue calling audio-separator/Demucs from the DAW.
alive:     commit/contributor/release detail unrecorded
why:       A thin wrapper around audio-separator/Demucs; nothing new beyond the DAW integration. Logged for completeness.
tags:      audio, reaper, lua, wrapper, thin

## DarienBrito/EssentiaTD
link:      https://github.com/DarienBrito/EssentiaTD
surfaced:  2026-05-14
what:      Five C++ CHOP plugins wrapping Essentia for TouchDesigner: spectrum, mel bands, MFCCs, pitch, key/scale, onset/BPM and EBU R128 loudness, in both realtime and batch modes.
alive:     91★; created 2026-03; commit/contributor/release detail unrecorded
why:       It's the cleanest recent map of which Essentia algorithms cover ASA's tonal-balance / dynamics / loudness brief and how to split realtime vs full-file analysis.
tags:      audio, essentia, mel, loudness, key, onset

## crlandsc/torch-l1-snr
link:      https://github.com/crlandsc/torch-l1-snr
surfaced:  2026-05-14
what:      L1-SNR loss functions for training separation models.
alive:     commit/contributor/release detail unrecorded
why:       Neither ASA nor Harmonia trains models — ASA runs pretrained Demucs. Only relevant if you ever fine-tune.
tags:      audio, pytorch, training-loss, out-of-scope

## craiglush/navidrome-mood-plugin
link:      https://github.com/craiglush/navidrome-mood-plugin
surfaced:  2026-05-14
what:      Navidrome plugin using essentia-tensorflow + Discogs-EffNet to score mood, danceability, energy and BPM with genre-aware corrections, then auto-building 13 themed playlists.
alive:     55★; created 2026-03; commit/contributor/release detail unrecorded
why:       Useful as a reference for Essentia-TF embeddings and the genre-context-boost trick; it's a media-server plugin, not a DSP library. It ships a separate FastAPI analyzer *because "essentia can't run inside WASM"* — which directly validates ASA's server-side architecture.
tags:      audio, essentia-tf, fastapi, mood, validates-arch

## Angel2mp3/AudioAuditor
link:      https://github.com/Angel2mp3/AudioAuditor
surfaced:  2026-05-14
what:      Windows app that flags fake-lossless upsampling, digital clipping, MQA and AI-generated audio, plus dynamic-range and true-peak (4× oversampled) measurement and a log-frequency spectrogram viewer.
alive:     70★; C#; created 2026-03; commit/contributor/release detail unrecorded
why:       The dynamics + true-peak + spectral-ceiling logic overlaps ASA's dynamics stage directly; it's C#/Windows so treat it as reference, not reuse. The "diagnose-then-recommend" shape is the transferable part.
tags:      audio, dynamics, true-peak, clipping, fake-lossless, reference

## williamzujkowski/live-coding-music-mcp
link:      https://github.com/williamzujkowski/live-coding-music-mcp
surfaced:  2026-05-13
what:      MCP server exposing Strudel.cc to Claude/Anthropic clients for live-coded pattern generation.
alive:     200★; TypeScript; created 2025-08; commit/contributor/release detail unrecorded
why:       Same MCP-in-the-DAW family as producer-pal but on the browser-pattern side; included mainly as a second data point if Harmonia ever wants an LLM-driven "reharm-as-pattern" channel. Nothing on the analysis path.
tags:      audio, mcp, strudel, livecoding, generation

## WeebLabs/DSPi
link:      https://github.com/WeebLabs/DSPi
surfaced:  2026-05-13
what:      RP2040 audio-DSP firmware.
alive:     commit/contributor/release detail unrecorded
why:       Hardware-only (microcontroller firmware); off a server-side software stack. Logged for completeness.
tags:      audio, hardware, rp2040, firmware

## vpavlenko/rawl
link:      https://github.com/vpavlenko/rawl
surfaced:  2026-05-13
what:      React+TS MIDI/MusicXML visualizer that color-codes pitch classes ("12 colors") and annotates harmonic language across classical, jazz, chiptune and modal systems.
alive:     81★; commit/contributor/release detail unrecorded
why:       Worth studying for piano-roll rendering and pedagogically motivated harmony annotations; the "harmony as flags" framing is a Harmonia-adjacent take. Reuse the 12-color pitch-class palette for any harmonic visualization.
tags:      audio, visualizer, harmony, pianoroll, midi

## sweetspotsoundsystem/stemgen-rt
link:      https://github.com/sweetspotsoundsystem/stemgen-rt
surfaced:  2026-05-13
what:      Real-time HS-TasNet 4-stem separation as a JUCE/VST3/AU plugin at 11.6 ms latency, with async inference threading and crossover/gating DSP polish.
alive:     27★; created 2026-01; inference model is binary-only; commit/contributor/release detail unrecorded
why:       Reference for the *plumbing* (async ONNX in a plugin callback, 44.1k constraint) rather than a model to lift.
tags:      audio, juce, vst, realtime, tasnet, plumbing

## ssmall256/demucs-mlx
link:      https://github.com/ssmall256/demucs-mlx
surfaced:  2026-05-13
what:      Demucs ported to Apple MLX — pip-importable (`from demucs_mlx import Separator`), ~73× realtime on Apple Silicon.
alive:     commit/contributor/release detail unrecorded
why:       Dropped as "a straight port of a known model" — but ASA is local-first and its users are Mac producers, so it's an L2 drop-in for fast on-device separation.
tags:      audio, mlx, apple-silicon, demucs, drop-in, local-first

## spyroskantarelis/chordonomicon
link:      https://github.com/spyroskantarelis/chordonomicon
surfaced:  2026-05-13
what:      666K symbolic chord progressions with section labels (verse/chorus/bridge), genre and release date, encoded as single chord / triad (root+quality+bass) / tetrad (+extensions) tokens on Hugging Face.
alive:     143★; commit/contributor/release detail unrecorded
why:       Drop-in training/eval set for any reharmonization model and a benchmark with RNN/GRU/LSTM baselines already published — fork the tokenization scheme and baselines.
tags:      audio, dataset, chords, progressions, hf

## sanderwood/clamp3
link:      https://github.com/sanderwood/clamp3
surfaced:  2026-05-13
what:      ACL 2025 framework that contrastively aligns text, sheet music, audio (via MERT features), MIDI and images into one 27-language embedding space — CLAP but multi-modal.
alive:     239★; Python; created 2025-02, active 2025-02; commit/contributor/release detail unrecorded
why:       The value is the audio-side feature extractor and the retrieval primitives (find tracks-like-this, prompt-to-track) — drop in ahead of any reach for tagging/similarity.
tags:      audio, embeddings, multimodal, retrieval, clap

## rzru/nightingale
link:      https://github.com/rzru/nightingale
surfaced:  2026-05-13
what:      Tauri (Rust + React) karaoke app combining Demucs/UVR vocal isolation, WhisperX/Parakeet-v3 lyric transcription with word timestamps, real-time pitch scoring, and key/tempo shifting.
alive:     1.1k★; created 2026-03, active 2026-03; commit/contributor/release detail unrecorded
why:       Hits both projects: the local-PyTorch-from-Tauri shape is a template for ASA, and the pitch-scoring/key-shift logic is adjacent to Harmonia's note-domain code.
tags:      audio, tauri, demucs, transcription, pitch, key-shift

## ptnghia-j/ChordMiniApp
link:      https://github.com/ptnghia-j/ChordMiniApp
surfaced:  2026-05-13
what:      Next.js + Flask app that does chord recognition (Chord-CNN-LSTM, BTC-SL/PL from ISMIR2019), beat tracking (Beat-Transformer + madmom), lyrics (Music.ai + LRClib), and renders sheet via OpenSheetMusicDisplay with chord-db guitar diagrams.
alive:     282★; TypeScript; commit/contributor/release detail unrecorded
why:       This is the closest public neighbor to Harmonia's product surface; read its UX choices before adding new ones. The Flask chord-recognition service is a forkable audio→chord backend.
tags:      audio, chord, beat, lyrics, sheet, nextjs

## prabal-rje/latentscore
link:      https://github.com/prabal-rje/latentscore
surfaced:  2026-05-13
what:      Retrieval-based ambient music generation: a sentence-transformer (or LAION-CLAP) embeds a prompt, cosine-matches against ~10k pre-computed synth configs, and drives a real-time CPU synth — no GPU, ~2s latency.
alive:     36★; Python; commit/contributor/release detail unrecorded
why:       Interesting as a "music as configuration retrieval" pattern; not a generative model in the usual sense. A cheap, no-GPU template for an audition path that wants config retrieval rather than neural generation.
tags:      audio, retrieval, ambient, clap, synth

## openvpi/GAME
link:      https://github.com/openvpi/GAME
surfaced:  2026-05-13
what:      Singing-voice → MIDI transcription via D3PM (structured denoising diffusion) with adaptive boundary extraction; ONNX-exportable, Python 3.12, PyTorch Lightning.
alive:     161★; commit/contributor/release detail unrecorded
why:       Not on-stack, but if Harmonia ever ingests sung input the F0 + boundary outputs would be the upstream; otherwise a technique reference for diffusion-based transcription.
tags:      audio, singing, midi, diffusion, onnx, transcription

## ModernMube/OwnAudioSharp
link:      https://github.com/ModernMube/OwnAudioSharp
surfaced:  2026-05-13
what:      C#/.NET audio library.
alive:     commit/contributor/release detail unrecorded
why:       C# only; off ASA's Python stack. (Reasoning corrected later: a stack mismatch, not a native penalty.)
tags:      audio, csharp, dotnet, off-stack

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

## linuxmatters/jivetalking
link:      https://github.com/linuxmatters/jivetalking
surfaced:  2026-05-13
what:      Go CLI that measures a recording's integrated LUFS, true peak, LRA (EBU R128), noise floor and spectral signature, then picks per-pass filter params from that — adaptive de-essing, gating, comp, two-stage R128 normalisation to -16 LUFS.
alive:     71★; created 2025-11; commit/contributor/release detail unrecorded
why:       The "measure first, then choose parameters" pipeline is exactly what ASA's loudness + dynamics stage should output as recommendations. Model the recommendation output on it.
tags:      audio, go, r128, adaptive-params, measure-then-choose

## jpoindexter/ableton-mcp
link:      https://github.com/jpoindexter/ableton-mcp
surfaced:  2026-05-13
what:      Python Ableton MCP with 200+ tools, Gemini-capable.
alive:     commit/contributor/release detail unrecorded
why:       Dropped as "another Ableton-via-MCP take, thinner than the already-logged producer-pal," then un-dropped as on-theme for ASA's Ableton+LLM surface. A second, broader Ableton-MCP tool inventory to compare against producer-pal when deciding write-side tool granularity.
tags:      audio, ableton, mcp, gemini

## JorenSix/Olaf
link:      https://github.com/JorenSix/Olaf
surfaced:  2026-05-13
what:      Portable acoustic fingerprinting in C with WASM and ESP32 targets.
alive:     396★; created 2020 but still actively pushed in 2026; commit/contributor/release detail unrecorded
why:       Tangential to ASA's core but a clean reference if you ever need audio identification or cross-take alignment in-browser. Strip the in-browser novelty, though, and audio identification isn't an ASA use case.
tags:      audio, fingerprinting, c, identification

## JeffreyCA/spleeter-web
link:      https://github.com/JeffreyCA/spleeter-web
surfaced:  2026-05-13
what:      Self-hostable React + Django app (Celery/Redis + Docker) for vocal/bass/drums isolation backed by Spleeter, Demucs and BS-RoFormer, with a job queue.
alive:     544★; pushed within the 05-13 window but the project itself is from 2019; commit/contributor/release detail unrecorded
why:       Not a new idea, but the React front for queueing/running stem jobs is a useful pattern if ASA grows a stem-separation stage. React + queue + Docker running Demucs *is* ASA's app+queue+L2 shape — only the web framework differs.
tags:      audio, react, django, celery, demucs, queue

## Ircam-Partiels/Partiels
link:      https://github.com/Ircam-Partiels/Partiels
surfaced:  2026-05-13
what:      IRCAM's Vamp-plugin host wrapping FFT, LPC, transients, F0, formants and tempo behind a JUCE GUI, with batch CLI and exports to CSV/SDIF/JSON/REAPER/Max/PD.
alive:     74★; C++; commit/contributor/release detail unrecorded
why:       Useful as a reference for how a serious analysis tool structures multi-track, multi-channel pipelines and result interchange — and the SDIF export format is worth a look for ASA result storage.
tags:      audio, vamp, juce, export, sdif, interchange

## innermost47/ai-dj
link:      https://github.com/innermost47/ai-dj
surfaced:  2026-05-13
what:      Server-side Python (Stable Audio Open) loop-generator VST, now renamed OBSIDIAN-Neural.
alive:     commit/contributor/release detail unrecorded
why:       Originally dropped as "pure generation, no analysis or theory overlap," then un-dropped because ASA Phase-3 is on-demand audition-sample generation — this is a Phase-3 plumbing reference. Fork the Stable-Audio-Open loop-generation server as a starting point.
tags:      audio, generation, stable-audio, vst

## httpsworldview/openmeters
link:      https://github.com/httpsworldview/openmeters
surfaced:  2026-05-13
what:      Linux audio metering in Rust: short-term/momentary LUFS to ITU-R BS.1770-5, true peak, A-weighted spectrum, spectrogram with spectral reassignment for sharp time-frequency resolution, oscilloscope, goniometer.
alive:     135★; created 2025-10; commit/contributor/release detail unrecorded
why:       The reassignment trick and the exact BS.1770 revision are worth lifting; UI is wgpu/Iced.
tags:      audio, rust, lufs, bs1770, true-peak, spectral-reassignment

## HeartMuLa/heartlib
link:      https://github.com/HeartMuLa/heartlib
surfaced:  2026-05-13
what:      Music-generation library.
alive:     commit/contributor/release detail unrecorded
why:       Well-known and orthogonal to both projects. Nothing specific to the analysis path.
tags:      audio, generation, known

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

## fspecii/ace-step-ui
link:      https://github.com/fspecii/ace-step-ui
surfaced:  2026-05-13
what:      UI over ACE-Step.
alive:     commit/contributor/release detail unrecorded
why:       Generation-side, no analysis. UI patterns for driving a gen model only.
tags:      audio, ui, acestep, generation

## FoxNoseTech/diarize
link:      https://github.com/FoxNoseTech/diarize
surfaced:  2026-05-13
what:      Speech diarization tool.
alive:     commit/contributor/release detail unrecorded
why:       Speech diarization, not music.
tags:      audio, speech, diarization, off-domain

## EmulationAI/awesome-large-audio-models
link:      https://github.com/EmulationAI/awesome-large-audio-models
surfaced:  2026-05-13
what:      An awesome-list of large audio models.
alive:     commit/contributor/release detail unrecorded
why:       Awesome-list, already on most people's radar — not a tool. Evaluated on 05-13 but never logged until the 05-20 pass.
tags:      audio, awesome-list, models

## daniel-c-silva/SynthBridge
link:      https://github.com/daniel-c-silva/SynthBridge
surfaced:  2026-05-13
what:      NumPy sine-wave synth behind a Flask endpoint.
alive:     commit/contributor/release detail unrecorded
why:       Thin — its "reharmonization" is just chord playback, with no analysis or theory.
tags:      audio, synth, flask, thin

## cuthbertLab/music21j
link:      https://github.com/cuthbertLab/music21j
surfaced:  2026-05-13
what:      JS port of music21.
alive:     commit/contributor/release detail unrecorded
why:       Well-known, on every music-theory shortlist already. Browser-side theory primitives (notes, intervals, keys) if a JS theory dep is wanted — adopt, don't reimplement.
tags:      audio, theory, music21, js

## crlandsc/moises-light
link:      https://github.com/crlandsc/moises-light
surfaced:  2026-05-13
what:      Unofficial PyTorch implementation of "Moises-Light: Resource-efficient Band-split U-Net" (WASPAA 2025) with RoPE bottleneck borrowed from BS-RoFormer.
alive:     27★; created 2026-03; training-only, no weights; commit/contributor/release detail unrecorded
why:       Useful as a clean modern band-split reference if ASA ever adds a separation pre-stage; otherwise read the paper.
tags:      audio, pytorch, band-split, unet, training-only

## creightonlinza/forever-jukebox
link:      https://github.com/creightonlinza/forever-jukebox
surfaced:  2026-05-13
what:      End-to-end Infinite-Jukebox replacement: madmom-beats-lite + Essentia generate beats/segments/sections locally and serve them through a small REST API, replacing Spotify's now-dead Audio Analysis endpoint.
alive:     24★; TypeScript+Python; created 2026-01; commit/contributor/release detail unrecorded
why:       Direct reference for the shape of ASA's analysis → JSON contract, and a local REST analysis service — fork the API surface and the beat/segment/section schema.
tags:      audio, jukebox, essentia, beats, rest, json-contract

## complexlogic/rsgain
link:      https://github.com/complexlogic/rsgain
surfaced:  2026-05-13
what:      Native C++ EBU R128 + true-peak + ReplayGain 2.0 CLI.
alive:     603★; active 2026; commit/contributor/release detail unrecorded
why:       Dropped verbatim for being "off-stack for ASA's in-browser/in-pipeline scope," which was the bias — it's a Phase-1 loudness reference in the same role as openmeters/soundscope, a clean fast native R128/true-peak implementation to cross-check against.
tags:      audio, native, cpp, r128, true-peak, replaygain

## chromatone/chromatone.center
link:      https://github.com/chromatone/chromatone.center
surfaced:  2026-05-13
what:      Vue/Vite app on top of Tonal.js + abcjs + Tone.js + audiomotion-analyzer presenting chords, scales, rhythms and pitch-color visualisations as PWA "instruments".
alive:     146★; started 2021 but actively pushed; commit/contributor/release detail unrecorded
why:       Direct overlap with Harmonia's stack; worth pillaging for chord/scale visual idioms and the color-coded pitch palette.
tags:      audio, theory, tonaljs, scales, pwa

## charlesvestal/schwung
link:      https://github.com/charlesvestal/schwung
surfaced:  2026-05-13
what:      Ableton Move firmware shim.
alive:     commit/contributor/release detail unrecorded
why:       Specific to one piece of hardware. Nothing transferable.
tags:      audio, ableton-move, hardware, shim

## BillyDM/awesome-audio-dsp
link:      https://github.com/BillyDM/awesome-audio-dsp
surfaced:  2026-05-13
what:      An awesome-list of audio DSP resources.
alive:     commit/contributor/release detail unrecorded
why:       Awesome-list, already on most people's radar — not a tool. Evaluated on 05-13 but never logged until the 05-20 pass.
tags:      audio, awesome-list, dsp

## bananaofhappiness/soundscope
link:      https://github.com/bananaofhappiness/soundscope
surfaced:  2026-05-13
what:      Rust TUI loudness analyzer: LUFS + true peak + FFT spectrum + min-max-decimated waveform on files or live mic.
alive:     174★; commit/contributor/release detail unrecorded
why:       Smaller scope than openmeters and CLI-only; mostly useful as a second BS.1770 implementation to cross-check against.
tags:      audio, rust, tui, lufs, true-peak, cross-check

## Asvarox/allkaraoke
link:      https://github.com/Asvarox/allkaraoke
surfaced:  2026-05-13
what:      Browser karaoke with pitch detection.
alive:     2022 project; commit/contributor/release detail unrecorded
why:       The README doesn't expose the analysis layer and it's a 2022 project.
tags:      audio, karaoke, browser, pitch

## asteroid-team/asteroid
link:      https://github.com/asteroid-team/asteroid
surfaced:  2026-05-13
what:      Mature PyTorch audio source-separation toolkit (recipes, models, datasets).
alive:     commit/contributor/release detail unrecorded
why:       Dropped merely as "established" — but separation is L2 in-scope, so a mature PyTorch separation toolkit is a legitimate reference.
tags:      audio, pytorch, separation-toolkit, established

## asigalov61/tegridy-tools
link:      https://github.com/asigalov61/tegridy-tools
surfaced:  2026-05-13
what:      Symbolic-music NLP toolkit from 2020.
alive:     recent commits but no new direction; commit/contributor/release detail unrecorded
why:       Grab specific MIDI-processing utilities only; nothing architecturally new.
tags:      audio, symbolic, midi, nlp

## adamjmurray/producer-pal
link:      https://github.com/adamjmurray/producer-pal
surfaced:  2026-05-13
what:      Max-for-Live device + MCP server letting Claude/Gemini/ChatGPT/Ollama drive an Ableton Live session through natural language.
alive:     143★; JavaScript; active 2026-05; commit/contributor/release detail unrecorded
why:       Not directly ASA/Harmonia, but it's the cleanest current example of M4L ↔ MCP plumbing if either project ever wants a DAW-side companion. ASA *is* Ableton+Gemini, so it's really the "apply the Phase-2 recommendation in Live" companion — fork the M4L↔MCP bridge wholesale as the write-side.
tags:      audio, ableton, mcp, m4l, gemini

## ace-step/ACE-Step-1.5
link:      https://github.com/ace-step/ACE-Step-1.5
surfaced:  2026-05-13
what:      Large text-to-music generation model.
alive:     commit/contributor/release detail unrecorded
why:       Well-known and orthogonal to both projects. Only as the upstream model if Phase-3 ever wants full-track gen rather than short auditions.
tags:      audio, text-to-music, generation, known
