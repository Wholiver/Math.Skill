# Math.skill Search Policy

## 1. When to Search (When to Search)

A search must be performed when any of the following conditions are encountered:

### Trigger condition 1: Uncertain mathematical facts
When there is uncertainty about:
- precise statement of a theorem, prerequisite or conclusion
- The form, scope of application or derivation path of the formula
- A standard expression or equivalent form of a definition
- Exact or approximate values ​​of mathematical constants
- author, year or standard name of the naming theorem

**Example**: "What are the precise conditions for Stoltz's theorem? Does the sequence need to be strictly monotonic?" - should be searched for confirmation.

### Trigger 2: Highly specialized mathematical objects
When the question involves:
- Highly specialized mathematical objects (e.g. p-radical numbers, modular forms, homologous algebra, sheath theory)
- Papers or research results published in the past 5 years
- Cutting edge topics in modern mathematics research
- Non-standard notation or domain-specific conventions

**Example**: User asked about the properties of Perverse Sheaves - should search for confirmed definitions and known conclusions.

### Trigger condition 3: User’s explicit request
When a user explicitly expresses the following intent:
- "Check it for me..."
- "Are there any similar questions?"
- "Is there a source for this result?"
- "Can you help me find the original paper of...?"
- "Are there any standard answers online?"
- "Help me verify this theorem"

### Trigger condition 4: The source of the suspected question is known
When there is reason to suspect a problem:
- May be from known competitions (IMO, Putnam, China Mathematical Olympiad, etc.)
- Exercises that may come from well-known textbooks (such as Rudin, Artin, Tongji Mathematics, etc.)
- Conclusions that may come from a paper
- May be discussed on Math StackExchange or AOPS

### Trigger condition 5: Need to confirm whether it is a known unresolved issue
When a problem seems too difficult or involves known conjecture:
- Involving prime number distribution, Goldbach, Riemann conjecture, etc.
- Involving NP vs P, Collatz conjecture and other open problems
- Problems with simple structures but no known elementary solutions

### Trigger condition 6: Need to find standard definitions or authoritative expressions
When it is necessary to cite a generally accepted mathematical expression:
- Look up standard definitions (such as "equivalent definition of compactness")
- Look up the authoritative statement of the naming theorem (such as "the complete statement of the implicit function theorem")
- Compare the differences in expressions of the same concept in different textbooks or documents

### Trigger condition 7: Need to compare problem-solving methods or find known technologies
When the goal is to compare different solutions or discover known techniques:
- Want to compare more than 2 problem-solving paths
- Need to know the standard solution to a certain type of problem
- Need to find a standard application pattern of a certain theorem

---

## 2. Search Authority Hierarchy

Search results are divided into four levels based on credibility:

### Priority 1: Highest credibility
Sources you can trust and cite directly:
- **Classic textbooks**: such as Rudin's "Principles of Mathematical Analysis", Artin's "Algebra", Tongji's "Advanced Mathematics", etc.
- **Official university handouts**: course notes or handouts issued by well-known universities (such as MIT OCW, Stanford course notes)
- **Mathematical encyclopedia authoritative websites**: such as ProofWiki (rigorous proof), nLab (category theory, etc.), Springer Encyclopedia of Mathematics

**Usage**: Directly quote the theorem number, page number, and standard expression.

### Priority 2: High Confidence
Trusted but cross-verified sources:
- **Peer-reviewed mathematics papers**: papers published in recognized journals
- **MathWorld (Wolfram)**: The recognized mathematical reference resource
- **OEIS (oeis.org)**: Encyclopedia of Sequences, the authoritative reference for number theory/combinatorial problems
- **arXiv**: Preprint, please note whether it is an officially published version
- **Official answers to the competition**: Answers officially released by IMO, Putnam, etc.
- Blogs maintained by recognized mathematicians such as **Terence Tao Blog and Timothy Gowers Blog**

**How ​​to use**: Use these sources as the main reference, but in the event of conflict, your own derivation shall prevail.

### Priority 3: Medium confidence (caution required)
Sources that can be used as a reference but not to be followed blindly:
- **Math StackExchange**: The quality of answers varies, depending on the number of votes and comments
- **MathOverflow**: Research-grade math Q&A, usually higher quality than MSE, but still needs to be verified
- **Art of Problem Solving (AoPS)**: Contest community answers
- **Wikipedia (Mathematical Entry)**: Readable as a starting point, but requires cross-validation of key statements

**How ​​to use**: As a heuristic reference, key steps must be independently re-derived and verified.

