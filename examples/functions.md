# Monotonicity and extreme values ​​of functions

## User input
Find the monotonic interval and extreme value (including maximum value, minimum value, maximum value and minimum value) of function     $f(x) = x^3 - 3x^2 - 9x + 5$     on the interval     $[-2, 4]$    .

## Skill Category
Functions—derivative applications: monotonicity analysis and extreme value problems

## Question meaning analysis

**Known conditions:**
- Function:     $f(x) = x^3 - 3x^2 - 9x + 5$
- Closed interval:     $x \in [-2, 4]$

**Solution goal:**
- Monotonically increasing and decreasing intervals of the function
- Maximum points and maxima, minimum points and minima of functions
- Maximum and minimum values ​​on a closed interval

**Variables and Domains:**
- The function     $f(x)$     is a cubic polynomial that is continuously differentiable on     $\mathbb{R}$    , given the closed interval     $[-2, 4]$    .

**Implicit condition:**
- The maximum value on a closed interval may appear at the critical point (the point where the derivative is zero) or at the end of the interval, requiring all comparisons.
- The derivative is a quadratic function, the discriminant     $> 0$    , there are two different real roots, and the function has two stationary points.

## Method selection

**Selection method:** Derivative method (derivative → stationary point → symbolic analysis → monotonicity judgment) + endpoint comparison

**reason:**
- Derivation of polynomial functions is simple and straightforward.
- The most standard way to judge monotonicity is by the sign of the first derivative.
- The second-order derivative assists in determining the type of extreme value.

**Alternative method:**
- Cubic functions can be judged indirectly through the increase or decrease of     $f(x)$    , but it is not systematic.
- Numerical heuristics (list calculations) - not accurate enough and can only be used as a verification method.

## Problem solving process

### Step 1: Derivation

     $$
f'(x) = 3x^2 - 6x - 9
$$

Extract the common factor     $3$    :

     $$
f'(x) = 3(x^2 - 2x - 3)
$$

Factoring:

     $$
f'(x) = 3(x-3)(x+1)
$$

### Step 2: Find the stationary point

Let     $f'(x) = 0$     :

     $$
3(x-3)(x+1) = 0 \quad\Rightarrow\quad x = -1 \ \text{or}\ x = 3
$$

Both stationary points are within the interval     $[-2, 4]$    .

### Step 3: Monotonicity Analysis

Judge the monotonicity of the original function based on the sign of     $f'(x) = 3(x-3)(x+1)$    .

| interval |     $x$     range |     $x+1$     |     $x-3$     |     $f'(x)$     |     $f(x)$     monotonicity |
|------|----------|-------|-------|---------|--------------|
|     $[-2, -1)$     |     $-2 \leq x < -1$     |     $\leq 0$     /     $< 0$     |     $< 0$     |     $> 0$     | Strictly increasing ↗ |
|     $(-1, 3)$     |     $-1 < x < 3$     |     $> 0$     |     $< 0$     |     $< 0$     | Strictly Decreasing ↘ |
|     $(3, 4]$     |     $3 < x \leq 4$     |     $> 0$     |     $> 0$     |     $> 0$     | Strictly increasing ↗ |

Detailed derivation:

- When     $x \in [-2, -1)$     :     $x+1 < 0$     ,     $x-3 < 0$     , the two negatives are multiplied together to get a positive, multiplied by     $3$     is still positive,     $f'(x) > 0$     . The function is incremented.
- When     $x \in (-1, 3)$     :     $x+1 > 0$     ,     $x-3 < 0$     , one positive and one negative are multiplied together to get negative,     $f'(x) < 0$     . function decreases.
- When     $x \in (3, 4]$     :     $x+1 > 0$     ,     $x-3 > 0$     , the two positives are multiplied to get a positive value,     $f'(x) > 0$     . The function is incremented.

therefore:
- **Monotonically increasing intervals:**     $[-2, -1]$     and     $[3, 4]$
- **Monotonically decreasing interval:**     $[-1, 3]$

### Step 4: Determine the extreme value type

Find the second derivative:

     $$
f''(x) = 6x - 6 = 6(x-1)
$$

-     $f''(-1) = 6(-1-1) = -12 < 0$     →     $x = -1$     is the **maximum value point**
-     $f''(3) = 6(3-1) = 12 > 0$     →     $x = 3$     is the **minimum point**

### Step 5: Calculate the function value of each key point

Compute function values ​​for stationary points and endpoints:

     $$
\begin{aligned}
f(-2) &= (-2)^3 - 3(-2)^2 - 9(-2) + 5 = -8 - 12 + 18 + 5 = 3 \\[6pt]
f(-1) &= (-1)^3 - 3(-1)^2 - 9(-1) + 5 = -1 - 3 + 9 + 5 = 10 \\[6pt]
f(3) &= 3^3 - 3 \times 3^2 - 9 \times 3 + 5 = 27 - 27 - 27 + 5 = -22 \\[6pt]
f(4) &= 4^3 - 3 \times 4^2 - 9 \times 4 + 5 = 64 - 48 - 36 + 5 = -15
\end{aligned}
$$

