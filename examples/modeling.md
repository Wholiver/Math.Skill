#Mathematical modeling: Maximum area problem of riverside fence

## User input
A farmer has a 100 meter fence and wants to enclose a rectangular area close to the river (no fence is needed on the river side). Find the size of the rectangle that maximizes the area.

## Skill Category
Mathematical modeling/optimization problems

## Question meaning analysis

**Question translation**:
- **RESOURCE**: 100m Fence
- **Area Shape**: Rectangle
- **Constraint**: One side of the rectangle faces the river, and no fence is needed on this side (that is, only three sides need to build fences)
- **Goal**: Maximize the area of ​​the rectangle

**Variable definition**:
- Let     $x$    : the length of the side perpendicular to the river bank (width, two in total)
- Let     $y$    : the length of the side parallel to the river bank (length, one piece, no fence is needed near the river)

**Constraints**:
- Total fence length:     $2x + y = 100$
- Physical meaning:     $x > 0$    ,     $y > 0$     (side length is positive)
- Implied domain:     $x \in (0, 50)$     (because     $y = 100 - 2x > 0$     requires     $x < 50$    ;     $x > 0$     is a necessary condition)

**Objective function**: Area     $A = xy$

**Solution constraints**: When the maximum area is,     $x$     should be the interior point of the domain (not the boundary)

## Method selection

**Main method: single variable optimization (elimination + derivation)**

Use the constraint     $y = 100 - 2x$     to convert the binary optimization problem into a univariate optimization problem, and then use derivatives to find the extreme value.

Reason for selection: This problem has only one equality constraint. After elimination, a quadratic function of one variable can be obtained and just need to be differentiated. This is a typical three-step process of modeling-elimination-finding extreme values.

**Alternative Method**:
1. **Preparation method (complete square)**: Use the     $A(x) = 100x - 2x^2$     formula and directly read the maximum value
2. **Inequality method (AM-GM)**: Maximize     $A = xy$     using     $2x + y = 100$     constraints
3. **Lagrange multiplier method**: a general method for binary constrained optimization (a little excessive here)

This article demonstrates the elimination derivation method (main method) and combination method (check calculation), and conducts comprehensive verification.

## Problem solving process

### Step 1: Establish mathematical model

**Model elements**:

| Elements | Content |
|------|------|
| Decision variables |     $x$     (width),     $y$     (length) |
| Objective function |     $A = x \cdot y$     (maximize) |
| Constraints |     $2x + y = 100$    ,     $x > 0$    ,     $y > 0$     |

**Model type**: Quadratic objective function maximization problem under linear constraints (continuous optimization).

### Step 2: Eliminate into a univariate problem

From the constraint     $2x + y = 100$    , we get     $y = 100 - 2x$    .

Substitute into the objective function:
     $$A(x) = x \cdot (100 - 2x) = 100x - 2x^2$$

Domain:     $x \in (0, 50)$     (because     $y = 100 - 2x > 0$     ).

The problem is transformed into: find the maximum value of the unary function     $A(x) = 100x - 2x^2$     on     $(0, 50)$    .

### Step 3: Find the critical point by derivation

     $$A'(x) = 100 - 4x$$

Let     $A'(x) = 0$     :
     $$100 - 4x = 0 \implies x = 25$$

Within the domain     $(0, 50)$    , there is only one critical point     $x = 25$    .

### Step 4: Determine the extreme value type

**Second Derivative Test**:
     $$A''(x) = -4 < 0$$

    $A''(25) = -4 < 0$    , so     $x = 25$     is the maximum value point. Since the function has only one critical point on     $(0, 50)$     and the second derivative is always negative, this is the global maximum.

### Step 5: Calculate the optimal solution

     $$x = 25 \text{ m}$$
     $$y = 100 - 2 \times 25 = 50 \text{ m}$$
     $$A_{\max} = 25 \times 50 = 1250 \text{ m}^2$$

### Step 6: Boundary behavior confirmation

- When     $x \to 0^+$     :     $y \to 100$     ,     $A \to 0$     (degenerate into a one-dimensional line segment with zero area)
- When     $x \to 50^-$     :     $y \to 0$     ,     $A \to 0$     (degenerated into a two-dimensional line segment with zero area)

