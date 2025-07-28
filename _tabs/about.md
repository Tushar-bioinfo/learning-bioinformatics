---
layout: page
title: About Me
permalink: /about/
icon: fas fa-user
order: 5
---

<style>
.about-container {
  text-align: center;
  padding: 2rem;
  color: #ccc;
}

.about-container img {
  width: 170px;
  height: 170px;
  object-fit: cover;
  border-radius: 50%;
  border: 3px solid #00f2ff;
  box-shadow: 0 0 12px rgba(0,255,255,0.2);
  margin-bottom: 1rem;
}

.about-container h1 {
  font-size: 1.6rem;
  color: #00f2ff;
  margin-bottom: 0.5rem;
}

.about-container p {
  max-width: 700px;
  margin: 0 auto 1.5rem auto;
  line-height: 1.7;
  font-size: 1rem;
  color: #d4d4d4;
}

.skill-group {
  margin: 2rem auto;
  max-width: 850px;
  padding: 1.2rem 1.5rem;
  background: #1f1f1f;
  border-radius: 14px;
  box-shadow: 0 0 12px rgba(0,255,255,0.05);
}

.skill-group h3 {
  text-align: left;
  font-size: 1.2rem;
  color: #00f2ff;
  margin-bottom: 1rem;
}

.skill-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.6rem;
}

.skill-tags a {
  text-decoration: none;
  color: #00f2ff;
  background: #2c2c2c;
  padding: 0.4rem 0.8rem;
  border-radius: 10px;
  font-size: 0.85rem;
  transition: background 0.3s ease;
}

.skill-tags a:hover {
  background: #00f2ff;
  color: #000;
}
</style>

<div class="about-container">
  <img src="//assets/img/tushar-profile.png" alt="Profile Photo">
  <h1>MS Bioinformatics & Computational Biology</h1>

  <p>
    Hi, I’m Tushar, focused on applying machine learning and deep learning to biological data, with a particular interest in cancer research, immunogenomics, and transcriptomics.
  </p>
  <p>
    My work bridges deep learning with immune receptor sequence analysis, single-nucleus RNA-seq profiling, and structural characterization of CDR3 regions. I design modular, reproducible bioinformatics pipelines using tools like Nextflow, Docker, and HPC, enabling scalable analysis of real-world biomedical datasets.
  </p>
</div>

<!-- Skill Groups -->
<div class="skill-group">
  <h3>🧠 Machine & Deep Learning</h3>
  <div class="skill-tags">
    <a href="#">scikit-learn</a>
    <a href="#">XGBoost</a>
    <a href="#">LSTM</a>
    <a href="#">Mean Pooling</a>
    <a href="#">PyTorch</a>
    <a href="#">Optuna</a>
  </div>
</div>

<div class="skill-group">
  <h3>🔬 Bioinformatics</h3>
  <div class="skill-tags">
    <a href="#">Seurat</a>
    <a href="#">Harmony</a>
    <a href="#">VDJdb</a>
    <a href="#">metapredict</a>
    <a href="#">SAMtools</a>
  </div>
</div>

<div class="skill-group">
  <h3>🛠️ Pipelines & Reproducibility</h3>
  <div class="skill-tags">
    <a href="#">Nextflow</a>
    <a href="#">Docker</a>
    <a href="#">Conda</a>
    <a href="#">NGC</a>
  </div>
</div>

<div class="skill-group">
  <h3>⚙️ HPC & Data Tools</h3>
  <div class="skill-tags">
    <a href="#">Slurm</a>
    <a href="#">GDC Toolkit</a>
    <a href="#">Pandas</a>
    <a href="#">NumPy</a>
    <a href="#">JSONL</a>
  </div>
</div>

<div class="skill-group">
  <h3>📊 Data Visualization</h3>
  <div class="skill-tags">
    <a href="#">Matplotlib</a>
    <a href="#">Seaborn</a>
    <a href="#">UMAP</a>
  </div>
</div>
