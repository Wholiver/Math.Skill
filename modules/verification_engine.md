# Verification Engine

## Overview

The Verification Engine is the core quality-control system of Math.skill. Every solution output by this skill must pass at least **two independent verification methods** before being presented to the user. Verification is not optional; a failed verification is treated as an error signal requiring backtracking and correction (see `SKILL.md`, Section 16: Failure Handling).

This document defines all 11 verification methods (A through K), including:
- **When to apply**: Problem types and conditions that make each method applicable
- **How to apply**: Step-by-step procedure
- **Examples**: Concrete demonstrations
- **Failure handling**: What to do when a method detects an error

---

## Method Selection by Problem Type

The following table maps problem classifications to recommended verification methods. The first listed method is the primary; the second is the fallback or complement. At least two must be applied; three or more increase confidence for difficult or high-stakes problems.

**Method Numbering Note**: Methods are labeled A through K (11 total). The letters are mnemonic: A=Back-substitution, B=Boundary/Domain, C=Continuity/Boundary, D=Derivation(reverse), E=Estimation(numerical), F=Dimension(Formula), G=Special cases/limits, H=Independent method, I=Counterexample, J=Logic(formal), K=Consistency(computational).

| Problem Classification | Primary Method | Secondary Method | Tertiary Method |
|---|---|---|---|
| `calculation` | E (Numerical) | A (Back-substitution) | — |
| `algebra_simplification` | A (Back-substitution) | E (Numerical) | G (Special cases) |
| `equation_solving` | A (Back-substitution) | B (Domain check) | G (Special cases) |
| `system_of_equations` | A (Back-substitution) | B (Domain check) | E (Numerical) |
| `inequality_solving` | B (Domain check) | C (Boundary) | E (Numerical) |
| `function_analysis` | E (Numerical) | G (Limits/special) | H (Independent method) |
| `geometry` | B (Domain/conditions) | G (Special cases) | H (Independent method) |
| `analytic_geometry` | A (Back-substitution) | E (Numerical) | H (Independent method) |
| `trigonometry` | A (Back-substitution) | E (Numerical) | G (Special cases) |
| `sequence` | E (Numerical) | G (Limits) | H (Independent method) |
| `combinatorics` | E (Numerical) | H (Independent method) | I (Counterexample) |
| `probability_statistics` | E (Numerical) | H (Independent method) | K (Consistency) |
| `limit` | B (Domain) | E (Numerical) | G (Limits) |
| `differentiation` | E (Numerical) | H (Independent method) | K (Consistency) |
| `integration` | D (Reverse derivation) | E (Numerical) | H (Independent method) |
| `multivariable_calculus` | E (Numerical) | H (Independent method) | K (Consistency) |
| `linear_algebra` | A (Back-substitution) | E (Numerical) | H (Independent method) |
| `ordinary_differential_equation` | A (Back-substitution) | E (Numerical) | H (Independent method) |
| `complex_analysis` | E (Numerical) | H (Independent method) | K (Consistency) |
| `real_analysis` | G (Limits/special) | J (Formal logic) | H (Independent method) |
| `abstract_algebra` | A (Back-substitution) | J (Formal logic) | I (Counterexample) |
| `topology` | J (Formal logic) | I (Counterexample) | H (Independent method) |
| `number_theory` | E (Numerical) | H (Independent method) | I (Counterexample) |
| `discrete_math` | E (Numerical) | H (Independent method) | I (Counterexample) |
| `optimization` | A (Back-substitution) | C (Boundary) | E (Numerical) |
| `mathematical_modeling` | E (Numerical) | K (Consistency) | H (Independent method) |
| `proof` | J (Formal logic) | I (Counterexample) | G (Special cases) |
| `counterexample` | A (Back-substitution) | I (Counterexample) | — |
| `solution_checking` | A (Back-substitution) | B (Domain) | E (Numerical) |
| `problem_generation` | A (Back-substitution) | E (Numerical) | H (Independent method) |
| `research_level_problem` | All applicable | All applicable | All applicable |

### Method Applicability Matrix

To avoid overlap and clarify when each method should be used:

