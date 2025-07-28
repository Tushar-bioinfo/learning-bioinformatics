---
layout: page
title: About Me
permalink: /about/
icon: fas fa-user
order: 5
---

<style>
.about-wrapper {
  text-align: center;
  padding: 2rem;
  color: #fff;
}

.about-wrapper img {
  width: 160px;
  height: 160px;
  object-fit: cover;
  border-radius: 50%;
  border: 3px solid #00f2ff;
  margin-bottom: 1rem;
  box-shadow: 0 0 14px rgba(0, 255, 255, 0.2);
}

.about-wrapper h1 {
  font-size: 1.7rem;
  color: #ffffff;
  margin-bottom: 0.6rem;
  font-weight: 700;
}

.about-wrapper p {
  max-width: 750px;
  margin: 0 auto 1.8rem auto;
  font-size: 1rem;
  line-height: 1.7;
  color: #ccc;
}

/* Skill Section Styling */
.skill-category {
  background: #1a1a1a;
  border-radius: 14px;
  padding: 1.5rem 1.2rem;
  margin: 1.8rem auto;
  max-width: 860px;
  box-shadow: 0 0 14px rgba(0,255,255,0.05);
  text-align: left;
}

.skill-category h3 {
  font-size: 1.1rem;
  color: #00f2ff;
  margin-bottom: 0.9rem;
  font-weight: 600;
}

.icon-grid {
  display: flex;
  flex-wrap: wrap;
  gap: 0.8rem;
}

.icon-grid .icon-tag {
  display: flex;
  align-items: center;
  justify-content: center;
  background: #2a2a2a;
  padding: 0.8rem;
  border-radius: 12px;
  font-size: 1.3rem;
  color: #00f2ff;
  transition: all 0.3s ease;
  width: 52px;
  height: 52px;
}

.icon-grid .icon-tag:hover {
  background: #00f2ff;
  color: #000;
  transform: scale(1.2);
  cursor: pointer;
}
</style>

<div class="about-wrapper">
  <img src="/assets/img/profile.png" alt="Tushar">
  <h1>MS Bioinformatics & Computational Biology</h1>

  <p>
    Hi, I’m Tushar. I’m currently exploring how machine learning and deep learning can be applied to biological data, with a growing focus on cancer research, immunogenomics, and transcriptomics.
    <br><br>
    My work so far includes projects on immune receptor sequence analysis, single-nucleus RNA-seq profiling, and structural characterization of CDR3 regions. I'm learning to build scalable, reproducible pipelines using tools like Nextflow, Docker, and HPC, and I enjoy tackling real-world biomedical data challenges as I continue developing my skills.
  </p>
</div>

<!-- Skill Categories -->

<!-- ==================== Bioinformatics ==================== -->
<div class="skill-category">
  <h3>Bioinformatics</h3>
  <div class="icon-grid">
    <div class="icon-tag" title="Seurat — Single-cell RNA-seq">SR</div>
    <div class="icon-tag" title="Scanpy — Single-cell RNA-seq (Python)">SC</div>
    <div class="icon-tag" title="Bioconductor — R genomics packages">BC</div>
    <div class="icon-tag" title="STAR — RNA-seq aligner">STAR</div>
    <div class="icon-tag" title="BEDTools — Genomic intervals">BT</div>
    <div class="icon-tag" title="Bowtie2 — Short-read aligner">B2</div>
    <div class="icon-tag" title="MiXCR — TCR/BCR repertoire">MX</div>
    <div class="icon-tag" title="VDJdb — Immune repertoire DB">VDJ</div>
    <div class="icon-tag" title="DESeq2 — Differential expression">D2</div>
    <div class="icon-tag" title="GATK — Variant calling toolkit">GATK</div>
    <div class="icon-tag" title="SAMtools — BAM/SAM processing">ST</div>
    <div class="icon-tag" title="BLAST — Sequence search/alignment">BL</div>
  </div>
</div>
<!-- ==================== AI & Machine Learning ==================== -->
<div class="skill-category">
  <h3>AI & Machine Learning</h3>
  <div class="icon-grid">
    <div class="icon-tag" title="scikit-learn — ML toolkit">SK</div>
    <div class="icon-tag" title="XGBoost — Gradient boosting trees">XG</div>
    <div class="icon-tag" title="Random Forest — Ensemble method">RF</div>
    <div class="icon-tag" title="Support Vector Machine — SVM classifier">SVM</div>
    <div class="icon-tag" title="LSTM — Long Short-Term Memory network">LSTM</div>
    <div class="icon-tag" title="Transformer — Attention-based models">TRF</div>
    <div class="icon-tag" title="Attention Mechanisms — Deep learning attention layers">ATT</div>
    <div class="icon-tag" title="PyTorch — Deep learning framework">PT</div>
    <div class="icon-tag" title="TensorFlow — Deep learning framework">TF</div>
    <div class="icon-tag" title="Keras — High-level neural networks API">KR</div>
    <div class="icon-tag" title="SHAP — Explainable AI (model interpretability)">XAI</div>
  </div>
</div>
<!-- ==================== Pipelines & Reproducibility ==================== -->
<div class="skill-category">
  <h3>Pipelines & Reproducibility</h3>
  <div class="icon-grid">
    <div class="icon-tag" title="Nextflow — Workflow management">NF</div>
    <div class="icon-tag" title="Docker — Containerization">DK</div>
    <div class="icon-tag" title="Singularity — HPC containers">SG</div>
    <div class="icon-tag" title="Conda — Environment management">CD</div>
    <div class="icon-tag" title="AWS — Cloud computing">AWS</div>
  </div>
</div>

<!-- ==================== Statistical & Survival Analysis ==================== -->
<div class="skill-category">
  <h3>Statistical & Survival Analysis</h3>
  <div class="icon-grid">
    <div class="icon-tag" title="Kaplan–Meier estimator">KM</div>
    <div class="icon-tag" title="Cox Regression — Proportional hazards">COX</div>
    <div class="icon-tag" title="Fisher's Exact Test">FT</div>
    <div class="icon-tag" title="Log-Rank Test — Survival analysis">LR</div>
  </div>
</div>

<!-- ==================== Data Tools & HPC ==================== -->
<div class="skill-category">
  <h3>Data Tools & HPC</h3>
  <div class="icon-grid">
    <div class="icon-tag" title="Slurm — HPC job scheduler">SL</div>
    <div class="icon-tag" title="GDC Toolkit — Genomic Data Commons">GDC</div>
    <div class="icon-tag" title="Pandas — Python data analysis">PD</div>
    <div class="icon-tag" title="NumPy — Numerical computing">NP</div>
  </div>
</div>

<!-- ==================== Visualization ==================== -->
<div class="skill-category">
  <h3>Visualization</h3>
  <div class="icon-grid">
    <div class="icon-tag" title="Matplotlib — Python plots">MPL</div>
    <div class="icon-tag" title="Seaborn — Statistical visualization">SNS</div>
    <div class="icon-tag" title="ggplot2 — R plotting system">GG</div>
    <div class="icon-tag" title="UMAP — Dimensionality reduction">UM</div>
    <div class="icon-tag" title="t-SNE — Nonlinear dimensionality reduction">TSNE</div>
  </div>
</div>

