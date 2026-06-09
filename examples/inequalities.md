# Solutions to fractional inequalities

## User input
Solve the inequality:     $\displaystyle \frac{x^2-3x+2}{x+1} \geq 0$

## Skill Category
Inequalities - Fractional Inequalities and Symbol Table Method

## Question meaning analysis

**Known conditions:**
- Fractional inequality:     $\frac{x^2-3x+2}{x+1} \geq 0$

**Solution goal:**
- Find all real numbers     $x$     that satisfy the inequality     $\geq 0$    .

**Variables and Domains:**
- Denominator     $x+1 \neq 0$     , which is     $x \neq -1$
- The numerator     $x^2-3x+2$     is a quadratic polynomial and is defined for all real numbers
- Domain:     $x \in \mathbb{R} \setminus \{-1\}$

**Implicit condition:**
- The numerator is factorable as     $(x-1)(x-2)$     , which means that at     $x=1$     and     $x=2$     the fractional value is     $0$     , which should be included in the solution set (the inequality is     $\geq$     , including the equal sign).
- The denominator root     $x=-1$     is a discontinuity point, the fraction is not defined here and must not be included in the solution set.

**Number of solutions:**
- The solutions to the inequalities are intervals on the real number axis, and there are infinitely many possible solutions.

## Method selection

**Selection method:** Symbol table method (root crossing method/number axis marking method)

**reason:**
- The core of solving fractional inequalities is to determine the signs of the numerator and denominator in each interval.
- The symbol table method lists all zero points, divides the number axis into several intervals, and determines the symbols of each interval one by one, which is intuitive and difficult to miss.

**Alternative method:**
- Classification discussion method: Convert the fractional inequality     $\frac{P(x)}{Q(x)} \geq 0$     into     $\begin{cases} P(x) \geq 0 \\ Q(x) > 0 \end{cases}$     or     $\begin{cases} P(x) \leq 0 \\ Q(x) < 0 \end{cases}$    . It works but there are more steps.
- Direct transfer method: convert the inequality into     $\frac{(x-1)(x-2)}{x+1} \geq 0$    , and then analyze the symbols - actually it is the symbol table method.

**Key Principles:**
- The denominator cannot be zero,     $x=-1$     is marked with a hollow dot.
- The equality sign holds true at the zero point of the molecule,     $x=1$     and     $x=2$     are marked with solid dots.

## Problem solving process

### Step 1: Factor the numerator

     $$
x^2 - 3x + 2 = (x-1)(x-2)
$$

Verification:     $(x-1)(x-2) = x^2 - 2x - x + 2 = x^2 - 3x + 2$     ✓

The original inequality becomes:

     $$
\frac{(x-1)(x-2)}{x+1} \geq 0
$$

### Step 2: Determine key points

The sign of the fraction is determined by three linear factors:
- Numerator factors:     $x-1$     (zero point     $x=1$     ),     $x-2$     (zero point     $x=2$     )
- Denominator factor:     $x+1$     (zero point     $x=-1$     )

Arrange all key points on the number axis in order from small to large:

     $$
-1 \quad 1 \quad 2
$$

They divide four intervals on the number line:

     $$
(-\infty, -1),\ (-1, 1),\ (1, 2),\ (2, +\infty)
$$

### Step 3: Create symbol table

Take a representative point in each interval to determine the sign of each factor, and then determine the sign of the fraction.

| Interval | Representative point |     $x+1$     |     $x-1$     |     $x-2$     |     $\frac{(x-1)(x-2)}{x+1}$     | Symbol |
|------|--------|-------|-------|-------|---------------------------|------|
|     $(-\infty, -1)$     |     $x=-2$     |     $-$     |     $-$     |     $-$     |     $\frac{(-)\times(-)}{(-)} = \frac{(+)}{(-)} = (-)$     | **Negative** |
|     $(-1, 1)$     |     $x=0$     |     $+$     |     $-$     |     $-$     |     $\frac{(-)\times(-)}{(+)} = \frac{(+)}{(+)} = (+)$     | **True** |
|     $(1, 2)$     |     $x=1.5$     |     $+$     |     $+$     |     $-$     |     $\frac{(+)\times(-)}{(+)} = \frac{(-)}{(+)} = (-)$     | **Negative** |
|     $(2, +\infty)$     |     $x=3$     |     $+$     |     $+$     |     $+$     |     $\frac{(+)\times(+)}{(+)} = (+)$     | **True** |

### Step 4: Process boundary points

Judge the value of the fraction at key points:

-     $x = -1$    : **The denominator is zero, the fraction is meaningless**. Hollow points are not included in the solution set.
-     $x = 1$    : Substitute,     $\frac{(1-1)(1-2)}{1+1} = \frac{0 \times (-1)}{2} = 0$    , satisfy     $\geq 0$    . **Solid points are included in the solution set. **
-     $x = 2$    : Substitute,     $\frac{(2-1)(2-2)}{2+1} = \frac{1 \times 0}{3} = 0$    , satisfy     $\geq 0$    . **Solid points are included in the solution set. **

