# Limit calculation - Taylor expansion method

## User input
Find the limit:

     $$\lim_{x \to 0} \frac{e^x - 1 - \sin x}{x^2}$$

## Skill Category
Calculus

## Question meaning analysis
- **Limit type**: When     $x \to 0$    , both the numerator and denominator tend to     $0$    , which is the     $\frac{0}{0}$     type infinitive.
- **Molecular Structure**:     $e^x - 1 - \sin x$    . When     $x \to 0$     ,     $e^x \to 1$     ,     $\sin x \to 0$     , so the numerator is     $\to 1 - 1 - 0 = 0$     .
- **Denominator Structure**:     $x^2 \to 0$     .
- **Key Observation**:     $e^x$     and     $\sin x$     both have Taylor expansions at     $x = 0$    , which can be expanded to the order of     $x^2$     to eliminate the lower-order terms.
- **Choice of expansion order**: Denominator is     $x^2$    , expand to     $x^2$     terms (i.e.     $O(x^3)$    ) to capture terms in the numerator with the same order as     $x^2$    .

## Method selection
**Preferred method**: Taylor expansion. Expand     $e^x$     and     $\sin x$     to a sufficiently high order and simplify after substitution. The low-order terms cancel each other out, and the remaining dominant terms are the limit values.

**Alternative Method**: Lópida's Law. This problem can also be solved by L'Hôpital's rule, but it requires two derivatives, which requires a large amount of calculation and is prone to errors. Taylor expansion is more direct. Numerical approximations serve as numerical verification.

**Rationale**: As a limit of the form $e^x - \text{Polynomial}$ , Taylor's expansion is often more efficient than L'Hobida's rule, especially when the molecule contains multiple functions.

## Problem solving process

### Step 1: Write the Taylor expansion

Expansion of     $e^x$     at     $x = 0$     (to     $x^3$     item):

     $$e^x = 1 + x + \frac{x^2}{2} + \frac{x^3}{6} + O(x^4)$$

Expansion of     $\sin x$     at     $x = 0$     (to     $x^3$     item):

     $$\sin x = x - \frac{x^3}{6} + O(x^5)$$

### Step 2: Substitute the numerator

     $$e^x - 1 - \sin x = \left(1 + x + \frac{x^2}{2} + \frac{x^3}{6} + O(x^4)\right) - 1 - \left(x - \frac{x^3}{6} + O(x^5)\right)$$

Eliminate constant and linear terms:

     $$= x + \frac{x^2}{2} + \frac{x^3}{6} - x + \frac{x^3}{6} + O(x^4)$$

     $$= \frac{x^2}{2} + \frac{x^3}{3} + O(x^4)$$

### Step 3: Find the limit

     $$\frac{e^x - 1 - \sin x}{x^2} = \frac{\frac{x^2}{2} + \frac{x^3}{3} + O(x^4)}{x^2} = \frac{1}{2} + \frac{x}{3} + O(x^2)$$

Let     $x \to 0$     :

     $$\lim_{x \to 0} \frac{e^x - 1 - \sin x}{x^2} = \frac{1}{2}$$

## Check calculation

### Method 1: Lópida’s Law

First application (    $\frac{0}{0}$     type, conditions are met:     $x \to 0$    ,     $e^x - 1 - \sin x$     and     $x^2$     can all be derived):

     $$\lim_{x \to 0} \frac{e^x - 1 - \sin x}{x^2} = \lim_{x \to 0} \frac{e^x - \cos x}{2x}$$

Still of type     $\frac{0}{0}$     (     $\frac{1 - 1}{0}$     ), apply Lupida for the second time:

     $$= \lim_{x \to 0} \frac{e^x + \sin x}{2} = \frac{1 + 0}{2} = \frac{1}{2}$$

The results are consistent. ✓

(Note: Although Lupida is feasible in this problem, when the molecule contains more functions, the derivation will become cumbersome; the advantage of Taylor expansion is that it can be processed uniformly.)

### Method 2: Numerical approximation

|      $x$      |      $\frac{e^x - 1 - \sin x}{x^2}$      |
|-----|--------------------------------|
| 0.1 |      $\frac{1.1051709 - 1 - 0.0998334}{0.01} = \frac{0.0053375}{0.01} \approx 0.5338$      |
| 0.01 |      $\frac{1.0100502 - 1 - 0.0099998}{0.0001} = \frac{0.0000504}{0.0001} \approx 0.504$      |
| 0.001 |      $\frac{1.0010005 - 1 - 0.0010000}{0.000001} = \frac{0.0000005}{0.000001} \approx 0.500$      |

When     $x \to 0$    , the value approaches     $0.5$    . ✓

## Final answer

     $$\boxed{\lim_{x \to 0} \frac{e^x - 1 - \sin x}{x^2} = \frac{1}{2}}$$

## Easy to make mistakes
1. **Insufficient expansion order**: It is not enough to expand this question to     $x$     times (the linear terms of     $e^x$     and     $\sin x$     cancel each other out). It must be expanded to at least     $x^2$     items to obtain a non-zero result.
2. **O token processing**:     $O(x^4)/x^2 = O(x^2) \to 0$     (when     $x \to 0$    ), but cannot simply be written as 0 without losing information. The key is to ensure that the dominant term is preserved correctly.
3. **Applicable conditions for Lópida's law**: Before each application, it must be confirmed that the numerator and denominator tend to     $0$     (or both tend to     $\infty$    ) when they are at     $x \to 0$    , and the derivative exists and the ratio limit of the derivative exists.
4. **Expansion of     $\sin x$    **:     $\sin x = x - x^3/6 + \cdots$    . Note that     $x^3/6$     is subtracted instead of added.
