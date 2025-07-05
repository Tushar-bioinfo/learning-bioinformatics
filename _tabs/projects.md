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
  position: relative;
}

.project-card:hover {
  transform: scale(1.03);
  box-shadow: 0 0 20px rgba(0, 255, 255, 0.3);
}

.project-image {
  width: 100%;
  height: 200px;
  object-fit: cover;
  border-bottom: 1px solid #333;
}

.project-content {
  padding: 1rem 1.2rem;
  flex-grow: 1;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
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
  font-size: 1.3rem;
  margin-top: 0.6rem;
}

.project-links a {
  color: #56cc9d;
  transition: color 0.2s ease, transform 0.2s ease;
}

.project-links a:hover {
  color: #00f2ff;
  transform: scale(1.2);
}

.project-tags {
  margin-top: 0.8rem;
  display: flex;
  gap: 0.5rem;
  flex-wrap: wrap;
}

.project-tags span {
  background: #263238;
  color: #00f2ff;
  padding: 0.2rem 0.6rem;
  border-radius: 10px;
  font-size: 0.8rem;
}
</style>

<div class="project-grid">

  <!-- Project 1: Boston -->
  <a href="/learning-bioinformatics/projects/boston-house/" class="project-card">
    <img class="project-image" src="/assets/img/project-thumbs/boston.png" alt="Boston Housing">
    <div class="project-content">
      <div>
        <div class="project-title">Boston House Price Prediction</div>
        <div class="project-desc">A regression-based ML project exploring BIC, RMSE, and housing feature impacts.</div>
        <div class="project-tags">
          <span>regression</span><span>sklearn</span><span>housing</span>
        </div>
      </div>
      <div class="project-links">
        <a href="#" title="GitHub (coming soon)"><i class="fab fa-github"></i></a>
        <a href="#" title="Blog (coming soon)"><i class="fas fa-blog"></i></a>
      </div>
    </div>
  </a>

  <!-- Project 2: TRB Motif -->
  <a href="/learning-bioinformatics/projects/trb-survival/" class="project-card">
    <img class="project-image" src="/assets/img/project-thumbs/unannotated_clusters.png" alt="TRB Motif">
    <div class="project-content">
      <div>
        <div class="project-title">TRB Motif-Based Survival Analysis</div>
        <div class="project-desc">Built a pipeline to mine immune receptor motifs from BAM files and link them to survival outcomes in cancer.</div>
        <div class="project-tags">
          <span>immunogenomics</span><span>cancer</span><span>python</span>
        </div>
      </div>
      <div class="project-links">
        <a href="#" title="GitHub (coming soon)"><i class="fab fa-github"></i></a>
        <a href="#" title="Blog (coming soon)"><i class="fas fa-blog"></i></a>
      </div>
    </div>
  </a>

</div>
