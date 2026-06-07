# Routine — legaltech-nz discoveries

Recurring sweep that surfaces GitHub repos a **vibe-coding New Zealand property/conveyancing
lawyer** could **fork and build from** as **personal** tools (not commercial products). One of
two streams in this repo (see `routines/README.md`). Paste into the recurring task.

## Who this is for
- A NZ property/conveyancing lawyer who builds his own small tools with AI assistance, for
  PERSONAL use only.
- Stack he'll fork/extend: [edit — e.g. TypeScript/Next.js, Python; fine with Tauri/Electron or a
  CLI]. Favour modern, hackable, well-documented codebases.
- Documents are confidential, so LOCAL-FIRST / OFFLINE tools are preferred — but this is a
  preference, not a hard requirement.
- **AI is optional, not the point.** Favour tools that deliver real value *deterministically* —
  diff engines, document parsers, OOXML / tracked-change manipulation, productivity apps, data
  stores — where any LLM / RAG layer would be a bolt-on he could add himself. Do NOT award
  relevance just because a repo "has an LLM / RAG / agent." A repo whose ONLY substance is "pipe
  documents to a model" is a thin wrapper (see Drops). Local-LLM capability is at most a minor
  tiebreaker, never a reason to keep.
- Licence is NOT a consideration. Never score, flag, or gate on it.
- NZ relevance is a BONUS, not a requirement.
- He wants BOTH directly-useful tools AND creative seeds to build something novel from.

## What to look for — these are output LABELS, not pre-filters (never drop a repo for not fitting a bucket)
1. **Document comparison & legal-impact** — version / clause / structural diff, redlining, contract
   comparison, AND single-document consistency (defined terms, cross-references, contradictions).
   Substantive legal meaning, not formatting/metadata.
2. **Document understanding** — PDF / DOCX / OOXML parsing and extraction, layout / structure /
   section detection, defined-term and cross-reference extraction. DETERMINISTIC parsing and
   extraction first; chat-with-documents / RAG / summarisation are a sub-case, not the headline,
   and only count when the parsing / extraction itself is the real substance.
3. **Personal productivity** — to-do / task managers, notes / PKM, personal matter/time tracking,
   snippet & template libraries, small local dashboards.
