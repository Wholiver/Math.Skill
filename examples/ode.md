# Initial value problem of linear differential equations with constant coefficients

## User input
Solve the initial value problem of differential equations:

 $$y'' - 3y' + 2y = e^x,\quad y(0) = 0,\; y'(0) = 1$$

## Skill Category
ordinary differential equations

## Question meaning analysis
- **Equation type**: Second-order constant coefficient linear non-homogeneous ODE, in the form of $y'' + py' + qy = g(x)$, where $p = -3$, $q = 2$, $g(x) = e^x$.
- **Solution Goal**: A special solution that satisfies the initial conditions $y(0) = 0$ and $y'(0) = 1$.
- **Structure of solution**: General solution = homogeneous solution $y_h$ + special solution $y_p$. The homogeneous solution contains 2 undetermined constants, determined by the initial conditions.
- **Key Observation**: The non-homogeneous term $g(x) = e^x$ . It is necessary to check whether $e^x$ appears in the homogeneous solution (that is, whether $r = 1$ is a characteristic root).
- **Domain**: $x \in \mathbb{R}$, the entire real axis.

## Method selection
**Preferred method**: First find the homogeneous solution (characteristic equation method), and then find the non-homogeneous special solution (undetermined coefficient method). This is a standardized procedure for handling linear ODEs with constant coefficients.

**Alternative methods**: variable parameter method (parameter change method), Laplace transform method. The undetermined coefficient method is the most concise when the right-hand function is exponential, polynomial, sine and cosine.

## Problem solving process

### Step 1: Find the homogeneous solution $y_h$

Characteristic equation:

 $$r^2 - 3r + 2 = 0$$

 $$(r - 1)(r - 2) = 0$$

Characteristic roots: $r_1 = 1$, $r_2 = 2$.

Homogeneous solution:

 $$y_h(x) = C_1 e^{x} + C_2 e^{2x}$$

### Step 2: Find non-homogeneous special solution $y_p$

Non-homogeneous term $g(x) = e^x$ . Note that $r = 1$ is a characteristic root, so the standard attempt form $y_p = Ae^x$ is already in the homogeneous solution.

According to the modified rules of the method of undetermined coefficients, $e^x$ corresponds to the $m = 1$ multiple root, and the tried form should be multiplied by $x^m = x$ :

 $$y_p = A x e^x$$

Find the derivative:

 $$y_p' = A e^x + A x e^x = A e^x(1 + x)$$

 $$y_p'' = A e^x(1 + x) + A e^x = A e^x(2 + x)$$

Substitute into the original equation $y_p'' - 3y_p' + 2y_p = e^x$:

 $$A e^x(2 + x) - 3A e^x(1 + x) + 2A x e^x = e^x$$

Divide by $e^x$ (constant):

 $$A(2 + x) - 3A(1 + x) + 2Ax = A(2 + x - 3 - 3x + 2x) = A(-1) = 1$$

 $$A = -1$$

therefore:

 $$y_p(x) = -x e^x$$

### Step 3: Write the general solution and apply initial conditions

General explanation:

 $$y(x) = y_h(x) + y_p(x) = C_1 e^x + C_2 e^{2x} - x e^x$$

Apply $y(0) = 0$:

 $$C_1 e^0 + C_2 e^0 - 0 \cdot e^0 = C_1 + C_2 = 0 \quad \Rightarrow \quad C_2 = -C_1$$

Find the derivative:

 $$y'(x) = C_1 e^x + 2C_2 e^{2x} - e^x - x e^x$$

Apply $y'(0) = 1$:

 $$C_1 + 2C_2 - 1 - 0 = 1 \quad \Rightarrow \quad C_1 + 2C_2 = 2$$

Substitute $C_2 = -C_1$:

 $$C_1 + 2(-C_1) = -C_1 = 2 \quad \Rightarrow \quad C_1 = -2,\; C_2 = 2$$

### Step 4: Write the final special solution

 $$y(x) = -2e^x + 2e^{2x} - x e^x = 2e^{2x} - (x + 2)e^x$$

## Check calculation

### Method 1: Substitute into the original equation to verify

Calculate $y$ , $y'$ , $y''$ and substitute $y'' - 3y' + 2y$ :

 $$y = 2e^{2x} - (x + 2)e^x$$

 $$y' = 4e^{2x} - e^x - (x + 2)e^x = 4e^{2x} - (x + 3)e^x$$

 $$y'' = 8e^{2x} - e^x - (x + 3)e^x = 8e^{2x} - (x + 4)e^x$$

Substitute into the left end:

 $$y'' - 3y' + 2y = [8e^{2x} - (x + 4)e^x] - 3[4e^{2x} - (x + 3)e^x] + 2[2e^{2x} - (x + 2)e^x]$$

 $$= 8e^{2x} - (x + 4)e^x - 12e^{2x} + 3(x + 3)e^x + 4e^{2x} - 2(x + 2)e^x$$

Merge $e^{2x}$ items: $(8 - 12 + 4)e^{2x} = 0 \cdot e^{2x} = 0$

Merge $e^x$ items: $[-(x + 4) + 3(x + 3) - 2(x + 2)]e^x = [-x - 4 + 3x + 9 - 2x - 4]e^x$

 $$= [(-x + 3x - 2x) + (-4 + 9 - 4)]e^x = [0x + 1]e^x = e^x$$

Left end = $e^x$ = Right end. ✓

### Method 2: Verify initial conditions

 $$y(0) = 2e^0 - (0 + 2)e^0 = 2 - 2 = 0$$

 $$y'(0) = 4e^0 - (0 + 3)e^0 = 4 - 3 = 1$$

✓

### Method 3: General solution contains 2 constants verification

The homogeneous solution $y_h$ contains two linearly independent basis functions $e^x$ and $e^{2x}$ (Wronskian non-zero), and the degree of freedom of the general solution is 2, matching the order of the equation. ✓

## Final answer

 $$\boxed{y(x) = 2e^{2x} - (x + 2)e^x}$$

## Easy to make mistakes
1. **Order of $Axe^x$ in the undetermined coefficient method**: Since $r = 1$ is a characteristic root, the special solution form is $A x e^x$ instead of $A e^x$. If it is set to $A e^x$ by mistake, the left end will be zero after substitution and cannot match $e^x$ on the right end.
2. **Derivative $A x e^x$ **: The derivative of $y_p = Axe^x$ is $Ae^x(1+x)$ and the second derivative is $Ae^x(2+x)$. Forgetting the product rule (missing the derivative contribution of $x$ in $x e^x$) is a common mistake.
3. **Characteristic root symbol**: The solutions of $r^2 - 3r + 2 = 0$ are $r = 1$ and $r = 2$ (both positive), not $-1$ and $-2$. Note the sign of factorization $(\lambda - 1)(\lambda - 2)$.
4. **Sequence of application of initial conditions**: First find the general solution expression of $C_1, C_2$, and then substitute $y(0)$ and $y'(0)$; do not substitute initial conditions before using the undetermined coefficient method.
