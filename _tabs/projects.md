---
layout: page
title: Projects
icon: fas fa-flask
permalink: /projects/
order: 3
---

<div class="project-entry" onclick="toggleProjectDetails(this)" style="background: #212121; border-left: 5px solid #00f2ff;">
  <div class="project-info">
    <div class="project-title">Tumor vs Normal CDR3 Classifier</div>
    <p class="project-subtitle">LSTM-based classification from TCR β-chain sequences</p>
    <div class="project-details">
      <p>This deep learning project predicts tumor vs normal tissue from TCR repertoires using LSTM. It’s containerized with Docker and pipeline-managed with Nextflow for full reproducibility.</p>
      <p><strong>Tech Stack:</strong> <span class="badge">PyTorch</span> <span class="badge">Nextflow</span> <span class="badge">Docker</span> <span class="badge">JSONL</span></p>
      <a href="https://github.com/yourusername/yourproject" target="_blank">🔗 View on GitHub</a>
    </div>
  </div>
</div>

<div class="project-entry" onclick="toggleProjectDetails(this)" style="background: #212121; border-left: 5px solid #00f2ff;">
  <div class="project-info">
    <div class="project-title">Tumor vs Normal CDR3 Classifier</div>
    <p class="project-subtitle">LSTM-based classification from TCR β-chain sequences</p>
    <div class="project-details">
      <p>This deep learning project predicts tumor vs normal tissue from TCR repertoires using LSTM. It’s containerized with Docker and pipeline-managed with Nextflow for full reproducibility.</p>
      <p><strong>Tech Stack:</strong> <span class="badge">PyTorch</span> <span class="badge">Nextflow</span> <span class="badge">Docker</span> <span class="badge">JSONL</span></p>
      <a href="https://github.com/yourusername/project1" target="_blank">🔗 View on GitHub</a>
    </div>
  </div>
</div>

<div class="project-entry" onclick="toggleProjectDetails(this)" style="background: #212121; border-left: 5px solid #ff4da6;">
  <div class="project-info">
    <div class="project-title">Single-Nucleus RNA-seq of Hepatoblastoma</div>
    <p class="project-subtitle">Cluster annotation, DEG analysis, and Nextflow pipeline</p>
    <div class="project-details">
      <p>This single-nucleus RNA-seq project analyzes tumor heterogeneity in hepatoblastoma using Seurat and Harmony. It includes custom scripts for cell type annotation and differential expression.</p>
      <p><strong>Tech Stack:</strong> <span class="badge">Seurat</span> <span class="badge">Nextflow</span> <span class="badge">Docker</span> <span class="badge">R</span></p>
      <a href="https://github.com/yourusername/project2" target="_blank">🔗 View on GitHub</a>
    </div>
  </div>
</div>


<style>
.project-entry {
  display: flex;
  flex-direction: column;
  background: #1f1f1f;
  margin: 2rem 0;
  padding: 1.5rem 2rem;
  border-radius: 18px;
  box-shadow: 0 0 12px rgba(0, 255, 255, 0.08);
  transition: transform 0.3s ease, max-height 0.5s ease;
  cursor: pointer;
  overflow: hidden;
  max-height: 160px;
  color: #ffffff;
}

.project-entry:hover {
  transform: scale(1.01);
  box-shadow: 0 0 20px rgba(0, 255, 255, 0.3);
}

.project-title {
  font-size: 1.4rem;
  font-weight: bold;
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
  max-height: 600px;
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
</style>

<script>
function toggleProjectDetails(card) {
  card.classList.toggle("expanded");
}
</script>

