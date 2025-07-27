---
layout: page
title: 
permalink: /projects/boston-house/
icon: fas fa-house-user
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

<h1>Boston Housing Price Prediction</h1>

<h2>Summary</h2>
<p>
This project builds a complete machine learning pipeline using Python’s <code>scikit-learn</code> to predict Boston housing prices. The workflow focuses on feature selection, multivariable regression, residual diagnostics, and visual interpretability using <code>Matplotlib</code> and <code>Seaborn</code>.
</p>

<h2>What I Did</h2>
<ul>
  <li>Built a multivariable linear regression model with <strong>>80% R²</strong> on test data.</li>
  <li>Performed <strong>correlation analysis</strong> and addressed multicollinearity with <code>VIF</code>.</li>
  <li>Used <strong>RMSE</strong>, residual plots, and diagnostic graphs for performance assessment.</li>
  <li>Structured the ML pipeline end-to-end: <em>preprocessing → model training → threshold tuning → visualization</em>.</li>
  <li>Used <code>Matplotlib</code> and <code>Seaborn</code> for plotting residuals, confidence bands, and prediction trends.</li>
</ul>

<h2> </h2>
<div class="project-tags">
  <span class="project-tag">Scikit-learn</span>
  <span class="project-tag">Linear Regression</span>
  <span class="project-tag">Matplotlib</span>
  <span class="project-tag">Seaborn</span>
  <span class="project-tag">Pandas</span>
  <span class="project-tag">Statsmodels</span>
  <span class="project-tag">Exploratory Data Analysis</span>
</div>

<h2> </h2>
<div class="project-links">
  <a href="https://github.com/Tushar-bioinfo/Boston-house-price-prediction" target="_blank">
    <i class="fab fa-github"></i> GitHub
  </a>
  <a href="https://tushar-bioinfo.github.io/learning-bioinformatics/posts/boston-house-model/" target="_blank">
    <i class="fas fa-book-open"></i> Blog
  </a>
</div>

</div>
