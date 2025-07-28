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

  <h1>Intrinsic Disorder Analysis of Immune Receptor CDR3 Regions</h1>

  <h2>Summary</h2>
  <p>
    This project investigates the structural flexibility of TCR and BCR CDR3 regions by predicting their intrinsic disorder using <code>metapredict</code>. I built a custom pipeline to extract receptor sequences from cancer patient BAM files, run disorder analysis, and compare CDR3 segments to V and J regions to highlight unique biophysical properties.
  </p>

  <h2>What I Did</h2>
  <ul>
    <li>Developed a bioinformatics pipeline to extract CDR3 sequences from GDC-aligned BAM files using custom VDJ mining scripts and <code>SAMtools</code>.</li>
    <li>Validated extracted repertoires with <code>VDJdb</code> and processed data using R and Python.</li>
    <li>Applied <strong>metapredict</strong> to generate per-residue disorder profiles for CDR3, V, and J segments.</li>
    <li>Visualized disorder scores to show CDR3s are moderately disordered but less so than flanking regions.</li>
    <li>Explored implications for antigen-binding flexibility and immune recognition.</li>
  </ul>

  <div class="project-tags">
    <span class="project-tag">Intrinsic Disorder</span>
    <span class="project-tag">metapredict</span>
    <span class="project-tag">SAMtools</span>
    <span class="project-tag">VDJdb</span>
    <span class="project-tag">HPC</span>
    <span class="project-tag">R</span>
    <span class="project-tag">Python</span>
    <span class="project-tag">Matplotlib</span>
  </div>

  <div class="project-links" style="margin-top: 1rem; display: flex; gap: 1rem;">
    <a href="https://github.com/Tushar-bioinfo/CDR3-Intrinsic-Disorder" target="_blank" style="text-decoration: none; color: #00f2ff;">
      <i class="fab fa-github"></i> GitHub
    </a>
  </div>

</div>
