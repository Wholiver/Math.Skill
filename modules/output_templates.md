# Math.skill Output Templates

The following defines 6 output templates, each including: applicable scenarios, standard structure, complete examples, and special considerations.

---

## Template A: Standard Solution

### When to use
- Answers to general math problems
- Standard question types including calculation, derivation, and application of theorems
- This template is used by default when the user does not specify a special output format.

### Standard structure

 ```markdown
## Question meaning analysis
[Reformulate the problem in mathematical language and clarify the known conditions and solution goals]

## Method selection
[Explain the rationale for choosing this method and compare it with other possible methods]

## Problem solving process
[Full step-by-step derivation]

## Check calculation
[Substitution Verification/Inverse Operation Verification/Numerical Approximation Verification]

## Final answer
[Clearly mark the format of the final result]

## Easy to make mistakes
[List common mistakes and how to avoid them]
```

### Complete example

 ```markdown
## Question meaning analysis
Given the function f(x) = x³ - 3x² + 2, find the maximum and minimum values ​​of f on [-1, 3].

## Method selection
The optimal value problem of a one-variable closed interval continuous function: first find the stationary point, and then compare it with the endpoints.
The derivation method was chosen because f is differentiable everywhere on [-1,3] and the critical point can be found by f'(x) = 0.

## Problem solving process
**Step 1**: Derivative
f'(x) = 3x² - 6x = 3x(x - 2)

**Step 2**: Find the stationary point
Let f'(x) = 0, solve for x = 0 or x = 2
Both stationary points are in the interval [-1, 3].

**Step 3**: Calculate the function value
f(-1) = (-1)³ - 3(-1)² + 2 = -1 - 3 + 2 = -2
f(0) = 0³ - 3·0² + 2 = 2
f(2) = 2³ - 3·2² + 2 = 8 - 12 + 2 = -2
f(3) = 3³ - 3·3² + 2 = 27 - 27 + 2 = 2

**Step 4**: Compare to get the best value
maximum value = max{-2, 2, -2, 2} = 2
Minimum value = min{-2, 2, -2, 2} = -2

## Check calculation
- f(-1) = -2：(-1)³ = -1, -3(-1)² = -3, -1-3+2 = -2 ✓
- f(0) = 2：0-0+2 = 2 ✓
- f(2) = -2：8-12+2 = -2 ✓
- f(3) = 2：27-27+2 = 2 ✓
- Endpoints -1 and 3 checked
- At the stationary point, f''(0) = -6 < 0 (maximum point), f''(2) = 6 > 0 (minimum point), consistent with the calculation results

## Final answer
The maximum value is 2, taken at x = 0 and x = 3.
The minimum value is -2, taken at x = -1 and x = 2.

## Easy to make mistakes
1. Forget to check the endpoint value - the maximum value of a closed interval may be taken at the endpoint
2. Missing out that f(3) is equal to f(0) leads to the belief that the maximum value can only be obtained at x=0
3. The solution of f'(x) = 0 is directly regarded as the maximum point without comparing the size.
```

### Special Notes
- In the "Analysis of Question Meaning" part, avoid directly copying the user's original words, and should show your understanding of the question.
- The "Verification" section contains at least one verification method
- "Error prone points" should be based on real common mistakes, not fictional ones

---

## Template B: Answer Only

### When to use
- User explicitly asked for "just the answer"
- Users say "give results directly" and "no process required"
- The user has already shown the complete idea in the conversation and only needs final confirmation

### Standard structure

 ```markdown
The answer is: [formula or numerical value]

Simple verification: [One line verification]
```

### Complete example

 ```markdown
The answer is: ∬_D (x² + y²) dxdy = 8π/3

Simple calculation: using polar coordinates, ∫₀²∫₀²ᵖⁱ r²·r dθ dr = 2π·[r⁴/4]₀² = 2π·4 = 8π ✓
```

### Special Notes
- The verification row must exist to ensure the credibility of the answer
- If the problem has multiple solutions, all must be listed
- If it is an approximate value, please indicate the accuracy

---

## Template C: Proof

### When to use
- The user asks to prove a certain proposition
- "Please prove...", "Please prove..."
- Mathematical arguments that need to show logical chains of derivation

