---
layout: page
title: Cloud omics pipelines
description: Proteomics and small-RNA workflows on AWS HealthOmics (Nextflow)
importance: 1
category: industry
---

**Capricor Therapeutics · 2025–present**

I built and maintain production workflows that take raw instrument data to analysis-ready results in the cloud:

- **Mass-spectrometry proteomics**: containerized FragPipe (MSFragger, IonQuant, DIA-NN, Philosopher) and ProteoWizard, run as private **Nextflow workflows on AWS HealthOmics**. Includes DIA and label-free configurations, custom FASTA search databases with decoys and contaminants, and downstream quantification (iBAQ, Total Protein Approach).
- **Small-RNA profiling**: a containerized SPORTS workflow on HealthOmics for miRNA, tRNA- and rRNA-derived fragments, and other small RNAs.
- **Reproducibility**: versioned container images (ECR), parameterized workflow definitions, and checksummed inputs and outputs, so any result can be regenerated.
- **Data movement**: streaming public datasets (PRIDE, MassIVE, GEO) directly into S3 with batch jobs.

**Stack:** Nextflow · AWS HealthOmics, Batch, ECR, S3, EC2 · Docker · Python · FragPipe · DIA-NN · SPORTS
