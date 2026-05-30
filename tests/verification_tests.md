# Verification Engine Test Cases

Test cases designed specifically to stress-test the verification engine. Each test presents a mathematical claim that may or may not be correct.

---

## Test 1: Correct Equation Solution

**Test ID:** V-001
**Input:** "Check my answer: I solved x^2 - 5x + 6 = 0 and got x = 2 or x = 3."
**Expected Behavior:** Verify by back-substitution: 2^2-5·2+6=4-10+6=0 ✓, 3^2-5·3+6=9-15+6=0 ✓. Confirm both are correct.
**Required Verification:** Back-substitution into ORIGINAL equation
**Key Checks:** Both roots checked, no rounding errors
**Failure Modes:** Checking only one root, checking against factored form instead of original

---

## Test 2: Extraneous Root Not Detected

**Test ID:** V-002
**Input:** "I solved √(x+3) = x+1. I squared both sides: x+3 = (x+1)^2. Simplified: x+3 = x^2+2x+1. So x^2+x-2 = 0. Factor: (x+2)(x-1)=0. Answer: x = -2 or x = 1."
**Expected Behavior:** Detect that x=-2 gives √(1)=-1 which is false. Back-substitution catches this. Correct answer: x=1 only.
**Required Verification:** Back-substitution into original radical equation
**Key Checks:** Both candidate solutions checked against original, not squared form
**Failure Modes:** Only checking against squared equation, accepting both without domain check

---

## Test 3: Identity Verification

**Test ID:** V-003
**Input:** "Is (a+b)^2 = a^2 + b^2 true?"
**Expected Behavior:** Expand left: a^2+2ab+b^2 ≠ a^2+b^2. Identity is FALSE. Provide counterexample: a=1, b=1 gives LHS=4, RHS=2.
**Required Verification:** Expansion + numerical counterexample
**Key Checks:** All terms accounted for
**Failure Modes:** Missing the 2ab term, visual pattern matching without expansion

---

## Test 4: False Identity with Numerical Counterexample

**Test ID:** V-004
**Input:** "Prove that x^2 + x + 1 > 0 for all real x."
**Expected Behavior:** This IS true (discriminant = 1-4 = -3 < 0, parabola opens up). Verify by completing square: (x+1/2)^2 + 3/4 > 0. Numerical verification: x=0 gives 1>0, x=-1 gives 1>0, x=-0.5 gives 0.75>0. Domain check complete.
**Required Verification:** Completing square + numerical sampling + discriminant
**Key Checks:** Discriminant sign, completing square correctly
**Failure Modes:** False claim of counterexample when none exists

---

## Test 5: Derivative Verification by Integration

**Test ID:** V-005
**Input:** "I found d/dx[ln(x^2+1)] = 2x/(x^2+1). Is this correct?"
**Expected Behavior:** Verify by chain rule: d/dx[ln(u)] = (1/u)·du/dx = 1/(x^2+1)·2x = 2x/(x^2+1). Correct. Also integrate result: ∫2x/(x^2+1)dx = ln(x^2+1)+C. Back-derivative matches.
**Required Verification:** Chain rule check + reverse integration
**Key Checks:** Domain (x^2+1>0 always true), integration constant
**Failure Modes:** Missing the 2x factor, domain issues with ln

---

## Test 6: Incorrect Derivative Detection

**Test ID:** V-006
**Input:** "d/dx[x^x] = x·x^(x-1)"
**Expected Behavior:** This is WRONG. Correct: x^x = e^(x ln x). d/dx = e^(x ln x)·(ln x + 1) = x^x(ln x + 1). The student incorrectly used power rule which only applies when exponent is constant.
**Required Verification:** Logarithmic differentiation, numerical check at x=2
**Key Checks:** Power rule vs exponential rule distinction
**Failure Modes:** Not recognizing that both base and exponent are variable

---

## Test 7: Integral Verification

**Test ID:** V-007
**Input:** "I computed ∫(2x+1)/(x^2+x+1) dx = ln|x^2+x+1| + C"
**Expected Behavior:** Substitute u=x^2+x+1, du=(2x+1)dx. Integral = ∫du/u = ln|u|+C = ln|x^2+x+1|+C. Correct. Verify by differentiation: d/dx[ln(x^2+x+1)] = (2x+1)/(x^2+x+1). Domain: x^2+x+1 always >0.
**Required Verification:** Differentiation of result
**Key Checks:** Domain (no absolute value needed), u-substitution correct
**Failure Modes:** Forgetting +C, sign errors in differentiation

---

## Test 8: Integral with Missing Constant

**Test ID:** V-008
**Input:** "∫cos(2x) dx = sin(2x) + C"
**Expected Behavior:** WRONG. Correct: ∫cos(2x)dx = (1/2)sin(2x) + C. Verify: d/dx[(1/2)sin(2x)] = (1/2)·2cos(2x) = cos(2x) ✓. Student's answer gives derivative of 2cos(2x), which is wrong. Missing factor 1/2 from chain rule.
**Required Verification:** Differentiation of candidate result
**Key Checks:** Chain rule factor from substitution u=2x
**Failure Modes:** Forgetting to divide by coefficient in chain rule

---

