---
layout: page
title: Tumor Severity Prediction from RNA-Seq
permalink: /projects/project-tumor-severity/
icon: fas fa-dna
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

<h1>Tumor Severity Prediction from RNA-Seq</h1>
<p class="meta"><strong>Duration:</strong> Aug 2025 &nbsp;|&nbsp; <strong>Tags:</strong> RNA-Seq, ML, Deep Learning, Docker, TCGA-LUAD</p>

<h2>Summary</h2>
<p>
Designed and implemented a machine learning and deep learning pipeline to classify tumor severity in lung adenocarcinoma based on TCGA-LUAD RNA-seq data, stratifying patients as “severe” (stage >1) or “non-severe” (stage 1) using clinical metadata.
</p>

<h2>Project Highlights</h2>
<ul>
  <li>Developed an end-to-end ML/DL workflow that automates tumor severity prediction directly from RNA-seq profiles.</li>
  <li>Improved model interpretability and performance by systematically evaluating ANOVA-selected gene subsets across classifiers.</li>
  <li>Increased predictive performance by 21% through deep learning optimization, achieving best results using a CNN model.</li>
  <li>Accelerated hyperparameter tuning by integrating <strong>Optuna</strong> with Keras, streamlining CNN optimization workflows.</li>
  <li>Enhanced reproducibility and future scalability with Docker containerization and a modular <strong>Nextflow</strong> pipeline for HPC use.</li>
</ul>


<h2></h2>
<div class="project-tags">
  <span class="project-tag">Keras</span>
  <span class="project-tag">Machine Learning</span>
  <span class="project-tag">CNN</span>
  <span class="project-tag">RNA-Seq</span>
  <span class="project-tag">Optuna</span>
  <span class="project-tag">Docker</span>
  <span class="project-tag">Nextflow</span>
</div>

<h2></h2>
<div class="project-links">
  <a href="https://github.com/yourusername/tumor-severity-ml" target="_blank" rel="noopener noreferrer">
    <i class="fab fa-github"></i>GitHub
  </a>
  <a href="/blog/2025/08/06/tumor-severity-prediction-rnaseq.html" target="_blank" rel="noopener noreferrer">
    <i class="fas fa-book-open"></i>Blog
  </a>
</div>

</div>
