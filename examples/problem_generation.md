# Generation of quadratic equation practice questions (including answers and scoring standards)

## User input
Generate 3 quadratic equation questions with increasing difficulty, including complete solutions and scoring criteria.

## Skill Category
Algebra/Question Generation and Assessment

## Question meaning analysis
- **Goal**: Generate 3 quadratic equation (or quadratic equation related) questions of increasing difficulty
- **Requirements**: Each question must include a problem statement, complete answer, common mistakes, and scoring criteria.
- **Ascending Difficulty Paths**:
- Easy: direct factorization
- Medium: The root formula needs to be used, and the coefficient is not 1
- Hard: Contains parameter discussion and needs to analyze the discriminant

---

## Problem 1 (Simple) — Factoring

### Title
Solve the equation:     $x^2 - 7x + 12 = 0$

### Problem solving process

**Step 1: Factorization**

Find two numbers whose sum is     $-7$     and their product is     $12$    . The two numbers are     $-3$     and     $-4$     .

     $$x^2 - 7x + 12 = (x - 3)(x - 4) = 0$$

Verification:     $(x-3)(x-4) = x^2 - 4x - 3x + 12 = x^2 - 7x + 12$     ✓

**Step 2: Zero factor property**

$$(x - 3)(x - 4) = 0 \implies x - 3 = 0 \text{ or } x - 4 = 0$$

$$x = 3 \quad \text{or} \quad x = 4$$

**Check**:
-      $x = 3$     ：     $3^2 - 7 \times 3 + 12 = 9 - 21 + 12 = 0$      ✓
-      $x = 4$     ：     $4^2 - 7 \times 4 + 12 = 16 - 28 + 12 = 0$      ✓

### Final answer
$$x = 3 \quad \text{or} \quad x = 4$$

### Common mistakes
1. The sign is wrong when finding the factors, it is written as     $(x+3)(x+4)$    , and the sum becomes     $+7$     instead of     $-7$
2. Forgetting to set each factor to 0 after factoring
3. Only one root is given

### Scoring criteria (total 10 points)

| Rating items | Points | Description |
|--------|------|------|
| Correct factorization | 4 points | Write     $(x-3)(x-4)=0$     |
| Apply the zero factor property | 3 points | Let     $x-3=0$     and     $x-4=0$     respectively |
| Get the correct solution | 2 points |     $x=3$     and     $x=4$     |
| Check calculation | 1 point | Substitute the solution into the original equation to verify |

---

## Problem 2 (medium) - Root formula method

### Title
Solve the equation:     $2x^2 + 3x - 2 = 0$

### Problem solving process

**Analysis**: Coefficient     $a=2$    , direct factorization is not easy, use the root formula.

**Step 1: Calculate the discriminant**

     $$\Delta = b^2 - 4ac = 3^2 - 4 \times 2 \times (-2) = 9 + 16 = 25$$

    $\Delta = 25 > 0$     , has two unequal real roots.

**Step 2: Apply the root formula**

     $$x = \frac{-b \pm \sqrt{\Delta}}{2a} = \frac{-3 \pm \sqrt{25}}{2 \times 2} = \frac{-3 \pm 5}{4}$$

     $$x_1 = \frac{-3 + 5}{4} = \frac{2}{4} = \frac{1}{2}$$

     $$x_2 = \frac{-3 - 5}{4} = \frac{-8}{4} = -2$$

**Alternative method (factorization)**:

     $$2x^2 + 3x - 2 = (2x - 1)(x + 2) = 0$$

Verify expansion:     $2x^2 + 4x - x - 2 = 2x^2 + 3x - 2$     ✓

Get     $2x - 1 = 0$     or     $x + 2 = 0$    , that is,     $x = \frac{1}{2}$     or     $x = -2$    , which is consistent with the root formula.

**Check**:
-      $x = \frac{1}{2}$     ：     $2 \times \frac{1}{4} + 3 \times \frac{1}{2} - 2 = \frac{1}{2} + \frac{3}{2} - 2 = 0$      ✓
-      $x = -2$     ：     $2 \times 4 + 3 \times (-2) - 2 = 8 - 6 - 2 = 0$      ✓

### Final answer
$$x = \frac{1}{2} \quad \text{or} \quad x = -2$$

### Common mistakes
1. The denominator in the root formula is written as     $a$     instead of     $2a$    , that is,     $x = (-b \pm \sqrt{\Delta})/a$
2. The sign of     $4ac$     is wrong when calculating     $\Delta$     (    $c=-2$    ,     $4 \times 2 \times (-2) = -16$    , subtracting negative numbers is adding)
3. Forgetting to simplify fractions

### Scoring criteria (total 10 points)

| Rating items | Points | Description |
|--------|------|------|
| Correct identification coefficient     $a, b, c$     | 2 points |     $a=2, b=3, c=-2$     |
| Calculate     $\Delta$     Correct | 2 points |     $\Delta=25$     |
| Correctly substitute the root formula | 3 points |     $x = \frac{-3\pm 5}{4}$     |
| Get the correct solution | 2 points |     $x=1/2$     and     $x=-2$     |
| Verification | 1 point | Substitution verification |

