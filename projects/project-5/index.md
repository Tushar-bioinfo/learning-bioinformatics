---
layout: page
title: 
permalink: /projects/project-5/
icon: fas fa-code-branch
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

  <h1>SRA to BAM: Immune Receptor Extraction Pipeline</h1>

  <h2>Summary</h2>
  <p>
    This modular <code>Nextflow</code> pipeline automates extraction of immune receptor regions (TCR/BCR) from public sequencing datasets. It processes SRA accessions end-to-end: FASTQ conversion, genome alignment, BAM slicing, and cleanup — enabling scalable, reproducible immunogenomic studies.
  </p>

  <h2>What I Did</h2>
  <ul>
    <li>Developed a robust <strong>Nextflow DSL2 pipeline</strong> to convert raw SRA reads into receptor-specific BAMs.</li>
    <li>Integrated <code>prefetch</code>, <code>fasterq-dump</code>, and <code>STAR</code> or <code>bwa mem</code> for alignment.</li>
    <li>Used <strong>SAMtools</strong> to extract TRA, TRB, IGH, IGK, and IGL regions from aligned BAMs.</li>
    <li>Implemented automatic sorting, indexing, and optional cleanup to optimize storage and runtime.</li>
    <li>Designed for reproducibility with <strong>SLURM</strong> HPC support, containerization, and flexible config profiles.</li>
  </ul>

  <div class="project-tags">
    <span class="project-tag">Nextflow</span>
    <span class="project-tag">SRA Toolkit</span>
    <span class="project-tag">STAR</span>
    <span class="project-tag">bwa mem</span>
    <span class="project-tag">SAMtools</span>
    <span class="project-tag">HPC</span>
    <span class="project-tag">SLURM</span>
    <span class="project-tag">Conda</span>
  </div>

  <div class="project-links" style="margin-top: 1rem; display: flex; gap: 1rem;">
    <a href="https://github.com/yourusername/immune-receptor-nextflow" target="_blank" style="text-decoration: none; color: #00f2ff;">
      <i class="fab fa-github"></i> GitHub
    </a>
    <a href="/blog/2025/07/28/nextflow-immune-receptor-pipeline.html" target="_blank" style="text-decoration: none; color: #00f2ff;">
      <i class="fas fa-book-open"></i> Blog
    </a>
  </div>

</div>
