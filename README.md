# MIC-Drop-seq Analysis Code

Code to reproduce figures from Carey et al., "MIC-Drop-seq: Scalable single-cell phenotyping of mutant vertebrate embryos"

[![bioRxiv](https://img.shields.io/badge/bioRxiv-10.1101%2F2025.05.27.656468-b31b1b.svg)](https://doi.org/10.1101/2025.05.27.656468)

---

## Abstract 

Advances in genome engineering and single-cell RNA sequencing (scRNAseq) have revolutionized the ability to precisely map gene functions, yet scaling these techniques for large-scale genetic screens in animals remains challenging. We combined high-throughput gene disruption in zebrafish embryos via Multiplexed Intermixed CRISPR Droplets with phenotyping by multiplexed scRNAseq (MIC-Drop-seq). In one MIC-Drop-seq experiment, we intermixed and injected droplets targeting 50 transcriptional regulators into 1,000 zebrafish embryos, followed by pooled scRNAseq. Tissue-specific gene expression and cell abundance analysis of demultiplexed mutant cells recapitulated many known phenotypes, while also uncovering novel functions in brain and mesoderm development. We observed pervasive cell-extrinsic effects among these phenotypes, highlighting how whole-embryo sequencing captures complex developmental interactions. Thus, MIC-Drop-seq provides a powerful and scalable platform for mapping gene functions in vertebrate development with cellular resolution.

---
## What's here

This repository contains R Markdown files to reproduce all main and supplementary figures from the manuscript:

- `Figure1_MIC-Drop-seq.Rmd` - Proof-of-concept validation (8-gene pilot)
- `Figure2_MIC-Drop-seq.Rmd` - 50-gene screen analysis  
- `Figure3_MIC-Drop-seq.Rmd` - Phenotype validations
- `Figure4_MIC-Drop-seq.Rmd` - Cell-extrinsic effects

---

## Requirements

**Software:**
- R ≥ 4.0 (tested on 4.3.1)
- RStudio (recommended)


**Hardware:**
- 16 GB RAM minimum, 32 GB recommended
- ~5 GB free disk space

Tested on macOS Ventura/Sonoma and Ubuntu 20.04/22.04.

---

## Installation

Install R packages:

```r
# CRAN packages
install.packages(c("tidyverse", "ggplot2", "viridis", "BiocManager", "devtools"))

# Bioconductor
BiocManager::install(c("Seurat", "edgeR", "monocle3", "ComplexHeatmap"))

# GitHub packages
devtools::install_github("samuel-marsh/scCustomize")
devtools::install_github("cole-trapnell-lab/hooke")
```

Installation takes ~20-30 minutes depending on your system.

---

## Getting the data

Download input data (1.2 GB) from Google Drive:

**[Download input_data.zip](https://drive.google.com/file/d/1_s4SJdaYLeF-0qQSutJPpQfDakyEfRVV/view?usp=drive_link)**

Extract to `input_data/` in this directory.

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

**Processed data**: Available via Google Drive link above

**Raw sequencing**: Will be available on GEO upon publication

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

**Primary Author** 
- Clay Carey: clay.carey@utah.edu

**Corresponding authors:**
- James Gagnon: james.gagnon@utah.edu  
- Randall Peterson: randall.peterson@pharm.utah.edu


---

## License

CC BY-NC 4.0
