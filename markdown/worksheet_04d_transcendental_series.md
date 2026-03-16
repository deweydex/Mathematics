# Worksheet 4D: Transcendental Functions via Series
**AIML Foundations Mathematics**  
**Dublin and Dún Laoghaire ETB**  
**Instructor: Josh Aaron**

---

> **What This Worksheet Is About**
>
> The functions $e^x$, $\sin(x)$, $\cos(x)$, and $\ln(x)$ aren't polynomials — they're **transcendental functions**.
>
> But here's the beautiful secret: They can be written as **infinite polynomials** (power series)!
>
> Once we write them as series, we can differentiate and integrate term by term — discovering their derivatives and integrals through pure algebra!

---

## Part A: The Exponential Function $e^x$ (14 problems)

### The Series Definition:

$$e^x = 1 + x + \frac{x^2}{2!} + \frac{x^3}{3!} + \frac{x^4}{4!} + \cdots = \sum_{n=0}^{\infty} \frac{x^n}{n!}$$

where $n! = n \times (n-1) \times \cdots \times 2 \times 1$ (factorial)

---

**Understanding the Series:**

**1.** Write out the first 6 terms of the series for $e^x$:

$e^x = 1 + x + \frac{x^2}{2} + $ \_\_\_\_ + \_\_\_\_ + \_\_\_\_ + $\cdots$

**2.** Calculate $e^0$ using the series (plug in $x = 0$):

$e^0 = 1 + 0 + 0 + 0 + \cdots = $ \_\_\_\_

**3.** Approximate $e^1$ using the first 6 terms:

$e^1 \approx 1 + 1 + \frac{1}{2} + \frac{1}{6} + \frac{1}{24} + \frac{1}{120} = $ \_\_\_\_

(Actual value: $e \approx 2.71828...$)

**4.** Approximate $e^{0.1}$ using the first 4 terms:

$e^{0.1} \approx 1 + 0.1 + \frac{0.01}{2} + \frac{0.001}{6} = $ \_\_\_\_

---

### Differentiating $e^x$ Term by Term:

**5.** Differentiate each term of the series:

| Term | Derivative |
|------|------------|
| $1$ | $0$ |
| $x$ | $1$ |
| $\frac{x^2}{2!} = \frac{x^2}{2}$ | $\frac{2x}{2} = x$ |
| $\frac{x^3}{3!} = \frac{x^3}{6}$ | \_\_\_\_ |
| $\frac{x^4}{4!} = \frac{x^4}{24}$ | \_\_\_\_ |
| $\frac{x^5}{5!}$ | \_\_\_\_ |

**6.** Write out the derivative series:

$\frac{d}{dx}e^x = 0 + 1 + x + $ \_\_\_\_ + \_\_\_\_ + \_\_\_\_ + $\cdots$

**7.** Compare to the original series. What do you notice?

$$\boxed{\frac{d}{dx}e^x = e^x}$$

**The exponential function is its own derivative!**

---

**8.** Since $\frac{d}{dx}e^x = e^x$, what is $\int e^x \, dx$?

**9.** Verify by integrating the series term by term:

$\int e^x dx = \int (1 + x + \frac{x^2}{2} + \frac{x^3}{6} + \cdots) dx$

$= x + \frac{x^2}{2} + \frac{x^3}{6} + \frac{x^4}{24} + \cdots + C$

$= (1 + x + \frac{x^2}{2} + \frac{x^3}{6} + \cdots) - 1 + C$

$= e^x + C'$ ✓

---

**With Chain Rule:**

**10.** Using the chain rule, find $\frac{d}{dx}e^{2x}$.

**11.** Find $\frac{d}{dx}e^{x^2}$.

**12.** Find $\int e^{3x} dx$.

**13.** Find $\int 2xe^{x^2} dx$ using substitution.

**14.** The function $e^x$ satisfies $\frac{dy}{dx} = y$. Explain why this makes $e^x$ special for modeling growth.

---

## Part B: Sine and Cosine via Series (18 problems)

### The Series Definitions:

$$\sin(x) = x - \frac{x^3}{3!} + \frac{x^5}{5!} - \frac{x^7}{7!} + \cdots = \sum_{n=0}^{\infty} \frac{(-1)^n x^{2n+1}}{(2n+1)!}$$

$$\cos(x) = 1 - \frac{x^2}{2!} + \frac{x^4}{4!} - \frac{x^6}{6!} + \cdots = \sum_{n=0}^{\infty} \frac{(-1)^n x^{2n}}{(2n)!}$$

**Note:** $x$ must be in **radians**!

---

**Understanding the Series:**

