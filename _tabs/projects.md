---
layout: page
title: Projects
icon: fas fa-flask
permalink: /projects/
order: 3
---

<style>
.project-entry {
  display: flex;
  align-items: center;
  justify-content: space-between;
  background: #1f1f1f;
  margin: 2rem 0;
  padding: 1.5rem 2rem;
  border-radius: 18px;
  box-shadow: 0 0 12px rgba(0, 255, 255, 0.08);
  transition: transform 0.3s ease;
  position: relative;
}

.project-entry:hover {
  transform: scale(1.01);
  box-shadow: 0 0 20px rgba(0, 255, 255, 0.3);
}

.project-info {
  flex: 1;
  padding-right: 1.5rem;
}

.project-title {
  font-size: 1.4rem;
  font-weight: 700;
  color: #00f2ff;
  margin-bottom: 0.4rem;
}

.project-description {
  font-size: 1rem;
  color: #ccc;
}

.project-links {
  position: absolute;
  top: 1.5rem;
  right: 2rem;
  display: flex;
  gap: 1rem;
}

.project-links a {
  color: #00f2ff;
  font-size: 1.3rem;
  transition: color 0.3s ease;
}

.project-links a:hover {
  color: #ffffff;
}
</style>

<div class="project-entry">
  <div class="project-info">
    <div class="project-title">Tumor vs Normal TCR Classification</div>
    <div class="project-description">
      Deep learning on TRB CDR3 sequences using LSTM to classify tumor vs normal immune repertoires. Fully tokenized, normalized, and modular with Optuna tuning and Nextflow + Docker integration.
    </div>
  </div>
  <div class="project-links">
    <a href="https://github.com/yourusername/tcr-tumor-normal" target="_blank" title="GitHub Repository">
      <i class="fab fa-github"></i>
    </a>
    <a href="/blog/2025/07/25/tcr-tumor-normal-deep-learning.html" title="Read Blog Post">
      <i class="fas fa-book-open"></i>
    </a>
  </div>
</div>

<div class="project-entry">
  <div class="project-info">
    <div class="project-title">Single-Nucleus RNA-Seq of Hepatoblastoma</div>
    <div class="project-description">
      Processed and analyzed fetal-like tumor vs PDX using Seurat, Harmony, and differential expression. Includes cluster annotation and professional visualization. Dockerized for reproducibility.
    </div>
  </div>
  <div class="project-links">
    <a href="https://github.com/yourusername/snRNAseq-hepatoblastoma" target="_blank" title="GitHub Repository">
      <i class="fab fa-github"></i>
    </a>
    <a href="/blog/2025/07/21/hepatoblastoma-snRNAseq-cluster-analysis.html" title="Read Blog Post">
      <i class="fas fa-book-open"></i>
    </a>
  </div>
</div>

<!-- Add more project-entry blocks below as needed -->
