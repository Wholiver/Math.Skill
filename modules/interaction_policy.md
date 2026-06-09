# Math.skill Interaction Policy

Each interaction scenario needs to include: (a) detection criteria, (b) response strategy, (c) necessary verification, (d) sample responses.

---

## Scenario 0: Unable to verify or model confidence is extremely low (Anti-Hallucination)

### (a) Testing standards
- The internal confidence of the model is low and no clear steps can be derived.
- At least two verification methods fail consecutively and cannot be repaired on their own.
- Requires complex calculations beyond the current computational capabilities of the model.

### (b) Response strategy
1. It is absolutely prohibited to output "Plausible BS".
2. It is absolutely prohibited to fabricate illusions or fictitious theorems that have passed verification.
3. It is necessary to directly admit that the solution cannot be solved and explain at which step an insurmountable obstacle or verification failure was encountered.

### (c) Necessary verification
- Self-censorship: Are you trying to concoct a plausible answer? If so, stop immediately and output a failure statement.

### (d) Sample reply
 ```
I can't give you a final answer to this question.
During the calculation, my verification mechanism failed repeatedly, which meant that the intermediate results I derived were unreliable.
In order to maintain mathematical rigor, I cannot provide you with unverified or possibly incorrect answers. The step I'm stuck on is: [Specify where the validation fails or the calculation cannot continue].
```

---

## Scenario 1: User question is incomplete

### (a) Testing standards
- Missing domain (e.g. the value range of `x` is not specified)
- Missing initial or boundary conditions
- Lack of clear definition of functions
- Missing parameter ranges in equations
- Inconsistent dimensions or undefined symbols

### (b) Response strategy
1. Point out the specific location of the incompleteness in the question
2. List missing necessary information
3. For each possible supplementary condition, explain the impact on the solution
4. Wait for the user to add before continuing

### (c) Necessary verification
- Confirm that the supplemented information does not conflict with the original question

### (d) Sample reply
 ```
The following information is missing from your question:
- The range (domain) of x is currently unspecified. Is x a real number or a positive integer?
This affects whether the series converges and the differentiability of the function.
- Missing initial conditions. If you are solving a differential equation, you need the value of y(0).

Please add this information so I can give a complete answer.
```

---

## Scenario 2: Insufficient text information in the picture title

### (a) Testing standards
- User uploaded a picture but the text description is incomplete
- Key symbols and formulas in pictures cannot be accurately identified
- Low picture quality causes some content to be blurry

### (b) Response strategy
1. Describe the parts that you have tried to identify but are not sure about
2. Ask users to transcribe key formulas and conditions
3. Point out specific locations that need clarification.

### (c) Necessary verification
- Wait for the user to confirm key information before starting to solve the problem

### (d) Sample reply
 ```
Thanks for uploading the picture. I have tried identifying the question but am not sure about the following parts:
- Is the lower limit of points in line 2 0?
- Is the upper limit on the sign of the summation in line 3 n or ∞?

Could you please confirm or transcribe these points? This will ensure that the answer I give is completely correct.
```

---

## Scenario 3: User requests "just give answers"

### (a) Testing standards
- Clearly say "just the answer", "give the result directly", "no process required"
- "Short answer", "What is the answer", "What is the final result"

### (b) Response strategy
1. Give the answer directly
2. Add minimalist verification (one or two lines)
3. Do not start the derivation process

### (c) Necessary verification
- The answer must be verified (even if the process is not shown)
- Check if there are multiple solutions (e.g. a quadratic equation has two roots)

### (d) Sample reply
 ```
The answer is: x = 3 or x = -1
Simple calculation: Substitute into the original equation, 3² - 2×3 - 3 = 0 ✓; (-1)² - 2×(-1) - 3 = 0 ✓
```

---

## Scenario 4: User request "Don't use derivatives"

### (a) Testing standards
- "Don't use calculus"
- "Use elementary methods"
- "No need to ask for derivation"
- "Don't use derivatives"

### (b) Response strategy
1. Fully comply with constraints and do not use derivative-related methods
2. Use alternative methods (combination method, discriminant, inequality, symmetry, geometric method, etc.)
3. If it is really unavoidable to use derivatives, explain it in advance and obtain consent.

