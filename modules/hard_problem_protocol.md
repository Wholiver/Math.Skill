# Math.skill Hard Problem Protocol

When encountering problems beyond the scope of standard problem solving, follow the following protocol process.

---

## 1. Problem Classification

Before starting to solve the problem, first classify the problem:

| Classification | Features | Examples |
|------|------|------|
| **Standard textbook questions** | There are clear standard solutions and known theorems can be directly applied | Calculate derivatives, solve differential equations with constant coefficients, and calculate determinants |
| **Competition questions** | Requires skills but does not exceed the scope of elementary/advanced mathematics, and is known to have solutions | IMO questions, Putnam questions, and national training team questions |
| **Research level questions** | Involving cutting-edge mathematics, original ideas may be required | Conjectures raised in a certain paper, graduate-level research questions |
| **Known theorem** | Is a special case or direct corollary of a known theorem | A known conclusion that the user may not know |
| **Known open problems** | Unsolved problems in mathematics | Riemann conjecture, Goldbach conjecture, Collatz conjecture |
| **Missing conditions** | The problem statement is incomplete and necessary conditions are missing | The domain is missing, the initial conditions are missing, and the convergence assumption is missing |

### Classification decision-making process

1. First check whether the problem statement is complete → If it is incomplete, it will be classified as "missing condition"
2. Check whether the problem is an equivalent form of a known open problem → If so, classify it as a "known open problem"
3. Check whether there are standard solutions or direct applications of known theorems → If so, classify them into "standard textbook questions" or "known theorems"
4. Assess the technical depth required for the problem → Determine it as a "competition question" or "research level question"

---

## 2. Search Phase

For non-standard textbook questions, perform the following search:

### Search keyword structure
1. Extract the core mathematical objects in the problem
2. Construct 2-3 different sets of search queries
3. Use English keywords + LaTeX syntax

### Search target list
- [ ] Relevant theorems and their scope of application
- [ ] Is the issue a known open issue?
- [ ] Are there any known issues with similar structures?
- [ ] Whether there are known counterexamples
- [ ] Is there a known standard solution pattern?

---

## 3. Processing when similar problems are found (If Similar Problems Found)

### Processing principles
1. **Reference ideas, do not copy answers**: Understand the logical structure of online answers, but do not copy verbatim
2. **Independent re-derivation**: Close the search page and deduce based on the definition and conditions of the problem itself
3. **Step-by-step verification**: Each step must pass the verification check
4. **Reorganize in your own words**: The final solution must be your own understanding

### Output format
Clearly label the impact of search results in your answer:
     ```
## Reference to similar questions
- Find similar structured questions in [Source] [Brief Description]
- The method used in this question is different from the reference plan in [specific aspects]
- The following is the complete solution of independent derivation
```

---

## 4. No solution to similar problems can be found (first principles mode)

If the search does not find any similar problems, enter **First Principles Mode**.

### First principles model process

#### Step 1: Write down all relevant definitions
     ```
Definition of object X:…
Definition of property P:…
Precise definition of the problem: [Restated in mathematical language]
```

#### Step 2: Break down the goal into sub-goals
     ```
Goal: Prove P(X)
Sub-goal 1: Prove Q(X)
Subgoal 2: Prove R(X)
Subgoal 3: deduce P from Q and R
```

#### Step 3: Try a simple scenario
- n=1, n=2 and other small parameter cases
- Degenerate situations (such as matrices degenerating into scalars)
- Symmetrical situation
- homogeneous situation

#### Step 4: Try to construct a counterexample
- Try to find special circumstances that make the conclusion invalid
- If a counterexample is found → the conclusion is not valid and the problem ends here
- If no counterexample can be found → Increases confidence that the conclusion is true

#### Step 5: Try induction
- Check whether a parameter (dimension, degree, order, etc.) can be generalized
- Check whether the induction step needs to strengthen the inductive hypothesis

#### Step 6: Try mathematical transformations
- Variable substitution
- Coordinate transformation
- Dual transformation
- Generate function
- Fourier/Laplace transformation
- Symmetrization

#### Step 7: Try to establish the lemma
- Split the difficult proof into multiple independent lemmas
- Prove the lemma first, and then use the combination of lemmas to prove the main conclusion

#### Step 8: Try an equivalent restatement
- Converse proposition
- Dual form
- Geometric explanation
- Algebraic reformulation
- Restated in the language of random variables

#### Step 9: Numerical Experiment
- Perform numerical calculations on specific parameter values
- Observe numerical mode
- Use numerical results to guide the direction of theoretical derivation

