# Higher Mathematics Test Cases

Test cases for advanced mathematical domains: real analysis, abstract algebra, topology, complex analysis, number theory, optimization.

---

## Test 1: ε-N Proof for Sequence Limit

**Test ID:** HM-001
**Input:** "Prove that lim(n→∞) 1/(n^2+1) = 0 using the ε-N definition."
**Expected Classification:** real_analysis, limit
**Expected Behavior:** Construct ε-N proof: for any ε>0, need |1/(n^2+1)| < ε → n > √(1/ε - 1). Choose N = ⌈max(0, √(1/ε - 1))⌉. Then for n>N, |1/(n^2+1)| < ε. Verify the inequality algebraically.
**Required Verification:** ε-N structure correctness, inequality verification
**Key Checks:** N must be integer, N depends on ε, inequality direction
**Failure Modes:** Wrong inequality direction, non-integer N, assuming limit without proof

---

## Test 2: Uniform Continuity Check

**Test ID:** HM-002
**Input:** "Is f(x)=x^2 uniformly continuous on [0,1]? On [0,∞)?"
**Expected Classification:** real_analysis
**Expected Behavior:** On [0,1]: Yes. |f(x)-f(y)|=|x+y||x-y|≤2|x-y|, so δ=ε/2 works for all x,y∈[0,1]. On [0,∞): No. Choose x_n=n, y_n=n+1/n. Then |f(x_n)-f(y_n)|=|n^2-(n+1/n)^2|=|n^2-n^2-2-1/n^2|=2+1/n^2>2. But |x_n-y_n|=1/n→0, so can't find δ independent of x.
**Required Verification:** ε-δ structure, counterexample construction for [0,∞)
**Key Checks:** The bound |x+y|≤2 on [0,1], the sequence counterexample validity
**Failure Modes:** Confusing uniform with pointwise continuity, not understanding domain dependence

---

## Test 3: Series Convergence Test

**Test ID:** HM-003
**Input:** "Determine if Σ(n=1→∞) 1/(n^2+n) converges."
**Expected Classification:** real_analysis
**Expected Behavior:** Compare with 1/n^2. 1/(n^2+n) < 1/n^2 for all n, and Σ1/n^2 converges (p-series, p=2>1). By comparison test, series converges. Alternatively: partial fraction 1/n-1/(n+1), telescoping sum = 1.
**Required Verification:** Comparison test conditions, p-series criterion, telescoping verification
**Key Checks:** Inequality direction correct, comparison series convergence known
**Failure Modes:** Confusing with harmonic series, wrong comparison direction

---

## Test 4: Subgroup Proof

**Test ID:** HM-004
**Input:** "Let G be a group. If H and K are subgroups of G, prove that H∩K is also a subgroup."
**Expected Classification:** abstract_algebra
**Expected Behavior:** Check subgroup criteria: (1) Identity: e∈H and e∈K so e∈H∩K ✓. (2) Closure: let a,b∈H∩K. Then a,b∈H→ab∈H. Similarly a,b∈K→ab∈K. So ab∈H∩K ✓. (3) Inverses: a∈H∩K→a∈H→a^(-1)∈H. Similarly a^(-1)∈K. So a^(-1)∈H∩K ✓. Therefore H∩K is a subgroup.
**Required Verification:** All three subgroup axioms checked
**Key Checks:** Must use both H and K properties, intersection definition correct
**Failure Modes:** Forgetting one axiom, confusing intersection with union

---

## Test 5: Homomorphism Construction

**Test ID:** HM-005
**Input:** "Construct a non-trivial group homomorphism from Z_6 to Z_3."
**Expected Classification:** abstract_algebra
**Expected Behavior:** Define φ: Z_6 → Z_3 by φ([x]_6) = [x]_3. Check it's well-defined: if [x]_6=[y]_6, then 6|(x-y), so 3|(x-y), thus [x]_3=[y]_3 ✓. Check homomorphism: φ([x]_6+[y]_6)=φ([x+y]_6)=[x+y]_3=[x]_3+[y]_3=φ(x)+φ(y) ✓. Non-trivial: φ([1]_6)=[1]_3≠[0]_3.
**Required Verification:** Well-definedness, homomorphism property for multiple test values
**Key Checks:** Well-definedness is crucial for quotient groups
**Failure Modes:** Not checking well-definedness, confusing domain/codomain

