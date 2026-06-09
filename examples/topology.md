# Proof of closure of finite sets in metric space

## User input
In the metric space $(X, d)$, show that any finite set is closed.

## Skill Category
Topology/Basics of Point Set Topology

## Question meaning analysis
- **Condition**: $(X, d)$ is an arbitrary metric space, $F = \{x_1, x_2, \ldots, x_n\}$ is a finite subset of $X$ ( $n \in \mathbb{N}^+$ )
- **Goal**: Prove that $F$ is a closed set, that is, the complement of $F$ and $X \setminus F$ is an open set
- **Open set definition**: $U \subseteq X$ is an open set if and only if for any $y \in U$, there exists $\varepsilon > 0$ such that tee $B(y, \varepsilon) \subseteq U$
- **Metric space arbitrary**: This conclusion does not depend on the special properties of $\mathbb{R}^n$ and is true for any metric space
- **Uniqueness of solution**: Prove that the path is unique (the complement is open), and verification requires checking multiple details

## Method selection
Use **direct proof**: prove that $F$ is a closed set by proving that the complement is an open set. This is the standard way to deal with closed sets in metric spaces, directly exploiting the dual definition of open/closed sets.

Alternative: It is also possible to prove closure (equivalent characterization) by showing that $F$ contains all its limit points, but the approach of having the complement open is more intuitive and computationally explicit.

## Problem solving process

**Step 1: Conversion problem**

Proving that $F$ is a closed set is equivalent to proving that $X \setminus F$ is an open set. Defined by an open set, it needs to be proved: for any $y \in X \setminus F$, there exists $r > 0$ such that $B(y, r) \subseteq X \setminus F$, that is, $B(y, r) \cap F = \varnothing$.

**Step 2: Construct radius $r$ **

Take any $y \notin F$ . Since $y \neq x_i$ ( $i = 1, 2, \ldots, n$ ), defined by the metric there is $d(y, x_i) > 0$ .

make
 $$r = \min\{d(y, x_1), d(y, x_2), \ldots, d(y, x_n)\}$$

**Key point**: Since $F$ is a finite set, this minimum value must exist (the minimum value of a finite number of positive real numbers is still a positive real number). In the case of an infinite set, the lower bound may be zero and the minimum may not exist - this is where the "finiteness" condition comes into play.

Because each $d(y, x_i) > 0$ takes the minimum value of a finite number of positive numbers, so $r > 0$ .

**Step 3: Verify $B(y, r) \subseteq X \setminus F$ **

Take any $z \in B(y, r)$, which is $d(y, z) < r$. Need to prove $z \notin F$ .

For any $x_i \in F$, the definition of $r$ has $r \leq d(y, x_i)$. therefore:
 $$d(y, z) < r \leq d(y, x_i)$$

So $d(y, z) < d(y, x_i)$ , therefore $z \neq x_i$ (otherwise $d(y, z) = d(y, x_i)$ ).

Since this is true for all $i = 1, \ldots, n$ , $z \notin F$ is also $z \in X \setminus F$ .

Therefore $B(y, r) \subseteq X \setminus F$ , $X \setminus F$ are open sets.

**Step 4: Conclusion**

$X \setminus F$ is an open set $\implies$ $F$ is a closed set. Certification completed.

**Step 5: Counterexample - infinite sets are not necessarily closed**

Consider the infinite set $S = \left\{\frac{1}{n} \mid n \in \mathbb{N}^+\right\}$ in the metric space $\mathbb{R}$ (the usual metric). $0 \notin S$ , but for any $r > 0$ , taking $n > 1/r$ , there is $\frac{1}{n} \in B(0, r)$ , so there is no ball centered on $0$ that is completely in the complement set. Therefore $\mathbb{R} \setminus S$ is not an open set and $S$ is not a closed set.

Key comparison: for the infinite set $S$ , $\inf\{d(0, s) : s \in S\} = 0$ , but the minimum does not exist (because $0 \notin S$ ). This is exactly the counterexample corresponding to "finite sets ensure the existence of minimum values" in the proof.

## Check calculation

**Verification method 1: Verify each condition defined by the open set**

1. $y \notin F$ $\checkmark$ — Prerequisite
2. $r > 0$ $\checkmark$ — For each $d(y, x_i) > 0$ , the smallest of a finite number of positive numbers is positive
3. $B(y, r) \subseteq X \setminus F$ $\checkmark$ — As proved above, the distance from any point in the ball to $y$ is less than the distance to each $x_i$, so it is not in $F$

**Verification method 2: Verification through limit point equivalent conditions**

The equivalent condition for $F$ to be a closed set is that $F$ contains all its limit points. For the finite set $F$ : Assume $\{z_k\}$ is a convergent sequence in $F$ , $\lim z_k = z$ . Since $F$ is finite, the sequence must have an infinite number of items taking a fixed $x_i$, so $z = x_i \in F$. Therefore $F$ contains all limit points and is a closed set.

**Verification method 3: Special case verification**

Takes $X = \mathbb{R}$ (the usual measure), $F = \{1, 3, 5\}$ . $y = 2 \notin F$ , $r = \min\{|2-1|, |2-3|, |2-5|\} = \min\{1, 1, 3\} = 1$ , $B(2, 1) = (1, 3)$ , and $(1, 3) \cap F = \varnothing$ . ✓

## Final answer

In any metric space $(X, d)$, any finite subset $F = \{x_1, \ldots, x_n\}$ is a closed set.

Proof core: For $y \notin F$, take $r = \min_{1 \leq i \leq n} d(y, x_i) > 0$, then $B(y, r) \subseteq X \setminus F$.

## Easy to make mistakes
1. **Ignore the key role of finiteness**: The existence of the minimum depends on the finiteness of the set. For infinite sets, only the indeterminate can be taken, and the indeterminate may be zero.
2. **Confusing reasoning** for $r > 0$: $r > 0$ is not only because of each $d(y, x_i) > 0$, but also because it takes the **minimum** of **finite** positive numbers (rather than the lower bound)
3. **Misunderstood that "any infinite set is not a closed set"**: Infinite sets can be closed sets (such as the closed interval $[0,1]$ in $\mathbb{R}$), but the argument of finiteness in the proof does not apply to infinite sets
4. **Limit the conclusion to $\mathbb{R}^n$ **: Prove that only using three axioms of metric space (positive certainty, symmetry, triangle inequality), they are true for any metric space
