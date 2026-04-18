#  Single-Cell RNA-Seq Analysis Workflow

**Assignment | Bioinformatics | Galaxy Training Network Tutorials**

---

##  Overview

This repository contains the outputs and results from a series of **Single-Cell RNA-Seq (scRNA-seq)** pre-processing and analysis tutorials completed using the [Galaxy Training Network (GTN)](https://training.galaxyproject.org/training-material/topics/single-cell/). The tutorials cover the full scRNA-seq workflow — from raw FASTQ files to processed, analysis-ready data matrices — using 10X Genomics PBMC data.

---

##  Repository Structure

```
 scrna-seq-analysis-workflow/
│
├──  Basic scRNA-seq tutorial/
│   └── Introductory scRNA-seq analysis outputs
│
├──  galaxy tutorial/
│   └── Pre-processing of 10X Single-Cell RNA Datasets (STARsolo + DropletUtils)
│
├──  Anndata tutorial/
│   └── AnnData object generation and inspection
│
├──  Anndata 2nd tutorial/
│   └── Further AnnData manipulation and processing
│
└── README.md
```

---

##  Dataset

| Property | Details |
|----------|---------|
| **Dataset** | PBMC 1k v3 (10X Genomics) |
| **Organism** | *Homo sapiens* |
| **Chemistry** | 10X Chromium v3 |
| **Reference Genome** | GRCh37.75 |
| **Source** | [Zenodo](https://zenodo.org/) / 10X Genomics |

---

##  Workflow Summary

```
Raw FASTQ Reads (R1 + R2, 2 lanes)
            │
            ▼
   Mapping & Quantification
      (RNA STARsolo)
            │
            ├── Log file
            ├── Barcode/Feature Statistic Summaries
            └── Filtered Count Matrix (MTX + Barcodes + Genes)
            │
            ▼
   Cell Barcode Filtering
      (DropletUtils)
            │
            ├── Barcode Rank Plot (knee plot)
            ├── Barcode Ranks Table
            └── Filtered 10X Matrices (Barcodes, Genes, Matrix)
            │
            ▼
   AnnData Object Creation & Manipulation
      (Import AnnData / AnnData Operations)
            │
            └── Final .h5ad AnnData object
```

---

##  Tutorial Descriptions

### 1. Basic scRNA-seq Tutorial
An introduction to the concepts of single-cell RNA sequencing, covering the basics of cell barcoding, UMI counting, and the structure of scRNA-seq data.

### 2. Galaxy Tutorial — Pre-processing of 10X scRNA-seq Data
**Tutorial link:** [GTN Pre-processing of 10X Single-Cell RNA Datasets](https://training.galaxyproject.org/training-material/topics/single-cell/tutorials/scrna-preprocessing-tenx/tutorial.html)

The main pre-processing pipeline run on Galaxy, including:
- **RNA STARsolo** — splice-aware alignment and UMI counting of 10X Chromium reads
- **DropletUtils RankBarcodes** — generating the barcode rank (knee) plot to identify real cells vs empty droplets
- **DropletUtils DefaultDrops** — filtering the raw matrix to retain only high-quality cell barcodes

Key outputs:

| File | Description |
|------|-------------|
| `Barcode_Feature_Statistic_Summaries` | Mapping QC metrics from STARsolo |
| `Matrix_Gene_Counts_filtered` | Filtered count matrix (MTX format) |
| `DropletUtils_Plot` | Knee plot for cell calling |
| `DropletUtils_Barcodes/Genes/Matrices` | Final filtered 10X output |

### 3. AnnData Tutorial
Converting the filtered count matrix output from STARsolo/DropletUtils into the **AnnData (.h5ad)** format — the standard format for downstream scRNA-seq analysis tools like Scanpy.

### 4. AnnData 2nd Tutorial
Further manipulation and inspection of the AnnData object, including adding metadata annotations and preparing the object for downstream clustering and analysis.

---

## 🛠️ Tools Used

| Tool | Purpose |
|------|---------|
| **RNA STARsolo** | Read alignment and UMI quantification |
| **DropletUtils** | Cell barcode filtering (knee plot + DefaultDrops) |
| **MultiQC** | QC report aggregation |
| **Import AnnData** | Format conversion to AnnData (.h5ad) |
| **AnnData Operations** | Metadata manipulation and inspection |

All tools were run on **[Galaxy](https://usegalaxy.eu)** — an open-source, web-based bioinformatics platform.

---

##  Key Concepts

- **Cell Barcodes** — unique DNA sequences that tag each cell's reads
- **UMIs (Unique Molecular Identifiers)** — used to remove PCR duplicates and count unique transcripts
- **Knee Plot** — used to distinguish real cells (high UMI counts) from empty droplets (low UMI counts)
- **AnnData Format** — an HDF5-based format storing the cell × gene count matrix along with cell and gene annotations, used by Scanpy and other tools

---

##  References

- Zheng GX et al. (2017). Massively parallel digital transcriptional profiling of single cells. *Nature Communications*, 8, 14049.
- Wolf FA, Angerer P, Theis FJ (2018). SCANPY: large-scale single-cell gene expression data analysis. *Genome Biology*, 19, 15.
- Dobin A et al. (2013). STAR: ultrafast universal RNA-seq aligner. *Bioinformatics*, 29(1), 15–21.

---

##  Author

**Washma Sajjad**  
Single-Cell RNA-Seq Analysis Workflow Assignment  
Special Topics in Bioinformatics
Galaxy Training Network Tutorials
