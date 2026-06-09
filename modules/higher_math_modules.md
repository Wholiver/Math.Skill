# Math.skill Higher Math Modules

The following defines detailed problem solving and calculation requirements for 8 areas of advanced mathematics.

---

## Module 1: Limits

### Coverage
- Sequence limit: Existence and calculation of `lim_{n→∞} a_n`
- Function limit: `lim_{x→a} f(x)` (including `x→∞`)
- One-sided limits: `lim_{x→a+}`, `lim_{x→a-}`
- Comparison of infinitesimals: equivalent infinitesimals, higher order/lower order/same order/equivalent
-Taylor expansion method to find the limit
- Squeeze Theorem
- Monotone bounded theorem (monotone bounded must converge)
- Stolz's theorem (sequence L'Hôpital)
- L'Hôpital's law (function limits)
- asymptotic expansion

### Core theorem and applicable conditions

| Theorem | Applicable conditions |
|------|----------|
| Pinch Theorem | `a_n ≤ b_n ≤ c_n` and `lim a_n = lim c_n = L` |
| Monotone bounded theorem | The sequence is monotonically increasing and has an upper bound; or is monotonically decreasing and has a lower bound |
| Stolz's theorem | The denominator is strictly monotonic to `∞` (type `∞/∞`) or the numerator and denominator tend to `0` (type `0/0`); the limit must exist or be `∞` |
| L'Hôpital's Law | Infinitive `0/0` or `∞/∞` ; the limit of the derivative ratio exists or is `∞` |
| Taylor expansion | The function has continuous derivatives of sufficient order near the expansion point |

### Common pitfalls
1. **Stolz’s theorem conditions are not met**: the denominator must be monotonic infinity and cannot just tend to infinity.
2. **L'Hôpital recycling**: The infinitive cannot be eliminated after repeated use, and other methods need to be used.
3. **Insufficient order of Taylor expansion**: It leads to equivalent infinitesimal cancellation and requires higher order expansion.
4. **Ignoring the situation where the limit does not exist**: The left and right limits are not equal
5. **Use L'Hôpital for a sequence**: L'Hôpital only works with function limits

### Verification strategy
- **Theorem Condition Check**: Verify whether the conditions of the theorem used are met one by one.
- **Left and right consistency check**: For the limit of `x→a`, check whether the left and right limits are consistent
- **Expansion order check**: Confirm that the Taylor expansion order is sufficient and the remainder is controllable
- **Numerical verification**: Approximate calculation using specific numerical values ​​and compare with analytical results
- **Clamp verification**: Check whether the upper and lower bounds of the clamp are correct and equal

---

## Module 2: Differentiation

### Coverage
- Derivatives of functions of one variable
- Partial derivatives (multivariate functions)
- Implicit function derivation
- Derivation of parametric equations
- Higher order derivatives
- Extreme value and maximum value (univariate and multivariate)
- Concave-convexity and inflection points
- Taylor formula (including remainder)
- Directional Derivatives and Gradient (Basic)

### Core theorem and applicable conditions

| Theorem | Applicable conditions |
|------|----------|
| Fermat's theorem | The function is differentiable at the extreme point → the derivative is zero |
| Rolle's Theorem | `f(a)=f(b)` and continuous at `[a,b]`, `(a,b)` is differentiable |
| Lagrange's Mean Value Theorem | Continuous at `[a,b]`, Differentiable at `(a,b)` |
| Existence theorem of implicit functions | Partial derivatives are continuous and Jacobian is non-zero |
| Multivariate extreme value determination | Hessian matrix positive definite (minimum)/negative definite (maximum)/indefinite (saddle point) |

### Common pitfalls
1. **Forgot to use the chain rule when deriving implicit functions**: `d/dx[f(g(x),h(x))]`
2. **Forgot to check the sufficient conditions for extreme values**: It is only a necessary condition that the first derivative is zero
3. **Boundary point missing**: The maximum value of a closed interval may be obtained at the endpoint
4. **Hessian matrix semi-qualitative**: The extreme value type cannot be determined and higher-order analysis is required.
5. **Linear approximation error underestimation**: wrong order judgment of Taylor remainder

### Verification strategy
- **Inverse operation verification**: Derivative of the obtained indefinite integral should return the original function
- **Numerical Difference Verification**: Compare with analytic derivative using finite difference `(f(x+h)-f(x))/h`
- **First-order/second-order condition verification**: Check whether the extreme point satisfies both first-order and second-order conditions
- **Boundary point exhaustion**: Check all candidate points (stationary points, boundary points, non-differentiable points)
- **Hessian verification**: For multivariate extrema, calculate the Hessian and verify positive/negative definiteness