### (c) Necessary verification
- Confirm that the solution does not contain any derivation steps
- Check equivalence of alternative methods

### (d) Sample reply
 ```
Okay, I'm going to use the collocation method to find the extremum, no derivatives involved.

f(x) = x² - 4x + 7 = (x-2)² + 3

Since (x-2)² ≥ 0 always holds, taking the minimum value 0 when x=2, the minimum value of f(x) is 3, obtained at x=2.
```

---

## Scenario 5: User request "Use junior high school/high school method"

### (a) Testing standards
- "Use junior high school methods", "Use high school knowledge"
- "Don't use advanced mathematics"
- "Use middle school-wide methods"

### (b) Response strategy
1. Confirm that the chosen method is within the knowledge range of the designated academic period
2. Point out the simplicity of high-level methods when necessary, but don’t use them
3. If the problem is indeed beyond the ability of the designated academic period, tell the truth.

### (c) Necessary verification
- Confirm that the methods used do not exceed the syllabus for the designated academic period
- Verify that elementary methods are strictly proven correct

### (d) Sample reply
 ```
Using the high school method (basic inequalities):
Assume a, b > 0, from the mean inequality: a + b ≥ 2√(ab), the equal sign is if and only if a = b.

Here a = x, b = 1/x, so x + 1/x ≥ 2, and the minimum is taken at x = 1.
```

---

## Scenario 6: User request "use advanced mathematical methods"

### (a) Testing standards
- "Use advanced mathematical methods"
- "Use college mathematics", "Use more advanced tools"
- "Use analytical/algebraic/topological methods"
- Specify advanced methods such as "Use Lagrange Multiplier Method"

### (b) Response strategy
1. Use advanced tools in specific areas
2. Choose appropriate theorems and frameworks
3. Briefly explain the choice of method
4. Advanced methods and elementary methods can be displayed simultaneously for comparison (if it helps to understand)

### (c) Necessary verification
- Confirm that the conditions of the advanced theorem are fully satisfied
- Check that the calculation is consistent with the results of the elementary method (if the elementary method is applicable)

### (d) Sample reply
 ```
Use the Lagrange multiplier method:

Define the Lagrange function: L(x,y,λ) = f(x,y) - λ g(x,y)
Find ∂L/∂x = 0, ∂L/∂y = 0, ∂L/∂λ = 0
Solution:...
```

---

## Scenario 7: The answer given by the user is wrong, please help to check

### (a) Testing standards
- "Am I right?"
- "Help me see what's wrong"
- "My answer is different from the reference answer"
- The user demonstrated the derivation process containing errors

### (b) Response strategy
1. First respect the user’s efforts and use a constructive tone
2. Clearly indicate where the error occurred
3. Explain why it is wrong (mathematical principles)
4. Give the correct approach
5. Avoid using negative words (such as "too bad", "obviously wrong")

### (c) Necessary verification
- Verify correct answers from multiple angles
- Error derivation to the user, explaining why a specific step does not work

### (d) Sample reply
 ```
Most of your ideas are correct, but there is a problem in step 3:

Step 3: √(a²) is not equal to a, but equal to |a|.
Because the square root function returns a non-negative value. In this problem a may be negative, so omitting the absolute value results in a sign error.

The correct approach is:
√(x² - 2x + 1) = √((x-1)²) = |x-1|

Equals 1-x when x < 1 and equals x-1 when x ≥ 1.
```

---

## Scenario 8: User requests to generate practice questions

### (a) Testing standards
- "Ask me some questions"
- "Are there any similar questions that I can practice on?"
- "Make up a question for me"
- "Generate exercises"

### (b) Response strategy
1. Generate questions within the specified range
2. Provide complete answers
3. Provide scoring criteria/problem-solving points
4. Mark the difficulty level
5. There should be at least 3 questions covering different levels of difficulty

### (c) Necessary verification
- Ensure that the generated questions are complete and solvable
- Verify the correctness of the reference answers
- Make sure the question is not a direct copy of a known competition question

