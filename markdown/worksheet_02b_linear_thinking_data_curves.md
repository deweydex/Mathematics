# Worksheet 2B: Linear Thinking — Data & Curves
**AIML Foundations Mathematics**  
**Dublin and Dún Laoghaire ETB**  
**Instructor: Josh Aaron**

---

> **What This Worksheet Is About**
> 
> In the real world, data is messy. Lines don't pass through every point perfectly. But we can still ask: "Does this data have a linear trend?" and "What's the slope telling us?"
> 
> We'll also look at curves and ask: "At this particular spot, what would a line look like?" This is the beginning of calculus thinking — but don't worry, no calculus required yet.

---

## Part A: Which Dataset Is Most Linear? (4 problems)

For each set of scatter plots below, decide which dataset is best represented by a linear model. Explain your reasoning.

---

**1.** Three datasets showing relationship between "Hours Studied" and "Exam Score":

**Dataset A:**
```
Hours:  1   2   3   4   5   6   7   8
Score: 45  52  58  61  67  73  78  84
```

**Dataset B:**
```
Hours:  1   2   3   4   5   6   7   8
Score: 50  55  70  60  85  65  90  75
```

**Dataset C:**
```
Hours:  1   2   3   4   5   6   7   8
Score: 40  45  55  70  82  88  92  94
```

- (a) Without graphing precisely, which dataset shows the most consistent linear pattern?
- (b) Which dataset appears most random/scattered?
- (c) Which dataset might show a curve (diminishing returns)?
- (d) For Dataset A, estimate the slope. What does it mean in context?

---

**2.** Temperature vs Ice Cream Sales:

**Dataset P:**
```
Temp(°C):  10   15   20   25   30   35
Sales(€): 120  180  250  310  380  440
```

**Dataset Q:**
```
Temp(°C):  10   15   20   25   30   35
Sales(€): 100  200  350  400  420  430
```

- (a) Which dataset is more linear?
- (b) Is the slope positive or negative? What does this mean?
- (c) For the more linear dataset, estimate the slope (change in sales per degree).
- (d) Using your slope estimate, predict sales at 40°C.

---

**3.** Year vs Global Average Temperature Anomaly (°C above baseline):

**Dataset X:**
```
Year:    1980  1990  2000  2010  2020
Anomaly: 0.26  0.45  0.42  0.72  1.02
```

**Dataset Y:**
```
Year:    1980  1990  2000  2010  2020
Anomaly: 0.20  0.35  0.50  0.70  0.90
```

- (a) Which dataset shows a more consistent linear trend?
- (b) For Dataset Y, what is the approximate slope (°C per decade)?
- (c) If the trend in Dataset Y continues, what anomaly would you predict for 2050?
- (d) Why might real climate data (like Dataset X) not be perfectly linear?

---

**4.** Training Epochs vs Model Accuracy:

**Dataset M:**
```
Epochs:    10   20   30   40   50   60
Accuracy: 0.60 0.72 0.81 0.87 0.91 0.93
```

**Dataset N:**
```
Epochs:    10   20   30   40   50   60
Accuracy: 0.55 0.65 0.75 0.85 0.95 1.05
```

