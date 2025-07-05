---
layout: page
title: Projects
icon: fas fa-flask
permalink: /projects/
---

<style>
.project-grid {
  display: flex;
  flex-direction: column;
  gap: 2rem;
  margin-top: 2rem;
}

.project-entry {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #1f1f1f;
  border-radius: 16px;
  padding: 1.8rem 2rem;
  box-shadow: 0 0 12px rgba(0, 255, 255, 0.08);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  text-decoration: none;
}

.project-entry:hover {
  transform: scale(1.01);
  box-shadow: 0 0 20px rgba(0, 255, 255, 0.25);
}

.project-info {
  flex: 1;
  padding-right: 1.8rem;
}

.project-title {
  font-size: 1.4rem;
  font-weight: bold;
  color: #00f2ff;
  margin-bottom: 0.4rem;
}

.project-desc {
  color: #ccc;
  margin-bottom: 0.9rem;
  font-size: 1rem;
}

.project-tags {
  display: flex;
  gap: 0.6rem;
  margin-bottom: 1rem;
  flex-wrap: wrap;
}

.project-tags span {
  background-color: #263238;
  color: #00f2ff;
  padding: 0.3rem 0.75rem;
  border-radius: 10px;
  font-size: 0.8rem;
}

.project-links {
  display: flex;
  gap: 1.6rem;
  align-items: center;
}

.project-links a {
  font-size: 1.8rem;
  color: #56cc9d;
  transition: 0.2s ease;
}

.project-links a:hover {
  color: #00f2ff;
  transform: scale(1.2);
}

.project-thumb {
  width: 280px;
  height: auto;
  border-radius: 12px;
  object-fit: cover;
  border: 2px solid #2c2c2c;
}
</style>

<div class="project-grid">

  <!-- Project 1 -->
  <a href="/projects/boston-house/" class="project-entry">
    <div class="project-info">
      <div class="project-title">Boston House Price Prediction</div>
      <div class="project-desc">A regression-based ML project exploring BIC, RMSE, and housing feature impacts.</div>
      <div class="project-tags">
        <span>regression</span>
        <span>sklearn</span>
        <span>housing</span>
      </div>
      <div class="project-links">
        <a href="#" title="GitHub (coming soon)"><i class="fab fa-github"></i></a>
        <a href="#" title="Blog (coming soon)"><i class="fas fa-blog"></i></a>
      </div>
    </div>
    <img class="project-thumb" src="/assets/img/project-thumbs/boston.png" alt="Boston Housing">
  </a>

  <!-- Project 2 -->
  <a href="/projects/trb-survival/" class="project-entry">
    <div class="project-info">
      <div class="project-title">TRB Motif-Based Survival Analysis</div>
      <div class="project-desc">Pipeline to extract immune receptor motifs from BAM files and link to cancer survival.</div>
      <div class="project-tags">
        <span>immunogenomics</span>
        <span>cancer</span>
        <span>python</span>
      </div>
      <div class="project-links">
        <a href="#" title="GitHub (coming soon)"><i class="fab fa-github"></i></a>
        <a href="#" title="Blog (coming soon)"><i class="fas fa-blog"></i></a>
      </div>
    </div>
    <img class="project-thumb" src="/assets/img/project-thumbs/unannotated_clusters.png" alt="TRB Analysis">
  </a>

</div>
