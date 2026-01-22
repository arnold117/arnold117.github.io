---
layout: page
title: LitScribe - Autonomous Academic Synthesis Engine
description: Multi-agent literature review system using Model Context Protocol for deep cross-paper synthesis and gap analysis
# img: assets/img/litscribe.jpg
importance: 1
category: ai-tools
toc:
  sidebar: left
---

## Overview

LitScribe is an autonomous academic synthesis engine designed to transform how researchers conduct literature reviews. Using the Model Context Protocol (MCP) and multi-agent architecture, it goes beyond simple summarization to provide deep cross-paper synthesis and gap analysis. The system acts as a "Digital Scribe" that faithfully organizes knowledge while minimizing hallucinations common in standard LLM outputs.

## Problem Statement

Traditional literature reviews are time-consuming and mentally exhausting. Researchers must manually search multiple databases, download papers, extract key findings, identify conflicts between studies, and synthesize insights across dozens or hundreds of papers. Existing AI tools often produce hallucinated citations or superficial summaries that lack the depth needed for serious academic work.

## Architecture

### Multi-Agent Design

**Agent Roles** (Planned):
- **Discovery Agent**: Multi-source literature search and intelligent deduplication
- **Critical Reading Agent**: Deep analysis of individual papers with citation extraction
- **Synthesis Agent**: Cross-paper analysis, conflict resolution, and gap identification

### Model Context Protocol Integration

**MCP Servers**:
- Academic database connectors (arXiv, PubMed, Google Scholar)
- Zotero library integration for reference management
- PDF processing pipeline with LaTeX support

## Features

### Current MVP

- **Multi-source Literature Search**: Query arXiv, PubMed, and Google Scholar simultaneously
- **Intelligent Deduplication**: Automatically identify and merge duplicate papers from different sources
- **PDF-to-Markdown Conversion**: Extract text with LaTeX equation support using marker-pdf
- **Vector-based Semantic Search**: Search within your Zotero library using embeddings
- **MCP Integration**: Standardized tool interface for academic databases

### Planned Features

- **Multi-agent Debate Mechanism**: Resolve conflicting claims through structured agent debate
- **Citation Traceability**: Every claim backed by source PDF evidence with page references
- **Apple Silicon Optimization**: Local inference acceleration via MLX on M4 chips
- **Structured Output**: Generate publication-ready literature review sections

## Technical Stack

### Core Technologies

| Component | Technology |
|-----------|------------|
| Language | Python 3.12+ |
| Package Management | Mamba |
| Agent Framework | LangGraph |
| MCP Implementation | FastMCP 2.0 |
| Local LLM | Qwen 3 (32B/14B) |
| Cloud LLM | Claude Opus/Sonnet 4.5 |
| PDF Processing | marker-pdf |
| Vector Store | Zotero + embeddings |

### Design Principles

- **Hallucination Minimization**: All claims traceable to source documents
- **Hybrid Inference**: Local models for routine tasks, cloud models for complex synthesis
- **Extensible MCP**: Easy addition of new academic database connectors
- **Privacy-First**: Option for fully local processing of sensitive research

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
- Patent prior art searches

## Limitations & Future Work

**Current Limitations**:
- MVP phase with core features still in development
- Requires API keys for cloud LLM functionality
- PDF extraction quality varies with document formatting

**Future Directions**:
- Integration with more academic databases (Semantic Scholar, IEEE)
- Collaborative features for research teams
- Export to popular reference managers beyond Zotero
- Fine-tuned models for specific research domains

## GitHub Repository

[LitScribe](https://github.com/arnold117/LitScribe)

## Timeline

**Status**: MVP Development (January 2025 - Present)
