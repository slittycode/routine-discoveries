# Routine — mac-gaming discoveries

Recurring sweep for GitHub projects that help run, mod, measure, or tune games on the user's rig:
M3 Pro MacBook, 18GB, 14" internal + external 4K panel + external 144Hz QHD panel. Games run
through CrossOver (Elden Ring now, a heavily modded Skyrim SE via portable MO2 planned). Xbox
Series pad, wired and Bluetooth. A Parallels Windows-ARM VM is kept around separately. The user has
written their own tool that taps raw HID at the kernel timestamp and pairs it with Metal HUD to get
a real per-button input latency number — measurement, not just "does it launch," is the point.

Territory (orientation, not a literal query list — don't grade against these words, judge by
whether it helps play or measure games on this machine): translation/compatibility layers and tools
built on them (Game Porting Toolkit, D3DMetal, MoltenVK, DXVK and its Metal descendants); bottle and
prefix managers; launchers; mod managers and the glue that makes Windows modding tools work off
Windows; script extenders and load-order tooling; frame timing/pacing and latency measurement; Metal
HUD parsing, powermetrics scraping, thermal/power logging; controller polling rate, HID timing,
input remapping; display sync/refresh/VRR handling; Rosetta and ARM translation performance work;
Parallels and VM guest tooling.

## Workflow

1. Read `discoveries/_seen-mac-gaming.txt` (dedupe, one `owner/repo` per line). SEPARATE from every
   other stream's `_seen` list — never mix.

2. Research broadly across the territory above (WebSearch/WebFetch — GitHub API access in this repo
   session is scoped to `routine-discoveries` itself, not the wider web, so this is a research sweep
   via search, not a GitHub API query sweep). Skip anything already in `_seen-mac-gaming.txt`.

3. Be skeptical by default: this domain is full of thin GUI wrappers around wine commands, install
   scripts that go stale in six months, and forks of dead projects with a new name. A wrapper only
   counts if it solves something the underlying tool genuinely doesn't. Weight:
   - real usage, not just stars (a high star count on a dead repo is a trap, not a signal)
   - commits/releases/issue responses in the last few months
   - survived at least one macOS or CrossOver major version bump
   - a maintainer who answers when something breaks
   - boring and reliable over clever and abandoned

4. No fixed threshold and no category has to fit — 3 to 6 finds total per sweep. For each: what it
   is in one sentence; evidence it's used and maintained (with dates); whether Apple Silicon support
   is CONFIRMED recently vs merely assumed; what to do with it (use / fork / take-an-idea); and
   whether it overlaps with the user's own HID+Metal-HUD latency tool (say plainly if something does
   the job better and the custom tool should be dropped — so far, nothing has).

5. If an entire sub-area's honest answer is "nothing good exists, everyone uses the built-in tool,"
   say so plainly rather than padding the list. This has been true for: frame-timing capture
   (no PresentMon-equivalent on macOS), Metal HUD logging/parsing over time, MO2-under-Wine glue,
   Parallels gaming tooling, and anything claiming to beat the user's own controller-latency tool —
   re-check each on future sweeps in case that's changed, don't assume it's still true.

6. Where a find isn't a repo (a wiki, a config database, a per-game tweak thread that's the
   canonical source) — note it, say plainly it isn't a repo, still count it if it's the honest
   answer. (`BetterDisplay` is a related edge case: it lives on GitHub for issues/releases but its
   application source isn't published — flag that distinction explicitly rather than treating it as
   a normal open-source find.)

7. Append the sweep's raw vetting notes (including what was ruled out and why) to
   `discoveries/mac-gaming-<YYYY-MM-DD>.md`.

8. Append the consolidated shortlist to `FINDS.md` (repo root) under a new dated section, tagged
   with whatever short tags describe each entry (e.g. `[translation-layer]`, `[power]`,
   `[not-actually-open-source]`).

9. Append every seriously-evaluated `owner/repo` (shortlisted or not) to `_seen-mac-gaming.txt`.

Be direct. Don't pad the pitches. Ignore licence considerations.