- (a) Which dataset shows diminishing returns (curve flattening)?
- (b) Which dataset shows perfectly linear improvement?
- (c) Why is Dataset N unrealistic? (Hint: what's the maximum possible accuracy?)
- (d) For Dataset M, between which epochs is the slope steepest?

---

## Part B: Positive, Negative, or Zero Slope? (6 problems)

For each scenario, state whether you'd expect a positive slope, negative slope, or approximately zero slope. Explain briefly.

**5.** 
- (a) Price of a product vs quantity demanded
- (b) Years of experience vs salary
- (c) Distance driven vs fuel remaining in tank
- (d) Shoe size vs intelligence
- (e) Altitude vs air pressure
- (f) Hours of sleep vs alertness (up to 8 hours)

**6.** Match each description to a slope value: **-2, -0.5, 0, 0.5, 2**

- (a) For every 1 unit increase in x, y decreases by 2
- (b) For every 2 unit increase in x, y increases by 1
- (c) Changes in x have no effect on y
- (d) For every 1 unit increase in x, y increases by 2
- (e) For every 2 unit increase in x, y decreases by 1

---

## Part C: Eyeballing the Line of Best Fit (4 problems)

**7.** Here's a scatter plot (imagine points at these coordinates):

```
Points: (1,2), (2,3), (3,5), (4,4), (5,6), (6,7), (7,8)
```

- (a) Sketch these points on graph paper (or imagine them).
- (b) Draw a line that "best fits" through or near the points.
- (c) Estimate the y-intercept of your line.
- (d) Estimate the slope of your line.
- (e) Write the approximate equation of your line.

**8.** The "residual" is how far each point is from your line (vertical distance).

Using the points from problem 7 and a line y = x + 1:
- (a) For point (1, 2): predicted y = 1 + 1 = 2. Residual = 2 - 2 = 0. 
- (b) Calculate the residual for (3, 5).
- (c) Calculate the residual for (4, 4).
- (d) A good fit has residuals that are small and roughly balanced (some positive, some negative). Based on your calculations, is y = x + 1 a reasonable fit?

**9.** Two students fit lines to the same data:
- Student A: y = 2x + 1 (residuals: -1, 0, 2, -1, 1, 0, -1)
- Student B: y = 1.8x + 1.5 (residuals: -0.3, 0.1, 0.5, -0.8, 0.2, 0.4, -0.1)

- (a) Which student's residuals are smaller overall?
- (b) Which line is probably a better fit?
- (c) What's one way to mathematically measure "total error"? (Hint: think about squaring)

**10.** Why do we square the residuals instead of just adding them up?

*(Hint: what happens if you have residuals of +5 and -5?)*

---

## Part D: Slope on Curves — Tangent Line Intuition (10 problems)

> **Key Idea:** On a straight line, the slope is the same everywhere. On a curve, the slope *changes* as you move along it. At any point on a curve, we can draw a line that "just touches" the curve — this is called the **tangent line**, and its slope tells us how steep the curve is at that exact point.

---

**11.** Here's a parabola: y = x²

```
        |     *
        |   *   *
        | *       *
        *-----------*----
       -2  -1   0   1   2
```

- (a) At x = 0 (the bottom of the curve), is the tangent line flat, going up, or going down?
- (b) At x = 2 (right side), is the slope positive or negative?
- (c) At x = -2 (left side), is the slope positive or negative?
- (d) Where on this curve is the slope equal to zero?

**12.** Here's an upside-down parabola: y = -x² + 4

```
        *-----------*
        | *       *
        |   *   *
        |     *
       -2  -1   0   1   2
```

- (a) At the peak (x = 0), what is the slope of the tangent line?
- (b) At x = 1 (going downhill to the right), is the slope positive or negative?
- (c) At x = -1, is the slope positive or negative?

**13.** Here's an exponential growth curve: y = 2ˣ

```
                    *
                  *
                *
             *
        * *
      ----------------
      0   1   2   3   4
```

- (a) Is the slope ever negative on this curve?
- (b) Is the slope ever zero on this curve?
- (c) As x increases, does the slope get steeper or flatter?
- (d) Where is the slope smallest (but still positive)?

**14.** Here's exponential decay: y = (½)ˣ

```
      *
        *
          *
            * *
                * * * *
      ----------------
      0   1   2   3   4
```

- (a) Is the slope positive or negative everywhere?
- (b) Where is the slope steepest (most negative)?
- (c) As x → ∞, what does the slope approach?

---

**15.** Here's a sine wave: y = sin(x)

```
          *   *
        *       *
      *-----------*-----------*
                    *       *
                      *   *
      0    π/2    π    3π/2   2π
```

- (a) At x = 0, is the tangent line going up, down, or flat?
- (b) At x = π/2 (the peak), what is the slope?
- (c) At x = π, is the slope positive, negative, or zero?
- (d) At x = 3π/2 (the trough), what is the slope?
- (e) Where is the slope most positive? Most negative?

**16.** For the curve y = x³:

```
            *
          *
        *
      *
    *
```

- (a) At x = 0, is the slope positive, negative, or zero?
- (b) Is this curve ever decreasing (slope negative)?
- (c) Is the slope constant or changing as you move along the curve?

---

**17.** Sketch a curve where:
- (a) The slope is always positive but decreasing (flattening out)
- (b) The slope is always negative but increasing toward zero
- (c) The slope starts positive, becomes zero, then becomes negative

**18.** A car's position over time follows this pattern:

```
Position
    |         ****
    |     ****
    |  ***
    | *
    |*
    +---------------> Time
```

- (a) Is the car moving forward or backward?
- (b) Is the car speeding up or slowing down?
- (c) At what point is the car moving fastest (steepest tangent)?
- (d) What would it mean if the tangent line were horizontal?

---

**19.** A ball is thrown upward. Its height over time looks like:

```
Height
    |     *  *
    |   *      *
    |  *        *
    | *          *
    |*            *
    +---------------> Time
```

- (a) At the very start (left side), is the slope positive or negative?
- (b) At the peak, what is the slope?
- (c) After the peak (right side), is the slope positive or negative?
- (d) What does the slope represent physically? (Hint: change in height over time)

**20.** For each description, sketch a possible curve:

- (a) Slope is zero at x = 0, positive for x > 0, negative for x < 0
- (b) Slope is always positive and always increasing
- (c) Slope is positive then zero then negative then zero then positive (like a wave)

---

## Part E: Connecting Lines to Data Science (4 problems)

**21.** In linear regression, we find the line y = mx + b that minimizes the sum of squared residuals. Given the line y = 2x + 3:

- (a) Predict y when x = 5.
- (b) If the actual y-value at x = 5 was 14, what's the residual?
- (c) What's the squared residual?

**22.** The correlation coefficient r measures how linear a relationship is:
- r = 1: perfect positive linear relationship
- r = -1: perfect negative linear relationship
- r = 0: no linear relationship

Match each r-value to a description:

- (a) r = 0.95
- (b) r = -0.85
- (c) r = 0.12
- (d) r = -0.02

Options: 
- Strong positive trend
- Strong negative trend  
- Almost no relationship
- Very weak relationship

**23.** "Correlation does not imply causation." For each pair, explain why a correlation might exist without direct causation:

- (a) Ice cream sales and drowning deaths (both high in summer)
- (b) Number of firefighters at a scene and damage amount
- (c) Shoe size and vocabulary in children

**24.** A model predicts house prices: `price = 150,000 + 200 × square_feet`

- (a) What does the slope (200) mean in plain English?
- (b) What does the y-intercept (150,000) represent?
- (c) Is the y-intercept realistic? What might it account for?
- (d) Predict the price of a 1,500 square foot house.

---

## Answer Key

### Part A
1. (a) Dataset A (b) Dataset B (c) Dataset C (d) ≈5 points per hour studied
2. (a) Dataset P (b) Positive; higher temp → more sales (c) ≈13 euros per degree (d) ≈500€
3. (a) Dataset Y (b) ≈0.175°C per decade (c) ≈1.4°C (d) Natural variability, complex systems
4. (a) Dataset M (b) Dataset N (c) Accuracy can't exceed 1.0 (d) Between epochs 10-20

### Part B
5. (a) Negative (b) Positive (c) Negative (d) Zero (e) Negative (f) Positive
6. (a) -2 (b) 0.5 (c) 0 (d) 2 (e) -0.5

### Part C
7. (c) ≈1 (d) ≈1 (e) y ≈ x + 1
8. (b) Predicted: 4, Actual: 5, Residual: +1 (c) Predicted: 5, Actual: 4, Residual: -1 (d) Yes, small balanced residuals
9. (a) Student B (b) Student B (c) Sum of squared residuals
10. Squaring makes all residuals positive; otherwise +5 and -5 would cancel to 0

### Part D
11. (a) Flat (b) Positive (c) Negative (d) At x = 0
12. (a) Zero (b) Negative (c) Positive
13. (a) No (b) No (c) Steeper (d) As x → -∞ (leftmost part)
14. (a) Negative everywhere (b) At far left (small x) (c) Zero
15. (a) Up (positive) (b) Zero (c) Negative (d) Zero (e) Most positive: x = 0, 2π; Most negative: x = π
16. (a) Zero (b) No, always increasing or flat (c) Changing
17. (Sketching exercise - answers will vary)
18. (a) Forward (b) Slowing down (c) At the beginning (d) Car is stopped
19. (a) Positive (b) Zero (c) Negative (d) Velocity (speed and direction)
20. (Sketching exercise - examples: (a) y = x³ (b) y = eˣ (c) y = sin(x))

### Part E
21. (a) 13 (b) +1 (c) 1
22. (a) Strong positive (b) Strong negative (c) Very weak (d) Almost none
23. (a) Both caused by summer/heat (b) Larger fires need more firefighters (c) Both caused by age
24. (a) Each additional sq ft adds €200 to price (b) Base price/land value (c) Represents land + fixed costs (d) €450,000

---

*End of Worksheet 2B*
