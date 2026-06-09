# Probability and expectation of hypergeometric distribution

## User input
There are 5 red balls and 3 blue balls in a bag. Draw 3 balls from it without replacement. Find: (1) the probability of drawing exactly 2 red balls; (2) the expectation of the number of red balls drawn.

## Skill Category
probability theory

## Question meaning analysis
- **Known conditions**: There are $N = 8$ balls in total, including $K = 5$ red balls (successful type) and $N - K = 3$ blue balls; sample size $n = 3$, sampling without replacement.
- **Solution target**: (1) $P(X = 2)$, where $X$ is the number of red balls; (2) $E[X]$.
- **Distribution type identification**: Sampling from a finite population without replacement, the number of red balls $X$ obeys **Hypergeometric distribution** $X \sim \text{Hypergeometric}(N=8, K=5, n=3)$.
- **The value range of $X$**: $\max\{0,\, n - (N - K)\} \leq k \leq \min\{n, K\}$, that is, $k \in \{0, 1, 2, 3\}$.
- **Key Premise**: Sampling is completely random, and each ball has an equal probability of being drawn.

## Method selection
**Preferred method**: Hypergeometric distribution formula. The probability mass function of the hypergeometric distribution is

 $$P(X = k) = \frac{\binom{K}{k} \binom{N-K}{n-k}}{\binom{N}{n}}$$

The expected formula is

 $$E[X] = n \cdot \frac{K}{N}$$

**Alternative methods**: Direct enumeration of classical probabilities; decomposition of expectations by indicator variable method (using linearity).

## Problem solving process

### (1) The probability of drawing exactly 2 red balls

Substitute into the hypergeometric distribution formula, $k = 2$:

 $$P(X = 2) = \frac{\binom{5}{2} \binom{3}{1}}{\binom{8}{3}}$$

Calculate the number of combinations separately:

 $$\binom{5}{2} = \frac{5 \times 4}{2} = 10$$

 $$\binom{3}{1} = 3$$

 $$\binom{8}{3} = \frac{8 \times 7 \times 6}{3 \times 2 \times 1} = 56$$

Substitute:

 $$P(X = 2) = \frac{10 \times 3}{56} = \frac{30}{56} = \frac{15}{28}$$

### (2) Expectation of the number of red balls

Method 1: Directly use the expectation formula of hypergeometric distribution

 $$E[X] = n \cdot \frac{K}{N} = 3 \cdot \frac{5}{8} = \frac{15}{8} = 1.875$$

Method 2: Calculation through distribution law (for verification)

First calculate the complete distribution law:

|  $k$  |  $\binom{5}{k}$  |  $\binom{3}{3-k}$  |  $P(X=k)$  |
|-----|----------------|-------------------|----------|
| 0   | 1              | 1                 |  $1/56$    |
| 1   | 5              | 3                 |  $15/56$   |
| 2   | 10             | 3                 |  $30/56$   |
| 3   | 10             | 1                 |  $10/56$   |

 $$E[X] = 0 \cdot \frac{1}{56} + 1 \cdot \frac{15}{56} + 2 \cdot \frac{30}{56} + 3 \cdot \frac{10}{56} = \frac{15 + 60 + 30}{56} = \frac{105}{56} = \frac{15}{8}$$

The results of both methods are consistent.

## Check calculation

### Method 1: Probability sum verification

The sum of the probabilities of all possible $k$ values ​​should be $1$ :

 $$P(X=0) + P(X=1) + P(X=2) + P(X=3) = \frac{1 + 15 + 30 + 10}{56} = \frac{56}{56} = 1$$

✓ Passed.

### Method 2: Decomposition of expected indicator variables

Define indicator variables $Y_i = \mathbb{1}_{\{\text{The }i\text{th ball is red}\}}$, $i = 1,2,3$. Then $X = Y_1 + Y_2 + Y_3$ .

Due to symmetry (despite sampling without replacement, the ball at each position has the same probability of being red):

$$E[Y_i] = P(\text{The $i$th ball is red}) = \frac{5}{8}$$

Exploiting linearity of expectations:

 $$E[X] = E[Y_1] + E[Y_2] + E[Y_3] = 3 \cdot \frac{5}{8} = \frac{15}{8}$$

The calculation results are completely consistent with the formula.

### Method 3: Each probability is within $[0, 1]$

$\frac{1}{56} \approx 0.018$, $\frac{15}{56} \approx 0.268$, $\frac{30}{56} \approx 0.536$, $\frac{10}{56} \approx 0.179$, all within $[0, 1]$.

## Final answer

 $$\boxed{P(X = 2) = \frac{15}{28}}$$

 $$\boxed{E[X] = \frac{15}{8} = 1.875}$$

## Easy to make mistakes
1. **Confusion between replacement and non-replacement**: This question is about sampling without replacement and applying hypergeometric distribution; if it is sampling with replacement, $X \sim \text{Binomial}(n=3, p=5/8)$, the two have the same expectation but different variances.
2. **Combination number calculation**: $\binom{8}{3} = 56$ instead of $8 \times 7 \times 6 = 336$ (forgot to divide by $3!$).
3. ** $k$ value range is missing**: $k = 0$ is possible (all 3 are blue balls), don’t miss it. Also $k=3$ is possible.
4. **Expected formula memory**: $E[X] = n \cdot \frac{K}{N}$, the numerator is the total number of successful classes $K$, not $N-K$.
