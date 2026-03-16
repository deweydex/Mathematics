# Worksheet 7A: Introduction to Matrices
**AIML Foundations Mathematics**
**Dublin and Dún Laoghaire ETB**
**Instructor: Josh Aaron**

---

> **What This Worksheet Is About**
>
> A matrix is a rectangular grid of numbers — and it turns out to be one of the most powerful ideas in mathematics.
>
> Matrices let us represent entire systems of equations as a single object, describe geometric transformations, store datasets, and run the computations inside every neural network.
>
> In this worksheet you will learn to read, write, add, multiply, and invert matrices — and start to see why they matter so much.

---

## Part A: Reading and Writing Matrices (8 problems)

### Notation

A matrix is written as a rectangular array enclosed in square brackets. A matrix with $m$ rows and $n$ columns is called an **$m \times n$ matrix**.

The element in row $i$ and column $j$ is written $a_{ij}$.

$$A = \begin{bmatrix} 2 & -1 & 5 \\ 0 & 3 & -4 \end{bmatrix} \quad \text{(a } 2 \times 3 \text{ matrix)}$$

Here $a_{12} = -1$ (row 1, column 2) and $a_{23} = -4$ (row 2, column 3).

A **column vector** is an $n \times 1$ matrix. A **row vector** is a $1 \times n$ matrix.

---

Let $A = \begin{bmatrix} 4 & 7 & -2 \\ 1 & 0 & 6 \\ -3 & 5 & 8 \end{bmatrix}$

**1.** State the dimensions of $A$.

**2.** Find: (a) $a_{11}$ (b) $a_{23}$ (c) $a_{32}$ (d) $a_{33}$

**3.** Write down the second **row** of $A$ as a row vector.

**4.** Write down the third **column** of $A$ as a column vector.

---

**5.** A dataset has 4 training examples and 3 features (height, weight, age). Write a suitable matrix $X$ with made-up values. State its dimensions.

**6.** The identity matrix $I_3$ is a $3 \times 3$ matrix with 1s on the main diagonal and 0s everywhere else. Write out $I_3$.

**7.** The **zero matrix** $O$ is a matrix of all zeros. Write out a $2 \times 3$ zero matrix.

**8.** A matrix is called **square** if $m = n$.
- (a) Which of the following are square? $2 \times 2$, $3 \times 2$, $4 \times 4$, $1 \times 3$
- (b) A **diagonal matrix** has non-zero values only on the main diagonal. Write an example $3 \times 3$ diagonal matrix.

---

## Part B: Addition, Subtraction, and Scalar Multiplication (12 problems)

### The Rules

**Addition:** Add corresponding elements. Only defined when both matrices have the same dimensions.

$$\begin{bmatrix} a & b \\ c & d \end{bmatrix} + \begin{bmatrix} e & f \\ g & h \end{bmatrix} = \begin{bmatrix} a+e & b+f \\ c+g & d+h \end{bmatrix}$$

**Scalar multiplication:** Multiply every element by the scalar $k$.

$$k \begin{bmatrix} a & b \\ c & d \end{bmatrix} = \begin{bmatrix} ka & kb \\ kc & kd \end{bmatrix}$$

---

Let $A = \begin{bmatrix} 3 & -1 \\ 2 & 4 \end{bmatrix}$, $B = \begin{bmatrix} 1 & 5 \\ -3 & 2 \end{bmatrix}$, $C = \begin{bmatrix} 0 & 2 \\ 1 & -1 \end{bmatrix}$

**9.** Compute $A + B$.

**10.** Compute $A - C$.

**11.** Compute $3A$.

**12.** Compute $2B - A$.

**13.** Compute $A + B + C$.

**14.** Is $A + B = B + A$? Verify using the matrices above.

---

**15.** The **transpose** of a matrix $A$, written $A^T$, swaps rows and columns: the element in row $i$, column $j$ of $A$ becomes the element in row $j$, column $i$ of $A^T$.

For $A = \begin{bmatrix} 1 & 2 & 3 \\ 4 & 5 & 6 \end{bmatrix}$, find $A^T$. What are the dimensions of $A^T$?

**16.** A matrix $S$ is called **symmetric** if $S^T = S$.

$$S = \begin{bmatrix} 1 & 4 & 7 \\ 4 & 2 & 5 \\ 7 & 5 & 3 \end{bmatrix}$$

Verify that $S$ is symmetric by computing $S^T$.

---

🤖 **AI Connection: Gradient Updates in Neural Networks**

