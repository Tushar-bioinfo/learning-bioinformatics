---
layout: page
title: Projects
icon: fas fa-flask
permalink: /projects/
---

<style>
.project-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
  gap: 2rem;
  margin-top: 2rem;
}

.project-card {
  background-color: #1f1f1f;
  border-radius: 16px;
  overflow: hidden;
  box-shadow: 0 0 10px rgba(0,255,255,0.08);
  transition: 0.3s ease;
  display: flex;
  flex-direction: column;
  text-decoration: none;
}

.project-card:hover {
  transform: scale(1.03);
  box-shadow: 0 0 20px rgba(0, 255, 255, 0.3);
}

.project-image {
  width: 100%;
  height: 160px;
  object-fit: cover;
}

.project-content {
  padding: 1rem 1.2rem;
  flex-grow: 1;
}

.project-title {
  font-size: 1.2rem;
  font-weight: 600;
  color: #00f2ff;
  margin-bottom: 0.3rem;
}

.project-desc {
  font-size: 0.95rem;
  color: #ccc;
  margin-bottom: 0.8rem;
}

.project-links {
  display: flex;
  gap: 1.2rem;
  align-items: center;
  font-size: 1.1rem;
}

.project-links a {
  color: #56cc9d;
  transition: 0.2s ease;
}

.project-links a:hover {
  color: #00f2ff;
}
</style>

<div class="project-grid">

  <!-- Project 1: Boston -->
  <a href="/projects/boston-house/" class="project-card">
    <img class="project-image" src="/assets/img/project-thumbs/boston.png" alt="Boston Housing">
    <div class="project-content">
      <div class="project-title">Boston House Price Prediction</div>
      <div class="project-desc">A regression-based ML project exploring BIC, RMSE, and housing feature impacts.</div>
      <div class="project-links">
        <i class="fab fa-github"></i>
        <span>Blog: Coming Soon</span>
      </div>
    </div>
  </a>

  <!-- Project 2: TRB Motif -->
  <a href="/projects/trb-survival/" class="project-card">
    <img class="project-image" src="/assets/img/project-thumbs/Antibody-CDR.png" alt="TRB Motif">
    <div class="project-content">
      <div class="project-title">TRB Motif-Based Survival Analysis</div>
      <div class="project-desc">Built a pipeline to mine immune receptor motifs from BAM files and link them to survival outcomes in cancer.</div>
      <div class="project-links">
        <i class="fab fa-github"></i>
        <span>Blog: Coming Soon</span>
      </div>
    </div>
  </a>

</div>
