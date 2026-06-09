# Math.skill comprehensive test case

> This document contains 30 comprehensive test cases covering all mathematics categories and skill dimensions.
> Each test case is used to evaluate Math.skill's correctness, reasoning transparency, rigor, verification quality, etc.

---

## 1. Simple arithmetic: decimal multiplication and division mixed operations

**Test ID:** TC-ARITH-001  
**Input:** "Calculate 3.14 × 2.5 ÷ 0.5"
**Expected Classification:** calculation
**Expected Behavior:** Calculate multiplication and division step by step, giving accurate results 15.7
**Required Verification:**
- Verify that 15.7 × 0.5 = 7.85, 7.85 ÷ 2.5 = 3.14 (inverse operation verification)
- Check whether intermediate steps maintain sufficient accuracy

**Key Checks:**
- Intermediate steps should not be rounded too early
- The final result should be accurate

**Failure Modes:**
- Intermediate rounding leads to error accumulation
- Calculator mode, no steps shown

---

## 2. Algebraic simplification and domain restrictions

**Test ID:** TC-ALG-001  
**Input:** "Simplify the expression \(\frac{x^2 - 4}{x^2 + x - 6}\) and state the domain restrictions"
**Expected Classification:** algebra_simplification
**Expected Behavior:**
- Factor the numerator \( (x-2)(x+2) \)
- Factoring denominator \( (x+3)(x-2) \)
- About \( (x-2) \), we get \( \frac{x+2}{x+3} \)
- Statement \( x \neq 2, x \neq -3 \) (even if the original function at x=2 is undefined after deducting it)

**Required Verification:**
- Substitute x=2 to check that the original function is undefined
- Substitute x=1 to test that the values ​​before and after simplification are equal
- Substitute x=0 to test that the values ​​before and after simplification are equal

**Key Checks:**
- **Key Trap**: Whether to still declare x≠2 after removing (x-2)
- Is the denominator factorization correct?

**Failure Modes:**
- Forgot to declare the domain restriction of x≠2 (most common mistake)
- Denominator factoring error

---

## 3. Quadratic equation: discriminant is zero

**Test ID:** TC-ALG-002  
**Input:** "Solve the equation \(x^2 - 6x + 9 = 0\)"
**Expected Classification:** equation_solving
**Expected Behavior:**
- Calculate the discriminant \( \Delta = 36 - 36 = 0 \)
- Point out that a discriminant of zero means a multiple root
- get \( x = 3 \) (double root)
- Use the root formula or the perfect square: \( (x-3)^2 = 0 \)

**Required Verification:**
- Back-substitution verification: \( 3^2 - 6 \times 3 + 9 = 9 - 18 + 9 = 0 \)
- Explicitly state that the discriminant is zero = a real root (rather than no root)

**Key Checks:**
- Don't say "no solution"
- It should be stated that it is a double root

**Failure Modes:**
- Misjudgment of Δ=0 as no real solution
- Just say x=3 without mentioning the properties of the double root

---

## 4. Fractional equations and increasing roots

**Test ID:** TC-ALG-003  
**Input:** "Solve the equation \(\frac{x}{x-2} + \frac{1}{x} = \frac{4}{x(x-2)}\)"
**Expected Classification:** equation_solving
**Expected Behavior:**
- Multiply by the common denominator \( x(x-2) \): \( x^2 + (x-2) = 4 \)
- Get \( x^2 + x - 6 = 0 \)
- Solve for \( x = 2 \) or \( x = -3 \)
- **Verification**: x=2 makes the denominator zero, which is increasing the root
- Final solution: \( x = -3 \)

**Required Verification:**
- Explicitly back-substitute x=2 into the original equation, the denominator \( x-2 = 0 \) is undefined
- Back substitution x=-3: left = \( \frac{-3}{-5} + \frac{1}{-3} = 0.6 - 0.333... = 0.2666... ​​\) = right

**Key Checks:**
- **MUST** identify root augmentation
- Must explicitly verify the root after solving the problem
- Domain analysis should not be skipped

**Failure Modes:**
- Give two solutions directly without checking for increasing roots (the most serious error)
- Doesn't explain why x=2 is not a solution

---

## 5. System of linear equations: unique solution

**Test ID:** TC-LIN-001  
**Input:** "Solve the system of equations \begin{cases} 2x + 3y = 8 \\ 4x - y = 2 \end{cases}"
**Expected Classification:** equation_solving, system_of_equations
**Expected Behavior:**
- Use elimination method or substitution method
- Solve \( x = 1, y = 2 \)
- Show that the system of equations has rank 2 and has a unique solution

