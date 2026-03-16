# Worksheet 7B: Linear Systems and Gaussian Elimination
**AIML Foundations Mathematics**
**Dublin and Dún Laoghaire ETB**
**Instructor: Josh Aaron**

---

> **What This Worksheet Is About**
>
> In ws07a you learned that a system of equations can be written as $A\mathbf{x} = \mathbf{b}$, and that one way to solve it is to compute $A^{-1}\mathbf{b}$.
>
> But computing an inverse is expensive — and sometimes impossible. Gaussian elimination is the systematic, efficient method that computers actually use. It works by row-reducing a matrix to a simpler form where the solution can be read off directly.
>
> It also reveals something deeper: not every system has a unique solution. Some have none. Some have infinitely many. Understanding which case you're in — and why — is fundamental to data fitting, machine learning, and numerical computing.

---

## Part A: Augmented Matrices (8 problems)

### From System to Matrix

A system of linear equations can be written as an **augmented matrix** $[A \mid \mathbf{b}]$ — the coefficient matrix $A$ with the right-hand-side vector $\mathbf{b}$ appended as an extra column.

$$\begin{cases} 2x + 3y = 7 \\ x - y = 1 \end{cases} \quad \longrightarrow \quad \left[\begin{array}{cc|c} 2 & 3 & 7 \\ 1 & -1 & 1 \end{array}\right]$$

No information is lost — the augmented matrix carries the complete system.

---

**Write each system as an augmented matrix:**

**1.** $3x - 2y = 5$ and $x + 4y = -3$

**2.** $x + y + z = 6$, $2x - y + 3z = 11$, $x + 2y - z = 2$

**3.** $4x = 12$ and $x + y = 7$ and $y - z = 1$

**4.** $2x_1 - x_2 + 3x_3 - x_4 = 4$ and $x_1 + 2x_2 - x_3 + x_4 = 1$ (a system in 4 unknowns)

---

**Read each augmented matrix and write the system of equations it represents:**

**5.** $\left[\begin{array}{cc|c} 1 & -3 & 5 \\ 0 & 1 & -2 \end{array}\right]$

**6.** $\left[\begin{array}{ccc|c} 1 & 0 & 2 & 4 \\ 0 & 1 & -1 & 3 \\ 0 & 0 & 1 & 2 \end{array}\right]$

**7.** $\left[\begin{array}{ccc|c} 1 & 0 & 0 & 5 \\ 0 & 1 & 0 & -2 \\ 0 & 0 & 1 & 3 \end{array}\right]$

What is the solution immediately from problem 7? (Explain why this form is so useful.)

**8.** A model with 3 parameters $w_1, w_2, w_3$ is trained on 3 data points, giving the system:
$$w_1 + 2w_2 + w_3 = 5, \quad 2w_1 - w_2 + 3w_3 = 8, \quad w_1 + w_2 - w_3 = 1$$

Write the augmented matrix.

---

## Part B: Row Operations (10 problems)

### The Three Legal Moves

When solving a system, these operations produce an equivalent system (same solution set):

1. **Swap** two rows: $R_i \leftrightarrow R_j$
2. **Scale** a row by a non-zero constant: $kR_i \to R_i$
3. **Replace** a row by itself plus a multiple of another: $R_i + kR_j \to R_i$

The goal is to reach **row echelon form (REF):** a staircase of leading entries (pivots), with zeros below each pivot.

---

**Perform the indicated row operation:**

**9.** Starting from $\left[\begin{array}{cc|c} 2 & 4 & 6 \\ 3 & -1 & 5 \end{array}\right]$, apply $\frac{1}{2}R_1 \to R_1$.

**10.** Starting from $\left[\begin{array}{cc|c} 1 & 2 & 3 \\ 3 & -1 & 5 \end{array}\right]$, apply $R_2 - 3R_1 \to R_2$.

**11.** Starting from $\left[\begin{array}{ccc|c} 1 & 2 & -1 & 4 \\ 0 & 3 & 2 & 7 \\ 2 & -1 & 3 & 1 \end{array}\right]$, apply $R_3 - 2R_1 \to R_3$.

---

**Use row operations to bring each matrix to row echelon form:**

**12.** $\left[\begin{array}{cc|c} 2 & 6 & 10 \\ 1 & 2 & 4 \end{array}\right]$

**13.** $\left[\begin{array}{ccc|c} 1 & 2 & 1 & 4 \\ 2 & 1 & -1 & 1 \\ 1 & -1 & 2 & 3 \end{array}\right]$

**14.** $\left[\begin{array}{ccc|c} 0 & 1 & 2 & 5 \\ 1 & 3 & -1 & 2 \\ 2 & 0 & 1 & 3 \end{array}\right]$