#### Step 10: Try Special Situation Promotions
- If it is proved that n=1, n=2, n=3, etc.
- Check whether the proof method can be generalized to general n

#### Step 11: Try weakening the target
- Can a weaker conclusion be proved?
- Can it be proven under additional conditions?
- Some results are also valuable

#### Step 12: Step-by-Step Verification
- Immediately verify the logical correctness after each step of derivation
- Check details such as division by zero, zero denominator, direction of inequality, etc.

---

## 5. Handling of suspected open problems (Possible Open Problem)

### Identifying features
- The problem form is extremely simple but the proof is extremely difficult
- Involving the properties of prime numbers in number theory
- Extreme value conjecture involving graph theory
- Involving chaotic systems or dynamical systems
-Problem statement similar to known Millenium issues

### Processing process

#### Step 1: Search and confirm
Search with question keyword + "open problem" or "unsolved" or "conjecture".

#### Step 2: If confirmed as an open issue
**MUST enforce the statement**:
     ```
## Problem status

This problem is a known open problem in mathematics: [standard name]

### Known facts (verified)
- [Fact 1]
- [Fact 2]

### Guess content
- The conjecture claims: [precise statement]

### Known partial results
- [Known Result 1]
- [Known Result 2]

### Known failed attempts and reasons
- [Direction 1]: [Reason for failure]
- [Direction 2]: [Reason for failure]

### Numerical evidence
- verified to n ≤ [range]
- No counterexamples found

### Statement
There is currently no complete proof recognized by the mathematical community. The following is an exploratory analysis based on existing theories and does not represent a complete proof.
```

#### Step 3: Exploratory Analysis
Can provide:
- Partial results (held under certain special conditions)
- Results of numerical experiments
- Possible directions of attack (but clearly marked as speculation)
- Connection to known conclusions

#### Step 4: Strictly Prohibited Behavior
- **Absolutely prohibited from claiming to solve open problems** (unless complete, verifiable, gap-free proof is provided)
- **It is absolutely forbidden to make up any groundbreaking conclusions**
- **Absolutely forbidden to claim "I found a simple proof"** - If it were that simple, Fermat's Last Theorem and Poincaré's conjecture wouldn't have been around for hundreds of years

---

## 6. Iterative Advancement Strategy

### Keep moving forward
Don't stop when you encounter difficulties, try:
1. Change perspective (geometry ↔ algebra ↔ analysis)
2. Increase or relax conditions
3. Return to the hypothetical deduction of "if... is true"
4. Think from the opposite direction: If the result does not hold, what conditions are needed?

### Sign of reaching the verifiable stage
- Got some clear conclusions (if not the ultimate goal)
- Ability to perform numerical tests
- Be able to cite special cases for verification

### Clearly explain barriers
When you encounter a step that you cannot break through:
     ```
## Current obstacle
Encountered an obstacle at step [X]:
- We need to prove [specific statement]
- The problem lies in [specific difficulty]
- Known [theorems/methods] cannot be applied directly because of [reason]
```

### Suggest follow-up directions
     ```
## Possible breakthrough direction
1. [Direction 1]: [Specific reasons and expectations]
2. [Direction 2]: [Specific reasons and expectations]
3. [Direction 3]: [Prerequisites requiring verification]
```

---

## 7. Decision Tree

     ```
receive complex math questions
│
├─ Are the questions complete?
│ ├─ No → Request the user to add conditions → Return to judgment
│ └─ Yes ↓
│
├─ Is it a known open issue?
│ ├─ Yes → Execute the open problem protocol → Output partial results and declare unsolved
│ └─ No ↓
│
├─ Is there a standard solution?
│ ├─ Yes → Execute the standard problem-solving process → Output the standard solution
│ └─ No ↓
│
├─ Search for similar questions?
│ ├─ Find similar questions → Reference ideas and independent derivation → Output the solution
│ └─ Not found ↓
│
├─Enter first principles mode
│ ├─ Can it be advanced within a reasonable time?
│ │ ├─ Can → Advance to the verifiable stage → Output partial results or complete answers
│ │ └─ Can’t ↓
│  │
│ └─ Output current progress + obstacle description + follow-up direction
│
└─ If conditions are found to be missing at any stage → return to request for supplementation
```

---

## 8. Recording and Traceability

### Problem record
For each puzzle, record the following information:
- Problem classification
- Search keywords and results
- Methods tried and their results (success or failure)
- Current progress status
- unresolved obstacles

### Advice to users
At the appropriate time, suggest to users:
- Consulting experts (professors, researchers)
- Ask questions in an appropriate manner on MathOverflow
- Review literature in a specific direction
- Consider if there is a simplified version that can be solved first