---

## Module 3: Integration

### Coverage
- Indefinite integrals: substitution method, integral by parts, integral of rational functions, trigonometric integral
- Definite integral: Newton-Leibniz formula
- Abnormal integral (generalized integral): Convergence determination
- Multiple integration: cumulative integration, coordinate transformation (polar coordinates, cylindrical coordinates, spherical coordinates)
- Exchange points (including Jacobian)
- Division points
- Curve integral and surface integral (basic level)

### Core theorem and applicable conditions

| Theorem | Applicable conditions |
|------|----------|
| Newton-Leibniz formula | The integrand is continuous in the integration interval, and the original function is continuously differentiable in the interval |
| Substitution integral method | The substitution function is continuously differentiable, and the integration interval transformation is correct |
| Integration by parts method | The two parts can be differentiated/integrated respectively |
| Integral mean value theorem | Functions are continuous in closed intervals |
| Abnormal integral comparison and discrimination method | Non-negative integrand, comparison function with known convergence |

### Common pitfalls
1. **Forgot to transform the integral limit when changing elements**: After changing the element of the definite integral, the upper and lower limits need to correspond to the new variables
2. **Inappropriate selection of division integration direction**: The splitting direction that can simplify should be selected
3. **Abnormal integral convergence condition is missing**: first determine whether convergence occurs, and then calculate
4. **Multiple integration order commutative conditions not checked**: Fubini’s theorem requires absolute integrability
5. **Jacobian omission or miscalculation during coordinate transformation**:
6. **Partial fraction decomposition error of rational function**: Incomplete factorization of the denominator

### Verification strategy
- **Indefinite integral derivation verification**: Derivative of the result should be equal to the integrand
- **Numerical approximation of definite integrals**: estimate using Simpson or trapezoidal method and compare with analytical results
- **Change transformation verification**: Check whether the integration interval transformation is correct
- **Convergence Verification**: For anomalous integrals, a priori convergence is required before calculating the value.
- **Inverse operation of integral by parts**: can be verified by the other direction of integral by parts

---

## Module 4: Linear Algebra (Linear Algebra)

### Coverage
- Matrix operations (addition, multiplication, transpose, inversion)
- Calculation and properties of determinants
- rank of matrix
- Solving linear equations (homogeneous/non-homogeneous)
- Vector spaces and subspaces
-Linear dependence and linear independence
- Eigenvalues ​​and eigenvectors
-Matrix diagonalization
- Gram-Schmidt orthogonalization
- Quadratic form and positive certainty

### Core theorem and applicable conditions

| Theorem | Applicable conditions |
|------|----------|
| Rank-zero degree theorem | For any matrix `A`: `rank(A) + nullity(A) = n` |
| Cramer's rule | The coefficient matrix is ​​a square matrix and the determinant is non-zero |
| Cayley-Hamilton Theorem | Any square matrix satisfies its characteristic polynomial |
| Spectral theorem (real symmetry) | Real symmetric matrices can be orthogonally diagonalized |
| Determination of positive definite quadratic form | All sequential principal formulas > 0 |

### Common pitfalls
1. **Feature vector calculation error**: `(A-λI)v=0`, not `(A-λ)v=0`
2. **Diagonalization condition is not met**: The matrix must be diagonalizable (geometric multiplicity = algebraic multiplicity)
3. **Inverse when the determinant is zero**: Reversibility should be checked first
4. **Misjudgment of rank**: row rank = column rank, but you need to be careful when performing row and column operations
5. **Incomplete representation of solutions to linear equations**: Forgot to include the general solution part of the homogeneous solution
6. **Gram-Schmidt numerical instability**: possible loss of orthogonality in large-scale calculations

### Verification strategy
- **Dimension Validation**: `rank + nullity = n`
- **Back substitution verification**: Substitute the solution into the original equation and verify `Ax = b`
- **Eigenvalue Validation**: Verify `det(A - λI) = 0` for each eigenvalue
- **Feature Vector Validation**: Validation `Av = λv`
- **Diagonal Verification**: Verify `A = PDP^{-1}` or `P^T A P = D`
- **Inverse Matrix Verification**: Verification `A A^{-1} = I`
- **Orthogonality Verification**: Verify `Q^T Q = I`

