# mac-gaming sweep — 2026-08-16

Raw vetting record. Consolidated picks are in `../FINDS.md`; this file is why-dropped detail for
everything seriously looked at. Rig: M3 Pro MacBook 18GB, internal 14" + external 4K + external
144Hz QHD, CrossOver (Elden Ring, planned modded Skyrim SE via portable MO2), Xbox Series pad
wired+Bluetooth, Parallels Windows-ARM VM, custom raw-HID+Metal HUD latency tool already in use.

One day after an unusually thorough first sweep (2026-08-15), most territory is saturated — this
sweep targeted specific gaps left in that sweep (the MO2/Skyrim-on-Mac question in particular) and
did a light recheck of the rest rather than re-running every search from scratch. Read
`discoveries/_seen-mac-gaming.txt` first; nothing below duplicates 2026-08-15's shortlist.

## Shortlisted → see FINDS.md
`Omni-guides/Tuxborn`, Anna Plays Skyrim's macOS modding wiki (not a repo), `apple/game-porting-toolkit`
(background infra, footnote-tier).

## Skyrim/MO2-on-Mac — the gap 2026-08-15 flagged as unsolved
- Went looking specifically for anything that's moved on `ModOrganizer2/modorganizer#372` (USVFS
  under Wine) since yesterday. Nothing has — still open, no new activity. Confirms yesterday's
  finding rather than changing it.
- Found `skyrim.annathepiper.org/wiki/recommended-means-of-playing-and-modding-skyrim-on-macos/`
  (+ a linked page specifically titled "Tuxborn for macOS users") — a maintained personal wiki, not
  a repo, but it's the closest thing to a canonical answer to exactly the question the user's plan
  depends on. Key claims (couldn't fully re-verify the page itself — see egress note below — so
  treat as one well-informed source, not confirmed by a second independent source):
  - **MO2 runs in CrossOver on Apple Silicon but will not run in a Parallels Windows-ARM VM.**
    Vortex is the mirror image: works in the VM, not in CrossOver. This directly validates the
    user's "portable MO2" plan over the alternative of running the mod manager inside the existing
    Parallels VM — MO2-in-CrossOver is apparently the only combination that works at all on Apple
    Silicon, not just the better one.
  - Parallels throttles VM RAM to 8GB unless you pay for the yearly (not one-time) licence tier —
    relevant if the VM route is ever reconsidered for a large load order.
  - Wabbajack itself (the installer that builds modlists like Tuxborn) has a known unresolved issue
    running under CrossOver: it installs and launches but Nexus login breaks because of a Webview
    dependency. Practical read: don't expect to run the Wabbajack *installer* app inside the
    CrossOver bottle — the working pattern people report is generating/updating the modlist
    elsewhere (a real Windows box, or accepting the VM only for that one step) and running the
    resulting MO2 install inside CrossOver afterward, since MO2 installs Wabbajack produces are
    already portable-MO2-shaped.
  - **Egress note:** `skyrim.annathepiper.org` was blocked by this session's network egress proxy
    on direct fetch (`EGRESS_BLOCKED`) — the above is reconstructed from search-result snippets, not
    a full read of the page. Worth a maintainer/user re-check next sweep if direct access becomes
    possible, rather than treating this as fully verified.
- `Omni-guides/Tuxborn` — the modlist itself. Wabbajack-format Skyrim SE modlist built for Steam
  Deck / lower-spec-PC performance targets (Legacy of the Dragonborn, BFCO combat overhaul, NPC/
  quest content). 99★, 262 commits, commits as recent as 2026-07-15 — active. No macOS mention in
  the repo's own README (it's Steam-Deck/Linux-framed), but the annathepiper guide above documents
  someone running it on Mac specifically, and a Steam-Deck-safe modlist is a reasonable proxy for
  "Wine/CrossOver-safe" since both avoid the same class of Windows-only INI/driver hacks. This is a
  modlist config repo, not executable tooling — noted plainly, still counted per the routine's own
  rule that non-tool canonical answers count.
- `anaximan/tuxborn_111` — a fork/mirror of Tuxborn, no independent activity signal found beyond the
  parent. Not a separate find.

## GPTK installer/wrapper GUIs — checked for anything that beats what 2026-08-15 already covered
Deliberately re-litigated this slot because 2026-08-15's shortlist didn't include Apple's own GPTK
repo or either of these two commonly-recommended installer GUIs, and the bar here is high (routine
explicitly warns this niche is full of thin wrappers).
- `installaware/AGPT` — free/open-source point-and-click installer for Apple's Game Porting Toolkit,
  from a real company (InstallAware), 542★, notarized builds. **Ruled out: stale.** Last commit
  2025-01-06 — 19+ months old as of today, and the underlying stack it wraps (D3DMetal, DXMT) has
  moved fast enough in that window that an installer frozen at that point is a real risk, not a
  nitpick. Not recommended over CrossOver, which the user already runs.
- `Porting-Kit-Wrapper-Suite` / `vitor251093/porting-kit-releases` ("Porting Kit") — Wineskin-based
  GUI wrapper suite with a large pre-made game/app catalog. **Ruled out: exactly the thin-wrapper
  pattern the routine warns about.** The releases repo checked has 16★ and reads as a single-commit
  releases dump with no visible link back to real source; activity/maintenance couldn't be
  established. Not pursued further.
- `apple/game-porting-toolkit` — Apple's own repo, not previously in `_seen`. 143★, structured as a
  single-commit "static drop" per release rather than incremental history (README explicitly says
  PRs aren't accepted — it's a controlled distribution channel, not a collaborative OSS project).
  README currently references "Game Porting Toolkit 4" and macOS/Xcode 27 prerequisites, confirming
  it's kept current with the OS beta cycle rather than stale. Footnote-tier find: the user doesn't
  need to touch this directly (CrossOver already bundles equivalent tooling, and it's the thing
  DXMT/Sikarugir/Whisky build config around), but worth having the actual upstream on record instead
  of only its downstream wrappers.

## Rechecked, no change from 2026-08-15
- `3Shain/dxmt` — an issue thread (`#151`, "DXMT 1.0 Release Plan," opened 2026-04-21) confirms
  active roadmap planning toward a 1.0. Not a new finding, just corroborates "active" from yesterday.
- Controller-latency and frame-pacing searches repeated with fresh query phrasing; same repo set
  surfaced as 2026-08-15 (`cakama3a/Polling`, `mrb0y/Gamepadla`, `stenyak/inputLagTimer`, etc.),
  same verdict — analog-stick-jitter proxies or camera/photodiode rigs, nothing pairing kernel HID
  timestamps with render-side ground truth. Not re-added to FINDS.md as a "nothing here" repeat;
  see 2026-08-15's entry, still accurate.
