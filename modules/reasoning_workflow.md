# Mathematical Reasoning Workflow

This module defines a rigorous, 7-step reasoning workflow for solving mathematical problems. Each step must be executed thoroughly — skipping or rushing any step increases the probability of error.

---

## Step 1: Problem Parsing

Extract the complete mathematical structure from the problem statement before any computation.

### 1.1 Explicit Information Extraction

| Category | What to Extract |
|---|---|
| **Known conditions** | Every given equation, inequality, relation, property |
| **Goal** | What exactly needs to be found, proved, or computed |
| **Variables** | All independent and dependent variables with symbols |
| **Parameters** | All symbolic parameters with their types (real, integer, complex, etc.) |
| **Constants** | Numerical constants and their significance |
| **Ranges/Domains** | Explicit domain restrictions on any variable |
| **Units** | Physical or abstract units associated with quantities |

### 1.2 Implicit Condition Extraction

- **Divisor** $\neq 0$: all denominators, matrix inverses, divisions
- **Radicand** $\geq 0$: all even-index radicals
- **Logarithm argument** $> 0$: all $\log_a(x)$ with $x > 0$, $a > 0$, $a \neq 1$
- **Trigonometric** ranges: $|\sin x| \leq 1$, $|\cos x| \leq 1$
- **Inequality operations**: sign reversal when multiplying/dividing by negatives
- **Probability**: $P(E) \in [0, 1]$
- **Set membership**: element belongs to specified universal set
- **Dimension compatibility**: matrix multiplication, inner product spaces
- **Continuity/differentiability**: implied by certain operations

### 1.3 Sufficiency Assessment

| Scenario | Indicator |
|---|---|
| **Sufficient conditions** | Number of independent conditions $\geq$ number of unknowns |
| **Overdetermined (may be inconsistent)** | More conditions than unknowns; verify consistency |
| **Underdetermined (infinite or parametrized solutions)** | Fewer conditions than unknowns; express answer with free parameters |
| **Ambiguous** | Missing quantifiers, unclear domain, vague terminology |

### 1.4 Solution Structure Prediction

- **Unique solution expected**: Well-posed problem with sufficient independent constraints
- **Multiple solutions possible**: Absolute values, squares, trigonometric equations, parameterized
- **No solution possible**: Contradictory conditions, impossible constraints
- **Case analysis required**: Parameter dependence, piecewise definitions, parity/non-negativity branching
- **Error/ambiguity in problem**: Inconsistent units, missing domain, undefined operations

### 1.5 Example

> Problem: "Solve for $x$: $\sqrt{x+3} = x - 3$"

**Parsing:**
- Explicit: equation $\sqrt{x+3} = x - 3$, unknown $x$
- Implicit domain: $x+3 \geq 0 \implies x \geq -3$ (radicand), also $x-3 \geq 0$ (square root output $\geq 0$) $\implies x \geq 3$
- Combined domain: $x \geq 3$
- Structure: squaring will produce quadratic, possible extraneous roots

---

## Step 2: Mathematical Object Modeling

Build a formal mathematical representation of the problem.

### 2.1 Model Selection Guide

| Problem Type | Appropriate Models |
|---|---|
| **Equations/inequalities** | Algebraic equations, systems, inequality sets |
| **Functions** | Explicit form $f(x)$, function composition, piecewise definition |
| **Sets** | Set-builder notation, Venn diagrams for combinatorics |
| **Linear systems** | Matrix equation $A\mathbf{x} = \mathbf{b}$ |
| **Vector geometry** | Vector spaces, bases, coordinates, dot/cross products |
| **Probability** | Sample space $\Omega$, event algebra, probability measure $P$ |
| **Graph problems** | Nodes, edges, adjacency matrices, adjacency lists |
| **Algebraic structures** | Groups $(G, \cdot)$, rings $(R, +, \cdot)$, fields, vector spaces |
| **Metric/analysis** | Metric spaces, norms, limits, continuity definitions |
| **ODE/PDE** | Differential equations with initial/boundary conditions |
| **Optimization** | Objective function $f(x)$, constraints $g_i(x) \leq 0$, feasible region |
| **Recurrence** | Recurrence relation $a_{n+k} = F(a_n, \ldots, a_{n+k-1})$ |
| **Limits/asymptotics** | Limit expressions, asymptotic equivalence, series |

### 2.2 Modeling Checklist

- [ ] All conditions translated into mathematical statements
- [ ] Unknown variables clearly identified
- [ ] Parameters treated as fixed but symbolic
- [ ] Domains explicitly included in the model
- [ ] Objective (maximize/minimize/solve/prove) precisely stated
- [ ] Appropriate level of abstraction chosen
- [ ] Units/dimensions consistent

### 2.3 Example

> "A rectangle has perimeter 24. Find dimensions maximizing area."