---

## Test 6: Ring Property

**Test ID:** HM-006
**Input:** "In a ring R, prove that a·0 = 0 for all a∈R."
**Expected Classification:** abstract_algebra
**Expected Behavior:** a·0 = a·(0+0) = a·0 + a·0. Subtract a·0 from both sides: 0 = a·0. Verify each step uses ring axioms: 0+0=0 (additive identity), distributivity, cancellation in additive group.
**Required Verification:** Each axiom referenced, cancellation justified
**Key Checks:** Cancellation is valid because (R,+) is a group
**Failure Modes:** Assuming the result, using multiplicative inverses (not in ring definition)

---

## Test 7: Open Set in Metric Space

**Test ID:** HM-007
**Input:** "In ℝ with the standard metric, prove that (0,1) is open."
**Expected Classification:** topology
**Expected Behavior:** For any x∈(0,1), let r=min(x,1-x)>0. Then B(x,r)⊆(0,1) because for y∈B(x,r): |y-x|<r≤x→y>0, and |y-x|<r≤1-x→y<1. Thus (0,1) is open.
**Required Verification:** Check r>0, check ball containment
**Key Checks:** Radius must be positive, containment proven for both bounds
**Failure Modes:** using r=0, only checking one bound, forgetting min function

---

## Test 8: Continuous Map Between Topological Spaces

**Test ID:** HM-008
**Input:** "Is f: ℝ→ℝ, f(x)=⌊x⌋ (floor function) continuous?"
**Expected Classification:** topology
**Expected Behavior:** NO. At x=1: f(1)=1, but for any ε<1, the preimage of (1-ε,1+ε) under f is [1,2) which is not open in ℝ. Alternatively: left limit at 1 is 0, right limit is 1, f(1)=1. Discontinuity at every integer.
**Required Verification:** Definition of continuity check, ε-δ counterexample
**Key Checks:** Distinguish standard vs discrete topology
**Failure Modes:** Assuming floor is continuous, checking only non-integer points

---

## Test 9: Compactness Argument

