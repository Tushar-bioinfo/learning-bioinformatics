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
<p class="meta"><strong>Duration:</strong> Jul 2025 &nbsp;|&nbsp; <strong>Tags:</strong> Nextflow, SRA, BAM, Immune Receptors, HPC</p>

<h2>Summary</h2>
<p>
This modular Nextflow pipeline automates immune receptor region extraction from public sequencing datasets. It processes SRA accessions end-to-end: from FASTQ conversion and genome alignment to BAM slicing and cleanup — enabling high-throughput analysis of TCR/BCR regions for immunogenomic studies.
</p>

<h2>Project Highlights</h2>
<ul>
  <li>Designed a fully modular <strong>Nextflow DSL2 pipeline</strong> to convert SRA data to immune receptor-specific BAM files.</li>
  <li>Integrated <code>prefetch</code>, <code>fasterq-dump</code>, and <code>STAR</code>/<code>bwa mem</code> aligners.</li>
  <li>Used <strong>SAMtools</strong> to extract genomic regions corresponding to TRA, TRB, IGH, IGK, and IGL loci.</li>
  <li>Included automatic sorting, indexing, and optional deletion of intermediate files for space efficiency.</li>
  <li>Built for reproducibility and HPC execution with <strong>SLURM</strong> support, <strong>containerization</strong>, and configurable profiles.</li>
</ul>

<h2> </h2>
<div class="project-tags">
  <span class="project-tag">Nextflow</span>
  <span class="project-tag">SRA Toolkit</span>
  <span class="project-tag">STAR</span>
  <span class="project-tag">bwa mem</span>
  <span class="project-tag">SAMtools</span>
  <span class="project-tag">HPC</span>
  <span class="project-tag">Immune Receptors</span>
</div>

<h2> </h2>
<div class="project-links">
  <a href="https://github.com/yourusername/immune-receptor-nextflow" target="_blank" rel="noopener noreferrer">
    <i class="fab fa-github"></i>GitHub
  </a>
  <a href="/blog/2025/07/28/nextflow-immune-receptor-pipeline.html" target="_blank" rel="noopener noreferrer">
    <i class="fas fa-book-open"></i>Blog
  </a>
</div>

</div>