4. **Build-your-own-tool foundations** — text / semantic / AST / structural diff libraries,
   OOXML / tracked-change engines, document parsers, desktop shells (Tauri/Electron), CLI
   scaffolds, embedded / local data stores (SQLite, CRDT). Plain, dependency-light libraries he
   can compose. (RAG / local-LLM plumbing is welcome but is the LEAST important sub-bucket here —
   don't let it crowd out deterministic foundations.)
5. **NZ legal content & data** — legislation.govt.nz / PCO, NZ case law (NZLII), NZ open datasets.
6. **Tangential but interesting.**
7. **Wildcard / cross-domain spark** — clever apps from OTHER domains whose pattern transfers
   (e.g. a code-review UI repurposed for prose, a spreadsheet-diff visualiser, a Zettelkasten
   engine). Cap 3 entries.

## Workflow

1. Read `discoveries/_seen-legaltech-nz.txt` (dedupe list, one `owner/repo` per line; absent =
   empty). This is SEPARATE from the audio stream's `discoveries/_seen.txt` — never mix them.

2. Find candidates — keyword search AND lateral discovery:
   - Keyword queries — LEAD with deterministic tooling; treat AI terms as a small minority of
     your queries, run LAST:
     - comparison / redline: "document comparison" OR "contract comparison" OR "semantic diff" OR
       redline OR "tracked changes" OR OOXML
     - diff / structure libraries: "structural diff" OR "AST diff" OR "text diff" library; docx OR
       OOXML ("tracked changes" / redline engines)
     - parsing & extraction (no-AI): "PDF extraction" OR docx OR OCR OR "layout analysis";
       "clause extraction" OR "defined terms" OR "cross-reference"
     - productivity (local-first, no-AI): todo OR "task manager" OR "note taking" OR PKM OR
       "time tracking" OR "snippet manager" OR "template manager"
     - foundations: "local-first" (Tauri/Electron); embedded datastore (SQLite / CRDT / sync)
     - NZ: "New Zealand" (legislation / "case law")
     - AI — CAP at one or two queries, run them LAST and sparingly: "contract analysis" (LLM) OR
       "chat with documents" / RAG (local / ollama). These already flood every sweep; you are
       trying to find what ELSE is out there, not more of them.
   - Lateral methods (use these too, not just keywords): browse GitHub TOPIC tags (e.g.
     `text-diff`, `redlining`, `local-first`, `knowledge-management`, `document-ai`); MINE
     awesome-lists for individual repos, INCLUDING non-legal ones (awesome-local-first / diff /
     pkm); and run ONE deliberate ADJACENT-DOMAIN pass (general diffing / writing / knowledge /
     dev-review tools) at stars>50 whose finds must clear the spark bar.
   - Recency filter: stars>5 and created within ~16 months OR pushed in the last ~45 days FOR
     APPLICATIONS. For libraries / parsers / diff-engines / scaffolds, DROP the recency gate — an
     old, stable base is fine.

3. Drop any candidate already in `_seen-legaltech-nz.txt`.

4. Ground-truth EVERY remaining candidate by fetching its actual GitHub page — never characterise
   (or set the local-first flag) from a search snippet. Pull description, stars, last-commit date,
   README (~200 words), primary language, and whether it genuinely runs locally/offline.

5. Score each on TWO axes, 1–5:
   - **fork-and-run fit** — how readily he could fork it and run/extend it as a personal tool.
   - **creative / spark potential** — would it teach a technique or seed a tool he couldn't
     otherwise build?

   **Keep** a repo if `fork-fit ≥3` **OR** (`spark ≥4` **AND** it clears the spark bar).
   - **Spark bar:** a spark-only survivor's pitch MUST name the specific tool or technique it lets
     HIM build ("I'd fork/mine this to build ___"). If you can't, drop it — even at spark 5.
     Generic dev tooling with no named application fails.
   - **Local-first:** record as a flag; use only as a tiebreaker; additionally CAP a cloud-native
     tool's fork-fit at 3 (posting client docs to an API is a rewrite, not a fork). Never drop
     solely on it; never ignore it.
   - **Drops:** drop thin-wrapper / abandoned repos only if they ALSO score `<4` spark; keep
     "abandoned-but-clever" as WILDCARD-only entries flagged `archived` (within its cap of 3).
     Exclude keyword-spam and pirated-software repos. **Do NOT drop a repo for being well-known or
     popular** — popularity is irrelevant to personal forking, and a famous repo is often the best
     base or teacher.
   - **LLM / RAG wrappers count as thin wrappers:** a repo whose substance is "send documents to a
     model" — chatbot UIs, generic ollama / RAG / agent starters, "chat with your PDF" clones —
     is a thin wrapper. Drop it unless it adds a DETERMINISTIC capability he couldn't trivially
     rebuild in an afternoon (a real parser, diff, datastore, or extraction step), OR it clears
     the spark bar with a specifically-named tool. Being popular does not rescue it here.

6. Caps: soft target 15 survivors, hard ceiling 20; within that ≤3 spark-only and ≤3 wildcard. No
   even-bucket-spread quota — a lopsided sweep is fine.
   - **AI-first cap:** at most ~1/3 of survivors may be "AI-first" (won't do anything useful
     without an LLM / RAG). The MAJORITY must be useful with ZERO AI. A sweep that is mostly
     deterministic tooling is the goal, not a shortfall — if you can't fill the cap with good
     non-AI finds, ship fewer survivors rather than padding with RAG starters.

7. Append survivors to `discoveries/legaltech-nz-<YYYY-MM-DD>.md` under the seven section
   headings. Entry format:
   `### [owner/repo](https://github.com/owner/repo) — **fork N / spark N**`
   then 2 sentences (what it is + what I'd build/run with it), then a meta line:
   `lang · local-first: yes/no/partial` (add `· why-kept: spark` on spark-only survivors and
   `· archived` on abandoned-but-clever wildcards). Optionally end the file with an "NZ data
   sources & APIs worth building on" appendix (legislation.govt.nz, NZLII, data.govt.nz, LINZ Data
   Service).

8. Append surfaced `owner/repo` lines to `_seen-legaltech-nz.txt`.

9. Commit to branch `claude/legaltech-discoveries-<YYYY-MM-DD>` and open a PR.

Be direct; pitch each repo as a personal tool he'd actually fork and run; state whether it runs
locally. Don't pad. Ignore licence entirely.
