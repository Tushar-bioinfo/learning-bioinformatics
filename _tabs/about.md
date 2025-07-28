---
layout: page
title: About
permalink: /about/
icon: fas fa-user
order: 5
---

<style>
.about-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding-top: 2rem;
}

.profile-pic {
  width: 160px;
  height: 160px;
  border-radius: 50%;
  object-fit: cover;
  box-shadow: 0 0 12px rgba(0, 255, 255, 0.2);
  margin-bottom: 1.5rem;
}

.heading {
  font-size: 1.8rem;
  color: #00f2ff;
  font-weight: bold;
  text-align: center;
  margin-bottom: 1rem;
}

.about-text {
  max-width: 800px;
  padding: 1rem 2rem;
  text-align: center;
  color: #e0e0e0;
  line-height: 1.8;
  font-size: 1.05rem;
}

.skill-wrapper {
  max-width: 960px;
  margin: 2.5rem auto 4rem;
  padding: 1.5rem 2rem;
  background: #1c1c1c;
  border-radius: 20px;
  box-shadow: 0 0 15px rgba(0,255,255,0.05);
}

.skill-title {
  font-size: 1.3rem;
  font-weight: 600;
  color: #00f2ff;
  margin-bottom: 1.2rem;
  text-align: center;
}

.skill-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.7rem;
  justify-content: center;
}

.skill-tag {
  background-color: #2a2a2a;
  color: #00f2ff;
  padding: 0.5rem 1rem;
  border-radius: 12px;
  font-size: 0.85rem;
  font-weight: 500;
  transition: all 0.3s ease;
}

.skill-tag:hover {
  background-color: #00f2ff;
  color: #000;
}
</style>

<div class="about-container">
  <img src="/assets/img/tushar-profile.png" alt="Tushar" class="profile-pic">

  <div class="heading">MS Bioinformatics & Computational Biology</div>

  <div class="about-text">
    Hi, I’m Tushar — a Master's student in Bioinformatics & Computational Biology at the University of South Florida (Class of 2026), 
    focused on applying machine learning and deep learning to biological data, with a particular interest in cancer research, 
    immunogenomics, and transcriptomics.

    <br><br>

    My work bridges deep learning with immune receptor sequence analysis, single-nucleus RNA-seq profiling, and structural 
    characterization of CDR3 regions. I design modular, reproducible bioinformatics pipelines using tools like Nextflow, Docker, 
    and HPC, enabling scalable analysis of real-world biomedical datasets.
  </div>
</div>

<div class="skill-wrapper">
  <div class="skill-title">🧠 Tools, Frameworks, & Techniques</div>
  <div class="skill-tags">
    <span class="skill-tag">scikit-learn</span>
    <span class="skill-tag">PyTorch</span>
    <span class="skill-tag">Optuna</span>
    <span class="skill-tag">LSTM</span>
    <span class="skill-tag">Mean Pooling</span>
    <span class="skill-tag">ROC AUC</span>
    <span class="skill-tag">F1 Score</span>
    <span class="skill-tag">Seurat</span>
    <span class="skill-tag">Harmony</span>
    <span class="skill-tag">DADA2</span>
    <span class="skill-tag">snRNA-seq</span>
    <span class="skill-tag">VDJdb</span>
    <span class="skill-tag">CDR3 Analysis</span>
    <span class="skill-tag">Differential Expression</span>
    <span class="skill-tag">metapredict</span>
    <span class="skill-tag">GDC / TCGA</span>
    <span class="skill-tag">Nextflow (DSL2)</span>
    <span class="skill-tag">Docker</span>
    <span class="skill-tag">Conda</span>
    <span class="skill-tag">HPC</span>
    <span class="skill-tag">SLURM</span>
    <span class="skill-tag">SAMtools</span>
    <span class="skill-tag">STAR</span>
    <span class="skill-tag">bwa mem</span>
    <span class="skill-tag">fasterq-dump</span>
    <span class="skill-tag">SRA Toolkit</span>
    <span class="skill-tag">Matplotlib</span>
    <span class="skill-tag">Seaborn</span>
    <span class="skill-tag">ggplot2</span>
    <span class="skill-tag">UMAP</span>
    <span class="skill-tag">PCA</span>
    <span class="skill-tag">EDA</span>
  </div>
</div>
