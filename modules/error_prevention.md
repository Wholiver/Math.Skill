# Error Prevention Guide

This module defines concrete error prevention rules, common pitfalls, and prevention strategies across 8 mathematical domains. These rules are derived from statistical analysis of real mathematical errors and should be applied during Step 4 (Step-by-Step Solution) of the reasoning workflow.

---

## 1. Algebraic Error Prevention

### Rules

1. **Post-factoring expansion check**: After factoring an expression, re-expand to verify it matches the original.
2. **Division-by-zero guard**: Before dividing by any expression, verify it is non-zero. If uncertain, treat zero case separately.
3. **Squaring root check**: After squaring both sides of an equation, check ALL candidate solutions against the original equation. Squaring is not an equivalent transformation.
4. **$\pm$ sign discipline**: $\sqrt{x^2} = |x|$, not $x$. Solving $a^2 = b$ yields $a = \pm\sqrt{b}$. When extracting a square root, always consider both signs.
5. **Rational equation denominator check**: Before solving rational equations, note excluded values (where any denominator $= 0$). Reject any solution equal to an excluded value.
6. **Domain check for transcendental equations**: For $\log_a f(x) = g(x)$, require $f(x) > 0$, $a > 0$, $a \neq 1$. For $a^{f(x)} = b$, domain depends on the base.
7. **Absolute value case split**: $|f(x)| = g(x)$ splits into $f(x) = g(x)$ for $f(x) \geq 0$ and $-f(x) = g(x)$ for $f(x) < 0$. Check both branches.
8. **Exponent rules verification**: $(a^m)^n = a^{mn}$ requires $a > 0$ when $m, n$ are not integers. $\sqrt{a}\sqrt{b} = \sqrt{ab}$ requires $a, b \geq 0$ in reals.

### Common Pitfalls with Examples

| Pitfall | Wrong | Correct |
|---|---|---|
| Canceling $(x-a)$ without checking $x \neq a$ | $\frac{(x-1)(x+2)}{x-1} = x+2$ for all $x$ | $\frac{(x-1)(x+2)}{x-1} = x+2$ for $x \neq 1$ |
| Forgetting $\pm$ when taking square root | $x^2 = 4 \implies x = 2$ | $x^2 = 4 \implies x = \pm 2$ |
| Applying $(a+b)^2 = a^2+b^2$ | $(x+1)^2 = x^2 + 1$ | $(x+1)^2 = x^2 + 2x + 1$ |
| $\sqrt{a+b} = \sqrt{a} + \sqrt{b}$ | $\sqrt{x^2 + 4} = x + 2$ | $\sqrt{x^2 + 4}$ cannot be simplified this way |
| Incorrect sign when moving terms | $x + 3 = 5 \to x = 5 + 3 = 8$ | $x + 3 = 5 \to x = 5 - 3 = 2$ |

### Prevention Strategy

1. **Write out every algebraic step** — no mental shortcuts
2. **Use parentheses liberally** to avoid sign and precedence errors
3. **After every 3–4 steps, do a quick sanity check** with a simple value
4. **When factoring, multiply back to verify**
5. **For rational equations: list excluded values BEFORE solving**

---

## 2. Inequality Error Prevention

### Rules

1. **Sign reversal when multiplying by negative**: Multiplying/dividing by a negative number reverses the inequality sign. This is the single most common inequality error.
2. **Case analysis for variable expressions**: When multiplying/dividing by an expression containing variables (e.g., $x-2$), split into cases based on the sign of the expression.
3. **Condition check for squaring**: $a < b \nRightarrow a^2 < b^2$ unless $a, b \geq 0$. For squaring inequalities, verify that both sides are non-negative.
4. **Direction of bounding**: When applying inequalities like AM-GM or Cauchy-Schwarz, note the direction carefully. $x + \frac{1}{x} \geq 2$ for $x > 0$, but $\leq -2$ for $x < 0$.
5. **Equality condition check**: When using inequalities (AM-GM, Cauchy, Hölder), always state the equality condition and verify it is attainable.
6. **Boundary point inclusion**: For solution intervals, explicitly state whether endpoints are included ($\leq, \geq$) or excluded ($<, >$).
7. **Reciprocal reversal**: For $a, b > 0$: $a < b \iff \frac{1}{a} > \frac{1}{b}$. For $a, b < 0$: $a < b \iff \frac{1}{a} > \frac{1}{b}$. Mixed signs: no simple rule — handle by case analysis.
8. **Logarithmic inequality monotonicity**: $\log_a x > \log_a y$ implies $x > y$ when $a > 1$, but $x < y$ when $0 < a < 1$.

