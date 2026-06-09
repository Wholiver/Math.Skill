#Input classification module

## Overview

This module defines the classification system for input problems in Math.skill. For each input, the system first classifies it into one of the following categories and then selects an appropriate solution strategy and verification method based on the characteristics of the category.

---

## calculation

**Identification Features:**
- Input contains only numeric values ​​and operators ($+,-,\times,\div,\hat{\ },\sqrt{}$ etc.)
- No variables, no equal sign or inequality sign
- Common expressions: "calculation", "evaluation", "what is the result"
- Example: $\sqrt{169} + 3^4 - 12 \div 4$

**Recommended solution strategy:**
- Calculate step by step according to operation priority
- Use parentheses to clarify the order of operations
- Decompose complex expressions step by step, and verify each step independently

**Conditions that must be checked:**
- The denominator of the division in the expression is not zero
- Expression under even-numbered radicals $\geq 0$
- base of logarithm $>0$ and $\neq 1$ , real number $>0$
- Whether the exponential operation result is within a reasonable range

**Common mistakes:**
- Incorrect operation priority (such as addition first and then multiplication)
- Negative sign handling error ($(-3)^2 = 9$, not $-9$)
- Common division errors in fraction operations
- Precision is lost when decimals and fractions are mixed
- Large number operation overflow or rounding error

**Recommended verification method:**
- Verification of inverse operation (use the result to infer)
- Is the estimated magnitude reasonable?
- Recalculate using different calculation paths
- Cross-validation of key intermediate results

**Output format:**
 ```
Result: [exact value]
Step-by-step calculation process: [Each step operation and intermediate results]
```

**Whether to ask the user:** No

---

## algebra_simplification

**Identification Features:**
- Expressions containing algebraic variables requiring reduction, factorization or expansion
- Keywords: "simplify", "factorization", "expand", "merge similar terms"
- Example: Simplify $(x+2)(x-3) - (x-1)^2$

**Recommended solution strategy:**
- Recognize expression structures (polynomials, fractions, radicals, etc.)
- Apply the distributive property to expand the brackets
- Merge similar items
- When factoring, first extract the common factors and then apply the formula

**Conditions that must be checked:**
- Conditions when the denominator is not zero
- Expression under even-numbered roots $\geq 0$
- Whether the factorization result is completely decomposed
- Whether the expansion result has merged all similar items

**Common mistakes:**
- Sign handling error (positive and negative signs on expansion)
- Missing items (forgot to expand all items)
- Incomplete factorization
- Misuse of square difference/perfect square formula
- Domain constraints are forgotten when simplifying fractions

**Recommended verification method:**
- Substitute special values ​​to check whether both ends are equal
- Re-expand the simplified results to verify whether they are equal to the original formula
- Check whether the factored result multiplied back is equal to the original formula
- Verify that domain constraints are consistent

**Output format:**
 ```
Simplification result: [simplest form]
Key steps: [Transformation of each step]
Note: [Domain constraints]
```

**Whether to ask the user:** Only if the expression is ambiguous

---

## equation_solving

**Identification Features:**
- A single equation with one unknown
- Keywords: "solve equations", "find $x$", equation
- Example: Solve the equation $2x^2 - 5x + 2 = 0$

**Recommended solution strategy:**
- Determine the type of equation (linear, quadratic, higher degree, fraction, radical, exponential, logarithmic, trigonometric, etc.)
- Linear: solution using the transfer method
- Quadratic: discriminant method $\Delta = b^2 - 4ac$, root formula $x = \frac{-b \pm \sqrt{\Delta}}{2a}$
- Higher order: factorization or root trial method
- Fraction: solve after removing the denominator, pay attention to adding roots
- Radical formula: square root elimination, pay attention to root addition

**Conditions that must be checked:**
- Whether there are increasing roots (substitute into the original equation to verify)
- The discriminant of the quadratic equation $\Delta$ is $\geq 0$
- The denominator of a fractional equation is not zero
- The radicand of a radical equation is non-negative
- Logarithmic equations have real numbers $>0$, bases $>0$ and $\neq 1$

**Common mistakes:**
- Forgot to verify root addition
- Missing solution to quadratic equation (two roots when $\Delta > 0$)
- divide by an expression that may be zero
- The root of the radical equation is not tested after squaring it
- Wrong sign when moving items

**Recommended verification method:**
- Substitute all solutions into the original equation to verify that they are established
- Check if the solution is within the domain
- Verify $x_1 + x_2 = -b/a$, $x_1 x_2 = c/a$ for quadratic equations
- Graphical method verification (intersection of function graph and $x$ axis)

**Output format:**
 ```
Equation type: [linear/quadratic/higher degree/fractional/radical/...]
Solution: $x = [value]$ (or $x_1 = [value], x_2 = [value]$)
Solution steps: [Key transformation steps]
Domain constraint: [illegal values ​​to exclude]
Root verification: [Insert verification result]
```

**Whether to ask the user:** Only if the equation is ambiguous or missing constraints

---

## system_of_equations

**Identification Features:**
- Multiple equations with multiple unknowns
- Keywords: "system of equations", multiple equations connected with braces
- Example: $\begin{cases} 2x + y = 5 \\ x - 3y = -1 \end{cases}$

**Recommended solution strategy:**
- System of linear equations: substitution method, elimination method, matrix method
- Nonlinear equations: substitution method, elimination method, factorization
- Symmetric systems of equations: Simplification using symmetry
- System of homogeneous equations: Ratio method

**Conditions that must be checked:**
- The relationship between the number of equations and the number of unknowns
- Is the coefficient matrix of the linear equation system singular?
- Whether there are infinitely many solutions or no solutions
- Root augmentation after substitution of nonlinear equations

**Common mistakes:**
- Error in coefficient multiplication/addition during elimination
- Incomplete substitution
- Ignore cases where there are no solutions or infinite solutions
- Introduction of increasing roots after transformation of nonlinear equations
- Omissions when exploiting symmetry

**Recommended verification method:**
- Verify by substituting all solutions into each equation
- Verification after solving linear equations using matrix method $A\vec{x} = \vec{b}$
- Cross-validation using Clem's rule for systems of linear equations in two variables

**Output format:**
 ```
System type: [Linear/Nonlinear]
Solution: $(x, y) = ([value], [value])$ (or $x = [value], y = [value], z = [value]$)
Solution method: [Substitution method/Elimination method/Matrix method]
Number of solutions: [unique solution/infinitely many solutions/no solutions]
Verification: [Results inserted into each equation]
```

**Whether to ask the user:** Confirm the processing method only when the equation is not satisfied with the rank

---

## inequality_solving

**Identification Features:**
- Expressions containing the inequality sign ($>, <, \geq, \leq$)
- Keywords: "solve inequalities", "find the range of $x$", "inequality group"
- Example: Solving Inequalities $\frac{x-1}{x+2} \geq 0$

**Recommended solution strategy:**
- First degree inequalities of one variable: shift terms, pay attention to the reverse direction of the negative signs in multiplication and division
- Quadratic inequalities of one variable: discriminant + root distribution, number axis through root method
- Fractional inequality: analysis of the same sign in the numerator and denominator after the common denominator is transferred.
- Absolute value inequalities: classification discussion or geometric significance
- Group of inequalities: solve them separately and find the intersection
- Higher-order inequalities: Number axis threading method (odd threads and even threads are not threaded)

