# Compressed Sensing Reconstruction using ADMM 

## Overview
This project implements a compressed sensing reconstruction algorithm using
the Alternating Direction Method of Multipliers (ADMM) combined with
Limited Shrinkage Thresholding (LST).

## Problem Statement
Recover a sparse high-dimensional signal from a limited number of linear
measurements by solving an ℓ₀-constrained optimization problem.

## Methodology
- Sparse signal model
- Random Gaussian sensing matrix
- ADMM-based optimization
- Limited Thresholding (LT)
- Hard thresholding for ℓ₀ constraint

## Files
- `admm_lsts.m` : MATLAB implementation of the algorithm
- `review.pdf` : Literature review document
- `review_presentation.pptx` : Review presentation slides

## Output
The algorithm successfully recovers the sparse signal, matching both
support and amplitude.

## Tools Used
- MATLAB
- GitHub