### Common Pitfalls with Examples

| Pitfall | Wrong | Correct |
|---|---|---|
| Multiply by $x$ without sign check | $x < \frac{1}{x} \implies x^2 < 1$ | Case 1: $x > 0 \implies x^2 < 1$; Case 2: $x < 0 \implies x^2 > 1$ |
| Square both sides without non-negativity | $x < -3 \implies x^2 < 9$ | Squaring is not valid here (signs differ) |
| Reciprocal without case analysis | $x < 3 \implies \frac{1}{x} > \frac{1}{3}$ | Only valid if $x > 0$; need cases for $x < 0$ and $x = 0$ excluded |

### Prevention Strategy

1. **Before any inequality manipulation, ask: "Does this reverse the sign?"**
2. **When multiplying by a variable, split into cases: positive, negative, zero**
3. **Sketch a number line** to visualize inequality solutions
4. **Test one point inside each proposed interval** as a quick check
5. **Check endpoints separately** for closed vs open intervals

---

## 3. Function Error Prevention

### Rules

1. **Domain first**: Always determine the domain of a function before analyzing its properties. Domain errors cascade into range, monotonicity, and extremum errors.
2. **Monotonicity needs complete analysis**: $f'(x) > 0$ on an interval is sufficient for strict increase, but $f'(x) \geq 0$ does NOT guarantee strict increase (counterexample: $f(x) = \text{constant}$). Also check non-differentiable points separately.
3. **Critical points $\neq$ extremum points**: A point where $f'(x) = 0$ is only a CANDIDATE for extremum. Must check:
   - First derivative test (sign change)
   - Second derivative test ($f''(x) \neq 0$)
   - Boundary values of the domain
   - Non-differentiable points
4. **Range depends on domain**: $f(x) = x^2$ on $\mathbb{R}$ has range $[0, \infty)$; on $[-1, 2]$ has range $[0, 4]$. Same formula, different domain, different range.
5. **Composite function range check**: For $f(g(x))$, the range of $g$ must be within the domain of $f$. If not, the composition is only defined on a restricted domain.
6. **Inverse function monotonicity**: A function has an inverse on an interval only if it is strictly monotone (one-to-one) there. Non-monotone functions require domain restriction.
7. **Visual intuition $\neq$ proof**: A sketch is a heuristic, not a rigorous justification. Statements about continuity, differentiability, or limits cannot be proven by looking at a graph.
8. **Asymptote classification**: Horizontal asymptote requires $\lim_{x\to\infty} f(x) = L$ (finite). Vertical asymptote requires diverging limit at finite $x$. Slant asymptote requires $\lim_{x\to\infty} f(x)/x = m$ (finite non-zero).

### Common Pitfalls with Examples

| Pitfall | Wrong | Correct |
|---|---|---|
| Assuming $f'(x) = 0 \implies$ extremum | $f(x) = x^3$, $f'(0) = 0$, "so 0 is extremum" | $f'(0) = 0$ but $f'(x) > 0$ for $x \neq 0$, so 0 is an inflection point |
| Forgetting boundary for range | $f(x) = e^x$ on $[-1, 0]$ has range $(0, 1)$ | Range is $[e^{-1}, 1]$ (closed on both ends) |
| Forgetting non-differentiable points | $f(x) = |x|$ has no critical points from derivative | The non-differentiable point $x=0$ IS the extremum |

### Prevention Strategy

1. **Always write the domain explicitly** before any analysis
2. **For extremum problems: list ALL candidates** — critical points, boundaries, non-differentiable points
3. **Evaluate function at ALL candidate points** before concluding
4. **Draw a sign chart for the derivative** rather than relying on algebraic sign conclusions
5. **For composite functions: draw a domain-range diagram**

---

## 4. Geometry Error Prevention

### Rules