### Standard structure

 ```markdown
## Proposition
[precise statement of the proposition being proved]

## Proof idea
[The overall logical structure of the proof, key lemmas, and core techniques]

## prove
[Complete logical deduction, including all intermediate steps and references]

## Counterexample checking and edge cases
[Check various boundary cases of the proposition and verify whether there are counterexamples]

## in conclusion
[Summary of completion of proposition proof]
```

### Complete example

 ```markdown
## Proposition
For any positive integer n, prove that: n³ - n is divisible by 6.

## Proof idea
The core is to factor n³ - n = n(n-1)(n+1), noting that this is the product of three consecutive integers.
One of the three consecutive integers must be a multiple of 2, and one must be a multiple of 3.
Therefore the product must have factors 2 × 3 = 6.

## prove
**Step 1**: Factorization
n³ - n = n(n² - 1) = n(n-1)(n+1)

**Step 2**: Properties of three consecutive integers
n-1, n, n+1 are three consecutive integers, therefore:
- There is at least one even number (divisible by 2)
- Exactly one of them is divisible by 3

**Step 3**: Combining Factors
Since the product contains both factors 2 and 3, and 2 and 3 are relatively prime,
So n³ - n contains the factor 6 = 2 × 3.

That is: 6 | (n³ - n), true for all n ∈ ℕ.

## Counterexample checking and edge cases
- n = 1: 1³ - 1 = 0, 0 is divisible by 6 ✓
- n = 2: 8 - 2 = 6, divisible by 6 ✓
- n = 3: 27 - 3 = 24 = 6×4, divisible by 6 ✓
- n = 0: 0-0=0 is divisible by 6 if n=0 is considered to be in the range of positive integers (not included here)

Unbounded counterexamples.

## in conclusion
Proof of the proposition: For any positive integer n, 6 | (n³ - n). ∎
```

### Special Notes
- The proposition statement must be precise and the quantification words must be complete
- The "Counterexample Checking and Bounds" section must be present even if there is no counterexample
- Use an appropriate closing tag (such as ∎ or Q.E.D.)

---

## Template D: Solution Checking

### When to use
- Users provided their own answers and asked to check if they are correct
- "Am I right?"
- "See what's wrong"
- Errors need to be pointed out and corrected

### Standard structure

 ```markdown
## Check conclusion
[Overall judgment: correct / incorrect / partially correct]

## Problem location
[If there is an error, identify the exact step and type of error]
[If correct, confirm the rationality of each step]

## Correct approach
[Show correct derivation (if it is a partial step correction, only correct the wrong part)]

## Check calculation
[Independent verification of correct answer]

## Final answer
[If it is wrong, give the correct answer; if it is correct, confirm the user's answer]
```

### Complete example

 ```markdown
## Check conclusion
Your answer is wrong. The first two steps are correct, but in step 3 a critical error occurs.

## Problem location
**Step 3**: You write √(x²) = x
This is wrong. The correct relationship is √(x²) = |x|.

Because the square root function returns a nonnegative value, x may be negative.

In this problem, the integration interval is [-2, 1], and x can take negative values ​​within this interval,
So √(x²) cannot simply be equal to x.

## Correct approach
**Correction from step 3**:
Split the integration interval into [-2, 0] and [0, 1]:

On [-2, 0]: √(x²) = |x| = -x (since x ≤ 0)
On [0, 1]: √(x²) = |x| = x (since x ≥ 0)

∫_{-2}^{1} |x| dx = ∫_{-2}^{0} (-x) dx + ∫_{0}^{1} x dx
= [-x²/2]_{-2}^{0} + [x²/2]_{0}^{1}
= (0 - (-4/2)) + (1/2 - 0)
= 2 + 0.5
= 2.5

## Check calculation
Geometric verification: The area of ​​|x| under [-2,0] is the area of ​​the triangle = 2×2/2 = 2
The area of ​​|x| under [0,1] is the area of ​​the triangle = 1×1/2 = 0.5
Total area = 2 + 0.5 = 2.5 ✓

## Final answer
The correct answer is 2.5, not the 1.5 you got.

Your mistake mainly lies in ignoring the non-negativity convention of the square root function.
```

