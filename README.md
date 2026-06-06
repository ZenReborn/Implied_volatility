# NIFTY 50 Implied Volatility Surface Reconstruction

This repository contains my solution for a Kaggle competition focused on reconstructing missing values in the NIFTY 50 implied volatility (IV) surface.

## Problem Statement

The dataset contains partially observed implied volatility values for NIFTY 50 options across different strikes. Due to illiquidity and sparse trading activity, several IV entries are missing.

The goal is to accurately reconstruct these missing values and generate a submission file in the required competition format.

## Approach

The final solution uses a combination of:

1. **Iterative PCA reconstruction**
   - Low-rank approximation of the IV surface
   - Multiple PCA ranks used to capture both global and local structure

2. **Ensembling**
   - Weighted combination of several PCA reconstructions
   - Improved robustness and reconstruction accuracy

## Key Ideas

- Implied volatility surfaces exhibit strong smoothness and low-rank structure.
- Neighboring strikes are highly correlated.
- A small number of latent factors explain most of the variation in the IV surface.
- Matrix reconstruction methods outperform traditional machine learning models for this task.

## Results

| Method | Score |
|----------|----------|
| LightGBM Baseline | 0.0246 |
| Interpolation + ML | 0.0035 |
| 2D Interpolation | 0.000305 |
| PCA Reconstruction | 0.000160 |
| Iterative PCA | 0.000130 |
| PCA Ensemble | 0.000087 |

## Repository Structure

```text
.
├── dataset.csv
├── notebooks/
│   ├── iterative_pca.ipynb
├── submissions/
├── README.md
└── requirements.txt
