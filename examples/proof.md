#     $\sqrt{2}$     is a proof of irrational numbers

## User input
Show that     $\sqrt{2}$     is an irrational number.

## Skill Category
Number theory / proof by contradiction

## Question meaning analysis
- **Condition**: Define     $\sqrt{2}$     as a positive real number that satisfies     $x^2 = 2$
- **Goal**: Prove that there is no integer     $p, q$     (     $q \neq 0$     ) such that     $\sqrt{2} = p/q$
- **Implicit condition**:     $p, q$     can be assumed to be relatively prime (that is, the fraction has been reduced to its simplest form)
- **Method Constraints**: Classical proof by contradiction, assuming there is a rational number expression and then deducing a contradiction
- **Boundary case**: When     $p = 0$    ,     $\sqrt{2} = 0$     is obviously not true and can be excluded

## Method selection

**Main method: standard proof by contradiction**

This is the most classic way to prove irrational numbers. Assume that     $\sqrt{2}$     is a rational number, write it in the simplest fractional form, and then use parity to derive a contradiction.

**Alternative 1: Rational Root Theorem**

Use the rational roots theorem: If     $x = p/q$     (in its simplest form) is a rational number and satisfies     $x^2 - 2 = 0$     , then     $p \mid 2$     and     $q \mid 1$     . So     $p \in \{\pm 1, \pm 2\}$     ,     $q \in \{\pm 1\}$     . Verify     $(\pm 1)^2 = 1 \neq 2$    ,     $(\pm 2)^2 = 4 \neq 2$    , indicating that     $\sqrt{2}$     is not a rational number.

**Alternative 2: Infinite descent method (geometric proof)**

Assuming     $\sqrt{2} = a/b$     (     $a > b > 0$     ), then     $a^2 = 2b^2$     . Considering an isosceles right triangle, a smaller positive integer pair     $(2b-a, a-b)$     can be constructed that also satisfies a similar relationship and derives an infinite descending contradiction.

This article shows two proofs of the main method and the rational root theorem.

## Problem solving process

### Method 1: Classical proof by contradiction

**Step 1: Assumption and Simplification**

Assume that     $\sqrt{2}$     is a rational number, that is, there is a relatively prime positive integer     $p, q$     (     $q \neq 0$     ) such that
     $$\sqrt{2} = \frac{p}{q}, \quad \gcd(p, q) = 1$$

Square both sides:
     $$2 = \frac{p^2}{q^2} \implies p^2 = 2q^2$$

**Step 2: Prove that     $p$     is an even number**

From     $p^2 = 2q^2$    , we know that     $p^2$     is an even number.

**Conclusion**: If     $p^2$     is an even number, then     $p$     must be an even number.

**Argument**: Suppose     $p$     is an odd number, that is, there is an integer     $k$     such that     $p = 2k + 1$     , then
     $$p^2 = (2k + 1)^2 = 4k^2 + 4k + 1 = 2(2k^2 + 2k) + 1$$

    $p^2$     is an odd number, which is inconsistent with     $p^2$     being an even number. Therefore     $p$     must be an even number.

Therefore there is an integer     $k$     such that     $p = 2k$     .

**Step 3: Prove that     $q$     is also an even number**

Substitute     $p = 2k$     into     $p^2 = 2q^2$     :
     $$(2k)^2 = 2q^2 \implies 4k^2 = 2q^2 \implies 2k^2 = q^2$$

So     $q^2$     is an even number. In the same way,     $q$     must be an even number.

**Step 4: Export contradictions**

If     $p$     and     $q$     are both even numbers, then     $\gcd(p, q) \geq 2$     is in conflict with the assumption     $\gcd(p, q) = 1$    .

Therefore, the assumption does not hold,     $\sqrt{2}$     is not a rational number, that is,     $\sqrt{2}$     is an irrational number.     $\square$

### Method 2: Rational Root Theorem

**Step 1: Construct polynomial**

    $\sqrt{2}$     is the positive root of the equation     $x^2 - 2 = 0$    .

**Step 2: Apply the rational root theorem**