**Test ID:** HM-009
**Input:** "Is the set {1/n : n∈ℕ} ∪ {0} compact in ℝ?"
**Expected Classification:** topology
**Expected Behavior:** YES. In ℝ, compact ⇔ closed and bounded (Heine-Borel). The set is bounded (in [0,1]) and closed (0 is the only limit point, and it's included). Therefore compact. Direct proof: any open cover of 0 covers all but finitely many 1/n, then pick covers for remaining finitely many.
**Required Verification:** Heine-Borel conditions, limit point analysis
**Key Checks:** Must include 0 for closedness, boundedness check
**Failure Modes:** Forgetting Heine-Borel is ℝ-specific, missing that without 0 it's not compact

---

## Test 10: Residue Computation

**Test ID:** HM-010
**Input:** "Find Res(f, 0) for f(z)=e^z/z^3."
**Expected Classification:** complex_analysis
**Expected Behavior:** Laurent series: e^z=1+z+z^2/2+z^3/6+... So f(z)=1/z^3+1/z^2+1/(2z)+1/6+... Residue at 0 is coefficient of 1/z: Res(f,0)=1/2.
**Required Verification:** Laurent expansion, coefficient extraction
**Key Checks:** Correct series expansion of e^z, identifying a_{-1} term
**Failure Modes:** Miscounting powers, truncating series too early

---

## Test 11: Contour Integral via Residues

**Test ID:** HM-011
**Input:** "Evaluate ∮_C 1/(z^2+1) dz where C is the circle |z|=2."
**Expected Classification:** complex_analysis
**Expected Behavior:** Poles at z=±i, both inside |z|=2. Res(f,i)=1/(2i), Res(f,-i)=-1/(2i). Sum of residues=0, so integral=0. Alternative: partial fractions, direct integration.
**Required Verification:** Pole locations, residue computation for each, sum
**Key Checks:** Check both poles inside contour, correct residue formula
**Failure Modes:** Forgetting one pole, residue sign error

---

## Test 12: Euler's Theorem Application

**Test ID:** HM-012
**Input:** "Find the last digit of 7^100."
**Expected Classification:** number_theory
**Expected Behavior:** φ(10)=4. By Euler: 7^4≡1 (mod 10) since gcd(7,10)=1. 100=4·25, so 7^100≡(7^4)^25≡1^25≡1 (mod 10). Last digit is 1. Verify: 7^1=7, 7^2=49→9, 7^3=343→3, 7^4=2401→1 ✓.
**Required Verification:** φ(10) computation, Euler's theorem conditions, cycle verification
**Key Checks:** gcd(7,10)=1 (required for Euler), cycle length
**Failure Modes:** Computing φ(10) wrong, forgetting to check gcd condition

---

## Test 13: Chinese Remainder Theorem

**Test ID:** HM-013
**Input:** "Solve: x≡2 (mod 3), x≡3 (mod 5), x≡2 (mod 7)."
**Expected Classification:** number_theory
**Expected Behavior:** CRT application. M=3·5·7=105. M_1=35, inv(35,3)=inv(2,3)=2. M_2=21, inv(21,5)=inv(1,5)=1. M_3=15, inv(15,7)=inv(1,7)=1. x≡2·35·2+3·21·1+2·15·1≡140+63+30≡233≡233-2·105=23 (mod 105). x=23+105k. Verify: 23 mod 3=2 ✓, 23 mod 5=3 ✓, 23 mod 7=2 ✓.
**Required Verification:** CRT computation, back-substitution into each congruence
**Key Checks:** Modular inverses correct, all three congruences satisfied
**Failure Modes:** Incorrect modular inverse, arithmetic error in sum

---

## Test 14: Graph Theory Proof

**Test ID:** HM-014
**Input:** "Prove that in any graph with at least 2 vertices, there exist two vertices with the same degree."
**Expected Classification:** discrete_math, proof
**Expected Behavior:** Pigeonhole principle. In a graph with n vertices, each vertex degree is in {0,1,...,n-1}. But if some vertex has degree n-1 (connected to all), none can have degree 0. So actual possible degrees are either {0,...,n-2} or {1,...,n-1} - both have n-1 values. With n vertices and n-1 possible degrees, by pigeonhole, two must share a degree.
**Required Verification:** Degree range argument, pigeonhole application
**Key Checks:** The mutual exclusion of degree 0 and n-1 in a simple graph
**Failure Modes:** Forgetting that degree 0 and n-1 can't coexist

---

## Test 15: Lagrange Multipliers

**Test ID:** HM-015
**Input:** "Maximize f(x,y)=xy subject to x^2+y^2=1."
**Expected Classification:** optimization, multivariable_calculus
**Expected Behavior:** Lagrangian L=xy-λ(x^2+y^2-1). ∂L/∂x=y-2λx=0, ∂L/∂y=x-2λy=0. From these: y/x=2λ=x/y if x,y≠0. So y/x=x/y→x^2=y^2→x=±y. With constraint: 2x^2=1→x=±1/√2. Points: (1/√2,1/√2): f=1/2, (-1/√2,-1/√2): f=1/2. Min at (1/√2,-1/√2): f=-1/2. Max value: 1/2.
**Required Verification:** All critical points checked, constraint satisfied, KKT conditions
**Key Checks:** Both maximum and minimum found, all candidate points on constraint
**Failure Modes:** Missing negative branch, division by zero case (x=0 or y=0 gives f=0)