**Modeling:**
- Variables: length $l$, width $w$ (both $> 0$)
- Constraint: $2l + 2w = 24 \implies l + w = 12$
- Objective: maximize $A = lw$
- Domain: $l > 0, w > 0$
- Optimization model: maximize $A(l) = l(12-l)$ on $l \in (0, 12)$

---

## Step 3: Method Selection

Choose the most appropriate solution method(s) based on the model.

### 3.1 Method Catalog

| Category | Methods |
|---|---|
| **Direct computation** | Arithmetic, numeric evaluation, substitution into formulas |
| **Algebraic manipulation** | Expansion, factoring, completing the square, discriminant analysis |
| **Equation solving** | Substitution, elimination, isolation, quadratic formula |
| **Inequality techniques** | Bounding, monotonicity analysis, sign analysis |
| **Calculus** | Derivatives for extrema, integrals for accumulation, limits, L'Hôpital, Taylor expansion, equivalent infinitesimals |
| **Linear algebra** | Gaussian elimination, matrix operations, eigenvalue/eigenvector decomposition, orthogonalization |
| **Discrete math** | Recurrence solving, generating functions, mathematical induction |
| **Proof techniques** | Direct proof, contradiction, contrapositive, construction, counterexample |
| **Analysis** | Compactness, completeness, continuity arguments, fixed point theorems |
| **Abstract algebra** | Homomorphisms, quotient structures, isomorphism theorems |
| **Complex analysis** | Contour integration, residue theorem |
| **Integral transforms** | Fourier transform, Laplace transform |
| **Numerical** | Approximation methods, error estimation |
| **CAS-assisted** | Computer algebra verification (symbolic computation) |
| **Geometric intuition** | Diagrams as heuristic, not proof |

### 3.2 Selection Criteria

1. **Directness**: Choose the method that maps most directly to the model
2. **Tractability**: Ensure the chosen method can actually reach a closed-form or exact answer
3. **Rigor**: Prefer exact/analytic methods over numerical when the problem calls for exactness
4. **Efficiency**: Among equally rigorous options, prefer the computationally simpler
5. **Verifiability**: Methods that produce checkable intermediate steps are preferable
6. **Fallback**: Have a secondary method in mind if the primary fails

### 3.3 Example

> "Find $\lim_{x \to 0} \frac{\sin x - x}{x^3}$"

**Method selection:**
- Option A: Taylor expansion $\sin x = x - \frac{x^3}{6} + O(x^5)$ → limit $= -\frac{1}{6}$ (preferred: direct, rigorous)
- Option B: L'Hôpital's rule applied 3 times (works but more computation)
- Option C: Equivalent infinitesimals (not applicable directly due to cancellation)

---

## Step 4: Step-by-Step Solution

Execute the chosen method with full mathematical justification at every step.

### 4.1 Mandatory Justifications

| Operation | Required Justification |
|---|---|
| **Division** | Divisor is non-zero |
| **Squaring both sides** | Both sides have the same sign (or note that extraneous roots may be introduced) |
| **Taking square root** | Specify $\pm$ branch, domain of radicand |
| **Taking logarithm** | Argument $> 0$, base $> 0$ and $\neq 1$ |
| **Reciprocals** | Both sides non-zero |
| **Inequality multiplication** | Sign of multiplier explicitly stated |
| **Differentiation** | Function is differentiable at that point |
| **Integration by substitution** | Transformation is bijective (or interval handling noted) |
| **Interchanging limit/integral/sum** | Applicable convergence theorem stated (DCT, MCT, uniform convergence) |
| **Applying theorem** | All hypotheses of the theorem verified |

### 4.2 Common Pitfalls to Avoid

1. **Treating approximations as exact**: Never use $\approx$ in a derivation that requires $=$
2. **Skipping key transformations**: Each algebraic manipulation must be spelled out
3. **Dividing by potentially zero expressions**: Always check zero case separately
4. **Missing domain changes**: Transformation may shrink/expand domain
5. **Uncritical squaring**: Always check for extraneous roots afterward
6. **Assuming monotonicity without proof**: Derivative sign must be verified on the entire interval
7. **Forgetting $\pm$**: $\sqrt{x^2} = |x|$, not $x$; solving $a^2 = b^2$ gives $a = \pm b$
8. **Lost solutions**: Dividing by an expression that could be zero

### 4.3 Case Analysis Protocol

When the solution depends on a parameter:

1. Identify the parameter and its domain
2. Find critical parameter values where behavior changes
3. For each sub-interval, state which method applies and why
4. Solve separately for each case
5. Verify that solutions for each case satisfy that case's assumptions

### 4.4 Step Format

Each step should follow the format:
```
**[Reason]**: Why this step is valid
**[Operation]**: The mathematical operation
**[Result]**: The result of the operation
```

---

## Step 5: Verification

Apply the verification protocol from `verification_engine.md`. At minimum:

### 5.1 Mandatory Checks (for every problem)

