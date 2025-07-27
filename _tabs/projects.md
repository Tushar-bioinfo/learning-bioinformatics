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

<!-- Project Card 1 -->
<div class="project-card">
  <div class="project-number">01</div>
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

<!-- Project Card 2 -->
<div class="project-card">
  <div class="project-number">02</div>
  <div class="project-title">Single-Nucleus RNA-seq of Hepatoblastoma</div>
  <div class="project-description">
    snRNA-seq analysis using Seurat and Harmony to identify cell clusters and tumor subtypes. Includes DEG analysis, Dockerization, and automated workflow.
  </div>
  <div class="tech-stack">
    <span class="tech-badge">Seurat</span>
    <span class="tech-badge">Differential Expression</span>
    <span class="tech-badge">PCA</span>
    <span class="tech-badge">Docker</span>
  </div>
  <a href="/learning-bioinformatics/projects/project-2/" class="project-link-icon" title="Project Details">
    <i class="fas fa-arrow-up-right-from-square"></i>
  </a>
</div>

<!-- Add more cards as needed -->
