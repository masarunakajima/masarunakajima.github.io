---
layout: page
title: Scientific data platforms
description: Multi-omics analysis and lab-data applications
importance: 3
category: industry
---

**Capricor Therapeutics · 2025–present**

- **Multi-omics analysis platform**: ingestion, quantification, statistics, and visualization for proteomics, miRNA, RNA-seq, and single-cell data. Python/R integration (DESeq2, limma, DEqMS, fgsea through rpy2). The platform launches and tracks cloud pipelines directly.
- **Lab-data applications**: web apps for assay data entry, review, and trending, with Azure Entra ID single sign-on and role-based access. Data integrity is built in: per-file hashes, recorded exclusion reasons, and stable record identity.
- **Data harmonization**: one data model across modalities, with ontology-backed controlled vocabularies (Cell Ontology, UBERON, MONDO, NCBI Taxon), following FAIR principles.

**USC Smith Lab · 2023–2024**

- Analysis-result storage for a large DNA methylation pipeline: MySQL and MongoDB services, a Flask application linking HPC compute nodes to a central database, and CI/CD with Docker image publishing.

**Stack:** FastAPI · PostgreSQL · SQLAlchemy/Alembic · Vue/Nuxt · Streamlit · R · Docker · GitHub Actions · AWS
