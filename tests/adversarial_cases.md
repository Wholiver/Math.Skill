# Math.skill adversarial test cases

> This document contains 15 adversarial test cases specifically designed to "fool" the system.
> Each use case contains easily overlooked pitfalls that test the defensibility and rigor of Math.skill.

---

## 1. Square introduces increasing roots

**Test ID:** ADV-001  
**Input:** "Solve the equation \(\sqrt{x+3} = x+1\)"
**Expected Classification:** algebra, radical_equation, extraneous_root_trap  
**Expected Behavior:**
- Square: x+3 = (x+1)² = x² + 2x + 1
- x² + x - 2 = 0 → x = 1 or x = -2
- Substitute x=1: √4 = 2, 1+1 = 2 ✓
- Substitute x=-2: √1 = 1, -2+1 = -1 ✗
- x = -2 is increasing root → final solution x = 1

**Required Verification:**
- must be substituted back into the original equation
- Must explicitly state that x=-2 is an increasing root and why

**Key Checks:**
- Are both sides of the square equivalent transformations?
- Is every solution resubstituted?

**Failure Modes:**
- Give two solutions directly without checking
- The explanation of the reasons for root increase is not clear enough

---

## 2. Divide by an expression that may be zero

**Test ID:** ADV-002  
**Input:** "Solve the equation \(\frac{x^2-1}{x-1} = x+1\), note that x≠1"
**Expected Classification:** algebra, rational_equation, removable_singularity_trap  
**Expected Behavior:**
- Note: Even if x≠1 is prompted, you still need to be rigorous
- When x≠1, the numerator factors (x-1)(x+1)
- Left = x+1 (when x≠1)
- The equation becomes x+1 = x+1 (true for all x≠1)
- Solution is: x ∈ ℝ \ {1} (all real numbers not equal to 1)
- Note: When x=1, the denominator is zero and the original formula is undefined.

**Required Verification:**
- cannot give x=1
- Need to understand that this is not "no solution", but "infinitely many solutions (except 1)"
- You may need to use the limit view: lim_{x→1} left = 2 = right, but the function at x=1 is undefined

**Key Checks:**
- Is it given that x can be any real number (except 1)?
- Explain why x=1 is excluded?

**Failure Modes:**
- Say "Identity, x ∈ ℝ" and omit x≠1 (serious)
- Incorrectly called "no solution"
- Directly substitute x=1 and it is considered established.

---

## 3. Symbol table trap in rational inequalities

**Test ID:** ADV-003  
**Input:** "Solve the inequality \(\frac{x-1}{x^2-4} \leq 0\)"
**Expected Classification:** algebra, rational_inequality, sign_chart_trap  
**Expected Behavior:**
- Numerator zero point: x = 1
- Denominator zeros (must be excluded!): x = -2, x = 2
- Symbol table test interval: (-∞,-2), (-2,1), (1,2), (2,∞)
- Note ≤0: When the numerator is 0 (x=1) the inequality holds (0 ≤ 0 ✓)
- Must be excluded when the denominator is 0 (function is undefined)
- Solution set: (-2, 1] ∪ (2, ∞)
- Verification: x=-3 negative number/positive number = negative <0 → (-∞,-2): No!
- Recalculate: x=-3: (-4)/(5)=-0.8<0 ✓
  - x=0: (-1)/(-4)=0.25>0 ✗
  - x=1.5: 0.5/(-1.75)<0 ✓
  - x=3: 2/5>0 ✗
- Correct solution set: (-∞,-2) ∪ (1, 2) ? Need to calculate carefully
  - x=-3: (-4)/(5) = -0.8 ✓ → (-∞,-2) ✓
  - x=0: (-1)/(-4) = 0.25 ✗ → (-2,1) ✗
  - x=1: 0/(-3) = 0 ✓ → x=1 ✓
  - x=1.5: 0.5/(-1.75) = -0.29 ✓ → (1,2) ✓
  - x=3: 2/5 = 0.4 ✗ → (2,∞) ✗
- Solution set: (-∞, -2) ∪ [1, 2)

**Required Verification:**
- Whether each interval of the symbol table is correct
- Treatment of the zero point of the numerator when it contains the equal sign
- Correct handling of denominator zeros

**Key Checks:**
- Is the symbol table created correctly?
- Direction of inequality at x=1 (including equal sign)
- domain exclusion at x=-2 and x=2

**Failure Modes:**
- Symbol table error
- The opening and closing intervals at x=1 are confused
- The denominator zero is not excluded correctly

---

## 4. Composite functions that hide domain restrictions

