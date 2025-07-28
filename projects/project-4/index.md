---
layout: page
title: 
permalink: /projects/project-4/
icon: fas fa-vial
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

<h1>Structural Disorder Analysis of Immune Receptor CDR3 Regions</h1>

<h2>Summary</h2>
<p>
This project explores the structural flexibility of TCR and BCR CDR3 regions by predicting their intrinsic disorder levels using <code>metapredict</code>. A custom pipeline was built to extract immune receptor sequences from cancer patient BAM files, perform disorder analysis, and compare CDR3 vs V and J segment regions to investigate their biophysical uniqueness.
</p>

<h2>What I Did</h2>
<ul>
  <li>Built a bioinformatics pipeline to extract CDR3 sequences from GDC-aligned BAM files using custom VDJ mining scripts and <code>SAMtools</code>.</li>
  <li>Validated extracted sequences using <code>VDJdb</code> and processed datasets in R and Python.</li>
  <li>Applied <strong>metapredict</strong> to predict per-residue disorder scores across CDR3, V, and J regions.</li>
  <li>Quantified and visualized disorder trends, showing CDR3 regions are moderately disordered but less so than their flanking domains.</li>
  <li>Suggested potential links between disorder levels and antigen-binding flexibility in immune response.</li>
</ul>

<h2> </h2>
<div class="project-tags">
  <span class="project-tag">metapredict</span>
  <span class="project-tag">SAMtools</span>
  <span class="project-tag">GDC Data Transfer Tool</span>
  <span class="project-tag">HPC</span>
  <span class="project-tag">Matplotlib</span>
</div>

<h2> </h2>
<div class="project-links">
  <a href="https://github.com/Tushar-bioinfo/CDR3-Intrinsic-Disorder" target="_blank">
    <i class="fab fa-github"></i> View Code on GitHub
  </a>
</div>

</div>
