# Worksheet 8A: Conditional Probability and Bayes' Theorem
**AIML Foundations Mathematics**
**Dublin and Dún Laoghaire ETB**
**Instructor: Josh Aaron**

---

> **What This Worksheet Is About**
>
> In ws06a you calculated the probability of a single event. But most interesting questions in life and in AI involve **knowing something already**.
>
> *"What is the probability this email is spam, given it contains the word 'winner'?"*
> *"What is the probability a patient has a disease, given a positive test result?"*
>
> These are questions about **conditional probability**. Bayes' Theorem — the central formula of this worksheet — is arguably the most important formula in all of machine learning. It lets us update our beliefs in light of new evidence.

---

## Part A: Conditional Probability — $P(A \mid B)$ (10 problems)

### The Definition

The **conditional probability** of event $A$ given that event $B$ has occurred is:

$$P(A \mid B) = \frac{P(A \cap B)}{P(B)} \quad \text{provided } P(B) > 0$$

Here $P(A \cap B)$ is the probability that **both** $A$ and $B$ occur.

Equivalently: $P(A \cap B) = P(A \mid B) \cdot P(B)$ — this is the **multiplication rule**.

---

**1.** A bag contains 4 red and 6 blue marbles. You draw two marbles without replacement.

- (a) What is the probability the first marble is red?
- (b) Given the first marble was red, what is the probability the second is also red?
- (c) What is the probability both marbles are red?

**2.** A class has 30 students. 18 study maths, 12 study French, and 6 study both.

- (a) What is the probability a randomly chosen student studies maths?
- (b) Given a student studies maths, what is the probability they also study French?
- (c) Given a student studies French, what is the probability they also study maths?

**3.** Roll two fair dice. Let $A$ = "the sum is 8" and $B$ = "the first die shows 4".

- (a) Without any information, what is $P(A)$? (Count the favourable outcomes.)
- (b) Given $B$ (first die is 4), what are the possible outcomes? What is $P(A \mid B)$?
- (c) Is $P(A \mid B) > P(A)$? Explain intuitively why.

---

**4.** A tech company's employees are categorised by role and gender:

| | Engineer | Designer | Manager | Total |
|---|---|---|---|---|
| Female | 60 | 40 | 20 | 120 |
| Male | 90 | 20 | 30 | 140 |
| **Total** | 150 | 60 | 50 | 260 |

Find:
- (a) $P(\text{Engineer})$
- (b) $P(\text{Female} \mid \text{Engineer})$
- (c) $P(\text{Engineer} \mid \text{Female})$
- (d) $P(\text{Manager} \mid \text{Male})$
- (e) Are the events "Female" and "Engineer" independent? (Check: is $P(\text{Female} \mid \text{Engineer}) = P(\text{Female})$?)

---

**5.** From a standard deck of 52 cards, one card is drawn. Let $A$ = "the card is a King" and $B$ = "the card is a face card" (Jack, Queen, King — 12 face cards total).

- (a) Find $P(A)$, $P(B)$, and $P(A \cap B)$.
- (b) Find $P(A \mid B)$ and $P(B \mid A)$.
- (c) Interpret $P(A \mid B)$: if you know the card is a face card, how does that change the probability it's a King?

**6.** A factory produces components. 5% of components are defective. A quality control test correctly identifies a defective component 90% of the time, and incorrectly flags a good component 2% of the time. Without using Bayes' Theorem yet, just set up the problem:

- (a) Let $D$ = "defective" and $+$ = "test positive". Write down $P(D)$, $P(D^c)$, $P(+ \mid D)$, $P(+ \mid D^c)$.
- (b) Using the multiplication rule, compute $P(D \cap +)$ and $P(D^c \cap +)$.

---

**7.** The **complement rule for conditional probability**: $P(A^c \mid B) = 1 - P(A \mid B)$.

Verify this makes sense using the following: in problem 4, given the employee is Female, what is the probability they are **not** an Engineer? Check two ways: directly from the table and using the complement rule.

**8.** The **chain rule** extends the multiplication rule to three events:

