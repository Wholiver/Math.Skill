# Quality Rubric for Math.skill (100 Points)

This rubric evaluates the overall quality of a Math.skill response across 8 dimensions.

---

## 1. Correctness (25 points)

The mathematical accuracy of the final answer and all intermediate steps.

| Score | Criteria |
|-------|----------|
| 25 | Answer completely correct. All conditions satisfied. All solutions found. All edge cases handled. No errors in any step. |
| 20 | Answer correct but one minor oversight (e.g., missing one non-critical boundary case, imprecise interval notation). |
| 15 | Answer essentially correct but one non-critical error in derivation that doesn't affect final result, or secondary solution missed. |
| 10 | Partially correct with significant errors (wrong sign, missing extraneous root, incorrect simplification). |
| 5 | Major errors throughout. Answer unreliable. Fundamental misunderstanding of the problem. |
| 0 | Completely wrong. Answer bears no relation to the correct solution. |

**Grading Notes:**
- An extraneous root that was included is a -5 deduction
- A missing domain restriction is -3 deduction
- A sign error that propagates is -10 deduction
- A completely wrong method choice that leads to wrong answer is -15 deduction

---

## 2. Reasoning Transparency (15 points)

How clearly and traceably the reasoning is presented.

| Score | Criteria |
|-------|----------|
| 15 | Every step clearly justified. Reasoning fully traceable from start to finish. Reader can follow without guessing. |
| 12 | Most steps justified. Minor gaps that don't affect understanding. |
| 8 | Some steps explained, but significant "jumps" that require the reader to fill in gaps. |
| 4 | Many unexplained steps. The derivation feels like a "black box." |
| 0 | No reasoning shown. Only the final answer (unless user requested "answer only" mode). |

**Grading Notes:**
- "It can be shown that..." without showing is -3 per instance
- Skipping a key algebraic simplification step is -2
- Not explaining WHY a particular method was chosen is -1

---

## 3. Mathematical Rigor (15 points)

The formal correctness of the mathematical language, use of theorems, and logical structure.

| Score | Criteria |
|-------|----------|
| 15 | Definitions stated. Theorem conditions explicitly checked before use. Quantifiers correct. Proof structure clear. |
| 12 | Mostly rigorous with minor imprecisions (e.g., forgetting to state one condition). |
| 8 | Moderate rigor. Some conditions unchecked. Some quantifier ambiguity. |
| 4 | Significant rigor issues. Using theorems without checking conditions. Confusing necessary/sufficient. |
| 0 | No mathematical rigor. Intuition presented as fact. |

**Grading Notes:**
- Using L'Hôpital without checking 0/0 or ∞/∞ form is -5
- Dividing by (x-a) without checking x≠a is -5
- "Obviously" without justification is -2 per instance
- Confusing "for all" and "there exists" is -5

---

## 4. Verification Quality (20 points)

The thoroughness and correctness of the verification performed.

| Score | Criteria |
|-------|----------|
| 20 | Multiple verification methods (≥2). All explicit with calculations shown. Edge cases covered. Domain verified. |
| 15 | Good verification with one solid method. Edge cases mostly covered. Some verification steps shown. |
| 10 | Basic verification attempted. One method, partial coverage. Some cases missed. |
| 5 | Token verification only — says "verified" without showing any work. |
| 0 | No verification at all. |

**Grading Notes:**
- Back-substitution shown explicitly is +5
- Domain analysis complete is +3
- Boundary checks done is +3
- Numerical sampling done is +3
- Cross-validation with second method is +5
- Counterexample search done (for proofs/universal statements) is +5

---

## 5. Higher Math Capability (10 points)

Ability to handle advanced mathematical domains correctly.

| Score | Criteria |
|-------|----------|
| 10 | Advanced techniques correctly applied. All conditions verified. Domain-specific verification performed. |
| 7 | Advanced techniques mostly correct. One minor oversight in condition verification. |
| 4 | Attempted advanced techniques but with errors. Missing key conditions. |
| 0 | Failed on higher math, or avoided it entirely when it was clearly needed. |

**Grading Notes:**
- Correct ε-δ/ε-N proof is +10
- Correct application of residue theorem is +10
- Well-definedness checked in algebraic structures is +5
- Compactness argument in topology is +5
- N/A (no higher math involved) → score 10 by default

---

## 6. Input Classification Accuracy (5 points)

How accurately the problem category is identified.

| Score | Criteria |
|-------|----------|
| 5 | Correctly identified all relevant categories. Multi-category problems recognized. |
| 3 | Partially correct. Primary category right, secondary missed. |
| 0 | Misclassified. Wrong approach chosen due to classification error. |

**Grading Notes:**
- Missing that a problem needs proof AND computation is -2
- Classifying a research problem as standard is -3
- Not recognizing insufficient conditions is -5

---

## 7. Search and Uncertainty Handling (5 points)

Appropriate use of search and honest treatment of uncertainty.

| Score | Criteria |
|-------|----------|
| 5 | Correctly identified when to search or flag uncertainty. Honest about limitations. |
| 3 | Somewhat appropriate but missed a search opportunity or overstated certainty. |
| 0 | Made false certainty claims, missed obvious open problem, or fabricated sources. |

**Grading Notes:**
- Recognizing Goldbach as unsolved is +5
- Admitting when a theorem name is uncertain is +3
- Fabricating a citation is -5 (automatic 0)

---

## 8. Output Format (5 points)

Adherence to the specified output template and presentation standards.

| Score | Criteria |
|-------|----------|
| 5 | Correct template used. Clear structure. Proper LaTeX formatting. All sections present. |
| 3 | Minor format issues. One section missing. LaTeX partially correct. |
| 0 | Poor formatting. No structure. LaTeX broken. Wrong template. |

**Grading Notes:**
- All LaTeX properly delimited is required for 5
- Missing verification section is -3
- Using wrong template is -3
- Answer not in boxed form when appropriate is -1

---

## Total Score Interpretation

| Score Range | Grade | Interpretation |
|-------------|-------|----------------|
| 90-100 | A | Excellent. Reliable, rigorous, well-verified. |
| 80-89 | B | Good. Minor issues but trustworthy. |
| 70-79 | C | Adequate. Some gaps but essentially correct. |
| 60-69 | D | Problematic. Significant gaps or errors. |
| Below 60 | F | Unreliable. Should not be used. |
