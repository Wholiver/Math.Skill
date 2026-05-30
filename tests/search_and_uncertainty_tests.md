# Search and Uncertainty Test Cases

Test cases for search-triggering scenarios and handling of uncertain/unknown mathematical questions.

---

## Test 1: Recent Mathematical Result

**Test ID:** SU-001
**Input:** "What's the current progress on the Riemann Hypothesis?"
**Expected Classification:** research_level_problem
**Expected Behavior:** State that RH remains unproven. Provide known results: verified for first 10^13 zeros, at least 40% of zeros on critical line, equivalent to many other statements. Suggest searching arXiv for recent developments if needed. Be clear about what IS proven vs what is NOT.
**Required Verification:** Factual accuracy of known results
**Key Checks:** Distinguish verified facts from conjectures, date of information
**Failure Modes:** Claiming it's solved, giving outdated information, fabricating a "proof"

---

## Test 2: Known Open Problem Identification

**Test ID:** SU-002
**Input:** "Prove that every even number greater than 2 can be expressed as the sum of two primes."
**Expected Classification:** research_level_problem, number_theory
**Expected Behavior:** Identify as Goldbach's conjecture (1742). State: unproven. Provide known results: verified up to 4×10^18, Chen's theorem (every sufficiently large even = prime + semiprime), ternary Goldbach proven. Do NOT attempt a fake proof. If user asks for specific number, can demonstrate decomposition.
**Required Verification:** Accuracy of historical facts, Chen's theorem statement
**Key Checks:** Honest about unproven status, provides useful partial information
**Failure Modes:** Claiming to prove it, fabricating a "recent breakthrough"

---

## Test 3: Textbook Formula Verification

**Test ID:** SU-003
**Input:** "My textbook says ∫dx/√(a^2-x^2) = arcsin(x/a) + C. Is this correct for all a?"
**Expected Classification:** integration
**Expected Behavior:** Verify: derivative of arcsin(x/a) = 1/√(1-(x/a)^2)·(1/a) = 1/√(a^2-x^2) ✓. But note: a must be positive, and domain is |x|<|a|. The formula is correct with these conditions.
**Required Verification:** Differentiation, domain analysis
**Key Checks:** Absolute value vs sign of a, domain restriction
**Failure Modes:** Not checking domain, sign issues with negative a

---

## Test 4: Named Theorem Reference

**Test ID:** SU-004
**Input:** "What conditions are needed to apply the Sokhotski-Plemelj theorem?"
**Expected Classification:** complex_analysis, research_level_problem
**Expected Behavior:** State the theorem: for a function φ satisfying Hölder condition on a contour, the limiting values of the Cauchy-type integral satisfy specific jump relations. Provide conditions (Hölder continuity, smooth contour). If uncertain about details, suggest consulting authoritative sources.
**Required Verification:** Accuracy of theorem statement
**Key Checks:** Hölder condition requirement, contour smoothness
**Failure Modes:** Confusing with other theorems, wrong conditions

---

## Test 5: Competition Problem Reference

**Test ID:** SU-005
**Input:** "Find all functions f: ℝ→ℝ such that f(x+f(y)) = f(x) + y for all real x,y."
**Expected Classification:** function_analysis, research_level_problem
**Expected Behavior:** This is a functional equation. Step-by-step: Set y=0 → f(x+f(0))=f(x). Set x=0 → f(f(y))=f(0)+y. Show f is bijective. Then f(0)=0. Prove f(x)=x and f(x)=-x are solutions. Verify both. Note: this is similar to Cauchy-type functional equations seen in competitions.
**Required Verification:** Both solutions verified by substitution
**Key Checks:** Bijectivity proof, all steps reversible
**Failure Modes:** Missing the negative solution, assuming continuity without proof

---

## Test 6: OEIS Sequence Reference

**Test ID:** SU-006
**Input:** "What's the closed form of the sequence 1, 1, 2, 3, 5, 8, 13, 21, ...?"
**Expected Classification:** sequence
**Expected Behavior:** This is Fibonacci. Closed form (Binet): F_n = (φ^n-ψ^n)/√5 where φ=(1+√5)/2, ψ=(1-√5)/2. Provide derivation via characteristic equation. No search strictly needed for this well-known sequence.
**Required Verification:** Verify formula for n=1,2,3,8
**Key Checks:** Both terms needed for integer result, √5 cancellation
**Failure Modes:** Only giving φ^n/√5 approximation, not exact form

