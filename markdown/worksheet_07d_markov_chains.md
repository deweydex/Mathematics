# Worksheet 7D: Markov Chains — When Probability Meets Matrices
**AIML Foundations Mathematics**
**Dublin and Dún Laoghaire ETB**
**Instructor: Josh Aaron**

---

> **What This Worksheet Is About**
>
> A Markov chain is a system that jumps between states randomly — but in a structured way. The probability of the next state depends **only on the current state**, not on history.
>
> When you write down the transition probabilities as a matrix and multiply by a probability vector, you get matrix multiplication doing real work: predicting the future.
>
> Markov chains power Google's PageRank algorithm, autocomplete systems, financial models, and the inference methods inside language models. This worksheet builds the concept from the ground up.

---

## Part A: States, Transitions, and Transition Matrices (10 problems)

### The Setup

A **Markov chain** has:
- A set of **states** (e.g., Sunny, Rainy; or Web Page A, B, C)
- A **transition probability** $P_{ij}$ = the probability of moving from state $i$ to state $j$
- A **transition matrix** $P$ where each **row** sums to 1

### Example: Dublin Weather

| | Tomorrow Sunny | Tomorrow Rainy |
|---|---|---|
| **Today Sunny** | 0.7 | 0.3 |
| **Today Rainy** | 0.4 | 0.6 |

$$P = \begin{bmatrix} 0.7 & 0.3 \\ 0.4 & 0.6 \end{bmatrix}$$

If today is sunny, the probability of sunshine tomorrow is 0.7 and rain is 0.3.

---

**1.** Using the Dublin weather matrix above:
- (a) If today is rainy, what is the probability of rain tomorrow?
- (b) What is the probability of sunshine tomorrow if today is rainy?
- (c) Verify that each row of $P$ sums to 1.

**2.** A website has three pages: Home (H), Products (P), Contact (C). The transition matrix (probability a visitor goes from one page to another) is:

$$P = \begin{bmatrix} 0.2 & 0.5 & 0.3 \\ 0.1 & 0.6 & 0.3 \\ 0.4 & 0.4 & 0.2 \end{bmatrix}$$

- (a) A visitor is on the Home page. What is the probability they next visit Products?
- (b) A visitor is on Contact. What is the probability they stay on Contact?
- (c) Verify that every row sums to 1.

**3.** A student either studies or procrastinates each hour. If they are studying, there is a 0.8 probability they continue studying next hour. If they are procrastinating, there is a 0.6 probability they start studying. Write the $2 \times 2$ transition matrix $P$.

**4.** Decide which of the following can be a row of a transition matrix:
- (a) $[0.5 \quad 0.5]$
- (b) $[0.3 \quad 0.8]$
- (c) $[1.0 \quad 0.0]$
- (d) $[0.3 \quad 0.4 \quad 0.3]$
- (e) $[0.2 \quad -0.1 \quad 0.9]$

---

### State Vectors

A **state vector** $\boldsymbol{\pi}^{(t)}$ is a row vector where entry $i$ is the probability of being in state $i$ at time $t$.

To find the state vector at time $t+1$: multiply on the right by $P$:

$$\boldsymbol{\pi}^{(t+1)} = \boldsymbol{\pi}^{(t)} P$$

**Example:** If today is definitely sunny, $\boldsymbol{\pi}^{(0)} = [1 \quad 0]$. Then:

$$\boldsymbol{\pi}^{(1)} = [1 \quad 0] \begin{bmatrix} 0.7 & 0.3 \\ 0.4 & 0.6 \end{bmatrix} = [0.7 \quad 0.3]$$

**5.** Start with $\boldsymbol{\pi}^{(0)} = [0 \quad 1]$ (definitely rainy today) and the Dublin weather matrix.
- (a) Compute $\boldsymbol{\pi}^{(1)}$.
- (b) Compute $\boldsymbol{\pi}^{(2)} = \boldsymbol{\pi}^{(1)} P$.

**6.** Start with $\boldsymbol{\pi}^{(0)} = [0.5 \quad 0.5]$ (equal probability) and compute $\boldsymbol{\pi}^{(1)}$ and $\boldsymbol{\pi}^{(2)}$.

**7.** In problem 5, what does $\boldsymbol{\pi}^{(2)}$ represent? Write a sentence interpreting the numbers.

**8.** Note that we use the convention $\boldsymbol{\pi}^{(t+1)} = \boldsymbol{\pi}^{(t)} P$ (row vector times matrix). What would change if we wrote it as $\boldsymbol{\pi}^{(t+1)} = P^T \boldsymbol{\pi}^{(t)}$ instead? Would the answers be the same?

---

