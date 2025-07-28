---
layout: page
title: Tumor vs Normal TCR Classification 
permalink: /projects/project-3/
icon: fas fa-brain
---

<style>
.project-container {
  background: #1f1f1f;
  padding: 2rem 2.5rem;
  border-radius: 20px;
  box-shadow: 0 0 20px rgba(0, 255, 255, 0.05);
  margin-top: 2rem;
  color: #eaeaea;
  line-height: 1.75;
}

.project-container h1 {
  color: #00f2ff;
  font-size: 2rem;
  margin-bottom: 0.3rem;
}

.project-container .meta {
  font-size: 0.9rem;
  color: #999;
  margin-bottom: 1.5rem;
}

.project-container h2 {
  font-size: 1.4rem;
  margin-top: 2rem;
  color: #00f2ff;
}

.project-container ul {
  margin-top: 1rem;
  padding-left: 1.2rem;
}

.project-container li {
  margin-bottom: 0.7rem;
}

.project-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin: 0.5rem 0 2rem;
}

.project-tag {
  background: #101010;
  color: #ccc;
  border: 1px solid #333;
  padding: 0.3rem 0.7rem;
  font-size: 0.8rem;
  border-radius: 12px;
  font-family: monospace;
}

.project-links {
  margin-top: 2.5rem;
  display: flex;
  gap: 1.2rem;
  flex-wrap: wrap;
}

.project-links a {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  background: #2c2c2c;
  color: #00f2ff;
  padding: 0.6rem 1.2rem;
  border-radius: 12px;
  font-weight: 500;
  text-decoration: none;
  transition: background 0.3s ease;
}

.project-links a:hover {
  background: #00f2ff;
  color: #000;
}

.project-links i {
  font-size: 1rem;
}
</style>

<div class="project-container">

<h1>Tumor vs Normal TCR Classification</h1>


<h2>Summary</h2>
<p>
This project uses deep learning to classify tumor vs normal immune repertoires using TRB CDR3 sequences from lung cancer patients in the CPTAC dataset. The pipeline includes preprocessing, sequence modeling, and interpretability — with modular code structured for reproducibility.
</p>

<h2>What I Did</h2>
<ul>
  <li>Developed a deep learning pipeline to classify tumor vs normal tissue using patient-level TRB CDR3 repertoires.</li>
  <li>Processed and tokenized variable-length CDR3 sequences with <strong>padding and mean-pooling</strong> strategies.</li>
  <li>Built and compared <strong>mean pooling</strong> and <strong>LSTM</strong>-based architectures in PyTorch.</li>
  <li>Evaluated models with <strong>ROC AUC</strong>, <strong>F1-score</strong>, and <strong>confusion matrices</strong>.</li>
  <li>Structured the code with modular, reproducible design following <strong>Nextflow-inspired principles</strong>.</li>
</ul>

<h2> </h2>
<div class="project-tags">
  <span class="project-tag">Deep Learning</span>
  <span class="project-tag">LSTM</span>
  <span class="project-tag">PyTorch</span>
  <span class="project-tag">Mean Pooling</span>
  <span class="project-tag">Tokenization</span>
</div>

<h2> </h2>
<div class="project-links">
  <a href="https://github.com/Tushar-bioinfo/DL-TCR-TRB-CDR3-Classification" target="_blank">
    <i class="fab fa-github"></i> View Code on GitHub
  </a>
  <a href="https://tushar-bioinfo.github.io/learning-bioinformatics/posts/TRB-CDR3-DL/" target="_blank">
    <i class="fas fa-book-open"></i> Read Blog Post
  </a>
</div>

</div>
