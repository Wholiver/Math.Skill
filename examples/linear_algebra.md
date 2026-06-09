# Eigenvalues ​​and diagonalization of matrices

## User input
Find the eigenvalues ​​and eigenvectors of matrix $A = \begin{pmatrix} 3 & 1 \\ 1 & 3 \end{pmatrix}$, and find the invertible matrix $P$ and the diagonal matrix $D$ such that $A = PDP^{-1}$.

## Skill Category
linear algebra

## Question meaning analysis
- **Known conditions**: $2 \times 2$ real symmetric matrix $A = \begin{pmatrix} 3 & 1 \\ 1 & 3 \end{pmatrix}$.
- **Solution objectives**: (1) eigenvalue $\lambda_1, \lambda_2$; (2) corresponding eigenvector $\mathbf{v}_1, \mathbf{v}_2$; (3) diagonalization $A = PDP^{-1}$.
- **Key Properties**: $A$ is a real symmetric matrix, so the eigenvalues ​​are all real numbers, the eigenvectors are orthogonal, and they must be diagonalizable.
- **Implicit condition**: The columns of $P$ are the eigenvectors, and the diagonals of $D$ are the eigenvalues ​​(the order corresponds to the eigenvectors in $P$).

## Method selection
**Preferred method**: Solve the characteristic equation $\det(A - \lambda I) = 0$ to get the eigenvalues, and then solve the homogeneous system of equations $(A - \lambda I)\mathbf{v} = \mathbf{0}$ for each $\lambda$ to get the eigenvectors.

**Alternative method**: Use the spectral theorem for symmetric matrices to perform orthogonal diagonalization. For the $2 \times 2$ matrix, you can also directly use the trace and determinant to find the eigenvalues ​​($\lambda_1 + \lambda_2 = \text{tr}(A) = 6$, $\lambda_1 \lambda_2 = \det(A) = 8$).

## Problem solving process

### Step 1: Find eigenvalues

Characteristic polynomial:

 $$\det(A - \lambda I) = \begin{vmatrix} 3 - \lambda & 1 \\ 1 & 3 - \lambda \end{vmatrix}$$

 $$= (3 - \lambda)^2 - 1 = \lambda^2 - 6\lambda + 8 = (\lambda - 4)(\lambda - 2)$$

 $$(\lambda - 4)(\lambda - 2) = 0$$

Eigenvalues:

 $$\lambda_1 = 2,\quad \lambda_2 = 4$$

### Step 2: Find the feature vector

**For $\lambda_1 = 2$ **, solve for $(A - 2I)\mathbf{v} = \mathbf{0}$:

 $$\begin{pmatrix} 1 & 1 \\ 1 & 1 \end{pmatrix} \begin{pmatrix} x \\ y \end{pmatrix} = \begin{pmatrix} 0 \\ 0 \end{pmatrix}$$

That is $x + y = 0$, take $x = 1$ then $y = -1$.

 $$\mathbf{v}_1 = \begin{pmatrix} 1 \\ -1 \end{pmatrix}$$

**For $\lambda_2 = 4$**, solve $(A - 4I)\mathbf{v} = \mathbf{0}$:

 $$\begin{pmatrix} -1 & 1 \\ 1 & -1 \end{pmatrix} \begin{pmatrix} x \\ y \end{pmatrix} = \begin{pmatrix} 0 \\ 0 \end{pmatrix}$$

That is $-x + y = 0$, take $x = 1$ then $y = 1$.

 $$\mathbf{v}_2 = \begin{pmatrix} 1 \\ 1 \end{pmatrix}$$

### Step 3: Construct $P$ and $D$

 $$P = \begin{pmatrix} \mathbf{v}_1 & \mathbf{v}_2 \end{pmatrix} = \begin{pmatrix} 1 & 1 \\ -1 & 1 \end{pmatrix}$$

 $$D = \begin{pmatrix} \lambda_1 & 0 \\ 0 & \lambda_2 \end{pmatrix} = \begin{pmatrix} 2 & 0 \\ 0 & 4 \end{pmatrix}$$

### Step 4: Verify $A = PDP^{-1}$

Asking for $P^{-1}$:

 $$\det(P) = 1 \cdot 1 - 1 \cdot (-1) = 2$$

 $$P^{-1} = \frac{1}{2} \begin{pmatrix} 1 & -1 \\ 1 & 1 \end{pmatrix}$$

