---
layout: page
title: My Links
icon: fas fa-link
permalink: /links/
---

<style>
.tree-svg-container {
  display: flex;
  justify-content: center;
  margin-top: 2rem;
}

.tree-link {
  fill: #00f2ff;
  cursor: pointer;
  font-family: 'Courier New', monospace;
  font-size: 14px;
  transition: all 0.3s ease;
}

.tree-link:hover {
  fill: #56cc9d;
}

.tree-line {
  stroke: #1e88e5;
  stroke-width: 2;
}
</style>

<div class="tree-svg-container">
  <svg width="600" height="500" viewBox="0 0 600 500">
    <!-- Trunk -->
    <line x1="300" y1="20" x2="300" y2="130" class="tree-line" />

    <!-- Branches -->
    <line x1="300" y1="130" x2="150" y2="230" class="tree-line" />
    <line x1="300" y1="130" x2="450" y2="230" class="tree-line" />
    <line x1="150" y1="230" x2="100" y2="330" class="tree-line" />
    <line x1="450" y1="230" x2="500" y2="330" class="tree-line" />

    <!-- Links as nodes -->
    <a href="https://tushar-bioinfo.github.io/learning-bioinformatics/" target="_blank">
      <text x="140" y="235" class="tree-link">Blog</text>
    </a>

    <a href="https://github.com/Tushar-bioinfo" target="_blank">
      <text x="90" y="335" class="tree-link">GitHub</text>
    </a>

    <a href="https://linkedin.com/in/tussi147" target="_blank">
      <text x="460" y="235" class="tree-link">LinkedIn</text>
    </a>

    <a href="mailto:tushar14032001@gmail.com">
      <text x="510" y="335" class="tree-link">Email</text>
    </a>

    <!-- Root label -->
    <text x="285" y="15" fill="#00e5ff" font-size="16" font-weight="bold">Bioinformaniac 🌱</text>
  </svg>
</div>
