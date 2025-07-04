---
layout: page
title: My Links
icon: fas fa-link
permalink: /links/
---

<style>
.tree-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 2rem;
}

.tree-branch {
  background-color: #1f1f1f;
  border-left: 4px solid #56cc9d;
  padding: 1rem 1.5rem;
  margin: 0.75rem 0;
  width: 80%;
  border-radius: 8px;
  position: relative;
  transition: 0.3s ease;
}

.tree-branch::before {
  content: "🌿";
  position: absolute;
  left: -1.8rem;
  top: 50%;
  transform: translateY(-50%);
}

.tree-branch:hover {
  background-color: #263238;
  border-left-color: #00f2ff;
  transform: scale(1.02);
}

.tree-branch a {
  text-decoration: none;
  color: #00f2ff;
  font-weight: 600;
  font-size: 1.1rem;
}
</style>

<div class="tree-container">
  <div class="tree-branch">
    <a href="https://tushar-bioinfo.github.io/learning-bioinformatics/" target="_blank">
      Blog: Learning Bioinformatics
    </a>
  </div>
  <div class="tree-branch">
    <a href="https://github.com/Tushar-bioinfo" target="_blank">
      GitHub: @Tushar-bioinfo
    </a>
  </div>
  <div class="tree-branch">
    <a href="https://linkedin.com/in/tussi147" target="_blank">
      LinkedIn: tussi147
    </a>
  </div>
  <div class="tree-branch">
    <a href="mailto:tushar14032001@gmail.com">
      Email: tushar14032001@gmail.com
    </a>
  </div>
</div>