1. **Do not rely on visual appearance**: A diagram can show a right angle that is actually $89.9^\circ$. Every geometric conclusion must be justified by a theorem or computation.
2. **State theorem conditions explicitly**: When applying a theorem (Pythagorean, similar triangles, circle theorems), explicitly verify all conditions before use. Example: "Triangle ABC is right-angled at C (given), therefore by the Pythagorean theorem, $AB^2 = AC^2 + BC^2$."
3. **Explain the purpose of auxiliary lines**: Each auxiliary construction must have a clear justification. Example: "Draw line through D parallel to AB to create similar triangles."
4. **Justify area/angle/length conclusions**: Chain of reasoning must be explicit. "Since $\triangle ABC \sim \triangle DEF$ (AA criterion), $\frac{AB}{DE} = \frac{BC}{EF}$."
5. **Coordinate setup: ensure no loss of generality**: When placing figures in coordinates, verify that the placement doesn't impose unintended constraints. "Place A at $(0,0)$, B at $(c,0)$ — this is without loss of generality by translation and rotation."
6. **Vector method: verify independence**: When using vector methods, ensure chosen basis vectors are linearly independent.
7. **Trigonometric method: check ambiguous case**: The Law of Sines can produce two possible triangles (SSA ambiguous case). Always check both possibilities.
8. **3D geometry: projection and cross-section**: Verify that properties of 3D figures are preserved in 2D projections. Cross-sections must be clearly defined.

### Common Pitfalls with Examples

| Pitfall | Correct Procedure |
|---|---|
| Assuming a quadrilateral is cyclic without proof | Verify that opposite angles sum to $180^\circ$ or one of the equivalent conditions |
| Using similar triangles without stating the similarity criterion | State which criterion (AA, SAS, SSS) and which corresponding pairs prove similarity |
| Blindly applying the Pythagorean theorem | First verify the triangle is right-angled |

### Prevention Strategy

1. **Label all points, angles, and lengths explicitly** in a diagram or table
2. **Write the theorem name and conditions** before applying it
3. **Check for degenerate cases** (collinear points, coincident points, zero-length segments)
4. **When using coordinates, verify the placement preserves generality** by checking degrees of freedom

---

## 5. Probability and Statistics Error Prevention

### Rules

1. **Define the sample space explicitly**: $\Omega = \{\text{list all outcomes}\}$ or $\Omega = \{\text{stated set}\}$. All probability calculations depend on correctly identifying $\Omega$.
2. **Distinguish with/without replacement**: "Draw 2 cards from a deck" — with replacement means $52 \times 52$ possible outcomes; without replacement means $52 \times 51$. State which one explicitly.
3. **Distinguish permutation vs combination**: $P(n,k) = \frac{n!}{(n-k)!}$ (order matters); $C(n,k) = \binom{n}{k}$ (order does not matter). Pick the right one based on the problem context.
4. **Distinguish independent vs mutually exclusive**: Independent: $P(A \cap B) = P(A)P(B)$. Mutually exclusive: $A \cap B = \emptyset$, $P(A \cap B) = 0$. These are NOT the same — in fact, mutually exclusive events with positive probability CANNOT be independent.
5. **Distinguish conditional vs joint probability**: $P(A|B) = \frac{P(A \cap B)}{P(B)}$ requires $P(B) > 0$. Do not confuse with $P(A \cap B)$.
6. **Range check**: Every probability must satisfy $0 \leq P(E) \leq 1$. If a calculation yields $P > 1$ or $P < 0$, there is an error.
7. **Total probability check**: For a partition of $\Omega$, $\sum_i P(A_i) = 1$. If your probabilities don't sum to 1, there is an error.
8. **Variance non-negativity**: $\text{Var}(X) \geq 0$ always. Negative variance is impossible.
9. **Expectation dimension check**: $E[X]$ has the same units/dimension as $X$. $E[X^2]$ has squared units. The variance formula $\text{Var}(X) = E[X^2] - (E[X])^2$ must be dimensionally consistent.
10. **Law of total probability / Bayes' theorem**: Explicitly write the partition of $\Omega$ used. For Bayes: state the prior, likelihood, and evidence explicitly.

### Common Pitfalls with Examples

