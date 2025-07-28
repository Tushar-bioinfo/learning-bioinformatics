---
layout: page
title: 
permalink: /projects/project-2/
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

<h1>Single-nucleus RNA-Seq of Hepatoblastoma Tumors</h1>

<h2>Summary</h2>
<p>
This project analyzes the single-nucleus transcriptomic landscape of hepatoblastoma tumors and matched PDX models. Using <code>Seurat</code> and <code>Harmony</code>, we performed batch correction, dimensionality reduction, and unsupervised clustering to dissect tumor heterogeneity and microenvironmental structure.
</p>

<h2>What I Did</h2>
<ul>
  <li>Developed a fully Dockerized snRNA-seq pipeline using <strong>Seurat</strong> and <strong>Harmony</strong> for batch correction and UMAP visualization.</li>
  <li>Annotated over <strong>10 cell clusters</strong> using marker gene expression profiles and GeneCards cross-referencing.</li>
  <li>Identified tumor subtypes and microenvironmental components including stromal and immune populations.</li>
  <li>Performed <strong>differential expression analysis</strong> between tumor and PDX nuclei in fetal-like clusters, revealing immune and stress-related signatures.</li>
</ul>

<h2> </h2>
<div class="project-tags">
  <span class="project-tag">R</span>
  <span class="project-tag">Seurat</span>
  <span class="project-tag">Harmony</span>
  <span class="project-tag">PCA</span>
  <span class="project-tag">UMAP</span>
  <span class="project-tag">Differential Expression</span>
  <span class="project-tag">Docker</span>
</div>

<h2> </h2>
<div class="project-links">
  <a href="https://github.com/Tushar-bioinfo/ScRNAseq-Hepatoblastoma" target="_blank">
    <i class="fab fa-github"></i>GitHub
  </a>
  <a href="https://tushar-bioinfo.github.io/learning-bioinformatics/posts/Single-Nucleus-RNA-seq/" target="_blank">
    <i class="fas fa-book-open"></i>Blog
  </a>
</div>

</div>