$$P(A \cap B \cap C) = P(A) \cdot P(B \mid A) \cdot P(C \mid A \cap B)$$

A deck of cards. You draw three cards without replacement. Find the probability all three are Aces.

**9.** Two events $A$ and $B$ have $P(A) = 0.4$, $P(B) = 0.5$, and $P(A \cap B) = 0.2$.

- (a) Find $P(A \mid B)$ and $P(B \mid A)$.
- (b) Are $A$ and $B$ independent? (Check whether $P(A \mid B) = P(A)$.)

**10.** If $P(A \mid B) = 0.6$ and $P(B) = 0.3$, find $P(A \cap B)$.

---

## Part B: Independence (8 problems)

### Independence

Events $A$ and $B$ are **independent** if knowing $B$ occurred gives no information about $A$:

$$P(A \mid B) = P(A) \quad \Longleftrightarrow \quad P(A \cap B) = P(A) \cdot P(B)$$

This is the multiplication rule **simplified for independent events**.

---

**11.** A fair coin is flipped twice. Let $A$ = "first flip is Heads" and $B$ = "second flip is Heads".

- (a) Find $P(A)$, $P(B)$, and $P(A \cap B)$.
- (b) Verify independence: is $P(A \cap B) = P(A) \cdot P(B)$?

**12.** From the company table in problem 4, are "Female" and "Designer" independent? Compute both $P(\text{Female} \cap \text{Designer})$ and $P(\text{Female}) \cdot P(\text{Designer})$ and compare.

**13.** A sensor fails with probability 0.01 on any given day, independently of other days.

- (a) What is the probability the sensor works for 5 consecutive days?
- (b) What is the probability the sensor fails at least once in 5 days?
- (c) What is the probability the sensor fails on exactly day 3?

**14.** Three independent events $A$, $B$, $C$ each have probability 0.5. What is the probability all three occur?

**15.** **Mutual independence vs. pairwise independence.** Consider three events where any two are independent but all three together are not. Give an example with two coin flips: $A$ = "first flip H", $B$ = "second flip H", $C$ = "both flips the same". Show that $A$ and $B$ are independent, $A$ and $C$ are independent, but $P(A \cap B \cap C) \neq P(A)P(B)P(C)$.

---

**16.** 🤖 **Naïve Bayes assumption.** A spam filter treats each word in an email as an independent indicator of spam. Given an email contains the words "winner", "free", and "click", and assuming independence:

$$P(\text{spam} \mid \text{winner, free, click}) \propto P(\text{winner} \mid \text{spam}) \cdot P(\text{free} \mid \text{spam}) \cdot P(\text{click} \mid \text{spam}) \cdot P(\text{spam})$$

If $P(\text{spam}) = 0.3$, $P(\text{winner} \mid \text{spam}) = 0.8$, $P(\text{free} \mid \text{spam}) = 0.7$, $P(\text{click} \mid \text{spam}) = 0.6$, calculate the unnormalised spam score.

**17.** Continuing problem 16, the corresponding "not spam" probabilities are $P(\text{winner} \mid \neg\text{spam}) = 0.05$, $P(\text{free} \mid \neg\text{spam}) = 0.2$, $P(\text{click} \mid \neg\text{spam}) = 0.3$. Calculate the unnormalised not-spam score.

**18.** Using problems 16 and 17, normalise to find $P(\text{spam} \mid \text{winner, free, click})$. (Divide spam score by the sum of spam and not-spam scores.) Would this email be classified as spam?

---

## Part C: The Law of Total Probability (8 problems)

### Partitions and Total Probability

If events $B_1, B_2, \ldots, B_n$ partition the sample space (they are mutually exclusive and exhaustive), then for any event $A$:

$$P(A) = \sum_{i=1}^{n} P(A \mid B_i) \cdot P(B_i)$$

This is the **Law of Total Probability**. It says: to find $P(A)$, consider all the ways $A$ can happen.

---

**19.** A factory has two machines, M1 and M2. M1 produces 60% of components and has a 3% defect rate. M2 produces 40% and has a 5% defect rate.