Assume     $x = p/q$     (     $p, q$     is relatively prime,     $q > 0$     ) is a rational root of     $x^2 - 2 = 0$    , then     $p \mid (-2)$     and     $q \mid 1$     .

So     $p \in \{\pm 1, \pm 2\}$     ,     $q \in \{1\}$     ,     $x \in \{\pm 1, \pm 2\}$     .

**Step 3: Verify one by one**

-      $x = 1$     ：     $1^2 - 2 = -1 \neq 0$      ✗
-      $x = -1$     ：     $(-1)^2 - 2 = -1 \neq 0$      ✗
-      $x = 2$     ：     $2^2 - 2 = 2 \neq 0$      ✗
-      $x = -2$     ：     $(-2)^2 - 2 = 2 \neq 0$      ✗

None of them are satisfied, so     $x^2 - 2 = 0$     has no rational root and     $\sqrt{2}$     is an irrational number.     $\square$

## Check calculation

**Check calculation method 1: Check the logic of each step of proof by contradiction**

- Assumptions     $\sqrt{2} = p/q$    ,     $\gcd(p,q)=1$     — reasonable, any rational number can be written as the simplest fraction ✓
-     $p^2 = 2q^2$     — Square operation is correct ✓
- "    $p^2$     even     $\implies$         $p$     even" — proved by the inverse proposition "    $p$     odd     $\implies$         $p^2$     odd", calculate     $(2k+1)^2 = 4k^2+4k+1 = 2(2k^2+2k)+1$     correct ✓
-     $q^2 = 2k^2$     — Substitute     $p=2k$     to get     $4k^2=2q^2$    , which is     $q^2=2k^2$     ✓
- "    $q^2$     even     $\implies$         $q$     even" — The same logic is correct ✓
-     $\gcd(p,q) \geq 2$     Contradiction — Two even numbers must have common factors 2 ✓

**Check method 2: Check the application of the rational root theorem**

- The leading coefficient of the polynomial is     $1$     and the constant term is     $-2$     ✓
- The rational root theorem requires $p \mid \text{constant term}$ , $q \mid \text{first term coefficient}$ ✓
- Candidate value     $\pm 1, \pm 2$     Complete ✓
- Substitution verification is correct ✓

**Check Calculation Method 3: Boundary Check**

    $p = 0$     is     $\sqrt{2} = 0/q = 0$     , but     $0^2 = 0 \neq 2$     , so     $\sqrt{2} \neq 0$     ,     $p = 0$     cannot be solutions. Exclude this edge case.

**Verification method 4: Numerical verification**

    $\sqrt{2} \approx 1.4142135623730951$    , the decimal part of this value is infinite and non-cyclic (characteristic of irrational numbers), consistent with the conclusion ✓

## Final answer

$$\sqrt{2} \notin \mathbb{Q}, \quad \text{i.e. } \sqrt{2} \text{ is an irrational number}$$

Both proof methods lead to the same conclusion, and verification confirms that each step of reasoning is correct.

## Easy to make mistakes
1. **Forgot to set     $\gcd(p, q) = 1$     **: Without assuming mutual prime, the contradiction cannot be derived (    $p, q$     may be an even number but is not contradictory, because it can be divided by 2 at the same time to continue the reduction)
2. **Confusing the inverse proposition and the inverse proposition**: Prove that "    $p^2$     even     $\implies$         $p$     even" uses the inverse proposition "    $p$     odd     $\implies$         $p^2$     odd", not the inverse proposition "    $p$     even"     $\implies$         $p^2$     even" (the latter is also correct but not required here)
3. **Wrong Generalization**: Do not think that using similar methods can prove that all square roots are irrational. For example,     $\sqrt{4} = 2$     is a rational number. Using the same reasoning, the odd-even contradiction cannot be derived after the "     $p^2 = 4q^2$     " step.
4. **Conditions for using the rational root theorem**: The rational root theorem requires that the polynomial coefficients are integers and the first coefficient is not zero. Here     $x^2 - 2$     meets the conditions
