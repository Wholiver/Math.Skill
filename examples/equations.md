#Solution of fractional equations

## User input
Solve the equation:     $\displaystyle \frac{x}{x-1} + \frac{1}{x+2} = \frac{3}{x^2+x-2}$

## Skill Category
Equations — Fractional equations and root-increasing tests

## Question meaning analysis

**Known conditions:**
- Fractional equation:     $\frac{x}{x-1} + \frac{1}{x+2} = \frac{3}{x^2+x-2}$

**Solution goal:**
- Find the real number     $x$     that satisfies the equation.

**Variables and Domains:**
A fraction is meaningful if all denominators are     $\neq 0$     :

-     $x-1 \neq 0$     , which is     $x \neq 1$
-     $x+2 \neq 0$     , which is     $x \neq -2$
-     $x^2+x-2 = (x-1)(x+2) \neq 0$     , that is,     $x \neq 1$     and     $x \neq -2$

Comprehensive domain:     $x \in \mathbb{R} \setminus \{-2, 1\}$

**Implicit condition:**
- Observe that the third denominator     $x^2+x-2$     can be decomposed into     $(x-1)(x+2)$    , which is exactly the product of the first two denominators. This is the core of the design of this question.

**Number of solutions:**
- After removing the denominator, a quadratic equation of one variable is obtained, with up to two roots. It needs to be checked whether it is within the definition domain.

## Method selection

**Selection method:** Denominator removal method (multiply by the least common multiple of each denominator) + root-increasing test

**reason:**
- The standard solution to a fractional equation is to multiply both sides by the LCM (least common multiple) of all denominators, converting the fractional equation into an integer equation.
- In this question,     $x^2+x-2 = (x-1)(x+2)$     happens to be the product of the first two denominators, and elimination is very simple.

**Alternative method:**
- Common division method: first divide the left side and then compare it with the right side - the steps are equivalent and the final result is the same.
- Substitution method: Not applicable to this question, there is no obvious substitutable structure.

**risk assessment:**
- Removing the denominator may introduce additional roots (roots that make the original denominator zero), which must be substituted into the original equation one by one after solving.

## Problem solving process

### Step 1: Determine the domain of definition

Solve for the value of     $x$     such that the denominator is zero:

-      $x-1=0 \Rightarrow x=1$
-      $x+2=0 \Rightarrow x=-2$

Domain:     $x \neq 1$     and     $x \neq -2$

### Step 2: Factor the third denominator

Notice that     $x^2+x-2$     can be factored:

     $$
x^2 + x - 2 = (x-1)(x+2)
$$

Verification:     $(x-1)(x+2) = x^2 + 2x - x - 2 = x^2 + x - 2$     ✓

### Step 3: Remove the denominator

Multiply both sides of the equation by     $(x-1)(x+2)$     (not zero in the domain):

     $$
\frac{x}{x-1} \cdot (x-1)(x+2) + \frac{1}{x+2} \cdot (x-1)(x+2) = \frac{3}{(x-1)(x+2)} \cdot (x-1)(x+2)
$$

Various simplifications:

- First item:     $x \cdot (x+2) = x(x+2)$
- Second item:     $1 \cdot (x-1) = x-1$
- Right:     $3$

Get the integral equation:

     $$
x(x+2) + (x-1) = 3
$$

### Step 4: Simplify and solve

Expand:

     $$
x^2 + 2x + x - 1 = 3
$$

Merge similar items:

     $$
x^2 + 3x - 1 = 3
$$

Move items:

     $$
x^2 + 3x - 4 = 0
$$

Factoring:

     $$
(x+4)(x-1) = 0
$$

Solution:

     $$
x = -4 \quad \text{or} \quad x = 1
$$

### Step 5: Check the root increase

**Check     $x = 1$    :**

Substituting into the original equation, the denominator is     $x-1 = 0$    , and the fraction is meaningless. **     $x=1$     is to increase the root and discard it. **

**Check     $x = -4$    :**

Left style     $= \frac{-4}{-4-1} + \frac{1}{-4+2} = \frac{-4}{-5} + \frac{1}{-2} = \frac{4}{5} - \frac{1}{2}$

Common scores:     $\frac{4}{5} = \frac{8}{10}$    ,     $\frac{1}{2} = \frac{5}{10}$

Left style     $= \frac{8}{10} - \frac{5}{10} = \frac{3}{10}$

Right style     $= \frac{3}{(-4)^2 + (-4) - 2} = \frac{3}{16 - 4 - 2} = \frac{3}{10}$

Left style     $=$     Right style     $= \frac{3}{10}$     ✓

## Check calculation

### Calculation method one: Substitute into the original equation (increased root test)

Completed in the previous step,     $x=-4$     satisfies the original equation.

### Calculation method two: Verify the original equation by dividing it into two parts

For     $x = -4$     , verify that the original equation is equivalent to the identity:

Common participle of left-hand formula:     $\frac{x}{x-1} + \frac{1}{x+2} = \frac{x(x+2) + (x-1)}{(x-1)(x+2)} = \frac{x^2+3x-1}{(x-1)(x+2)}$

Right form:     $\frac{3}{x^2+x-2} = \frac{3}{(x-1)(x+2)}$

The original equation is equivalent to:     $\frac{x^2+3x-1}{(x-1)(x+2)} = \frac{3}{(x-1)(x+2)}$

That is     $x^2+3x-1 = 3$     (at     $x \neq 1, -2$     ), which is     $x^2+3x-4=0$     .

When     $x=-4$    :     $(-4)^2 + 3(-4) - 4 = 16 - 12 - 4 = 0$    , satisfied. ✓

### Calculation method three: reverse reasoning

Starting from     $x=-4$     and working backwards:

If     $x=-4$     , then the equivalent form of the equation     $x^2+3x-4=0$     holds.

The original equation is equivalent to     $\frac{x^2+3x-1}{(x-1)(x+2)} = \frac{3}{(x-1)(x+2)}$

Substituting     $x=-4$    , the denominator on both sides is     $(-5)(-2)=10$    , the left side of the numerator is     $16-12-1=3$    , and the right side is     $3$    , both sides are equal.

In summary,     $x=-4$     is indeed the solution to the original equation.

## Final answer

     $$
\boxed{x = -4}
$$

(    $x=1$     is to increase the root, discard it.)

## Easy to make mistakes
1. **Forgot to check for root addition:** After removing the denominator, we get two roots     $x=-4$     and     $x=1$    . If we don’t do the test and directly use     $x=1$     as the answer, we will lose points. **All fractional equations must be tested for increasing roots. **
2. **Loss of domain analysis:** If     $x \neq 1$     and     $x \neq -2$     are not written down at the beginning of solving the problem, it is easy to miss them in subsequent tests.
3. **Error in removing the denominator:** Forgot to multiply each item, especially the integer     $3$     on the right must also be multiplied by     $(x-1)(x+2)$    .
4. **Factorization error:**     $x^2+x-2$     is easily decomposed into     $(x-1)(x-2)$     by mistake. Correct cross-checking can avoid this error.
5. **Confusion of augmented root types:** The augmented root     $x=1$     happens to coincide with the domain exclusion value. It is not a coincidence - the factor multiplied when removing the denominator is exactly     $(x-1)(x+2)$    , so     $x=1$     and     $x=-2$     are both potential augmented roots (although     $x=-2$     in this question is not a root of the equation).