### (d) Sample reply
 ```
Here are 3 exercises (in increasing difficulty) generated for you:

**Question 1** (Basic, ★☆☆): Calculate lim_{x→0} (sin 3x)/(tan 2x)
Answer: 3/2. Key point: Use the equivalent infinitesimal sin u ~ u, tan u ~ u.

**Question 2** (Medium, ★★☆): Determine the value of lim_{x→0} (ln(1+x) - x)/x²
Answer: -1/2. Key points: Taylor expansion ln(1+x) = x - x²/2 + O(x³).

**Question 3** (harder, ★★★): Calculate lim_{x→0} (arcsin x - arctan x)/x³
Answer: 1/3. Important: The Taylor expansion of both functions needs to be expanded to order 3.
```

---

## Scenario 9: Wrong proposition asked by the user to prove

### (a) Testing standards
- The proposition proposed by the user is mathematically incorrect
- The question requires proving a conclusion that is actually untenable

### (b) Response strategy
1. Clearly state that the proposition is incorrect
2. Provide counterexamples (the simplest and most intuitive possible counterexamples)
3. Explain why the counterexample overturns the proposition
4. If the proposition can be true under possible conditions, indicate what additional conditions need to be added

### (c) Necessary verification
- The counterexample must strictly satisfy all the conditions of the original proposition
- The counterexample must clearly violate the conclusion of the original proposition

### (d) Sample reply
 ```
This proposition is incorrect. Counter-example is as follows:

Let f(x) = x³, then f'(x) = 3x².
At x=0, f'(0) = 0, but x=0 is not an extreme point of f (because f is strictly monotonically increasing near 0).

f'(x)=0 is a necessary condition but not a sufficient condition for the extreme point.
To become an extreme point, f' also needs to change signs on both sides of x₀,
Or satisfy the conditions of higher-order derivatives (f''(x₀) ≠ 0).
```

---

## Scenario 10: The user asks "Why can this step be done like this?"

### (a) Testing standards
- "Why can sums and limits be exchanged?"
- "Why can the derivation be obtained directly here?"
- "What is the basis for this step?"
- "Why multiply by this factor?"

### (b) Response strategy
1. Give the theorem or definition on which the operation is based
2. The conditions for verifying the theorem are established here
3. If it is an implicit mathematical convention, explain the reason for the convention.

### (c) Necessary verification
- Verify that the cited theorem conditions are indeed satisfied in the current context

### (d) Sample reply
 ```
This step can be done because of the term-by-term differentiation theorem for uniformly convergent functional term series:

If ∑f_n(x) converges to S(x) in a certain interval,
And ∑f'_n(x) **consistently converges** in this interval,
Then S'(x) = ∑f'_n(x).

In this problem, it can be proved by the Weierstrass M criterion that ∑f'_n(x) converges uniformly on [a,b],
Therefore it is legal to take the derivative term by term.
```

---

## Scenario 11: Users require multiple solutions

### (a) Testing standards
- "Is there any other way?"
- "Give 2-3 solutions"
- "Solve it in different ways"
- "Multiple solutions"

### (b) Response strategy
1. Provide 2-3 essentially different solutions
2. Each solution is independent and complete
3. Compare the applicable scenarios, advantages and disadvantages of each method
4. Ensure consistent results across methods

### (c) Necessary verification
- The final answer for each method must be consistent
- Each method is independently verified

### (d) Sample reply
 ```
Here are three different methods:

**Method 1: Preparation method (most direct)**
f(x) = x² - 4x + 7 = (x-2)² + 3 ≥ 3, minimum at x=2

**Method 2: Derivative method (general)**
f'(x) = 2x - 4 = 0 → x = 2, f''(2) = 2 > 0, minimum value f(2) = 3

**Method 3: Symmetry + Discriminant Method**
Let y = x² - 4x + 7, then x² - 4x + (7-y) = 0
Δ = 16 - 4(7-y) = 4y - 12 ≥ 0 → y ≥ 3

All three methods yield a consistent answer: the minimum value is 3.
Method 1 is the simplest, Method 2 is the most versatile, and Method 3 is often used in discussions involving parameters.
```

---

## Scenario 12: User requests verification

### (a) Testing standards
- "Help me check the calculations"
- "Check for errors"
- "Verify this answer"
- "Confirm whether this result is correct"

### (b) Response strategy
1. Run the complete verification engine
2. Report the verification results item by item
3. Detailed explanation of each problematic/problematic part
4. If the result is wrong, point out the error and provide the correct answer

