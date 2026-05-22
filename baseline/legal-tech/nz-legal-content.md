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

## Official NZ siblings — unscored (worth a look alongside the PCO repo above)

- local-first:yes · [nzpco/PCO-AI-Chatbot-for-NZL](https://github.com/nzpco/PCO-AI-Chatbot-for-NZL) · `Python` · `2★` · `maturity:reference`
  Official PCO sibling: a chatbot over New Zealand legislation. **Build:** a worked NZ-legislation RAG reference to compare against AnythingLLM-based approaches. _(05-21 · tags: nz, pco, chatbot, legislation, official)_
- local-first:yes · [nzpco/PCO-AI-Classification-of-Legislation](https://github.com/nzpco/PCO-AI-Classification-of-Legislation) · `Python` · `1★` · `maturity:reference`
  Official PCO sibling: AI classification of NZ legislation. **Build:** a reference for tagging/classifying NZ statutory text by topic or type. _(05-21 · tags: nz, pco, classification, legislation, official)_
- local-first:yes · [nzpco/PCO-AI-Plain-Language-Recommendations](https://github.com/nzpco/PCO-AI-Plain-Language-Recommendations) · `TypeScript` · `3★` · `maturity:reference`
  Official PCO sibling: plain-language recommendations for legislative drafting. **Build:** a reference for a "plain-English rewrite" assist over clauses or advice letters. _(05-21 · tags: nz, pco, plain-language, drafting, official)_
