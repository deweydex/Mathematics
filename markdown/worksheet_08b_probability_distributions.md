# Worksheet 8B: Probability Distributions
**AIML Foundations Mathematics**
**Dublin and Dún Laoghaire ETB**
**Instructor: Josh Aaron**

---

> **What This Worksheet Is About**
>
> In ws06a and ws08a you worked with probabilities of specific events. A **probability distribution** is the whole picture: it assigns a probability to every possible outcome.
>
> Some distributions appear again and again across science, engineering, and AI. The **Binomial** counts successes in repeated trials. The **Poisson** counts rare events. The **Normal** (Gaussian) describes noise, measurement error, and — by a remarkable theorem — the average of almost anything.
>
> Knowing these distributions means you can recognise the shape of a problem and reach immediately for the right tool.

---

## Part A: The Bernoulli and Binomial Distributions (12 problems)

### Bernoulli: One Trial

A single trial with probability $p$ of success ($X = 1$) and $1 - p$ of failure ($X = 0$).

$$P(X = 1) = p, \quad P(X = 0) = 1 - p$$

$$\text{Mean: } \mu = p \qquad \text{Variance: } \sigma^2 = p(1-p)$$

### Binomial: $n$ Trials

The number of successes $X$ in $n$ independent Bernoulli trials with success probability $p$:

$$P(X = k) = \binom{n}{k} p^k (1-p)^{n-k}, \quad k = 0, 1, \ldots, n$$

$$\binom{n}{k} = \frac{n!}{k!(n-k)!} \quad \text{(the number of ways to choose } k \text{ from } n \text{)}$$

$$\text{Mean: } \mu = np \qquad \text{Variance: } \sigma^2 = np(1-p)$$

---

**1.** A biased coin has $P(\text{Heads}) = 0.6$.

- (a) Find the probability of exactly 3 heads in 5 flips.
- (b) Find the probability of exactly 0, 1, 2, 3, 4, and 5 heads. Verify they sum to 1.
- (c) What is the mean and variance of the number of heads?

**2.** A spam filter is 95% accurate (correctly identifies spam and non-spam). Ten emails arrive, 4 of which are spam.

- (a) Let $X$ = number of spam emails correctly identified. State the distribution of $X$.
- (b) Find $P(X = 4)$ (all spam correctly identified).
- (c) Find $P(X \geq 3)$.

**3.** A machine learning model classifies images with 80% accuracy. It is tested on 10 images.

- (a) Find the probability of exactly 8 correct classifications.
- (b) Find the probability of 9 or 10 correct.
- (c) Find the expected number of correct classifications and the standard deviation.

**4.** The binomial expansion: $(p + q)^n = \sum_{k=0}^{n} \binom{n}{k} p^k q^{n-k}$ where $q = 1 - p$.

Show that the binomial probabilities sum to 1 by setting $p + q = 1$.

---

**5.** Compute the following combinations (needed for problems above):

- (a) $\binom{5}{2}$ \quad (b) $\binom{6}{0}$ \quad (c) $\binom{6}{6}$ \quad (d) $\binom{10}{3}$ \quad (e) $\binom{8}{4}$

**6.** A quality control inspector samples 20 items. Historical data shows 10% are defective. Let $X$ = number of defective items.

- (a) State the distribution of $X$.
- (b) Find $P(X = 0)$ (none defective).
- (c) Find $P(X \leq 2)$.
- (d) What is the expected number of defectives?

**7.** For a Binomial$(n=20, p=0.5)$ distribution:

- (a) What is the most likely value of $X$ (the mode)?
- (b) What is the mean?
- (c) What happens to the distribution as $n$ increases? (Think of the shape.)

**8.** If $X \sim \text{Binomial}(n=100, p=0.3)$, find the mean, variance, and standard deviation of $X$.

---

🤖 **AI Connection: A/B Testing**

**9.** You run an A/B test: version A of a webpage has 2% click-through rate; version B has an unknown rate. You show version B to 500 users and observe 15 clicks.

- (a) If version B also has a 2% rate, what is the expected number of clicks?
- (b) Under the assumption of 2% rate, what is the probability of observing exactly 15 clicks? (Use $\binom{500}{15}(0.02)^{15}(0.98)^{485}$; you may leave the answer in this form or use the Poisson approximation from Part B.)
- (c) Does 15 out of 500 suggest version B is different from version A?

**10.** In the spam filter problem (problem 2), the model has $n = 1000$ emails, 40% spam ($p = 0.95$ accuracy on spam). The exact Binomial calculation involves $1000!$ — clearly impractical. What approximation would you use? (Hint: look ahead to Part B.)