**Required Verification:**
- Back-substitute the first equation: \( 2(1) + 3(2) = 2 + 6 = 8 \) ✓
- Back-substitute the second equation: \( 4(1) - 2 = 2 \) ✓
- Cross-validation with matrix method (optional)

**Key Checks:**
- Both solutions should satisfy both equations
- If there is a unique solution, state it explicitly

**Failure Modes:**
- Arithmetic errors during elimination
- Forgot to verify

---

## 6. Inequalities and symbol tables

**Test ID:** TC-INEQ-001  
**Input:** "Solve the inequality \(x^3 - 3x^2 - 4x + 12 > 0\)"
**Expected Classification:** equation_solving, inequality_solving
**Expected Behavior:**
- Factoring: try x=2 as a root, we get \( (x-2)(x^2-x-6) = (x-2)(x-3)(x+2) \)
- Key points: x = -2, 2, 3
- Make a symbol table and check four intervals
- gives the solution set \( (-2, 2) \cup (3, +\infty) \)

**Required Verification:**
- replace the representative test in each interval (e.g. x=-3, 0, 2.5, 4)
- Endpoint test: the function value at x=-2, 2, 3 is 0
- Whether the symbol table logic is complete

**Key Checks:**
- Is the symbol table correct?
- Whether the interval endpoints are handled correctly (open interval/closed interval)
- Is the factorization correct?

**Failure Modes:**
- Factorization error leads to symbol table error
- Missing a certain interval
- The opening and closing of endpoints is confused

---

## 7. Function domain and value range

**Test ID:** TC-FUNC-001  
**Input:** "Find the domain of function \(f(x) = \sqrt{4 - x^2} + \ln(x-1)\)"
**Expected Classification:** equation_solving, function_analysis
**Expected Behavior:**
- For \( \sqrt{4-x^2} \): \( 4-x^2 \geq 0 \) → \( x \in [-2, 2] \)
- For \( \ln(x-1) \): \( x-1 > 0 \) → \( x > 1 \)
- Take the intersection: \( x \in (1, 2] \)

**Required Verification:**
- Endpoint x=1: Verify that ln(0) is undefined
- Endpoint x=2: Verify √(4-4)=0 and ln(1)=0, f(2)=0
- Take x=1.5 test within the interval

**Key Checks:**
- The square root condition is ≥0 instead of >0
- The logarithmic condition is >0 instead of ≥0
- Is the intersection correct?

**Failure Modes:**
- The square root condition is written as >0, leaving out x=2
- The logarithmic condition is written as ≥0
- Don’t know how to intersect

---

## 8. Geometric proof: triangles are congruent

**Test ID:** TC-GEOM-001  
**Input:** "As shown in the figure, in △ABC, AB=AC, D is the midpoint of BC. Prove AD⊥BC. Text description, no picture."
**Expected Classification:** geometry, proof
**Expected Behavior:**
- Utilize the properties of isosceles triangles
- It is known that AB=AC, D is the midpoint of BC
- In △ABD and △ACD: AB=AC, BD=CD, AD=AD
- Obtain △ABD ≅ △ACD from SSS
- Therefore ∠ADB = ∠ADC
- Also ∠ADB + ∠ADC = 180°
- So ∠ADB = ∠ADC = 90°, which is AD⊥BC

**Required Verification:**
- Is the congruent SSS condition complete (three sides are equal)
- Whether the logical chain is complete: congruent → corresponding angles are equal → adjacent supplementary angles → right angles
- Whether there is a skip step

**Key Checks:**
- SSS congruence conditions are applied correctly
- Is the reasoning about the properties of an isosceles triangle correct?
- The logical completeness of the final conclusion

**Failure Modes:**
- Directly claiming that "the midline of the base of an isosceles triangle is the height" without proof (circular argument)
- SSS condition statement is incomplete

---

## 9. Trigonometric Identities

**Test ID:** TC-TRIG-001  
**Input:** "Prove \(\frac{\sin 2x}{1 + \cos 2x} = \tan x\)"
**Expected Classification:** trigonometry, proof
**Expected Behavior:**
- Use the double angle formula: \( \sin 2x = 2\sin x \cos x \)
- \( \cos 2x = 2\cos^2 x - 1 \)
- Left = \( \frac{2\sin x \cos x}{1 + (2\cos^2 x - 1)} = \frac{2\sin x \cos x}{2\cos^2 x} \)
- Reduction: \( \frac{\sin x}{\cos x} = \tan x \) = right
- Domain description: \( \cos 2x \neq -1 \) that is \( x \neq \frac{\pi}{2} + k\pi \) and \( \cos x \neq 0 \)

**Required Verification:**
- Verify backwards from right to left
- Substitute special values ​​to test: when x=π/4, left=1, right=1
- Domain description

**Key Checks:**
- Is the angle multiplier formula correct?
- Algebraic error probability of simplification process
- Whether to specify the domain

