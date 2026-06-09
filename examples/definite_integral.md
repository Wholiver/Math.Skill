# Definite integral: Calculation of $\displaystyle \int_0^{\pi/2} \cos^2 x \, dx$

## User input
Compute definite integrals $\displaystyle \int_0^{\pi/2} \cos^2 x \, dx$

## Skill Category
Calculus / Definite Integral

## Question meaning analysis
- **integrand**: $\cos^2 x$, which is the square of the trigonometric function
- **Integral interval**: $[0, \pi/2]$, the cosine function is non-negative in this interval
- **Goal**: Calculate the exact value of the definite integral
- **Method selection basis**: $\cos^2 x$ needs to be reduced by trigonometric identity
- **Constraints on the solution**: The value of the definite integral should be a positive real number (the integrand is non-negative) and not exceed the interval length $\pi/2$ ( $\cos^2 x \leq 1$ )

## Method selection

**Main Method: Trigonometric Identity Reduction + Direct Integration**

Use the double angle formula $\cos^2 x = \dfrac{1 + \cos 2x}{2}$ to convert the quadratic trigonometric function into a linear trigonometric function and then integrate directly.

Reason for selection: For the form of $\cos^2 x$ or $\sin^2 x$, descending is the most standard processing method, the calculation is simple and error-free.

**Alternative Method**:
1. **Wallis formula**: Recursion formula of $\int_0^{\pi/2} \cos^n x \, dx$
2. ** $\beta$ function**: converted into $B(1/2, 3/2)/2$ calculation
3. **Symmetry**: $\int_0^{\pi/2} \cos^2 x \, dx = \int_0^{\pi/2} \sin^2 x \, dx$, and the sum of the two is $\pi/2$, so each is $\pi/4$

This article shows the main method and symmetry method, and uses the midpoint method for numerical verification.

## Problem solving process

### Method 1: Reduction of trigonometric identities

**Step 1: Apply the double angle formula**

 $$\cos 2x = 2\cos^2 x - 1 \implies \cos^2 x = \frac{1 + \cos 2x}{2}$$

Verify the identity: $2\cos^2 x - 1 = \cos^2 x - \sin^2 x = \cos 2x$ ✓

**Step 2: Substitute points**

 $$\int_0^{\pi/2} \cos^2 x \, dx = \int_0^{\pi/2} \frac{1 + \cos 2x}{2} \, dx$$

 $$= \frac{1}{2} \int_0^{\pi/2} 1 \, dx + \frac{1}{2} \int_0^{\pi/2} \cos 2x \, dx$$

**Step 3: Calculate separately**

First item:
 $$\frac{1}{2} \int_0^{\pi/2} 1 \, dx = \frac{1}{2} \cdot \left[x\right]_0^{\pi/2} = \frac{1}{2} \cdot \frac{\pi}{2} = \frac{\pi}{4}$$

Second item:
 $$\frac{1}{2} \int_0^{\pi/2} \cos 2x \, dx = \frac{1}{2} \cdot \left[\frac{\sin 2x}{2}\right]_0^{\pi/2} = \frac{1}{4} \left[\sin 2x\right]_0^{\pi/2}$$
 $$= \frac{1}{4} (\sin \pi - \sin 0) = \frac{1}{4} (0 - 0) = 0$$

**Step 4: Summary**

 $$\int_0^{\pi/2} \cos^2 x \, dx = \frac{\pi}{4} + 0 = \frac{\pi}{4}$$

### Method 2: Symmetry method (alternative verification)

**Step 1: Take advantage of symmetry**

On $[0, \pi/2]$, let $u = \pi/2 - x$:

 $$\int_0^{\pi/2} \cos^2 x \, dx = \int_{\pi/2}^0 \cos^2(\pi/2 - u) \cdot (-du)$$
 $$= \int_0^{\pi/2} \sin^2 u \, du$$

So $\int_0^{\pi/2} \cos^2 x \, dx = \int_0^{\pi/2} \sin^2 x \, dx$

