---
layout: page
title: Projects
icon: fas fa-flask
permalink: /projects/
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
  text-decoration: none;
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

.project-desc {
  color: #ccc;
  margin-bottom: 0.8rem;
  font-size: 1rem;
}

.project-tags {
  margin: 0.6rem 0 1rem 0;
  display: flex;
  flex-wrap: wrap;
  gap: 0.6rem;
}

.project-tags span {
  background: #263238;
  color: #00f2ff;
  padding: 0.3rem 0.75rem;
  font-size: 0.8rem;
  border-radius: 10px;
}

.project-links a {
  color: #56cc9d;
  font-size: 1.6rem;
  margin-right: 1.2rem;
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

<!-- Project 1 -->
<a class="project-entry" href="/learning-bioinformatics/projects/boston-house/">
  <div class="project-info">
    <div class="project-title">Boston House Price Prediction</div>
    <div class="project-desc">A regression-based ML project exploring BIC, RMSE, and housing feature impacts.</div>
    <div class="project-tags">
      <span>regression</span><span>sklearn</span><span>housing</span>
    </div>
    <div class="project-links">
      <a href="https://github.com/your-username/boston-house" title="GitHub (coming soon)" target="_blank"><i class="fab fa-github"></i></a>
      <a href="/learning-bioinformatics/projects/boston-house/" title="Blog or Description Page"><i class="fas fa-blog"></i></a>
    </div>
  </div>
  <img class="project-thumb" src="/learning-bioinformatics/assets/img/project-thumbs/boston.png" alt="Boston Housing">
</a>

<!-- Project 2 -->
<a class="project-entry" href="/learning-bioinformatics/projects/trb-survival/">
  <div class="project-info">
    <div class="project-title">TRB Motif-Based Survival Analysis</div>
    <div class="project-desc">Built a pipeline to extract immune receptor motifs from BAM files and link them to cancer survival outcomes.</div>
    <div class="project-tags">
      <span>immunogenomics</span><span>cancer</span><span>python</span>
    </div>
    <div class="project-links">
      <a href="https://github.com/your-username/trb-survival" title="GitHub (coming soon)" target="_blank"><i class="fab fa-github"></i></a>
      <a href="/learning-bioinformatics/projects/trb-survival/" title="Blog or Description Page"><i class="fas fa-blog"></i></a>
    </div>
  </div>
  <img class="project-thumb" src="/learning-bioinformatics/assets/img/project-thumbs/unannotated_clusters.png" alt="TRB Motif Analysis">
</a>