### Step 5: Write the solution set

The inequality     $\geq 0$     requires that the fraction value be nonnegative. It can be seen from the symbol table that the interval where the fraction takes a positive value (    $>0$    ) is     $(-1, 1)$     and     $(2, +\infty)$    , and the points where the fraction takes a zero value are     $x=1$     and     $x=2$    . Combined:

     $$
x \in (-1, 1] \cup [2, +\infty)
$$

Represented on a number line:

     ```
<---(----●========●)----(----●=======>
    -1       0       1       2
Hollow Positive Solid Solid
```

## Check calculation

### Calculation method one: representative points of classification interval

Take points in each solution set interval and non-solution set interval to verify:

**Interval     $(-1, 1]$     (should be satisfied): **

     $x = 0$     ：     $\frac{0-0+2}{1} = 2 \geq 0$      ✓

     $x = 0.5$     ：     $\frac{0.25-1.5+2}{1.5} = \frac{0.75}{1.5} = 0.5 > 0$      ✓

    $x = 1$     (boundary):     $\frac{1-3+2}{2} = \frac{0}{2} = 0 \geq 0$     ✓

**Interval     $[2, +\infty)$     (should be satisfied): **

    $x = 2$     (boundary):     $\frac{4-6+2}{3} = \frac{0}{3} = 0 \geq 0$     ✓

     $x = 3$     ：     $\frac{9-9+2}{4} = \frac{2}{4} = 0.5 > 0$      ✓

     $x = 10$     ：     $\frac{100-30+2}{11} = \frac{72}{11} > 0$      ✓

**Interval     $(-\infty, -1)$     (should not be met):**

    $x = -2$    :     $\frac{4+6+2}{-1} = \frac{12}{-1} = -12 < 0$     (not satisfied) ✓

    $x = -10$    :     $\frac{100+30+2}{-9} = \frac{132}{-9} < 0$     (not satisfied) ✓

**Interval     $(1, 2)$     (should not be met): **

    $x = 1.5$    :     $\frac{2.25-4.5+2}{2.5} = \frac{-0.25}{2.5} = -0.1 < 0$     (not satisfied) ✓

All verification points are as expected.

### Calculation method two: function image method

Let     $f(x) = \frac{x^2-3x+2}{x+1}$     , analyze its asymptotes and zeros.

- Vertical asymptote:     $x = -1$
- Zero point:     $x = 1$    ,     $x = 2$
- Horizontal asymptote:     $\lim_{x\to +\infty} f(x) = +\infty$     (numerator quadratic, denominator linear)

The function's fractional value at zero points is     $0$     , and its sign alternates between zero points, consistent with symbol table analysis. The solution set of     $f(x) \geq 0$     is the part of the function graph located on and above the     $x$     axis, that is,     $(-1, 1] \cup [2, +\infty)$     .

## Final answer

     $$
\boxed{x \in (-1,\ 1] \cup [2,\ +\infty)}
$$

Or expressed as an inequality:     $-1 < x \leq 1$     or     $x \geq 2$

## Easy to make mistakes
1. **The zero point of the denominator is mistakenly included in the solution set:**     $x=-1$     The time fraction is meaningless and must be eliminated. Even if     $\geq$     notation is used, the denominator zero cannot be equal.
2. **The zero point in the denominator causes the missing interval:** When making a symbol table, the zero point in the numerator divides the number axis into intervals, and the zero point in the denominator also divides the interval**. Forgetting the zero point in the denominator will result in one less interval being analyzed and the solution set being wrong.
3. **Symbol judgment error:** Calculation error when the signs of three factors are multiplied. It is recommended to write down the symbols factor by factor in the symbol table and then make a comprehensive judgment. You can also use the root-penetrating method: starting from the upper right, it will penetrate the root when encountering odd-order factors, and rebound when encountering even-order factors.
4. **The interval endpoint symbols are written incorrectly:** In     $(-1, 1]$    ,     $-1$     uses parentheses (not included), and     $1$     uses square brackets (inclusive). The range     $[2, +\infty)$     contains     $2$    . If you write it backwards, you will lose points directly.
5. **Ignore the "equal" condition:** When the inequality is     $\geq 0$    ,     $=0$     at the zero point of the molecule satisfies the condition and should be included in the solution set. In the case of     $>0$     (strictly unequal), the numerator zeros also need to be excluded.
6. **Starting direction of root threading method:** It is customary to start root threading from the upper right, but if there is a negative sign in front of the highest order term, you should start from the lower right. Verifying the sign of the rightmost interval can avoid directional errors.
