# routine-discoveries

A log of GitHub repos surfaced by recurring discovery routines.

Capture is unopinionated and lossless. Organisation is a view derived from
capture — regenerable, deletable, and with no authority over what gets logged.

## Layout

| path | what it is | authoritative? |
| --- | --- | --- |
| `FINDS.md` | Single append-only log. Every find, newest at top. | **Yes — the only authoritative file.** |
| `_seen.txt` | Dedupe list. One `owner/repo` per line, sorted. | Yes, for dedupe only. |
| `routines/` | The prompt for each recurring sweep. | Yes, for how sweeps run. |
| `views/` | Generated summaries filtered out of `FINDS.md`. | **No.** Regenerable; safe to delete. |
| `incorporations/` | Plans for lifting a find into a project. | Yes, for those plans. |

## The rules

**`FINDS.md` is the only authoritative file.** Everything else is either input
to a sweep (`routines/`), bookkeeping (`_seen.txt`), downstream work
(`incorporations/`), or derived output (`views/`). If those disagree with
`FINDS.md`, `FINDS.md` wins.

**There is no relevance threshold.** No score, rating, priority or status is
recorded anywhere. Nothing is filtered out at write time for being too marginal,
too well-known, too small, or too far from anything currently being built. If a
sweep looked at a repo, it gets an entry.

**A find does not need to map onto an existing project.** There is no list of
projects a repo must serve. A repo that is interesting on its own terms — a
technique worth knowing, a tool worth having, a shape worth copying, a thing
that is simply good — belongs in `FINDS.md` exactly as much as one that plugs
straight into something already running. "I couldn't say which project this is
for" is not a reason to drop it; it's a reason to write the `why` field
carefully.

**`views/` and its filenames carry no authority.** `views/audio.md`,
`views/legal.md` and `views/general.md` exist because those happen to be the
shapes of what has been logged so far. They are the output of a filter, not a
set of buckets a find must fall into. Adding a view does not create a category;
deleting one loses nothing. Never decline to log a find because no view would
show it — `views/general.md` catches everything the other filters miss, and if
it is empty that means nothing has landed there yet, not that nothing could.

**Tags are freeform.** Lowercase words, comma-separated, whatever the entry's
own text supports. There is no controlled list, and there must not become one —
a fixed tag vocabulary is a taxonomy, and a taxonomy is the filter this
structure exists to remove.

## Entry format

```
## owner/repo
link:      https://github.com/owner/repo
surfaced:  YYYY-MM-DD
what:      one plain sentence
alive:     last commit, contributor count, release cadence
why:       why it's worth my attention
tags:      freeform lowercase words, comma-separated
```

Append new entries at the top of `FINDS.md`, add the slug to `_seen.txt`, and
keep `_seen.txt` sorted. Every entry in `FINDS.md` must appear in `_seen.txt`.

## Regenerating views

`views/*.md` are filters over `FINDS.md` tags: `audio.md` is everything tagged
`audio`, `legal.md` everything tagged `legal`, `general.md` everything tagged
neither. Rebuild them by re-reading `FINDS.md` and re-filtering; never edit a
view by hand, and never treat a view as the record.

## History

Before 2026-08 this repo split finds across two per-project streams
(`discoveries/`, `baseline/`) and a score-gated shortlist
(`RECOMMENDATIONS.md`). Every repo those files recorded — including ones scored
below the old threshold or marked dropped — was migrated into `FINDS.md`, and
the old structure was removed. `git log` has the detail.