- (a) Write $P(D \mid M_1)$, $P(D \mid M_2)$, $P(M_1)$, $P(M_2)$.
- (b) Use the law of total probability to find $P(D)$ — the overall defect rate.

**20.** A email arrives. 40% of emails are work emails, 35% are personal, and 25% are spam. The probability of containing the word "urgent" is 0.3 for work, 0.1 for personal, and 0.6 for spam.

- (a) Find $P(\text{"urgent"})$ using the law of total probability.
- (b) Interpret this number: roughly what fraction of all emails contain "urgent"?

**21.** A diagnostic test is given to a population where 2% have a disease. The test has:
- Sensitivity (true positive rate): $P(+ \mid D) = 0.95$
- Specificity (true negative rate): $P(- \mid D^c) = 0.90$

Compute $P(+)$, the overall probability of a positive test.

**22.** In problem 21, compute $P(-)$ using $1 - P(+)$, and also directly. Do you get the same answer?

---

**23.** A weather forecast model has three possible states: Clear (C), Cloudy (O), Rainy (R), with probabilities 0.5, 0.3, 0.2. An outdoor event is cancelled with probabilities:
- 0.05 if Clear
- 0.30 if Cloudy
- 0.90 if Rainy

Find $P(\text{cancelled})$.

**24.** 🤖 **Mixture models.** In a Gaussian Mixture Model (a common ML clustering algorithm), data points are assumed to come from one of $k$ clusters, each with probability $P(Z = k)$ (called a **mixture weight**). The probability of observing data point $\mathbf{x}$ is:

$$P(\mathbf{x}) = \sum_{k=1}^{K} P(\mathbf{x} \mid Z = k) \cdot P(Z = k)$$

This is exactly the law of total probability. Identify the correspondence between this formula and the general law stated above.

---

**25.** Three roads lead to a town. Road A is used by 50% of travellers and has a 10% chance of traffic. Road B is used by 30% and has a 20% chance of traffic. Road C is used by 20% and has a 5% chance of traffic.

- (a) What is the overall probability of a traveller encountering traffic?
- (b) You know you encountered traffic. Which road are you most likely to have taken? (Set this question up for Part D: Bayes.)

**26.** Verify the law of total probability on a simple example: rolling a fair die. Let $A$ = "the result is even". Partition the sample space into $B_1 = \{1, 2\}$, $B_2 = \{3, 4\}$, $B_3 = \{5, 6\}$ (each with probability $\frac{1}{3}$). Compute $P(A \mid B_i)$ for each partition and verify the law gives $P(A) = \frac{1}{2}$.

---

## Part D: Bayes' Theorem (10 problems)

### The Formula

$$\boxed{P(A \mid B) = \frac{P(B \mid A) \cdot P(A)}{P(B)}}$$

In words: the **posterior** probability of $A$ given $B$ equals the **likelihood** of $B$ given $A$, times the **prior** probability of $A$, divided by the **evidence** $P(B)$.

Combined with the law of total probability for $P(B)$:

$$P(A \mid B) = \frac{P(B \mid A) \cdot P(A)}{P(B \mid A) \cdot P(A) + P(B \mid A^c) \cdot P(A^c)}$$

---

**27.** Return to the factory in problem 19. A component is found to be defective. What is the probability it came from M1? (Compute $P(M_1 \mid D)$.)

**28.** Return to the medical test in problem 21. A patient tests positive. What is the probability they actually have the disease? (Compute $P(D \mid +)$.)

- (a) You may be surprised by the answer. What does it say about testing in a low-prevalence population?
- (b) Repeat the calculation if the prevalence increases to 20%. How does the answer change?

**29.** 📧 Return to the email example in problem 20. An email contains the word "urgent". What is the probability it is spam? Work email?

**30.** 🚗 A self-driving car's sensor detects an obstacle with probability 0.9 when one is present ($P(+ \mid O) = 0.9$) and incorrectly detects one with probability 0.01 when none is present ($P(+ \mid O^c) = 0.01$). In urban driving, an obstacle is present 5% of the time. What is $P(O \mid +)$?

