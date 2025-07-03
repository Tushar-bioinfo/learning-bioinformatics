---
layout: page
title: Projects
permalink: /projects/
---

Welcome to my projects page! Below are selected works in immunogenomics, machine learning and transcriptomics. Each project includes code, datasets, and write-ups when available.

---

### Computational Analysis of Intrinsic Disorder in CDR3 Immune Receptor Regions

- **Type**: Immunoinformatics / Structural Bioinformatics  
- **Tech**: Python, R, metapredict, SAMtools, VDJdb  
- **Data**: BAM files from TCGA & CPTAC (via GDC)  
- **Summary**:  
  Explored the structural flexibility of CDR3 regions in immune receptor sequences through per-residue disorder prediction. Combined BAM-based VDJ sequence mining with `metapredict` to score intrinsic disorder across CDR3 and V/J contexts.

- **Workflow**:
  - Extracted CDR3-containing reads from immune receptor loci (e.g., IGH, TRB)
  - Validated V(D)J sequences using VDJdb
  - Processed and exported sequence data with R
  - Applied `metapredict` to generate disorder profiles

- **Key Findings**:
  - CDR3s exhibit **moderate disorder**, consistent with structural flexibility
  - Disorder increases when V/J segments are included, but not to fully disordered levels

- **Links**:  
  - [GitHub](https://github.com/Tushar-bioinfo/Computational-Analysis-of-Intrinsic-Disorder-in-CDR3-Immune-Receptor-Regions)

---

### Single-cell RNA-Seq Analysis of Hepatoblastoma Tumors

- **Type**: Single-Cell Transcriptomics / Cancer Biology  
- **Tech**: R, Seurat, Harmony, ggplot2, dplyr  
- **Data**: snRNA-seq from patient tumors, liver, and PDX models  
- **Summary**:  
  Extended and replicated analysis from a Nature Cancer hepatoblastoma study (PMID: [34497364](https://pubmed.ncbi.nlm.nih.gov/34497364)). Focused on tumor heterogeneity, fetal-like gene expression, and immune infiltration across tissue types.

- **Workflow**:
  - Preprocessed snRNA-seq data with **Seurat**
  - Batch-corrected and clustered cells using **Harmony**
  - Annotated clusters using marker genes and GeneCards
  - Conducted differential gene expression between tumor and PDX cells
  - Visualized genes like **AFP**, **CFH**; profiled immune cell composition

- **Goals**:
  - Identify **fetal-like hepatoblastoma subtypes**
  - Compare transcriptional programs of **tumor vs. PDX**
  - Quantify T cell infiltration and immune landscapes

- **Links**:  
  - [GitHub](https://github.com/Tushar-bioinfo/Single-Cell-RNA-Seq-Analysis-of-Hepatoblastoma-Tumors)

---

### Boston House Price Prediction

- **Type**: Machine Learning / Regression  
- **Tech**: Scikit-learn, pandas, matplotlib  
- **Data**: Boston Housing Dataset (UCI)  
- **Summary**:  
  Built and evaluated linear regression models to predict Boston housing prices based on neighborhood-level features. Explored preprocessing, multicollinearity (VIF), model evaluation, and interpretation.

- **Workflow**:
  - Data cleaning and standardization
  - Exploratory analysis and feature correlation
  - Feature selection using VIF and Lasso
  - Linear regression modeling and interpretation of coefficients
  - Evaluation via R², MAE, RMSE, and residual plots

- **Links**:  
  - [Preprocessing Blog Post](/learning-bioinformatics/2024/07/01/boston-housing_preprocessing.html)  
  - [Model Blog Post](/learning-bioinformatics/2025/07/01/boston-house-model.html)  

---