| Method | Best For | Not Suitable For | Unique Strength |
|---|---|---|---|
| A (Back-substitution) | Equations, systems, explicit solutions | Proofs, existence claims | Directly verifies solution satisfies original conditions |
| B (Domain check) | ALL problems (universal pre-check) | None — always applicable | Catches extraneous solutions from non-reversible steps |
| C (Boundary check) | Inequalities, optimization, intervals | Discrete problems without natural boundaries | Tests edge behavior where errors often hide |
| D (Reverse derivation) | Proofs, derivations, integration | Numerical answers without derivation chain | Validates logical flow reversibility |
| E (Numerical sampling) | Quantitative problems, identities | Pure existence proofs, symbolic manipulation only | Quick sanity check with concrete values |
| F (Dimensional analysis) | Physics problems, formulas with units | Pure mathematics without physical interpretation | Structural validation of formula form |
| G (Limits/special cases) | Functions, sequences, series, calculus | Finite combinatorics without parameters | Reveals asymptotic and degenerate behavior |
| H (Independent method) | Problems with multiple solution approaches | Problems with only one known method | Strongest confidence via independent derivation |
| I (Counterexample) | Universal claims, conjectures, "true/false" | Constructive existence proofs | Definitively disproves false claims |
| J (Formal logic) | Proofs, abstract math, quantified statements | Computational problems | Catches reasoning errors that survive algebraic checks |
| K (Computational consistency) | Matrix operations, statistics, multi-step computation | Simple single-step calculations | Uses invariants to catch propagation errors |

---

## Method A: Back-Substitution

### When to Apply

Back-substitution is the most fundamental verification method. Apply it whenever the solution is a specific value, expression, or function that can be substituted back into the original condition.

### How to Apply

1. Take the final answer (value, expression, function, or tuple of values)
2. Substitute it into **every** original equation, inequality, or condition
3. Simplify and verify that each equality holds exactly or that each inequality is satisfied
4. If the problem involves multiple conditions, check them all — not just the last one used in solving

### Step-by-Step Procedure

**For a single equation $f(x) = g(x)$ with solution $x = x_0$:**

1. Compute $f(x_0)$ — substitute $x_0$ everywhere $x$ appears
2. Compute $g(x_0)$ similarly
3. Verify $f(x_0) = g(x_0)$
4. If $f(x_0)$ or $g(x_0)$ is undefined (division by zero, negative radicand, etc.), the solution is invalid

**For a system of equations:**

1. Substitute the solution tuple into each equation independently
2. All equations must be satisfied simultaneously
3. If only some equations hold, the solution is incorrect

**For a differential equation $y' = f(x, y)$ with solution $y(x)$:**

1. Differentiate $y(x)$ to obtain $y'(x)$
2. Substitute both $y(x)$ and $y'(x)$ into the DE
3. Simplify and verify the identity holds
4. Also substitute initial/boundary conditions if provided

### Example

**Problem**: Solve $x^2 - 5x + 6 = 0$

**Claimed solution**: $x = 2$ and $x = 3$

**Verification**:
- For $x = 2$: $2^2 - 5(2) + 6 = 4 - 10 + 6 = 0$ ✓
- For $x = 3$: $3^2 - 5(3) + 6 = 9 - 15 + 6 = 0$ ✓

Both solutions pass back-substitution.

### Failure Handling

If back-substitution fails:
- The equation $f(x_0) \neq g(x_0)$ indicates an algebraic error in solving
- If a solution makes a denominator zero or a radicand negative even though the left equals the right after simplification, flag it as extraneous (should have been caught by domain check, Method B)
- Re-examine the solving steps from the beginning; back-substitution typically catches algebraic errors, sign errors, or lost solutions

---

## Method B: Domain Check

### When to Apply

Apply Domain Check to **every** problem. It is the most broadly applicable verification method. Domain violations are among the most common and hardest-to-spot errors in mathematical reasoning.

### How to Apply

1. **Before solving**: Identify all implicit domain constraints from the problem statement
2. **During verification**: Check that every intermediate step respects these constraints
3. **After solving**: Verify the final solution lies within the domain

### Domain Constraint Checklist

| Expression Type | Constraint |
|---|---|
| Denominator $1/f(x)$ | $f(x) \neq 0$ |
| Even root $\sqrt[2n]{f(x)}$ | $f(x) \geq 0$ |
| Logarithm $\log(f(x))$ | $f(x) > 0$ |
| Tangent $\tan(f(x))$ | $f(x) \neq \frac{\pi}{2} + k\pi$ |
| Arcsine $\arcsin(f(x))$ | $-1 \leq f(x) \leq 1$ |
| Fractional exponent $[f(x)]^{p/q}$ ($q$ even) | $f(x) \geq 0$ |
| Division by variable in any form | variable $\neq 0$ |
| Function with restricted domain | Stated domain for the function |