---

**31.** A spam filter has $P(\text{spam}) = 0.25$. After seeing the word "prize", it updates to $P(\text{spam} \mid \text{prize}) = 0.85$.

- (a) This updated probability is the **posterior** after one piece of evidence. What is the **prior**?
- (b) If a second word "winner" is seen, and $P(\text{winner} \mid \text{spam}) = 0.9$ while $P(\text{winner} \mid \neg\text{spam}) = 0.1$, use the posterior from (a) as the new prior to compute the updated probability of spam.
- (c) This sequential updating is called **Bayesian updating** and is a core idea in machine learning. Describe in words what is happening.

**32.** An archaeologist finds a pottery fragment. Based on style alone (prior), she assigns 60% probability to the Roman period and 40% to the Medieval period. She then applies a radiocarbon test. The test gives the observed result with probability 0.7 for Roman and 0.2 for Medieval.

- (a) Using Bayes, update her probability that the fragment is Roman.
- (b) What is the posterior probability it is Medieval?

---

**33.** 🎲 The **Monty Hall problem**. You choose one of three doors. Behind one is a car; behind the other two are goats. The host opens one of the other two doors to reveal a goat. Should you switch?

Let $C_i$ = "car is behind door $i$", $H_j$ = "host opens door $j$".

- (a) Before the host acts, what is $P(C_1)$?
- (b) The host opens door 3 (revealing a goat). Use Bayes' theorem to compute $P(C_1 \mid H_3)$ and $P(C_2 \mid H_3)$.
- (c) What does the calculation tell you? (Be careful: the host's choice of door is not random — they always choose a door with a goat, and avoid your door.)

**34.** Bayes' theorem in the form $P(A \mid B) \propto P(B \mid A) \cdot P(A)$ (proportional to, ignoring the denominator) is sometimes called the **unnormalised posterior**. When would it be useful to work with the unnormalised form rather than computing the exact posterior?

**35.** 🤖 **Naïve Bayes classifier (full version).** Given a new email with features (words) $w_1, w_2, \ldots, w_n$, the Naïve Bayes classifier assigns the class that maximises:

$$P(\text{class} \mid w_1, \ldots, w_n) \propto P(\text{class}) \cdot \prod_{i=1}^n P(w_i \mid \text{class})$$

Explain each term in this formula. Where does Bayes' theorem appear? Where does the independence assumption from Part B appear? Why is this classifier called "Naïve"?

**36.** 🔢 **Log probabilities.** In practice, multiplying many small probabilities leads to numerical underflow (the number rounds to zero). The solution is to take the $\log$:

$$\log P(\text{class} \mid \mathbf{w}) \propto \log P(\text{class}) + \sum_{i=1}^n \log P(w_i \mid \text{class})$$

Using the values from problems 16 and 17, compute the log-scores for spam and not-spam (use $\ln$). Does the comparison give the same classification?

---

## Part E: Putting It Together (4 problems)

**37.** A friend says: "I ran Bayes' theorem and found the probability of rain given dark clouds is 0.98. So I should definitely cancel the picnic." What information would you want to verify before trusting this conclusion?

**38.** The **base rate fallacy** occurs when people ignore the prior $P(A)$ and focus only on the likelihood $P(B \mid A)$. Describe a realistic example from medicine, security screening, or social media moderation where the base rate fallacy leads to poor decisions.

**39.** 🌐 Looking back across this worksheet:
- (a) In Part C you used the law of total probability. In ws07d you computed $\boldsymbol{\pi}^{(n+1)} = \boldsymbol{\pi}^{(n)} P$. Show that the state vector update is exactly the law of total probability applied to a Markov chain.
- (b) The stationary distribution $\boldsymbol{\pi}$ satisfies $\boldsymbol{\pi} P = \boldsymbol{\pi}$. What does this say about the probabilities of being in each state "in the long run" — is this related to Bayes somehow?

**40.** Write three sentences summarising Bayes' theorem in plain English for someone who has never heard of it. Then write one sentence explaining why it matters in AI.