**Step 2: Sum**

 $$\int_0^{\pi/2} \cos^2 x \, dx + \int_0^{\pi/2} \sin^2 x \, dx = \int_0^{\pi/2} (\cos^2 x + \sin^2 x) \, dx$$
 $$= \int_0^{\pi/2} 1 \, dx = \frac{\pi}{2}$$

Since the two integrals are equal, each is $\pi/4$ . That is $\int_0^{\pi/2} \cos^2 x \, dx = \frac{\pi}{2} \div 2 = \frac{\pi}{4}$ ✓

## Check calculation

**Check calculation method 1: Midpoint method numerical approximation ($n = 10$)**

Divide $[0, \pi/2]$ equally into $n = 10$ subranges, each width $\Delta x = \pi/20 \approx 0.15708$ .

Midpoint method formula: $\int_a^b f(x) \, dx \approx \Delta x \sum_{i=1}^n f\left(\frac{x_{i-1} + x_i}{2}\right)$

| $i$ | Midpoint $m_i$ | $\cos^2(m_i)$ |
|-----|-----------|---------------|
| 1 |  $0.07854$  |  $0.99384$  |
| 2 |  $0.23562$  |  $0.94550$  |
| 3 |  $0.39270$  |  $0.85355$  |
| 4 |  $0.54978$  |  $0.72701$  |
| 5 |  $0.70686$  |  $0.57725$  |
| 6 |  $0.86394$  |  $0.41753$  |
| 7 |  $1.02102$  |  $0.26278$  |
| 8 |  $1.17810$  |  $0.12808$  |
| 9 |  $1.33518$  |  $0.02802$  |
| 10 |  $1.49226$  |  $0.00000$  |

Sum $\approx 4.93357$

Approximate value $= 0.15708 \times 4.93357 \approx 0.7750$

Exact value $\pi/4 \approx 0.785398$, relative error $\approx 1.3\%$ (expected accuracy of midpoint method at $n=10$)✓

**Verification method 2: Wallis formula verification**

 $$\int_0^{\pi/2} \cos^{2} x \, dx = \frac{2-1}{2} \cdot \frac{\pi}{2} = \frac{1}{2} \cdot \frac{\pi}{2} = \frac{\pi}{4}$$

Consistent with the results ✓

**Check Calculation Method 3: Interval Reasonability Check**

The integrand $\cos^2 x$ satisfies $0 \leq \cos^2 x \leq 1$ on $[0, \pi/2]$ , so:
 $$0 \leq \int_0^{\pi/2} \cos^2 x \, dx \leq \frac{\pi}{2}$$

$\pi/4 \approx 0.7854$ within $[0, 1.5708]$ ✓

In addition, the average value of $\cos^2 x$ on $[0, \pi/2]$ is $\frac{\pi/4}{\pi/2} = \frac{1}{2}$, which is consistent with the intuition that $\cos^2 x + \sin^2 x = 1$ and the graphs of the two functions are symmetric ✓

## Final answer
 $$\int_0^{\pi/2} \cos^2 x \, dx = \frac{\pi}{4}$$

## Easy to make mistakes
1. **Missing calculation when substituting upper and lower limits of definite integral**: When calculating $\frac{1}{4}[\sin 2x]_0^{\pi/2}$, pay attention to $\sin \pi = 0$ (not $1$), $\sin 0 = 0$
2. **Double angle formula symbol**: $\cos 2x = 2\cos^2 x - 1 = 1 - 2\sin^2 x$, be careful not to confuse the variants
3. **Coefficient after reduction**: $\cos^2 x = \frac{1 + \cos 2x}{2}$. After integration, it must be multiplied by the factor of $\frac{1}{2}$, which is easy to miss.
4. **Premise of the symmetry method**: $\int_0^{\pi/2} \cos^2 x \, dx = \int_0^{\pi/2} \sin^2 x \, dx$ is only established on $[0, \pi/2]$ (variable substitution $u = \pi/2 - x$), and cannot be extended to other intervals at will
5. **Significance of numerical verification**: The midpoint method of $n=10$ has an error of about 1% and is used for rough verification rather than precise proof; to be sure that the results are correct, analytical derivation should prevail.