**Conditions that must be checked:**
- Whether the direction of the inequality is reversed when multiplying or dividing negative numbers
- The denominator of the fraction inequality is not zero
- Are all branches of the absolute value inequality complete?
- Whether the endpoint of the interval is included (whether the equal sign is true)

**Common mistakes:**
- Forgetting to reverse the direction of the inequality sign when multiplying negative numbers
- Direct cross multiplication of fractional inequalities
- Forgetting to discuss symbols when squaring both sides
- Incomplete discussion of absolute value classification
- Wrong interval representation (confusion of open and closed intervals)

**Recommended verification method:**
- Take test points within the solution interval to verify the original inequality
- Take test points outside the solution interval to confirm that it is not established.
- Check the endpoints of the interval (substitute the equal case)
- Number line verification method

**Output format:**
 ```
Inequality type: [primary/quadratic/fraction/absolute value/inequality group]
Solution set: $x \in [interval expression]$
Key steps: [Classification discussion process]
```

**Whether to ask the user:** No

---

## function_analysis

**Identification Features:**
- Given a function expression, ask to analyze its properties
- Keywords: "definition domain", "range", "monotonicity", "parity", "extreme value", "maximum value", "image"
- Example: Analyze the properties of function $f(x) = \frac{x^2-1}{x-2}$

**Recommended solution strategy:**
- Domain: exclude denominator zero, negative root sign, true logarithm number $\leq 0$, etc.
- Value range: inverse function, combination method, derivation method, image method
- Monotonicity: derivation judgment symbol, monotonicity rule of composite functions
- Parity: Verify $f(-x) = f(x)$ (even) or $f(-x) = -f(x)$ (odd)
- Extreme value: Find the critical point by taking the derivative, and determine the type of extreme value by using the second-order derivative.
- Image: find key points (zero points, extreme points, inflection points, asymptotes) and depict trends

**Conditions that must be checked:**
- Define all constraints within the domain
- Existence of derivatives (non-differentiable points may be extreme points)
- Asymptotes: horizontal, vertical, oblique asymptotes
- Continuity of piecewise functions

**Common mistakes:**
- Missing domain (only denominator is considered, root sign or logarithm is ignored)
- Composite function domain error
- Confusion of extreme points (stationary points are not necessarily extreme points)
- Error in endpoint handling of monotonic intervals
- Ignore odd functions at $x=0$ $f(0)=0$

**Recommended verification method:**
- Take special points to verify function values
- Validation of derivation results against integrals
- Use symmetry to verify parity
- Verify extreme points using monotonicity

**Output format:**
 ```
Function: $f(x) = [expression]$
Domain: $x \in [interval]$
Range: $f(x) \in [interval]$
Monotonicity: [increasing and decreasing intervals]
Parity: [odd function/even function/neither odd nor even]
Extreme value: [Extreme point coordinates]
Asymptote: [Asymptote equation]
```

**Whether to ask the user:** Only when the function definition is not clear

---

## geometry

**Identification Features:**
- Involving plane geometric figures: triangles, quadrilaterals, circles, etc.
- Keywords: "proof", "verification", "area", "congruence", "similarity", "angle"
- Example: In $\triangle ABC$, $AB=AC$, verify $\angle B = \angle C$

**Recommended solution strategy:**
- Draw pictures to aid understanding
- Identify known conditions and verification goals
- Congruent judgment: SSS, SAS, ASA, AAS, HL
- Similarity determination: AA, SAS, SSS
- Area method, vector method, coordinate method
- Auxiliary line construction (midpoint line, perpendicular line, parallel line)

**Conditions that must be checked:**
- Triangle inequality (the sum of any two sides is greater than the third side)
- Angle sum constraints (triangle angle sum $180^\circ$ )
- Is the congruent/similar correspondence correct?
- The rationality of the auxiliary line construction

**Common mistakes:**
- Congruent/similar corresponding vertices are in the wrong order
- The construction of auxiliary lines is unreasonable or redundant
- Ignore special cases such as collinearity and common points
- Unit confusion (degrees and radians) when calculating angles
- Misuse of area formula

**Recommended verification method:**
- Construct specific numerical verification (special triangle)
- Cross-validation using different methods
- Protractor or coordinate method to verify angles
- Backward verification

**Output format:**
 ```
Known: [condition]
Proof/Solution: [Objective]
Proof/Solution Steps: [Reasoning Process]
Auxiliary lines: [Description of added auxiliary lines]
Conclusion: [Final Result]
```

**Whether to ask the user:** Yes, you need to confirm whether there are attached pictures or supplementary conditions

---

## analytic_geometry

**Identification Features:**
- Geometric problems in coordinate systems, involving points, straight lines, circles, and conics
- Keywords: "coordinates", "equation of a straight line", "equation of a circle", "ellipse", "hyperbola", "parabola"
- Example: Find the equation of the straight line passing through the point $(1,2)$ and parallel to the straight line $2x-y+3=0$

**Recommended solution strategy:**
- Establish a suitable coordinate system
- Use distance formula and slope formula
- Equation of a circle: $(x-a)^2 + (y-b)^2 = r^2$
- Line position relationship: parallel (slopes are equal), perpendicular (the product of slopes is $-1$ )
- Distance: point to line $d = \frac{|Ax_0+By_0+C|}{\sqrt{A^2+B^2}}$
- Definition and standard equations of conic sections

**Conditions that must be checked:**
- Case where slope does not exist (vertical line)
- A straight line cannot be determined when two points coincide
- Judgment of tangency/intersection/separation between circles and straight lines
- Is the standard form of a conic section correct?

**Common mistakes:**
- The denominator of the slope formula is not processed when it is zero.
- Forgot to add the absolute value in the distance formula
- The formula for the angle between two straight lines is used incorrectly
- Wrong formula for circle equation
- $a,b,c$ relation confusion in ellipse/hyperbola

**Recommended verification method:**
- Verify whether the substitution point is on the curve
- Symmetry verification
- Cross-validation of different methods to solve the same problem
- Visual inspection of drawings

**Output format:**
 ```
Coordinate system: [Rectangular coordinates/polar coordinates]
The equation of the geometric object sought: [equation]
Solution steps: [Derivation process]
Key properties: [Focus/Directrix/Circle Center/Radius, etc.]
```

**Whether to ask the user:** Only when the coordinate system or conditions are unclear

---

## trigonometry

**Identification Features:**
- Involves trigonometric functions $\sin, \cos, \tan$ etc.
- Keywords: "Trigonometric functions", "Trigonometric identities", "Solution of triangles", "Sine theorem", "Cosine theorem"
- Example: Proof $\sin^2\theta + \cos^2\theta = 1$

**Recommended solution strategy:**
- Memorize and apply basic identities
- Sum and difference formula: $\sin(A \pm B), \cos(A \pm B)$
- Double angle formula: $\sin 2\theta = 2\sin\theta\cos\theta$
- Solve triangles: sine theorem $\frac{a}{\sin A} = 2R$, cosine theorem $a^2 = b^2 + c^2 - 2bc\cos A$
- Trigonometric equations: using periodicity to find general solutions

**Conditions that must be checked:**
- Angle range (acute angle, $[0, 2\pi)$, etc.)
- Trigonometric function domain ($\tan\theta$ in $\theta \neq \frac{\pi}{2}+k\pi$)
- Solutions of triangles (one solution/two solutions/no solution)
- Units for radians and angles are unified

