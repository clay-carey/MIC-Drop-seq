# MIC-Drop-seq: Scalable single-cell phenotyping of mutant vertebrate embryos

[![bioRxiv](https://img.shields.io/badge/bioRxiv-10.1101%2F2025.05.27.656468-b31b1b.svg)](https://doi.org/10.1101/2025.05.27.656468)

> **Carey CM**, **Parvez S**, Brandt ZJ, Bisgrove BW, Yates CJ, Peterson RT*, Gagnon JA*  
> *Corresponding authors

---

## Overview

MIC-Drop-seq combines high-throughput CRISPR mutagenesis in zebrafish embryos with multiplexed single-cell RNA sequencing to enable scalable phenotyping of genetic perturbations at cellular resolution. In a single experiment targeting 50 transcriptional regulators across 1,000 embryos, we demonstrate how whole-organism sequencing captures both cell-intrinsic and cell-extrinsic developmental phenotypes that would be missed in traditional screening approaches.


---

## Abstract

Advances in genome engineering and single-cell RNA sequencing (scRNAseq) have revolutionized the ability to precisely map gene functions, yet scaling these techniques for large-scale genetic screens in animals remains challenging. We combined high-throughput gene disruption in zebrafish embryos via Multiplexed Intermixed CRISPR Droplets with phenotyping by multiplexed scRNAseq (MIC-Drop-seq). In one MIC-Drop-seq experiment, we intermixed and injected droplets targeting 50 transcriptional regulators into 1,000 zebrafish embryos, followed by pooled scRNAseq. Tissue-specific gene expression and cell abundance analysis of demultiplexed mutant cells recapitulated many known phenotypes, while also uncovering novel functions in brain and mesoderm development. We observed pervasive cell-extrinsic effects among these phenotypes, highlighting how whole-embryo sequencing captures complex developmental interactions. Thus, MIC-Drop-seq provides a powerful and scalable platform for mapping gene functions in vertebrate development with cellular resolution.

---

### Required Input Data

All input data required to reproduce the figures is available here:

**[ Download input_data.zip (1.2 GB)](https://drive.google.com/file/d/1_s4SJdaYLeF-0qQSutJPpQfDakyEfRVV/view?usp=drive_link)**

After downloading, extract the contents into the `input_data/` directory:


### Raw Sequencing Data

Raw sequencing data (FASTQ files) and processed count matrices will be deposited to GEO upon publication.

---

## Installation

### System Requirements
- **R version**: ≥ 4.0 


### Required R Packages

Install all required packages before running the analysis:

```r
# CRAN packages
install.packages(c(
  "dplyr", "tidyverse", "ggplot2", "stringr",
  "viridis", "ggridges", "cowplot", "patchwork",
  "ggpubr", "rstatix", "DescTools", "ggtext",
  "igraph", "gtExtras"
))

# Bioconductor packages
if (!require("BiocManager", quietly = TRUE))
    install.packages("BiocManager")

BiocManager::install(c(
  "Seurat",
  "edgeR",
  "presto",
  "SingleCellExperiment",
  "scDblFinder",
  "ComplexHeatmap",
  "EnhancedVolcano",
  "monocle3"
))

# GitHub packages
devtools::install_github("samuel-marsh/scCustomize")
devtools::install_github("dtm2451/dittoSeq")
devtools::install_github("cole-trapnell-lab/PLNmodels") 
devtools::install_github("cole-trapnell-lab/hooke")



```

---

## Usage

### Running the Analysis

Each figure is generated from a self-contained R Markdown (`.Rmd`) file. You can run them interactively in RStudio.

#### Option 1: Interactive Analysis (Recommended)
1. Open RStudio
2. Open any `Figure*_MIC-Drop-seq.Rmd` file
3. Update the working directory in the setup chunk to your local path:
   ```r
   knitr::opts_knit$set(root.dir = "/path/to/MIC-Drop-seq")
   ```
4. Run chunks sequentially using `Cmd/Ctrl + Enter` or click "Run All"