**9.** For the student study/procrastination matrix from problem 3, start with $\boldsymbol{\pi}^{(0)} = [1 \quad 0]$ (student is studying).
- (a) Compute $\boldsymbol{\pi}^{(1)}$ and $\boldsymbol{\pi}^{(2)}$.
- (b) Interpret $\boldsymbol{\pi}^{(2)}$ in plain English.

**10.** A fair coin flip can be modelled as a Markov chain with states Heads (H) and Tails (T), where every transition has probability 0.5.
- (a) Write the transition matrix.
- (b) This chain has a special name: it is said to be **i.i.d.** (independent and identically distributed). Why does the Markov property hold trivially for a fair coin?

---

## Part B: Evolving Through Time — Powers of the Transition Matrix (8 problems)

### Two Steps at Once

To find the probability of going from state $i$ to state $j$ in **exactly 2 steps**, compute $P^2 = P \cdot P$.

More generally, $P^n$ gives the $n$-step transition probabilities.

If the initial state vector is $\boldsymbol{\pi}^{(0)}$, then after $n$ steps:

$$\boldsymbol{\pi}^{(n)} = \boldsymbol{\pi}^{(0)} P^n$$

---

**11.** Using the Dublin weather matrix $P = \begin{bmatrix} 0.7 & 0.3 \\ 0.4 & 0.6 \end{bmatrix}$, compute $P^2$.

**12.** Using $P^2$ from problem 11: if today is definitely sunny, what is the probability of sunshine in two days?

**13.** Verify your answer to problem 12 by computing $\boldsymbol{\pi}^{(0)} P^2$ directly, with $\boldsymbol{\pi}^{(0)} = [1 \quad 0]$.

**14.** Also check using the two-step method: $\boldsymbol{\pi}^{(0)} \to \boldsymbol{\pi}^{(1)} \to \boldsymbol{\pi}^{(2)}$ as in Part A. Do you get the same answer? (You should.)

---

**15.** Complete the table by computing $\boldsymbol{\pi}^{(n)}$ for $n = 0, 1, 2, 3, 4$ starting from $\boldsymbol{\pi}^{(0)} = [1 \quad 0]$ (definitely sunny):

| $n$ | Sunny | Rainy |
|-----|-------|-------|
| 0 | 1.000 | 0.000 |
| 1 | 0.700 | 0.300 |
| 2 | | |
| 3 | | |
| 4 | | |

**16.** Looking at the table in problem 15: what do you notice as $n$ increases? Does the distribution seem to be converging to something?

**17.** Now start with $\boldsymbol{\pi}^{(0)} = [0 \quad 1]$ (definitely rainy) and fill in the same table. Compare rows 3 and 4 with those from problem 15.

**18.** This convergence — regardless of where you start — is a key property of well-behaved Markov chains. What does it suggest about long-run predictions?

---

## Part C: The Steady State (10 problems)

### The Long Run

A **stationary distribution** (steady state) is a probability vector $\boldsymbol{\pi}$ such that:

$$\boldsymbol{\pi} P = \boldsymbol{\pi}$$

Once the chain reaches this distribution, it stays there. This is analogous to a fixed point.

### Finding the Steady State

For a $2 \times 2$ matrix with transition matrix $P = \begin{bmatrix} 1-a & a \\ b & 1-b \end{bmatrix}$ (where $a, b > 0$):

$$\boldsymbol{\pi} = \left[\frac{b}{a+b} \quad \frac{a}{a+b}\right]$$

**Alternatively**, solve $\boldsymbol{\pi} P = \boldsymbol{\pi}$ with the constraint that the entries sum to 1.

---

**19.** For the Dublin weather chain, $a = 0.3$ and $b = 0.4$. Use the formula above to find the stationary distribution $\boldsymbol{\pi}$.

**20.** Verify your answer to problem 19 by checking $\boldsymbol{\pi} P = \boldsymbol{\pi}$ directly.

**21.** Does the long-run probability in your table from problem 15 match $\boldsymbol{\pi}$? It should be approaching it.

---

**22.** Find the stationary distribution for the student study/procrastination chain from problem 3 by solving the system:

Let $\boldsymbol{\pi} = [\pi_S \quad \pi_P]$ where $\pi_S + \pi_P = 1$. Write out the equation $\boldsymbol{\pi} P = \boldsymbol{\pi}$ as two simultaneous equations and solve.

**23.** Interpret the stationary distribution from problem 22: in the long run, what fraction of time does the student spend studying?