---

## Problem 3 (difficult)—including parameter and discriminant analysis

### Title
Find all real numbers     $k$     such that the equation     $x^2 + 2kx + k + 2 = 0$     has real roots.

### Problem solving process

**Analysis**: This is a quadratic equation with parameter     $k$     (the first coefficient is     $1 \neq 0$    , which is indeed quadratic). The condition for having real roots is that the discriminant is non-negative.

**Step 1: Identification coefficient**

     $$a = 1, \quad b = 2k, \quad c = k + 2$$

**Step 2: Write the discriminant and simplify it**

     $$\Delta = b^2 - 4ac = (2k)^2 - 4 \times 1 \times (k + 2)$$

     $$\Delta = 4k^2 - 4(k + 2) = 4k^2 - 4k - 8$$

     $$\Delta = 4(k^2 - k - 2)$$

**Step 3: Factor the discriminant expression**

     $$k^2 - k - 2 = (k - 2)(k + 1)$$

Verification:     $(k-2)(k+1) = k^2 + k - 2k - 2 = k^2 - k - 2$     ✓

     $$\Delta = 4(k - 2)(k + 1)$$

**Step 4: Solve the inequality     $\Delta \geq 0$     **

Requires a real root, i.e.     $\Delta \geq 0$     :

     $$4(k - 2)(k + 1) \geq 0$$

Because of     $4 > 0$     , the inequality is equivalent to:

     $$(k - 2)(k + 1) \geq 0$$

**Step 5: Solve the quadratic inequality**

Zero points:     $k = -1$     and     $k = 2$     .

The coefficient of the quadratic term is positive, and the parabola opens upward. The solution for factor     $(k-2)(k+1) \geq 0$     is:

$$k \leq -1 \quad \text{or} \quad k \geq 2$$

That is     $k \in (-\infty, -1] \cup [2, +\infty)$     .

**Step 6: Boundary verification**

-     $k = -1$     : the equation becomes     $x^2 - 2x + 1 = 0 \implies (x-1)^2 = 0 \implies x = 1$     (double root,     $\Delta = 0$     ) ✓
-     $k = 2$     : the equation becomes     $x^2 + 4x + 4 = 0 \implies (x+2)^2 = 0 \implies x = -2$     (double root,     $\Delta = 0$     ) ✓
-     $k = 0$     (intermediate value, should not have real roots): equation becomes     $x^2 + 0x + 2 = 0 \implies x^2 = -2$     (no real roots,     $\Delta = -8$     )✓
-     $k = -2$     (less than     $-1$     ):     $\Delta = 4 \times (-4) \times (-1) = 16 > 0$     , has real roots ✓
-     $k = 3$     (greater than     $2$     ):     $\Delta = 4 \times 1 \times 4 = 16 > 0$     , has real roots ✓

### Final answer
     $$k \in (-\infty, -1] \cup [2, +\infty)$$

That is     $k \leq -1$     or     $k \geq 2$     .

### Common mistakes
1. Forget that the discriminant is "non-negative" (     $\geq 0$     ), only consider strictly greater than (missing boundary values ​​    $k=-1$     and     $k=2$     , in which case there are multiple roots)
2. When solving the inequality     $(k-2)(k+1) \geq 0$    , write the opposite direction (written as     $-1 \leq k \leq 2$    ), confusing the relationship between the two sides and the middle
3. Forgetting to extract common factors when simplifying the discriminant, making the inequality difficult to solve
4. Mistakenly thinking that     $a=0$     also needs to be discussed (here     $a=1$     is always not zero, so there is no need to discuss the situation of degenerating into a linear equation)

### Scoring criteria (total 10 points)

| Rating items | Points | Description |
|--------|------|------|
| Correct identification of     $a,b,c$     | 1 point |     $a=1, b=2k, c=k+2$     |
| Write the discriminant and simplify it | 3 points |     $\Delta = 4k^2 - 4k - 8 = 4(k^2 - k - 2)$     |
| Factoring discriminant | 2 points |     $\Delta = 4(k-2)(k+1)$     |
| Solve the inequality     $\Delta \geq 0$     | 3 points | Correctly derive     $k \leq -1$     or     $k \geq 2$     |
| Bounds verification | 1 point | Verify that     $k=-1$     and     $k=2$     have duplicate roots |

---

## Overall difficulty progression description

| Difficulty | Core Methods | Cognitive Requirements |
|------|----------|----------|
| Easy | Factorization | Find two numbers whose sum is     $-7$     and whose product is     $12$     |
| Medium | Root formula | Identify coefficients, calculate discriminants, substitute formulas, simplify fractions |
| Hard | Parametric analysis | Parametric discriminant, factorization, quadratic inequality solution, boundary checking |