---

**11.** The **negative binomial** distribution counts the number of trials until the $r$-th success. For $r = 1$, this is the **geometric distribution**:

$$P(X = k) = (1-p)^{k-1} p, \quad k = 1, 2, 3, \ldots$$

A footballer has a 25% chance of scoring each penalty. Find the probability they score their first goal on the 3rd, 4th, and 5th attempt.

**12.** For the geometric distribution with parameter $p$:

$$\text{Mean} = \frac{1}{p} \qquad \text{Variance} = \frac{1-p}{p^2}$$

For a network connection that fails independently with probability 0.1 on each attempt, find the expected number of attempts until a successful connection.

---

## Part B: The Poisson Distribution (10 problems)

### Counting Rare Events

The Poisson distribution models the number of events in a fixed interval (time, space, area), when events occur independently at an average rate $\lambda$:

$$P(X = k) = \frac{\lambda^k e^{-\lambda}}{k!}, \quad k = 0, 1, 2, \ldots$$

$$\text{Mean: } \mu = \lambda \qquad \text{Variance: } \sigma^2 = \lambda$$

Note: the mean and variance are **equal** — a useful diagnostic.

### Poisson as a Limit of Binomial

When $n$ is large and $p$ is small (so $\lambda = np$ is moderate), Binomial$(n, p) \approx$ Poisson($\lambda$).

---

**13.** A website receives an average of 4 visits per minute. Using the Poisson distribution:

- (a) Find the probability of exactly 4 visits in a minute.
- (b) Find the probability of 0 visits.
- (c) Find the probability of more than 6 visits.
- (d) What is the variance of the number of visits per minute?

**14.** Typos occur in a document at a rate of 2 per page. What is the probability of:

- (a) 0 typos on a given page?
- (b) Exactly 2 typos?
- (c) At most 2 typos?
- (d) More than 3 typos?

**15.** A hospital emergency department receives an average of 10 patients per hour.

- (a) Find the probability of exactly 8 patients in a given hour. (Leave as $\frac{10^8 e^{-10}}{8!}$ or compute: $e^{-10} \approx 0.0000454$.)
- (b) Find the expected number of patients in a 30-minute window.
- (c) If the rate is 10 per hour, what is the rate per minute?

**16.** Rare events: a radiation detector records an average of 0.5 particle impacts per second.

- (a) Find $P(X = 0)$, $P(X = 1)$, $P(X = 2)$ for a given second.
- (b) What is the probability of at least one impact per second?

---

**17.** A Binomial$(n=200, p=0.01)$ distribution is approximated by a Poisson. What is $\lambda$? Use the Poisson to find $P(X = 0)$ and $P(X = 2)$.

**18.** The number of defects in a 10 m length of cable averages 3. The defects follow a Poisson distribution.

- (a) Find $P(X = 0)$ for a 10 m length.
- (b) What is the average number of defects in a 5 m length?
- (c) Find $P(X = 0)$ for a 5 m length.