**15.** Notice: $\sin(x)$ has only \_\_\_\_\_ powers of $x$ (1, 3, 5, 7, ...)

**16.** Notice: $\cos(x)$ has only \_\_\_\_\_ powers of $x$ (0, 2, 4, 6, ...)

**17.** Calculate $\sin(0)$ using the series:

$\sin(0) = 0 - 0 + 0 - \cdots = $ \_\_\_\_

**18.** Calculate $\cos(0)$ using the series:

$\cos(0) = 1 - 0 + 0 - \cdots = $ \_\_\_\_

**19.** Approximate $\sin(0.1)$ using first 3 non-zero terms:

$\sin(0.1) \approx 0.1 - \frac{0.001}{6} + \frac{0.00001}{120} = $ \_\_\_\_

(Actual: $\sin(0.1) = 0.0998334...$)

**20.** Approximate $\cos(0.1)$ using first 3 non-zero terms.

---

### Differentiating Sine Term by Term:

**21.** Differentiate each term of $\sin(x) = x - \frac{x^3}{6} + \frac{x^5}{120} - \frac{x^7}{5040} + \cdots$

| Term | Derivative |
|------|------------|
| $x$ | $1$ |
| $-\frac{x^3}{6}$ | $-\frac{3x^2}{6} = -\frac{x^2}{2}$ |
| $\frac{x^5}{120}$ | \_\_\_\_ |
| $-\frac{x^7}{5040}$ | \_\_\_\_ |

**22.** Write the derivative series:

$\frac{d}{dx}\sin(x) = 1 - \frac{x^2}{2} + $ \_\_\_\_ - \_\_\_\_ + $\cdots$

**23.** Compare to the cosine series. What do you notice?

$$\boxed{\frac{d}{dx}\sin(x) = \cos(x)}$$

---

### Differentiating Cosine Term by Term:

**24.** Differentiate $\cos(x) = 1 - \frac{x^2}{2} + \frac{x^4}{24} - \frac{x^6}{720} + \cdots$

| Term | Derivative |
|------|------------|
| $1$ | $0$ |
| $-\frac{x^2}{2}$ | $-x$ |
| $\frac{x^4}{24}$ | \_\_\_\_ |
| $-\frac{x^6}{720}$ | \_\_\_\_ |

**25.** Write the derivative series:

$\frac{d}{dx}\cos(x) = 0 - x + $ \_\_\_\_ - \_\_\_\_ + $\cdots$

**26.** Factor out $-1$: $= -(x - \frac{x^3}{6} + \frac{x^5}{120} - \cdots)$

What function is this?

$$\boxed{\frac{d}{dx}\cos(x) = -\sin(x)}$$

---

### The Beautiful Cycle:

**27.** Complete the derivative cycle:

$$\sin(x) \xrightarrow{\frac{d}{dx}} \cos(x) \xrightarrow{\frac{d}{dx}} -\sin(x) \xrightarrow{\frac{d}{dx}} -\cos(x) \xrightarrow{\frac{d}{dx}} \text{\_\_\_\_\_\_}$$

**28.** After how many derivatives does sine return to itself?

**29.** What is $\frac{d^{100}}{dx^{100}}\sin(x)$? (Hint: $100 \div 4 = ?$)

---

### Integrals (Reversing):

**30.** Since $\frac{d}{dx}\sin(x) = \cos(x)$, what is $\int \cos(x) dx$?

**31.** Since $\frac{d}{dx}\cos(x) = -\sin(x)$, what is $\int \sin(x) dx$?

**32.** Verify $\int \sin(x) dx = -\cos(x) + C$ by differentiating.

---

## Part C: The Natural Logarithm $\ln(x)$ (12 problems)

### Finding the Derivative:

The logarithm is defined as the inverse of $e^x$. If $y = \ln(x)$, then $e^y = x$.

**33.** Differentiate $e^y = x$ implicitly:

$e^y \cdot \frac{dy}{dx} = 1$

$\frac{dy}{dx} = \frac{1}{e^y} = \frac{1}{x}$

$$\boxed{\frac{d}{dx}\ln(x) = \frac{1}{x}}$$

---

**34.** What is $\int \frac{1}{x} dx$?

**35.** Remember from 4A: We couldn't integrate $x^{-1}$ using the power rule because it gave $\frac{x^0}{0}$. 

Now we know: $\int x^{-1} dx = $ \_\_\_\_\_\_\_\_\_\_

---

### The Series for $\ln(1+x)$:

$$\ln(1+x) = x - \frac{x^2}{2} + \frac{x^3}{3} - \frac{x^4}{4} + \cdots \quad \text{(for } -1 < x \leq 1\text{)}$$