### Special Notes
- The error location should be specific to the line number or step number
- Be constructive when pointing out mistakes and don't say things like "You're so stupid"
- If the answer is completely correct, just confirm and give the verification

---

## Template E: Higher Math Solutions (Higher Math)

### When to use
- Questions require the use of college level or above mathematical tools
- Involving advanced course content such as real analysis, abstract algebra, topology, etc.
- Users explicitly request advanced mathematical methods

### Standard structure

 ```markdown
## Question type
[Field classification: real analysis / abstract algebra / topology / advanced probability...]

## Conditions and domains
[Formal expression of all conditions in the problem, detailed definition of the domain]

## Theorems used and applicable conditions
[Listed theorem names, statements, and verification that the conditions in this question are met]

## Derivation
[Strict derivation process based on selected theorem]

## Calculation and consistency check
[Cross-validate results in multiple ways to check consistency with other known conclusions]

## Final conclusion
[Formal statement of conclusion]
```

### Complete example

 ```markdown
## Question type
Real analysis - the relationship between uniform convergence and point-wise convergence

## Conditions and domains
Let the function sequence f_n(x) = x^n and the domain x ∈ [0, 1].
Discuss whether f_n converges uniformly on [0, 1].

## Theorems used and applicable conditions
**Judgment method adopted**: The necessary and sufficient condition for consistent convergence is sup|f_n(x) - f(x)| → 0
where f(x) is the pointwise limit.

**Pointwise Limit**:
For any x ∈ [0, 1):
  lim_{n→∞} x^n = 0
For x = 1:
  lim_{n→∞} 1^n = 1

So f(x) = { 0, x ∈ [0, 1); 1, x = 1 }

## Derivation
Compute the exact bound:
For any n, sup_{x∈[0,1]} |f_n(x) - f(x)|

When x ∈ [0, 1): |f_n(x) - 0| = x^n
When x = 1: |f_n(1) - 1| = |1 - 1| = 0

On [0, 1), the supremum of x^n = 1 (when x → 1⁻),
Therefore sup |f_n(x) - f(x)| = 1

Since lim_{n→∞} 1 = 1 ≠ 0,
According to necessary and sufficient conditions, f_n **inconsistently converges** on [0,1].

## Calculation and consistency check
1. **Continuity Test**: Every f_n(x) = x^n is continuous on [0,1].
If there is uniform convergence, the limit function should also be continuous.
But f(x) is discontinuous at x=1 (the limit is 0 and the function value is 1).
This inversely confirms inconsistent convergence. ——The conclusion is self-consistent ✓

2. **Uniform convergence on compact sets**: If the domain is reduced to [0, c] (c < 1),
Then sup x^n = c^n → 0 (n → ∞), which converges uniformly.
This is completely consistent with the theory ✓

## Final conclusion
The sequence of functions f_n(x) = x^n converges pointwise but inconsistently on [0, 1].
The limit function has a jump discontinuity at x = 1, breaking continuity.
```

### Special Notes
- The conditional verification of the theorem must be listed in full one by one and cannot be omitted.
- Concepts need to be distinguished (such as point state and consistent convergence, compactness and column compaction)
- Consistency checking is an indispensable part of advanced mathematics solutions

---

## Template F: Research/Open Problem (Research/Open Problem)

### When to use
- The issue is confirmed as a known open issue
- Question is research level and has no known standard answer
- When the user’s mathematical level may not be sufficient to judge the difficulty of the problem, an honest explanation is required

### Standard structure

 ```markdown
## Preliminary judgment
[The status of this problem in the current mathematical knowledge system]

## Known information and possible related theories
[Known conclusions, theorems and theoretical frameworks related to this problem]

## Search or check results
[Search the summary of results for this issue and see if similar discussions and related literature are found]

## Analysis from first principles
[Analysis starting from basic definitions, showing rigorous derivations that can be made]

## Some verified conclusions
[A conclusion that is truly verifiable under specific conditions]

## Counterexample search
[Results of numerical search, found/not found counterexamples]

## Current obstacle
[Critical steps that hinder complete proofs, why existing tools are insufficient]

## Directions that can be continued
[Suggested next research directions]

## Conclusion status
[Specify the current status of this issue: Open/Partially Resolved/Resolved under certain conditions]
```