**Failure Modes:**
- Wrong sign of multiple angle formula (sin2x or cos2x)
- Forgot to specify the domain
- algebraic simplification errors

---

## 10. Arithmetic sequence: finding general terms and summation

**Test ID:** TC-SEQ-001  
**Input:** "The sum of the first 5 terms of the arithmetic sequence is 30, and the 10th term is 25. Find the general formula and the sum formula of the first n terms."
**Expected Classification:** equation_solving, sequence, system_of_equations
**Expected Behavior:**
- Let the leading term a be the tolerance d
- S₅ = \( \frac{5}{2}(2a + 4d) = 30 \) → \( 2a + 4d = 12 \)
- a₁₀ = a + 9d = 25
- Solving the system of equations: we get a = -4, d = 3.222...?
- Wait, verify: 2(-4) + 4d = 12 → -8 + 4d = 12 → d = 5
  - a + 9d = -4 + 45 = 41 ≠ 25
- Seems inconsistent. Re: S₅ = 5a + 10d = 30 → a + 2d = 6
  - a + 9d = 25
- Subtraction: 7d = 19 → d = 19/7 ≈ 2.714...
  - a = 6 - 2(19/7) = 6 - 38/7 = 4/7
- Verification: S₅ = 5(4/7) + 10(19/7) = 20/7 + 190/7 = 210/7 = 30 ✓

**Required Verification:**
- Verify a₁₀: 4/7 + 9(19/7) = 4/7 + 171/7 = 175/7 = 25 ✓
- General term: \( a_n = \frac{4}{7} + (n-1)\frac{19}{7} \)
- Sum of the first n terms: \( S_n = \frac{n}{2}(2 \cdot \frac{4}{7} + (n-1)\frac{19}{7}) \)

**Key Checks:**
- Is the system of equations written correctly?
- Are the solutions for a and d correct?
- Verify step completeness

**Failure Modes:**
- Arithmetic sequence formula error
- Error in solving system of equations

---

## 11. Combinatorial Mathematics: Permutation Restrictions

**Test ID:** TC-COMB-001  
**Input:** "Select 4 people from 5 boys and 4 girls to form a committee, including at least 1 girl. How many different selection methods are there?"
**Expected Classification:** combinatorics
**Expected Behavior:**
- Method 1 (complement method): Total number C(9,4) - All boys C(5,4)
  - C(9,4) = 126, C(5,4) = 5 → 121
- Method 2 (different situations): 1 woman, 3 men + 2 women, 2 men + 3 women, 1 man + 4 women, 0 men
  - C(4,1)C(5,3) + C(4,2)C(5,2) + C(4,3)C(5,1) + C(4,4)C(5,0)
  - 4×10 + 6×10 + 4×5 + 1×1 = 40+60+20+1 = 121

**Required Verification:**
- The results of both methods are consistent (121)
- Verify the calculations of each situation one by one
- Make sure there are no omissions or duplications

**Key Checks:**
- Is the complement method applied correctly?
- Is the calculation of C(n,k) correct?
- Have all circumstances been considered?

**Failure Modes:**
- Add directly without considering the combination
- The way of subtracting the total in the complement method is wrong
- Discuss omissions on a case-by-case basis

---

## 12. Probability: Conditional probability

**Test ID:** TC-PROB-001  
**Input:** "There are 3 red balls and 2 blue balls in the bag. Touch it twice without replacing it. Knowing that the red ball was touched the first time, find the probability that the red ball is also touched the second time."
**Expected Classification:** probability_statistics
**Expected Behavior:**
- After touching the red ball for the first time, there are 4 balls left, 2 red and 2 blue.
- P(second red | first red) = 2/4 = 1/2
- Also available definition: P(A∩B)/P(A) = (3/5 × 2/4) / (3/5) = (6/20)/(3/5) = 6/20 × 5/3 = 1/2

**Required Verification:**
- The results of both methods are consistent
- Explain the intuitive meaning of conditional probability
- Effect of sampling without replacement

**Key Checks:**
- Correct application of the definition of conditional probability
- Whether the impact of not replacing is reflected correctly
- Is the result 1/2 reasonable (visual inspection)

**Failure Modes:**
- Misuse of replacement sampling formula
- Conditional probability definition confuses P(A|B) and P(B|A)

---

## 13. Calculus: L'Hôpital's rule for finding limits

**Test ID:** TC-CALC-001  
**Input:** "Find the limit \(\lim_{x \to 0} \frac{e^x - 1 - x}{x^2}\)"
**Expected Classification:** limit
**Expected Behavior:**
- Substitute x→0: numerator 1-1-0=0, denominator 0, 0/0 type
- First L'Hôpital: \( \lim \frac{e^x - 1}{2x} \), still 0/0
- Second time L'Hôpital: \( \lim \frac{e^x}{2} = \frac{1}{2} \)
- Or expand \( e^x = 1 + x + x^2/2 + x^3/6 + ... \)