**36.** Differentiate term by term:

$\frac{d}{dx}\ln(1+x) = 1 - x + x^2 - x^3 + \cdots$

**37.** The series $1 - x + x^2 - x^3 + \cdots$ is a geometric series with first term 1 and ratio $-x$.

Sum $= \frac{1}{1-(-x)} = \frac{1}{1+x}$

Verify: $\frac{d}{dx}\ln(1+x) = \frac{1}{1+x}$ ✓ (chain rule!)

---

**With Chain Rule:**

**38.** $\frac{d}{dx}\ln(2x)$

**39.** $\frac{d}{dx}\ln(x^2)$

**40.** $\frac{d}{dx}\ln(x^2 + 1)$

**41.** $\int \frac{2x}{x^2 + 1} dx$ (substitution: let $u = x^2 + 1$)

**42.** $\int \frac{1}{2x + 3} dx$

---

**Connection:**

**43.** $e^x$ and $\ln(x)$ are inverse functions.

- $\frac{d}{dx}e^x = e^x$
- $\frac{d}{dx}\ln(x) = \frac{1}{x}$

At $x = 1$: $\frac{d}{dx}e^x\big|_{x=0} = e^0 = 1$ and $\frac{d}{dx}\ln(x)\big|_{x=1} = 1$

The slopes are \_\_\_\_\_\_ at corresponding points!