**Common mistakes:**
- Sine theorem/cosine theorem application errors
- Incorrect determination of the number of triangle solutions (SSA case)
-Induced formula symbol errors
- Missing general explanation
- Mixing radians and degrees

**Recommended verification method:**
- Verify the identity by substituting special angles
- Calculate the same angle on both sides of the trigonometric identity
- Verify triangle angle sum $180^\circ$
- Use different methods to find the same amount of cross-validation

**Output format:**
 ```
Solve/Prove: [Objective]
Use the formula: [sine theorem/cosine theorem/sum and difference formula/...]
Steps: [Derivation process]
Result: [angle value/side length/identity proof]
Number of solutions: [One solution/Two solutions/No solution]
```

**Whether to ask the user:** Only when the angle range is unclear

---

## sequence

**Identification Features:**
- Involving the definition, general terms and summation of sequence
- Keywords: "arithmetic sequence", "geometric sequence", "general formula", "sum of first $n$ terms", "recursion"
- Example: Given that $\{a_n\}$ is an arithmetic sequence, $a_3=5$ , $a_7=13$ , find $a_n$ and $S_n$

**Recommended solution strategy:**
- Equal differences: $a_n = a_1 + (n-1)d$, $S_n = \frac{n(a_1+a_n)}{2} = na_1 + \frac{n(n-1)}{2}d$
- Equivalent: $a_n = a_1 q^{n-1}$, $S_n = \frac{a_1(1-q^n)}{1-q}$ ($q \neq 1$)
- Recursive sequence: characteristic root method, accumulation/accumulation multiplication method, fixed point method
- General term and summation relationship: $a_n = S_n - S_{n-1}$ ($n \geq 2$)

**Conditions that must be checked:**
- Range of $n$ ( $n \in \mathbb{N}^*$ )
- Special case of geometric sequence common ratio $q=1$
- Initial conditions for recursive formulas
- The case where the characteristic root is a complex root
- The sum of infinite decreasing geometric sequences ($|q| < 1$)

**Common mistakes:**
- Confusion with equal difference/equal ratio formulas
- The initial item of the recursive sequence is incorrectly substituted into the range
- The special case of missing $q=1$ in proportional summation
- Wrong calculation of number of terms when summing by groups
- Misplaced subtraction sign error

**Recommended verification method:**
- Substitute the first few items to verify the general formula
- Directly list the first few items and compare them
- Verify using $a_n = S_n - S_{n-1}$
- Mathematical induction verification

**Output format:**
 ```
Sequence type: [arithmetic/equal ratio/recursion]
General formula: $a_n = [expression]$
Sum of first $n$ terms: $S_n = [expression]$
Derivation steps: [Process]
```

**Whether to ask the user:** Only if the initial conditions are incomplete

---

## combinatorics

**Identification Features:**
- Involving counting problems, permutations and combinations
- Keywords: "arrangement", "combination", "how many types", "selection method", "arrangement method"
- Example: Select 3 people from 5 boys and 4 girls to form a committee, requiring at least 1 girl. How many choices are there?

**Recommended solution strategy:**
- Arrangement: in order, $A_n^m = \frac{n!}{(n-m)!}$ or $P_n^m$
- Combination: no order, $C_n^m = \binom{n}{m} = \frac{n!}{m!(n-m)!}$
- Principle of classification counting (addition principle) and step counting principle (multiplication principle)
- Complement method: subtract the total number that does not meet the conditions
- Bundling method and interpolation method to deal with adjacent/non-adjacent problems

**Conditions that must be checked:**
- Are there duplicate elements?
- Whether to consider order (permutation vs combination)
- Whether to allow repeated selection
- Whether the classification is complete and non-overlapping

**Common mistakes:**
- Confusion of permutations and combinations
- Overlapping categories lead to double counting
- Classification missing
- Wrong calculation of insertion position for adjacent/non-adjacent questions
- Wrong judgment on the applicable conditions of the Partition Law

**Recommended verification method:**
- Validation of smaller enumerations
- Complementary set method cross-validation
- Recursive formula verification
- Use different classification methods to get the same results

**Output format:**
 ```
Question Type: [Permutation/Combination/Mixed]
Method: [Classification counting/step counting/complement method/bundling method/...]
Calculation: [Formula Substitution]
Result: [numeric value]
Enumeration verification (small scale): [enumeration result]
```

**Whether to ask the user:** Only if there is ambiguity between "same" and "different" elements

---

## probability_statistics

**Identification Features:**
- Involving probability calculations, random variables, distributions, statistics
- Keywords: "probability", "expectation", "variance", "distribution", "Bayes", "normal distribution"
- Example: Roll two dice and find the probability that the sum of the points is 7

**Recommended solution strategy:**
- Classical profile: $P(A) = \frac{\text{Number of favorable situations}}{\text{Number of total situations}}$
- Conditional probability: $P(A|B) = \frac{P(AB)}{P(B)}$, Bayesian formula
- Independent event: $P(AB) = P(A) \cdot P(B)$
- Binomial distribution: $P(X=k) = C_n^k p^k (1-p)^{n-k}$
- Expectation: $E(X) = \sum x_i p_i$, Variance: $D(X) = E(X^2) - [E(X)]^2$

**Conditions that must be checked:**
- Whether events are mutually exclusive ($P(A+B) = P(A) + P(B)$)
- Whether the events are independent
- Is the division in the total probability formula complete?
- Is the sample space equal to possibility?
- Definition of measures in geometric concepts

**Common mistakes:**
- Misuse of the addition formula (not subtracting the probability of intersection)
- Confusion between conditional probability and unconditional probability
- Expected linearity conditions ignored
- Binomial distribution probability of success $p$ constant conditions ignored
- Calculation errors of each order moment

**Recommended verification method:**
- Whether the sum of probabilities equals 1
- Validation of expectation and variance formulas
- Verify small-scale problems with simple enumerations
- Different solutions get consistent results

**Output format:**
 ```
Probability type: [classical concept/conditional probability/geometric concept]
Sample space: [description]
Advantages: [Description and Count]
Probability: $P = [fraction or decimal]$
Expectation (if any): $E(X) = [value]$
```

**Whether to ask the user:** Only if the meaning of "random" or "equally possible" is unclear

---

## word_problem

**Identification Features:**
- Practical problems described in natural language require the establishment of mathematical models
- Keywords: Actual problem scenarios (trip, project, concentration, profit, age, etc.)
- Example: Two people A and B are traveling towards each other from A and B. The speed of A is 1.5 times that of B. They will meet after 3 hours. Find the speed of the two people.

**Recommended solution strategy:**
1. Read carefully and extract key information
2. Assume unknown numbers (clear physical meaning)
3. Series of equations/inequality based on equivalence relations
4. Solve mathematical models
5. Test the rationality of the solution (whether it is consistent with reality)

**Conditions that must be checked:**
- Implied conditions (speed $>0$ , age a positive integer, etc.)
- Is the unit unified?
- Is the physical meaning of the solution reasonable?
- Whether there are multiple solutions or the model is not unique

**Common mistakes:**
- Improper assumption of unknowns leads to complicated equations
- Ignore implicit conditions
- Units are not unified
- Rounding requirements in actual questions are ignored
- The relationship is incorrectly listed (e.g. speed = distance/time)