**Required Verification:**
- Verify that each time L'Hôpital is preceded by 0/0 or ∞/∞ infinitive
- Cross-validation with Taylor expansion: \( e^x - 1 - x = x^2/2 + x^3/6 + ... \), divided by x^2 → 1/2
- Verify numerically: when x=0.001 the approximate value is 0.500000167...

**Key Checks:**
- Whether the conditions of L'Hôpital are met twice
- Final Answer 1/2
- Cross-validation method

**Failure Modes:**
- Apply without checking L'Hôpital conditions
- Do L'Hôpital just once and stop

---

## 14. Derivative Application: Optimization

**Test ID:** TC-CALC-002  
**Input:** "Use a square piece of iron sheet with a side length of 12cm, cut off an identical small square at each of the four corners, and then fold it into a rectangular box without a lid. What is the maximum volume of the box when the side length of the small square is cut off?"
**Expected Classification:** limit, optimization, differentiation
**Expected Behavior:**
- Let the side length of the small square be cut off as x (0 < x < 6)
- The bottom side of the box is 12-2x, and the height is x
- Volume V(x) = x(12-2x)² = 4x(6-x)²
- V'(x) = 4(6-x)² - 8x(6-x) = 4(6-x)[(6-x) - 2x] = 4(6-x)(6-3x)
- Let V'(x) = 0: x=6 or x=2
- x=6 corresponds to volume 0 (minimum), x=2 corresponds to maximum
- Verification: V''(2) < 0
- Maximum volume V(2) = 2 × 8² = 128 cm³

**Required Verification:**
- Give a detailed derivation of V'(x)
- Second derivative test for critical points
- Endpoint test: when x→0, V→0, when x→6, V→0
- Reasonability test of answers

**Key Checks:**
- Is the derivative calculation correct?
- The extreme value judgment is the correct maximum value rather than the minimum value
- Practical meaning: Side length cannot exceed 6

**Failure Modes:**
- Forgot to check the second derivative
- product derivation error
- Not understanding the basic steps of optimization

---

## 15. Substitution integral method

**Test ID:** TC-CALC-003  
**Input:** "Calculate indefinite integral \(\int x\sqrt{2x+1}\,dx\)"
**Expected Classification:** limit, integration
**Expected Behavior:**
- Substitution: Let u = 2x+1, then x = (u-1)/2, dx = du/2
- \( \int \frac{u-1}{2} \cdot \sqrt{u} \cdot \frac{du}{2} = \frac{1}{4} \int (u-1)u^{1/2} du \)
- = \( \frac{1}{4} \int (u^{3/2} - u^{1/2}) du \)
- = \( \frac{1}{4} \left( \frac{2}{5}u^{5/2} - \frac{2}{3}u^{3/2} \right) + C \)
- = \( \frac{1}{10}(2x+1)^{5/2} - \frac{1}{6}(2x+1)^{3/2} + C \)
- can be further simplified to \( \frac{(2x+1)^{3/2}(3x-1)}{15} + C \)

**Required Verification:**
- Derivative verification: Derive the result and check whether it is equal to the original integrand
- Substitute special values ​​for numerical verification

**Key Checks:**
- Conversion of dx in the substitution step
- Algebraic simplification after integration
- Don't forget +C

**Failure Modes:**
- dx conversion error when changing yuan
- Incorrect integration formula application
- Errors in algebraic simplification

---

## 16. Abnormal integral convergence

**Test ID:** TC-CALC-004  
**Input:** "Judge the convergence and divergence of the anomalous integral \(\int_1^\infty \frac{\ln x}{x^2}\,dx\), and find its value if it converges."
**Expected Classification:** limit, integration
**Expected Behavior:**
- First determine the convergence: the growth order of \( \frac{\ln x}{x^2} \)
- For any ε>0, ln x = o(x^ε)
- \( \frac{\ln x}{x^2} = \frac{\ln x}{x^{1/2}} \cdot \frac{1}{x^{3/2}} \leq \frac{C}{x^{3/2}} \) (for sufficiently large x)
- By p-integration, \( \int_1^\infty \frac{1}{x^{3/2}} dx \) converges (p=3/2 > 1)
- According to the comparative discrimination method, the original integral converges
- Calculate integral value: Integration by parts method
- Let u = ln x, dv = dx/x²
  - du = dx/x, v = -1/x
  - \( \int \frac{\ln x}{x^2} dx = -\frac{\ln x}{x} + \int \frac{1}{x^2} dx = -\frac{\ln x}{x} - \frac{1}{x} + C \)
  - \( \lim_{t \to \infty} [-\frac{\ln x}{x} - \frac{1}{x}]_1^t = 0 - 0 - (-0 - (-1)) = 1 \)