| Pitfall | Wrong | Correct |
|---|---|---|
| Adding probabilities of non-mutually-exclusive events | $P(A \cup B) = P(A) + P(B)$ | $P(A \cup B) = P(A) + P(B) - P(A \cap B)$ |
| Confusing $P(A|B)$ with $P(B|A)$ | "Probability disease given positive test" vs "Probability positive test given disease" | Use Bayes' theorem to convert |
| Overlooking "at least one" complement | Direct counting for "at least one head in 10 flips" | $1 - P(\text{all tails}) = 1 - \left(\frac{1}{2}\right)^{10}$ |
| Independence assumption without justification | Assuming $A$ and $B$ are independent because it simplifies the problem | Check $P(A \cap B) = P(A)P(B)$ or justify by problem context |

### Prevention Strategy

1. **Write out $\Omega$ explicitly** at the start
2. **Label each event clearly** ($A$, $B$, etc.) with descriptions
3. **Draw a tree diagram or Venn diagram** for conditional probability problems
4. **After computing any probability, check it's in $[0, 1]$**
5. **Sum all probabilities of a partition — should be exactly 1**
6. **For combinatorics: verify the counting method** with a small case that can be enumerated

---

## 6. Calculus Error Prevention

### Rules

1. **Check left and right limits for $\lim_{x \to a}$**: The limit exists only if left and right limits exist and are equal. This is especially important for piecewise functions and absolute values.
2. **Verify L'Hôpital's rule conditions before applying**:
   - Limit is of indeterminate form $\frac{0}{0}$ or $\frac{\infty}{\infty}$
   - $f$ and $g$ are differentiable near $a$ (except possibly at $a$)
   - $g'(x) \neq 0$ near $a$ (except possibly at $a$)
   - $\lim_{x \to a} \frac{f'(x)}{g'(x)}$ exists (or is $\pm\infty$)
3. **State remainder/error order for Taylor expansions**: For approximations, state the order: $f(x) = T_n(x) + O(x^{n+1})$ or $f(x) = T_n(x) + R_n(x)$ where $|R_n(x)| \leq \frac{M}{(n+1)!}|x-a|^{n+1}$.
4. **Check domain before differentiating**: A function must be defined (and ideally differentiable) at a point to differentiate there. $\frac{d}{dx}\ln x$ is only valid for $x > 0$.
5. **Check boundary points for piecewise functions**: At junction points of piecewise functions, check continuity BEFORE checking differentiability. Differentiability implies continuity.
6. **Interval transformation for integration by substitution**: For $\int_a^b f(g(x))g'(x)dx$ with $u = g(x)$, transform limits: $\int_{g(a)}^{g(b)} f(u)du$. Verify $g$ is continuously differentiable on $[a, b]$.
7. **Add $+C$ for indefinite integrals**: Every indefinite integral must include the constant of integration. Omitting it is an incomplete answer.
8. **Check convergence for improper integrals**: $\int_a^\infty f(x)dx$ converges only if the limit of $\int_a^b f(x)dx$ exists as $b \to \infty$. Test via comparison, limit comparison, or direct evaluation.
9. **State conditions for interchanging operations**:
   - $\frac{d}{dx}\int f(x,t)dt = \int \frac{\partial}{\partial x}f(x,t)dt$ requires conditions (dominated convergence or uniform convergence)
   - $\int \sum f_n = \sum \int f_n$ requires uniform convergence or monotone/dominated convergence
   - $\lim_{n\to\infty} \int f_n = \int \lim_{n\to\infty} f_n$ requires dominated convergence or uniform convergence
10. **Check series convergence before manipulating**: Operations like reordering terms of conditionally convergent series can change the sum (Riemann rearrangement theorem).

### Common Pitfalls with Examples

| Pitfall | Wrong | Correct |
|---|---|---|
| Applying L'Hôpital without checking form | $\lim_{x \to 0} \frac{\sin x}{x+1}$ — not $\frac{0}{0}$ or $\frac{\infty}{\infty}$ | Cannot apply L'Hôpital; $\lim = \frac{0}{1} = 0$ directly |
| Forgetting $+C$ | $\int x^2 dx = \frac{x^3}{3}$ | $\int x^2 dx = \frac{x^3}{3} + C$ |
| Ignoring absolute value in $\int \frac{1}{x}dx$ | $\int \frac{dx}{x} = \ln x + C$ | $\int \frac{dx}{x} = \ln|x| + C$ |
| Not checking convergence of improper integral | $\int_{-\infty}^\infty x\,dx = 0$ (by symmetry) | Integral diverges; symmetric cancellation is invalid for improper integrals |