**Recommended verification method:**
- Substitute the solution into the original problem scenario to verify
- Reasonableness of estimates
- Dimensional analysis
- Re-model and solve using different methods of setting unknowns

**Output format:**
 ```
Problem analysis: [Extracted known quantities and unknown quantities]
Assume unknown number: [variable definition]
Modeling: [Equations/Inequalities]
Solution: [Calculation process]
Result: [Answer with units]
Actual plausibility test: [Verification]
```

**Whether to ask the user:** Yes, when the conditions are ambiguous or necessary information is missing

---

## limit

**Identification Features:**
- Involving sequence limits or function limits
- Keywords: "limit", "$\lim$", "tend to", "tendency", "convergence"
- Example: Find $\lim_{x \to 0} \frac{\sin x}{x}$

**Recommended solution strategy:**
- Substitution method (if it can be substituted directly and there is no infinitive)
- Infinitive type identification ($\frac{0}{0}, \frac{\infty}{\infty}, 0\cdot\infty, \infty-\infty, 1^\infty, 0^0, \infty^0$)
- Equivalent infinitesimal substitution: $\sin x \sim x, \tan x \sim x, \ln(1+x) \sim x, e^x-1 \sim x$ ( $x \to 0$ )
- Lópida's Law (Type $0/0$ or $\infty/\infty$)
- Important limits: $\lim_{x\to 0}\frac{\sin x}{x}=1$, $\lim_{x\to\infty}(1+\frac{1}{x})^x=e$
- Pinch theorem

**Conditions that must be checked:**
- Conditions of Lópida's law (the numerator and denominator are differentiable, the limit is $0/0$ or $\infty/\infty$ )
- Equivalent infinitesimal substitution is only used in multiplication and division (not directly used in addition and subtraction)
- Are the left and right limits equal?
- The domain of the function at the limit point

**Common mistakes:**
- Equivalent infinitesimals are used directly in addition and subtraction
- Used when the conditions of Lópida's Law are not met
- Ignore left and right limits
- Wrong conclusion that limit does not exist
- Improper selection of upper and lower bounds for the pinch theorem

**Recommended verification method:**
- Numerical approximation (substitute the approximate value for calculation)
-Taylor expanded verification
- The result of L'Block's law verifies the limit of $f'(x)/g'(x)$
- Construction verification of the pinching theorem

**Output format:**
 ```
Limit: $\lim_{x \to [value]} [expression]$
Type: [deterministic / infinitive $\frac{0}{0}$ / ...]
Method: [equivalent replacement/Lópida/pinch/...]
Result: [limit value]
Verification: [Numerical approximation or alternative method results]
```

**Whether to ask the user:** No

---

## differentiation

**Identification Features:**
- Involves derivation, tangent, rate of change
- Keywords: "derivative", "derivative", "$f'(x)$", "$\frac{dy}{dx}$", "tangent equation", "rate of change"
- Example: Find the derivative of $f(x) = x^3\ln x$

**Recommended solution strategy:**
- Memorize basic derivation formulas
- Four arithmetic operations: $(u \pm v)' = u' \pm v'$, $(uv)' = u'v + uv'$, $(\frac{u}{v})' = \frac{u'v-uv'}{v^2}$
- Chain Rule: $y = f(g(x)) \Rightarrow y' = f'(g(x)) \cdot g'(x)$
- Implicit function derivation
- Derivative of parametric equations: $\frac{dy}{dx} = \frac{dy/dt}{dx/dt}$
- Higher order derivatives

**Conditions that must be checked:**
- Whether the function is differentiable at the derivation point
- Chain rule inner function differentiability
- Theorem conditions for the existence of implicit functions
- The denominator of the derivative of a fraction is not zero.

**Common mistakes:**
- Missing chain rule (incomplete derivation of composite functions)
- The sign of the product derivative formula is wrong
- Implicit function derivation misses $\frac{dy}{dx}$ items
- Logarithmic derivation domain check missing
- Missing terms in the calculation of higher-order derivatives

**Recommended verification method:**
- Integral verification (the integral of the derivative is restored to the original function)
- Numerical derivation verification (differential approximation)
- Substitute verification for simple points
- Symmetry verification using derivation formulas

**Output format:**
 ```
Function: $f(x) = [expression]$
Derivative: $f'(x) = [expression]$
Method: [direct derivation/chain rule/implicit function derivation/...]
Key steps: [Main transformation process]
(Optional) Tangent equation: $y = f'(x_0)(x - x_0) + f(x_0)$
```

**Whether to ask the user:** Only if it is unclear which variable to derive the derivative from

---

## integration

**Identification Features:**
- Involving indefinite integrals, definite integrals, area, and volume
- Keywords: "integral", "$\int$", "original function", "area", "volume", "indefinite integral", "definite integral"
- Example: Calculate $\int_0^1 x e^x \,dx$

**Recommended solution strategy:**
- Memory of basic integral formulas
- Integral method with substitution of elements (first type/differentiation, second type/trigonometric substitution)
- Integration by parts method: $\int u\,dv = uv - \int v\,du$
- Integral of rational functions: partial fraction decomposition
- Trigonometric Rational Integration: Universal Formula
- Definite integral: Newton-Leibniz formula $\int_a^b f(x)dx = F(b) - F(a)$

**Conditions that must be checked:**
- Whether the integrand is continuous on the integration interval
- Convergence of anomalous integrals
- Corresponding transformation of upper and lower limits after substitution
- Selection strategy of $u$ and $dv$ in partial integration (LIATE principle)

**Common mistakes:**
- Forgot to change the upper and lower limits of the points after changing yuan
- Improper selection of the direction of partial integration leads to more complexity
- Missing items in partial fraction decomposition
- Abnormal integration does not test convergence
- Integration of absolute value functions ignores segmentation

**Recommended verification method:**
- Derivation to verify indefinite integral results
- Approximate verification of definite integrals by numerical integration
- Cross-validation between the substitution method and the original method
- Symmetry exploit verification

**Output format:**
 ```
Integral: $\int [expression] \,dx$ (or upper and lower limits of definite integral)
Method: [Substitution method/integration by parts/partial fractions/...]
Key steps: [Change setting / $u, dv$ selection / decomposition]
Original function: $F(x) = [expression] + C$
Definite integral value (if any): [value]
```

**Whether to ask the user:** Only when the point range is unclear

---

## multivariable_calculus

**Identification Features:**
- Partial derivatives, total differentials, and heavy integrals involving multivariate functions
- Keywords: "Partial derivative", "$\frac{\partial}{\partial x}$", "Total differential", "Double integral", "Triple integral", "Gradient"
- Example: Find the partial derivatives $\frac{\partial f}{\partial x}$ and $\frac{\partial f}{\partial y}$ of $f(x,y) = x^2y + e^{xy}$

**Recommended solution strategy:**
- Partial derivatives: When deriving the derivative of a certain variable, other variables are treated as constants
- Chain Rule: $\frac{\partial z}{\partial t} = \frac{\partial z}{\partial x}\frac{\partial x}{\partial t} + \frac{\partial z}{\partial y}\frac{\partial y}{\partial t}$
- Full differential: $dz = \frac{\partial f}{\partial x}dx + \frac{\partial f}{\partial y}dy$
- Directional derivatives and gradients: $\nabla f = (\frac{\partial f}{\partial x}, \frac{\partial f}{\partial y})$
- Double integral: select the order of integration, interchange rectangular coordinates and polar coordinates
- Triple integral: rectangular coordinates, cylindrical coordinates, spherical coordinates