(Hint: swap rows first to get a non-zero entry in the top-left pivot position.)

---

**15.** A matrix is in **row echelon form** if:
- All zero rows are at the bottom.
- Each row's leading entry (pivot) is to the right of the row above's pivot.
- All entries below a pivot are zero.

Identify which of the following are in row echelon form, and why:

- (a) $\begin{bmatrix} 1 & 2 & 3 \\ 0 & 4 & 5 \\ 0 & 0 & 6 \end{bmatrix}$
- (b) $\begin{bmatrix} 1 & 0 & 2 \\ 0 & 0 & 1 \\ 0 & 3 & 4 \end{bmatrix}$
- (c) $\begin{bmatrix} 2 & 1 \\ 0 & 3 \\ 0 & 0 \end{bmatrix}$
- (d) $\begin{bmatrix} 1 & 2 & 0 \\ 0 & 1 & 3 \\ 0 & 0 & 0 \end{bmatrix}$

**16.** Show that the three row operations are **reversible** — i.e., each one can be undone by another row operation of the same type. Why does this guarantee the solution set is unchanged?

**17.** Why is dividing a row by zero not a legal operation? What does this constraint say about pivots?

**18.** In the row operation $R_i + kR_j \to R_i$, we cannot set $i = j$. Why not?

---

## Part C: Back Substitution and Gauss–Jordan Elimination (10 problems)

### From REF to Solution

Once a matrix is in row echelon form, solve **from the bottom up** (back substitution).

**Example:**
$$\left[\begin{array}{ccc|c} 1 & 2 & -1 & 4 \\ 0 & 3 & 1 & 7 \\ 0 & 0 & 2 & 6 \end{array}\right]$$

Row 3: $2z = 6 \Rightarrow z = 3$. Row 2: $3y + 3 = 7 \Rightarrow y = \frac{4}{3}$. Row 1: $x + \frac{8}{3} - 3 = 4 \Rightarrow x = \frac{13}{3}$.

**Gauss–Jordan** goes further: reduce all the way to **reduced row echelon form (RREF)**, where each pivot is 1 and all entries above *and* below each pivot are 0 — then the solution can be read directly.

---

**Solve each system by Gaussian elimination and back substitution:**

**19.** $\begin{cases} x + 2y = 5 \\ 3x - y = 4 \end{cases}$

**20.** $\begin{cases} 2x + y - z = 3 \\ x - y + 2z = 1 \\ 3x + 2y + z = 8 \end{cases}$

**21.** $\begin{cases} x_1 + x_2 + x_3 = 6 \\ 2x_1 - x_2 + 3x_3 = 11 \\ x_1 + 2x_2 - x_3 = 2 \end{cases}$

---

**Use Gauss–Jordan elimination (reduce to RREF) to solve:**

**22.** $\begin{cases} 3x + 6y = 12 \\ x + 2y - z = 4 \\ 2x + 4y + z = 10 \end{cases}$

**23.** $\begin{cases} x + y + z = 6 \\ x - y + z = 2 \\ 2x + y - z = 3 \end{cases}$

---

**24.** Use Gauss–Jordan to find $A^{-1}$ for $A = \begin{bmatrix} 2 & 1 \\ 5 & 3 \end{bmatrix}$ by row-reducing $[A \mid I]$ to $[I \mid A^{-1}]$.

**25.** Explain in words why row-reducing $[A \mid I] \to [I \mid A^{-1}]$ gives the inverse. (What is the row-reduced form saying about the operations applied?)

---

## Part D: Types of Solutions (10 problems)

### Three Possibilities

When you row-reduce, one of three things happens:

1. **Unique solution**: $n$ equations, $n$ unknowns, $n$ non-zero pivot rows. One solution.
2. **No solution** (inconsistent): a row of the form $[0\ 0\ \cdots\ 0 \mid c]$ with $c \neq 0$.
3. **Infinitely many solutions**: fewer pivots than unknowns — some variables are **free** and can take any value.

---

**Classify each system and solve (or explain why no solution exists):**

**26.** $\begin{cases} x + 2y = 3 \\ 2x + 4y = 6 \end{cases}$

**27.** $\begin{cases} x + 2y = 3 \\ 2x + 4y = 7 \end{cases}$

**28.** $\begin{cases} x - y + z = 2 \\ 2x - 2y + 2z = 5 \end{cases}$

**29.** $\begin{cases} x + y + z = 6 \\ x - y + 2z = 5 \\ 2x + 3z = 11 \end{cases}$

**30.** $\begin{cases} x_1 + 2x_2 - x_3 + x_4 = 3 \\ 2x_1 + 4x_2 + x_3 - x_4 = 7 \\ x_1 + 2x_2 + 2x_3 - 2x_4 = 4 \end{cases}$

