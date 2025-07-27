---
layout: page
title: Projects
icon: fas fa-flask
permalink: /projects/
order: 3
---

<!-- 🧬 Project 1 -->
<div class="project-entry enhanced" onclick="toggleProjectDetails(this)">
  <div class="project-thumb">
    <img src="/assets/img/snrna-04-07-2025/anotated_umap.png" alt="Project 1 Thumbnail" />
  </div>
  <div class="project-info">
    <div class="project-title">🧬 Tumor vs Normal CDR3 Classifier</div>
    <p class="project-subtitle">LSTM-based classification from TCR β-chain sequences</p>
    <div class="project-details">
      <p>This deep learning project predicts tumor vs normal tissue from TCR repertoires using LSTM. It’s containerized with Docker and pipeline-managed with Nextflow for full reproducibility.</p>
      <p><strong>Tech Stack:</strong>
        <span class="badge">PyTorch</span>
        <span class="badge">Nextflow</span>
        <span class="badge">Docker</span>
        <span class="badge">JSONL</span>
      </p>
      <div class="project-links">
        <a href="https://github.com/yourusername/project1" class="project-btn" target="_blank">🔗 View on GitHub</a>
        <a href="/projects/project1-blog" class="project-btn" target="_blank">📝 Read Full Blog</a>
      </div>
    </div>
  </div>
</div>

<!-- 🔬 Project 2 -->
<div class="project-entry enhanced" onclick="toggleProjectDetails(this)">
  <div class="project-thumb">
    <img src="/assets/img/snrna-04-07-2025/DE_volcano_tumor_PDX.png" alt="Project 2 Thumbnail" />
  </div>
  <div class="project-info">
    <div class="project-title">🔬 Single-Nucleus RNA-seq of Hepatoblastoma</div>
    <p class="project-subtitle">Cluster annotation, DEG analysis, and Nextflow pipeline</p>
    <div class="project-details">
      <p>This single-nucleus RNA-seq project explores cell-type diversity in hepatoblastoma tumors using Seurat and Harmony, supported by a fully modular and Dockerized Nextflow workflow.</p>
      <p><strong>Tech Stack:</strong>
        <span class="badge">Seurat</span>
        <span class="badge">R</span>
        <span class="badge">Nextflow</span>
        <span class="badge">Docker</span>
      </p>
      <div class="project-links">
        <a href="https://github.com/yourusername/project2" class="project-btn" target="_blank">🔗 View on GitHub</a>
        <a href="/projects/project2-blog" class="project-btn" target="_blank">📝 Read Full Blog</a>
      </div>
    </div>
  </div>
</div>

<!-- 💅 STYLES -->
<style>
.project-entry.enhanced {
  display: flex;
  flex-direction: column;
  background: #1f1f1f;
  margin: 2rem 0;
  border-radius: 18px;
  overflow: hidden;
  box-shadow: 0 0 12px rgba(0, 255, 255, 0.08);
  transition: transform 0.3s ease, max-height 0.5s ease;
  cursor: pointer;
  max-height: 200px;
  color: #ffffff;
}

.project-entry:hover {
  transform: scale(1.01);
  box-shadow: 0 0 20px rgba(0, 255, 255, 0.3);
}

.project-thumb img {
  width: 100%;
  height: auto;
  max-height: 200px;
  object-fit: cover;
  border-bottom: 2px solid #00f2ff;
}

.project-info {
  padding: 1.2rem 1.5rem;
}

.project-title {
  font-size: 1.3rem;
  font-weight: 700;
  color: #00f2ff;
}

.project-subtitle {
  font-size: 1rem;
  opacity: 0.8;
}

.project-details {
  margin-top: 1rem;
  display: none;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.project-entry.expanded {
  max-height: 900px;
  background: #292929;
}

.project-entry.expanded .project-details {
  display: block;
  opacity: 1;
}

.badge {
  background-color: #00f2ff;
  color: #000;
  padding: 0.2em 0.6em;
  border-radius: 12px;
  font-size: 0.75rem;
  margin-right: 0.5em;
}

.project-links {
  margin-top: 1rem;
}

.project-btn {
  display: inline-block;
  margin-right: 0.8rem;
  padding: 0.5em 1em;
  border-radius: 8px;
  background: #00f2ff;
  color: #000;
  text-decoration: none;
  font-weight: 600;
  transition: background 0.3s ease;
}

.project-btn:hover {
  background: #ffffff;
}
</style>

<!-- 📜 SCRIPT -->
<script>
function toggleProjectDetails(card) {
  card.classList.toggle("expanded");
}
</script>
