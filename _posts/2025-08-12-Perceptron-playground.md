---
title: "Perceptron Playground — When It Works and When It Fails"
date: 2025-08-12 00:00:00 +0000
image:
  path: https://tushar-bioinfo.github.io/learning-bioinformatics/assets/img/snrna-04-07-2025/img-.png
  alt: "Boston housing prediction banner"
---

Today, I decided to dive into one of the most classic machine learning algorithms: the **Perceptron**.  
It’s simple, fast, and a great starting point for understanding how linear models work — but also a perfect example of their limitations.

{: .prompt-info }
**What is a Perceptron?**  
A perceptron is essentially a single neuron: it takes input features, multiplies them by weights, adds a bias, and passes the sum through a step function to decide between two classes.

---

## Linearly Separable Data — The Perceptron’s Comfort Zone

To warm up, I generated two Gaussian blobs that can be perfectly split by a straight line.  
Here’s what happened when I trained a perceptron:

![Perceptron Linear](https://tushar-bioinfo.github.io/learning-bioinformatics/assets/img/blog1/plot1.png){: width="500" height="500" }

**Observation:**  
- The perceptron quickly converged and drew a straight boundary between the two classes.
- Training accuracy: **100%** — exactly what we expect when the data are **linearly separable**.

{: .prompt-tip }
If your dataset *can* be split perfectly by a straight line, a perceptron will find that line and stop updating its weights once all points are correctly classified.

---

## Partial Overlap — Imperfect but Still Linear

I then moved the blobs closer together, creating some overlap.

![Perceptron Overlap](https://tushar-bioinfo.github.io/learning-bioinformatics/assets/img/blog1/plot2.png){: width="500" height="500" }

**Observation:**  
- The perceptron still learned a straight line, but **couldn’t separate overlapping points**.
- Accuracy dropped below 1.0 because no linear boundary can fix mislabeled regions.

{: .prompt-warning }
Don’t expect 100% accuracy if your classes overlap — no matter how long you train, a linear model can’t do magic here.

---

## The Famous XOR Problem — A Hard Fail

The **XOR** dataset labels alternate corners differently.  
No single straight line can separate these points.

![Perceptron XOR](https://tushar-bioinfo.github.io/learning-bioinformatics/assets/img/blog1/plot3.png){: width="500" height="500" }

**What happened:**  
- The perceptron kept updating but couldn’t improve beyond ~50% accuracy.
- This is a **fundamental limitation**: XOR is **not linearly separable**.

---

## Curved Boundaries — Moons and Circles

I also tried datasets where the boundary is curved:

- **Two Moons:** Interleaved crescents.  
- **Concentric Circles:** Inner ring vs outer ring.

![Perceptron Moons](https://tushar-bioinfo.github.io/learning-bioinformatics/assets/img/blog1/plot4.png){: width="500" height="500" }
![Perceptron Circles](https://tushar-bioinfo.github.io/learning-bioinformatics/assets/img/blog1/plot5.png){: width="500" height="500" }

**Observation:**  
- The perceptron draws a straight line through the pattern, cutting across both shapes.  
- Accuracy is limited because the true boundaries are **non-linear**.

---

## Summary — Key Takeaways

1. Perceptrons work well **only** for linearly separable binary classification.  
2. Overlapping or non-linear patterns require either:
   - Feature transformations (e.g., polynomial features)
   - Multi-layer networks (MLPs) with non-linear activations
3. The XOR problem is the classic proof that **we need hidden layers**.

{: .prompt-tip }
This is exactly why modern deep learning architectures stack multiple layers with non-linearities — so they can model boundaries of *any* shape, not just straight lines.

---

## What’s Next?
In the next post, I’ll extend this to **multi-layer perceptrons** and show how just one hidden layer can solve XOR and other non-linear problems.

**Full notebook:** [Perceptron Playground on GitHub](#)  