**Test ID:** ADV-004  
**Input:** "Find the domain of the function \(f(x) = \frac{\ln(x^2-1)}{\sqrt{x-2}}\)."
**Expected Classification:** algebra, domain_analysis, composite_function_trap  
**Expected Behavior:**
- Denominator √(x-2) Condition: x-2 > 0 → x > 2 (the square root must be > 0 because it is still in the denominator)
- Wait a minute: √(x-2) as denominator → x-2 > 0 → x > 2
- Logarithmic condition: ln(x²-1) requires x²-1 > 0 → x < -1 or x > 1
- Take the intersection: x > 2 and (x < -1 or x > 1) = x > 2
- Domain: (2, ∞)

**Required Verification:**
- Conditions for each component
- Whether the intersection calculation considers both parts
- Endpoint test: denominator is zero when x=2

**Key Checks:**
- The square root must be ≥0 or >0 (depending on whether it is in the denominator)
- Conditions for logarithms
- Get the intersection correctly

**Failure Modes:**
- Forgot the condition for the square root in the denominator
- Intersection calculation error

---

## 5. L'Hôpital's Law seems to apply but doesn't

**Test ID:** ADV-005  
**Input:** "Find the limit \(\lim_{x \to 0} \frac{x^2 \sin(1/x)}{x}\)"
**Expected Classification:** calculus, limit, LHopital_not_applicable  
**Expected Behavior:**
- Try L'Hôpital: Nolecular derivative = 2x sin(1/x) + x² cos(1/x) · (-1/x²) = 2x sin(1/x) - cos(1/x)
- Denominator derivative = 1
- But lim_{x→0} cos(1/x) does not exist! So L'Hôpital does not apply
- Correct method: reduce x: lim_{x→0} x sin(1/x) = 0 (pinch theorem: -x ≤ x sin(1/x) ≤ x)
- **The converse of L'Hôpital is not true**: the existence of the limit of the ratio of derivatives is a sufficient but not necessary condition

**Required Verification:**
- It must be stated why L'Hôpital does not apply
- Verify using the pinch theorem
- Explain the conditions of L'Hôpital's law

**Key Checks:**
- Has L'Hôpital been abused?
- Do you understand L'Hôpital's conditions of use?

**Failure Modes:**
- Misusing L'Hôpital and arriving at non-existent/wrong limits
- claims that the limit does not exist (actually it does and is 0)

---

## 6. Misleading Geometry: Impossible Triangle

**Test ID:** ADV-006  
**Input:** "In triangle ABC, AB=5, BC=7, CA=13. Text description, find the area of ​​the triangle."
**Expected Classification:** geometry, triangle_inequality_check, impossible_figure  
**Expected Behavior:**
- Check the triangle inequality: 5+7 = 12 < 13
- This does not satisfy the triangle inequality!
- Such a triangle does not exist
- Instead of giving the area, point out that the triangle cannot exist
- If you use Heron's formula, s = (5+7+13)/2 = 12.5
- √(12.5·7.5·5.5·(-0.5)) will have a negative radicand number

**Required Verification:**
- Triangle inequality check
- Explicitly declare that the triangle does not exist
- Explain why Heron's formula gives imaginary numbers

**Key Checks:**
- Key trap: Will Heron's formula be used blindly?
- Are the most basic geometric axioms ignored?

**Failure Modes:**
- No plausibility checks on side lengths
- Forced use of Helen's formula
- gives an area value

---

## 7. Subtle independence assumption

**Test ID:** ADV-007  
**Input:** "Events A and B satisfy P(A)=0.5, P(B)=0.4, P(A∪B)=0.7. Are A and B independent?"
**Expected Classification:** probability, independence_test, common_trap  
**Expected Behavior:**
- From the addition formula: P(A∪B) = P(A) + P(B) - P(A∩B)
- 0.7 = 0.5 + 0.4 - P(A∩B) → P(A∩B) = 0.2
- Check independence: P(A)·P(B) = 0.5 × 0.4 = 0.2
- P(A∩B) = 0.2 = P(A)·P(B)
- So A and B are independent!

**Required Verification:**
- Correct application of addition formulas
- Correct independence test
- Numerical calculation

**Key Checks:**
- Trap: Many people will directly substitute P(A∪B)=P(A)+P(B) (mutually exclusive assumption)
- Must use addition formula to derive correctly

**Failure Modes:**
- Mistaken for not being independent (intuition is sometimes misleading)
- Error in calculating P(A∩B)

---

## 8. Domain trap in substitution integrals

**Test ID:** ADV-008  
**Input:** "Calculate definite integral \(\int_{-1}^1 \frac{dx}{1+x^2}\)"
**Expected Classification:** calculus, definite_integral, substitution_domain  
**Expected Behavior:**
- Antiderivative: arctan(x)
- ∫_{-1}^{1} dx/(1+x²) = arctan(1) - arctan(-1) = π/4 - (-π/4) = π/2
- If you change the element x = tan θ, you need to pay attention to the range of θ
- x ∈ [-1,1] → θ ∈ [-π/4, π/4]
- ∫ dx/(1+x²) = θ|_{θ=-π/4}^{θ=π/4} = π/4 - (-π/4) = π/2