**Conditions that must be checked:**
- Commutative conditions for mixed partial derivatives ($f_{xy} = f_{yx}$, when second-order partial derivatives are continuous)
- Correct description of the integration area for heavy integration
- Calculation of Jacobian (when changing elements)
- $r$ factor for polar/spherical coordinates

**Common mistakes:**
- Forget about treating other variables as constants when taking partial derivatives
- Wrong area description when double integral exchange order
- Polar coordinate substitution misses $r$ in $r\,dr\,d\theta$
- Jacobian calculation error
- Green's formula/Stokes' formula direction error

**Recommended verification method:**
- Verify $f_{xy} = f_{yx}$ (second-order partial derivative)
- Numerical integration to verify re-integration
- Substitution and direct calculation cross-validation
- Symmetry exploit verification

**Output format:**
 ```
Function: $f(x,y,\dots) = [expression]$
Partial derivatives: $\frac{\partial f}{\partial x} = [expression], \frac{\partial f}{\partial y} = [expression]$
(optional) gradient: $\nabla f = ([value], [value])$
(optional) reintegration value: [value]
Method: [Rectangular coordinates/polar coordinates/cylindrical coordinates/spherical coordinates]
```

**Whether to ask the user:** Only when the points area is unclear

---

## linear_algebra

**Identification Features:**
- Involving matrices, vectors, linear equations, determinants, and eigenvalues
- Keywords: "matrix", "determinant", "eigenvalue", "eigenvector", "rank", "linear correlation", "diagonalization"
- Example: Find the eigenvalues ​​and eigenvectors of matrix $A = \begin{pmatrix} 2 & 1 \\ 1 & 2 \end{pmatrix}$

**Recommended solution strategy:**
- Determinant calculation: expansion method, elementary transformation, special matrix formula
- Matrix operations: addition, multiplication, transpose, inverse matrix
- Eigenvalue: Solution $|A - \lambda I| = 0$
- Eigenvector: Solution $(A - \lambda I)\vec{x} = \vec{0}$
- Diagonalization: $A = PDP^{-1}$ (the columns of $P$ are eigenvectors and $D$ is the diagonal matrix)
- Calculation of rank: elementary transformation into row echelon form

**Conditions that must be checked:**
- Is matrix multiplication multiplicable (dimension matching)
- Condition for the existence of inverse matrix ($|A| \neq 0$)
- Diagonalization condition (whether there are $n$ linearly independent eigenvectors)
- A real symmetric matrix must be diagonalizable

**Common mistakes:**
- Matrix multiplication is not commutative ($AB \neq BA$)
- Wrong sign during determinant calculation
- Error in solving characteristic equation
- Improper setting of eigenvector free variables
- Calculation errors in the orthogonalization process

**Recommended verification method:**
- Verify $A\vec{v} = \lambda\vec{v}$ for each feature pair
- Verify $P^{-1}AP = D$
- Verify $A \cdot A^{-1} = I$
- Verification of the relationship between trace and eigenvalue sum

**Output format:**
 ```
matrix/vector: [representation]
Determinant (if any): $|A| = [value]$
Eigenvalues: $\lambda_1 = [value], \lambda_2 = [value], \dots$
Feature vector: $\vec{v}_1 = ([], \dots)^T, \dots$
Inverse matrix (if any): $A^{-1} = [matrix]$
Rank: $r(A) = [value]$
```

**Whether to ask the user:** No

---

## ordinary_differential_equation

**Identification Features:**
- Involves equations containing derivatives
- Keywords: "differential equation", "general solution", "particular solution", "initial conditions", " $y'$ ", " $\frac{dy}{dx}$ "
- Example: Solve differential equation $y' + 2xy = x$, satisfying $y(0) = 1$

**Recommended solution strategy:**
- Identify equation types: separable variables, first-order linear, homogeneous, Bernoulli, proper equation, etc.
- Detachable variable: $\frac{dy}{dx} = f(x)g(y) \Rightarrow \int \frac{dy}{g(y)} = \int f(x)dx$
- First-order linear: $y' + P(x)y = Q(x)$, integration factor $\mu = e^{\int P(x)dx}$
- Second-order linear with constant coefficients: characteristic equation $r^2 + pr + q = 0$
- Constant variation method
- Initial conditions determine the specific solution

**Conditions that must be checked:**
- $g(y) = 0$ Whether a strange solution is generated
- Is the integration factor defined?
- The solution form corresponding to the characteristic root type (real root/multiple root/complex root)
- Is the equation linear?

**Common mistakes:**
- Missing solution to $g(y) = 0$ when variables are separable
- Calculation error of integration factor
- The solution form of the characteristic equation is wrongly selected (real roots/multiple roots/complex roots)
- Error in judging linearly independent solutions
- Wrong setting of special solution form

**Recommended verification method:**
- Substitute the solution into the original equation to verify
- Verify that the general solution contains all linearly independent solutions
- Verify that the particular solution satisfies the initial conditions
- Approximate verification of numerical solutions

**Output format:**
 ```
Equation type: [separable variable/first-order linear/second-order constant coefficient/...]
General solution: $y = [expression] + C$
(optional) Special solution: $y = [expression]$
Solution method: [Integral factor/Characteristic equation/Constant variation method]
Steps: [Main transformation]
```

**Whether to ask the user:** Only if initial conditions are missing

---

## complex_analysis

**Identification Features:**
- Involving complex functions, residues, and circumferential integrals
- Keywords: "complex number", "complex function", "residue", "analysis", "$e^{iz}$", "circuit integral"
- Example: Calculate residue $\operatorname{Res}\left(\frac{e^z}{z^2}, 0\right)$

**Recommended solution strategy:**
- Determine whether the function is analytical (Cauchy-Riemann equation)
- Residue calculation: $\operatorname{Res}(f, z_0) = \frac{1}{(m-1)!}\lim_{z\to z_0}\frac{d^{m-1}}{dz^{m-1}}[(z-z_0)^m f(z)]$ ($m$ order pole)
-Block points: $\oint_C f(z)dz = 2\pi i \sum \operatorname{Res}(f, z_k)$
- Laurent Expand
-Use the Cauchy integral formula

**Conditions that must be checked:**
- Judgment of pole order
- Singularities contained within the enclosure
- Whether the function is analytic in the enclosure except for isolated singularities
- Processing of branch cutting

**Common mistakes:**
- Wrong judgment of pole order
- Improper use of the residue calculation formula
- Omission of singular points in the enclosure
- The direction of the enclosure and the relationship between symbols are reversed
- Laurent series expansion error

**Recommended verification method:**
- Comparison of direct integration and residue theorem results
- Cauchy integral formula verification
- Series expansion cross validation

**Output format:**
 ```
Function: $f(z) = [expression]$
Singularity: $z = [value]$ (type: [pole/nature singularity/removable singularity])
Residue: $\operatorname{Res}(f, z_0) = [value]$
(optional) perimeter integral value: [value]
```

**Whether to ask the user:** No

---

## real_analysis

