# routines/

The routine prompt for each discovery stream in this repo. Each stream runs independently, writes
its own dated files under `discoveries/`, and keeps its own `_seen` dedupe list — never mix them.

- **[`audio-mir.md`](audio-mir.md)** — audio / MIR / music-theory / LLM-music tooling for the ASA
  project, plus **Harmonia** (an unpublished single-file vanilla-JS chord/reharmonization tool) as a conceptual-reference-only axis. → `discoveries/audio-mir-<date>.md` · `discoveries/_seen.txt` · `RECOMMENDATIONS.md`
- **[`legaltech-nz.md`](legaltech-nz.md)** — personal, forkable tools for a NZ property lawyer who
  vibe-codes (document comparison / legal-impact, productivity, build-your-own-tool foundations;
  local-first preferred). → `discoveries/legaltech-nz-<date>.md` · `discoveries/_seen-legaltech-nz.txt`

Licence is ignored in both streams. To add a new stream, drop a routine file here and give it its
own dated-file prefix and `_seen` list.