The boundary values ​​are all 0, which is less than     $1250$     at the interior point     $x=25$    , confirming that this is the global maximum.

## Check calculation

### Verification method 1: Matching method (algebraic verification)

     $$A(x) = 100x - 2x^2 = -2(x^2 - 50x)$$
     $$= -2\left[(x^2 - 50x + 625) - 625\right] = -2(x - 25)^2 + 1250$$

Since     $-2(x - 25)^2 \leq 0$     takes 0 when     $x = 25$    , therefore:
$$A_{\max} = 1250, \quad \text{obtained}$$ when } x = 25 \text{

Consistent with the derivation result ✓

### Verification method 2: Neighborhood verification

|     $x$     |     $y = 100 - 2x$     |     $A = xy$     | Description |
|-----|----------------|----------|------|
| 24 | 52 | 1248 | Less than 1250 |
| 25 | 50 | 1250 | Maximum value |
| 26 | 48 | 1248 | Less than 1250 |

Verified that     $x=25$     indeed gives a larger area than neighboring points ✓

### Calculation method 3: Dimension check

- Fence length:     $2x + y = 2 \times 25 + 50 = 100$     m ✓
- Area unit:     $A = 25 \text{ m} \times 50 \text{ m} = 1250 \text{ m}^2$     ✓
- The variables have the same dimensions:     $x$     and     $y$     are both in meters, and     $A$     is in square meters ✓

### Verification method 4: Analogous verification of isoperiodic problems

Maximizing the area of ​​a rectangle with fixed perimeter:
- Closed rectangle (four-sided fence): When the perimeter is fixed at     $P = 2x + 2y$    , the area is the largest (square) when     $x = y$
- Semi-closed rectangle (with fences on three sides and one side by the river):     $2x + y = 100$    , the largest area is obtained when     $y = 2x$     is obtained

This is consistent with intuition: the river front is "free", so the river front (     $y$     ) should be made wider - with half-width fences on each side to form the wings. The result     $y:x = 50:25 = 2:1$     fits this intuition ✓

### Verification method 5: Rough verification by enumeration method

Enumerate several values ​​with step size     $\Delta x = 5$    :

|      $x$      |      $y$      |      $A$      |
|-----|-----|-----|
| 5 | 90 | 450 |
| 10 | 80 | 800 |
| 15 | 70 | 1050 |
| 20 | 60 | 1200 |
| 25 | 50 | 1250 |
| 30 | 40 | 1200 |
| 35 | 30 | 1050 |
| 40 | 20 | 800 |
| 45 | 10 | 450 |

    $A$     is maximum at     $x=25$     ✓

## Final answer

Optimal solution: width perpendicular to the river bank     $x = 25$     meters, length parallel to the river bank     $y = 50$     meters, maximum area     $1250$     square meters.

Mathematical expression:
     $$x^* = 25 \text{ m}, \quad y^* = 50 \text{ m}, \quad A_{\max} = 1250 \text{ m}^2$$

## Easy to make mistakes
1. **The constraint equation is written incorrectly**: There is no need for a fence near the river, so the total length of the fence is     $2x + y = 100$     (not     $2x + 2y = 100$    ). This is the easiest trap to fall into.
2. **Ignore physical constraints**:     $x$     and     $y$     must be positive, causing the domain to be     $(0, 50)$     instead of     $\mathbb{R}$    . Although     $x=0$     and     $x=50$     correspond to degenerate situations mathematically, they are not acceptable in a physical sense
3. **Distinguishing between extreme values ​​and maximum values**: The first-order derivative of zero gives the extreme point, and second-order derivative test + boundary check is required to confirm that it is the global maximum.
4. **derivative error**: The derivative of     $A(x) = 100x - 2x^2$     is     $100 - 4x$     (note that the derivative of     $2x^2$     is     $4x$    , not     $2x$    )
5. **Excessive generalization of question conditions**: This conclusion (    $y = 2x$    ) is only true when it is a rectangle and one side is close to the river. If the shape is not rectangular, or if it is close to the river on more than one side, the conclusion will be completely different.
6. **Completeness of the optimization problem**: In addition to giving the optimal solution, the optimal value (maximum area) should also be given. This is a common deduction point for mathematical modeling questions.