verify:

 $$PDP^{-1} = \frac{1}{2} \begin{pmatrix} 1 & 1 \\ -1 & 1 \end{pmatrix} \begin{pmatrix} 2 & 0 \\ 0 & 4 \end{pmatrix} \begin{pmatrix} 1 & -1 \\ 1 & 1 \end{pmatrix}$$

 $$= \frac{1}{2} \begin{pmatrix} 1 & 1 \\ -1 & 1 \end{pmatrix} \begin{pmatrix} 2 & -2 \\ 4 & 4 \end{pmatrix} = \frac{1}{2} \begin{pmatrix} 6 & 2 \\ 2 & 6 \end{pmatrix} = \begin{pmatrix} 3 & 1 \\ 1 & 3 \end{pmatrix} = A$$

✓

## Check calculation

### Method 1: Verify $A\mathbf{v}_i = \lambda_i \mathbf{v}_i$

 $$A\mathbf{v}_1 = \begin{pmatrix} 3 & 1 \\ 1 & 3 \end{pmatrix} \begin{pmatrix} 1 \\ -1 \end{pmatrix} = \begin{pmatrix} 3 - 1 \\ 1 - 3 \end{pmatrix} = \begin{pmatrix} 2 \\ -2 \end{pmatrix} = 2 \begin{pmatrix} 1 \\ -1 \end{pmatrix} = \lambda_1 \mathbf{v}_1$$

 $$A\mathbf{v}_2 = \begin{pmatrix} 3 & 1 \\ 1 & 3 \end{pmatrix} \begin{pmatrix} 1 \\ 1 \end{pmatrix} = \begin{pmatrix} 3 + 1 \\ 1 + 3 \end{pmatrix} = \begin{pmatrix} 4 \\ 4 \end{pmatrix} = 4 \begin{pmatrix} 1 \\ 1 \end{pmatrix} = \lambda_2 \mathbf{v}_2$$

✓

### Method 2: Trace and determinant verification

 $$\text{tr}(A) = 3 + 3 = 6 = 2 + 4 = \lambda_1 + \lambda_2$$

 $$\det(A) = 3 \cdot 3 - 1 \cdot 1 = 8 = 2 \cdot 4 = \lambda_1 \lambda_2$$

✓

### Method 3: Orthogonality of eigenvectors

 $$\mathbf{v}_1 \cdot \mathbf{v}_2 = 1 \cdot 1 + (-1) \cdot 1 = 0$$

The eigenvectors are orthogonal and conform to the properties of real symmetric matrices. ✓

## Final answer

 $$\boxed{\lambda_1 = 2,\; \mathbf{v}_1 = \begin{pmatrix} 1 \\ -1 \end{pmatrix}}$$

 $$\boxed{\lambda_2 = 4,\; \mathbf{v}_2 = \begin{pmatrix} 1 \\ 1 \end{pmatrix}}$$

 $$\boxed{P = \begin{pmatrix} 1 & 1 \\ -1 & 1 \end{pmatrix},\quad D = \begin{pmatrix} 2 & 0 \\ 0 & 4 \end{pmatrix},\quad A = PDP^{-1}}$$

## Easy to make mistakes
1. **Symbol of characteristic equation**: $\det(A - \lambda I) = 0$ or $\det(\lambda I - A) = 0$? After the expansion of the former, the characteristic polynomial is $(-1)^n \det(\lambda I - A)$. The two are equivalent to find the eigenvalues, but pay attention to the symbolic details.
2. **Order of eigenvectors**: The order of eigenvectors in $P$ must be consistent with the order of eigenvalues ​​on the diagonal of $D$. If the positions of $\mathbf{v}_1$ and $\mathbf{v}_2$ are swapped, the diagonal of $D$ should also become $\operatorname{diag}(4, 2)$ .
3. **Eigenvector Scaling**: The eigenvector is not unique (can be multiplied by any non-zero scalar), but the result of $PDP^{-1}$ remains unchanged.
4. **Check diagonalizability premise**: Not all matrices are diagonalizable (such as Jordan blocks). Real symmetric matrices are naturally diagonalizable, but general matrices need to check geometric multiplicity = algebraic multiplicity.
