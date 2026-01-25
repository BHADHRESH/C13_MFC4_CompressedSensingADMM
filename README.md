#  Compressed Sensing Reconstruction using ADMM 

## Team Members


- **Jignesh Sudheer** – CB.SC.U4AIE24222  
- **Bhadhresh R P** – CB.SC.U4AIE24208  
- **Shravan Rajesh Menon** – CB.SC.U4AIE24253  
- **Gautham T** – CB.SC.U4AIE24264


---



## Base / Reference Paper

Yuan-Min Li and Hao Wang,  
**"A New Limited Shrinkage Thresholding Iterative ADMM Algorithm for Compressed Sensing Signal Reconstruction,"**  
*Signal Processing*, Elsevier, vol. 239, 2026, Article 110319.


This paper proposes an ADMM-based framework combined with a Limited Shrinkage Thresholding (LST) operator for solving ℓ₀-norm constrained sparse optimization problems and provides convergence analysis under RIP and Kurdyka–Łojasiewicz (KŁ) conditions.

---

## Project Outline

The objective of this project is to study and implement a **compressed sensing reconstruction algorithm** based on the concepts presented in the reference paper. The focus is on recovering a sparse signal from underdetermined linear measurements using an ADMM-based optimization framework with thresholding-based sparsity enforcement.

Key aspects of the project include:
- Understanding compressed sensing and sparsity assumptions
- ℓ₀-norm constrained problem formulation
- Use of ADMM for variable splitting and constrained optimization
- Application of Limited Thresholding (LT) and hard thresholding
- MATLAB-based implementation and validation

---

## Updates

1. Studied the fundamentals of compressed sensing and sparsity-based signal recovery.
2. Understood the ℓ₀-constrained compressed sensing formulation discussed in the base paper.
3. Reviewed the ADMM framework and the role of Limited Shrinkage Thresholding (LST).
4. Implemented a basic ADMM-based compressed sensing reconstruction algorithm in MATLAB.
5. Verified sparse signal recovery through simulation and visual comparison of original and reconstructed signals.

---

## Challenges / Issues Faced

- Understanding the non-convex nature of ℓ₀-norm constrained optimization.
- Interpreting the role of LST and its difference from hard and soft thresholding.
- Relating theoretical convergence conditions (RIP, stationarity) to practical implementation.
- Selecting appropriate parameters such as step size and threshold value.
- Ensuring numerical stability during iterative reconstruction.

---

## Future Plans

- Extend the implementation to include noisy measurement scenarios.
- Incorporate more elements from the base paper such as LTP-stationary concepts.
- Compare performance with ℓ₁-based sparse recovery methods.
- Evaluate reconstruction quality using metrics such as MSE and SNR.
- Analyze convergence behavior for different sparsity levels and parameters.
- Prepare final report and presentation for project evaluation.

---

## Folders

- `code` : MATLAB implementation of compressed sensing using ADMM  
- `base_paper` : Reference research paper (PDF)  
- `review_pdf` : Project documentation  

---

## Tools & Technologies

- MATLAB (Algorithm implementation )
- Git & GitHub (Version control and project management)


