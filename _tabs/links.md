---
layout: page
title: My Links
icon: fas fa-link
permalink: /links/
---

<!-- Tree-style link page with Font Awesome icons and hover effects -->
<style>
.tree-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 3rem;
}

.tree-branch {
  background-color: #1f1f1f;
  border-left: 5px solid #56cc9d;
  padding: 1rem 2rem;
  margin: 1rem 0;
  width: 85%;
  border-radius: 10px;
  position: relative;
  transition: all 0.3s ease;
  box-shadow: 0 4px 12px rgba(0, 255, 255, 0.05);
}

.tree-branch:hover {
  background-color: #263238;
  border-left-color: #00f2ff;
  transform: scale(1.015);
  box-shadow: 0 0 12px rgba(0, 255, 255, 0.3);
}

.tree-branch a {
  display: flex;
  align-items: center;
  text-decoration: none;
  color: #00f2ff;
  font-weight: 600;
  font-size: 1.1rem;
}

.tree-branch i {
  font-size: 1.4rem;
  margin-right: 1rem;
  color: #56cc9d;
  transition: color 0.3s ease;
}

.tree-branch:hover i {
  color: #00f2ff;
}
</style>

<div class="tree-container">
  <div class="tree-branch">
    <a href="https://tushar-bioinfo.github.io/learning-bioinformatics/" target="_blank">
      <i class="fas fa-blog"></i> Blog: Learning Bioinformatics
    </a>
  </div>
  <div class="tree-branch">
    <a href="https://github.com/Tushar-bioinfo" target="_blank">
      <i class="fab fa-github"></i> GitHub: @Tushar-bioinfo
    </a>
  </div>
  <div class="tree-branch">
    <a href="https://linkedin.com/in/tussi147" target="_blank">
      <i class="fab fa-linkedin"></i> LinkedIn: tussi147
    </a>
  </div>
  <div class="tree-branch">
    <a href="mailto:tushar14032001@gmail.com">
      <i class="fas fa-envelope"></i> Email: tushar14032001@gmail.com
    </a>
  </div>
</div>