---

## Test 7: Mathematical Constant Uncertainty

**Test ID:** SU-007
**Input:** "What is the exact value of sin(18°)?"
**Expected Classification:** trigonometry
**Expected Behavior:** sin(18°)= (√5-1)/4. Derivation: using sin(5θ) formula or geometric construction with regular pentagon. Verify: compute sin(18°) numerically ≈ 0.309017, (√5-1)/4 ≈ 0.309017. Both match.
**Required Verification:** Numerical comparison, pentagon geometry consistency
**Key Checks:** Exact radical form correctness
**Failure Modes:** Confusing sin(18°) with sin(36°), wrong sign

---

## Test 8: Solution Comparison Request

**Test ID:** SU-008
**Input:** "Compare my solution of ∫tan(x)dx with the standard one. My answer: -ln|cos(x)|+C. Standard: ln|sec(x)|+C."
**Expected Classification:** integration, solution_checking
**Expected Behavior:** Both are equivalent! -ln|cos(x)| = ln|cos(x)|^(-1) = ln|1/cos(x)| = ln|sec(x)|. Both correct. Verify by differentiating both: d/dx[-ln|cos(x)|] = tan(x) ✓, d/dx[ln|sec(x)|] = tan(x) ✓.
**Required Verification:** Differentiation of both forms, algebraic equivalence
**Key Checks:** Logarithm properties, domain restrictions
**Failure Modes:** Claiming they're different, missing the equivalence

---

## Test 9: Standard Definition Lookup

**Test ID:** SU-009
**Input:** "What's the formal ε-δ definition of a limit?"
**Expected Classification:** limit, real_analysis
**Expected Behavior:** lim(x→a) f(x)=L iff ∀ε>0 ∃δ>0 such that 0<|x-a|<δ ⇒ |f(x)-L|<ε. Explain each quantifier, provide example. No external search needed for this standard definition.
**Required Verification:** Correct quantifier order, example application
**Key Checks:** The "0<" excludes the point itself, δ depends on ε and potentially a
**Failure Modes:** Reversing quantifier order, forgetting the 0< part

---

## Test 10: Counterexample Search

**Test ID:** SU-010
**Input:** "Is it true that if f'(0) exists, then f is differentiable in a neighborhood of 0?"
**Expected Classification:** counterexample, real_analysis
**Expected Behavior:** FALSE. Counterexample: f(x)=x^2 for rational x, f(x)=0 for irrational x. f'(0)=lim(h→0) f(h)/h. For rational h: h^2/h=h→0. For irrational h: 0/h=0→0. So f'(0)=0. But f is not differentiable at any x≠0 (in fact, not even continuous). Verify f'(0) computation carefully using squeeze theorem.
**Required Verification:** Limit computation at 0, non-differentiability check at x≠0
**Key Checks:** Two-sided limit works at 0, nowhere continuous elsewhere
**Failure Modes:** Confusing existence of derivative at a point with local differentiability

---

## Test 11: Integer Sequence Closed Form

**Test ID:** SU-011
**Input:** "Is there a closed form for a_n = a_{n-1} + a_{n-2}^2 with a_0=0, a_1=1?"
**Expected Classification:** sequence, research_level_problem
**Expected Behavior:** This is a nonlinear recurrence. No known simple closed form exists. The sequence grows super-exponentially. Can analyze asymptotic behavior: roughly doubly exponential. Be honest: "This nonlinear recurrence has no known elementary closed form. Here's what we can say about its growth rate..."
**Required Verification:** Compute first few terms to verify understanding
**Key Checks:** Honest about lack of closed form, asymptotic analysis
**Failure Modes:** Fabricating a fake closed form, claiming it can't be analyzed at all

---

## Test 12: Standard Definition Verification

**Test ID:** SU-012
**Input:** "What's the difference between 'compact' in metric spaces vs general topological spaces?"
**Expected Classification:** topology
**Expected Behavior:** In metric spaces: compact ⇔ sequentially compact ⇔ complete and totally bounded ⇔ every sequence has convergent subsequence. In general topological spaces: compact means every open cover has finite subcover. Sequential compactness is NOT equivalent to compactness in general. Provide counterexample: the ordinal space [0,ω_1) is sequentially compact but not compact.
**Required Verification:** Definitions accuracy, counterexample validity
**Key Checks:** Distinguishing metric vs general topology equivalence
**Failure Modes:** Assuming metric space equivalences hold in general topology