**Identification Features:**
- Involves rigorous real-analytic proof of concept
- Keywords: "$\epsilon$ - $\delta$ definition", "consistent continuity", "consistent convergence", "Lebesgue", "measure", "completeness"
- Example: Prove $\lim_{x\to 2} x^2 = 4$ in $\epsilon$ - $\delta$ language

**Recommended solution strategy:**
- Understand and apply $\epsilon$ - $\delta$ ( $\epsilon$ - $N$ ) definitions
- Starting from $|f(x)-L|<\epsilon$ and working backward to $|x-a|<\delta$
- Utilize zooming techniques
- Real number completeness theorems such as the certainty principle and the monotonic bounded theorem
- Judgment of consistent continuity: If it is continuous on a closed interval, it is consistent and continuous.

**Conditions that must be checked:**
- Arbitrariness of $\epsilon$
- Dependency of $\delta$ on $\epsilon$
- Whether the domain is a closed interval
- Strict definition of function continuity

**Common mistakes:**
- $\delta$ is only related to $\epsilon$ and should not depend on $x$
- Excessive scaling causes $\delta$ to not meet the requirements
- Confusing uniform continuity with point-wise continuity
- The logical reasoning chain of the real number completeness theorem is broken
- Improper assumptions in proof by contradiction

**Recommended verification method:**
- Logical derivation for each step check
-Construct concrete $\epsilon$ value validation
- Counterexample test

**Output format:**
 ```
proposition: [statement]
Proof method: [$\epsilon$-$\delta$ / proof by contradiction / certainty / ...]
Proof: [Strict derivation process]
Conclusion: [The proposition is true/not true]
```

**Whether to ask the user:** Yes, you need to confirm the required strictness

---

## abstract_algebra

**Identification Features:**
- Involving the definition and properties of algebraic structures such as groups, rings, fields, etc.
- Keywords: "group", "ring", "domain", "homomorphism", "isomorphism", "subgroup", "normal subgroup", "ideal"
- Example: Prove that the subgroup $H$ of $G$ is a normal subgroup if and only if $\forall g \in G, gHg^{-1} = H$

**Recommended solution strategy:**
- Verify group axioms (closure, associativity, identity element, inverse element)
- Subgroup determination: $H \leq G \iff \forall a,b \in H, ab^{-1} \in H$
- Regular subgroup: $\forall g\in G, gH = Hg$ or $gHg^{-1} \subseteq H$
- Fundamental theorem of homomorphism: $G/\ker\phi \cong \operatorname{Im}\phi$
- Lagrange's theorem: The order of a subgroup divides the order of the group
- Ideal judgment of the ring

**Conditions that must be checked:**
- Whether the operation is closed
- order of group elements
- The difference between subgroups and regular subgroups
- Is homomorphic mapping well defined?

**Common mistakes:**
- Missing group axiom verification
- Confusion between normal subgroups and subgroups
- The normal subgroup condition is missing when constructing the quotient group
- Well-qualified neglect of homomorphic mapping definitions
- Misuse of the converse of Lagrange's theorem

**Recommended verification method:**
- Verify the axioms one by one
- Construct counterexamples to verify non-properties
- Test general conclusions with specific groups ($\mathbb{Z}_n, S_3$, etc.)
- Two-way verification of isomorphic mapping

**Output format:**
 ```
Algebraic structure: [group/ring/field/module]
Known: [given conditions]
Proof: [Property to be proved]
Proof: [logical deduction]
Key theorem: [name of theorem used]
```

**Whether to ask the user:** Yes, confirm the precise definition of the algebraic structure

---

## topology

**Identification Features:**
- Involving topological concepts such as open sets, closed sets, continuity, compactness, and connectivity
- Keywords: "open set", "closed set", "compact", "connected", "homeomorphism", "topological space", "Hausdorff"
- Example: Prove that the continuity of a compact space is compact

**Recommended solution strategy:**
- Understand the definition of topological space (open set axiom)
- Continuity: The original shape of an open set is an open set (or the original shape of a closed set is a closed set)
- Compactness: Any open cover has finite subcovers
- Connectivity: cannot be expressed as the union of two disjoint non-empty open sets
- Hausdorff space: any two points have disjoint open neighborhoods

**Conditions that must be checked:**
- Is the topology of the space clearly given?
- Is it a metric space induced topology?
- Is the mapping continuity defined correctly?
- Inheritance of subspace topology

**Common mistakes:**
- Confusing the properties of metric spaces and general topological spaces
- Omission of open coverage in tightness judgment
- Confusion between connectivity and road connectivity
- The image of a closed set under continuous mapping is not necessarily closed
- Confusion between compact spaces and bounded closed sets

**Recommended verification method:**
- Verify general theorems in specific topological spaces
- Construct counterexamples to verify non-properties
- Check the axioms and definitions one by one

**Output format:**
 ```
Space: $(X, \tau)$ / specific space
Property/proposition: [statement]
Proof idea: [Core strategy]
Proof: [strict derivation]
Counterexample (if any): [Explanation]
```

**Whether to ask the user:** Yes, confirm the topological space definition

---

## number_theory

**Identification Features:**
- Involving divisibility of integers, prime numbers, and congruence
- Keywords: "Divisibility", "Prime Numbers", "Congruence", "$\pmod{n}$", "Fermat's Little Theorem", "Euler's Theorem", "Chinese Remainder Theorem"
- Example: Prove that there is no largest prime number

**Recommended solution strategy:**
- Division with remainder: $a = bq + r$, $0 \leq r < |b|$
- Greatest common factor: Euclidean algorithm
- Congruence operations and properties
- Fermat's Little Theorem: $a^{p-1} \equiv 1 \pmod{p}$ ($p$ is a prime number, $p \nmid a$)
- Euler's Theorem: $a^{\varphi(n)} \equiv 1 \pmod{n}$ ( $\gcd(a,n)=1$ )
- Chinese Remainder Theorem to solve the system of congruence equations

**Conditions that must be checked:**
- Whether the modulus in modular operation is positive
- Whether $p$ in Fermat's Little Theorem is a prime number
- Euler's theorem $\gcd(a,n) = 1$
- In the Chinese Remainder Theorem, the modulus are pairwise prime

**Common mistakes:**
- Forgetting to take the modulus in the modulo operation during congruence operation
- Misuse when the conditions of Fermat’s Little Theorem are not met
- Modules are not mutually prime when using the Chinese Remainder Theorem
- Divisor confusion ($a \mid b$ vs $b \mid a$)
- Prime number determination ignores the specialness of $2$

**Recommended verification method:**
- Substitute specific numerical values ​​for verification
- Cross-solve congruence equations using different methods
- Inverse element verification ($a \cdot a^{-1} \equiv 1 \pmod{n}$)

**Output format:**
 ```
Question Type: [Divisibility/Congruence/Prime Numbers/Diophantine Equation]
Theorem reference: [Fermat's Little Theorem/Euler's Theorem/Chinese Remainder Theorem/...]
Solution/Proof: [Step]
Result: [numeric value or conclusion]
```

**Whether to ask the user:** No

---

## discrete_math

**Identification Features:**
- Involving graph theory, logic, set theory, Boolean algebra, relations
- Keywords: "graph", "vertex", "edge", "logic", "proposition", "set", "relation", "lattice", "Boolean algebra"
- Example: Prove that among any 6 people, there must be 3 people who know each other or do not know each other