**19.** 🤖 **NLP Connection.** Word frequencies in natural language roughly follow a power law (Zipf's law), not a Poisson distribution — but for rare words, the Poisson is a reasonable approximation. If the word "serendipity" appears on average 0.3 times per 1000 words, what is the probability it appears at least once in a 1000-word passage?

**20.** Verify numerically that Binomial$(n=50, p=0.06)$ is well-approximated by Poisson$(\lambda=3)$ by comparing $P(X=0)$, $P(X=1)$, $P(X=2)$ for each. (Binomial: use $(0.94)^{50} \approx 0.0453$, $(0.94)^{49} \approx 0.0482$.)

---

**21.** For the Poisson distribution, show that the probabilities sum to 1 by recognising $\sum_{k=0}^\infty \frac{\lambda^k}{k!} = e^\lambda$.

**22.** The **Poisson process** describes events in continuous time: if events occur at rate $\lambda$ per unit time, then in time interval $t$ the count is Poisson$(\lambda t)$. A call centre receives 12 calls per hour.

- (a) Find the expected calls in 15 minutes.
- (b) Find $P(X = 0)$ in a 5-minute period.
- (c) How does the Poisson process connect to the exponential distribution? (The waiting time between consecutive Poisson events follows an exponential distribution — we will see this in Part C.)

---

## Part C: Continuous Distributions (10 problems)

### From Discrete to Continuous

For continuous random variables, probabilities are given by areas under a **probability density function (PDF)** $f(x)$:

$$P(a \leq X \leq b) = \int_a^b f(x)\, dx$$

The total area must equal 1: $\int_{-\infty}^{\infty} f(x)\, dx = 1$

The **cumulative distribution function (CDF)** is $F(x) = P(X \leq x) = \int_{-\infty}^x f(t)\, dt$.

---

### The Uniform Distribution: $X \sim \text{Uniform}(a, b)$

$$f(x) = \frac{1}{b-a} \quad \text{for } a \leq x \leq b, \quad f(x) = 0 \text{ otherwise}$$

$$\text{Mean: } \frac{a+b}{2} \qquad \text{Variance: } \frac{(b-a)^2}{12}$$

**23.** A random number generator produces values uniformly between 0 and 10.

- (a) Sketch the PDF.
- (b) Find $P(3 \leq X \leq 7)$.
- (c) Find $P(X > 8)$.
- (d) Find the mean and variance.

**24.** A bus arrives at uniformly random times between 9:00 and 9:10.

- (a) What is the probability you wait more than 7 minutes?
- (b) What is your expected waiting time if you arrive at 9:00?

---

### The Exponential Distribution: $X \sim \text{Exp}(\lambda)$

$$f(x) = \lambda e^{-\lambda x} \quad \text{for } x \geq 0$$

$$\text{Mean: } \frac{1}{\lambda} \qquad \text{Variance: } \frac{1}{\lambda^2} \qquad P(X > x) = e^{-\lambda x}$$

The exponential models **waiting times** between Poisson events.

**25.** Customer service calls arrive at an average rate of 6 per hour, so the time between calls is Exponential with $\lambda = 6$ per hour (or $\lambda = 0.1$ per minute).

- (a) What is the expected waiting time between calls (in minutes)?
- (b) Find $P(\text{wait} > 15 \text{ min})$.
- (c) Find $P(\text{wait} \leq 5 \text{ min})$.

**26.** The exponential distribution has the **memoryless property**: $P(X > s + t \mid X > s) = P(X > t)$.

If a component has not failed after 100 hours, the probability it survives another 50 hours is the same as the probability a new component survives 50 hours. Verify this using $P(X > x) = e^{-\lambda x}$.

**27.** 🔗 **Connecting to Poisson.** If arrivals follow a Poisson process with rate $\lambda$, the time between arrivals follows Exp($\lambda$). A website gets 4 visits per minute.

- (a) What distribution describes the time between visits?
- (b) Find the probability the next visit takes more than 1 minute.
- (c) Find the expected time between visits.

---

## Part D: The Normal Distribution (10 problems)

### The Most Important Distribution in Statistics

$$X \sim N(\mu, \sigma^2): \quad f(x) = \frac{1}{\sigma\sqrt{2\pi}} \exp\!\left(-\frac{(x-\mu)^2}{2\sigma^2}\right)$$

The bell-curve shape is centred at mean $\mu$ and spread controlled by standard deviation $\sigma$.

### The Standard Normal: $Z \sim N(0, 1)$

Any normal variable can be standardised: $Z = \frac{X - \mu}{\sigma}$.

Use the **68-95-99.7 rule**:
- $P(\mu - \sigma \leq X \leq \mu + \sigma) \approx 0.68$
- $P(\mu - 2\sigma \leq X \leq \mu + 2\sigma) \approx 0.95$
- $P(\mu - 3\sigma \leq X \leq \mu + 3\sigma) \approx 0.997$

---

**28.** Heights of adult males in a population are approximately $N(\mu = 178, \sigma^2 = 64)$ cm (so $\sigma = 8$ cm).

- (a) Find the interval containing 68% of heights.
- (b) Find the interval containing 95% of heights.
- (c) What fraction of men are taller than 194 cm? (Use the 68-95-99.7 rule.)
- (d) A man is 162 cm tall. Express this as a $z$-score.

**29.** Exam scores follow $N(\mu = 65, \sigma = 10)$.

- (a) What score is 1.5 standard deviations above the mean?
- (b) What fraction of students score between 55 and 75?
- (c) The top 2.5% of students get an A. What score is the threshold?

**30.** A factory produces bolts with diameter $N(\mu = 10, \sigma = 0.1)$ mm. Acceptable range: $9.8$ to $10.2$ mm.

- (a) Express the limits as $z$-scores.
- (b) What fraction of bolts are acceptable? (Use the 68-95-99.7 rule.)
- (c) How would you reduce the rejection rate without changing $\mu$?

---

**31.** Standardisation practice. For $X \sim N(50, 25)$ (mean 50, variance 25):

- (a) Find $P(X < 55)$ by converting to $Z$.
- (b) Find $P(45 < X < 60)$.
- (c) Find the value $x$ such that $P(X < x) = 0.975$. (This is the 97.5th percentile.)

Use the table: $P(Z < 1) \approx 0.841$, $P(Z < 2) \approx 0.977$, $P(Z < -1) \approx 0.159$.

**32.** 🤖 **Gaussian noise in ML.** Many ML algorithms assume that errors or noise follow a Normal distribution. If prediction errors follow $N(0, \sigma^2)$ (zero mean, unknown variance), the Maximum Likelihood Estimate of $\sigma^2$ from errors $\epsilon_1, \ldots, \epsilon_n$ is:

$$\hat{\sigma}^2 = \frac{1}{n} \sum_{i=1}^n \epsilon_i^2$$

Explain why this is just the mean squared error (MSE). This shows that minimising MSE is equivalent to maximum likelihood estimation under Gaussian noise — connecting ws04e's optimisation to probability.

---

**33.** The **log-normal** distribution: if $\ln X \sim N(\mu, \sigma^2)$, then $X$ is log-normal. Many quantities in nature (income, stock prices, reaction times) are approximately log-normal.

- (a) If $\ln X \sim N(2, 1)$, what is the median of $X$? (Hint: $P(X \leq m) = 0.5$ means $P(\ln X \leq \ln m) = 0.5$.)
- (b) Why is a log-normal distribution right-skewed?

**34.** 🤖 **The softmax and the Normal.** In logistic regression, the output is $P(Y=1) = \sigma(w^T x)$ where $\sigma(z) = 1/(1+e^{-z})$ is the sigmoid. The log-odds $\ln\frac{p}{1-p} = w^T x$ is linear. Why do Gaussian distributed features lead naturally to logistic regression? (Hint: apply Bayes' theorem to $P(x \mid Y=1) \sim N(\mu_1, \sigma^2)$ and $P(x \mid Y=0) \sim N(\mu_0, \sigma^2)$.)

---

## Part E: The Central Limit Theorem (6 problems)

### The Remarkable Theorem

If $X_1, X_2, \ldots, X_n$ are independent random variables from **any** distribution with mean $\mu$ and variance $\sigma^2$, then the sample mean $\bar{X} = \frac{1}{n}\sum X_i$ is approximately normal for large $n$:

$$\bar{X} \approx N\!\left(\mu,\, \frac{\sigma^2}{n}\right)$$

This is the **Central Limit Theorem (CLT)** — arguably the most important theorem in statistics.

---

**35.** A die is rolled 100 times. The expected value of a single roll is 3.5 and the variance is 35/12.

- (a) What is the approximate distribution of the total score $S = X_1 + \cdots + X_{100}$?
- (b) Find the approximate probability that the total score exceeds 370.
- (c) Find the approximate probability that the average score $\bar{X}$ is between 3.3 and 3.7.

**36.** The Binomial$(n, p)$ approaches $N(np, np(1-p))$ for large $n$ (by the CLT). For $n=100$, $p=0.4$:

- (a) State the approximate normal distribution.
- (b) Find $P(X \leq 45)$ using the normal approximation.
- (c) This is called the **normal approximation to the binomial**. When is it most accurate?

**37.** A company processes 500 insurance claims per day. Each claim takes a random time with mean 6 minutes and standard deviation 3 minutes. What is the approximate distribution of the total processing time? What is the probability the total exceeds 3100 minutes?

**38.** 🤖 **Why averaging helps in ML.** In ensemble methods (like Random Forests), many weak models are averaged. If each model has error with variance $\sigma^2$, the average of $n$ independent models has error variance $\sigma^2/n$. This is exactly the CLT reducing variance by averaging. Explain why this justifies using many trees instead of one.

**39.** The CLT requires independence. Give an example where the CLT would **not** apply because of dependency. (Hint: think about correlated stock prices or correlated sensor readings.)

**40.** Looking back across this worksheet and the series:
- (a) The Binomial distribution in Part A connects to ws08a: what is the relationship between a Binomial trial and a Bernoulli random variable?
- (b) The Poisson distribution connects to ws07d Markov chains: a Poisson process has the memoryless property. Which Markov chain property is this equivalent to?
- (c) The Normal distribution connects to ws04e optimisation: minimising MSE is equivalent to what probabilistic procedure?
- (d) The CLT connects to ws06a statistics: the sample mean $\bar{x}$ you computed in ws06a is approximately normal by the CLT. What does this say about the reliability of your estimates?
