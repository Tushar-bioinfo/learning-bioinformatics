---
layout: page
title: Projects
icon: fas fa-flask
permalink: /projects/
order: 3
---
  
<style>
.project-card {
  position: relative;
  background: #1f1f1f;
  padding: 1.8rem 2rem;
  border-radius: 16px;
  box-shadow: 0 4px 18px rgba(0,0,0,0.15);
  margin-bottom: 2rem;
  transition: transform 0.3s ease;
  border: 1px solid #333;
}

.project-card:hover {
  transform: scale(1.01);
}

.project-number {
  font-family: monospace;
  font-size: 1rem;
  color: #00f2ff;
  margin-bottom: 0.4rem;
}

.project-title {
  font-weight: bold;
  font-size: 1.3rem;
  color: #fff;
  margin-bottom: 0.3rem;
}

.project-description {
  font-size: 1rem;
  color: #ccc;
  margin-bottom: 1rem;
}

.tech-stack {
  display: flex;
  flex-wrap: wrap;
  gap: 0.6rem;
}

.tech-badge {
  background: #101010;
  border: 1px solid #333;
  color: #eee;
  font-size: 0.8rem;
  padding: 0.3rem 0.7rem;
  border-radius: 12px;
  font-family: monospace;
}

.project-link-icon {
  position: absolute;
  top: 1.5rem;
  right: 1.5rem;
  background: #2c2c2c;
  border-radius: 50%;
  width: 38px;
  height: 38px;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: background 0.2s ease;
}

.project-link-icon:hover {
  background: #00f2ff;
}

.project-link-icon i {
  color: white;
  font-size: 1rem;
}
</style>

<!-- Project Card 01 -->
<div class="project-card">
  <div class="project-number">01</div>
  <div class="project-title">Single-Nucleus RNA-seq of Hepatoblastoma</div>
  <div class="project-description">
    I built a complete end-to-end machine learning pipeline in Python using scikit-learn to predict Boston housing prices. This project demonstrates my ability to perform data cleaning, feature engineering, multivariable regression, diagnostic evaluation, and clear result interpretation — skills I also apply to biological datasets. Visualizations were created with Matplotlib and Seaborn for clear insights.
  </div>
  <div class="tech-stack">
    <span class="tech-badge">Seurat</span>
    <span class="tech-badge">Differential Expression</span>
    <span class="tech-badge">PCA</span>
    <span class="tech-badge">Dimensionality Reduction</span>
  </div>
  <a href="/learning-bioinformatics/projects/project-2/" class="project-link-icon" title="Project Details">
    <i class="fas fa-arrow-up-right-from-square"></i>
  </a>
</div>

<!-- Project Card 2 -->
<div class="project-card">
  <div class="project-number">02</div>
  <div class="project-title">Tumor vs Normal TCR Classification</div>
  <div class="project-description">
    This project applies deep learning to classify tumor versus normal immune repertoires using TRB CDR3 sequences from lung cancer patients in the CPTAC dataset. The pipeline covers end-to-end preprocessing, variable-length sequence modeling, and interpretability.
  </div>
  <div class="tech-stack">
    <span class="tech-badge">Deep Learning</span>
    <span class="tech-badge">LSTM</span>
    <span class="tech-badge">PyTorch</span>
    <span class="tech-badge">Mean Pooling</span>
  </div>
  <a href="/learning-bioinformatics/projects/project-3/" class="project-link-icon" title="Project Details">
    <i class="fas fa-arrow-up-right-from-square"></i>
  </a>
</div>

<!-- Project Card 3 -->
<div class="project-card">
  <div class="project-number">03</div>
  <div class="project-title">SRA to BAM: Immune Receptor Extraction Pipeline</div>
  <div class="project-description">
    This modular Nextflow pipeline automates immune receptor region extraction from public sequencing datasets. It processes SRA accessions end-to-end: from FASTQ conversion and genome alignment to BAM slicing and cleanup — enabling high-throughput analysis of TCR/BCR regions for immunogenomic studies.
  </div>
  <div class="tech-stack">
    <span class="tech-badge">Nextflow</span>
    <span class="tech-badge">Conda</span>
    <span class="tech-badge">NCBI SRA Toolkit</span>
    <span class="tech-badge">STAR</span>
  </div>
  <a href="/learning-bioinformatics/projects/project-4/" class="project-link-icon" title="Project Details">
    <i class="fas fa-arrow-up-right-from-square"></i>
  </a>