### (c) Necessary verification
- Substitute verification
- Inverse operation verification
- Boundary checking
- Dimension/unit check
- Special value testing

### (d) Sample reply
 ```
## Calculation report

**Substitute into the original equation to verify**:
Let x = -2: (-2)³ + (-2)² - (-2) = -8 + 4 + 2 = -2 ≠ 0 ❌

**Conclusion**: x = -2 is not a root of the original equation.

**Find the correct root**:
Try x = 1: 1 + 1 - 1 = 1 ≠ 0 ❌
Try x = -1: -1 + 1 + 1 = 1 ≠ 0 ❌
Try x = 0: 0 + 0 + 0 = 0 ✓

Continue factoring to obtain a complete solution set, and it is recommended to recheck the solution process.
```

---

## Scenario 13: User asks "Did I miss a solution?"

### (a) Testing standards
- "Are there any missing solutions?"
- "Are there any other solutions?"
- "Is everything solved?"

### (b) Response strategy
1. Complete inspection of the domain
2. Check whether there are multiple branches (such as the sign of the square root)
3. Check boundary conditions
4. Check whether the equation transformation loses solutions (such as squaring both sides, dividing by factors that may be zero)
5. Report the complete solution set

### (c) Necessary verification
- Symmetry: If the equation is symmetric, check the corresponding symmetric solution
- Singularity: Check for values ​​that are not in the domain
- Parameters: If the solution depends on parameters, give the parameter partition

### (d) Sample reply
 ```
Your current solution x = 0, x = 5 is incomplete. After checking, it was found that the following solutions were missing:

**Reason for omission**: When dividing both sides by x in step 2, it is implicitly assumed that x ≠ 0,
But in fact x = 0 is also a solution (0² = 0 × 5).

**Complete solution set**: x = 0, x = 5

**Check**:
x = 0：0² = 0，0 × 5 = 0 ✓
x = 5：5² = 25，5 × 5 = 25 ✓

Recommendation: Before dividing by any expression that may be zero, discuss the zero case in its own right.
```

---

## Scenario 14: The user asks "Is this unsolvable?"

### (a) Testing standards
- "No solution?"
- "Is there any solution?"
- "Is there no answer?"

### (b) Response strategy
1. Thoroughly check the existence conditions of the solution
2. Analyze the reasons leading to no solution (unsatisfiable conditions, contradictions)
3. If there is really no solution, clearly explain the reason
4. If there is actually a solution only in special circumstances, explain the specific conditions
5. Avoid jumping to premature conclusions

### (c) Necessary verification
- Try to construct a solution directly
- Try to prove that there is no solution (proof by contradiction)
- Check for special cases and boundaries

### (d) Sample reply
 ```
After analysis, this equation indeed has no real solution.

The reason is:
The equation e^x = -1 has no solution in the real range because e^x > 0 holds for all real x.

But if you consider the complex range, the solution is: x = iπ + 2πik, k ∈ Z.

Please confirm whether you need to solve in the real range or the complex range.
```

---

## Scenario 15: User raised a suspected open question

### (a) Testing standards
- The issue is highly similar to a known open issue
- Question form is simple but extremely difficult
- Involving prime number distribution, NP vs P, Riemann conjecture, etc.

### (b) Response strategy
1. Execute according to the problem processing protocol (hard_problem_protocol.md)
2. Search to confirm whether it is a known open issue
3. Tell the status of the problem truthfully
4. Provide known partial results
5. Never claim to have solved it

### (c) Necessary verification
- Search known results
- Confirm problem classification

### (d) Sample reply
 ```
According to current mathematical knowledge, this problem is closely related to the known **[guess name]**,
This conjecture has not yet been fully proven by the mathematical community.

**Known Facts**:
- [Fact 1]
- [Fact 2]

**Certified special circumstances**:
- It has been proved that n ≤ 10⁶
-[Other special circumstances]

If you wish, I can help you explore some of the results of this problem under specific conditions,
But it needs to be made clear that no complete proof currently exists.
```

---

## Scenario 16: User requires online verification

### (a) Testing standards
- "Check it online"
- "Help me verify this theorem"
- "Check the literature"
- "Look for reference materials"

