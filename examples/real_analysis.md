# Proof and counterexample construction of consistent continuity

## User input
Show that the function $f(x) = x^2$ is consistently continuous on the interval $[0, 1]$ but not on the interval $[0, \infty)$.

## Skill Category
real analysis

## Question meaning analysis
- **Function**: $f(x) = x^2$, defined in the real number domain.
- **Two propositions that need to be proved**:
1. $f$ is uniformly continuous on the closed interval $[0, 1]$.
2. $f$ is not consistent on the unbounded interval $[0, \infty)$.
- **Key difference**: $[0, 1]$ is a compact set (closed and bounded), and continuous functions on the closed interval must be consistent and continuous (Cantor's theorem, which can be used to support but cannot replace constructive proof). $[0, \infty)$ is not a compact set.
- **Consistent Definition**: $\forall \varepsilon > 0,\ \exists \delta > 0,\ \forall x, y \in D,\ |x - y| < \delta \implies |f(x) - f(y)| < \varepsilon$.
- **Inconsistent Continuous Meaning**: There exists $\varepsilon_0 > 0$ such that for any $\delta > 0$ , there is always $x, y$ that satisfies $|x - y| < \delta$ but not $|f(x) - f(y)| \geq \varepsilon_0$ .

## Method selection
**Prove consistent continuity**: Use the identity $|x^2 - y^2| = |x + y| \cdot |x - y|$ and scale $|x + y|$ on the bounded interval. This is the standard $\varepsilon$ - $\delta$ constructor.

**Prove inconsistent continuity**: Construct a sequence counterexample, select $x_n$ and $y_n$ so that $|x_n - y_n| \to 0$ but $|f(x_n) - f(y_n)|$ remains lower bound. Commonly used constructs are $x_n = n + \frac{1}{n}$, $y_n = n$, which use the $2n$ factor divergence in the squared difference expansion.

## Problem solving process

### Part One: $f(x) = x^2$ is consistent on $[0, 1]$

For any $x, y \in [0, 1]$ :

 $$|f(x) - f(y)| = |x^2 - y^2| = |x + y| \cdot |x - y|$$

Since $x, y \in [0, 1]$ , so $|x + y| \leq 1 + 1 = 2$ . therefore:

 $$|f(x) - f(y)| \leq 2|x - y|$$

Given $\varepsilon > 0$ , take $\delta = \dfrac{\varepsilon}{2} > 0$ . Then when $|x - y| < \delta$:

 $$|f(x) - f(y)| \leq 2|x - y| < 2 \cdot \frac{\varepsilon}{2} = \varepsilon$$

This is the very definition of consistent continuity. $\square$

### Part Two: $f(x) = x^2$ is inconsistently contiguous on $[0, \infty)$

Proof idea: Assuming there is a consistent and continuous $\delta(\varepsilon)$, then for sufficiently large $x$, $|f(x+\delta/2) - f(x)|$ should be controlled by $\varepsilon$. but

 $$|f(x + h) - f(x)| = |(x+h)^2 - x^2| = |2xh + h^2|$$

For a fixed $h$ , when $x \to \infty$ , this difference tends to infinity, paradoxically.

Formal proof: take $\varepsilon_0 = 1$ . For any $\delta > 0$ , select

 $$x = \frac{1}{\delta},\quad y = \frac{1}{\delta} + \frac{\delta}{2}$$

then $|x - y| = \dfrac{\delta}{2} < \delta$ , but:

 $$|f(x) - f(y)| = \left|\left(\frac{1}{\delta} + \frac{\delta}{2}\right)^2 - \left(\frac{1}{\delta}\right)^2\right|$$

 $$= \left|\frac{2}{\delta} \cdot \frac{\delta}{2} + \left(\frac{\delta}{2}\right)^2\right| = 1 + \frac{\delta^2}{4} \geq 1 = \varepsilon_0$$

Therefore for any $\delta > 0$ , there exists $x, y \in [0, \infty)$ that satisfies $|x - y| < \delta$ but not $|f(x) - f(y)| \geq 1$ .

This violates the definition of $f$ being consistently continuous over $[0, \infty)$ . $\square$

**Alternative construction** (more elegant): take $x_n = n$ , $y_n = n + \frac{1}{n}$ . then $|x_n - y_n| = \frac{1}{n} \to 0$ , but:

 $$|f(x_n) - f(y_n)| = \left|n^2 - \left(n + \frac{1}{n}\right)^2\right| = \left|n^2 - n^2 - 2 - \frac{1}{n^2}\right| = 2 + \frac{1}{n^2} > 2$$

Contradicts consistent continuity (consistent continuity requires $|x_n - y_n| \to 0 \implies |f(x_n) - f(y_n)| \to 0$ ).

## Check calculation

### Method 1: $\varepsilon$ - $\delta$ structure check

**Structural Verification of Consistent Continuity Proofs**:
1. Starting from the inequality scaling: $|f(x) - f(y)| \leq L|x - y|$ (Lipschitz condition).
2. Find the Lipschitz constant $L = 2$, independent of the selection of $x, y$.
3. Given $\varepsilon$ , $\delta$ in $\delta = \varepsilon/2$ only depends on $\varepsilon$ , not on the specific $x$ or $y$ . This is exactly what "consistent" means. ✓

**Structural Verification of Inconsistent Continuity Proofs**:
1. Select $\varepsilon_0 = 1$ to be a specific positive number.
2. Constructing $x, y$ for "any" $\delta$ makes $|x - y| < \delta$ but not $|f(x) - f(y)| \geq \varepsilon_0$ . It is correct that the construction of $x$ and $y$ depends on $\delta$ (i.e. $x = 1/\delta$ ) - counterexamples can of course rely on the given $\delta$ . ✓

### Method 2: Verification of boundary conditions

** $[0, 1]$ on **: When $x = 1$ , $y = 0.999$ ( $|x-y| = 0.001$ ):
 $$|f(1) - f(0.999)| = |1 - 0.998001| = 0.001999 \approx 2 \times 0.001$$
Meets Lipschitz circles. ✓

** $[0, \infty)$ on**: when $n = 100$ , $x_n = 100$ , $y_n = 100.01$ :
 $$|f(100) - f(100.01)| = |10000 - 10002.0001| = 2.0001 > 2$$
Even though the distance between the two points is only $0.01$, the function value difference exceeds $2$. ✓

### Method 3: Theorem comparison

Cantor's theorem: Continuous functions on compact sets are uniformly continuous. $[0, 1]$ is a compact set in $\mathbb{R}$ , $f(x) = x^2$ is continuous, and therefore uniformly continuous. This is consistent with the conclusion of the first part of the constructive proof. ✓

$[0, \infty)$ is not a compact set (unbounded), Cantor's theorem does not apply, so consistent continuity cannot be directly derived from continuity - the counterexample confirms this. ✓

## Final answer

$$\boxed{f(x) = x^2 \text{ is consistent and continuous on } [0, 1] \text{}}$$

$$\boxed{f(x) = x^2 \text{ is inconsistently continuous on } [0, \infty) \text{}}$$

## Easy to make mistakes
1. **The effect of Lipschitz constant on bounded intervals**: The key to scaling $|x + y| \leq 2$ is to take advantage of the boundedness of the interval. If the interval is unbounded (such as $[0, \infty)$ ), $|x + y|$ does not have a uniform upper bound, so the global Lipschitz estimate cannot be derived.
2. **Construction of counterexamples**: $|x_n - y_n| \to 0$ but $|f(x_n) - f(y_n)| \not\to 0$ is an inconsistent and continuous **equivalent characterization** and is not a sufficient condition. This condition is equivalent to "there is $\varepsilon_0$ such that $\forall \delta, \exists x, y: |x-y|<\delta \land |f(x)-f(y)|\geq\varepsilon_0$". Constructed to ensure that the difference is at least constant (does not tend to zero).
3. ** Dependence of $\delta$ and $\varepsilon$**: Consistent continuity requires that $\delta$ only depends on $\varepsilon$ and not on $x$. In the proof of $[0,1]$ $\delta = \varepsilon/2$ does exactly this. Don't confuse point-by-point continuity with consistent continuity.
4. ** Discussion of $x = 1/\delta$**: When $\delta \to 0$ is $x \to \infty$, it means that the counterexample does need to go to infinity. This reveals that the source of inconsistent continuity lies in the infinite growth of the slope of the function in the distance.
