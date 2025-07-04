---
layout: page
title: My Links
icon: fas fa-link
permalink: /links/
---

<style>
.link-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 1.2rem;
  margin-top: 1.5rem;
}

.link-card {
  background-color: #1e1e1e;
  border: 1px solid #333;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
  transition: all 0.3s ease;
  box-shadow: 0 4px 10px rgba(0, 255, 255, 0.05);
}

.link-card:hover {
  transform: scale(1.03);
  box-shadow: 0 0 15px rgba(0, 255, 255, 0.25);
}

.link-card a {
  text-decoration: none;
  color: #00f2ff;
  font-weight: 600;
  display: block;
  margin-top: 0.5rem;
}

.link-icon {
  font-size: 2rem;
  color: #56cc9d;
}
</style>

<div class="link-grid">
  <div class="link-card">
    <div class="link-icon"><i class="fas fa-blog"></i></div>
    <a href="https://tushar-bioinfo.github.io/learning-bioinformatics/" target="_blank">Blog: Learning Bioinformatics</a>
  </div>
  <div class="link-card">
    <div class="link-icon"><i class="fab fa-github"></i></div>
    <a href="https://github.com/Tushar-bioinfo" target="_blank">GitHub: @Tushar-bioinfo</a>
  </div>
  <div class="link-card">
    <div class="link-icon"><i class="fab fa-linkedin"></i></div>
    <a href="https://linkedin.com/in/tussi147" target="_blank">LinkedIn: tussi147</a>
  </div>
  <div class="link-card">
    <div class="link-icon"><i class="fas fa-envelope"></i></div>
    <a href="mailto:tushar14032001@gmail.com">Email: tushar14032001@gmail.com</a>
  </div>
</div>
