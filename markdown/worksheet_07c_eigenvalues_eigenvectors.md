# Worksheet 7C: Eigenvalues and Eigenvectors
**AIML Foundations Mathematics**
**Dublin and Dún Laoghaire ETB**
**Instructor: Josh Aaron**

---

> **What This Worksheet Is About**
>
> Most vectors, when multiplied by a matrix, change both their length and their direction. But some special vectors — **eigenvectors** — only get scaled. The matrix stretches or flips them, but doesn't rotate them.
>
> These special directions are the "natural axes" of a matrix, and the scaling factors are the **eigenvalues**. They appear throughout applied mathematics: the stationary distribution of a Markov chain (ws07d) is an eigenvector. Principal Component Analysis — the dimension reduction algorithm used in almost every major ML pipeline — is pure eigenvalue decomposition. Google's PageRank is an eigenvector computation.
>
> This worksheet builds the concept geometrically, develops the algebra, and connects it to everything you have seen so far.

---

## Part A: Geometric Intuition (8 problems)

### The Core Idea

If $A$ is a matrix and $\mathbf{v}$ is a non-zero vector such that:

$$A\mathbf{v} = \lambda \mathbf{v}$$

then $\mathbf{v}$ is an **eigenvector** of $A$ and $\lambda$ is the corresponding **eigenvalue**.

The matrix $A$ acts on $\mathbf{v}$ by scaling it (by $\lambda$) — without changing its direction (or reversing it if $\lambda < 0$).

---

**1.** Let $A = \begin{bmatrix} 3 & 0 \\ 0 & 2 \end{bmatrix}$ (a diagonal matrix).

- (a) Compute $A \begin{bmatrix} 1 \\ 0 \end{bmatrix}$ and $A \begin{bmatrix} 0 \\ 1 \end{bmatrix}$.
- (b) Are these vectors eigenvectors? What are the eigenvalues?
- (c) Compute $A \begin{bmatrix} 1 \\ 1 \end{bmatrix}$. Is this an eigenvector?
- (d) What do the eigenvalues tell you about what $A$ does to the coordinate axes?

**2.** A matrix $A$ scales every vector by 5: $A\mathbf{v} = 5\mathbf{v}$ for all $\mathbf{v}$. What matrix is $A$? What are its eigenvalues? How many eigenvectors does it have?

**3.** The rotation matrix $R = \begin{bmatrix} 0 & -1 \\ 1 & 0 \end{bmatrix}$ rotates vectors by $90°$.

- (a) Does any real vector stay pointing in the same direction after a $90°$ rotation?
- (b) What does this tell you about the real eigenvalues of $R$?
- (c) This is a hint that $R$ has complex eigenvalues. We will see this in Part B.

**4.** The reflection matrix $F = \begin{bmatrix} 1 & 0 \\ 0 & -1 \end{bmatrix}$ reflects vectors across the $x$-axis.

- (a) Find two vectors that are eigenvectors of $F$ by inspection.
- (b) What are their eigenvalues? Interpret the values geometrically.
- (c) What does the negative eigenvalue represent geometrically?

---

**5.** If $\mathbf{v}$ is an eigenvector of $A$ with eigenvalue $\lambda$, show that $2\mathbf{v}$ is also an eigenvector with the same eigenvalue.

**6.** If $\mathbf{v}$ and $\mathbf{w}$ are both eigenvectors of $A$ with the **same** eigenvalue $\lambda$, show that $\mathbf{v} + \mathbf{w}$ is also an eigenvector (assuming the result is non-zero).

**7.** If $\mathbf{v}$ is an eigenvector of $A$ with eigenvalue $\lambda \neq 0$, what is the eigenvalue of $\mathbf{v}$ with respect to $A^{-1}$? (Hint: apply $A^{-1}$ to both sides of $A\mathbf{v} = \lambda\mathbf{v}$.)