### Example

**Problem**: Solve $\frac{x+1}{x-2} = 3$

**Domain**: $x \neq 2$

**Solving**: $x+1 = 3(x-2) \implies x+1 = 3x-6 \implies 7 = 2x \implies x = \frac{7}{2}$

**Domain check**: $x = \frac{7}{2} \neq 2$ ✓ — solution is valid

**Counterexample (domain violation)**:

**Problem**: Solve $\frac{x+1}{x-2} = \frac{3x}{x-2}$

**Naive solving**: Multiply both sides by $(x-2)$: $x+1 = 3x \implies 1 = 2x \implies x = \frac{1}{2}$

**Domain check**: $x = \frac{1}{2}$ is valid ($\neq 2$), but wait — the equation implies both denominators are zero at $x=2$, however that's outside the domain so it doesn't invalidate the solution. $x = \frac{1}{2}$ passes the domain check.

### Failure Handling

- If the solution violates a domain constraint, it is extraneous — remove it from the solution set
- If an intermediate step divides by an expression that could be zero, revisit that step and handle the zero case separately
- Domain violations often arise from squaring both sides, multiplying by variable expressions, or applying functions with restricted domains

---

## Method C: Boundary Check

### When to Apply

Apply when the solution involves inequalities, optimization, or any problem where the answer is "achieved at" some boundary. Also apply as a sanity check for any problem with a natural domain boundary.

### How to Apply

1. Identify all boundaries: interval endpoints, parameter limits, zero, infinity, empty set
2. Test the boundary values in the original problem
3. Verify the solution behaves reasonably at boundaries

### Types of Boundary Checks

**Inequality boundaries**: Test points just inside and just outside the claimed solution interval(s). The inequality should hold inside and fail outside.

**Optimization boundaries**: The maximum/minimum must either be at a critical point in the interior or at a boundary. Verify both.

**Degenerate cases**: Test the boundary where a parameter equals zero, one, or infinity. Does the solution reduce to a known special case?

### Example

**Problem**: Solve $x^2 - 4 \leq 0$

**Claimed solution**: $-2 \leq x \leq 2$

**Boundary check**:
- $x = -2$: $(-2)^2 - 4 = 0 \leq 0$ ✓
- $x = 2$: $2^2 - 4 = 0 \leq 0$ ✓
- $x = -2.1$ (just outside): $4.41 - 4 = 0.41 > 0$ — fails, correct ✓
- $x = 2.1$ (just outside): $4.41 - 4 = 0.41 > 0$ — fails, correct ✓
- $x = 0$ (center): $0 - 4 = -4 \leq 0$ ✓

The solution interval is correctly bounded.

### Failure Handling

- If boundary values don't satisfy the original inequalities, the interval endpoints are wrong
- If the inequality holds at values outside the claimed interval, the interval is too narrow
- For optimization, if the optimum at a boundary contradicts the interior critical-point claim, re-examine the derivative analysis

---

## Method D: Reverse Derivation

### When to Apply

Apply when the problem involves a chain of forward deductions — proofs, algebraic derivations, integration, or any solution that produces an answer through a sequence of implications.

### How to Apply

1. Start from the final answer
2. Attempt to derive the original problem statement by reversing each step
3. Check whether each reverse step is valid (some forward implications are not reversible, e.g., squaring, multiplying by a sign-unknown expression)
4. If all steps are reversible, the forward derivation is consistent

### Reversibility of Common Operations

| Forward Operation | Reverse Operation | Always Reversible? |
|---|---|---|
| Add $c$ to both sides | Subtract $c$ from both sides | Yes |
| Multiply both sides by $c \neq 0$ | Divide both sides by $c$ | Yes |
| Square both sides | Take square root | **No** — introduces extraneous solutions |
| Multiply by expression $E(x)$ | Divide by $E(x)$ | **No** — if $E(x)$ can be zero |
| Exponentiate both sides (base $a > 0, a \neq 1$) | Take log base $a$ | Yes (within domain) |
| Differentiate | Integrate | **No** — loses constant of integration |
| Integrate | Differentiate | Yes (up to constant) |

