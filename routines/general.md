# Routine — general GitHub discovery

Recurring sweep that surfaces GitHub projects worth using, building on, or developing further —
not scoped to a single domain. Third stream in this repo (see `routines/README.md`); the other two
(`audio-mir`, `legaltech-nz`) already own their niches, so this stream should route around them,
not duplicate them.

## Who this is for

A property lawyer in NZ by trade, hobby coder in TypeScript/Python/Rust on a Mac (iTerm2, Bun, uv).
Half-finished side projects worth knowing about when judging a find: a chord progression tool, an
audio analysis pipeline, a fork of opencode, a terminal news reader. Games on Mac through CrossOver
and cares about it running well. Reads a lot, keeps more notes than gets used. Holds shares he
doesn't understand as well as he should.

That context is for judging candidates, not for generating search queries — don't mechanically
turn it into keyword searches. If something is obviously useful and matches none of it, it still
counts as a find.

## Bar for inclusion — bias hard toward proven usefulness over novelty

- Real adoption and sustained use, not a spike from one write-up or launch post.
- Commits, releases, and issue responses in the last few months.
- More than one contributor, or a single maintainer who's clearly still active (not gone quiet).
- Solves a real problem, boringly and well.
- Old and quietly maintained beats new and exciting.

Skip: thin wrappers, tutorial repos, awesome-lists, anything whose main asset is a README, anything
that reads like it exists to be starred. Ground-truth every candidate against its live GitHub page
(stars, commit dates, contributor spread, open issue/PR activity) before including it — don't
report from a blog post or search snippet alone. If a promising-sounding project doesn't hold up
under that check, note it in a "Dropped" section rather than silently discard it or force it in.

## Workflow

1. Read `discoveries/_seen-general.txt` (dedupe list, one `owner/repo` per line). Separate from the
   audio-mir and legaltech-nz `_seen` lists — never mix them.
2. Skim recent entries in `discoveries/general-*.md` to avoid re-pitching the same repos, but don't
   let their categories or shape constrain this sweep — change the shape if a good find doesn't fit.
3. Find candidates broadly — no fixed category list. Recent release notes, changelogs, "what shipped
   this month" roundups, and topic browsing all work better than guessing keywords from the bio.
4. Drop anything already in `_seen-general.txt`.
5. Ground-truth every survivor directly on GitHub (stars, forks, open issues/PRs, dates of the most
   recent commits, distinct authors in recent history, license, tech stack).
6. Land on 3–6 finds. For each: what it is in one plain sentence, evidence it's actually used and
   maintained, why it's worth attention (use it / build on it / steal the idea), and the single most
   obvious first move. List anything seriously considered and dropped, with why.
7. Append to `discoveries/general-<YYYY-MM-DD>.md`, append surfaced `owner/repo` lines to
   `discoveries/_seen-general.txt`, commit, and open a PR.

Be direct. Don't pad to hit a count — 3 strong finds beat 6 padded ones.
# routine: general

Runs on a schedule. Not scoped to one project — judged against the whole picture of
the person running it, not any single keyword from it:

> Writes for a living (property law, NZ), codes as a hobby. TypeScript and Python
> mostly, a little Rust. Mac, iTerm2, Bun, uv. Half-finished things lying around: a
> chord progression tool, an audio analysis pipeline, a fork of opencode, a terminal
> news reader. Games on a Mac through CrossOver and puts real effort into making it
> run properly. Reads a lot and keeps more notes than are used. Holds some shares
> not understood as well as they should be.

That paragraph is for judging candidates, not for generating search terms — a good
find that maps onto none of it still counts if it's obviously useful.

**Bar:** proven usefulness over novelty. Real adoption and sustained use (not a
one-post spike), commits/releases/issue-responses in the last few months, more than
one contributor (or a solo maintainer who clearly hasn't abandoned it), solves a
boring real problem well. Old and quietly maintained beats new and exciting. Skip
thin wrappers, tutorial repos, awesome-lists, README-only projects, star-bait.

**Output:** 3–6 finds per run. Each gets: what it is (one sentence), evidence it's
used and maintained, why it's worth attention (use / build on / steal the idea),
and the single most obvious first move.

→ `discoveries/general-<date>.md` · dedupe: `discoveries/_seen-general.txt`

Unlike the other streams, this one has no fixed category list — the shape can
change run to run if something good doesn't fit it.
