# Indefinite integral: calculation of $\int x \sin x \, dx$

## User input
Compute indefinite integrals $\displaystyle \int x \sin x \, dx$

## Skill Category
Calculus / Indefinite integral

## Question meaning analysis
- **integrand**: $x \sin x$, is the product of two functions
- **Goal**: Find the original function (indefinite integral), which must include the integration constant $C$
- **Method selection basis**: The integrand is the product of the polynomial $x$ and the trigonometric function $\sin x$. This is a typical application situation of the **integration by parts method**
- **Implicit condition**: The integration variable is $x$ and the integration interval is not specified (indefinite integral)
- **Uniqueness of solution**: The original function is not unique (difference constant), but it can be expressed in standard form

## Method selection

**Main method: Integration by Parts**

Reason for selection: The integral method by parts is suitable for the integration of the product of two different types of functions, especially when one of the functions is simplified after derivation ($x \to 1$) and the other function is easy to integrate ($\sin x \to -\cos x$).

Integral by parts formula:
 $$\int u \, dv = uv - \int v \, du$$

**LIATE Rule**: The priority for selecting $u$ is Logarithmic > Inverse trig > Algebraic > Trigonometric > Exponential. Here $x$ is an algebraic function (A), $\sin x$ is a trigonometric function (T), and according to LIATE rules $u = x$ , $dv = \sin x \, dx$ should be chosen.

Alternative methods: None - $x \sin x$ There is no simple method of substitution of variables, integration by parts is the only standard method.

## Problem solving process

**Step 1: Select $u$ and $dv$ **

make:
 $$u = x, \quad dv = \sin x \, dx$$

**Step 2: Calculate $du$ and $v$ **

 $$du = dx, \quad v = \int \sin x \, dx = -\cos x$$

**Step 3: Substitute the integral of parts formula**

 $$\int x \sin x \, dx = uv - \int v \, du$$

 $$= x \cdot (-\cos x) - \int (-\cos x) \, dx$$

 $$= -x \cos x + \int \cos x \, dx$$

**Step 4: Calculate remaining points**

 $$\int \cos x \, dx = \sin x$$

**Step 5: Get the final result**

 $$\int x \sin x \, dx = -x \cos x + \sin x + C$$

Where $C$ is the integration constant.

## Check calculation

**Verification method 1: Derivative verification of the results**

Derivative of $F(x) = -x \cos x + \sin x + C$:

 $$\frac{d}{dx}[-x \cos x] = -1 \cdot \cos x + (-x) \cdot (-\sin x) = -\cos x + x \sin x$$
(Used the product rule: $(fg)' = f'g + fg'$ )

 $$\frac{d}{dx}[\sin x] = \cos x$$

 $$\frac{d}{dx}[C] = 0$$

Sum:
 $$F'(x) = (-\cos x + x \sin x) + \cos x + 0 = x \sin x$$

Exactly equal to the integrand $x \sin x$ ✓

**Check Calculation Method 2: Backward Derivation of Integral by Parts**

Starting from the result, the integral of parts should be:
 $$\int x \sin x \, dx = -x \cos x - \int (-\cos x) \cdot 1 \, dx = -x \cos x + \sin x + C$$

Consistent with the calculation process ✓

**Verification method 3: Numerical verification (take $C=0$)**

Let $F(x) = -x \cos x + \sin x$ :
-  $F(0) = -0 \cdot 1 + 0 = 0$
-  $F(\pi/2) = -\frac{\pi}{2} \cdot 0 + 1 = 1$

And $\int_0^{\pi/2} x \sin x \, dx = [-x \cos x + \sin x]_0^{\pi/2} = 1 - 0 = 1$ ✓

Numerical $\int_0^{\pi/2} x \sin x \, dx$ can be approximated: $x \sin x$ is a positive function on $[0, \pi/2]$, and the integral $1$ is reasonable ✓

## Final answer
 $$\int x \sin x \, dx = -x \cos x + \sin x + C$$

## Easy to make mistakes
1. **Wrong selection of $u$ and $dv$**: If you select $u = \sin x$, $dv = x \, dx$, then $du = \cos x \, dx$, $v = x^2/2$, the points become $\frac{1}{2}x^2\sin x - \frac{1}{2}\int x^2 \cos x \, dx$, which is more complicated - indicating the importance of the LIATE rule
2. **Symbol of $v$**: $\int \sin x \, dx = -\cos x$ (not $\cos x$). Symbol error will cause verification to fail.
3. **Forgot the integral constant $C$ **: Indefinite integral must contain the integral constant, points will be deducted if omitted
4. **The direction of the product rule is reversed**: Pay attention to $(uv)' = u'v + uv'$ when deriving and verifying, and do not write in the wrong order.