**17.** In training, the weight matrix $W$ is updated by subtracting a scaled gradient matrix $G$:

$$W_{\text{new}} = W_{\text{old}} - \alpha \cdot G$$

where $\alpha = 0.1$ (the learning rate). Given:

$$W_{\text{old}} = \begin{bmatrix} 0.5 & -0.3 \\ 1.2 & 0.8 \end{bmatrix}, \quad G = \begin{bmatrix} 0.4 & -0.2 \\ 0.6 & 1.0 \end{bmatrix}$$

Compute $W_{\text{new}}$.

**18.** Why does the formula subtract $\alpha \cdot G$ rather than add it? (Hint: think about which direction reduces the loss.)

---

**19.** If $A$ is $3 \times 4$ and $B$ is $3 \times 4$, what are the dimensions of $A + B$? What about $2A - 3B$?

**20.** If $A$ is $2 \times 3$ and $B$ is $3 \times 2$, can you compute $A + B$? Explain why or why not.

---

## Part C: Matrix Multiplication (14 problems)

### The Rule

To multiply $A$ (an $m \times n$ matrix) by $B$ (an $n \times p$ matrix), the **inner dimensions must match** ($n = n$). The result $C = AB$ is an $m \times p$ matrix.

The element $c_{ij}$ is the **dot product** of row $i$ of $A$ with column $j$ of $B$:

$$c_{ij} = \sum_{k=1}^{n} a_{ik} \cdot b_{kj}$$

**Example:**

$$\begin{bmatrix} 2 & 1 \\ 0 & 3 \end{bmatrix} \begin{bmatrix} 4 & -1 \\ 2 & 5 \end{bmatrix} = \begin{bmatrix} 2(4)+1(2) & 2(-1)+1(5) \\ 0(4)+3(2) & 0(-1)+3(5) \end{bmatrix} = \begin{bmatrix} 10 & 3 \\ 6 & 15 \end{bmatrix}$$

---

**21.** Before multiplying, check the dimensions. For each pair, state: (a) whether the product is defined, and (b) if so, the dimensions of the result.

| Left matrix | Right matrix | Defined? | Result size |
|-------------|--------------|----------|-------------|
| $2 \times 3$ | $3 \times 4$ | | |
| $3 \times 2$ | $3 \times 2$ | | |
| $4 \times 1$ | $1 \times 3$ | | |
| $2 \times 2$ | $2 \times 2$ | | |
| $1 \times 4$ | $4 \times 1$ | | |

**22.** Compute $AB$ where $A = \begin{bmatrix} 1 & 2 \\ 3 & 4 \end{bmatrix}$ and $B = \begin{bmatrix} 5 & 0 \\ 1 & -1 \end{bmatrix}$.

**23.** Compute $BA$ using the same matrices. Is $AB = BA$? What does this tell you about matrix multiplication?

**24.** Compute $AI$ where $I = \begin{bmatrix} 1 & 0 \\ 0 & 1 \end{bmatrix}$ and $A$ is from problem 22. What do you notice about $AI$?

---

**25.** Let $A = \begin{bmatrix} 2 & 0 & 1 \\ -1 & 3 & 2 \end{bmatrix}$ and $B = \begin{bmatrix} 1 & 4 \\ 0 & -2 \\ 3 & 1 \end{bmatrix}$. Compute $AB$.

**26.** Let $\mathbf{x} = \begin{bmatrix} 3 \\ -1 \\ 2 \end{bmatrix}$ (a column vector) and $A = \begin{bmatrix} 1 & 0 & -1 \\ 2 & 1 & 0 \end{bmatrix}$. Compute $A\mathbf{x}$.

---

🤖 **AI Connection: The Forward Pass**

**27.** A neural network layer computes $\mathbf{y} = W\mathbf{x} + \mathbf{b}$ where $W$ is the weight matrix, $\mathbf{x}$ is the input vector, and $\mathbf{b}$ is the bias vector.

Given $W = \begin{bmatrix} 0.2 & 0.8 \\ -0.5 & 0.3 \\ 0.1 & 0.6 \end{bmatrix}$, $\mathbf{x} = \begin{bmatrix} 1 \\ 2 \end{bmatrix}$, $\mathbf{b} = \begin{bmatrix} 0.1 \\ -0.2 \\ 0.3 \end{bmatrix}$

Compute $W\mathbf{x}$ and then $W\mathbf{x} + \mathbf{b}$.