**Required Verification:**
- If the element is changed, is the domain transformation correct?
- Answer π/2
- The direct method is the same as the substitution method

**Key Checks:**
- Is the conversion time interval conversion correct?
- Are the points values ​​correct?

**Failure Modes:**
- Swap time interval mapping error
- Forgot to change the points limit

---

## 9. The series where the ratio test method fails

**Test ID:** ADV-009  
**Input:** "Judge the convergence and divergence of the series \(\sum_{n=1}^\infty \frac{n!}{n^n}\)."
**Expected Classification:** calculus, series_convergence, ratio_test_edge  
**Expected Behavior:**
- Ratio test: a_n/a_{n+1} = ...
- Actually: lim_{n→∞} a_{n+1}/a_n = lim_{n→∞} (n+1)!/(n+1)^(n+1) · n^n/n!
  = lim n^n/(n+1)^n = lim (n/(n+1))^n = lim (1 - 1/(n+1))^n = 1/e
- 1/e < 1, the series convergence is known from the ratio test
- This is different from intuition (some people will think that n! grows quickly and diverges)

**Required Verification:**
- Are the limits of the ratio test correct?
- Meaning of result < 1
- Other testing methods (such as Stirling's formula)

**Key Checks:**
- Pitfall: Intuitive judgment may be wrong
- Whether the algebra of the ratio test limit calculation is correct

**Failure Modes:**
- Judgment of divergences based on intuition
- Ratio test limit calculation error

---

## 10. Matrix dimensions do not match

**Test ID:** ADV-010  
**Input:** "Let A be a 2×3 matrix and B be a 3×2 matrix. Verify that AB and BA are both meaningful but not experienced the same way. Compute the relationship between tr(AB) and tr(BA)."
**Expected Classification:** linear_algebra, matrix_multiplication, trace_properties  
**Expected Behavior:**
- AB is 2×2, BA is 3×3
- tr(AB) = tr(BA) = Σ_i Σ_j a_{ij} b_{ji} (the cyclic property of the trace is true even if the dimensions are different)
- But AB ≠ BA because they have different dimensions

**Required Verification:**
- Dimensional reasoning
- Application of cyclic properties of traces
- You cannot incorrectly say AB = BA

**Key Checks:**
- Pitfall: Possibly incorrectly assuming AB = BA
- nature of trace
- Dimensional understanding

**Failure Modes:**
- Say AB = BA
- Not understanding the cyclic nature of traces
- Dimensional chaos

---

## 11. Hide the "proof" of division by zero

**Test ID:** ADV-011  
**Input:** "What's wrong with the following proof? Suppose a=b, then a²=ab, a²-b²=ab-b², (a-b)(a+b)=b(a-b), a+b=b, 2b=b, 2=1."
**Expected Classification:** algebra, error_detection, division_by_zero  
**Expected Behavior:**
- The step from (a-b)(a+b) = b(a-b) to a+b = b is divided by (a-b)
- But we know a=b, so a-b = 0
- The step of dividing by zero is illegal
- This explains why the contradictory results were obtained

**Required Verification:**
- Pinpoint the steps to divide by zero
- Explain why it is illegal
- Show correct derivation (cannot eliminate zero factors)

**Key Checks:**
- Can the precise location of the error be found?
- Was the rationale for the error explained?

**Failure Modes:**
- Hidden divide by zero not found
- Thinks "there is something obviously wrong with the proof" but does not point out precisely

---

## 12. Misunderstandings of Bayes’ Theorem

**Test ID:** ADV-012  
**Input:** "The prevalence of a certain disease in the population is 0.1%. The sensitivity of the detection method is 99% (the probability of being detected as positive if the disease is present), and the specificity is also 99% (the probability of being detected as negative without the disease). When someone tests positive, what is the actual probability of having the disease?"
**Expected Classification:** probability, Bayes_theorem, base_rate_fallacy  
**Expected Behavior:**
- It's not 99%!
- P(disease|positive) = P(positive|disease)P(disease) / P(positive)
  = 0.99 × 0.001 / (0.99×0.001 + 0.01×0.999)
  = 0.00099 / (0.00099 + 0.00999)
  = 0.00099 / 0.01098
  ≈ 0.0902 ≈ 9%
- Although the test is very accurate, only about 9% of positive results are actually sick because the underlying prevalence is so low

**Required Verification:**
- Application of Bayesian formula
- Total probability formula calculation P (positive)
- Numerical calculations

**Key Checks:**
- Trap: Many people simply say 99%
- Basic probability fallacy
- Bayesian inference

**Failure Modes:**
- Direct answer 99% (most common Bayesian error)
- Wrong use of formulas

---

## 13. Constraints that appear to be inactive

**Test ID:** ADV-013  
**Input:** "Under the constraint x² + y² ≤ 1, find the maximum and minimum values ​​of f(x,y) = x + y."
**Expected Classification:** optimization, constrained_optimization, boundary_check  
**Expected Behavior:**
- Unconstrained critical point: ∇f = (1,1) ≠ (0,0) → No internal critical point
- The constraint reaches its extreme value on the boundary x²+y²=1
- Lagrange multiplier method or direct solution: x=cos θ, y=sin θ → f(θ)=cos θ + sin θ = √2 sin(θ+π/4)
- Maximum value √2 (θ=π/4), minimum value -√2 (θ=5π/4)

**Required Verification:**
- Check whether there are critical points inside
- Find the extreme value on the boundary
- Whether the constraint is active

**Key Checks:**
- Pitfall: Possibility of mistakenly thinking that a constraint is inactive
- Boundary analysis

**Failure Modes:**
- Ignore constraints
- No Lagrange multiplier method or parameterization required

---

## 14. Discussion of incomplete classification in parametric equations

**Test ID:** ADV-014  
**Input:** "Solve the equation \(ax^2 + (a-1)x - 1 = 0\) for x (a is a parameter)."
**Expected Classification:** algebra, parametric_equation, case_analysis  
**Expected Behavior:**
- Case 1: a = 0 → equation becomes -x - 1 = 0 → x = -1
- Case 2: a ≠ 0 → quadratic equation
- Discriminant: Δ = (a-1)² + 4a = a² - 2a + 1 + 4a = a² + 2a + 1 = (a+1)² ≥ 0
  - x = [-(a-1) ± |a+1|] / (2a)
- Subcase 2a: a+1 ≥ 0 (a ≥ -1 and a≠0)
    - x₁ = -(a-1+a+1)/(2a) = -1
    - x₂ = -(a-1-a-1)/(2a) = 2/(2a) = 1/a
- Subcase 2b: a+1 < 0 (a < -1)
    - x₁ = 1/a
    - x₂ = -1

**Required Verification:**
- Processing of a=0
- The case of a≠0 is covered
- Parametric analysis of discriminant
- Completeness of discussion

**Key Checks:**
- Pitfall: forgetting that the equation degenerates when a=0
- Processing of a in the discriminant
- Completeness of classification

**Failure Modes:**
- Forget the case a=0
- Forget the absolute value when taking the square root of the discriminant
- Classification discussion is incomplete

---

## 15. Correct answer but wrong reason

**Test ID:** ADV-015  
**Input:** "Student answer: Because \(\sqrt{16} = \pm 4\). Is this statement correct?"
**Expected Classification:** arithmetic, notation, conceptual_error  
**Expected Behavior:**
- No!
- The symbol √(16) is defined in the real range as a non-negative square root, which is 4
- The solution to the equation x² = 16 is x = ±4, but this is different from √16 = ±4
- The √ symbol is a function, defined as the principal square root (the non-negative one)
- If a student says √16 = ±4, this is a misuse of symbols

**Required Verification:**
- Distinguish the difference between the √ symbol and the concept of "square root"
- Point out student confusion

**Key Checks:**
- Do you understand the precise definition of the √ symbol?
- Can you differentiate between squaring operations and equation solving?

**Failure Modes:**
- Agree with the student's statement
- Failure to clearly differentiate between the two concepts

---

## Summary of adversarial test cases

| Test ID | Trap Type | Risk Level | Core Defense |
|---------|----------|----------|----------|
| ADV-001 | Square introduction of increasing roots | High | Back-substitution test |
| ADV-002 | Divide by Zero | High | Domain Check |
| ADV-003 | Symbol table trap | High | Interval-by-interval testing |
| ADV-004 | Hidden domain | Medium | Condition-by-condition analysis |
| ADV-005 | L'Hôpital Abuse | High | Condition Verification |
| ADV-006 | Impossible Figure | Height | Triangle Inequality |
| ADV-007 | Independence Intuition Trap | Medium | Formula Calculation |
| ADV-008 | Change domain | Medium | Interval transformation |
| ADV-009 | Conflict between intuition and formula | Medium | Strict calculation |
| ADV-010 | Matrix Dimension Trap | Medium | Dimension Check |
| ADV-011 | Hidden division by zero | High | Algebra Review |
| ADV-012 | Bayesian Fallacy | High | Base Probability |
| ADV-013 | Constraint Liveness | Medium | Boundary Analysis |
| ADV-014 | Incomplete parameter classification | High | Full discussion |
| ADV-015 | Concept Confusion | Medium | Definition Accuracy |
