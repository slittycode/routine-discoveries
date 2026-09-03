# routine-discoveries

A log of GitHub repos surfaced by recurring discovery routines.

Capture is unopinionated and lossless. Organisation is a view derived from
capture — regenerable, deletable, and with no authority over what gets logged.

**573 entries, 2026-05-13 to 2026-08-16.**

## Start here

| I want to… | Go to |
| --- | --- |
| See everything, in full | [`FINDS.md`](FINDS.md) — the whole log, newest first |
| Skim one domain | [`views/audio.md`](views/audio.md) · [`views/legal.md`](views/legal.md) · [`views/general.md`](views/general.md) — the same entries as tables |
| Check whether a repo was already seen | [`_seen.txt`](_seen.txt) — one `owner/repo` per line |
| Know how a sweep runs | [`routines/`](routines/) — one prompt per sweep |
| Read a plan built on a find | [`incorporations/`](incorporations/) |

## Layout

| path | what it is | authoritative? |
| --- | --- | --- |
| `FINDS.md` | Single append-only log. Every find, newest at top. | **Yes — the only authoritative file.** |
| `_seen.txt` | Dedupe list. One `owner/repo` per line, sorted. | Yes, for dedupe only. |
| `routines/` | The prompt for each recurring sweep. | Yes, for how sweeps run. |
| `views/` | Tables filtered out of `FINDS.md` by tag. | **No.** Regenerable; safe to delete. |
| `incorporations/` | Plans for lifting a find into a project. | Yes, for those plans. |

There is no per-sweep directory and no shortlist file. A sweep appends to
`FINDS.md` and adds its slugs to `_seen.txt`; that is the whole write path.

## The rules

**`FINDS.md` is the only authoritative file.** Everything else is either input
to a sweep (`routines/`), bookkeeping (`_seen.txt`), downstream work
(`incorporations/`), or derived output (`views/`). If those disagree with
`FINDS.md`, `FINDS.md` wins.

**There is no relevance threshold.** No score, rating, priority or status is
recorded anywhere. Nothing is filtered out at write time for being too marginal,
too well-known, too small, or too far from anything currently being built. If a
sweep looked at a repo, it gets an entry — including the ones it looked at and
rejected, and the reason it rejected them.

**A find does not need to map onto an existing project.** There is no list of
projects a repo must serve. A repo that is interesting on its own terms — a
technique worth knowing, a tool worth having, a shape worth copying, a thing
that is simply good — belongs in `FINDS.md` exactly as much as one that plugs
straight into something already running. "I couldn't say which project this is
for" is not a reason to drop it; it's a reason to write the `why` field
carefully.

**`views/` and its filenames carry no authority.** They are the output of a
filter, not a set of buckets a find must fall into. Adding a view does not
create a category; deleting one loses nothing. Never decline to log a find
because no view would show it — `views/general.md` catches everything the other
filters miss, and if it is empty that means nothing has landed there yet, not
that nothing could.

**Tags are freeform.** Lowercase words, comma-separated, whatever the entry's
own text supports. A tag naming the sweep that found something (`mac-gaming`,
`general`) is just another word — it confers nothing and gates nothing. There
is no controlled list, and there must not become one: a fixed tag vocabulary is
a taxonomy, and a taxonomy is the filter this structure exists to remove.

## Adding a find

Prepend the entry to `FINDS.md`, add the slug to `_seen.txt`, keep `_seen.txt`
sorted. Every entry in `FINDS.md` must appear in `_seen.txt` and vice versa.

```
## owner/repo
link:      https://github.com/owner/repo
surfaced:  YYYY-MM-DD
what:      one plain sentence
alive:     last commit, contributor count, release cadence
why:       why it's worth my attention
tags:      freeform lowercase words, comma-separated
```

Write `alive: not recorded` rather than guessing. A missing liveness signal is a
gap in the record, never a finding about the repo.

Nothing about a new sweep requires new files. A new stream appends to `FINDS.md`
like every other one and picks up whatever tags fit.

## Regenerating views

`views/*.md` are tag filters over `FINDS.md`: `audio.md` is everything tagged
`audio`, `legal.md` everything tagged `legal`, `general.md` everything tagged
neither. Rebuild them by re-reading `FINDS.md` and re-filtering. Never edit a
view by hand, and never treat a view as the record.

## History

Before 2026-09 this repo split finds across four per-stream silos
(`discoveries/`, `baseline/`) plus score-gated shortlists (`RECOMMENDATIONS.md`,
`LEGALTECH-RECOMMENDATIONS.md`, and a per-stream `FINDS.md` the mac-gaming
sweep had started). Every repo those files recorded — including ones scored
below the old threshold, marked dropped, or logged to a dedupe list with no
write-up at all — was migrated here, and the old structure was removed. `git
log` has the detail.

The old streams survive only as tags — `audio`, `legal`, `general`,
`mac-gaming` — and only because that is what has been logged so far. They are
not a schema. The clearest evidence for that: a `general` stream had to be
invented once finds stopped fitting the two original projects, and under the old
layout it simply became a third silo. Here it is four characters in a tag list.
