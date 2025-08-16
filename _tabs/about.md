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
  color: #00f2ff;
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

/* Skills Section */

.skill-category {
  background: #1a1a1a;
  border-radius: 14px;
  padding: 1.2rem 1rem;
  margin: 2rem auto;
  max-width: 860px;
  box-shadow: 0 0 12px rgba(0,255,255,0.04);
  text-align: left;
}

.skill-category h3 {
  font-size: 1.05rem;
  color: #00f2ff;
  margin-bottom: 0.6rem;
  font-weight: 600;
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
  font-size: 0.78rem;
  padding: 0.3rem 0.75rem;
  border-radius: 12px;
  font-family: monospace;
  transition: all 0.3s ease;
}

.tech-badge:hover {
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
    Hi, I’m Tushar, I’m currently exploring how machine learning and deep learning can be applied to biological data, with a growing focus on cancer research, immunogenomics, and transcriptomics.
    <br><br>
    My work so far includes projects on immune receptor sequence analysis, single-nucleus RNA-seq profiling, and structural characterization of CDR3 regions. I'm learning to build scalable, reproducible pipelines using tools like Nextflow, Docker, and HPC, and I enjoy tackling real-world biomedical data challenges as I continue developing my skills.
  </p>
</div>

<h2 style="text-align:center; color:#00f2ff;">Skills</h2>

<!-- ==================== Bioinformatics ==================== -->
<div class="skill-category">
  <h3>Bioinformatics</h3>
  <div class="tech-stack">
    <div class="tech-badge">Seurat</div>
    <div class="tech-badge">Scanpy</div>
    <div class="tech-badge">Bioconductor</div>
    <div class="tech-badge">STAR</div>
    <div class="tech-badge">BEDTools</div>
    <div class="tech-badge">Bowtie2</div>
    <div class="tech-badge">MiXCR</div>
    <div class="tech-badge">VDJdb</div>
    <div class="tech-badge">DESeq2</div>
    <div class="tech-badge">GATK</div>
    <div class="tech-badge">SAMtools</div>
    <div class="tech-badge">BLAST</div>
  </div>
</div>

<!-- ==================== AI & Machine Learning ==================== -->
<div class="skill-category">
  <h3>AI & Machine Learning</h3>
  <div class="tech-stack">
    <div class="tech-badge">scikit-learn</div>
    <div class="tech-badge">XGBoost</div>
    <div class="tech-badge">Random Forest</div>
    <div class="tech-badge">SVM</div>
    <div class="tech-badge">LSTM</div>
    <div class="tech-badge">Transformer</div>
    <div class="tech-badge">Attention</div>
    <div class="tech-badge">PyTorch</div>
    <div class="tech-badge">TensorFlow</div>
    <div class="tech-badge">Keras</div>
    <div class="tech-badge">SHAP</div>
  </div>
</div>

<!-- ==================== Pipelines & Reproducibility ==================== -->
<div class="skill-category">
  <h3>Pipelines & Reproducibility</h3>
  <div class="tech-stack">
    <div class="tech-badge">Nextflow</div>
    <div class="tech-badge">Docker</div>
    <div class="tech-badge">Singularity</div>
    <div class="tech-badge">Conda</div>
    <div class="tech-badge">AWS</div>
  </div>
</div>

<!-- ==================== Statistical & Survival Analysis ==================== -->
<div class="skill-category">
  <h3>Statistical & Survival Analysis</h3>
  <div class="tech-stack">
    <div class="tech-badge">Kaplan–Meier</div>
    <div class="tech-badge">Cox Regression</div>
    <div class="tech-badge">Fisher's Exact Test</div>
    <div class="tech-badge">Log-Rank Test</div>
  </div>
</div>

<!-- ==================== Data Tools & HPC ==================== -->
<div class="skill-category">
  <h3>Data Tools & HPC</h3>
  <div class="tech-stack">
    <div class="tech-badge">Slurm</div>
    <div class="tech-badge">GDC Toolkit</div>
    <div class="tech-badge">Pandas</div>
    <div class="tech-badge">NumPy</div>
  </div>
</div>

<!-- ==================== Visualization ==================== -->
<div class="skill-category">
  <h3>Visualization</h3>
  <div class="tech-stack">
    <div class="tech-badge">Matplotlib</div>
    <div class="tech-badge">Seaborn</div>
    <div class="tech-badge">ggplot2</div>
    <div class="tech-badge">UMAP</div>
    <div class="tech-badge">t-SNE</div>
  </div>
</div>
