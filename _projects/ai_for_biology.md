---
layout: page
title: AI/ML for biology
description: Single-cell foundation models and LLM evidence pipelines
importance: 2
category: industry
---

**Capricor Therapeutics · 2025–present**

- **Single-cell foundation models**: evaluated and adapted **scGPT** for cell embedding, reference-based label transfer (with and without Harmony), zero-shot similarity, and joint bulk/pseudobulk analysis. Packaged a containerized cell-type annotator that runs as GPU inference jobs on **AWS Batch**.
- **LLM evidence extraction**: multi-step pipelines (LLM query generation → PubMed retrieval → relevance ranking → evidence classification) that read thousands of papers to summarize literature support for genes, proteins, and miRNAs.
- **Biomedical knowledge graph**: harmonized PubMed/PMC, ClinicalTrials.gov, and about 15 ontologies and databases (MONDO, HPO, MeSH, OMIM, Orphanet, HGNC, UBERON, ChEMBL, and others) through ontology cross-mapping, with embedding-based semantic search.

**EMD Serono · 2024–2025**

- **Ontology mapping with LLMs**: benchmarked string matching, a fine-tuned **BioBERT** (PyTorch), and GPT-4o prompting for mapping free-text cell-type labels to the **Cell Ontology**. Improved accuracy by **20%** and deployed it as an R Shiny tool in the single-cell RNA-seq pipeline.

**Stack:** PyTorch · scGPT · BioBERT / Hugging Face · OpenAI API · sentence-transformers · Qdrant · PostgreSQL · AWS Batch (GPU) · R Shiny
