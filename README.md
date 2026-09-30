# single-cell-transcriptomic

Independent replication and extension of a published single-cell RNA-seq analysis of induced sputum from individuals with asthma and non-asthmatic controls.

This repository is based on:

**Yan et al. (2025)**  
*Single-cell RNA Sequencing Analysis of Sputum Cell Transcriptomes Reveals Pathways and Communication Networks That Contribute to the Pathogenesis of Asthma*  
**bioRxiv DOI:** `10.1101/2025.03.31.646405`

The goal is to reproduce key components of the published analysis and build additional analyses to evaluate the dataset independently.

## Current module: Cell-type annotation

The first component of the pipeline focuses on reproducing and validating cell-type annotations from the scRNA-seq dataset.

The workflow includes:

- inspection of the provided Seurat clustering
- cluster-level annotation with **SingleR** using the Human Primary Cell Atlas reference
- identification of the top SingleR candidate labels and annotation scores
- validation using curated canonical marker genes
- calculation of cluster-level average expression and percentage of cells expressing each marker
- comparison with the cell-type annotations provided in the original dataset
- manual resolution of ambiguous clusters using combined reference-based and marker-based evidence
- UMAP visualization of the resulting cell-type assignments

Rather than relying on a single annotation method, final labels are assigned using agreement between **reference-based annotation, marker expression, cluster structure, and the published biological context**.

## Repository structure

```text
.
├── scripts/
│   └── 01_celltype_annotation.R
│
├── results/
│   └── celltype_annotation/
│       ├── tables/
│       └── figures/
│
└── README.md
```

Generated results are kept separate from the analysis code so the workflow can be rerun reproducibly.

## Tools

**R · Seurat · SingleR · celldex · ggplot2 · dplyr**

## Planned extensions

Additional modules will progressively reproduce and extend other components of the published analysis, including:

- cell-type-specific expression analysis
- asthma vs. control comparisons
- pathway-level analyses
- additional subject-level and cell-type-specific analyses

## Reproducibility

The analysis is implemented as modular R scripts with explicit intermediate outputs and diagnostic visualizations.

This repository represents an **independent replication/reanalysis** and is not the official code repository associated with the original publication.