### Prevention Strategy

1. **Before L'Hôpital: write "$0/0$ form" or "$\infty/\infty$ form"** to confirm applicability
2. **After every indefinite integral: check that there is a $+C$**
3. **For integration: differentiate your answer** and verify it recovers the integrand
4. **For limits: check left and right limits separately** when there's any discontinuity risk
5. **For series: state the convergence test** used and verify its conditions
6. **For interchanging operations: name the theorem** (e.g., "by the Dominated Convergence Theorem")

---

## 7. Linear Algebra Error Prevention

### Rules

1. **Check matrix multiplication dimensions**: $A_{m \times n} \cdot B_{p \times q}$ is defined only if $n = p$. The result is $m \times q$.
2. **Record elementary row operations clearly**: $R_2 \leftarrow R_2 - 3R_1$ or $R_2 \to R_2 - 3R_1$. Track all row swaps, scaling, and addition operations.
3. **Determinant double-check**: Compute via two methods:
   - Expansion by minors (Laplace expansion)
   - Row reduction to triangular form (product of diagonal entries, times $(-1)^{\text{\#swaps}}$)
4. **Verify eigenvalues/eigenvectors by substitution**: For each eigenvalue $\lambda$ and eigenvector $\mathbf{v}$, check $A\mathbf{v} = \lambda\mathbf{v}$ directly.
5. **Check matrix invertibility before using $A^{-1}$**: $\det(A) \neq 0$ OR $\text{rank}(A) = n$ OR $A$ has $n$ pivot positions. Never assume a matrix is invertible.
6. **Diagonalization requires $n$ linearly independent eigenvectors**: A matrix is diagonalizable iff it has a full set of eigenvectors. Defective matrices (like Jordan blocks) cannot be diagonalized.
7. **Inner product = 0 for orthogonalization check**: After Gram-Schmidt, verify $\langle v_i, v_j \rangle = 0$ for $i \neq j$. Verify $\|v_i\| = 1$ if orthonormalization was the goal.
8. **Identify free variables in linear systems**: In reduced row echelon form, columns without pivots correspond to free variables. The dimension of the solution space equals the number of free variables.
9. **Rank-nullity theorem check**: $\text{rank}(A) + \text{nullity}(A) = n$ (number of columns). Use this as a consistency check.
10. **Similarity invariants**: Similar matrices have the same determinant, trace, eigenvalues, rank, and characteristic polynomial. If these don't match, the similarity claim is wrong.

### Common Pitfalls with Examples

| Pitfall | Wrong | Correct |
|---|---|---|
| Multiplying matrices in wrong order | $A \cdot B$ when dimensions don't match | Check $(m \times n) \cdot (n \times p)$ |
| Computing determinant of sum as sum of determinants | $\det(A+B) = \det(A) + \det(B)$ | $\det(A+B) \neq \det(A) + \det(B)$ in general |
| Assuming all matrices are diagonalizable | Claiming $\begin{pmatrix} 1 & 1 \\ 0 & 1 \end{pmatrix}$ is diagonalizable | It has $\lambda=1$ with algebraic multiplicity 2 but geometric multiplicity 1 — not diagonalizable |

### Prevention Strategy

1. **Write matrix dimensions** next to each matrix: $A_{3\times 2}$, $B_{2\times 4}$
2. **For Gaussian elimination: use augmented matrix and track operations**
3. **After computing eigenvalues: check sum = trace, product = determinant**
4. **For eigenvectors: substitute back and verify $A\mathbf{v} = \lambda\mathbf{v}$**
5. **For linear systems: express solution in parametric vector form**
6. **Use computational checks when available**: rank, determinant, eigenvalues should be consistent

---

## 8. Abstract Math Error Prevention

### Rules

1. **Check definition completeness**: Every object must be fully defined before any property is claimed. "Let $G$ be a group" is incomplete without specifying the operation.
2. **Check quantifier order**: "For every $x$ there exists $y$" ($\forall x \exists y$) is different from "There exists $y$ for every $x$" ($\exists y \forall x$). The order changes meaning radically.
3. **Verify constructions are well-defined**: When defining an operation on equivalence classes (e.g., $\bar{a} + \bar{b} = \overline{a+b}$ in $\mathbb{Z}/n\mathbb{Z}$), verify the result is independent of representatives.
4. **Equivalence relation verification (3 properties)**:
   - Reflexive: $a \sim a$ for all $a$
   - Symmetric: $a \sim b \implies b \sim a$
   - Transitive: $a \sim b$ and $b \sim c \implies a \sim c$
   - Missing any one means it's NOT an equivalence relation.
5. **Map well-definedness**: A function $f: X \to Y$ defined on equivalence classes or via representatives must be checked for independence of representation.
6. **Injective check**: $f(x_1) = f(x_2) \implies x_1 = x_2$. Do NOT confuse with "different inputs give different outputs" without proper logical formulation.
7. **Surjective check**: For every $y \in Y$, there exists $x \in X$ such that $f(x) = y$. Must prove existence, not just state it.
8. **Homomorphism preservation**: A map $\phi: G \to H$ is a homomorphism if $\phi(ab) = \phi(a)\phi(b)$. Must verify this explicitly — do not assume.
9. **Do not assume special space properties**: $\mathbb{R}^n$ is complete, connected, Hausdorff, but a general metric/topological space may lack these properties. Every claim must be justified by the specific definition.
10. **Counterexample awareness**: When studying a definition, immediately construct examples that satisfy the minimal axioms and nothing more, to avoid over-assuming properties.

### Common Pitfalls with Examples

| Pitfall | Wrong | Correct |
|---|---|---|
| Forgetting to check transitivity | Claiming a relation is an equivalence relation after checking only reflexive and symmetric | All three properties must be verified |
| Assuming all groups are abelian | $ab = ba$ assumed in a non-commutative group proof | Only valid if the group is explicitly abelian |
| Assuming metric spaces are complete | "The limit exists because the sequence is Cauchy" | Cauchy $\implies$ convergence only in COMPLETE spaces |
| Not verifying well-definedness | Defining $\frac{a}{b} + \frac{c}{d} = \frac{a+c}{b+d}$ on rationals | This is not well-defined: $\frac{1}{2} = \frac{2}{4}$ but $\frac{1+1}{2+3} \neq \frac{2+1}{4+3}$ |

### Prevention Strategy

1. **Write the full definition** of every algebraic structure at the start, listing all axioms
2. **For equivalence relations: explicitly check all 3 properties** — use a checklist
3. **For well-definedness: pick two different representations and verify they yield the same result**
4. **For counterexample search: construct the simplest possible example** (smallest group, simplest topological space)
5. **Label each inference with the axiom/theorem it uses** to prevent assuming unstated properties
6. **When generalizing from $\mathbb{R}^n$ to a general space: explicitly verify which properties of $\mathbb{R}^n$ are used** and whether they hold in the general case

---

## 9. Complex Analysis Error Prevention

### Rules

1. **Analyticity domain check**: Before applying Cauchy's theorem or residue calculus, verify the function is analytic on and inside the contour except at isolated singularities.
2. **Branch cut handling**: For multi-valued functions ($\log z$, $z^\alpha$, $\sqrt{z}$), explicitly define the branch cut and ensure the contour does not cross it.
3. **Singularity classification**: Correctly classify singularities as removable, pole (with order), or essential before applying residue formulas.
4. **Residue calculation verification**: For a pole of order $n$ at $z_0$: $\text{Res}(f, z_0) = \frac{1}{(n-1)!}\lim_{z\to z_0}\frac{d^{n-1}}{dz^{n-1}}[(z-z_0)^n f(z)]$. Verify the order before differentiating.
5. **Contour orientation**: Standard positive orientation is counterclockwise. Reversing orientation changes the sign of the integral.
6. **Jordan's lemma conditions**: For $\int_{-\infty}^\infty f(x)e^{iax}dx$ with $a > 0$, the semicircular arc contribution vanishes only if $|f(z)| \to 0$ uniformly as $|z| \to \infty$ in the upper half-plane.
7. **Argument principle application**: $\frac{1}{2\pi i}\oint_\gamma \frac{f'(z)}{f(z)}dz = N - P$ where $N$ = zeros, $P$ = poles (counted with multiplicity). Ensure $f$ has no zeros or poles ON the contour.
8. **Conformal mapping boundary correspondence**: When using conformal maps, verify that boundary points map correctly and the orientation is preserved.

### Common Pitfalls with Examples

| Pitfall | Wrong | Correct |
|---|---|---|
| Applying residue theorem across branch cut | Integrating $\log z$ around a circle centered at origin without accounting for branch cut | Define branch cut (e.g., negative real axis) and use keyhole contour |
| Miscounting pole order | $\frac{1}{(z-1)^2(z+1)}$ has a simple pole at $z=1$ | Pole at $z=1$ is order 2; pole at $z=-1$ is order 1 |
| Forgetting $2\pi i$ factor | $\oint \frac{dz}{z} = 1$ around unit circle | $\oint \frac{dz}{z} = 2\pi i$ |
| Wrong residue for essential singularity | Using pole formula for $e^{1/z}$ at $z=0$ | Use Laurent series: $\text{Res}(e^{1/z}, 0) = 1$ (coefficient of $1/z$) |

### Prevention Strategy

1. **Draw the contour and mark all singularities** before computing
2. **Identify branch cuts explicitly** for multi-valued functions
3. **Classify each singularity** before choosing a residue calculation method
4. **Check contour orientation** and apply sign accordingly
5. **Verify decay conditions** for infinite contours (Jordan's lemma, estimation lemma)

---

## 10. Topology Error Prevention

### Rules

1. **Open set definition dependence**: "Open" is relative to the topology. Always specify which topology is being used (standard, discrete, indiscrete, subspace, quotient, etc.).
2. **Continuity definition**: $f: X \to Y$ is continuous iff $f^{-1}(U)$ is open in $X$ for every open $U \subseteq Y$. Do NOT assume "$f$ maps open sets to open sets" (that's an open map, a different concept).
3. **Compactness vs closed+bounded**: In $\mathbb{R}^n$, compact $\iff$ closed and bounded (Heine-Borel). In general metric/topological spaces, this equivalence FAILS.
4. **Connectedness verification**: A space is connected if it cannot be written as a union of two disjoint non-empty open sets. Path-connected $\implies$ connected, but the converse fails (e.g., topologist's sine curve).
5. **Hausdorff property**: A space is Hausdorff if any two distinct points have disjoint neighborhoods. $\mathbb{R}^n$ is Hausdorff, but quotient spaces may not be.
6. **Homeomorphism requirements**: A homeomorphism must be bijective, continuous, AND have a continuous inverse. Bijective + continuous is NOT sufficient.
7. **Subspace topology**: For $A \subseteq X$, open sets in $A$ are intersections $U \cap A$ where $U$ is open in $X$. Do not assume $A$ inherits properties like compactness or connectedness without verification.
8. **Product topology basis**: Open sets in $\prod X_i$ are unions of products $\prod U_i$ where each $U_i$ is open in $X_i$ and $U_i = X_i$ for all but finitely many $i$ (for infinite products).

### Common Pitfalls with Examples

| Pitfall | Wrong | Correct |
|---|---|---|
| Assuming closed+bounded $\implies$ compact | "The set $(0,1)$ is bounded, so it's compact" | $(0,1)$ is NOT compact (not closed); $[0,1]$ IS compact in $\mathbb{R}$ |
| Confusing continuity with open mapping | "$f(x)=x^2$ is continuous, so it maps open sets to open sets" | $f((-1,1)) = [0,1)$ which is NOT open |
| Assuming connected components are open | "Connected components are always open" | Only true in locally connected spaces; false in general |
| Quotient space Hausdorff assumption | "The quotient of a Hausdorff space is Hausdorff" | Generally false; requires additional conditions |

### Prevention Strategy

1. **State the topology explicitly** at the start of any topological argument
2. **Use the correct definition of continuity** (preimage of open is open)
3. **Distinguish between properties that hold in $\mathbb{R}^n$ vs general spaces**
4. **Construct standard counterexamples** (topologist's sine curve, line with two origins, etc.) to test intuition
5. **Verify all homeomorphism conditions**, especially continuity of the inverse

---

## 11. Number Theory Error Prevention

### Rules

1. **Divisibility definition**: $a \mid b$ means $\exists k \in \mathbb{Z}$ such that $b = ak$. Note that $0 \mid 0$ is true (since $0 = k \cdot 0$ for any $k$), but $0 \mid b$ for $b \neq 0$ is false.
2. **Modular arithmetic domain**: Congruences $a \equiv b \pmod{n}$ are defined for integers. Extending to rationals or reals requires careful interpretation.
3. **Prime factorization uniqueness**: The Fundamental Theorem of Arithmetic applies to $\mathbb{Z}^+$ (positive integers). In other rings (e.g., $\mathbb{Z}[\sqrt{-5}]$), unique factorization may fail.
4. **Fermat's Little Theorem conditions**: $a^p \equiv a \pmod{p}$ for prime $p$ and any integer $a$. The form $a^{p-1} \equiv 1 \pmod{p}$ requires $\gcd(a,p) = 1$.
5. **Euler's totient function**: $\phi(n)$ counts integers in $\{1, 2, \ldots, n\}$ coprime to $n$. For $n = p_1^{e_1} \cdots p_k^{e_k}$: $\phi(n) = n \prod_{i=1}^k (1 - \frac{1}{p_i})$.
6. **Chinese Remainder Theorem**: The system $x \equiv a_i \pmod{n_i}$ has a unique solution mod $\text{lcm}(n_1, \ldots, n_k)$ if the moduli are pairwise coprime. Without coprimality, solutions may not exist or may not be unique.
7. **Quadratic reciprocity**: For odd primes $p, q$: $\left(\frac{p}{q}\right)\left(\frac{q}{p}\right) = (-1)^{\frac{p-1}{2} \cdot \frac{q-1}{2}}$. Check that both primes are odd before applying.
8. **Infinite descent validity**: Proof by infinite descent requires showing that assuming a solution exists leads to a smaller positive integer solution, contradicting well-ordering of $\mathbb{N}$.

### Common Pitfalls with Examples

| Pitfall | Wrong | Correct |
|---|---|---|
| Applying FLT without coprimality | "$2^4 \equiv 1 \pmod{4}$" (using $a^{p-1} \equiv 1$ with $p=2$) | FLT in form $a^{p-1} \equiv 1$ requires $\gcd(a,p)=1$; here $\gcd(2,4) \neq 1$ |
| Assuming unique factorization in all rings | "$6 = 2 \cdot 3 = (1+\sqrt{-5})(1-\sqrt{-5})$ shows non-uniqueness in $\mathbb{Z}$" | Non-uniqueness occurs in $\mathbb{Z}[\sqrt{-5}]$, NOT in $\mathbb{Z}$ |
| CRT without checking coprimality | Solving $x \equiv 1 \pmod{4}$, $x \equiv 2 \pmod{6}$ assuming unique solution mod 24 | $\gcd(4,6) = 2 \neq 1$; check consistency first ($1 \not\equiv 2 \pmod{2}$), no solution exists |
| Quadratic reciprocity for $p=2$ | Applying reciprocity formula with $p=2$ | Handle $p=2$ separately: $\left(\frac{2}{q}\right) = (-1)^{\frac{q^2-1}{8}}$ |

### Prevention Strategy

1. **Verify primality** before applying prime-specific theorems
2. **Check gcd conditions** for modular arithmetic results
3. **Specify the ring** when discussing factorization
4. **Test small cases** numerically before generalizing
5. **Use the extended Euclidean algorithm** to verify Bezout coefficients

---

## Cross-Domain Prevention Checklist

Before finalizing any mathematical answer, run through this summary checklist:

- [ ] **Algebra**: Back-substituted, domain verified, denominators non-zero, $\pm$ signs handled
- [ ] **Inequalities**: Sign reversals checked, boundary points included/excluded correctly
- [ ] **Functions**: Domain stated, all extremum candidates evaluated, range verified
- [ ] **Geometry**: All theorem conditions stated, diagram assumptions justified, degenerate cases checked
- [ ] **Probability**: Sample space defined, probabilities in $[0,1]$, sum to 1, variance $\geq 0$
- [ ] **Calculus**: L'Hôpital conditions checked, $+C$ added, convergence verified, limits checked
- [ ] **Linear Algebra**: Dimensions matched, eigenvalues verified by substitution, determinants double-checked
- [ ] **Abstract Math**: Definitions complete, quantifier order correct, constructions well-defined, all equivalence properties checked
- [ ] **Complex Analysis**: Analyticity verified, branch cuts handled, singularities classified, contour orientation correct
- [ ] **Topology**: Topology specified, continuity definition correct, compactness/connectedness properly verified
- [ ] **Number Theory**: Primality verified, gcd conditions checked, ring specified for factorization