### Complete example

 ```markdown
## Preliminary judgment
This problem is essentially equivalent to **Collatz Conjecture (3n+1 problem)**.
This question has not been proven or disproven since it was raised in 1937.
At present, it has been numerically verified to about 2⁶⁸, and no counterexamples have been found.

## Known information and possible related theories
- Review of "The Ultimate Challenge: The 3x+1 Problem" by Jeffery Lagarias (2010)
- Terence Tao (2019) proved that the logarithmic density tends to 0
- It has been concluded that almost all numbers are ultimately smaller than the original number after Collatz iteration

## Search or check results
Find related discussions on MathOverflow (highly praised answers by Tao, etc.):
Confirm that the special case raised in this question is within the scope of Collatz's conjecture,
No complete proof is known.

## Analysis from first principles
For the specific form you propose, an equivalent mapping to standard Collatz iterations can be established:
Assume T(n) = n/2 (n is even), 3n+1 (n is odd), then...
[Specific equivalent derivation]

This shows that both your question and Collatz's conjecture are either true or false at the same time.

## Some verified conclusions
For numbers in the range n ≤ 10⁶:
- After finite step iteration, enter the 4→2→1 loop
- No other loops found with loop length > 10⁴
This result can be reproduced using Python verification (takes ~5 seconds).

## Counterexample search
No counterexamples were found in the range n ∈ [1, 10⁶].
This result is consistent with known large-scale numerical verification results.

## Current obstacle
To complete the general proof, one needs to deal with the problem of arbitrarily long orbits in Collatz iterations,
There are currently no known mathematical tools that can completely solve this problem.

## Directions that can be continued
1. Study the statistical behavior of the problem (as done by Tao)
2. Explore connections to p-radical number analysis or other number theory tools
3. Study the enumeration properties of specific subsets
4. If you have a new perspective on this issue, it is recommended to check out Lagarias’ review to understand the known progress

## Conclusion status
**There is currently no complete proof of this problem recognized by the mathematical community. **
The above analysis is a compilation of existing knowledge and numerical experiments of special cases.
It does not represent a proof of the original question.
```

### Special Notes
- Must be clearly marked "A complete certificate does not currently exist"
- Distinguish between "verified facts" and "speculations"
- Follow-up suggestions provided to users should be specific and actionable
- When citing documents, there must be specific and verifiable sources (no fictitious ones)

---

## Template G: Research-Level Deep Analysis

### When to use
- Users explicitly ask research-level mathematical questions
- Questions involving the intersection of multiple branches of mathematics
- Need to demonstrate in-depth theoretical analysis and multiple possible solution paths
- Users have a graduate degree or above in mathematics background

### Standard structure

 ```markdown
## Problem classification and positioning
[The mathematical field to which the problem belongs, and its relationship to known problems]

## Analysis of core difficulties
[What is the essential difficulty of the problem and why the standard method fails]

## Related theoretical framework
[In-depth theories and tools that may be needed]

## Summary of known results
[The closest known theorem and conclusion to the problem]

## Try path one: [method name]
[Detailed derivation of the first solution]
### Progress
[How far can this approach go]
### Obstacles
[Specific difficulties encountered]

## Try path two: [method name]
[Detailed derivation of the second solution idea]
### Progress
### Obstacles

## Try path three: [method name]
[Detailed derivation of the third solution idea]
### Progress
### Obstacles

## Some results and lemmas
[Intermediate results that can be rigorously proven]

## Numerical/symbolic calculation verification
[Results of computer-aided verification]

## Possible breakthrough direction
[Based on the above analysis, the most promising research direction]

## Open conclusion
[Be honest about the limitations of the current analysis]
```