**Required Verification:**
- Is the selection of the benchmark p-point of the comparative discrimination method reasonable?
- Are the partial integration steps correct?
- Limit calculation: lim(t→∞) ln(t)/t = 0
- Numerical verification: partial sum approximations

**Key Checks:**
- Prove convergence first and then calculate (key step for anomalous integration)
- Application of comparative discrimination method
- Correctness of integrals by parts

**Failure Modes:**
- Direct calculation without verifying convergence (most common mistake)
- diverges but gives finite values

---

## 17. Multivariate functions: critical points and classification

**Test ID:** TC-MULTI-001  
**Input:** "Find all critical points of the function \(f(x,y) = x^3 + 3xy^2 - 15x - 12y\) and classify them (maximum, minimum or saddle point)."
**Expected Classification:** multivariable_calculus
**Expected Behavior:**
- Find partial derivatives:
  - \( f_x = 3x^2 + 3y^2 - 15 = 3(x^2 + y^2 - 5) \)
  - \( f_y = 6xy - 12 = 6(xy - 2) \)
- Solution f_x = 0: \( x^2 + y^2 = 5 \)
- Solve f_y = 0: \( xy = 2 \)
- Solve the system of equations: x² + y² = 5, xy = 2
  - (x+y)² = x² + y² + 2xy = 5 + 4 = 9 → x+y = ±3
  - (x-y)² = x² + y² - 2xy = 5 - 4 = 1 → x-y = ±1
- Four combinations: 4 critical points
  - (2,1), (1,2), (-1,-2), (-2,-1)
- Hessian matrix: H = [[6x, 6y], ​​[6y, 6x]], det(H) = 36(x² - y²)
- (2,1): det(H)=108>0, f_{xx}=12>0 → local minimum
- (1,2): det(H)=-108<0 → saddle point
- (-1,-2): det(H)=-108<0 → saddle point
- (-2,-1): det(H)=108>0, f_{xx}=-12<0 → local maximum

**Required Verification:**
- Whether the solution to the system of equations is complete
- Is the Hessian determinant classification correct?
- f_{xx} sign check for each critical point

**Key Checks:**
- Can't miss a solution
- Application of Hessian discriminant method
- Distinguish between saddle points and extreme points

**Failure Modes:**
- Missing solution in solving system of equations
- Hessian calculation error
- The classification is reversed (very large/very small)

---

## 18. Matrix eigenvalue problem

**Test ID:** TC-LINALG-001  
**Input:** "Find the eigenvalues ​​and eigenvectors of the matrix \(A = \begin{pmatrix} 2 & 1 & 1 \\ 1 & 2 & 1 \\ 1 & 1 & 2 \end{pmatrix}\)."
**Expected Classification:** linear_algebra
**Expected Behavior:**
- Characteristic equation: det(A - λI) = 0
  - \( \begin{vmatrix} 2-λ & 1 & 1 \\ 1 & 2-λ & 1 \\ 1 & 1 & 2-λ \end{vmatrix} = 0 \)
- Calculate the determinant: \( (2-λ)^3 + 1 + 1 - (2-λ) - (2-λ) - (2-λ) \)
  - = \( (2-λ)^3 - 3(2-λ) + 2 \)
- Let t = 2-λ: t³ - 3t + 2 = (t-1)²(t+2) = 0
- t = 1 (double) or t = -2
- λ = 1 (double) or λ = 4
- Verification trace: tr(A) = 6, sum of eigenvalues ​​= 1+1+4 = 6 ✓
- Eigenvector of λ=1 (solution (A-I)x=0)
- Eigenvector of λ=4 (solution (A-4I)x=0)

**Required Verification:**
- The trace is equal to the sum of eigenvalues
- The determinant is equal to the product of eigenvalues
- Substitution test Av=λv

**Key Checks:**
- Determinant calculation is correct
- Characteristic polynomial factorization
- Basic solution system of eigenvectors

**Failure Modes:**
- Determinant calculation error
- Missing solution for eigenvalues ​​(triple root vs double root + single root)
- Forget about eigenvectors

---

## 19. First-order linear ordinary differential equations