### Priority 4: Not available
The following sources must not be used:
- **Random Personal Blog**: Personal blog without obvious academic qualifications
- **Unverified Forum**: Unverified answers from non-professional mathematics forums such as Zhihu (Zhihu) and Baidu Zhidao (Baidu Zhidao)
- **AI generated content**: mathematical content generated by other AI or LLM, ChatGPT output, etc.
- **Social media posts**: Unstructured discussions on Weibo, Twitter, Reddit, etc.
- **Content Farm**: Math content cobbled together for SEO purposes

---

## 3. Search Ethics and Rules

### Rule 1: Direct copying is strictly prohibited
**Absolutely prohibited** Directly copying solutions found online. The search results can only be used as a reference, and the final solution must be independently re-derived from the principles.

### Rule 2: Search results are for reference
Search results only serve as a means of understanding the structure and direction of the question; the final solution must be restated in your own words, with each step independently verified.

### Rule 3: Handling Conflicts
If the answer found online is inconsistent with your own derivation:
1. Mark each step where a conflict exists
2. List the differences between your own derivation and online answers
3. Recheck each condition on both sides
4. Try to use counterexamples to distinguish between the two methods
5. If you are not sure which side is correct, explain it truthfully.

### Rule 4: When no similar questions can be found
If you can't find any similar questions or methods after searching:
1. Derivation from the definition
2. Use known standard theorems
3. Use basic mathematical methods (induction, disproof, construction, etc.)
4. Clearly mark "This question has no similar questions found in public resources"
5. Do not reduce the rigor of the derivation.

### Rule 5: Known Open Issues
If the issue is found to be a known open issue:
1. Clearly state that "This is a known unsolved problem, and there is currently no complete proof recognized by the mathematical community."
2. Provide a known standard name for the problem
3. Summarize some of the known results (if any)
4. Indicate known attempts at proof and why they failed (if any)
5. Never claim that an open issue is "solved"

### Rule 6: No fictitious references allowed
**Absolutely prohibited** The following fictional content:
- Non-existent paper title, author or journal
- non-existent theorem number or name
- References to non-existent textbooks
- Non-existent DOI or URL

If you really need to cite but the exact source cannot be found, use the expression "based on known mathematical results..."

---

## 4. Countermeasures when there is no network

When Internet access is not available, follow these strategies:

### Available internal resources
1. **Mathematical reasoning itself is the first resource** - derivation from first principles does not require an Internet connection
2. **Knowledge reserve of standard theorems** - using the mathematical knowledge internalized in the training data
3. **Systematic application of basic methods** - Methodologies such as induction, disproof, construction, and transformation do not rely on the Internet

### Response Framework
1. **Start with definitions and axioms**: Write down all relevant definitions
2. **Quoting known standard theorems**: Although the exact number cannot be verified, the theorem name and standard expression can be used
3. **Explicitly state assumptions**: If the condition memory of a certain theorem is uncertain, clearly state "Assume...the conditions of the theorem are satisfied"
4. **Mark the part that requires network verification**: Add the `[to be network verified]` mark at the end of the answer

### Labeling specifications
 ```
## Internet verification suggestions
- [ ] Verify the precise requirement of Stoltz's theorem on the monotonicity of the denominator
- [ ] Confirm whether the analytical solution of the integral exists
- [ ] Check the standard name of the combined identity
```

---

## 5. Search Query Formulation

### Basic principles
1. **Use English keywords**: Mathematics literature is mainly in English, and the hit rate of English queries is significantly higher than that of Chinese
2. **Contains LaTeX syntax**: Use `$a_n$`, `$\sum$` and other LaTeX fragments directly in the query
3. **Target source specific**: If you want to search StackExchange, add `site:math.stackexchange.com`
4. **Contains theorem name**: If there is a standard name, directly use the standard name to query

### Query construction template

#### Check definition/theorem expression
 ```
"theorem_name" statement conditions
```
Example: `"Stolz Cesaro theorem" statement conditions`

#### Check similar questions
 ```
"[Simplified mathematical expression]" similar problem solution
```
Example: `sum_(k=1)^n k*k! similar problem`

#### Check if it is an open issue
 ```
"[Problem description]" open problem unsolved conjecture
```
Example: `"is every even number sum of two primes" open problem`

#### Check specific competition questions
 ```
"[Keywords]" IMO OR Putnam OR "Chinese Mathematical Olympiad" problem solution
```

#### Check the standard method
 ```
"[Problem type]" standard technique OR method OR approach
```
Example: `"evaluate improper integral" standard technique contour`

#### Using OEIS
 ```
"[First few items of the sequence]" OEIS
```
Example: `1, 1, 2, 3, 5, 8, 13 OEIS`

### Post-search processing
1. Read summaries of search results instead of clicking through them one by one
2. Prioritize reading StackExchange’s highly praised answers (>10 upvotes) and MathOverflow answers
3. Verify whether the key formulas are consistent with your own understanding
4. Record the key conclusions and sources found
