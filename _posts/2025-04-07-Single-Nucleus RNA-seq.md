---
title: "Single-Nucleus RNA-seq Analysis of Hepatoblastoma: Clustering, Annotation & Tumor–PDX Comparison"
date: 2025-04-07 00:00:00 +0000
tags: [Seurat, Harmony, Single-Nucleus RNA-seq, Hepatoblastoma, Docker, Bioinformatics]
image:
  path: https://tushar-bioinfo.github.io/learning-bioinformatics/assets/img/post3/roc_curve.png
  alt: "Boston housing prediction banner"
---

This project presents a reproducible pipeline for analyzing **single-nucleus RNA-seq (snRNA-seq)** data from hepatoblastoma tumor, PDX, and normal samples. The workflow includes Seurat-based QC, batch correction using Harmony, clustering, cell type annotation using GeneCards, and a focused differential gene expression (DGE) analysis on cluster 1 (fetal-like hepatoblastoma).

---

## Project Overview

> **Goal**: Analyze transcriptional differences between tumor and PDX cells within hepatoblastoma using snRNA-seq data, and understand how the tumor microenvironment influences gene expression.

---

## Technologies Used

- **Seurat** for preprocessing, clustering, visualization
- **Harmony** for batch correction
- **EnhancedVolcano** for differential expression visualization
- **GeneCards** for biological annotation
- **Docker** for reproducibility

---

## Step-by-Step Workflow

### 1. Data Input & Setup

```r
basedir <- "/your/absolute/path/to/data"
dirs <- list.dirs(basedir, full.names = FALSE, recursive = FALSE)

for (i in dirs) {
  read <- Read10X(file.path(basedir, i))
  obj <- CreateSeuratObject(counts = read, min.cells = 3, min.features = 200)
  seurat_list[[gsub("_filtered_feature_bc_matrix", "", i)]] <- obj
}
```

---

### 2. Quality Control & Normalization

```r
filtered_obj <- subset(merged_obj, subset = nFeature_RNA > 500 & nCount_RNA > 1000 & mt_percent < 10)
filtered_obj <- NormalizeData(filtered_obj)
filtered_obj <- FindVariableFeatures(filtered_obj)
filtered_obj <- ScaleData(filtered_obj)
filtered_obj <- RunPCA(filtered_obj)
```

---

### 3. Batch Correction with Harmony

```r
harmony_obj <- filtered_obj %>%
  RunHarmony(group.by.vars = 'sample_id') %>%
  RunUMAP(reduction = 'harmony', dims = 1:20) %>%
  FindNeighbors(reduction = 'harmony', dims = 1:20) %>%
  FindClusters(resolution = 0.1)
```

> Harmony effectively reduced batch effects across samples, enabling accurate clustering.

---

### 4. Clustering and Manual Annotation

```r
top10 <- FindAllMarkers(harmony_obj, only.pos = TRUE) %>%
  group_by(cluster) %>%
  top_n(10, wt = avg_log2FC)

harmony_obj$celltype <- "unknown"
harmony_obj$celltype[which(Idents(harmony_obj) == "1")] <- "Fetal-like hepatoblastoma"
```

> GeneCards was used to interpret marker genes and assign biologically meaningful labels. ( add tip) 

---

### 5. Focus: Cluster 1 – Fetal-like Hepatoblastoma

Cluster 1 showed high expression of **AFP**, **SLC22A9**, **CYP3A7** — matching fetal liver identity. We compared gene expression between tumor and PDX cells to study environmental effects.

```r
deg_fetal <- FindMarkers(fetal_like, ident.1 = "tumor", ident.2 = "PDX", logfc.threshold = 0.25)
```

>  Tumor cells showed higher expression of immune/stress response genes (e.g., **CFH**, **CYP3A5**), reflecting their in vivo complexity. ( add - warning)

---

### 6. Visualization

```r
DimPlot(harmony_obj, group.by = "celltype", label = TRUE)
DoHeatmap(harmony_obj, features = top10$gene)
EnhancedVolcano(deg_balanced, lab = rownames(deg_balanced),
                x = 'avg_log2FC', y = 'p_val_adj')
```

---

## {% include label.html text="Key Insights" %}

- PDX cells retained fetal liver identity; tumor cells diverged under immune pressure
- DGE analysis revealed complement/stress response activation in tumors
- Supports [PMID: 34497364](https://pubmed.ncbi.nlm.nih.gov/34497364): PDXs are cleaner models, but lack complex tumor–host interactions

---

## Docker Integration

```dockerfile
FROM rocker/r-ver:4.3.1
RUN R -e "remotes::install_version('Seurat', version = '5.3.0')"
...
```

> Docker ensures reproducibility of the R environment and pipeline. tip

---

## Conclusion

This project demonstrates a full snRNA-seq analysis pipeline from raw data to biological insight. It combines technical rigor with biological interpretation, showing how tumor context alters transcriptional profiles — and how to build reproducible pipelines using Docker.
