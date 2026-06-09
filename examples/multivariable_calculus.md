# Critical points and classification of multivariate functions

## User input
Find all critical points of function $f(x, y) = x^3 + y^3 - 3xy$ and determine the type of each critical point (maximum point, minimum point or saddle point).

## Skill Category
multivariable calculus

## Question meaning analysis
- **Function form**: $f(x, y) = x^3 + y^3 - 3xy$, the domain is $\mathbb{R}^2$.
- **Solution objectives**: (1) All critical points (that is, the points of $\nabla f = \mathbf{0}$); (2) Classify each critical point.
- **Key theorem**: Second derivative test (Hessian determinant method). For the critical point $(x_0, y_0)$, calculate

   $$D = f_{xx}(x_0, y_0) \cdot f_{yy}(x_0, y_0) - [f_{xy}(x_0, y_0)]^2$$

- If $D > 0$ and $f_{xx} > 0$ : Minimum point
- If $D > 0$ and $f_{xx} < 0$: maximum value point
- if $D < 0$ : saddle point
- If $D = 0$: Unable to determine

- **Implicit condition**: $f$ is a $C^\infty$ function (infinitely differentiable), all partial derivatives exist and are continuous, and the second-order derivative test conditions are met.

## Method selection
**Preferred method**: Find the critical point with zero gradient + Hessian matrix determinant classification. This is the standard procedure for the extreme value problem of multivariate functions.

**Alternative method**: Taylor expansion to second-order terms determines the positive definiteness of the quadratic form. Essentially equivalent to the Hessian discriminant.

## Problem solving process

### Step 1: Find the first-order partial derivative and make it zero

 $$f_x = \frac{\partial f}{\partial x} = 3x^2 - 3y$$

 $$f_y = \frac{\partial f}{\partial y} = 3y^2 - 3x$$

Let $\nabla f = \mathbf{0}$ :

 $$\begin{cases}
3x^2 - 3y = 0 \\
3y^2 - 3x = 0
\end{cases}
\implies
\begin{cases}
x^2 = y \\
y^2 = x
\end{cases}$$

### Step 2: Solve the system of equations

Substitute $y = x^2$ into $y^2 = x$ :

 $$(x^2)^2 = x \quad \Rightarrow \quad x^4 = x \quad \Rightarrow \quad x^4 - x = 0 \quad \Rightarrow \quad x(x^3 - 1) = 0$$

 $$x(x - 1)(x^2 + x + 1) = 0$$

Real solution: $x = 0$ or $x = 1$ ($x^2 + x + 1 = 0$ has no real roots, discriminant $1 - 4 = -3 < 0$).

- When $x = 0$ : $y = x^2 = 0$ , the critical point is $(0, 0)$ .
- When $x = 1$ : $y = x^2 = 1$ , the critical point is $(1, 1)$ .

### Step 3: Find the second-order partial derivative

 $$f_{xx} = \frac{\partial^2 f}{\partial x^2} = 6x$$

 $$f_{yy} = \frac{\partial^2 f}{\partial y^2} = 6y$$

 $$f_{xy} = f_{yx} = \frac{\partial^2 f}{\partial x \partial y} = -3$$

### Step 4: Calculate the Hessian determinant for each critical point

**Critical point $(0, 0)$ **:

 $$f_{xx}(0,0) = 0, \quad f_{yy}(0,0) = 0, \quad f_{xy}(0,0) = -3$$

 $$D(0,0) = 0 \cdot 0 - (-3)^2 = 0 - 9 = -9 < 0$$

$D < 0$ , so $(0, 0)$ is a saddle point.

**Critical point $(1, 1)$ **:

 $$f_{xx}(1,1) = 6, \quad f_{yy}(1,1) = 6, \quad f_{xy}(1,1) = -3$$

 $$D(1,1) = 6 \cdot 6 - (-3)^2 = 36 - 9 = 27 > 0$$

$D > 0$ and $f_{xx}(1,1) = 6 > 0$ , so $(1, 1)$ is the minimum point.

The minimum value is:

 $$f(1, 1) = 1^3 + 1^3 - 3 \cdot 1 \cdot 1 = 1 + 1 - 3 = -1$$

## Check calculation

### Method 1: Verify that the gradient is zero at the critical point

$(0, 0)$ points: $f_x(0,0) = 3(0)^2 - 3(0) = 0$ , $f_y(0,0) = 3(0)^2 - 3(0) = 0$ . ✓

$(1, 1)$ points: $f_x(1,1) = 3(1)^2 - 3(1) = 0$ , $f_y(1,1) = 3(1)^2 - 3(1) = 0$ . ✓

### Method 2: Function value comparison method

Take a test point near $(0, 0)$:

- Along direction $y = x$: $f(t, t) = 2t^3 - 3t^2$. When $t$ is small, $f(t, t) \approx -3t^2 < 0 = f(0,0)$ ( $t \neq 0$ ).
- Along the $y = -x$ direction: $f(t, -t) = t^3 + (-t)^3 - 3t(-t) = 0 + 3t^2 = 3t^2 > 0 = f(0,0)$ ( $t \neq 0$ ).

The function values ​​near $(0,0)$ are both greater than $f(0,0)$ and less than $f(0,0)$, which are confirmed as saddle points. ✓

Take a test point near $(1, 1)$ and perform second-order Taylor expansion:

 $$f(1+h,1+k) \approx f(1,1) + \frac{1}{2}(6h^2 + 6k^2 - 6hk) = -1 + \frac{3}{2}((h-k)^2 + h^2 + k^2) > -1$$

For $(h,k) \neq (0,0)$, the function value is greater than $-1$, which is confirmed as a minimum value point. ✓

## Final answer

$$\boxed{\text{Critical points: }(0, 0) \text{ and } (1, 1)}$$

$$\boxed{(0, 0) \text{ is a saddle point}}$$

$$\boxed{(1, 1) \text{ is the minimum value point, minimum value } f_{\min} = -1}$$

## Easy to make mistakes
1. **Omission of $x = 0$ Solution**: When solving $x^4 = x$, do not eliminate $x = 0$ (that is, you cannot divide both sides by $x$ at the same time). You should move the terms and write it as $x^4 - x = 0$, and factor it to get all the solutions.
2. **Sign judgment of Hessian determinant**: $D > 0$ and $f_{xx} > 0$ are minimum values; $D > 0$ and $f_{xx} < 0$ are maximum values. Some textbooks use the judgment of $-D$, pay attention to the direction of the positive and negative signs.
3. **Only Two Critical Points**: Don’t let the symmetry of the system of equations $x^2 = y$ and $y^2 = x$ fool you into thinking there are infinitely many solutions. By substituting elimination, we can see that there are only two real solutions.
4. ** Case of $D = 0$**: If the Hessian determinant is zero, the second-order derivative test fails, and higher-order expansion or other methods need to be used to determine. This question does not cover this situation.
