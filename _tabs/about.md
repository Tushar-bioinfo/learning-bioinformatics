---
layout: page
title: About
permalink: /about/
icon: fas fa-user
order: 2
---

<style>
.about-wrapper {
  display: flex;
  flex-wrap: wrap;
  gap: 2rem;
  align-items: flex-start;
  margin-top: 2rem;
}

.about-image {
  flex: 0 0 180px;
  max-width: 180px;
  border-radius: 16px;
  overflow: hidden;
  box-shadow: 0 0 15px rgba(0,255,255,0.1);
}

.about-image img {
  width: 100%;
  border-radius: 16px;
  display: block;
}

.about-text {
  flex: 1;
  min-width: 260px;
  background: #1f1f1f;
  padding: 2rem 2.5rem;
  border-radius: 20px;
  box-shadow: 0 0 20px rgba(0, 255, 255, 0.05);
  color: #eaeaea;
  line-height: 1.75;
}

.about-text h1 {
  color: #00f2ff;
  font-size: 2rem;
  margin-bottom: 1rem;
}

.about-text p {
  margin-bottom: 1rem;
}

.skill-section {
  background: #111;
  border-radius: 14px;
  padding: 1.5rem 2rem;
  box-shadow: 0 0 10px rgba(0,255,255,0.03);
  margin-top: 2rem;
}

.skill-section h2 {
  font-size: 1.2rem;
  color: #00f2ff;
  margin-bottom: 1rem;
}

.skill-category {
  margin-bottom: 1.2rem;
}

.skill-category-title {
  font-weight: bold;
  font-size: 0.95rem;
  color: #ccc;
  margin-bottom: 0.5rem;
}

.skill-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.6rem;
}

.skill-tag {
  background-color: #2c2c2c;
  color: #00f2ff;
  padding: 0.35rem 0.8rem;
  border-radius: 12px;
  font-size: 0.8rem;
  font-weight: 500;
  transition: background 0.3s ease;
}

.skill-tag:hover {
  background-color: #00f2ff;
  color: #000;
}
</style>

<div class="about-wrapper">
  <div class="about-image">
    <img src="/assets/img/tushar-profile.png" alt="Tushar's profile photo">
  </div>
  <div class="about-text">
    <h1>👋 About Me</h1>
    <p>
      Hi, I'm Tushar — a Master’s student in Bioinformatics and Computational Biology at the University of South Florida (Class of 2026).
      I specialize in applying machine learning and deep learning to biological data, with a focus on <strong>cancer research</strong>,
      <strong>immunogenomics</strong>, and <strong>transcriptomics</strong>.
    </p>
    <p>
      My projects span deep learning on immune receptor sequences, single-nucleus RNA-seq analysis, and structural profiling of CDR3 regions.
      I develop reproducible, modular pipelines using <strong>Nextflow</strong>, <strong>Docker</strong>, and <strong>HPC</strong> to handle real-world biomedical data.
    </p>
  </div>
</div>

<div class="skill-section">
  <h2>🛠️ Skills & Tools</h2>

  <div class="skill-category">
    <div class="skill-category-title">Machine Learning & Deep Learning</div>
    <div class="skill-tags">
      <span class="skill-tag">scikit-learn</span>
      <span class="skill-tag">PyTorch</span>
      <span class="skill-tag">Optuna</span>
      <span class="skill-tag">LSTM</span>
      <span class="skill-tag">ROC AUC</span>
      <span class="skill-tag">F1 Score</span>
      <span class="skill-tag">Mean Pooling</span>
    </div>
  </div>

  <div class="skill-category">
    <div class="skill-category-title">Bioinformatics & Genomics</div>
    <div class="skill-tags">
      <span class="skill-tag">Seurat</span>
      <span class="skill-tag">Harmony</span>
      <span class="skill-tag">DADA2</span>
      <span class="skill-tag">VDJdb</span>
      <span class="skill-tag">metapredict</span>
      <span class="skill-tag">GDC / TCGA</span>
      <span class="skill-tag">snRNA-seq</span>
      <span class="skill-tag">CDR3 Analysis</span>
      <span class="skill-tag">Differential Expression</span>
    </div>
  </div>

  <div class="skill-category">
    <div class="skill-category-title">Pipelines & Reproducibility</div>
    <div class="skill-tags">
      <span class="skill-tag">Nextflow (DSL2)</span>
      <span class="skill-tag">SLURM</span>
      <span class="skill-tag">Docker</span>
      <span class="skill-tag">Conda</span>
      <span class="skill-tag">HPC</span>
    </div>
  </div>

  <div class="skill-category">
    <div class="skill-category-title">NGS Data Processing</div>
    <div class="skill-tags">
      <span class="skill-tag">SRA Toolkit</span>
      <span class="skill-tag">STAR</span>
      <span class="skill-tag">bwa mem</span>
      <span class="skill-tag">SAMtools</span>
      <span class="skill-tag">BAM Slicing</span>
      <span class="skill-tag">fasterq-dump</span>
    </div>
  </div>

  <div class="skill-category">
    <div class="skill-category-title">Visualization & Analysis</div>
    <div class="skill-tags">
      <span class="skill-tag">Seaborn</span>
      <span class="skill-tag">Matplotlib</span>
      <span class="skill-tag">ggplot2</span>
      <span class="skill-tag">UMAP</span>
      <span class="skill-tag">PCA</span>
      <span class="skill-tag">EDA</span>
    </div>
  </div>
</div>
