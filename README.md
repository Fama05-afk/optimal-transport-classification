# Supervised Classification via Optimal Transport

**Flow cytometry data classification using Optimal Transport theory (Python)**  
Master MSS — Université de Bordeaux | 2024–2025

---

## Objective

Classify target data points (unknown labels) using the structural information of a labeled source distribution, via Optimal Transport theory.  
This work is motivated by **flow cytometry** analysis, a high-throughput biotechnology used to characterize large quantities of biological cells.

---

## Project Structure

```
├── Projet_OT_Mixture_Fama_Saad_Harrach_F.ipynb   # Full implementation
└── README.md
```

---

## Approach

The core idea is to compute an optimal transport plan between a labeled source distribution and an unlabeled target distribution, then propagate class labels via weighted majority voting.

**Cost matrix**

$$C_{ij} = \log(1 + \|X_i - Y_j\|^2)$$

The log transformation reduces the influence of large distances and improves numerical stability.

**Two methods compared**

| Method | Description | Computation time | Accuracy |
|---|---|---|---|
| **EMD** (Earth Mover's Distance) | Exact solution via linear programming | ~600s | — |
| **Sinkhorn** | Regularized OT (entropy regularization ε=0.04) | ~23s | **93.66%** |

---

## Methodology

**Label propagation**  
For each target point Y_j, the predicted class is determined by weighted majority voting using the transport masses P*_ij from source points X_i.

**Evaluation**  
- Accuracy score
- Confusion matrix (10 classes)
- Comparison of predicted vs true class proportions

**Key finding**  
Sinkhorn (regularized) achieves 93.66% accuracy with a 26x speedup over exact EMD, while maintaining comparable class proportion estimates.

---

## Tech Stack

- Python 3
- POT (Python Optimal Transport)
- NumPy, pandas, scikit-learn
- Matplotlib, Seaborn
- Google Colab

---

## Author

Fama DIALLO — Master MSS, Université de Bordeaux
