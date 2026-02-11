---
layout: page
title: LitScribe - Autonomous Academic Synthesis Engine
description: LangGraph multi-agent system with GraphRAG for deep cross-paper literature synthesis and gap analysis
# img: assets/img/litscribe.jpg
importance: 1
category: ai-tools
toc:
  sidebar: left
---

## Overview

LitScribe is an autonomous academic synthesis engine that transforms literature review workflows using a LangGraph multi-agent architecture with GraphRAG knowledge synthesis. Rather than simple summarization, it delivers deep cross-paper analysis and gap identification. A recent benchmark produced a 24-paper CHO metabolism review (7,679 words, 100% citation grounding) in 15 minutes at $0.098 total cost.

## Problem Statement

Traditional literature reviews are time-consuming and mentally exhausting. Researchers must manually search multiple databases, download papers, extract key findings, identify conflicts between studies, and synthesize insights across dozens or hundreds of papers. Existing AI tools often produce hallucinated citations or superficial summaries that lack the depth needed for serious academic work.

## Architecture

### Multi-Agent System (7 Agents)

- **Planning Agent**: Complexity assessment (1-5 scale), sub-topic decomposition, domain detection across arXiv categories, Semantic Scholar fields, and PubMed MeSH terms; supports interactive plan revision (up to 3 rounds)
- **Discovery Agent**: Per-sub-topic searching with domain-aware query expansion, two-stage abstract screening (keyword + LLM), multi-round snowball with co-citation analysis, and tiered review system (standard/large/massive)
- **Critical Reading Agent**: PDF parsing, 5-8 key findings extraction, methodology analysis, LLM-assessed relevance scoring, and pre-synthesis filtering
- **GraphRAG Agent**: Knowledge graph construction with entity extraction (methods, datasets, metrics, concepts), entity linking via embeddings, and Leiden community detection for multi-level summarization
- **Synthesis Agent**: GraphRAG-enhanced theme identification, gap analysis, citation name normalization via fuzzy matching, and auto-generated review titles
- **Self-Review Agent**: Automated quality scoring (relevance, coverage, coherence, argumentation), irrelevant paper removal, and incremental loop-back to Discovery for targeted re-search
- **Refinement Agent**: Iterative review modification through natural language instructions with session version tracking and rollback support

### Workflow

Planning → Discovery → Critical Reading → GraphRAG → Synthesis → Self-Review (loop-back if needed) → Session creation with interactive refinement

## Features

### Multi-Source Search
- Unified search across arXiv, PubMed, and Semantic Scholar with domain-aware filtering
- Word-boundary keyword matching to prevent false positives
- Zotero integration for personal library management
- Unpaywall open-access PDF acquisition
- Local-first prioritization: SQLite cache → Zotero library → external APIs

### GraphRAG Knowledge Synthesis
- Automatic entity extraction (methods, datasets, metrics, concepts)
- Entity linking with deduplication across papers using embeddings
- NetworkX-based knowledge graphs with Leiden community detection
- Multi-level summarization: entity → community → global scope

### Export & Citations
- BibTeX export with auto-detected entry types
- Five citation styles: APA, MLA, IEEE, Chicago, GB/T 7714
- Multi-format export: Word, PDF, HTML, LaTeX, Markdown

### Quality Assurance
- 100% citation grounding verification (every citation maps to actual papers)
- Automated scoring across relevance, coverage, coherence, and argumentation
- Citation normalization via fuzzy matching
- Token tracking with per-agent cost breakdown

### Multi-Language Support
- Direct generation in target languages (not post-translation)
- CJK-aware word counting
- Language mismatch detection with automatic correction suggestions

### Caching & Persistence
- SQLite cache for search results, PDF parses, and GraphRAG data
- Checkpointing enables resuming interrupted reviews via thread_id
- Incremental updates reuse cached entities
- Session management with version tracking and rollback

### PDF Processing
- High-fidelity PDF-to-Markdown conversion with LaTeX equation preservation
- Dual backend: pymupdf4llm (fast) or marker-pdf (OCR-capable)

## Technical Stack

| Component | Technology |
|-----------|------------|
| Language | Python 3.12+ |
| Agent Orchestration | LangGraph with state management |
| Async Processing | asyncio with concurrent batching and semaphore control |
| Cloud LLM | Qwen3-Max (default), DeepSeek Chat, Claude Opus |
| Knowledge Graph | NetworkX + graspologic (Leiden community detection) |
| Embeddings | sentence-transformers for entity linking |
| PDF Processing | pymupdf4llm (default) / marker-pdf (OCR) |
| Storage | SQLite (caching, checkpointing, GraphRAG) |
| Interface | CLI with optional MCP server |

## Results & Benchmarks

**24-paper CHO Metabolism Review**:
- 7,679 words generated in 15 minutes
- 100% citation grounding (every claim traceable to source)
- $0.098 total cost
- Scales to 50-500 papers via tiered review system

**Test Coverage**: 272 tests across 20 test files covering search quality, citation grounding, GraphRAG pipeline, export functionality, Zotero integration, and more

## Use Cases

**Academic Researchers**:
- Rapid literature surveys for new research directions
- Systematic review preparation with comprehensive coverage
- Identification of research gaps and contradictions

**Graduate Students**:
- Thesis literature review chapters
- Understanding the state-of-the-art in a new field
- Finding seminal papers and citation networks

**Industry R&D**:
- Technical due diligence on emerging technologies
- Competitive landscape analysis from academic publications

## Limitations & Future Work

**Current Limitations**:
- Requires API keys for cloud LLM functionality
- PDF extraction quality varies with document formatting
- No web UI yet (CLI only)

**Planned**:
- Phase 11: Local LLM support (Ollama/MLX/vLLM)
- Phase 12: Subscription system and daily digest
- Phase 13: Web UI (React + FastAPI)

## GitHub Repository

[LitScribe](https://github.com/arnold117/LitScribe)

## Timeline

**Status**: Active Development (January 2026 - Present, 10+ phases completed)