---

**31.** For a system with 3 equations and 4 unknowns, explain why a **unique** solution is impossible. What are the other two possibilities?

**32.** A homogeneous system ($A\mathbf{x} = \mathbf{0}$) always has at least one solution. What is it? Under what condition does it have infinitely many?

**33.** The **rank** of a matrix is the number of non-zero pivot rows in its row echelon form. For an $m \times n$ matrix $A$:
- If $\text{rank}(A) = n$: unique solution (when consistent).
- If $\text{rank}(A) < n$: infinitely many (or no) solutions.

Find the rank of: (a) $\begin{bmatrix} 2 & 4 \\ 1 & 2 \end{bmatrix}$ (b) $\begin{bmatrix} 1 & 0 & 2 \\ 0 & 1 & 3 \\ 0 & 0 & 1 \end{bmatrix}$ (c) $\begin{bmatrix} 1 & 2 & 0 \\ 0 & 0 & 0 \end{bmatrix}$

**34.** The **null space** (kernel) of $A$ is the set of all solutions to $A\mathbf{x} = \mathbf{0}$. Find the null space of $A = \begin{bmatrix} 1 & 2 & -1 \\ 2 & 4 & -2 \end{bmatrix}$.

**35.** The **column space** of $A$ is the set of all $\mathbf{b}$ for which $A\mathbf{x} = \mathbf{b}$ has a solution. For the matrix in problem 34, which vectors $\mathbf{b} = \begin{bmatrix} b_1 \\ b_2 \end{bmatrix}$ are in the column space?

---

## Part E: Applications (6 problems)

🔬 **Circuit Analysis**

**36.** Kirchhoff's laws give the system:

$$I_1 - I_2 - I_3 = 0, \quad 2I_1 + 3I_2 = 12, \quad 3I_2 - 2I_3 = 6$$

Solve for the currents $I_1, I_2, I_3$.

---

🤖 **AI Connection: Least Squares and Over-determined Systems**

**37.** In practice, we have more equations than unknowns (more data points than parameters). This gives an **over-determined** system $A\mathbf{x} = \mathbf{b}$ with no exact solution. The least-squares solution minimises $\|A\mathbf{x} - \mathbf{b}\|^2$ and satisfies the **normal equations**:

$$A^T A \mathbf{x} = A^T \mathbf{b}$$

Given $A = \begin{bmatrix} 1 & 1 \\ 1 & 2 \\ 1 & 3 \end{bmatrix}$ and $\mathbf{b} = \begin{bmatrix} 1 \\ 2 \\ 4 \end{bmatrix}$:

- (a) Compute $A^T A$ and $A^T \mathbf{b}$.
- (b) Solve the normal equations for $\mathbf{x}$.
- (c) The solution $\mathbf{x} = \begin{bmatrix} w_0 \\ w_1 \end{bmatrix}$ gives the line $y = w_0 + w_1 x$ that best fits the data. Interpret the result.

**38.** In problem 37, each row of $A$ is $[1, x_i]$ and each entry of $\mathbf{b}$ is $y_i$. This is linear regression in matrix form. Why is this an over-determined system? Why can't you just compute $A^{-1}\mathbf{b}$ directly?

---

🧬 **Balancing Chemical Equations**

**39.** Balance the equation $a\ \text{C}_2\text{H}_6 + b\ \text{O}_2 \to c\ \text{CO}_2 + d\ \text{H}_2\text{O}$ by writing conservation equations for each element (C, H, O) and solving the resulting linear system. Set $a = 1$ and solve for $b, c, d$.

---

🌐 **Network Flow**

**40.** A traffic network has four intersections with the following flow (cars per minute):

The incoming and outgoing flows at each intersection must balance. This gives a linear system. Write it down as an augmented matrix and solve. (Use the given diagram: into node A: 50 from outside and $x_3$; out of A: $x_1$ and $x_2$. Into node B: $x_1$; out of B: 30 and $x_4$. Into node C: $x_2$ and $x_4$; out of C: 40. Into node D: $x_3$; out of D: 30 and into A.)

What does the free variable (if any) represent physically?

---

**41.** Looking back at this worksheet:
- (a) In ws07a problem 39 you solved a $2 \times 2$ system using the inverse. For a $100 \times 100$ system, why would Gaussian elimination be preferable?
- (b) The three types of solution (unique / none / infinite) correspond to geometric concepts: two lines intersecting / parallel / coincident. What would the geometric picture be for three planes in 3D?
- (c) The over-determined system in problem 37 is the mathematical foundation of linear regression — one of the most used algorithms in data science. What would change if $A^T A$ were not invertible?