### Example

**Problem**: Prove that if $a > 0$ and $b > 0$, then $\frac{a+b}{2} \geq \sqrt{ab}$.

**Forward derivation**: $(\sqrt{a} - \sqrt{b})^2 \geq 0 \implies a + b - 2\sqrt{ab} \geq 0 \implies a + b \geq 2\sqrt{ab} \implies \frac{a+b}{2} \geq \sqrt{ab}$

**Reverse check**: Starting from $\frac{a+b}{2} \geq \sqrt{ab}$, each step is reversible by reversing the inequality and algebraic manipulation, and all conditions ($a > 0, b > 0$) remain satisfied throughout.

### Failure Handling

- If the reverse derivation fails, identify which forward step was not reversible
- Non-reversible steps may have introduced extraneous solutions or lost solutions
- Restart from before the non-reversible step or apply Method A (back-substitution) to filter results

---

## Method E: Numerical Sampling

### When to Apply

Apply to any quantitative problem. Numerical sampling is especially valuable when analytic verification is difficult, messy, or error-prone. It provides a quick sanity check and catches gross errors immediately.

### How to Apply

1. Select 3–5 representative numerical values from the domain
2. Include special values: $0$, $1$, $-1$, fractions, parameter extremes
3. For each value, compute the left-hand side and right-hand side of every equation, or evaluate the function at claimed key points
4. Verify numerical agreement (to within reasonable precision for floating-point calculations)
5. If the problem has parameters, sample multiple parameter values

### Sampling Strategy by Problem Type

- **Equation**: Pick values that are solutions (should satisfy) and non-solutions (should not satisfy)
- **Inequality**: Pick values inside the claimed interval (should satisfy) and outside (should not)
- **Function**: Pick domain endpoints, zeros, critical points, and an interior point
- **Identity**: Pick random values — the identity should hold for all
- **Integration**: Pick a specific value of the upper limit and compare numerical integration result to the claimed antiderivative

### Example

**Problem**: Verify that $\frac{d}{dx}[\sin(x^2)] = 2x\cos(x^2)$

**Numerical sampling** (using approximate values):
- $x = 0$: derivative $= 2(0)\cos(0) = 0$; check numerically $\frac{\sin((0.001)^2) - \sin(0)}{0.001} \approx 0$ ✓
- $x = 1$: derivative $= 2(1)\cos(1) \approx 2 \times 0.5403 = 1.0806$; numerical $\frac{\sin(1.001^2)-\sin(1)}{0.001} \approx 1.0806$ ✓
- $x = \sqrt{\pi/2}$: derivative $= 2\sqrt{\pi/2}\cos(\pi/2) = 0$; numerical derivative $\approx 0$ ✓

### Failure Handling

- Consistent numerical disagreement indicates an error in the analytic derivation
- If numerical values match approximately but not exactly, check for floating-point precision issues — the analytic result may still be correct
- For subtle errors that only appear at extreme parameter values, increase the sampling range

---

## Method F: Dimensional Analysis

### When to Apply

Apply to problems involving physical quantities or composite units. Also useful as a structural check for any formula with terms of potentially different mathematical "dimensions" (e.g., adding a scalar to a vector, mixing degrees and radians).

### How to Apply

1. Assign dimensions to every quantity in the problem (length, time, mass, dimensionless, etc.)
2. Check that all terms added or equated have the same dimension
3. Check that the dimension of the result matches the expected dimension of the answer
4. For transcendental functions ($e^x$, $\sin x$, $\ln x$), the argument must be dimensionless

### Synthetic Example

**Problem**: The period of a pendulum is claimed to be $T = 2\pi \sqrt{\frac{m}{g}}$ where $m$ is mass [M], $g$ is acceleration [L T$^{-2}$].

**Dimensional check**:
- Under the square root: $[m/g] = [M] / [L T^{-2}] = [M L^{-1} T^2]$
- Square root gives: $[M^{1/2} L^{-1/2} T]$
- Period $T$ should have dimension $[T]$

**Result**: Mismatch! The dimension $[M^{1/2}]$ should not appear. The correct formula is $T = 2\pi\sqrt{L/g}$ where $L$ is length [L].

### Failure Handling

- Dimensional mismatch means the formula is structurally wrong — it's not fixable by adjusting constants; the functional form is incorrect
- Re-examine the derivation for terms added with mismatched dimensions or missing conversion factors