**Recommended solution strategy:**
- Graph theory: handshake theorem, Euler path conditions, Euler formula for plane graphs, coloring
- Logic: truth table, logical equivalence, paradigm shift
- Set theory: Venn diagram, set operations, cardinality
- Pigeonhole principle
- Simplification of Boolean algebra (Karnaugh map)

**Conditions that must be checked:**
- Whether the graph has multiple edges/self-loops
- Definition of truth value of logical propositions
- Domain of set operations (complete set)
- The correspondence between pigeons and pigeon nests in the pigeon nest principle

**Common mistakes:**
- Degree calculation error for handshake theorem
- Hamiltonian graph/Eulerian graph condition confusion
- Missing steps in logical equivalent transformation
- The direction of the collection inclusion relationship is reversed
- Improper application of the pigeonhole principle

**Recommended verification method:**
- Small-scale enumeration
- Truth table to verify logical equivalence
- Test theorems with specific graph examples
- Counterexample construction

**Output format:**
 ```
Branch: [Graph Theory/Logic/Set Theory/Relationship]
proposition: [statement]
Method: [Handshake theorem/truth table/pigeon nest principle/...]
Proof/Solution: [Step]
Conclusion: [result]
```

**Whether to ask the user:** Only if the definition of the graph is ambiguous

---

## optimization

**Identification Features:**
- Involves finding the maximum or minimum value under constraints
- Keywords: "maximization", "minimization", "optimality", "constraints", "linear programming", "nonlinear programming"
- Example: Under the condition of $x+y \leq 10, x \geq 0, y \geq 0$, find the maximum value of $z = 3x + 2y$

**Recommended solution strategy:**
- Linear programming: simplex method or graphical method (2D)
- Equality constrained extreme values: Lagrange multiplier method
- Inequality constraints: KKT conditions
- Unconstrained extreme value: gradient is zero + Hessian matrix judgment
- Dynamic programming (multi-stage decision-making)

**Conditions that must be checked:**
- Whether the feasible region is non-empty
- Is linear programming bounded?
- Are the KKT conditions sufficient?
- Whether the constraints are linearly independent
- Convexity of the objective function

**Common mistakes:**
- The feasible region is incorrectly drawn or described incorrectly
- Forgot to check bounds and vertices
- Lagrange multiplier method solution error
- KKT condition missing
- Confusion between local optimal and global optimal

**Recommended verification method:**
- Two-dimensional problem drawing verification
- Substitute into feasible region boundary point test
- Dual problem cross-validation
- Sensitivity analysis

**Output format:**
 ```
Optimization type: [Linear programming/nonlinear programming/integer programming/dynamic programming]
Objective function: [expression]
Constraints: [Inequalities/Equations]
Method: [Simplex method/Lagrangian method/KKT/Graphic method]
Optimal solution: $(x^*, y^*) = ([value], [value])$
Optimal value: $z^* = [value]$
```

**Whether to ask the user:** Only if the constraint is unclear

---

## mathematical_modeling

**Identification Features:**
- Required to construct a mathematical model based on the description
- Keywords: "model building", "mathematical model", "modeling", open problems without ready-made formulas
- Example: Building a mathematical model of the spread of infectious diseases

**Recommended solution strategy:**
1. Understand the problem background and identify key variables
2. Make reasonable assumptions (simplifying reality)
3. Establish relationships between variables (differential equations, difference equations, probability models, etc.)
4. Determine parameters
5. Solve and analyze the model
6. Verify whether the model is reasonable

**Conditions that must be checked:**
- Are the assumptions reasonable and clearly stated?
- Are the dimensions consistent?
- Does the model have a solution?
-Whether the parameters have actual meaning
- Scope of application of the model

**Common mistakes:**
- Assumptions are oversimplified and make the model meaningless
- Key variables missing
- The causal relationship is reversed
- Dimensional consistency is not considered
- There is no basis for parameter values

**Recommended verification method:**
- Sensitivity analysis (the impact of small changes in parameters on the results)
- Extreme case testing
- Compare with actual data
- Dimensional analysis

**Output format:**
 ```
Problem Description: [Overview]
Assumptions: [List all assumptions]
Variable definition: [Meaning and unit of each variable]
model: [mathematical expression]
Solution: [Method]
Result analysis: [Model prediction]
Limitations: [Model limitations]
```

**Do you want to ask the user:** Yes, you need to confirm the modeling goals and the acceptable level of simplification

---

## proof

**Identification Features:**
- Ask to prove a certain mathematical proposition
- Keywords: "proof", "verification", "test", "prove or deny"
- Example: Prove that $\sqrt{2}$ is an irrational number

**Recommended solution strategy:**
- Determine the proof method: direct proof, proof by contradiction, mathematical induction, construction method, equivalent transformation
- Mathematical induction: verify that $n=1$ is established, assume that $n=k$ is established and conclude that $n=k+1$ is established
- Evidence by contradiction: Assume that the conclusion is not valid and derive contradictions
- Construction method: Construct specific objects that meet the conditions
- Analyze the structure of propositions and determine premises and conclusions

**Conditions that must be checked:**
- Are the prerequisites complete?
- Reasoning whether there is a basis for each step
- Whether the contradiction in proof by contradiction is indeed contradictory to what is known
- Whether the basic steps and induction steps of mathematical induction are complete
- Whether untested assumptions are implicitly used

**Common mistakes:**
- Circular argument (use conclusion to prove premise)
- The opposite of the hypothesis in proof by contradiction is incomplete (forget about edge cases)
- Mathematical induction omits basic steps
- Jumps in reasoning, missing intermediate steps
- Use of unproven theorems

**Recommended verification method:**
- Logic check for each step of reasoning
-Special value substitution verification conclusion
- Try to find counterexamples
- Prove it again in different ways

**Output format:**
 ```
proposition: [statement]
Proof method: [direct proof/contradiction/mathematical induction/construction method/...]
Hypothesis (such as proof by contradiction): [hypothesis by contradiction]
Proof: [Step-by-step derivation]
Conclusion: The proposition holds $\square$
```

**Whether to ask the user:** Only if the propositional statement is ambiguous

---

## counterexample

**Identification Features:**
- Ask for counterexamples to refute a certain proposition
- Keywords: "counterexample", "not established", "cite counterexamples", "whether it is established", "cite...refutation"
- Example: Is the proposition "If $f'(x_0)=0$ , then $x_0$ is the extreme point of $f(x)$" true? If this is not true, please give a counterexample.

**Recommended solution strategy:**
1. Analyze the conditions and conclusions of propositions
2. Find situations where the conditions are met but the conclusion is not true
3. Start looking for boundary conditions and degradation conditions
4. Choose the simplest possible counterexample
5. Verify that the counterexample satisfies the condition but does not satisfy the conclusion

**Conditions that must be checked:**
- Does the counterexample satisfy all the conditions of the proposition?
-Whether the counterexample actually violates the conclusion
- Whether the counterexample is within a reasonable definition domain
- Whether the counterexample is in its simplest form

**Common mistakes:**
- The counterexample does not satisfy the propositional condition
- Although the counterexample violates the conclusion, the definition domain does not match
- Counterexamples are too complex
- Misjudge "the proposition is true" as "the proposition is not true"
- Missing propositional implicit conditions