</div>
<!-- Project Card 4 -->
<div class="project-card">
  <div class="project-number">04</div>
  <div class="project-title">Boston House Price Prediction</div>
  <div class="project-description">
    This project builds a complete machine learning pipeline using Python’s scikit-learn to predict Boston housing prices. 
  </div>
  <div class="tech-stack">
    <span class="tech-badge">Scikit-learn</span>
    <span class="tech-badge">Linear Regression</span>
    <span class="tech-badge">Docker</span>
    <span class="tech-badge">Machine Learning</span>
  </div>
  <a href="/learning-bioinformatics/projects/boston-house/" class="project-link-icon" title="Project Details">
    <i class="fas fa-arrow-up-right-from-square"></i>
  </a>
</div>

<!-- Project Card 5 -->
<div class="project-card">
  <div class="project-number">05</div>
  <div class="project-title">Intrinsic Disorder Analysis of Immune Receptor CDR3 Regions</div>
  <div class="project-description">
    This project investigates the structural flexibility of TCR and BCR CDR3 regions by predicting their intrinsic disorder using metapredict. I built a custom pipeline to extract receptor sequences from cancer patient BAM files, run disorder analysis, and compare CDR3 segments to V and J regions to highlight unique biophysical properties.
  </div>
  <div class="tech-stack">
    <span class="tech-badge">metapredict</span>
    <span class="tech-badge">SAMtools</span>
    <span class="tech-badge">GDC (Data Transfer Tool)</span>
    <span class="tech-badge">HPC</span>
  </div>
  <a href="/learning-bioinformatics/projects/project-4/" class="project-link-icon" title="Project Details">
    <i class="fas fa-arrow-up-right-from-square"></i>
  </a>
</div>

<!-- Project Card 6 -->
<div class="project-card">
  <div class="project-number">06</div>
  <div class="project-title">Tumor Severity Prediction from RNA-Seq using ML & Deep Learning</div>
  <div class="project-description">
    Developed a reproducible ML/DL pipeline to classify tumor severity in lung adenocarcinoma using TCGA-LUAD RNA-seq data. Applied ANOVA F-test for gene selection, benchmarked classical models against a CNN with Optuna tuning, and achieved 79% accuracy. Dockerized the project and integrated a future-ready Nextflow pipeline for scalable optimization.
  </div>
  <div class="tech-stack">
    <span class="tech-badge">Keras</span>
    <span class="tech-badge">Optuna</span>
    <span class="tech-badge">CNN</span>
    <span class="tech-badge">RNA-Seq</span>
  </div>
  <a href="/learning-bioinformatics/projects/project-tumor-severity/" class="project-link-icon" title="Project Details">
    <i class="fas fa-arrow-up-right-from-square"></i>
  </a>
</div>
<!-- Project Card 7 -->
<div class="project-card">
  <div class="project-number">07</div>
  <div class="project-title">GATK4 CNV Analysis in Glioblastoma</div>
  <div class="project-description">
    Built an end-to-end, HPC-optimized copy number variation (CNV) pipeline for dbGaP-protected cancer RNA-seq data using GATK4 CNV, automating SRA-to-BAM processing and genome-wide CNV calling across large patient cohorts on the USF RRA cluster.
  </div>
  <div class="tech-stack">
    <span class="tech-badge">GATK4</span>
    <span class="tech-badge">CNV analysis</span>
    <span class="tech-badge">Shell scripting</span>
    <span class="tech-badge">Variant Calling & Structural Variant Detection</span>
  </div>
  <a href="/learning-bioinformatics/projects/project-cnv-gatk4/" class="project-link-icon" title="Project Details">
    <i class="fas fa-arrow-up-right-from-square"></i>
  </a>
</div>
<!-- Add more cards -->
