# Problem-solving process review: solving quadratic equations

## User input
A student solves the equation     $x^2 - 5x + 6 = 0$    , writes     $(x-2)(x-3) = 0$    , and gets     $x = 2, 3$    . Then the student writes: "Looking at     $(x-6)^2 = x^2 - 12x + 36 = 0$     again, it seems different, so     $x = 6$     is not the solution." Please check this problem-solving process.

## Skill Category
Algebra/Problem Solving Review

## Question meaning analysis
- **Student Answer**:     $x = 2, 3$     (Correct)
- **Content that needs to be reviewed**:
1. Are the main problem-solving steps correct?
2. Whether the student’s test of     $x = 6$     is correct (whether the reasoning logic is reasonable)
3. Are there any unnecessary steps?
- **Objective**: Point out what is correct, correct wrong reasoning, and give standard verification methods

## Method selection
Use the **step-by-step analysis method**: review each step of the student's reasoning one by one, distinguish the correct steps from the wrong/redundant steps, and then give standard answers and verifications.

## Problem solving process

### Review student solutions

**Step 1: Factorization**     $(x-2)(x-3) = 0$

Review:     $x^2 - 5x + 6 = (x-2)(x-3)$     ✓

Verification: Expand     $(x-2)(x-3) = x^2 - 3x - 2x + 6 = x^2 - 5x + 6$     , absolutely correct.

**Step 2: Apply the zero-factor property** →     $x = 2$     or     $x = 3$

Review: Zero Factor Property - If the product of two real numbers is zero, then at least one factor is zero. That is $(x-2)(x-3) = 0 \iff x-2=0 \text{ or } x-3=0 \iff x=2 \text{ or } x=3$ ✓

**Step 3: Verify     $x = 6$     **

Review: Student writes "    $(x-6)^2 = x^2 - 12x + 36 = 0$     seems different, so     $x = 6$     is not the solution"

There is a problem with this reasoning:
1. **Logic Error**:     $(x-6)$     is not a factor of the original polynomial     $x^2-5x+6$    , and the expansion     $(x-6)^2$     has nothing to do with the original equation (unless you are trying to compare two different polynomials, which in itself is not a valid verification method)
2. **Unnecessary step**: The correct answer     $x=2,3$     is already factored, and the additional check     $x=6$     is purely redundant
3. **Incorrect verification method**: The correct verification is to substitute     $x=6$     into the original equation to calculate whether     $6^2 - 5 \cdot 6 + 6$     is equal to     $0$

### Correct verification method

**Verify     $x = 2$    :**
     $$2^2 - 5 \cdot 2 + 6 = 4 - 10 + 6 = 0 \quad \checkmark$$

**Verify     $x = 3$    :**
     $$3^2 - 5 \cdot 3 + 6 = 9 - 15 + 6 = 0 \quad \checkmark$$

**Verify     $x = 6$     (explain why it is not a solution):**
$$6^2 - 5 \cdot 6 + 6 = 36 - 30 + 6 = 12 \neq 0 \quad \text{It is indeed not a solution}$$

### Why is factoring enough?

A quadratic polynomial     $x^2 - 5x + 6$     has at most two roots (Fundamental Theorem of Algebra). Factoring yields two roots     $2$     and     $3$     , which exhaustively exhaust all possible roots. There is no need (and no reason) to check     $x=6$     - unless you suspect that the factorization is wrong (in which case you should check     $x=2$     and     $x=3$     rather than picking any other number).

## Check calculation

**Verification method 1: Directly enter the verification**

|     $x$     |     $x^2$     |     $-5x$     |     $+6$     | Total | Judgment |
|-----|-------|-------|------|------|------|
|     $2$     |     $4$     |     $-10$     |     $6$     |     $0$     | ✓ is the root |
|     $3$     |     $9$     |     $-15$     |     $6$     |     $0$     | ✓ is the root |
|     $6$     |     $36$     |     $-30$     |     $6$     |     $12$     | ✗ Not a root |

**Verification method 2: Verification of root formula**

For     $ax^2 + bx + c = 0$     (     $a=1, b=-5, c=6$     ):

     $$x = \frac{-b \pm \sqrt{b^2 - 4ac}}{2a} = \frac{5 \pm \sqrt{25 - 24}}{2} = \frac{5 \pm 1}{2}$$

Get     $x = 3$     or     $x = 2$    , consistent with factoring ✓

**Check Calculation Method 3: Verification of Vedic Theorem**

Assume the two roots are     $x_1, x_2$     , then:
-     $x_1 + x_2 = 5$     ✓ (     $2+3=5$     , equal to     $-b/a$     )
-     $x_1 \cdot x_2 = 6$     ✓ (     $2 \times 3 = 6$     , equal to     $c/a$     )

## Final answer

The student's answer     $x = 2$     or     $x = 3$     is **correct**. But in the process of solving the problem:
- Application of factorization and zero factor property **Correct** ✓
- Test of     $x=6$     **unnecessary and poorly reasoned** ✗ (    $(x-6)^2$     has nothing to do with the original equation and is not a valid verification)

The correct verification method is to directly substitute the candidate solution into the original equation for calculation.

## Easy to make mistakes
1. **Confusing Factors and Verification**: Using     $(x-6)^2$     to "compare" is an invalid method - verification should always go back to the **original equation**
2. **Superfluous**: After the roots have been found correctly, there is no need to additionally check numbers that are irrelevant to the problem.
3. **Applicable scope of zero factor property**: $(x-2)(x-3)=0 \iff x=2 \text{ or } x=3$ The correct premise is that it is in the real number (or complex number) domain, and the factorization is exact (not approximate)
4. **General principles of verification**: Any claimed solution     $x_0$     must satisfy     $f(x_0) = 0$    , which can be verified by substituting it without constructing an irrelevant polynomial.
5. **The number of roots of a quadratic equation**: A polynomial of degree n can have at most n different roots. Once n are found, the exhaustive list is complete.
