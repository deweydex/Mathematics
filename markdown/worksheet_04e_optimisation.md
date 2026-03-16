# Worksheet 4E: Optimisation — Calculus Finds the Best Answer
**AIML Foundations Mathematics**
**Dublin and Dún Laoghaire ETB**
**Instructor: Josh Aaron**

---

> **What This Worksheet Is About**
>
> Calculus was invented, in large part, to answer the question: *where is the highest? where is the lowest?*
>
> Every machine learning algorithm, at its core, is doing optimisation: finding the weights that minimise the loss function. Every engineer designing a bridge, every economist maximising profit, every physicist finding the path of least time is doing the same thing.
>
> In this worksheet you will use derivatives — which you built in ws04a through ws04d — to find maximum and minimum values. At the end, you will see exactly how this connects to gradient descent, the algorithm that trains neural networks.

---

## Part A: Critical Points (10 problems)

### Finding Where a Function Turns

A **critical point** of $f(x)$ is a value $x = c$ where either:
- $f'(c) = 0$ (the tangent is horizontal), or
- $f'(c)$ is undefined

A critical point is a **candidate** for a local maximum, local minimum, or neither (a saddle point / inflection point).

---

**Find all critical points of the following functions:**

**1.** $f(x) = x^2 - 6x + 5$

**2.** $g(x) = 2x^3 - 9x^2 + 12x - 4$

**3.** $h(x) = x^4 - 8x^2 + 3$

**4.** $f(x) = x^3$ (this one has a critical point that is neither a max nor a min — do you see why?)

**5.** $f(x) = \frac{x^2 - 1}{x^2 + 1}$ (you will need the quotient rule from ws04a)

---

**6.** $f(x) = e^x - ex$ (where $e \approx 2.718$)

**7.** $f(x) = x - \ln(x)$ for $x > 0$

**8.** $f(x) = \sin(x) + \cos(x)$ on $[0, 2\pi]$

**9.** $f(x) = xe^{-x}$

**10.** $f(x) = \frac{\ln(x)}{x}$ for $x > 0$

---

## Part B: The First and Second Derivative Tests (10 problems)

### Classifying Critical Points

**First Derivative Test:** Check the sign of $f'(x)$ on either side of the critical point.
- If $f'$ goes from positive to negative: **local maximum**
- If $f'$ goes from negative to positive: **local minimum**
- If $f'$ does not change sign: **inflection point** (saddle)

**Second Derivative Test:** At a critical point $c$ where $f'(c) = 0$:
- If $f''(c) > 0$: the function is concave up → **local minimum**
- If $f''(c) < 0$: the function is concave down → **local maximum**
- If $f''(c) = 0$: the test is inconclusive

---

**For each function below, find the critical points and classify them using both the first and second derivative tests:**

**11.** $f(x) = x^2 - 6x + 5$

**12.** $g(x) = 2x^3 - 9x^2 + 12x - 4$

**13.** $h(x) = x^4 - 8x^2 + 3$

**14.** $f(x) = xe^{-x}$

**15.** $f(x) = \frac{\ln(x)}{x}$ for $x > 0$

---

**16.** A function $f$ has $f'(3) = 0$ and $f''(3) = -7$. What can you conclude?

**17.** A function $g$ has $g'(5) = 0$ and $g''(5) = 0$. Give an example showing why the second derivative test is inconclusive here.

**18.** Sketch a rough graph of a function that has:
- A local maximum at $x = -2$
- A local minimum at $x = 1$
- An inflection point at $x = -0.5$

**19.** The function $f(x) = ax^2 + bx + c$ always has exactly one critical point (if $a \neq 0$). Find it and show it's a minimum if $a > 0$ and a maximum if $a < 0$.

**20.** For $f(x) = x^n$ where $n$ is a positive integer: find the critical points and classify them for even $n$ and odd $n$. What pattern do you notice?

---

## Part C: Optimisation Word Problems (12 problems)

### Setting Up Optimisation Problems

**Step 1:** Identify the quantity to be maximised or minimised. Write it as a function.
**Step 2:** Identify any constraints. Use them to reduce to one variable.
**Step 3:** Find critical points. Check which gives a max or min.
**Step 4:** Check the boundary conditions if the domain is restricted.

---