**8.** The **identity matrix** $I$ has every vector as an eigenvector. What is the eigenvalue? The **zero matrix** $O$ also has every vector as an eigenvector — what is the eigenvalue? These are the two extreme cases.

---

## Part B: Finding Eigenvalues — The Characteristic Polynomial (10 problems)

### The Algorithm

The equation $A\mathbf{v} = \lambda\mathbf{v}$ can be written as $(A - \lambda I)\mathbf{v} = \mathbf{0}$.

This has a non-zero solution $\mathbf{v}$ **only when** $A - \lambda I$ is singular, i.e., when:

$$\det(A - \lambda I) = 0$$

This is the **characteristic equation**. The polynomial $p(\lambda) = \det(A - \lambda I)$ is the **characteristic polynomial**.

For a $2 \times 2$ matrix $A = \begin{bmatrix} a & b \\ c & d \end{bmatrix}$:

$$\det(A - \lambda I) = (a - \lambda)(d - \lambda) - bc = \lambda^2 - (a+d)\lambda + (ad-bc) = \lambda^2 - \text{tr}(A)\lambda + \det(A)$$

---

**Find the characteristic polynomial and eigenvalues:**

**9.** $A = \begin{bmatrix} 4 & 1 \\ 2 & 3 \end{bmatrix}$

**10.** $B = \begin{bmatrix} 5 & -1 \\ 2 & 3 \end{bmatrix}$

**11.** $C = \begin{bmatrix} 2 & 2 \\ 1 & 3 \end{bmatrix}$

**12.** $D = \begin{bmatrix} 1 & -1 \\ 1 & 3 \end{bmatrix}$

(This one has a repeated eigenvalue — can you spot it before computing?)

**13.** $E = \begin{bmatrix} 0 & -1 \\ 1 & 0 \end{bmatrix}$ (the $90°$ rotation matrix)

(The eigenvalues will be complex: $\lambda = \pm i$. This confirms problem 3.)

---

**14.** For any $2 \times 2$ matrix, the eigenvalues satisfy:
$$\lambda_1 + \lambda_2 = \text{tr}(A) \quad \text{and} \quad \lambda_1 \cdot \lambda_2 = \det(A)$$

Verify these relationships for the matrices in problems 9 and 11.

**15.** If $\det(A) = 0$, what must be true about at least one eigenvalue? What does this say about the invertibility of $A$?

**16.** Find the eigenvalues of a $3 \times 3$ triangular matrix:

$$T = \begin{bmatrix} 2 & 4 & -1 \\ 0 & 3 & 5 \\ 0 & 0 & -1 \end{bmatrix}$$

(Hint: for triangular matrices, the eigenvalues are the diagonal entries — try to see why by computing $\det(T - \lambda I)$.)

**17.** The **characteristic polynomial** of an $n \times n$ matrix has degree $n$, so an $n \times n$ matrix has exactly $n$ eigenvalues (counting multiplicity, and allowing complex values). What does this say about the maximum number of eigenvalues for a $3 \times 3$ matrix?

**18.** A matrix is called **positive definite** if all its eigenvalues are positive. This property is crucial for optimisation (it means the function $f(\mathbf{x}) = \mathbf{x}^T A \mathbf{x}$ has a unique minimum). Is the matrix $\begin{bmatrix} 3 & 1 \\ 1 & 2 \end{bmatrix}$ positive definite?

---

## Part C: Finding Eigenvectors (10 problems)

### The Algorithm

For each eigenvalue $\lambda$, find the eigenvectors by solving $(A - \lambda I)\mathbf{v} = \mathbf{0}$, i.e., row-reducing the matrix $(A - \lambda I)$ with a zero right-hand side.

The solution set is the **eigenspace** for $\lambda$.

---

**Find the eigenvalues and eigenvectors for each matrix:**

**19.** $A = \begin{bmatrix} 4 & 1 \\ 2 & 3 \end{bmatrix}$ (from problem 9)

