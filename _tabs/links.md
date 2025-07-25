---
layout: page
title: My Links
icon: fas fa-link
permalink: /links/
order: 4
---

<style>
/* Icon grid layout */
.icon-grid {
  display: grid;
  grid-template-columns: repeat(2, 200px);
  grid-template-rows: repeat(2, 200px);
  gap: 3rem;
  justify-content: center;
  margin-top: 3rem;
}

/* Individual icon box */
.icon-box {
  width: 200px;
  height: 200px;
  background-color: #1f1f1f;
  border-radius: 24px;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.3s ease;
  box-shadow: 0 0 12px rgba(0, 255, 255, 0.1);
}

.icon-box:hover {
  transform: scale(1.08);
  box-shadow: 0 0 25px rgba(0, 255, 255, 0.6);
  background-color: #263238;
}

/* Icon inside box */
.icon-box i {
  font-size: 58px;
  color: #00f2ff;
}
</style>

<!-- Icon Grid -->
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