### Complete example

 ```markdown
## Problem classification and positioning
**Field**: Analytic Number Theory × Algebraic Geometry
**Problem type**: Association of zero point distribution of L-functions with arithmetic objects
**Correlation Conjecture**: Generalized Riemann hypothesis, Birch and Swinnerton-Dyer conjecture

## Analysis of core difficulties
1. **Existence of analytic continuation**: The analytic continuation of this L-function has not been proven yet
2. **Unknown functional equation**: The lack of functional equation makes zero-point distribution analysis extremely difficult
3. **Arithmetic Information Encoding**: The relationship between L-function coefficients and elliptic curve rank is unclear

## Related theoretical framework
- **Modular form theory**: If the L-function comes from modular form, modularity theorem can be used
- **Iwasawa Theory**: Study of the properties of p-radical L-functions
- **Trace formula**: Arthur-Selberg trace formula may provide spectral information

## Summary of known results
- **Nearest Theorem**: Wiles (1995) proved the modularity of semi-stable elliptic curves
- **Partial results**: Kolyvagin (1988) proved the BSD conjecture for the case of rank 0 or 1
- **Numerical evidence**: Cremona database verified for conductor < 500000

## Try path one: improve modularity
An attempt is made to relate this elliptic curve to a modular form via the known modularity promotion theorem.

### Progress
For a prime p of good reduction, the local factors can be calculated...

### Obstacles
The bad reduction at p = 2, 3 is of unknown type and the existing lifting theorem cannot be applied.

## Try path two: p-advanced method
Construct p-adic L-functions and study their zeros.

### Progress
The p-adic interpolation formula can be obtained using the Klingen-Stackelberg construction...

### Obstacles
The corresponding relationship between the non-trivial zeros of the p-radical L-function and the original L-function is not clear.

## Try path three: average results
Consider a family of similar L-functions and study the statistical properties.

### Progress
It can be shown that the zero-point density estimate in the mean sense...

### Obstacles
The properties of individual L-functions cannot be deduced from the average results.

## Some results and lemmas
**Lemma 1**: In the region Re(s) > 3/2, the L-function absolutely converges.
**Lemma 2**: If there is a functional equation, then the critical line is Re(s) = 1.
**Proposition**: For 90% of primes p, the local factors satisfy the expected bounds.

## Numerical/symbolic calculation verification
Use SageMath to calculate the first 1000 Dirichlet coefficients:
- The coefficient growth is consistent with the Ramanujan-Petersson conjecture
- The first 100 non-trivial zeros are all on the critical line (accuracy 10⁻¹⁰)

## Possible breakthrough direction
1. **Determine bad reduction type**: Calculate discriminant and conductor
2. **Find function equation**: Guess the form of function equation through numerical fitting
3. **Application of converse theorem**: Verify sufficient analytic properties to derive modularity

## Open conclusion
**Current Status**: A complete solution of this problem is beyond the scope of known mathematical tools.
The above analysis illustrates a variety of possible research paths, each of which presents substantial obstacles.
It is recommended to decompose this problem into several tractable sub-problems and solve them one by one.
```

### Special Notes
- It is necessary to clearly distinguish between the three assertion strengths of "proven", "speculation" and "numerical evidence"
- The cited theorem must state the conditions accurately and cannot be blurred
- Do not provide false "answers" to open questions
- Proposed research directions should be specific and feasible
- If calculations are involved, the tools and precision used should be stated

---

## Template selection decision tree

 ```
received a math question
│
├─ User specified template → Use specified template
│
├─ No template specified ↓
│  │
│ ├─ "Just the answer" → Template B: Only the answer
│ ├─ "Help me see if I'm right" → Template D: Answer Check
│ ├─ "Proof..." → Template C: Proof
│ ├─ Known Open Issues/General Research Level → Template F: Research/Open
│ ├─ In-depth research-level problem (multi-branch crossover) → Template G: Research-level in-depth analysis
│ ├─ Advanced Mathematics Field → Template E: Advanced Mathematics
│ └─ Other situations → Template A: Standard answer (default)
```

---

## Common specifications across templates

1. **Mathematical notation**: Use standard LaTeX syntax ($...$ inline, $$...$$ independent line)
2. **Format Consistency**: The numbering, indentation, and marking methods within the same template must be consistent
3. **Language**: Simplified Chinese is used, and professional terms are used in Chinese or English depending on the expression that the reader may be more familiar with.
4. **Check Calculation**: All templates must include a verification link (Template B exists in the form of "Simple Calculation")
5. **Answer Marking**: The final answer must be clearly marked for easy location.
6. **Citation Standards**: When citing a theorem, the name of the theorem must be indicated, and when citing external sources, the source must be indicated.