**21.** A farmer has 120 m of fencing and wants to enclose a rectangular field. One side is against a wall (no fencing needed).

- (a) Let $x$ be the width (perpendicular to the wall). Write the area $A(x)$ as a function of $x$.
- (b) Find the dimensions that maximise the area.
- (c) What is the maximum area?

**22.** A box with a square base and no lid must have a volume of 32 m³. The material for the base costs €2/m² and the sides cost €1/m².

- (a) Let $x$ be the side of the base and $h$ the height. Write the volume constraint: $x^2 h = 32$.
- (b) Express the total cost $C$ as a function of $x$ alone.
- (c) Find the dimensions that minimise the cost.

**23.** A can (cylinder) must hold 500 cm³. Minimise the total surface area (the amount of metal needed).

The surface area of a cylinder with radius $r$ and height $h$ is $S = 2\pi r^2 + 2\pi r h$.

- (a) Use the volume constraint $\pi r^2 h = 500$ to eliminate $h$.
- (b) Find the radius and height that minimise $S$.
- (c) What is the ratio $h/r$ at the optimum? (The answer has a nice form.)

**24.** The revenue from selling $x$ items is $R(x) = 50x - 0.5x^2$ (in euros). The cost is $C(x) = 10x + 200$.

- (a) Write the profit function $P(x) = R(x) - C(x)$.
- (b) Find the number of items that maximises profit.
- (c) What is the maximum profit?

---

**25.** 🌉 A ship is 4 km from the nearest point $A$ on a straight coastline. It needs to reach a town that is 9 km along the coast from $A$. The ship can travel at 20 km/h at sea and 30 km/h on land. Where should it land to minimise travel time?

**26.** 📡 A window has the shape of a rectangle topped by a semicircle. The perimeter is fixed at 10 m. Find the dimensions that maximise the area.

**27.** 💡 The total cost of producing $x$ units per day is $C(x) = 0.04x^3 - 0.9x^2 + 10x + 200$ for $0 \leq x \leq 20$.

