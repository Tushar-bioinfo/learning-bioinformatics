---
layout: page
title: About Me
permalink: /about/
icon: fas fa-user
order: 5
---

<style>
.skill-category {
  background: #1a1a1a;
  border-radius: 12px;
  padding: 1.2rem 1rem;
  margin: 1.5rem auto;
  max-width: 860px;
  box-shadow: 0 0 12px rgba(0,255,255,0.04);
  text-align: left;
}

.skill-category h3 {
  font-size: 1rem;
  color: #00f2ff;
  margin-bottom: 0.6rem;
  font-weight: 600;
}

.icon-grid {
  display: flex;
  flex-wrap: wrap;
  gap: 0.6rem;
}

.icon-grid .icon-tag {
  background: #2a2a2a;
  padding: 0.5rem 0.9rem;
  border-radius: 10px;
  font-size: 0.85rem;
  color: #e2e2e2;
  font-weight: 500;
  border: 1px solid #00f2ff2a;
  transition: all 0.3s ease;
}

.icon-grid .icon-tag:hover {
  background: #00f2ff;
  color: #000;
  transform: scale(1.05);
  cursor: pointer;
}
</style>


<div class="about-wrapper">
  <img src="/assets/img/tushar-profile.png" alt="Tushar">
  <h1>MS Bioinformatics & Computational Biology</h1>

  <p>
    Hi, I’m Tushar. I’m currently exploring how machine learning and deep learning can be applied to biological data, with a growing focus on cancer research, immunogenomics, and transcriptomics.
    <br><br>
    My work so far includes projects on immune receptor sequence analysis, single-nucleus RNA-seq profiling, and structural characterization of CDR3 regions. I'm learning to build scalable, reproducible pipelines using tools like Nextflow, Docker, and HPC, and I enjoy tackling real-world biomedical data challenges as I continue developing my skills.
  </p>
</div>

<!-- ==================== Skills Heading ==================== -->
<div class="about-wrapper">
  <h1>Skills</h1>
</div>

<!-- ==================== Bioinformatics ==================== -->
<div class="skill-category">
  <h3>Bioinformatics</h3>
  <div class="icon-grid">
    <div class="icon-tag" title="Seurat — Single-cell RNA-seq">Seurat</div>
    <div class="icon-tag" title="Scanpy — Single-cell RNA-seq (Python)">Scanpy</div>
    <div class="icon-tag" title="Bioconductor — R genomics packages">Bioconductor</div>
    <div class="icon-tag" title="STAR — RNA-seq aligner">STAR</div>
    <div class="icon-tag" title="BEDTools — Genomic intervals">BEDTools</div>
    <div class="icon-tag" title="Bowtie2 — Short-read aligner">Bowtie2</div>
    <div class="icon-tag" title="MiXCR — TCR/BCR repertoire">MiXCR</div>
    <div class="icon-tag" title="VDJdb — Immune repertoire DB">VDJdb</div>
    <div class="icon-tag" title="DESeq2 — Differential expression">DESeq2</div>
    <div class="icon-tag" title="GATK — Variant calling toolkit">GATK</div>
    <div class="icon-tag" title="SAMtools — BAM/SAM processing">SAMtools</div>
    <div class="icon-tag" title="BLAST — Sequence search/alignment">BLAST</div>
  </div>
</div>

<!-- ==================== AI & Machine Learning ==================== -->
<div class="skill-category">
  <h3>AI & Machine Learning</h3>
  <div class="icon-grid">
    <div class="icon-tag" title="scikit-learn — ML toolkit">scikit-learn</div>
    <div class="icon-tag" title="XGBoost — Gradient boosting trees">XGBoost</div>
    <div class="icon-tag" title="Random Forest — Ensemble method">Random Forest</div>
    <div class="icon-tag" title="Support Vector Machine — SVM classifier">SVM</div>
    <div class="icon-tag" title="LSTM — Long Short-Term Memory network">LSTM</div>
    <div class="icon-tag" title="Transformer — Attention-based models">Transformer</div>
    <div class="icon-tag" title="Attention — Deep learning layers">Attention</div>
    <div class="icon-tag" title="PyTorch — Deep learning framework">PyTorch</div>
    <div class="icon-tag" title="TensorFlow — Deep learning framework">TensorFlow</div>
    <div class="icon-tag" title="Keras — High-level API">Keras</div>
    <div class="icon-tag" title="SHAP — Model interpretability">SHAP</div>
  </div>
</div>

<!-- ==================== Pipelines & Reproducibility ==================== -->
<div class="skill-category">
  <h3>Pipelines & Reproducibility</h3>
  <div class="icon-grid">
    <div class="icon-tag" title="Nextflow — Workflow automation">Nextflow</div>
    <div class="icon-tag" title="Docker — Containerization">Docker</div>
    <div class="icon-tag" title="Singularity — HPC containers">Singularity</div>
    <div class="icon-tag" title="Conda — Env management">Conda</div>
    <div class="icon-tag" title="AWS — Cloud">AWS</div>
  </div>
</div>

<!-- ==================== Statistical & Survival Analysis ==================== -->
<div class="skill-category">
  <h3>Statistical & Survival Analysis</h3>
  <div class="icon-grid">
    <div class="icon-tag" title="Kaplan–Meier estimator">Kaplan–Meier</div>
    <div class="icon-tag" title="Cox Regression — Survival modeling">Cox Regression</div>
    <div class="icon-tag" title="Fisher’s Exact Test">Fisher's Test</div>
    <div class="icon-tag" title="Log-Rank Test — Survival stats">Log-Rank Test</div>
  </div>
</div>

<!-- ==================== Data Tools & HPC ==================== -->
<div class="skill-category">
  <h3>Data Tools & HPC</h3>
  <div class="icon-grid">
    <div class="icon-tag" title="Slurm — HPC job manager">Slurm</div>
    <div class="icon-tag" title="GDC Toolkit — Data commons">GDC Toolkit</div>
    <div class="icon-tag" title="Pandas — Python data analysis">Pandas</div>
    <div class="icon-tag" title="NumPy — Scientific computing">NumPy</div>
  </div>
</div>

<!-- ==================== Visualization ==================== -->
<div class="skill-category">
  <h3>Visualization</h3>
  <div class="icon-grid">
    <div class="icon-tag" title="Matplotlib — Plots">Matplotlib</div>
    <div class="icon-tag" title="Seaborn — Stats viz">Seaborn</div>
    <div class="icon-tag" title="ggplot2 — R visualization">ggplot2</div>
    <div class="icon-tag" title="UMAP — Dim. reduction">UMAP</div>
    <div class="icon-tag" title="t-SNE — Visualization">t-SNE</div>
  </div>
</div>