**Test ID:** TC-ODE-001  
**Input:** "Solve the differential equation \(y' + 2xy = x\) such that y(0) = 1."
**Expected Classification:** ordinary_differential_equation
**Expected Behavior:**
- Identified as a first-order linear ODE: \( y' + P(x)y = Q(x) \), P(x) = 2x, Q(x) = x
- Integration factor: \( \mu(x) = e^{\int 2x dx} = e^{x^2} \)
- Multiply both sides: \( e^{x^2}y' + 2xe^{x^2}y = xe^{x^2} \)
- Left = \( \frac{d}{dx}(e^{x^2}y) \)
- Integral: \( e^{x^2}y = \int xe^{x^2} dx = \frac{1}{2}e^{x^2} + C \)
- \( y = \frac{1}{2} + Ce^{-x^2} \)
- Using y(0) = 1: 1 = 1/2 + C → C = 1/2
- Special solution: \( y = \frac{1}{2}(1 + e^{-x^2}) \)

**Required Verification:**
- Substitute into ODE to verify: y' = -xe^{-x^2}, y' + 2xy = -xe^{-x^2} + x(1+e^{-x^2}) = x ✓
- Check initial conditions

**Key Checks:**
- The integration factor is calculated correctly
- Integration steps
- Substitution of initial conditions

**Failure Modes:**
- Memory error in the integral factor formula
- Incorrect integration on the right
- Forgot to use initial conditions to find C

---

## 20. Real analysis: proving consistent continuity

**Test ID:** TC-ANALYSIS-001  
**Input:** "Prove that the function \(f(x) = \sqrt{x}\) is uniformly continuous on \([0, \infty)\)? Give a proof or a counterexample."
**Expected Classification:** real_analysis
**Expected Behavior:**
- Conclusion: Yes, √x is uniformly continuous in [0,∞)
- Proof: For any ε>0, take δ = ε²
- If |x-y| < δ, then |√x - √y| = |x-y|/(√x+√y) ≤ |x-y|/√|x-y| (using √x+√y ≥ √|x-y|)
- And when x,y≥0, |√x-√y|² = |x-y| - 2√xy(1 - sgn(xy)...) ≤ |x-y|
- More concise: |√x - √y| ≤ √|x-y| (√ is 1/2-Hölder continuous)
- So when |x-y| < δ = ε², |√x - √y| ≤ √δ = ε

**Required Verification:**
- whether δ depends only on ε and not on x (uniformly continuous core)
- Is the derivation of the inequality correct?
- Another proof: use compactness in [0,1], bounded by derivatives in [1,∞)

**Key Checks:**
- Understanding of consistent continuity vs. ordinary continuity
- Choice of δ
- Use of inequalities

**Failure Modes:**
- Confusing consistent continuity and ordinary continuity
- Incorrectly determined to be inconsistently continuous
- The inequality in the proof is not rigorous

---

## 21. Abstract Algebra: Properties of Groups

**Test ID:** TC-ALGEBRA-001  
**Input:** "Assume G is a group, prove: if g² = e for any g∈G, then G is a commutative group."
**Expected Classification:** abstract_algebra
**Expected Behavior:**
- For any a,b∈G, it is necessary to prove ab = ba
- Given: (ab)² = e → abab = e
- Multiply both sides by a on the left and b on the right: a(abab)b = aeb → a²bab² = ab
- Since a² = b² = e: ebab = ab → ab = ab (this is wrong, re-derive)
- Correct derivation: (ab)² = e → abab = e
- Left multiplication of a: a(abab) = a → (a²)bab = a → bab = a
- Right multiply b: bab·b = ab → ba·b² = ab → ba = ab
- Prove that G is a commutative group

**Required Verification:**
- Logical basis for each step
- Check whether the associativity of group operations is used correctly
- Conclusion: ba = ab

**Key Checks:**
- Application of associative law
- Reasonableness of every step

**Failure Modes:**
- Skipping intermediate steps, "obviously" reasoning
- Reverse the order of operations

---

## 22. Topology: open sets and closed sets

**Test ID:** TC-TOPOL-001  
**Input:** "In the set R of real numbers (with standard topology), is the set A = [0,1) open? Is it closed? Please explain."
**Expected Classification:** topology
**Expected Behavior:**
- is not an open set: 0 ∈ A but any neighborhood (-ε,ε) of 0 is not completely contained in A (including negative numbers is not in A)
- is not a closed set: the limit point 1 ∉ A (every neighborhood of 1 intersects A), but A does not contain 1
- A = [0,1) neither open nor closed
- But if it is in the subspace topology [0,1], it is open...

**Required Verification:**
- Pointwise negation of open set definition
- Definition of closed set: the complement (-∞,0)∪[1,∞) is not an open set (the neighborhood of 1 is not entirely in the complement set)

**Key Checks:**
- Distinguish between "non-open" and "closed"
- Distinguish between "non-closed" and "open"
- Accurately apply definitions

**Failure Modes:**
- Misjudged as an open set
- Misjudgment as closed set
- Confusing the definition of opening and closing

---

## 23. Number theory: modular arithmetic

**Test ID:** TC-NUMTH-001  
**Input:** "Find the value of 3^100 mod 7."
**Expected Classification:** number_theory
**Expected Behavior:**
- Use Fermat's little theorem: 3⁶ ≡ 1 (mod 7) (because 3 and 7 are relatively prime)
- 100 = 6×16 + 4
- 3¹⁰⁰ = 3⁶·¹⁶⁺⁴ ≡ (3⁶)¹⁶ · 3⁴ ≡ 1¹⁶ · 3⁴ ≡ 3⁴ (mod 7)
- 3⁴ = 81 ≡ 81 - 7×11 = 81 - 77 = 4 (mod 7)
- Answer: 4

**Required Verification:**
- Applicability of Fermat's Little Theorem: 3 and 7 are relatively prime ✓
- Direct calculation verification: 3²=9≡2, 3³=6≡-1, 3⁴=18≡4 ✓
- 3¹⁰⁰ ≡ 4 (mod 7)

**Key Checks:**
- Reference to Fermat's Little Theorem
- Exponential decomposition
- Modulo operation steps

**Failure Modes:**
- Forgot to verify the coprime condition
- Index calculation error

---

## 24. Insufficient conditions problem

**Test ID:** TC-INSUFF-001  
**Input:** "The length of one side of the triangle is 5, find the area."
**Expected Classification:** ambiguous_or_incomplete, geometry
**Expected Behavior:**
- **No direct answers should be given**
- It should be pointed out that the area of ​​a triangle cannot be determined by knowing only the length of one side.
- Specify what additional information is needed (e.g. height, angle, other side lengths, etc.)
- Possibly give a range of values ​​for area (>0 and ≤ upper bound by inequality)

**Required Verification:**
- Whether insufficient conditions are identified
- Whether to request more information
- Whether to explain the reason?

**Key Checks:**
- Never guess or make up conditions
- Be honest about uncertainties and shortcomings

**Failure Modes:**
- Give the "answer" directly (the worst mistake)
- Unaware of insufficient conditions

---

## 25. Out of scope problem

**Test ID:** TC-OUTOFSCOPE-001  
**Input:** "What is the meaning of life?"  
**Expected Classification:** out_of_scope
**Expected Behavior:**
- Recognize that this is not a math problem
- Politely explain that the scope of Math.skill is math problems
- No attempt to answer (even answer 42 is inappropriate)

**Required Verification:**
- Whether it is correctly identified as a non-mathematical question
- Is the reply professional?

**Key Checks:**
- Cannot be treated as a math problem
- Don’t force the answer from a mathematical perspective

**Failure Modes:**
- Try to answer mathematically ("Probabilistically...")
- No sense of boundaries

---

## 26. User request "only answer"

**Test ID:** TC-META-001  
**Input:** "Solve x²-5x+6=0, just give the answer."
**Expected Classification:** equation_solving
**Expected Behavior:**
- Understand user requirements for "answers only"
- But after giving the answer (x=2, 3), one can succinctly suggest the verification steps
- Or just give x=2 or x=3

**Required Verification:**
- Is the answer correct?
- Whether the user's format preferences are respected
- Whether the minimum necessary information is still provided
- Is it possible to retroactively verify

**Key Checks:**
- Whether minimum verification needs to be provided when the user asks for an answer only
- Weigh simplicity and correctness

**Failure Modes:**
- Ignore user requests and output lengthy complete answers
- No verification clues are given at all, users cannot confirm

---

## 27. User request "use junior high school method"

**Test ID:** TC-META-002  
**Input:** "Find the maximum and minimum values ​​of the function f(x)=x²-4x+3 on [0,3]. Use the junior high school method, do not use calculus."
**Expected Classification:** equation_solving, function_analysis
**Expected Behavior:**
- Use the matching method: f(x) = (x-2)² - 1
- The axis of symmetry x=2 is in the interval [0,3]
- The minimum is at the vertex: f(2) = -1
- The maximum value is at the endpoint (farthest from the axis of symmetry): f(0) = 3, f(3) = 0 → the maximum value is 3
- **Do not use derivatives**

**Required Verification:**
- Are derivatives used? (inspection team)
- Are the quadratic function vertex method and endpoint comparison correct?
- Is the endpoint comparison complete?

**Key Checks:**
- Method constraints are observed (no calculus required)
- Solve correctly using collocation method/vertex method

**Failure Modes:**
- Derivatives used (violation of method restrictions)
- Forgot to compare endpoints

---

## 28. False propositions require counterexamples

**Test ID:** TC-PROOF-001  
**Input:** "Judge true or false: If the sequence {a_n} and {b_n} both diverge, then {a_n + b_n} must diverge. Prove or give a counterexample."
**Expected Classification:** real_analysis, counterexample, sequence
**Expected Behavior:**
- Judgment: False
- Counterexample: a_n = n, b_n = -n, then a_n + b_n = 0 (convergence)
- Note: The sum of a diverging sequence may converge

**Required Verification:**
- Is the counterexample correct?
-Explain why it is a counterexample

**Key Checks:**
- Specific counterexamples must be given
- Cannot say "Obviously true"

**Failure Modes:**
- Falsely judge to be true and "prove"
- The counterexample is unreasonable

---

## 29. Minor errors in student answers

**Test ID:** TC-STUDENT-001  
**Input:** "The student solves the equation √(x+5) = x-1 and gets x=4 and x=-1, thinking both are solutions. Please check the student's solution."
**Expected Classification:** equation_solving, solution_checking
**Expected Behavior:**
- Square: x+5 = (x-1)² = x² - 2x + 1
- x² - 3x - 4 = 0 → (x-4)(x+1) = 0 → x=4 or x=-1
- Test x=4: √9 = 3, 4-1 = 3 ✓
- Test x=-1: √4 = 2, -1-1 = -2 ✗
- x=-1 is increasing root
- The final solution is only x=4

**Required Verification:**
- Substitute x=-1 back into the original equation
- Explain why increasing roots occur (square operations are not equivalent)

**Key Checks:**
- Must identify additional roots
- Must explain the reasons for root growth

**Failure Modes:**
- Think the student is absolutely right
- No additional roots found

---

## 30. Generating probability problem

**Test ID:** TC-GEN-001  
**Input:** "Give me a moderately difficult probability question and give me a complete answer."
**Expected Classification:** problem_generation, probability_statistics
**Expected Behavior:**
- Generate a complete and self-consistent probability question
- Questions should contain all necessary information
- Complete solution provided, including steps and final answer
-Answer should include verification

**Required Verification:**
- Is the problem solved?
- Is the answer correct?
- Whether the difficulty is indeed "medium"
- Is the topic self-consistent?

**Key Checks:**
- Cannot generate ambiguous questions
- Unable to generate unsolvable questions
- Are the steps to answer the questions complete?

**Failure Modes:**
- The generated questions are inconsistent with the answers
- The question contains inherent contradictions
- Difficulty mismatch

---

## Test case summary

| Test ID | Category | Difficulty | Key Risks |
|---------|------|------|----------|
| TC-ARITH-001 | Arithmetic | Easy | Precision, Rounding |
| TC-ALG-001 | Algebra | Medium | Domain missing |
| TC-ALG-002 | Algebra | Easy | Interpretation of discriminants |
| TC-ALG-003 | Algebra | Medium | Root augmentation |
| TC-LIN-001 | Algebra | Easy | Arithmetic Error |
| TC-INEQ-001 | Algebra | Medium | Symbol table |
| TC-FUNC-001 | Algebra | Medium | Intersection |
| TC-GEOM-001 | Geometry | Medium | Logic Jump |
| TC-TRIG-001 | Trigonometric | Medium | Formula error |
| TC-SEQ-001 | Sequence | Medium | Misuse of formula |
| TC-COMB-001 | Combination | Medium | Duplicate/Omission |
| TC-PROB-001 | Probability | Medium | Conditional Confusion |
| TC-CALC-001 | Calculus | Medium | L'Hôpital Abuse |
| TC-CALC-002 | Calculus | Medium | Extreme Value Judgment |
| TC-CALC-003 | Calculus | Medium | Substitution error |
| TC-CALC-004 | Calculus | Difficult | Convergence not verified |
| TC-MULTI-001 | Multiple | Difficult | Missing solution |
| TC-LINALG-001 | Line Generation | Medium | Polynomial Factorization |
| TC-ODE-001 | Differential Equations | Medium | Integration Factors |
| TC-ANALYSIS-001 | Analysis | Difficult | Consistent Continuous Understanding |
| TC-ALGEBRA-001 | Abstract Algebra | Difficult | Order of Operations |
| TC-TOPOL-001 | Topology | Medium | Open and closed confusion |
| TC-NUMTH-001 | Number Theory | Medium | Fermat’s Little Theorem |
| TC-INSUFF-001 | Border | Medium | Forced fabrication |
| TC-OUTOFSCOPE-001 | Boundary | Easy | Boundary Awareness |
| TC-META-001 | Interaction | Easy | Format Preference |
| TC-META-002 | Interactive | Medium | Method Limitations |
| TC-PROOF-001 | Proof | Medium | Counterexample awareness |
| TC-STUDENT-001 | Error Correction | Medium | Root Recognition |
| TC-GEN-001 | Generate | Medium | Self-consistency |
