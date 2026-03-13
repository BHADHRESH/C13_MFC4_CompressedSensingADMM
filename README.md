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

### 5. Combining the Linear and Quadratic Terms

Now consider the terms

$$
z^{kT}(Ax - y^k) + \frac{\rho}{2}\|Ax - y^k\|^2
$$

Let

$$
u = Ax - y^k
$$

Then the expression becomes

$$
z^{kT}u + \frac{\rho}{2}u^Tu
$$

Factor $\frac{\rho}{2}$:

$$
\frac{\rho}{2}\left(u^Tu + \frac{2}{\rho}z^{kT}u\right)
$$

Using the identity

$$
\|u + a\|^2 = u^Tu + 2a^Tu + a^Ta
$$

choose

$$
a = \frac{z^k}{\rho}
$$

so that

$$
u^Tu + \frac{2}{\rho}z^{kT}u =
\left\|u + \frac{z^k}{\rho}\right\|^2 -
\left\|\frac{z^k}{\rho}\right\|^2
$$


#### Multiply Back by $\frac{\rho}{2}$

Recall that we obtained

$$
\frac{\rho}{2}\left(u^Tu + \frac{2}{\rho}z^{kT}u\right)
$$

Substituting the completed square expression

$$
u^Tu + \frac{2}{\rho}z^{kT}u =
\left\||u+\frac{z^k}{\rho}\right\||^2 -
\left\||\frac{z^k}{\rho}\right\||^2
$$

gives

$$
\frac{\rho}{2}
\left(
\left\||u+\frac{z^k}{\rho}\right\||^2 -
\left\||\frac{z^k}{\rho}\right\||^2
\right)
$$

---

#### Separate the Terms

Expanding the expression gives

$$
\frac{\rho}{2}\||u + \frac{z^k}{\rho}\||^2 - \frac{\rho}{2}\left\||\frac{z^k}{\rho}\right\||^2
$$

The second term does **not depend on $x$**, so it is constant.

In optimization, constants do not affect the minimization, so this term can be ignored.

---

#### Final Simplified Form

Thus we keep only

$$
\frac{\rho}{2}\left\||u + \frac{z^k}{\rho}\right\||^2
$$

Now substitute

$$
u = Ax - y^k
$$

Then

$$
u + \frac{z^k}{\rho} = Ax - y^k + \frac{z^k}{\rho}
$$

Rewrite this as

$$
Ax - \left(y^k - \frac{z^k}{\rho}\right)
$$

Define

$$
b_k = y^k - \frac{z^k}{\rho}
$$

Therefore the expression becomes

$$
\frac{\rho}{2}\||Ax - b_k\||^2
$$



Thus

$$
\begin{aligned}
z^{kT}(Ax - y^k) + \frac{\rho}{2}\||Ax - y^k\||^2
&= \frac{\rho}{2}\||Ax - b_k\||^2
\end{aligned}
$$

---

### 6. Simplified x-Subproblem

The x-update becomes

$$
x^{k+1} =
\arg\min_x
\left(
\frac{\rho}{2}\||Ax - b_k\||^2 + \lambda\||x\||_0
\right)
$$

This is a **sparse least-squares problem**.

---

### 7. Gradient of the Quadratic Term

Consider

$$
f(x) = \|Ax - b_k\|^2
$$

The gradient is

$$
\nabla f(x) = A^T(Ax - b_k)
$$

because the derivative of $Ax$ with respect to $x$ produces $A^T$.

---

### 8. Gradient Descent Update

Using gradient descent,

$$
x_{\text{temp}} =
x_k - \frac{1}{v} A^T(Ax_k - b_k)
$$

where

- $x_k$ is the estimate at iteration $k$
- $v$ controls the step size.


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