**Recommended verification method:**
- Check whether the conditions are met one by one
- Check whether the conclusions are violated one by one
- Whether simplifying counterexamples can maintain the properties of counterexamples

**Output format:**
 ```
proposition: [original proposition statement]
Analysis: [Why this proposition may not be true]
Counterexample: [Specific counterexample construction]
Verification conditions: [Check whether the conditions are met one by one]
Verification conclusion: [Explanation that the conclusion is not valid]
Minimal counterexample: [Can it be simpler]
```

**Whether to ask the user:** No

---

## solution_checking

**Identification Features:**
- Given a solution (possibly a student answer), ask to check if it is correct or incorrect
- Keywords: "is it right", "is it correct", "check", "correct", "are there any errors", "this solution"
- Example: Check whether the following solution is correct or incorrect: solve $x^2=4$ to get $x=2$

**Recommended solution strategy:**
1. Solve the problem independently again
2. Compare the given solution line by line with the standard solution.
3. Check every step of logical derivation
4. Verify final results
5. Classification error types (calculation errors, logical errors, conceptual errors, omissions)

**Conditions that must be checked:**
- Is the final result correct?
- Are there any logical jumps in the derivation process?
- Whether the domain/constraint conditions are satisfied
- Are there any missing solutions?
- Is the calculation process correct?

**Common mistakes (corrector errors):**
- Only look at the results and not the process
- Equivalent solutions (different forms) are judged as errors
- Ignore legitimate alternative solutions
- The final step error ignores the previous correct derivation

**Recommended verification method:**
- Substitute the final result of verification
- Get the answer to the same question in different ways
- Check the equivalence of each transformation step
- Estimating plausibility of numerical results

**Output format:**
 ```
Question: [original question]
Given solution: [Solution to be checked]
Independent solution result: [Correct answer]
Judgment: [Correct/Partially Correct/Incorrect]
Error location: [Error in step X, specific error description]
Error type: [Calculation error/Logical error/Conceptual error/Omission/Inappropriate presentation]
Correction suggestions: [How to correct it]
```

**Whether to question the user:** Only if the answer is unclear or the handwriting is difficult to read

---

## problem_generation

**Identification Features:**
- Ask to generate new math problems
- Keywords: "give a question", "generate a question", "help me give a question", "make up a question", "design a question"
- Example: Generate an application question of the maximum value of a quadratic function, with a difficulty level of College Entrance Examination Medium

**Recommended solution strategy:**
1. Determine the topic and knowledge points of the question
2. Design the question structure and known conditions
3. Construct the numerical value (make sure the numerical value is reasonable and the calculation is simple)
4. Solve it yourself first to verify the solvability
5. Provide reference answers

**Conditions that must be checked:**
- Are the question conditions complete and self-consistent?
- Whether there is a solution and the solution is unique (if unique)
- Are the values ​​reasonable (no strange decimals will appear)
- Whether the difficulty meets the requirements
- There is no contradiction between the conditions

**Common mistakes:**
- Insufficient conditions lead to multiple or no solutions
- Contradictory conditions
- Unreasonable numerical construction leads to complicated calculations
- Beyond the specified difficulty range
- There is ambiguity in the title description

**Recommended verification method:**
- Solve generated questions independently
- Check for unexpected solutions
- Verify the rationality of the values
- Estimated trial time

**Output format:**
 ```
Knowledge points: [Knowledge points covered]
Title: [Full title description]
Difficulty: [Easy/Medium/Hard]
Reference answer: [Complete solution process]
Answer: [final result]
Examination points: [What is the main examination of the question]
```

**Whether to ask the user:** Yes, confirm the difficulty, knowledge point range, and question type preference

---

## research_level_problem

**Identification Features:**
- Very high level of difficulty, possibly close to competition finals, mathematical studies or open questions
- Keywords: References involving Fermat’s Last Theorem and Riemann Hypothesis, or that are obviously beyond the standard curriculum
- Example: Prove that the non-trivial zeros of Riemann's $\zeta$ function are located on $\operatorname{Re}(s) = 1/2$

**Recommended solution strategy:**
- First determine whether the problem is known to have been solved
- If the result is known, provide a summary of the result and relevant literature
- If it’s an open question, tell it honestly
- Provide possible ideas or related sub-results
- Citing authoritative sources

**Conditions that must be checked:**
- Is the problem equivalent to a known open problem?
- Is there any known partial progress on the issue?
- Whether the user understands the difficulty of the question
- Whether it is necessary to downgrade to approximate or special circumstances

**Common mistakes:**
- Provide error proofs for open questions
- Underestimating the difficulty of the problem
- Ignore known progress
- Use premature reasoning

**Recommended verification method:**
- Review the literature to verify the conclusion
- Check the proof for holes
- Compare with known results

**Output format:**
 ```
Problem Assessment: [Known Result/Partially Solved/Open Issue]
Known progress: [Related theorems and partial results]
References: [Key Citation]
Suggestions: [Possible ideas or simplification directions]
Note: [Question Difficulty Description]
```

**Whether to ask the user:** Yes, confirm the processing method and depth expected by the user

---

## ambiguous_or_incomplete

**Identification Features:**
- Missing conditions, ambiguous expressions, and insufficient information
- Keywords: vague reference, undefined symbols, contradictory conditions
- Example: "Find the maximum value of this function" (no function given)

**Recommended solution strategy:**
- Point out missing/ambiguous specific content
- Give possible explanations under reasonable assumptions
- Request additional information from the user
- Do not answer without permission before the user replies

**Conditions that must be checked:**
- Are all symbols in the question defined?
- Is the numerical range clear?
- Is the hypothesis self-consistent?
- Are there multiple reasonable explanations?

**Common mistakes:**
- Make up the conditions on your own and give wrong answers
- Ignore the ambiguity and answer directly
- Not all ambiguities are listed
- Added unreasonable assumptions

**Recommended verification method:**
- List all possible explanations
- Check whether the answers under each explanation are consistent

**Output format:**
 ```
Question: [Original user input]
Ambiguities/missing points: [itemize]
Possible explanation:
Explanation 1: [Description] → In this explanation the answer is [Value]
Explanation 2: [Description] → In this explanation the answer is [Value]
Confirmation required: [Specific content needs to be clarified by the user]
```

**Whether to ask the user:** Yes, must ask

---

## out_of_scope

**Identification Features:**
- Input is not a math problem
- Involving non-mathematical subjects, daily conversations, and content that cannot be classified
- Examples: "How is the weather today", "Write an email for me"

**Recommended solution strategy:**
- Polite description of Math.skill’s scope of responsibilities
- If you know the answer, please give a brief reply
- Recommend users to use other more suitable tools

**Conditions that must be checked:**
- Does it contain any mathematical content?
- Can it be reformulated as a mathematical problem
- Whether the user is interested in testing system boundaries

**Common mistakes:**
- Forcing non-mathematical problems to be treated as mathematical problems
- Misjudgment of edge problems (such as mathematical derivation in physics)

**Recommended verification method:**
- Confirm that the input does not contain processable mathematical content

**Output format:**
 ```
Judgment: The input does not belong to the category of mathematical problems
Specific reason: [Explanation]
Recommendation: [Recommend user to use other tools or rephrase if applicable]
```

**Whether to ask the user:** Yes, it is recommended to rephrase or confirm the intention

---

Last updated: 2026-05-30
