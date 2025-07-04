---
layout: page
title: My Links
icon: fas fa-link
permalink: /links/
---

<style>
.icon-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
  gap: 2rem;
  justify-items: center;
  margin-top: 3rem;
  padding: 0 2rem;
}

.icon-box {
  width: 80px;
  height: 80px;
  background-color: #1f1f1f;
  border-radius: 15px;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.3s ease;
  box-shadow: 0 0 5px rgba(0, 255, 255, 0.1);
}

.icon-box:hover {
  transform: scale(1.1);
  box-shadow: 0 0 15px rgba(0, 255, 255, 0.4);
}

.icon-box i {
  font-size: 28px;
  color: #00f2ff;
}
</style>

<div class="icon-grid">
  <a href="https://tushar-bioinfo.github.io/learning-bioinformatics/" class="icon-box" target="_blank">
    <i class="fas fa-blog"></i>
  </a>
  <a href="https://github.com/Tushar-bioinfo" class="icon-box" target="_blank">
    <i class="fab fa-github"></i>
  </a>
  <a href="https://linkedin.com/in/tussi147" class="icon-box" target="_blank">
    <i class="fab fa-linkedin"></i>
  </a>
  <a href="mailto:tushar14032001@gmail.com" class="icon-box">
    <i class="fas fa-envelope"></i>
  </a>
</div>