**20.** $B = \begin{bmatrix} 2 & 2 \\ 1 & 3 \end{bmatrix}$ (from problem 11)

**21.** $C = \begin{bmatrix} 3 & 0 \\ 0 & 5 \end{bmatrix}$ (diagonal — what do you expect?)

**22.** $D = \begin{bmatrix} 2 & 1 \\ 0 & 2 \end{bmatrix}$ (repeated eigenvalue $\lambda = 2$)

(This matrix has only one linearly independent eigenvector. Explain why this is a degenerate case.)

---

**23.** For the matrix $A = \begin{bmatrix} 4 & 1 \\ 2 & 3 \end{bmatrix}$ from problem 19, verify your eigenvectors by substituting back into $A\mathbf{v} = \lambda\mathbf{v}$.

**24.** If $\mathbf{v} = \begin{bmatrix} 1 \\ 1 \end{bmatrix}$ is an eigenvector of $A = \begin{bmatrix} 3 & 1 \\ 1 & 3 \end{bmatrix}$, find the corresponding eigenvalue without solving the characteristic equation. What is the other eigenvalue? What is the other eigenvector?

**25.** A symmetric matrix (like $A$ in problem 24) always has:
- Real eigenvalues
- Eigenvectors corresponding to different eigenvalues that are **perpendicular** (orthogonal)

Verify the perpendicularity of the eigenvectors in problem 24 by checking their dot product.

**26.** The **spectral radius** of a matrix is $\rho(A) = \max|\lambda_i|$ (the largest absolute eigenvalue). For the Dublin weather Markov chain matrix $P = \begin{bmatrix} 0.7 & 0.3 \\ 0.4 & 0.6 \end{bmatrix}$:

- (a) Find the eigenvalues of $P$.
- (b) What is $\rho(P)$?
- (c) One eigenvalue is exactly 1. What is the corresponding eigenvector? Compare to the stationary distribution from ws07d.

**27.** 🤖 **Covariance and PCA.** The covariance matrix $\Sigma = \begin{bmatrix} 4 & 2 \\ 2 & 3 \end{bmatrix}$ describes the spread of a 2D dataset. Find its eigenvalues and eigenvectors. The eigenvector with the largest eigenvalue is the **principal component** — the direction of maximum variance. Which direction is it?

**28.** For problem 27, the eigenvalues tell you how much variance lies in each principal direction. What fraction of the total variance is captured by the first principal component? (Divide the largest eigenvalue by the sum of all eigenvalues.)

---

## Part D: Diagonalisation (8 problems)

### Why It Matters

If $A$ has $n$ linearly independent eigenvectors $\mathbf{v}_1, \ldots, \mathbf{v}_n$ with eigenvalues $\lambda_1, \ldots, \lambda_n$, then:

$$A = P \Lambda P^{-1}$$

where $P = [\mathbf{v}_1 \mid \cdots \mid \mathbf{v}_n]$ (eigenvectors as columns) and $\Lambda = \text{diag}(\lambda_1, \ldots, \lambda_n)$.

This is incredibly useful because: $A^k = P \Lambda^k P^{-1}$, and $\Lambda^k$ is just raising the diagonal entries to the power $k$.

---

**29.** For $A = \begin{bmatrix} 4 & 1 \\ 2 & 3 \end{bmatrix}$ (problem 19), form the matrix $P$ from its eigenvectors and the diagonal matrix $\Lambda$. Verify $A = P\Lambda P^{-1}$ (you may use the inverse formula from ws07a).

**30.** Use diagonalisation to compute $A^3$ for the matrix in problem 29. (Compute $P\Lambda^3 P^{-1}$.)

**31.** For the Markov chain matrix $P_{\text{chain}} = \begin{bmatrix} 0.7 & 0.3 \\ 0.4 & 0.6 \end{bmatrix}$:

