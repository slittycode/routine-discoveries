# legal-tech / NZ legal content & data

NZ-specific legislation/content tooling and the closest Commonwealth corpus templates.
NZ relevance is a bonus, not a requirement — but this is where it lands. Scores are
**fork N / spark N** plus a `local-first:` flag (see `../README.md`). Provenance:
`discoveries/legaltech-nz-2026-05-21.md`. (Official NZ data sources to build on —
legislation.govt.nz XML, NZLII, data.govt.nz, LINZ — are listed in the 05-21 sweep's
appendix, not as repos to fork.)

## Scored

- **fork 3 / spark 5** · local-first:yes · [nzpco/PCO-AI-Generating-an-Updated-Act](https://github.com/nzpco/PCO-AI-Generating-an-Updated-Act) · `TypeScript` · `1★` · `maturity:reference`
  Official NZ Parliamentary Counsel Office code that takes an amendment Act and applies it to the principal Act from the legislation.govt.nz **XML**, presenting the consolidated result — and it documents running locally with Ollama. **NZ gold.** **Build:** fork it as both a worked example of parsing NZ legislation XML and a personal "what does the in-force version actually say?" consolidator. _(05-21 · tags: nz, pco, legislation-xml, consolidation, ollama)_
- **fork 3 / spark 4** · local-first:yes · [isaacus-dev/open-australian-legal-corpus-creator](https://github.com/isaacus-dev/open-australian-legal-corpus-creator) · `Python` · `120★` · `maturity:lib`
  The maintained scrapers + assembly pipeline behind the first open corpus of Australian legislation *and* case law. Not NZ, but the closest live Commonwealth template. **Build:** adapt its per-jurisdiction scraper/normaliser design to build your own offline NZ legislation+caselaw corpus (pointed at legislation.govt.nz XML or NZLII). _(05-21 · tags: corpus, scraper, commonwealth, caselaw, normaliser)_
- **fork 3 / spark 4** · local-first:yes · [nzpco/PCO-AI-Chatbot-for-NZL](https://github.com/nzpco/PCO-AI-Chatbot-for-NZL) · `Python` · `2★` · `maturity:reference`
  Official PCO sibling of `PCO-AI-Generating-an-Updated-Act` above: a chatbot grounded in the live New Zealand Legislation corpus. Moved here from "unscored" once the 05-27 sweep gave it a real score. **Build:** a worked example of "RAG over legislation.govt.nz XML, with Ollama at the back" — the closest official template for a personal "ask the Act" tool. _(05-21, scored 05-27 · tags: nz, pco, chatbot, legislation, official)_
- **fork 3 / spark 4** · local-first:yes · [nzpco/PCO-AI-Plain-Language-Recommendations](https://github.com/nzpco/PCO-AI-Plain-Language-Recommendations) · `TypeScript` · `3★` · `maturity:reference`
  Official PCO sibling: TypeScript implementation that suggests plain-language rewrites of statutory text. Moved here from "unscored" once the 05-27 sweep gave it a real score. **Build:** the statute-aware prompting and evaluation scaffolding is the genuinely transferable piece for any "rewrite this clause in plain English for the client" tool. _(05-21, scored 05-27 · tags: nz, pco, plain-language, drafting, official)_
- **fork 5 / spark 4** · local-first:yes · [russellbrenner/auslaw-mcp](https://github.com/russellbrenner/auslaw-mcp) · `TypeScript` · `maturity:app`
  MCP server for Australian and New Zealand legal research: searches AustLII for case law and legislation, retrieves full-text judgments with paragraph numbers preserved, OCRs scanned PDFs (Tesseract), extracts neutral citations and formats to AGLC4; runs locally via npm/Docker. The most on-point NZ find. **Build:** fork it to give a local AI assistant grounded NZ/AU case-law and legislation lookup. _(06-03, rescored 06-03-v2 · tags: mcp, austlii, case-law, ocr, aglc4)_
- **fork 5 / spark 3** · local-first:yes (queries the official PCO API) · [edithatogo/nz-legislation](https://github.com/edithatogo/nz-legislation) · `TypeScript` · `maturity:app`
  CLI and MCP server that searches, retrieves and cites NZ Acts, bills, regulations and instruments straight from the Parliamentary Counsel Office's legislation.govt.nz API (43+ tests, v1.2.0). **Build:** the statutory-lookup backbone — e.g. pulling the current Property Law Act / Unit Titles Act sections into a drafting assistant. _(06-03, rescored 06-03-v2 · tags: mcp, pco-api, legislation, statutory-lookup)_
- **fork 3 / spark 3** · local-first:yes · [thecolab-ai/.skills](https://github.com/thecolab-ai/.skills) · `Python` · `maturity:lib`
  Community-contributed AI "skills" for NZ public data — LINZ, Stats NZ, Auckland Transport, weather and more. **Build:** mine it for ready-made access patterns to NZ open datasets (LINZ titles/parcels are directly property-relevant) and fork the skills you need into your own agent. _(06-03, rescored 06-03-v2 · tags: nz-open-data, linz, stats-nz, skills, access-patterns)_

## Official NZ siblings — unscored (worth a look alongside the PCO repo above)

- local-first:yes · [nzpco/PCO-AI-Classification-of-Legislation](https://github.com/nzpco/PCO-AI-Classification-of-Legislation) · `Python` · `1★` · `maturity:reference`
  Official PCO sibling: AI classification of NZ legislation. **Build:** a reference for tagging/classifying NZ statutory text by topic or type. _(05-21 · tags: nz, pco, classification, legislation, official)_