---

## Module 5: Ordinary Differential Equations (ODEs)

### Coverage
- Equations of separable variables
- First order linear differential equation
- Homogeneous equations
- Linear differential equations with constant coefficients (homogeneous/non-homogeneous)
- Initial value problem (IVP)
- System of simple differential equations

### Core theorem and applicable conditions

| Theorem | Applicable conditions |
|------|----------|
| Existence and uniqueness theorem (Picard-Lindelöf) | `f(t,y)` satisfies the Lipschitz condition with respect to y |
| Superposition principle (homogeneous linearity) | A linear combination of solutions is still a solution |
| Characteristic equation method | Homogeneous linear differential equations with constant coefficients |
| Undetermined coefficient method | Non-homogeneous terms are the products/sums of polynomials, exponentials, and trigonometric functions |
| Constant mutation method | Applicable to any non-homogeneous linear ODE (if a homogeneous solution can be found) |

### Common pitfalls
1. **Forgot the integral constant**: `+ C` must be added after the indefinite integral
2. **Confusion between general solution and special solution**: Initial value problem requires determination of constants
3. **The number of constants does not match the order**: The general solution of an n-order ODE should have n independent constants
4. **Confusion between homogeneous and non-homogeneous solutions**: General solution = Homogeneous general solution + Non-homogeneous special solution
5. **Error in handling multiple root cases**: The solution is specially constructed when the characteristic equation has multiple roots.
6. **Incomplete guess on the form of the undetermined coefficient method**: When the non-homogeneous term overlaps with the homogeneous solution, it needs to be multiplied by `t^k`

### Verification strategy
- **Substitute into the original equation to verify**: Substitute the obtained solution into ODE and check whether the equation is always true.
- **Initial value condition check**: Substitute `t=t_0` into the solution to verify whether the initial value is met
- **Independence check of solutions**: Wronski determinant is non-zero
- **General solution completeness**: number of independent solutions = order of equation
- **Check for the number of constants**: Number of independent constants in the general solution = Order of the equation

---

## Module 6: Basics of Real Analysis (Real Analysis)

### Coverage
- Judgment of convergence and divergence of sequence
- Continuity and consistent continuity
- Differentiability and derivatives
- Basic properties of Riemann integrals
- Series convergence (positive terms, staggered terms, arbitrary terms)
- Consistent convergence of function sequences and function term series

### Core theorem and applicable conditions

| Theorem | Applicable conditions |
|------|----------|
| Cauchy Convergence Criterion | Complete Metric Space (Real Numbers, Complex Numbers) |
| Bolzano-Weierstrass Theorem | A bounded sequence must have a convergent subsequence |
| Intermediate value theorem of continuous functions | Functions are continuous in closed intervals |
| Uniform continuity theorem | Continuous functions on closed intervals must be uniformly continuous |
| Weierstrass M criterion | Control series with convergent function term series |
| Continuity of uniform convergence limit | Consistently convergent continuous function sequence, limit function continuity |

### Common pitfalls
1. **The order of quantifiers is reversed**: The consistent and continuous `∀ε ∃δ ∀x,y` is different from the point-state continuous `∀ε ∀x ∃δ`
2. **ε-δ and ε-N are confused**: use ε-N for sequences and ε-δ for functions.
3. **Confusion between point-state convergence and uniform convergence**: Uniform convergence means point-state convergence, but not vice versa.
4. **Use conclusions when conditions are lacking**: such as using the intermediate value theorem on discontinuous closed intervals
5. **Conditions for series rearrangement**: Absolute convergence can lead to arbitrary rearrangement
6. **Exchange of limits and integrals**: Requires consistent convergence or controlled convergence theorem

### Verification strategy
- **Quantifier order verification**: Check the quantifier structure of ε-δ or ε-N
- **Counterexample construction**: If you have doubts about a certain promotion, construct a counterexample test
- **Pointwise Convergence vs Uniform Convergence**: Check if the supremum approaches zero
- **Continuity Verification**: Check whether the limit definition and the left and right limits are consistent

---

## Module 7: Abstract Algebra

### Coverage
- Groups: subgroups, normal subgroups, quotient groups, fundamental theorem of homomorphism
- Ring: sub-ring, ideal, business ring
- Basic concepts of domain
- Basics of Polynomial Rings

### Core theorem and applicable conditions

