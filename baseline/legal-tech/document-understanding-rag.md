# legal-tech / document-understanding & RAG

PDF/DOCX understanding, chat-with-documents (RAG), clause/defined-term extraction and
summarisation — ideally offline / local-LLM. Scores are **fork N / spark N** plus a
`local-first:` flag (see `../README.md`). Provenance:
`discoveries/legaltech-nz-2026-05-21.md`.

Day-one stack: self-host `anything-llm`, then layer `contextgem` for cited clause/term
extraction. Parsers that feed these live in `foundations.md`.

## Strong — fork-and-run

- **fork 5 / spark 4** · local-first:yes · [Mintplex-Labs/anything-llm](https://github.com/Mintplex-Labs/anything-llm) · `JavaScript` · `60.4k★` · `maturity:app`
  A polished, fully-offline "private ChatGPT over your documents" desktop app with workspaces, PDF/DOCX ingestion, source citations and a local vector DB (Ollama/LM Studio). **Build:** self-host it day one as your confidential "chat with my matter files" base, then graft clause-extraction prompts onto its workspace model (workspaces map neatly to matters). _(05-21 · tags: rag, offline, ollama, vector-db, workspaces)_
- **fork 5 / spark 5** · local-first:yes · [shcherbak-ai/contextgem](https://github.com/shcherbak-ai/contextgem) · `Python` · `1.8k★` · `maturity:lib`
  An LLM extraction framework built around "Aspects" and "Concepts" that returns results with paragraph/sentence-level source references and auto-generated justifications, and can run against a local model. **Build:** your structured clause/defined-term/date extractor — the cite-back-to-source is exactly what trustworthy legal output needs. _(05-21 · tags: extraction, aspects-concepts, citations, local-llm, justifications)_
- **fork 4 / spark 5** · local-first:yes · [Open-Source-Legal/OpenContracts](https://github.com/Open-Source-Legal/OpenContracts) · `Python` · `1.3k★` · `maturity:app`
  A self-hosted document-annotation + knowledge-base platform with vector + full-text search, LLM clause extraction, version control, and agents that compare clauses across many contracts. Heavier to stand up (Docker). **Build:** the most complete self-hosted foundation if you want one app for both understanding and cross-document comparison of your private corpus. _(05-21 · tags: annotation, knowledge-base, cross-doc, version-control, docker)_
- **fork 5 / spark 3** · local-first:yes · [run-llama/liteparse](https://github.com/run-llama/liteparse) · `Rust` · `maturity:lib`
  LlamaIndex's offline PDF parser: Rust + PDFium for fast text + bounding-box extraction, selective Tesseract OCR, JSON/text output, per-page screenshots for LLM agents — explicitly no cloud dependencies. Sits next to (not on top of) docling: docling is the generalist, liteparse the fast-and-light specialist. **Build:** fork it when you need positional control (fixed-layout NZ forms — ADLS/REINZ agreements, LIM reports, rates statements) without the heavier model stack. _(05-27, rescored 06-03/v2 · tags: pdf, bounding-box, ocr, offline, fixed-layout)_
- **fork 5 / spark 3** · local-first:yes · [ocrmypdf/OCRmyPDF](https://github.com/ocrmypdf/OCRmyPDF) · `Python` · `maturity:app`
  Well-known but missing from the first sweep — Tesseract-backed OCR layer that makes scanned PDFs searchable in place. **Build:** run it across the matter folder once and the entire historical archive becomes greppable, RAG-able, diff-able; foundational plumbing for everything downstream. _(05-27 · tags: ocr, tesseract, searchable-archive, foundational)_
- **fork 5 / spark 4** · local-first:yes · [gmickel/gno](https://github.com/gmickel/gno) · `TypeScript` · `maturity:app` · AI-first, kept for a real deterministic core
  Fully-offline document-intelligence engine (Bun/TS) doing hybrid retrieval (BM25 + embeddings + cross-encoder rerank) with grounded, cited answers over notes, code, PDFs and Office docs, exposed via CLI/Web UI/MCP, using embedded Qwen models. Kept despite the LLM layer because the retrieval engine is real and deterministic underneath. **Build:** a near-complete "chat with my matter files, offline, with citations" tool — fork it and point it at a matter folder. _(06-03, rescored 06-03-v2 · tags: hybrid-retrieval, offline, citations, mcp, ai-first-kept)_
- **fork 4 / spark 3** · local-first:partial · [Nebutra/MinerU-Skill](https://github.com/Nebutra/MinerU-Skill) · `Python` · `maturity:app`
  Zero-dependency CLI (and Claude Code skill) wrapping MinerU to turn PDF/Office/images into clean Markdown with preserved tables, LaTeX and OCR. **Build:** a higher-fidelity ingestion path when layout matters (tables, schedules in a lease) — use where liteparse's plain text loses the structure. _(06-03/v2 · tags: mineru, ocr, tables, layout, claude-skill)_

## Spark — pattern to mine

- **fork 3 / spark 5** · local-first:partial · [tomasonjo-labs/legal-tech-chat](https://github.com/tomasonjo-labs/legal-tech-chat) · `Jupyter Notebook` · `159★` · `maturity:reference`
  A worked pipeline that extracts structured fields from contracts into a Neo4j knowledge graph and answers questions via a LangGraph agent (self-hostable; reference notebooks use cloud LLMs). **Build:** fork the *pattern* to make your contracts queryable by relationship ("every lease whose rent-review clause references CPI") instead of flat one-doc-at-a-time RAG. _(05-21 · tags: knowledge-graph, neo4j, langgraph, graphrag, notebooks)_

## Marginal — kept with a note (dropped on 05-21 for redundancy)

- **fork 3 / spark 3** · local-first:yes · [curiousily/ragbase](https://github.com/curiousily/ragbase) · `Python` · `129★` · `maturity:reference` · quiet since 2024
  A small, fully-local chat-with-PDF skeleton (LangChain + Streamlit + Ollama/Llama 3.1 + Qdrant, with reranking and semantic chunking). Dropped 05-21 as superseded by AnythingLLM, and quiet since 2024. **Build:** a tinier base to own line-by-line if you want fewer moving parts than AnythingLLM. _(05-21 · tags: rag, local, streamlit, qdrant, minimal)_
