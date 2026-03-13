# C13_MFC4_Compressed_Sensing_Reconstruction_ADMM  

---

# Project Title
## Compressed Sensing Reconstruction using ADMM 

---

## Member Details

## Team C-13

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

### ADMM Formulation
### x-Update Derivation (ILSTAT-ADMM)

#### 1. Optimization Problem

The image reconstruction problem is formulated as

$$
\min_x ||Ax - b||^2 + \lambda ||x||_0
$$

where

- $x$ – original image  
- $A$ – blur operator  
- $b$ – observed blurred image  
- $\lambda$ – sparsity regularization parameter  

The first term enforces **data fidelity**, while the second promotes **sparsity**.

---

#### 2. Variable Splitting

Introduce an auxiliary variable

$$
y = Ax
$$

The optimization becomes

$$
\min_{x,y} \frac{1}{2} ||y - b||^2 + \lambda ||x||_0
$$

subject to

$$
y = Ax
$$

This separates

- the **data fidelity term** (depends on $y$)
- the **sparsity term** (depends on $x$).

---

#### 3. Augmented Lagrangian

To enforce the constraint $y = Ax$, the augmented Lagrangian is constructed:

$$
L(x,y,z) =
\frac{1}{2} ||y - b||^2
+
\lambda ||x||_0
+
z^T (Ax - y)
+
\frac{\rho}{2} ||Ax - y||^2
$$

where

- $z$ is the Lagrange multiplier  
- $\rho$ is the penalty parameter.

---

#### 4. x-Update Subproblem

In ADMM, the $x$ update is obtained by minimizing the Lagrangian while fixing $y^k$ and $z^k$:

$$
x^{k+1} = \arg\min_x L(x, y^k, z^k)
$$

Substituting the Lagrangian gives

$$
\min_x
\left(
\lambda ||x||_0
+
z^{kT}(Ax - y^k)
+
\frac{\rho}{2} ||Ax - y^k||^2
\right)
$$

The term $\frac{1}{2}||y-b||^2$ is removed since it does not depend on $x$.

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


- Apply the proposed compressed sensing reconstruction algorithm to medical imaging problems such as MRI, where fast image acquisition and reduced sampling are critical.


---

## References

[1] Y.-M. Li and H. Wang,  
“A New Limited Shrinkage Thresholding Iterative ADMM Algorithm for Compressed Sensing Signal Reconstruction,”  
Signal Processing, Elsevier, 2026.  
https://doi.org/10.1016/j.sigpro.2025.110319

---

## Repository Structure

- `code` : MATLAB implementation of the ADMM + LST algorithm  
- `doc` : Base paper, review pdf, figure 
- `README.md` : Project documentation