### Step 6: Determine the extreme value and maximum value

| Location |     $x$     |     $f(x)$     | Properties |
|------|-----|--------|------|
| Left endpoint |     $-2$     |     $3$     | — |
| Stationary point |     $-1$     |     $10$     | Maximum value, maximum value |
| Stationary point |     $3$     |     $-22$     | Minimum value, minimum value |
| Right endpoint |     $4$     |     $-15$     | — |

Compare four values:

- Maximum value:     $\max\{3, 10, -22, -15\} = 10$    , obtained at     $x = -1$
- Minimum value:     $\min\{3, 10, -22, -15\} = -22$    , taken at     $x = 3$
- Maximum value:     $10$     (     $x=-1$     )
- Minimum value:     $-22$     (     $x=3$     )

## Check calculation

### Verification method one: Second-order derivative verification extreme value type

The previous step has been verified with the second derivative, at     $x=-1$         $f''(-1) = -12 < 0$     (maximum value), at     $x=3$         $f''(3) = 12 > 0$     (minimum value). The judgment is correct.

### Calculation method two: take points to verify monotonicity

Pick two points in the monotonically increasing interval and verify     $f(x_1) < f(x_2)$    ; pick two points in the decreasing interval and verify     $f(x_1) > f(x_2)$    .

- Increasing intervals     $[-2, -1]$    :     $f(-2) = 3$    ,     $f(-1.5) = (-1.5)^3 - 3(2.25) + 13.5 + 5 = -3.375 - 6.75 + 13.5 + 5 = 8.375$    .     $3 < 8.375 < 10$     , increment ✓
- Decreasing interval     $[-1, 3]$    :     $f(-1) = 10$    ,     $f(0) = 5$    ,     $f(1) = 1-3-9+5 = -6$    ,     $f(2) = 8-12-18+5 = -17$    .     $10 > 5 > -6 > -17 > -22$     , decreasing ✓
- Increasing intervals     $[3, 4]$    :     $f(3) = -22$    ,     $f(3.5) = 42.875 - 36.75 - 31.5 + 5 = -20.375$    ,     $f(4) = -15$    .     $-22 < -20.375 < -15$     , increment ✓

### Verification method three: Numerical verification of derivative symbols

Take points in the key interval to verify the sign of     $f'(x)$    :

-     $x = -1.5$     (in     $[-2, -1)$     ):     $f'(-1.5) = 3(2.25) - 6(-1.5) - 9 = 6.75 + 9 - 9 = 6.75 > 0$     ✓
-     $x = 0$     (in     $(-1, 3)$     ):     $f'(0) = 0 - 0 - 9 = -9 < 0$     ✓
-     $x = 3.5$     (in     $(3, 4]$     ):     $f'(3.5) = 3(12.25) - 6(3.5) - 9 = 36.75 - 21 - 9 = 6.75 > 0$     ✓

## Final answer

**Monotonicity:**

     $$
\boxed{\text{Increasing interval:}[-2, -1] \cup [3, 4],\quad \text{Decreasing interval:}[-1, 3]}
$$

**Extreme value and maximum value:**

     $$
\boxed{
\begin{aligned}
&\text{Maximum value:} f(-1) = 10 \quad (\text{Also the maximum value}) \\[4pt]
&\text{Minimum value:} f(3) = -22 \quad (\text{Also the minimum value})
\end{aligned}
}
$$

## Easy to make mistakes
1. **Forgot to compare endpoint values:** When finding the maximum value on a closed interval, the extreme value of the stationary point is not necessarily the global maximum value and must be compared with the endpoint value. In this example the extreme value happens to be the maximum value, but this is not always the case.
2. **Station point not within the interval:** If a stationary point is not within the given interval, it should not be included in the comparison. In this question, the two stationary points     $x=-1$     and     $x=3$     are both within     $[-2,4]$    .
3. **Irregular writing of monotonic intervals:** The function is not differentiable at     $x=-1$     (it is differentiable in this question), but the monotonic interval can still include endpoints. In fact,     $f(x)$     is the maximum value point at     $x=-1$    . The left side increases and the right side decreases. The monotonic interval can be written as     $[-2, -1]$     and     $[-1, 3]$    .
4. **The case where the second-order derivative is zero:** If     $f''(c)=0$    , the second-order derivative discrimination method fails, and the sign change of the first-order derivative needs to be used to judge. In this question,     $f''(1)=0$     but     $x=1$     are not stationary points and do not pose a problem.
5. **Error in derivation:** The constant term     $5$     is zero after derivation and is easily left behind. Pay attention to the coefficients - especially     $-9x$     which is     $-9$     after derivation.
6. **The difference between extreme value and maximum value:** Maximum value/minimum value is a local concept (derivative judgment), and maximum value/minimum value is a global concept (compare all possible points). Don't get confused.