1. **Back-substitution (Method A)**: Substitute the answer into the original equation/condition
2. **Domain check (Method B)**: Verify all domain constraints are satisfied
3. **Boundary check (Method C)**: Verify behavior at domain boundaries and critical points

### 5.2 Context-Dependent Checks

| Problem Type | Verification Methods |
|---|---|
| **Proofs** | Logic check (Method J), reverse derivation (Method D), counterexample search (Method I) |
| **Calculations** | Computational consistency (Method K), independent cross-validation (Method H) |
| **Optimization** | Boundary + interior critical point check |
| **Identities** | Numerical sampling (Method E), special case check (Method G) |
| **Applied problems** | Dimensional analysis (Method F) |

### 5.3 Verification Protocol

1. Perform the mandatory checks
2. If any check fails, go to Step 6 (Error Location)
3. Perform context-dependent checks
4. If any optional check fails, go to Step 6
5. If all checks pass, proceed to Step 7 (Final Answer)

---

## Step 6: Error Location and Correction

When verification fails, systematically locate and fix the error.

### 6.1 Error Isolation Protocol

1. **Identify which verification method failed** and exactly where
2. **Re-examine the failed verification**: Was the verification itself correct?
3. **Binary search through steps**: Check intermediate results starting from the middle
4. **Locate the first incorrect step**: The error is at or before the first verifiably wrong result
5. **Classify the error**:
   - Algebraic/arithmetic mistake (most common)
   - Domain violation (overlooked constraint)
   - Method applicability error (theorem hypothesis not met)
   - Sign error
   - Missing case (parameter branch, zero divisor, etc.)
   - Conceptual error (fundamental misunderstanding)

### 6.2 Correction Protocol

1. **Backtrack**: Discard all conclusions after the first error
2. **Fix**: Correct the identified error
3. **Recalculate**: Redo all steps from the correction point
4. **Re-verify**: Apply ALL verification methods again
5. **Loop**: If re-verification fails, repeat from step 6.1

### 6.3 Unfixable Situations

If after 3 correction attempts the solution still fails verification:

- State clearly: "The attempted methods have not produced a verifiable solution"
- Report the verified intermediate results (the steps that DID verify)
- Identify the specific point where reasoning breaks down
- If the problem appears to be open or ill-posed, state that honestly
- **Never output an answer known to be incorrect**

---

## Step 7: Final Answer

Present the answer in a clear, complete, and rigorous format.

### 7.1 Answer Format Elements

| Element | When Required | Example |
|---|---|---|
| **Conclusion** | Always | "$x = 3$ is the unique solution" |
| **Condition ranges** | When answer depends on parameters | "$x = -a$ for $a < 0$; no solution for $a \geq 0$" |
| **Exact form** | When exact form exists | "$x = \sqrt{2}$", not "$x \approx 1.414$" |
| **Approximation** | Supplement when helpful | "$x = \sqrt[3]{2} \approx 1.260$" |
| **Verification summary** | Always | "Verified by back-substitution, domain check, and boundary analysis" |
| **Complete solution set** | When multiple solutions | "$x \in \{2, 3, -1\}$" |
| **No solution** | When none exists | Statement + reason: "No solution because ... contradicts ..." |
| **Counterexample** | When statement is false | Explicit counterexample with verification |
| **Missing conditions** | When insufficient | "Need additional condition ... to determine uniquely" |
| **Open problem remark** | Only if truly open | "This reduces to the Riemann hypothesis, which is unsolved" |

### 7.2 Presentation Guidelines

1. **Bold** the final answer for visual clarity
2. Box or clearly demarcate the conclusion
3. Use exact mathematical notation, not informal language
4. Include the verification summary in one sentence
5. State parameter ranges in interval notation when possible
6. If multiple solutions, present them sorted (e.g., ascending)

### 7.3 Example

> **Final Answer**: $\mathbf{x = 6}$ is the unique solution.
>
> **Solution set**: $\{6\}$
> **Domain**: $x \geq 3$ was the natural domain; $x = 6$ satisfies this.
> **Verification**: Back-substitution $\sqrt{6+3} = \sqrt{9} = 3 = 6-3$ confirms the result. The extraneous root $x = 1$ (from squaring) was rejected as it falls outside the domain $x \geq 3$.
>
> **Alternative notation**: $x = 6,\ x \in \mathbb{R}$

---

## Quick Reference: Workflow Summary

```
Step 1: PARSE ──→ Step 2: MODEL ──→ Step 3: SELECT METHOD
                                              │
                                              ▼
                    Step 6: FIX ERROR ←── Step 4: SOLVE
                         │                      │
                         │                      ▼
                         └───── (fail) ──── Step 5: VERIFY
                                                 │
                                                 ▼ (pass)
                                          Step 7: ANSWER
```

Revise as: `PARSE → MODEL → SELECT → SOLVE → VERIFY → [FIX if needed] → ANSWER`
