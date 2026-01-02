# MIC-Drop-seq Analysis Code

Code to reproduce figures from Carey, Parvez et al., "MIC-Drop-seq: Scalable single-cell phenotyping of mutant vertebrate embryos"

[![bioRxiv](https://img.shields.io/badge/bioRxiv-10.1101%2F2025.05.27.656468-b31b1b.svg)](https://doi.org/10.1101/2025.05.27.656468)

---

## Abstract 

Advances in genome engineering and single-cell RNA sequencing (scRNAseq) have revolutionized the ability to precisely map gene functions, yet scaling these techniques for large-scale genetic screens in animals remains challenging. We combined high-throughput gene disruption in zebrafish embryos via Multiplexed Intermixed CRISPR Droplets with phenotyping by multiplexed scRNAseq (MIC-Drop-seq). In one MIC-Drop-seq experiment, we intermixed and injected droplets targeting 50 transcriptional regulators into 1,000 zebrafish embryos, followed by pooled scRNAseq. Tissue-specific gene expression and cell abundance analysis of demultiplexed mutant cells recapitulated many known phenotypes, while also uncovering novel functions in brain and mesoderm development. We observed pervasive cell-extrinsic effects among these phenotypes, highlighting how whole-embryo sequencing captures complex developmental interactions. Thus, MIC-Drop-seq provides a powerful and scalable platform for mapping gene functions in vertebrate development with cellular resolution.

---
## Interactive Data Exploration

We have developed an interactive analysis tool to allow users to fully explore the MIC-Drop-seq dataset.

**[LINK](https://019aad8c-f0c6-c979-f701-311a7d235fb7.share.connect.posit.cloud/)**

---
## What's here

This repository contains R Markdown files to reproduce all main and supplementary figures from the manuscript:

- `Figure1_MIC-Drop-seq.Rmd` - Proof-of-concept validation (8-gene pilot)
- `Figure2_MIC-Drop-seq.Rmd` - 50-gene screen analysis 
- `Figure3_MIC-Drop-seq.Rmd` - Phenotype validations and analysis
- `Figure4_MIC-Drop-seq.Rmd` - Phenotype classification and validation

---

## Requirements

**Software:**
- R ≥ 4.0 
- RStudio (recommended)


**Hardware:**
- 16 GB RAM minimum, 32 GB recommended
- ~30 GB free disk space, 2+ TB if using raw data

Tested on macOS Sequoia 15.5

---

## Installation

Install R packages:

```r
# Install required R packages for MIC-Drop-seq analysis

# CRAN packages
install.packages(c("tidyverse", "ggplot2", "viridis", "cowplot", "patchwork",
                   "ggpubr", "ggtext", "ggrepel", "ggridges", "rstatix", 
                   "DescTools", "igraph", "gtExtras", "circlize", 
                   "devtools", "BiocManager"))

# Bioconductor packages
BiocManager::install(c("Seurat", "edgeR", "presto", "SingleCellExperiment", 
                       "scDblFinder", "ComplexHeatmap", "EnhancedVolcano", 
                       "monocle3", "SeuratWrappers"))

# GitHub packages
devtools::install_github(c("samuel-marsh/scCustomize", 
                           "dtm2451/dittoSeq",
                           "cole-trapnell-lab/hooke",
                           "cole-trapnell-lab/PLNmodels", 
                           "jokergoo/bubbleHeatmap"))
```

Note: To exactly recapitulate q values for differential abundance analysis, PLNmodels must be installed from cole-trapnell-lab, not from other sources.

---

## Getting the data

Download processed input data (~30 GB):

**[Download input_data.zip](https://drive.google.com/file/d/1UcX7488msB4lrT9UUWTUvYUg4rvRFYHe/view?usp=drive_link)**

Extract to `input_data/` in your chosen directory.

The data includes:
- Processed Seurat objects (pilot data,  50-gene screen)
- Daniocell reference atlas (for label transfer)
- Supporting files for scRNAseq analysis
- gRNA detection tables
- Pre-computed differential expression results
- Validation measurements (in situ, imaging data measurements)

---

## Quick start

1. Open any `.Rmd` file in RStudio
2. Update the working directory path in the setup chunk:
   ```r
   knitr::opts_knit$set(root.dir = "/path/to/MIC-Drop-seq")
   ```
3. Run chunks sequentially or click "Run All"

**Figure 1 demo**: The pilot experiment (8 genes, 22K cells) runs in ~20 minutes and generates all Figure 1 panels in `outputs_fig1/`.

---

## Reproducing figures

Each .Rmd file generates the corresponding figure panels:

| Script | Run time | Outputs |
|--------|----------|---------|
| Figure 1 | ~20 min | Main: 1B-I; Supp: S2, S4, S5 |
| Figure 2 | ~30 min - 24 hr | Main: 2B-D; Supp: S6-S8, Table S4 |
| Figure 3 | ~20 min | Main: 3A-L; Supp: S9 |
| Figure 4 | ~20 min | Main: 4A-I; Supp: S10-S11 |


Outputs are saved to `outputs_fig*/` directories. Total runtime ~1-1.5 hours on a standard desktop.

---


---

## Data availability

**Processed data**: Available via the link above

**Raw sequencing data**: Is available to download on GEO with accession [GSE315445](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE315445) 

---

## Citation

```bibtex
@article{carey2025micdropseq,
  title={MIC-Drop-seq: Scalable single-cell phenotyping of mutant vertebrate embryos},
  author={Carey, Clayton M and Parvez, Saba and Brandt, Zachary J and 
          Bisgrove, Brent W and Yates, Christopher J and 
          Peterson, Randall T and Gagnon, James A},
  journal={bioRxiv},
  year={2025},
  doi={10.1101/2025.05.27.656468}
}
```

---

## Contact

**Primary Authors* 
- Clay Carey: clay.carey@utah.edu
- Saba Parvez: saba.parvez@northwestern.edu

**Corresponding authors:**
- James Gagnon: james.gagnon@utah.edu  
- Randall Peterson: randall.peterson@pharm.utah.edu


---

## License

CC BY 4.0
