---
layout: page
title: My Links
icon: fas fa-link
permalink: /links/
---

<style>
/* Background banner wrapper */
.banner-bg {
  background-image: url('/assets/img/dna-banner.gif');
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center;
  border-radius: 16px;
  padding: 4rem 2rem;
  margin-top: 2rem;
  box-shadow: inset 0 0 100px rgba(0, 255, 255, 0.15);
}

/* Icon grid layout */
.icon-grid {
  display: grid;
  grid-template-columns: repeat(2, 160px);
  grid-template-rows: repeat(2, 160px);
  gap: 2.5rem;
  justify-content: center;
}

/* Individual icon box */
.icon-box {
  width: 160px;
  height: 160px;
  background-color: rgba(31, 31, 31, 0.9);
  border-radius: 20px;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.3s ease;
  box-shadow: 0 0 10px rgba(0, 255, 255, 0.08);
}

.icon-box:hover {
  transform: scale(1.07);
  box-shadow: 0 0 22px rgba(0, 255, 255, 0.5);
  background-color: rgba(38, 50, 56, 0.95);
}

/* Font Awesome icon inside box */
.icon-box i {
  font-size: 48px;
  color: #00f2ff;
}
</style>

<!-- Icon Grid Inside Animated Background -->
<div class="banner-bg">
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
</div>