**28.** In the above example, what are the dimensions of $W$, $\mathbf{x}$, and the output $\mathbf{y}$? If the next layer has 2 output neurons, what would the dimensions of the next weight matrix need to be?

---

🔬 **Science Connection: Simultaneous Equations as Matrix Equations**

The system $\begin{cases} 2x + 3y = 7 \\ x - y = 1 \end{cases}$ can be written as $\begin{bmatrix} 2 & 3 \\ 1 & -1 \end{bmatrix} \begin{bmatrix} x \\ y \end{bmatrix} = \begin{bmatrix} 7 \\ 1 \end{bmatrix}$ or $A\mathbf{x} = \mathbf{b}$.

**29.** Write each system as a matrix equation $A\mathbf{x} = \mathbf{b}$:

- (a) $3x - 2y = 5$ and $x + 4y = -3$
- (b) $x + y + z = 6$, $2x - y + 3z = 11$, $x + 2y - z = 2$

**30.** Verify that $\mathbf{x} = \begin{bmatrix} 2 \\ 1 \end{bmatrix}$ is the solution to the system in problem 29(a) by computing $A\mathbf{x}$ and checking it equals $\mathbf{b}$.

---

**31.** Compute $(A + B)C$ and $AC + BC$ for:

$$A = \begin{bmatrix} 1 & 0 \\ 2 & -1 \end{bmatrix}, \quad B = \begin{bmatrix} 3 & 1 \\ -1 & 2 \end{bmatrix}, \quad C = \begin{bmatrix} 2 & -1 \\ 0 & 3 \end{bmatrix}$$

What property does this demonstrate?

**32.** True or false (and briefly explain):
- (a) Matrix multiplication is commutative: $AB = BA$ always.
- (b) Matrix multiplication is associative: $(AB)C = A(BC)$ always.
- (c) Multiplying any matrix by the identity matrix leaves it unchanged.

---

**33.** A dataset has 100 examples, each with 5 features. The feature matrix $X$ has shape $100 \times 5$ and the weight vector $\mathbf{w}$ has shape $5 \times 1$. What is the shape of the prediction vector $\hat{\mathbf{y}} = X\mathbf{w}$? What does each entry of $\hat{\mathbf{y}}$ represent?

**34.** A transformation matrix $R = \begin{bmatrix} 0 & -1 \\ 1 & 0 \end{bmatrix}$ rotates vectors by $90°$ anticlockwise. Apply $R$ to the vector $\begin{bmatrix} 1 \\ 0 \end{bmatrix}$ and to $\begin{bmatrix} 0 \\ 1 \end{bmatrix}$. Does the result match your geometric expectation?

---

## Part D: Determinants and Inverses (10 problems)

### Determinants

For a $2 \times 2$ matrix: $\det\begin{bmatrix} a & b \\ c & d \end{bmatrix} = ad - bc$

For a $3 \times 3$ matrix, expand along the first row:

$$\det\begin{bmatrix} a & b & c \\ d & e & f \\ g & h & i \end{bmatrix} = a(ei - fh) - b(di - fg) + c(dh - eg)$$

**The determinant tells you whether a matrix is invertible:** if $\det(A) = 0$, there is no inverse. If $\det(A) \neq 0$, $A$ is invertible.

### Inverse of a $2 \times 2$ Matrix

$$A^{-1} = \frac{1}{\det(A)} \begin{bmatrix} d & -b \\ -c & a \end{bmatrix}$$

If $A^{-1}$ exists, then $AA^{-1} = A^{-1}A = I$.

---

**35.** Compute the determinant of each matrix:

- (a) $\begin{bmatrix} 3 & 2 \\ 1 & 4 \end{bmatrix}$
- (b) $\begin{bmatrix} 5 & -1 \\ 10 & -2 \end{bmatrix}$
- (c) $\begin{bmatrix} 2 & 0 & 1 \\ -1 & 3 & 2 \\ 4 & -2 & 1 \end{bmatrix}$

**36.** For matrix (a) in problem 35, find $A^{-1}$ using the formula above.

**37.** Verify your answer to problem 36 by computing $AA^{-1}$. You should get $I$.

**38.** For matrix (b) in problem 35, the determinant is zero. Explain geometrically why this matrix has no inverse. (Hint: what does $\det = 0$ say about the two rows?)

---

**39.** Solve the system $A\mathbf{x} = \mathbf{b}$ by computing $\mathbf{x} = A^{-1}\mathbf{b}$:

$$A = \begin{bmatrix} 2 & 1 \\ 5 & 3 \end{bmatrix}, \quad \mathbf{b} = \begin{bmatrix} 4 \\ 9 \end{bmatrix}$$

**40.** The **condition number** of a matrix measures how sensitive the solution $A^{-1}\mathbf{b}$ is to small errors in $\mathbf{b}$. A matrix with determinant near zero is called **ill-conditioned**. Why would this be a problem when training a machine learning model?

---

**41.** A $2 \times 2$ transformation matrix scales the $x$-axis by 3 and the $y$-axis by 2. Write this matrix, find its determinant, and explain what the determinant tells you about area scaling.

**42.** If $\det(A) = 5$ and $\det(B) = 3$ (both $2 \times 2$), what is $\det(AB)$? (Use the rule $\det(AB) = \det(A)\det(B)$.)

---

**43.** The **trace** of a square matrix is the sum of its diagonal elements: $\text{tr}(A) = \sum_i a_{ii}$.

Find the trace of: (a) $\begin{bmatrix} 4 & 2 \\ -1 & 7 \end{bmatrix}$ (b) $\begin{bmatrix} 1 & 0 & 3 \\ 2 & 5 & -1 \\ 0 & 4 & 2 \end{bmatrix}$

**44.** The trace and determinant of a $2 \times 2$ matrix are related to its **eigenvalues** $\lambda_1, \lambda_2$ (covered in a later worksheet) by: $\text{tr}(A) = \lambda_1 + \lambda_2$ and $\det(A) = \lambda_1 \lambda_2$. If a matrix has $\text{tr}(A) = 5$ and $\det(A) = 6$, what are its eigenvalues?

---

## Part E: Matrices in Context (6 problems)

**45.** A confusion matrix from an image classifier looks like this:

$$C = \begin{bmatrix} 850 & 30 & 20 \\ 15 & 920 & 25 \\ 10 & 20 & 970 \end{bmatrix}$$

Rows represent true labels (Cat, Dog, Bird); columns represent predicted labels.

- (a) How many cats were correctly classified?
- (b) How many dogs were misclassified as birds?
- (c) What is the overall accuracy? (Hint: sum of diagonal / sum of all elements.)

**46.** A **covariance matrix** $\Sigma$ summarises how features vary together. For two features:

$$\Sigma = \begin{bmatrix} \sigma_1^2 & \sigma_{12} \\ \sigma_{12} & \sigma_2^2 \end{bmatrix}$$

where $\sigma_1^2$ and $\sigma_2^2$ are variances and $\sigma_{12}$ is the covariance. Given $\Sigma = \begin{bmatrix} 4 & 2 \\ 2 & 9 \end{bmatrix}$:

- (a) What are the standard deviations of each feature?
- (b) Is $\Sigma$ symmetric? Why must a covariance matrix always be symmetric?

**47.** The **softmax** function used in neural network output layers can be applied to a vector. Given a score vector $\mathbf{z} = \begin{bmatrix} 2.0 \\ 1.0 \\ 0.5 \end{bmatrix}$, compute $e^{z_i}$ for each element and then normalise so the entries sum to 1. (Use $e^2 \approx 7.39$, $e^1 \approx 2.72$, $e^{0.5} \approx 1.65$.)

**48.** A **stochastic vector** has non-negative entries that sum to 1. Which of the following are stochastic vectors?

- (a) $\begin{bmatrix} 0.3 \\ 0.5 \\ 0.2 \end{bmatrix}$
- (b) $\begin{bmatrix} 0.6 \\ -0.1 \\ 0.5 \end{bmatrix}$
- (c) $\begin{bmatrix} 1 \\ 0 \\ 0 \end{bmatrix}$
- (d) $\begin{bmatrix} 0.4 \\ 0.4 \\ 0.3 \end{bmatrix}$

**49.** A **doubly stochastic matrix** has all entries non-negative, every row sums to 1, and every column sums to 1. Give an example of a $2 \times 2$ doubly stochastic matrix.

**50.** Looking back at this worksheet:
- (a) In which worksheet did you first encounter the idea of solving two simultaneous equations? How does $A\mathbf{x} = \mathbf{b}$ generalise that?
- (b) In ws02a you computed dot products of vectors. Where does a dot product appear in matrix multiplication?
- (c) The formula for gradient descent is $\mathbf{w} \leftarrow \mathbf{w} - \alpha \nabla L$. Why does this require matrix operations when there are many weights?
