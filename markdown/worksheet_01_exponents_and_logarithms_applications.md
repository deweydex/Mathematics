# Worksheet 01: Exponents and Logarithms in Science and Technology

**AIML Foundations Mathematics**  
**Dublin and Dún Laoghaire ETB**  
**Instructor: Josh Aaron**

---

> **A Note Before You Begin**
> 
> This worksheet explores real-world applications of exponents and logarithms in science and technology. You don't need to fully understand the underlying physics or technology. Focus on the mathematical relationships in the examples provided.
> 
> **Keep calm and solve on.**

---

## Part A: Physics — Radioactive Decay and Half-Life

The decay of a radioactive substance follows the equation:

$$N(t) = N_0 e^{-\lambda t}$$

Here:
- $N_0$ is the initial amount
- $N(t)$ is the amount remaining after time $t$
- $\lambda$ is the decay constant
- $t$ is time

**1.** A certain substance starts with $N_0 = 100$ grams and has a decay constant of $\lambda = 0.1$ per year. How much remains after:
- (a) 1 year?
- (b) 5 years?
- (c) 10 years?

**2.** Solve for the half-life $T_{1/2}$ in terms of $\lambda$ using the formula $N(T_{1/2}) = \frac{N_0}{2}$.

**3.** Carbon-14 has a half-life of 5730 years. What is the decay constant $\lambda$? *(Use the result from Question 2.)*

---

## Part B: Astronomy — Apparent Magnitude of Stars

The brightness of a star as seen from Earth is given by:

$$m = -2.5 \log_{10}\left( \frac{I}{I_0} \right)$$

Here:
- $m$ is the apparent magnitude
- $I$ is the intensity of the light received on Earth
- $I_0$ is a reference intensity

**4.** If a star’s intensity is 100 times fainter than $I_0$, what is its magnitude $m$?

**5.** Two stars have magnitudes $m_1 = 1$ and $m_2 = 6$. How many times brighter is the first star compared to the second?

---

## Part C: Engineering — Decibels and Sound Intensity

The loudness of sound is measured in decibels (dB):

$$L = 10 \log_{10}\left( \frac{I}{I_0} \right)$$

Here:
- $L$ is the sound level in decibels
- $I$ is the intensity of the sound (watts per square meter)
- $I_0$ is the reference intensity ($10^{-12}$ W/m²)

**6.** A sound has intensity $I = 10^{-6}$ W/m². What is its decibel level $L$?

**7.** If a sound is 1000 times more intense than another, how much louder is it in decibels? *(Hint: Use the ratio $\frac{I_1}{I_0}$.)*

---

## Part D: Technology — Computing Time Complexity

The time to complete a task in computing sometimes grows exponentially:

$$T(n) = 2^n$$

Here:
- $T(n)$ is the time (in seconds) for input size $n$

**8.** If $T(10) = 1024$ seconds, what is $T(20)$? *(Compare the growth rate.)*

**9.** Solve for $n$ when $T(n) = 2048$.

The logarithm base 2 is often used in algorithms:

**10.** The runtime of an algorithm is $T(n) = \log_2(n)$. Solve for $n$ when:
- (a) $T(n) = 10$
- (b) $T(n) = 20$

---

## Part E: Biology — Population Growth

The population of bacteria grows exponentially:

$$P(t) = P_0 e^{rt}$$

Here:
- $P_0$ is the initial population
- $P(t)$ is the population after time $t$
- $r$ is the growth rate

**11.** A colony starts with $P_0 = 500$ bacteria and doubles every hour. What is the growth rate $r$? *(Hint: Use $P(T_{2x}) = 2P_0$ to find $r$.)*

**12.** How many bacteria are there after 5 hours?

---

## Part F: Information Theory — Shannon Entropy

The surprise (or information content) of an event is:

$$H = -\sum P(x) \log_2(P(x))$$

**13.** Consider a coin toss where $P(Heads) = 0.5$ and $P(Tails) = 0.5$.
- Calculate the entropy $H$.

**14.** Suppose the coin is biased, with $P(Heads) = 0.8$ and $P(Tails) = 0.2$.
- Recalculate the entropy $H$. Is there more uncertainty or less?

---

## Answer Key

A detailed key for all problems will be provided in class discussions.