**44.** For inverse functions $f$ and $f^{-1}$: $\frac{d}{dx}f^{-1}(x) = \frac{1}{f'(f^{-1}(x))}$

Verify this for $e^x$ and $\ln(x)$.

---

## Part D: Integration by Parts with Transcendentals (10 problems)

Now we can use by parts with these functions!

$$\int u \, dv = uv - \int v \, du$$

---

**45.** $\int x e^x dx$

Let $u = x$, $dv = e^x dx$
Then $du = dx$, $v = e^x$

$= xe^x - \int e^x dx = xe^x - e^x + C = e^x(x - 1) + C$

**46.** Verify by differentiating $e^x(x - 1)$.

---

**47.** $\int x \cos(x) dx$

Let $u = x$, $dv = \cos(x) dx$

**48.** $\int x \sin(x) dx$

**49.** $\int x^2 e^x dx$ (need by parts twice!)

**50.** $\int e^x \sin(x) dx$ (a famous one — try it!)

*Hint: Use by parts twice, you'll get the original integral on the right side. Solve for it!*

---

**51.** $\int \ln(x) dx$

Let $u = \ln(x)$, $dv = dx$
Then $du = \frac{1}{x}dx$, $v = x$

$= x\ln(x) - \int x \cdot \frac{1}{x} dx = x\ln(x) - x + C$

**52.** Verify by differentiating $x\ln(x) - x$.

---

**53.** $\int x \ln(x) dx$

**54.** $\int (\ln x)^2 dx$ (by parts twice)

---

## Part E: Euler's Formula — The Most Beautiful Equation (8 problems)

### The Connection:

Using the series:
- $e^{ix} = 1 + ix + \frac{(ix)^2}{2!} + \frac{(ix)^3}{3!} + \frac{(ix)^4}{4!} + \cdots$

Since $i^2 = -1$, $i^3 = -i$, $i^4 = 1$, $i^5 = i$, ...

**55.** Expand the first 6 terms of $e^{ix}$:

$e^{ix} = 1 + ix - \frac{x^2}{2!} - \frac{ix^3}{3!} + \frac{x^4}{4!} + \frac{ix^5}{5!} - \cdots$

**56.** Separate into real and imaginary parts:

Real: $1 - \frac{x^2}{2!} + \frac{x^4}{4!} - \cdots = $ \_\_\_\_\_\_\_\_

Imaginary: $x - \frac{x^3}{3!} + \frac{x^5}{5!} - \cdots = $ \_\_\_\_\_\_\_\_

**57.** Therefore:

$$\boxed{e^{ix} = \cos(x) + i\sin(x)}$$

This is **Euler's Formula**!

**58.** Plug in $x = \pi$:

$e^{i\pi} = \cos(\pi) + i\sin(\pi) = $ \_\_\_\_ + \_\_\_\_ $= -1$

$$\boxed{e^{i\pi} + 1 = 0}$$

**This is "Euler's Identity" — often called the most beautiful equation in mathematics!**

---

**59.** Using Euler's formula, show that:

$\cos(x) = \frac{e^{ix} + e^{-ix}}{2}$

$\sin(x) = \frac{e^{ix} - e^{-ix}}{2i}$

**60.** Now we can see WHY $\frac{d}{dx}\sin(x) = \cos(x)$:

Differentiate $\sin(x) = \frac{e^{ix} - e^{-ix}}{2i}$ using chain rule on each exponential.

**61.** These connections show that $e$, $\pi$, $i$, $\sin$, and $\cos$ are all deeply related.

In your own words, why is this surprising/beautiful?

**62.** The formula $e^{ix} = \cos(x) + i\sin(x)$ means exponential growth in the imaginary direction produces \_\_\_\_\_\_\_\_\_\_.

---

## Part F: Summary — The Big Picture (6 problems)

**63.** Complete the derivative table:

| Function | Derivative |
|----------|------------|
| $e^x$ | |
| $\ln(x)$ | |
| $\sin(x)$ | |
| $\cos(x)$ | |

**64.** Complete the integral table:

| Function | Integral |
|----------|----------|
| $e^x$ | |
| $\frac{1}{x}$ | |
| $\sin(x)$ | |
| $\cos(x)$ | |

**65.** We derived all of these using \_\_\_\_\_\_\_\_\_\_ expansions!

**66.** The key insight: Transcendental functions can be written as \_\_\_\_\_\_\_\_\_\_ polynomials, and we know how to differentiate polynomials term by term.

**67.** Why can't we integrate $e^{-x^2}$ in closed form?

*The series would be $1 - x^2 + \frac{x^4}{2!} - \frac{x^6}{3!} + \cdots$, and integrating gives a series with no nice closed form.*

**68.** This is why numerical methods matter in ML and statistics — the Gaussian/Normal distribution involves $e^{-x^2}$!

---

## Answer Key

### Part A
1. $1 + x + \frac{x^2}{2} + \frac{x^3}{6} + \frac{x^4}{24} + \frac{x^5}{120}$
2. $1$
3. $\approx 2.7167$ (actual $e \approx 2.7183$)
4. $\approx 1.1052$
5. $\frac{x^2}{2}$, $\frac{x^3}{6}$, $\frac{x^4}{24}$
6. $1 + x + \frac{x^2}{2} + \frac{x^3}{6} + \cdots$
7. It's the same series! $\frac{d}{dx}e^x = e^x$
8. $e^x + C$
10. $2e^{2x}$
11. $2xe^{x^2}$
12. $\frac{1}{3}e^{3x} + C$
13. $e^{x^2} + C$

### Part B
15. odd
16. even
17. $0$
18. $1$
19. $\approx 0.09983$
20. $\approx 0.99500$
21. $\frac{x^4}{24}$, $-\frac{x^6}{720}$
22. $\frac{x^4}{24} - \frac{x^6}{720}$
23. It's the cosine series!
24. $\frac{x^3}{6}$, $-\frac{x^5}{120}$
25. $\frac{x^3}{6} - \frac{x^5}{120}$
26. $-\sin(x)$
27. $\sin(x)$
28. 4
29. $-\sin(x)$ (since $100 = 4 \times 25$, back to start)
30. $\sin(x) + C$
31. $-\cos(x) + C$

### Part C
34. $\ln|x| + C$
35. $\ln|x| + C$
38. $\frac{1}{x}$
39. $\frac{2}{x}$ (or use $\ln(x^2) = 2\ln(x)$)
40. $\frac{2x}{x^2+1}$
41. $\ln(x^2+1) + C$
42. $\frac{1}{2}\ln|2x+3| + C$
43. reciprocals
44. $\frac{d}{dx}\ln(x) = \frac{1}{e^{\ln(x)}} = \frac{1}{x}$ ✓

### Part D
46. $\frac{d}{dx}[e^x(x-1)] = e^x(x-1) + e^x = e^x \cdot x$ ✓
47. $x\sin(x) + \cos(x) + C$
48. $-x\cos(x) + \sin(x) + C$
49. $e^x(x^2 - 2x + 2) + C$
50. $\frac{e^x(\sin x - \cos x)}{2} + C$
51. $x\ln(x) - x + C$
52. $\ln(x) + 1 - 1 = \ln(x)$ ✓
53. $\frac{x^2\ln(x)}{2} - \frac{x^2}{4} + C$

### Part E
55. See work
56. Real: $\cos(x)$; Imaginary: $\sin(x)$
58. $-1 + 0i = -1$
62. rotation/circular motion

### Part F
63. $e^x$, $\frac{1}{x}$, $\cos(x)$, $-\sin(x)$
64. $e^x + C$, $\ln|x| + C$, $-\cos(x) + C$, $\sin(x) + C$
65. series/Taylor
66. infinite

---

*End of Worksheet 4D*