- (a) Diagonalise it using the eigenvalues and eigenvectors from problem 26.
- (b) Compute $P_{\text{chain}}^n$ as $n \to \infty$. (The eigenvalue with $|\lambda| < 1$ decays; only the eigenvalue 1 survives.)
- (c) What does $P_{\text{chain}}^\infty$ look like? Does each row equal the stationary distribution?

**32.** Not all matrices are diagonalisable. Problem 22 ($D = \begin{bmatrix} 2 & 1 \\ 0 & 2 \end{bmatrix}$) has a repeated eigenvalue with only one eigenvector. Explain why this prevents diagonalisation.

---

**33.** A **symmetric** matrix is always diagonalisable with real eigenvalues and orthogonal eigenvectors. This is the **Spectral Theorem** — one of the most important results in linear algebra. It means $A = Q \Lambda Q^T$ where $Q$ is orthogonal ($Q^T = Q^{-1}$). Why is the covariance matrix always symmetric? What does the Spectral Theorem guarantee about PCA?

**34.** If $A$ has eigenvalues $\lambda_1$ and $\lambda_2$, what are the eigenvalues of:
- (a) $3A$
- (b) $A + 5I$
- (c) $A^2$
- (d) $A^{-1}$ (if it exists)

**35.** The **trace** equals the sum of eigenvalues and the **determinant** equals the product (from problem 14). For a $3 \times 3$ matrix with eigenvalues $2, -1, 3$:
- (a) What is the trace?
- (b) What is the determinant?
- (c) Is the matrix invertible?

**36.** 🤖 **Dimensionality Reduction.** A dataset has 1000 features. The $1000 \times 1000$ covariance matrix has 1000 eigenvalues. If 95% of the total variance is captured by the top 10 eigenvalues, you can project the data onto those 10 eigenvectors and reduce from 1000 to 10 dimensions. This is PCA.

- (a) Why is this useful for machine learning?
- (b) What is lost by keeping only 10 eigenvectors?
- (c) How does this relate to the rank of a matrix (from ws07b)?

---

## Part E: Connections (4 problems)

**37.** 🌐 **Returning to Markov Chains.** In ws07d you found the stationary distribution $\boldsymbol{\pi}$ by solving $\boldsymbol{\pi} P = \boldsymbol{\pi}$. Show that this is equivalent to finding an eigenvector of $P^T$ with eigenvalue 1. (Transpose both sides of $\boldsymbol{\pi} P = \boldsymbol{\pi}$.)

**38.** 🔧 **Google PageRank.** The PageRank vector is the eigenvector of the web's link matrix corresponding to eigenvalue 1. The matrix is modified slightly (a "damping factor" is added) to ensure the eigenvector is unique. Why would a unique stationary distribution be important for a search engine?

**39.** 🤖 **The SVD.** Every matrix $A$ (even non-square) has a **Singular Value Decomposition** $A = U\Sigma V^T$, where $U$ and $V$ are orthogonal and $\Sigma$ is diagonal with non-negative entries (the **singular values**). The singular values are the square roots of the eigenvalues of $A^T A$. For $A = \begin{bmatrix} 3 & 1 \\ 1 & 3 \\ 1 & 1 \end{bmatrix}$, compute $A^T A$ and find its eigenvalues (hence the singular values of $A$).

**40.** Looking back across Series 7:
- (a) ws07a introduced matrix multiplication. ws07b used row reduction to solve systems. ws07c finds the "natural frame" of a matrix. How do all three relate to the question: *what does this matrix do?*
- (b) The eigenvalue equation $A\mathbf{v} = \lambda \mathbf{v}$ connects to ws04e (optimisation): maximising $\mathbf{x}^T A \mathbf{x}$ subject to $\|\mathbf{x}\| = 1$ gives the largest eigenvector. Explain in words why the direction of maximum stretch is the principal eigenvector.
- (c) The series will continue in ws07d (Markov chains, already covered) and eventually to the SVD. How does each worksheet in Series 7 build on the last?
