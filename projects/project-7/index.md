---
layout: page
title: 
permalink: /projects/project-cnv-gatk4/
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

<h1>GATK4 CNV Analysis in Glioblastoma</h1>

<h2>Summary</h2>
<p>
Built an end-to-end, HPC-optimized copy number variation (CNV) pipeline for dbGaP-protected cancer RNA-seq data using GATK4 CNV, automating SRA-to-BAM processing and genome-wide CNV calling across large patient cohorts on the USF RRA cluster.
</p>

<h2>Project Highlights</h2>
<ul>
  <li>Designed a secure, large-scale workflow to convert SRA accessions to aligned, sorted BAM files (SRA → FASTQ → BAM) using <strong>Slurm arrays</strong>, <strong>fasterq-dump</strong>, <strong>BWA-mem2</strong>, and <strong>samtools</strong>.</li>
  <li>Parallelized FASTQ extraction and alignment on scratch storage with timeout handling, enabling stable processing of <strong>thousands of samples</strong> without manual restarts.</li>
  <li>Constructed autosome-wide interval lists and a robust <strong>Panel of Normals</strong> from normal cohorts using GATK <strong>CreateReadCountPanelOfNormals</strong> to reduce technical noise in copy-ratio estimates.</li>
  <li>Automated CNV calling with GATK <strong>CollectReadCounts → DenoiseReadCounts → ModelSegments</strong>, generating standardized copy-ratio tracks and high-resolution CNV segments for each tumor sample.</li>
  <li>Implemented Python-based post-processing to map CNV segments to genes and assemble cohort-level gene-by-sample CNV matrices ready for survival analysis, immune feature integration, and downstream ML.</li>
</ul>

<h2></h2>
<div class="project-tags">
  <span class="project-tag">GATK4 CNV</span>
  <span class="project-tag">CNV Analysis</span>
  <span class="project-tag">RNA-Seq</span>
  <span class="project-tag">HPC</span>
  <span class="project-tag">Slurm</span>
  <span class="project-tag">BWA-mem2</span>
  <span class="project-tag">samtools</span>
  <span class="project-tag">Bash</span>
  <span class="project-tag">Python</span>
  <span class="project-tag">dbGaP</span>
</div>

<h2></h2>
<div class="project-links">
  <a href="https://github.com/Tushar-bioinfo/gatk-CNV" target="_blank" rel="noopener noreferrer">
    <i class="fab fa-github"></i>GitHub
  </a>
  <a href="#" target="_blank" rel="noopener noreferrer">
    <i class="fas fa-book-open"></i>Blog (coming soon)
  </a>
</div>