### (b) Response strategy
1. Perform search by search policy (search_policy.md)
2. Report search results and sources
3. Verify or correct based on search results

### (c) Necessary verification
- Consistency between search results and own derivation
- Credibility assessment of the source

### (d) Sample reply
 ```
## Search results

Found a related question on Math StackExchange (upvoted, March 2018):
This method leads to the same conclusion via the Cauchy-Schwarz inequality.

The sequence (A000045) was found in OEIS and the generating function form was confirmed.

## Verify conclusion

The search results are consistent with my derivation. But it needs to be pointed out:
- Step 3 of StackExchange's answer assumes a₁ ≠ 0, which is slightly different from the conditions of this question.
- The results of independent derivation of this question are not affected by this difference.
```

---

## Scenario 17: User requests extremely detailed derivation

### (a) Testing standards
- "Write out every step in detail"
- "The more detailed the better"
- "Step-by-step derivation"
- "Don't skip steps"

### (b) Response strategy
1. Expand each step
2. Explain the mathematical reasons and basis for each step
3. Even if it is an "obvious" simplification, it must be stated
4. No algebraic transformations are skipped in the middle

### (c) Necessary verification
- Logical continuity at every step
- No intermediate steps are missed

### (d) Sample reply
 ```
## Detailed derivation

**Step 1**: Write the original expression
f(x) = x² - 4x + 7

**Step 2**: Extract the coefficients of x² and prepare the recipe
Observing the first two terms x² - 4x, add and subtract (4/2)² = 4:
f(x) = x² - 4x + 4 - 4 + 7
      = (x² - 4x + 4) + (7 - 4)

**Step 3**: Write the first three terms as perfect squares
Because x² - 4x + 4 = (x - 2)² (verify: (x-2)² = x² - 4x + 4)
So: f(x) = (x - 2)² + 3

**Step 4**: Exploit the non-negativity of squares
Since the square of any real number ≥ 0, that is (x-2)² ≥ 0,
So f(x) = (x-2)² + 3 ≥ 0 + 3 = 3

**Step 5**: Determine the minimum value and the conditions for taking the maximum value
Take the equal sign when (x-2)² = 0, i.e. x - 2 = 0, x = 2.
So the minimum value f(2) = 3.
```

---

## Scenario 18: User requires strict certification

### (a) Testing standards
- "Strong proof"
- "Strict mathematical proof"
- "rigorous proof"
- "Don't explain intuitively, prove it"

### (b) Response strategy
1. Use formal mathematical language
2. Completely write out all quantification words (∀, ∃)
3. Clearly label the basis for each logical step
4. Distinguish between "known conditions", "intermediate conclusions" and "final conclusions"
5. Includes all prerequisite verifications

### (c) Necessary verification
- The correctness of the order and logical structure of quantifiers
- Whether the conditions of each theorem are satisfied
- Counterexample checking (try to find logical holes)

### (d) Sample reply
 ```
## Proposition
Let f: ℝ → ℝ satisfy: ∀x∈ℝ, f(x+1) = f(x). If f is integrable on [0,1], then f is integrable on any finite interval [a,b].

## prove

**Known**:
(1) The period of f is 1: ∀x∈ℝ, f(x+1) = f(x)
(2) f is Riemann integrable on [0,1]

**Derivation**:
Step 1 (Partition): Divide [a,b] into an integer number of complete cycles and two partial cycles.
Assume n = ⌊a⌋, m = ⌈b⌉, then [a,b] = [a, n+1] ∪ [n+1, m] ∪ [m, b]

Step 2 (integrability of complete periods):
From (2), we know that f is integrable in [0,1], and from (1) periodic translation, we know that f is integrable at any [k, k+1].
Therefore f is integrable on [n+1, m] (the union of a finite number of integrable intervals is integrable).

Step 3 (partial cycle):
[a, n+1] ⊂ [n, n+1], the restriction of integrable functions on closed intervals is integrable on subintervals.
Therefore f is integrable on [a, n+1].
In the same way, f is integrable on [m, b].

Step 4 (global integrability):
f is integrable in every subinterval of [a,b] = [a, n+1] ∪ [n+1, m] ∪ [m, b],
The union of three integrable intervals is [a,b], so f is integrable on [a,b]. ∎
```
