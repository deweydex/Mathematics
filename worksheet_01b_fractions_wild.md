# Worksheet 1B: Fractions in the Wild
**AIML Foundations Mathematics**  
**Dublin and Dún Laoghaire ETB**  
**Instructor: Josh Aaron**

---

> **A Note Before You Begin**
> 
> This worksheet contains formulas from physics, machine learning, probability, and information theory. Some of them look intimidating. They're not.
> 
> You don't need to understand what these formulas *do* in their original context. You just need to look at them as fractions and ask: "What happens when this variable gets bigger? Smaller? Approaches[...]"
> 
> This is about building confidence. If you can analyze the behavior of Einstein's equations, you can handle anything.
> 
> **Keep calm. These are just fractions.**

---

## Part A: Physics — Special Relativity

In Einstein's special relativity, several important quantities involve the same fraction pattern.

### The Lorentz Factor

\[\gamma = \dfrac{1}{\sqrt{1 - \dfrac{v^2}{c^2}}} \]

Here:
- $v$ = speed of an object
- $c$ = speed of light (the maximum possible speed)
- The object cannot exceed $c$, so $v < c$ always

**1.** 
- (a) When $v = 0$ (object at rest), what is $\dfrac{v^2}{c^2}$? What is $\gamma$?
- (b) When $v = 0.5c$ (half light speed), what is $\dfrac{v^2}{c^2}$? What is $1 - \dfrac{v^2}{c^2}$?
- (c) As $v$ approaches $c$, what does $\dfrac{v^2}{c^2}$ approach?
- (d) As $v$ approaches $c$, what does $1 - \dfrac{v^2}{c^2}$ approach?
- (e) As $v$ approaches $c$, what happens to $\gamma$?

---

### Time Dilation

A moving clock runs slower. The relationship is:

$$\text{TimeMoving} = \text{TimeStationary} \times \sqrt{1 - \dfrac{v^2}{c^2}}$$

**2.**
- (a) When $v = 0$, how does $\text{TimeMoving}$ compare to $\text{TimeStationary}$?
- (b) As $v \to c$, what happens to $\text{TimeMoving}$?
- (c) In words: as you move faster, does your clock run faster or slower compared to a stationary observer?

---

### Relativistic Energy

$$\text{Energy} = \dfrac{\text{RestMass} \times c^2}{\sqrt{1 - \dfrac{v^2}{c^2}}}$$

**3.**
- (a) When $v = 0$, what is the energy? (This is the famous $E = mc^2$)
- (b) As $v \to c$, what happens to the energy?
- (c) Why does this suggest that nothing with mass can actually reach light speed?

---

### Relativistic Momentum

$$\text{Momentum} = \dfrac{\text{Mass} \times v}{\sqrt{1 - \dfrac{v^2}{c^2}}}$$

**4.**
- (a) When $v$ is very small compared to $c$, the denominator is approximately 1. What does momentum approximately equal?
- (b) As $v \to c$, what happens to momentum?

---

## Part B: Probability — Bayes' Theorem

Bayes' theorem tells us how to update our beliefs when we get new evidence:

$$P(\text{Hypothesis} | \text{Evidence}) = \dfrac{P(\text{Evidence} | \text{Hypothesis}) \times P(\text{Hypothesis})}{P(\text{Evidence})}$$

This reads as: "The probability of our hypothesis *given* the evidence equals..."

Let's use a concrete example: **Medical Testing**

- $P(\text{Disease})$ = probability someone has a disease (let's say it's rare: 1%)
- $P(\text{Positive} | \text{Disease})$ = probability of testing positive if you have the disease (sensitivity: 99%)
- $P(\text{Positive} | \text{NoDisease})$ = probability of testing positive if healthy (false positive rate: 5%)

**5.** The formula becomes:

$$P(\text{Disease} | \text{Positive}) = \dfrac{P(\text{Positive} | \text{Disease}) \times P(\text{Disease})}{P(\text{Positive})}$$

- (a) If the disease is very rare (small $P(\text{Disease})$), what happens to the numerator?
- (b) If the test has many false positives (high $P(\text{Positive} | \text{NoDisease})$), what happens to $P(\text{Positive})$ in the denominator?
- (c) Combining (a) and (b): even with a positive test, why might the probability of actually having a rare disease still be low?

---

## Part C: Information Theory — Entropy and Compression

### Shannon Entropy

The "surprise" or information content of an event is:

$$\text{Surprise}(\text{Event}) = \log_2\left(\dfrac{1}{P(\text{Event})}\right)$$

**8.** 
- (a) If an event is very likely ($P(\text{Event})$ close to 1), what is $\dfrac{1}{P(\text{Event})}$ close to?
- (b) So what happens to the surprise value?
- (c) If an event is very unlikely ($P(\text{Event})$ close to 0), what happens to $\dfrac{1}{P(\text{Event})}$?
- (d) So what happens to the surprise value?
- (e) In plain English: are rare events more or less surprising?

**9.** Average entropy (average surprise) across all possible events:

$$H = \sum_{\text{EachEvent } i} P(\text{Event}_i) \times \log_2\left(\dfrac{1}{P(\text{Event}_i)}\right)$$

Consider a coin flip:
- Fair coin: $P(\text{Heads}) = 0.5$, $P(\text{Tails}) = 0.5$
- Biased coin: $P(\text{Heads}) = 0.99$, $P(\text{Tails}) = 0.01$

- (a) Which coin is more predictable?
- (b) Which coin has lower entropy (less average surprise)?
- (c) Which coin's outcomes could be compressed more efficiently? Why?

---

### Compression Ratio

$$\text{CompressionRatio} = \dfrac{\text{CompressedSize}}{\text{OriginalSize}}$$

**10.**
- (a) If the compressed size is much smaller than the original, is the ratio close to 0 or close to 1?
- (b) What compression ratio means "no compression at all"?
- (c) Can the compression ratio ever be greater than 1? What would that mean?

---

## Part D: Machine Learning Concepts

### The Sigmoid Function

The sigmoid "squashes" any input to a value between 0 and 1:

$$\text{Sigmoid}(x) = \dfrac{1}{1 + e^{-x}}$$

Remember: $e \approx 2.718$, and $e^{-x} = \dfrac{1}{e^x}$

**11.**
- (a) When $x = 0$, what is $e^{-x}$? What is $\text{Sigmoid}(0)$?
- (b) When $x$ is very large and positive, what happens to $e^{-x}$? What does $\text{Sigmoid}$ approximate?
- (c) When $x$ is very large and negative, what happens to $e^{-x}$? What does $\text{Sigmoid}$ approximate?
- (d) Can $\text{Sigmoid}$ ever actually equal 0 or 1 exactly?

**12.** The sigmoid is used to convert "confidence scores" to probabilities. Why is it useful that:
- (a) The output is always between 0 and 1?
- (b) An input of 0 gives output 0.5 (maximum uncertainty)?

...

---
*End of Worksheet 1B*