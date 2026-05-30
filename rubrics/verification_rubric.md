# Verification Rubric (100 Points)

This rubric evaluates the quality of verification performed on a mathematical solution. Verification is the core differentiator of Math.skill.

---

## 1. Back-Substitution into Original (15 points)

Substituting the candidate answer back into the ORIGINAL equation or expression (not a transformed version).

| Score | Criteria |
|-------|----------|
| 15 | Full substitution into original equation/form. All solutions checked. Calculations shown explicitly. |
| 10 | Substitution done but into a transformed form (e.g., squared equation instead of original radical). |
| 5 | Back-substitution mentioned but not shown. "It works" without demonstration. |
| 0 | No back-substitution performed. |

**Examples:**
- **15 pts**: "Check x=1 in original √(x+3)=x+1: √4=2, 1+1=2 ✓. Check x=-2: √1=1, -2+1=-1. 1≠-1 ✗. x=-2 is extraneous."
- **10 pts**: "Check x=1, x=-2 in x+3=(x+1)^2: both work." (verified against transformed equation, not original)
- **5 pts**: "After checking, both solutions are valid."
- **0 pts**: No verification mentioned.

---

## 2. Domain Check (15 points)

Verification that all domain restrictions are satisfied, including implicit ones.

| Score | Criteria |
|-------|----------|
| 15 | Complete domain analysis. All restrictions identified (denominators, radicals, logs, trig inverses, parameter bounds). All solutions checked against domain. |
| 10 | Most domain restrictions checked. One minor restriction missed (e.g., forgot to check log argument at one point). |
| 5 | Some restrictions mentioned but not systematically verified. |
| 0 | Domain completely ignored. Solution includes values outside domain. |

**Checklist:**
- Denominators ≠ 0
- Even-root radicands ≥ 0
- Logarithm arguments > 0
- Inverse trig function input in [-1,1] (for arcsin/arccos) or all ℝ (for arctan)
- Probability parameters in [0,1]
- Matrix dimension compatibility
- Integration interval validity
- Function space membership conditions

---

## 3. Boundary Case Analysis (15 points)

Checking endpoints, critical points, degenerate cases, and parameter boundaries.

| Score | Criteria |
|-------|----------|
| 15 | All boundary cases systematically checked. Endpoints, critical points, non-differentiable points, parameter transition values, degenerate/empty set cases, extreme parameter limits. |
| 10 | Most boundaries checked. One boundary type missed. |
| 5 | Only obvious boundaries checked. |
| 0 | No boundary analysis. |

**Checklist:**
- Endpoints of intervals (for extrema, inequalities, integration)
- Critical points where derivative=0 or DNE
- Non-differentiable points (cusps, corners)
- Parameter boundary values where classification changes
- Extreme/singular cases (zero, infinity, empty set)
- Degenerate cases (e.g., triangle with collinear points)

---

## 4. Counterexample Search (10 points)

Systematic search for counterexamples, especially for proofs, universal claims, and function properties.

| Score | Criteria |
|-------|----------|
| 10 | Systematic search across edge cases and special values. Either no counterexample found (increases confidence) or valid counterexample properly presented and analyzed. |
| 7 | Some counterexample attempts but not systematic. |
| 3 | Counterexample search mentioned but not actually performed. |
| 0 | Not attempted when needed (for proofs, "for all" claims, function property claims). |

**Search domains:**
- Low dimensions (n=0,1,2)
- Boundary values (0, 1, -1, ±∞)
- Identity elements (0 for addition, 1 for multiplication)
- Empty sets and trivial groups
- Degenerate matrices (singular, zero matrix)
- Special function values (0, π/2, π)
- Simple cases that might violate the claim

---

## 5. Numerical Sampling (10 points)

Using specific numerical values to spot-check the solution.

| Score | Criteria |
|-------|----------|
| 10 | Multiple well-chosen sample points. Diverse values (positive, negative, zero, boundary, interior). Results consistent with analytical solution. |
| 7 | Few samples or poorly chosen (all positive, all integers). |
| 3 | One token sample value checked. |
| 0 | No numerical sampling. |

**Sample selection guidance:**
- For functions: test positive, negative, zero, boundary values
- For identities: test at least 3 diverse values
- For inequalities: test points in each interval
- For limits: test values approaching the limit point from both sides
- For trigonometric: test standard angles (0, π/6, π/4, π/3, π/2)
- For probability: test extreme cases (p=0, p=1, p=0.5)

**IMPORTANT**: Numerical sampling is auxiliary. A discrepancy between numerical and analytical results requires re-examination, but numerical agreement alone does NOT constitute a proof.

---

## 6. Independent Method Cross-Validation (15 points)

Verifying the result using a completely different method.

| Score | Criteria |
|-------|----------|
| 15 | Complete second method executed. Both methods agree. Differences analyzed if any. |
| 10 | Partial second method attempted. Agreement confirmed for key steps. |
| 5 | Alternative method mentioned but not executed. |
| 0 | No cross-validation attempted. |

**Method pairings:**
- Algebraic ↔ Geometric
- Analytical ↔ Numerical
- Integration ↔ Differentiation (mutual inverse check)
- Matrix method ↔ Vector geometry
- Direct computation ↔ Generating function
- Induction ↔ Closed form verification

---

## 7. Logic and Quantifier Check (10 points)

Verification of logical structure, quantifier order, and absence of logical fallacies.

| Score | Criteria |
|-------|----------|
| 10 | All quantifiers verified. ∀ and ∃ clearly distinguished. Necessary vs sufficient conditions properly identified. No circular reasoning. No unproven premises used. |
| 7 | Most quantifiers correct. One minor logical imprecision. |
| 3 | Some logical issues present (e.g., confusing ∀x∃y with ∃y∀x). |
| 0 | Significant logical errors. Circular reasoning. Fallacy present. |

**Checklist:**
- Quantifier order correct (∀ε>0 ∃δ>0 ... NOT ∃δ>0 ∀ε>0)
- "If and only if" proven in both directions
- "For all" not confused with "there exists"
- No circular reasoning (conclusion used to prove itself)
- All premises stated and verified
- Contradiction properly derived (in proof by contradiction)
- Induction base case and inductive step both verified

---

## 8. Error Backtracking and Correction (10 points)

Behavior when verification reveals an error.

| Score | Criteria |
|-------|----------|
| 10 | Error systematically located. Backtracked to last reliable step. Error corrected with explanation. Recalculated. Re-verified. |
| 7 | Error identified but correction incomplete. Partial backtracking. |
| 3 | Error mentioned but not properly fixed. Same or related error persists. |
| 0 | Error ignored or denied. Incorrect answer maintained despite verification failure. |

**Protocol when error is found:**
1. Identify the exact step where the error occurred
2. Explain WHY it's wrong (not just "this is wrong")
3. Backtrack to the last correct conclusion
4. Redo the derivation from that point
5. Re-verify the corrected result
6. If the error cannot be fixed, state uncertainty clearly

---

## Total Score Interpretation

| Score | Grade | Verification Quality |
|-------|-------|---------------------|
| 90-100 | A | Excellent verification. Multiple methods, all edge cases, systematic. |
| 80-89 | B | Good verification. One or two minor gaps. |
| 70-79 | C | Adequate verification. Some important cases missed. |
| 60-69 | D | Weak verification. Significant gaps. |
| Below 60 | F | Inadequate verification. Result is unreliable regardless of correctness. |

**Critical Rule**: If verification score < 50, the answer MUST NOT be considered reliable, even if it happens to be correct.