- (a) Find the marginal cost $C'(x)$.
- (b) Find the minimum of the marginal cost (the most efficient production rate).
- (c) Find the average cost $\bar{C}(x) = C(x)/x$ and find its minimum. (Note: the minimum of average cost occurs where $\bar{C}(x) = C'(x)$.)

---

**28.** 🤖 **ML Connection: Mean Squared Error.** The simplest linear model predicts $\hat{y} = mx$ from one feature. Given three data points $(1, 2)$, $(2, 3)$, $(3, 5)$, the Mean Squared Error is:

$$L(m) = \frac{1}{3}\left[(m - 2)^2 + (2m - 3)^2 + (3m - 5)^2\right]$$

- (a) Expand and simplify $L(m)$.
- (b) Find $\frac{dL}{dm}$ and set it to zero.
- (c) What value of $m$ minimises the MSE? This is the least-squares slope.

**29.** 🤖 **ML Connection: Logistic Regression Loss.** The cross-entropy loss for a single data point with label $y \in \{0, 1\}$ and predicted probability $p$ is:

$$L(p) = -y\ln(p) - (1-y)\ln(1-p), \quad 0 < p < 1$$

For $y = 1$: find the value of $p$ that minimises $L(p)$. (Take $\frac{dL}{dp}$ using the chain rule from ws04c.)

**30.** 🔬 **Physics: Snell's Law.** Light travels from medium 1 (speed $v_1$) to medium 2 (speed $v_2$). By Fermat's Principle, light takes the path of minimum time. Show that minimising the travel time leads to **Snell's law**: $\frac{\sin\theta_1}{v_1} = \frac{\sin\theta_2}{v_2}$.

(Let the boundary be the $x$-axis. The light hits the boundary at position $x$. Write the total travel time and differentiate.)

---

**31.** 🤖 **ML Connection: Regularisation.** Adding a penalty term to the loss is called regularisation:

$$L_{\text{reg}}(m) = L(m) + \lambda m^2$$

where $\lambda > 0$ is a hyperparameter. Using your answer from problem 28, add a regularisation term $\lambda m^2$ and find the new minimising $m$ (called the **ridge regression** solution). How does increasing $\lambda$ change $m$?

**32.** A rectangle is inscribed in a circle of radius 5. Find the dimensions of the rectangle with maximum area. (Let the half-widths be $x$ and $y$; the constraint is $x^2 + y^2 = 25$.)

---

## Part D: Absolute Extrema on Closed Intervals (6 problems)

### Global Maximum and Minimum

On a **closed interval** $[a, b]$, the absolute (global) maximum and minimum are found by:

1. Finding all critical points in $(a, b)$
2. Evaluating $f$ at critical points and at the endpoints $a$ and $b$
3. The largest value is the absolute maximum; the smallest is the absolute minimum

---

**33.** Find the absolute maximum and minimum of $f(x) = x^3 - 3x + 2$ on $[-2, 2]$.

**34.** Find the absolute maximum and minimum of $g(x) = x - \frac{4}{x}$ on $[1, 4]$.

**35.** Find the absolute maximum and minimum of $h(x) = 2\sin(x) + \cos(2x)$ on $[0, \pi]$.

**36.** A temperature sensor records $T(t) = -t^2 + 6t + 10$ (°C) over $t \in [0, 8]$ hours.

- (a) At what time is the temperature highest?
- (b) What are the highest and lowest temperatures during the 8-hour period?

**37.** Prove that among all rectangles with perimeter $P$, the square has the maximum area. (Use the AM-GM inequality or calculus.)

**38.** Why doesn't the extreme value theorem guarantee a maximum and minimum for $f(x) = 1/x$ on the open interval $(0, 1)$? Give an example of the function approaching a limiting value but never reaching it.

---

## Part E: Gradient Descent (8 problems)

### The Algorithm That Trains Neural Networks

When the function has many variables (like millions of neural network weights), we cannot find critical points by setting derivatives to zero and solving. Instead, we **descend** in the direction of steepest decrease, one small step at a time:

$$x_{n+1} = x_n - \alpha \cdot f'(x_n)$$

where $\alpha > 0$ is the **learning rate** (step size).

- If $f'(x_n) > 0$, the function is increasing, so we step left (decrease $x$)
- If $f'(x_n) < 0$, the function is decreasing, so we step right (increase $x$)
- At a minimum, $f'(x_n) = 0$, so we stop

---

**39.** Let $f(x) = x^2$, so $f'(x) = 2x$. Starting at $x_0 = 4$ with $\alpha = 0.1$:

- (a) Compute $x_1 = x_0 - \alpha f'(x_0)$.
- (b) Compute $x_2, x_3, x_4$.
- (c) What value is the sequence approaching?

**40.** Repeat problem 39 with $\alpha = 0.5$. What happens? (Try $x_0 = 4$.)

**41.** Repeat problem 39 with $\alpha = 1.1$. What happens now? Why is a large learning rate dangerous?

**42.** Let $f(x) = (x - 3)^2 + 1$. Starting at $x_0 = 0$ with $\alpha = 0.2$, perform 5 gradient descent steps. At what value does it converge?

---

**43.** The MSE from problem 28 was $L(m) = \frac{14}{3}m^2 - \frac{52}{3}m + \frac{38}{3}$ (or similar). Starting at $m_0 = 0$ and using $\alpha = 0.1$, perform 3 steps of gradient descent. Are you approaching the true minimum you found in problem 28?

**44.** The **learning rate dilemma:**
- (a) If $\alpha$ is too small, what is the problem?
- (b) If $\alpha$ is too large, what is the problem?
- (c) Sketch roughly how $f(x)$ decreases over iterations for $\alpha$ too small, just right, and too large.

**45.** 🤖 **Stochastic Gradient Descent (SGD).** Real training data has millions of examples. Computing the exact gradient over all examples is expensive. SGD approximates the gradient using a random mini-batch. Explain why this is still effective — why does the noisy gradient still point roughly in the right direction?

**46.** 🔗 Looking back across the worksheet series:
- (a) In ws04a you learned that $f'(x) = 0$ at a maximum or minimum. How does gradient descent use this fact, without ever actually solving $f'(x) = 0$?
- (b) In ws04b you learned that $f''(x) > 0$ means the function is concave up, like a bowl. Why does gradient descent always find the minimum of a concave-up (convex) function, regardless of where you start?
- (c) In ws07a you multiplied matrices to compute the forward pass of a neural network. The gradient is also a matrix operation (the Jacobian). What would gradient descent look like in matrix form?