## Test 9: Eigenvalue Verification

**Test ID:** V-009
**Input:** "For A = [[2,1],[1,2]], I found eigenvalues λ=1 and λ=3."
**Expected Behavior:** Verify: det(A-1I)=det([[1,1],[1,1]])=0 ✓. det(A-3I)=det([[-1,1],[1,-1]])=0 ✓. Verify Av=λv for each: for λ=3, v=[1,1], Av=[3,3]=3[1,1] ✓. For λ=1, v=[1,-1], Av=[1,-1]=1[1,-1] ✓. Correct.
**Required Verification:** det(A-λI)=0 AND Av=λv
**Key Checks:** Both conditions, trace(2+2=4=1+3) ✓, det=4-1=3=1·3 ✓
**Failure Modes:** Only checking determinant equation, not eigenvectors

---

## Test 10: Incorrect Eigenvalue

**Test ID:** V-010
**Input:** "For A = [[1,2],[2,1]], eigenvalues are λ=0 and λ=2."
**Expected Behavior:** WRONG. det(A-λI)=(1-λ)^2-4=λ^2-2λ-3=(λ-3)(λ+1)=0. Correct λ=3 or λ=-1. Student's answer fails det check: det(A-2I)=det([[-1,2],[2,-1]])=1-4=-3≠0.
**Required Verification:** det(A-λI)=0 computation
**Key Checks:** Determinant calculation accuracy, trace consistency (1+1=2≠0+2)
**Failure Modes:** Arithmetic error in computing determinant

---

## Test 11: ODE Solution Verification

**Test ID:** V-011
**Input:** "y''-3y'+2y=0, solution: y=Ce^x + De^{2x}"
**Expected Behavior:** Characteristic eq: r^2-3r+2=0 → r=1,2. Correct. Verify: y'=Ce^x+2De^{2x}, y''=Ce^x+4De^{2x}. Substitute: (Ce^x+4De^{2x})-3(Ce^x+2De^{2x})+2(Ce^x+De^{2x}) = Ce^x(1-3+2)+De^{2x}(4-6+2)=0 ✓.
**Required Verification:** Substitution into ODE
**Key Checks:** Two constants for second-order, both independent solutions verified
**Failure Modes:** Only checking one solution, missing that both terms must cancel

---

## Test 12: Inequality with Missed Boundary

**Test ID:** V-012
**Input:** "Solve: x/(x-1) ≥ 0. Solution: x ∈ [0,+∞)"
**Expected Behavior:** WRONG. Forgot x≠1 (denominator zero). Sign chart: critical points x=0,1. Intervals: (-∞,0]: negative, [0,1): positive, (1,+∞): positive. Correct: x ∈ [0,1) ∪ (1,+∞). Also need to check x=0 is included (0≥0) ✓.
**Required Verification:** Domain check (denominator) + boundary point sampling
**Key Checks:** Denominator restriction, sign chart completeness
**Failure Modes:** Forgetting domain restriction, missing the need to split at x=1

---

## Test 13: Limit Claim Verification

**Test ID:** V-013
**Input:** "lim(x→0) (sin x)/x = 1"
**Expected Behavior:** TRUE. Verify by squeeze theorem (geometric argument) or Taylor series: sin x = x - x^3/6 + O(x^5), so (sin x)/x = 1 - x^2/6 + O(x^4) → 1. Numerical: x=0.1→0.9983, x=0.01→0.99998, x=0.001→0.9999998.
**Required Verification:** Taylor expansion AND numerical sampling
**Key Checks:** Multiple methods agree, numerical trend approaching 1
**Failure Modes:** Using L'Hôpital without checking conditions (actually it works here), numerical rounding errors

---

## Test 14: Proof with Logical Gap

**Test ID:** V-014
**Input:** "Prove: If n^2 is even, then n is even."
**Student proof:** "If n^2 is even, then n^2=2k. So n=√(2k). Since √(2k) can't be odd, n must be even."
**Expected Behavior:** Proof has a gap - "√(2k) can't be odd" is not justified. Correct proof: contrapositive. If n is odd, n=2m+1, n^2=4m^2+4m+1=2(2m^2+2m)+1, which is odd. Therefore if n^2 is even, n must be even.
**Required Verification:** Logical structure check, quantifier verification
**Key Checks:** The step "can't be odd" needs justification, contrapositive removes the gap
**Failure Modes:** Accepting hand-wavy justification as rigorous proof

---

## Test 15: Well-Definedness Failure

**Test ID:** V-015
**Input:** "Define f: Z_6 → Z_3 by f([x]_6) = [x]_3. Is this well-defined?"
**Expected Behavior:** YES, it IS well-defined. Check: If [x]_6 = [y]_6, then 6|(x-y), so 3|(x-y), meaning [x]_3 = [y]_3. Verify for examples: f([0]_6)=[0]_3, f([2]_6)=[2]_3, f([5]_6)=[2]_3, f([6]_6)=[0]_3.
**Required Verification:** Check that 6|(x-y) ⇒ 3|(x-y) AND test numerical examples
**Key Checks:** Transitivity of divisibility, consistency of mapping
**Failure Modes:** Forgetting to check well-definedness, confusing 6 and 3 moduli