| Theorem | Applicable conditions |
|------|----------|
| Lagrange's theorem | Finite group, the order of the subgroup is divided by the order of the group |
| Cayley's theorem | Any group is isomorphic to a subgroup of a permutation group |
| Fundamental Theorem of Homomorphism | `G/ker(φ) ≅ Im(φ)` |
| First isomorphism theorem | Correspondence between subgroups and normal subgroups |
| Chinese Remainder Theorem (Ring Theory Edition) | Ideal pairs are relatively prime |

### Common pitfalls
1. **Subgroup verification missing**: Need to verify closure, identity element, and inverse element (or equivalently `ab⁻¹ ∈ H` )
2. **Normal subgroup vs subgroup**: The statement that all subgroups are normal subgroups is only true in Abelian groups
3. **Incomplete homomorphism verification**: It is necessary to verify that the operation is maintained and the unit is maintained
4. **Goodness of business group**: It is necessary to confirm the formal subgroup first
5. **Relationship between the order of the group and the order of the elements**: The order of the element divides the order of the group, and the converse proposition is not always true.
6. **Generalize from partial to complete**: After having a few conclusions about small-order groups, directly generalize to all groups.

### Verification strategy
- **Closedness Check**: Generate all pairs of elements and verify that the product is within the set
- **Inverse check**: Each element has a unique inverse
- **Associative Law Check**: Check the triple product of specific elements
- **Homomorphic structure preservation verification**: `φ(ab) = φ(a)φ(b)`
- **Good Qualitative Verification of Business Groups**: The left and right cosets are equal
- **Prefer small-order counterexamples**: test each conjecture with small-order groups (such as S₃, D₄, Z₆)

---

## Module 8: Topology Basics

### Coverage
- Definition of open sets, closed sets, and topological spaces
- Topological definition of continuous mapping
- Basic properties of compactness
- Basic properties of connectedness
- Basic concepts of metric space

### Core theorem and applicable conditions

| Theorem | Applicable conditions |
|------|----------|
| Heine-Borel Theorem | `R^n` The neutron set compact iff is bounded and closed |
| Continuous functions maintain compactness | Continuous images map compact sets into compact sets |
| Intermediate value theorem (connectivity version) | Continuous image maps connected sets to connected sets |
| Tietze's expansion theorem | Closed subsets in normal spaces |
| Bolzano-Weierstrass theorem (metric space version) | Equivalence of compaction and compactness |

### Common pitfalls
1. **Extrapolate the intuition of Euclidean spaces to general topological spaces**: Not all topological spaces are Hausdorff spaces
2. **Confusion of compactness equivalence conditions**:
- In metric space: compact ↔ compact ↔ complete and fully bounded
- In general topological spaces: these equivalences do not necessarily hold
3. **Duality of open sets and closed sets**: The complement of an open set is a closed set, but there are sets that are both open and closed, and neither open nor closed.
4. **The sequence definition of continuous mapping is not suitable for general topological spaces**: the convergence concept of the network is required
5. **Connected spaces are not necessarily road-connected**: Famous counterexamples in topology (such as topologists’ sinusoids)
6. **The closed subset of a compact space is compact**, but the compact space needs to be Hausdorff's

### Verification strategy
- **Definition consistency check**: Check the open set axioms in the definition of topological space item by item
- **Counterexample search**: For each suspected generalization, find counterexamples in `R^n` or limited topology
- **The difference between metric spaces and general topological spaces**: Note which properties only apply to metric spaces
- **Hausdorff condition check**: Some conclusions require Hausdorff conditions (such as closure of compact subsets)
- **Compactness Verification**: Check whether each open cover has finite subcovers

---

## Common cross-module considerations

### Domain and Condition Checklist
It is mandatory to check before solving the problem:
- [ ] What is the domain of a function?
- [ ] Are all the conditions of the theorem used met?
- [ ] Are there degenerate boundary cases (zero, infinity, singularity)?
- [ ] Do all variables used have clear scopes?

### Common cross-domain errors
1. **Non-zero is not checked before division**
2. **Non-negative is not checked before formulating**
3. **Use derivation at non-differentiable points**
4. **Use integrals at discontinuous points**
5. **Using Riemann integrals on non-Riemann integrable functions**
6. **Calculating series sums without checking convergence**

### Cross-domain consistency of verification
- The conclusions of each module should be consistent with the conclusions of other modules
- If there are multiple ways to solve the same problem, use another method to check the calculation
- Pay special attention to the consistency of symbols, units and dimensions