---

## Method G: Limits and Special Cases

### When to Apply

Apply when the problem involves functions, sequences, series, calculus, or analysis. The behavior at limits and special parameter values often reveals errors that are invisible at typical values.

### How to Apply

#### Special Case Check

1. Set parameters to extreme or simplified values: $0$, $1$, $\infty$, negative values
2. Does the solution reduce to a known or clearly correct result?
3. If the problem is symmetric, does the solution preserve the symmetry?

#### Limit Check

1. Take the limit as parameters approach boundaries
2. Does the limit behave reasonably? (Finite, tends to expected value, doesn't oscillate unexpectedly)
3. For functions: check behavior as $x \to 0$, $x \to \infty$, and at singularities
4. For sequences: check convergence and limit value

### Example

**Problem**: Find $\lim_{n \to \infty} \left(1 + \frac{x}{n}\right)^n$

**Claimed answer**: $e^x$ (by definition)

**Special case check**:
- $x = 0$: limit $= 1 = e^0$ ✓
- $x = 1$: limit $= e^1 = e$ ✓ (consistent with the definition)
- Large $x$: limit grows exponentially — reasonable ✓

**Check specific values numerically**: For $x=2, n=100$: $(1 + 2/100)^{100} \approx 7.24$; $e^2 \approx 7.39$ — close, with error decreasing as $n$ increases ✓

### Failure Handling

- If special case behavior contradicts mathematical facts, the general solution is wrong
- If the limit yields nonsense (division by zero, oscillatory behavior for a problem that should converge), re-examine the derivation

---

## Method H: Independent Method Cross-Validation

### When to Apply

Apply whenever multiple solution methods exist for the same problem. This is the strongest verification method — two independent derivations producing the same result make an error extremely unlikely.

### How to Apply

1. Identify a fundamentally different approach to the same problem
2. Solve the problem using this independent method
3. Compare the results
4. If they agree, confidence is very high
5. If they disagree, at least one method has a flaw — re-examine both

### Independent Method Pairs

| Problem Type | Method 1 | Method 2 |
|---|---|---|
| Quadratic equation | Quadratic formula | Factoring |
| System of linear equations | Substitution | Elimination / Matrices |
| Definite integral | Antiderivative + FTC | Numerical integration / Substitution change |
| Limit | L'Hôpital's rule | Taylor expansion / Algebraic manipulation |
| Derivative | Limit definition | Differentiation rules |
| Combinatorial identity | Algebraic proof | Combinatorial argument (bijection) |
| Geometric problem | Coordinate geometry | Pure geometry (triangle similarity) |
| Optimization | Derivative (critical points) | Inequality bounding (AM-GM, Cauchy-Schwarz) |
| ODE | Standard method (separation, integrating factor) | Laplace transform / Series solution |

### Example

**Problem**: Compute $\int_0^1 x^2\,dx$

**Method 1 (Antiderivative)**: $\int x^2\,dx = \frac{x^3}{3}$, so $\int_0^1 x^2\,dx = \frac{1^3}{3} - \frac{0^3}{3} = \frac{1}{3}$

**Method 2 (Riemann sum)**: $\lim_{n \to \infty} \frac{1}{n} \sum_{k=1}^n \left(\frac{k}{n}\right)^2 = \lim_{n \to \infty} \frac{1}{n^3}\frac{n(n+1)(2n+1)}{6} = \frac{1}{3}$

Both methods agree: $\frac{1}{3}$ ✓

### Failure Handling

- Disagreement between methods triggers a full re-derivation of both
- Check for errors in each method independently before trying to reconcile
- Once the correct method is identified, analyze what went wrong in the failed method to prevent future recurrence

---

## Method I: Counterexample Search

### When to Apply

Apply for proofs, conjectures, "true or false" problems, and any claim of universal truth. Also useful for verifying that a claimed solution set is complete (no missing solutions).

### How to Apply

1. Assume the conjecture or claim is false
2. Systematically search for a counterexample:
   - Try small values (0, 1, 2, -1) first
   - Try edge cases (boundary values, zero denominators)
   - Try random values in the domain
   - If the statement is parameterized, test extreme parameter values
3. If a counterexample is found, the claim is definitively disproven
4. If no counterexample is found after thorough search, document the search space

### Systematic Search Patterns

- **Number-theoretic**: Test small integers, primes, composite numbers
- **Group-theoretic**: Test small groups (cyclic groups, Klein four-group, $S_3$)
- **Topological**: Test standard counterexample spaces (Sorgenfrey line, $\mathbb{R}$ with standard topology, etc.)
- **Analytic**: Test pathological functions (Weierstrass function, Dirichlet function, $x^2\sin(1/x)$ at 0)

### Example

**Claim**: All prime numbers are odd.

**Counterexample search**: Check small primes: 2, 3, 5, 7, 11, 13...

**Result**: 2 is prime and 2 is even. **Counterexample found.** The claim is false.

### Weakness: Incomplete Search

If no counterexample is found, the claim is **not** proven true — it is merely plausible. The counterexample search can disprove but not prove. Always note: "No counterexample found for [test range]; this is evidence in favor but not a proof."

---

## Method J: Formal Logic Check

### When to Apply

Apply for proofs, abstract mathematics, and any argument with a complex logical structure. This method catches errors in reasoning that survive algebraic verification.

### How to Apply

#### Quantifier Check

1. Identify all quantifiers ($\forall$, $\exists$) in the problem statement and in the proof
2. Verify the order: $\forall \varepsilon \exists \delta$ is NOT equivalent to $\exists \delta \forall \varepsilon$
3. Check that every $\exists$ statement is constructively justified or its existence is proven

#### Implication Check

1. For each "implies" ($\implies$) in the proof, verify that the conclusion logically follows from the premise
2. Check for reversed implications: $P \implies Q$ does not justify using $Q$ to conclude $P$
3. Check for hidden assumptions in implications

#### Proof Structure Check

1. **Direct proof**: Verify the chain of implications leads from hypothesis to conclusion
2. **Proof by contradiction**: Verify the negation of the conclusion plus the hypotheses leads to a genuine contradiction
3. **Proof by induction**: Verify base case(s) and that the inductive step works for all $n \geq$ base case
4. **Proof by contrapositive**: Verify that $\neg Q \implies \neg P$ is correctly derived (not $\neg P \implies \neg Q$)

#### Circular Reasoning Check

Verify that the proof does not assume what it's trying to prove (even in disguised form).

### Example

**Flawed proof**: "The function $f(x)$ is continuous because $\lim_{x \to a} f(x) = f(a)$ for all $a$ and this limit exists because the function is continuous."

**Logic check**: Circular reasoning — the continuity claim is used to justify the limit existence, which is then used to justify continuity.

### Failure Handling

- Logical errors are fundamental — they cannot be fixed by tweaking numbers; the proof structure must be rebuilt
- Quantifier order errors: restate with correct order and re-derive
- Circular reasoning: identify the point of circularity and build a new proof that doesn't use the target conclusion

---

## Method K: Computational Consistency Check

### When to Apply

Apply to problems involving computation-heavy operations: matrix manipulations, numerical integration, statistical calculations, and any multi-step computation where intermediate errors can propagate.

### How to Apply

1. Verify using known identities or invariants that must hold regardless of the specific computation:
   - **Linear Algebra**: Trace = sum of eigenvalues; determinant = product of eigenvalues; $AA^{-1} = I$; $Q^TQ = I$ for orthogonal matrices
   - **Statistics**: Sum of probabilities = 1; variance $\geq 0$; correlation in $[-1, 1]$
   - **Calculus**: Fundamental Theorem consistency; derivative of integral = integrand
2. Recalculate key intermediate results independently (different grouping, different order of operations)
3. Check symmetry: if the problem has symmetry, the solution must preserve it

### Consistency Checks by Domain

| Domain | Consistency Check |
|---|---|
| Matrix $A = PDP^{-1}$ | Recompute $PDP^{-1}$ and compare to $A$ |
| Eigenvalues of $A$ | $\sum \lambda_i = \operatorname{tr}(A)$, $\prod \lambda_i = \det(A)$ |
| Integration by parts | Verify derivative of result gives integrand |
| Statistical distribution | Total probability = 1; expected values within range |
| Numerical method | Check with smaller step size that result converges |
| Fourier series | Parseval's identity: $\frac{1}{2\pi}\int |f|^2 = \sum |c_n|^2$ |
| ODE solution | Verify Wronskian consistency for independent solutions |

### Example

**Problem**: Diagonalize $A = \begin{pmatrix} 2 & 1 \\ 1 & 2 \end{pmatrix}$

**Claimed result**: $A = PDP^{-1}$ with $P = \begin{pmatrix} 1 & 1 \\ 1 & -1 \end{pmatrix}$, $D = \begin{pmatrix} 3 & 0 \\ 0 & 1 \end{pmatrix}$

**Consistency checks**:
1. Trace: $\operatorname{tr}(A) = 4$, $\operatorname{tr}(D) = 4$ ✓ (sum of eigenvalues)
2. Determinant: $\det(A) = 3$, $\det(D) = 3$ ✓ (product of eigenvalues)
3. Eigenvector check: $A\begin{pmatrix}1\\1\end{pmatrix} = \begin{pmatrix}3\\3\end{pmatrix} = 3\begin{pmatrix}1\\1\end{pmatrix}$ ✓; $A\begin{pmatrix}1\\-1\end{pmatrix} = \begin{pmatrix}1\\-1\end{pmatrix}$ ✓
4. Reconstruction: $PDP^{-1} = \frac{1}{2}\begin{pmatrix}1&1\\1&-1\end{pmatrix}\begin{pmatrix}3&0\\0&1\end{pmatrix}\begin{pmatrix}1&1\\1&-1\end{pmatrix} = \begin{pmatrix}2&1\\1&2\end{pmatrix} = A$ ✓

All consistency checks pass.

### Failure Handling

- A consistency check failure is specific: the trace mismatch indicates eigenvalue sum error; determinant mismatch indicates product error; reconstruction failure indicates eigenvector or inverse error
- Trace the failure back to the specific computation step and fix

---

## Multi-Method Verification Strategy

### For Routine Problems

Apply two methods: the primary method for the problem type (from the table at the top of this document) plus Method B (Domain Check, which applies universally).

### For Moderate Difficulty

Apply three methods: primary + secondary + Method E (Numerical Sampling, nearly universally applicable).

### For Hard/Contest Problems

Apply four or more methods: primary + secondary + Method H (Independent Method) + Method G (Limits/Special Cases).

### For Research/Proof Problems

Apply all applicable methods from {D, G, H, I, J} plus numerical sampling where meaningful and domain checking.

---

## Verification Failure Protocol

When any verification method signals an error:

1. **Record the failure**: Which method? At what step? What was the specific discrepancy?
2. **Backtrack**: Return to the last intermediate result that all verification methods agreed was correct
3. **Diagnose**: Identify the nature of the error (algebraic, logical, domain, sign, missing case)
4. **Fix**: Correct the error and propagate the change forward
5. **Re-verify**: Apply the same verification methods again, plus at least one additional method
6. **If error persists** after two correction cycles: Switch to an independent solution method (Method H)
7. **If still failing**: State uncertainty explicitly; do not output an unverified answer

### Diagnostic Heuristics

| Failure Pattern | Likely Cause |
|---|---|
| Back-substitution fails but domain check passes | Algebraic manipulation error, sign error, lost solution |
| Domain check fails, back-substitution passes | Extraneous solution from non-reversible step |
| Numerical sampling fails consistently | Systematic error in derivation or formula |
| Numerical sampling fails at some values only | Domain restriction overlooked, piecewise error |
| Independent methods disagree | One method has a conceptual flaw; re-examine both |
| Limit/special case fails | Missing term in expansion, incorrect asymptotic behavior |
| Consistency check (trace/determinant) fails | Computational error in eigenvalue/vector or matrix operations |
| Formal logic check reveals quantifier error | Misunderstanding of definition; re-read definition carefully |
| Counterexample found easily | The claim was too strong or a condition was overlooked |

---

## Verification Documentation

Every solution output must include a verification section stating:
- Which methods were applied
- The outcome of each method (passed/failed)
- If a method was skipped, the reason must be stated
- For numerical sampling, state which values were tested

**Example documentation**:
```
## Verification
- **Method A (Back-substitution)**: ✓ $2^2 - 5(2) + 6 = 0$ and $3^2 - 5(3) + 6 = 0$
- **Method B (Domain check)**: ✓ Both solutions are real; no domain restrictions violated
- **Method E (Numerical sampling)**: ✓ $f(2) = 0$, $f(3) = 0$, $f(2.5) = -0.25 \neq 0$

All verification methods passed. Confidence: HIGH.
```
