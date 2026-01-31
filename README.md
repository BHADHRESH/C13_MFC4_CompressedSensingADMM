# D4_MFC4_ADMM  

---

## Project Title
Compressed Sensing Reconstruction using ADMM 

---

## Member Details

- **Jignesh Sudheer**  
  Roll No: CB.SC.U4AIE24222  
  Email: <cb.sc.u4aie24222@cb.students.amrita.edu>

- **Bhadhresh R P**  
  Roll No: CB.SC.U4AIE24208  
  Email: <cb.sc.u4aie24208@cb.students.amrita.edu>

- **Shravan Rajesh Menon**  
  Roll No: CB.SC.U4AIE24253  
  Email: <cb.sc.u4aie24253@cb.students.amrita.edu>

- **Gautham T**  
  Roll No: CB.SC.U4AIE24264  
  Email: <cb.sc.u4aie24264@cb.students.amrita.edu>

---

## Objective

The objective of this project is to study and implement a compressed sensing reconstruction algorithm using the Alternating Direction Method of Multipliers (ADMM) combined with Limited Shrinkage Thresholding (LST) for recovering sparse signals from underdetermined linear measurements.

---

## Motivation / Why the Project is Interesting

Compressed sensing allows signal reconstruction using fewer measurements by exploiting sparsity. This is important in applications where acquiring measurements is expensive or limited. The project is interesting because it combines optimization techniques with sparsity-promoting thresholding methods to solve an ill-posed reconstruction problem.

---

## Methodology

### Mathematical Techniques Used

- Sparse signal modeling
- ℓ₀-norm based sparsity concept
- Limited Shrinkage Thresholding (LST)
- Alternating Direction Method of Multipliers (ADMM)
- Gradient-based iterative updates
- ℓ₂-norm based reconstruction error analysis

### Demonstration Using a Toy Example

A synthetic sparse signal with a small number of non-zero elements is generated. Random linear measurements are obtained using a sensing matrix. The ADMM-based algorithm with LST is applied iteratively to reconstruct the sparse signal. The reconstructed signal is compared with the original signal to verify recovery performance.

---

## Results & Discussion

- Successful reconstruction of sparse signals from limited measurements is observed.
- The reconstructed signal closely matches the original sparse signal.
- Convergence behavior shows a decreasing reconstruction error with iterations.
- Sensitivity of the reconstruction to the LST threshold parameter (λ) is analyzed, showing that proper parameter selection is important.
- The observed results are consistent with the expected behavior discussed in the base paper.

---

## Future Plans

- Test the algorithm for different sparsity levels and measurement sizes.
- Extend the implementation to handle noisy measurements.
- Apply the method to simple real-world signals.
- Improve result visualization and analysis.

---

## References

[1] Y.-M. Li and H. Wang,  
“A New Limited Shrinkage Thresholding Iterative ADMM Algorithm for Compressed Sensing Signal Reconstruction,”  
Signal Processing, Elsevier, 2026.  
https://www.sciencedirect.com/

---

## Repository Structure

- `code` : MATLAB implementation of the ADMM + LST algorithm  
- `doc` : Base paper, review material, figures, and presentation files  
- `README.md` : Project documentation