**24.** For the website problem (problem 2), the stationary distribution satisfies $\boldsymbol{\pi} P = \boldsymbol{\pi}$ with $\pi_H + \pi_P + \pi_C = 1$. Setting up and solving this $3 \times 3$ system would give the long-run fraction of time spent on each page. Explain in plain English why this is useful for a website designer.

---

**25.** A chain is called **absorbing** if some states, once entered, can never be left. For example:

$$P = \begin{bmatrix} 1 & 0 \\ 0.3 & 0.7 \end{bmatrix}$$

State 1 is absorbing (first row: $P_{11} = 1$, $P_{12} = 0$).

- (a) Verify that the chain will eventually be absorbed into state 1 regardless of starting state.
- (b) What would the stationary distribution be for an absorbing chain?

**26.** A random walk on a line has three positions: Left (L), Centre (C), Right (R). From Centre, you go Left or Right with probability 0.5 each. Left and Right are absorbing. Write the transition matrix. What happens in the long run?

---

**27.** The **PageRank** algorithm (which made Google famous) models a random web surfer jumping between pages. The stationary distribution of the resulting Markov chain gives the "importance" of each page. Why is a page important if many other important pages link to it? How does the stationary distribution capture this?

**28.** A Markov chain has this unusual property: every row of $P$ is identical, i.e., $P_{ij} = \pi_j$ for all $i$. What does this say about the chain? What is the stationary distribution? Why is this degenerate?

---

## Part D: Applications — PageRank, Language, and More (10 problems)

**29.** 🌐 **Simplified PageRank.** Three web pages link to each other:
- Page A links to B and C (equal probability)
- Page B links only to A
- Page C links to A and B (equal probability)

- (a) Write the $3 \times 3$ transition matrix.
- (b) Check that each row sums to 1.
- (c) The page with the highest stationary probability is ranked #1. Which page do you predict will rank highest, and why intuitively?

**30.** 📝 **Language Modelling.** A simple bigram model estimates the probability of a word given the previous word. Treat each word as a state and transitions as bigram probabilities.

Given the transition matrix for words {I, like, cats, dogs}:

$$P = \begin{bmatrix} 0 & 0.5 & 0.2 & 0.3 \\ 0.0 & 0 & 0.6 & 0.4 \\ 0.8 & 0.1 & 0 & 0.1 \\ 0.7 & 0.1 & 0.1 & 0.1 \end{bmatrix}$$

- (a) Starting from "I", what is the most likely next word?
- (b) What is the probability of the sequence "I like cats"?
- (c) In a real language model, where does this matrix come from?

**31.** 🧬 **DNA Sequences.** DNA bases transition from one to another with certain probabilities. If the transition matrix for bases {A, T, G, C} is doubly stochastic (every row and column sums to 0.25), what is the stationary distribution? What does this tell you about the long-run composition of a DNA sequence?

**32.** 💰 **A Simple Economic Model.** Each year, a person is in one of three states: Employed (E), Unemployed (U), or Inactive (I).

$$P = \begin{bmatrix} 0.92 & 0.05 & 0.03 \\ 0.30 & 0.50 & 0.20 \\ 0.10 & 0.15 & 0.75 \end{bmatrix}$$

- (a) What is the probability an employed person loses their job within a year?
- (b) What is the probability an unemployed person finds work within a year?
- (c) Describe in words what the entry $P_{32} = 0.15$ means.

---

**33.** 🔁 **Mixing time.** Some Markov chains converge to their stationary distribution very quickly; others take a long time. Looking at the Dublin weather example, the convergence seemed fairly fast. What features of the transition matrix might make convergence slow? (Think about what happens if most of the probability stays on the diagonal.)

**34.** 🤖 **Reinforcement Learning Connection.** In reinforcement learning, an agent moves between states and collects rewards. The dynamics are described by a Markov Decision Process (MDP). Why is the Markov property — that the next state depends only on the current state, not history — important for the algorithms to work?

**35.** 📊 **Ergodicity.** A chain is **ergodic** if it is possible to get from any state to any other state. Examine the following transition matrix and determine whether it is ergodic:

$$P = \begin{bmatrix} 0.5 & 0.5 & 0 \\ 0 & 0.3 & 0.7 \\ 0.6 & 0 & 0.4 \end{bmatrix}$$

(Try to trace a path from state 1 to state 3 and from state 3 to state 1.)

**36.** Looking back at this worksheet:
- (a) In ws07a you multiplied a row vector by a matrix. Where does exactly that operation appear here?
- (b) In ws06a you calculated basic probabilities. How does a Markov chain extend basic probability to sequences of events?
- (c) Why does the stationary distribution $\boldsymbol{\pi} P = \boldsymbol{\pi}$ look like an **eigenvector** equation? (We will explore eigenvectors fully in ws07c.)
