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

## Spark — pattern to mine

- **fork 3 / spark 5** · local-first:partial · [tomasonjo-labs/legal-tech-chat](https://github.com/tomasonjo-labs/legal-tech-chat) · `Jupyter Notebook` · `159★` · `maturity:reference`
  A worked pipeline that extracts structured fields from contracts into a Neo4j knowledge graph and answers questions via a LangGraph agent (self-hostable; reference notebooks use cloud LLMs). **Build:** fork the *pattern* to make your contracts queryable by relationship ("every lease whose rent-review clause references CPI") instead of flat one-doc-at-a-time RAG. _(05-21 · tags: knowledge-graph, neo4j, langgraph, graphrag, notebooks)_

## Marginal — kept with a note (dropped on 05-21 for redundancy)

- **fork 3 / spark 3** · local-first:yes · [curiousily/ragbase](https://github.com/curiousily/ragbase) · `Python` · `129★` · `maturity:reference` · quiet since 2024
  A small, fully-local chat-with-PDF skeleton (LangChain + Streamlit + Ollama/Llama 3.1 + Qdrant, with reranking and semantic chunking). Dropped 05-21 as superseded by AnythingLLM, and quiet since 2024. **Build:** a tinier base to own line-by-line if you want fewer moving parts than AnythingLLM. _(05-21 · tags: rag, local, streamlit, qdrant, minimal)_
