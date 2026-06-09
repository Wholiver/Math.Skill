# Find the sum of the general term and the first n terms of the recursive sequence

## User input
It is known that the sequence $\{a_n\}$ satisfies $a_1 = 1$ and $a_{n+1} = 2a_n + 3$. Find the general formula of $\{a_n\}$ and the first $n$ terms and $S_n$.

## Skill Category
Sequence

## Question meaning analysis
- **Known conditions**: first item $a_1 = 1$, recursion relationship $a_{n+1} = 2a_n + 3$ ($n \geq 1$).
- **Solution Objective**: General term $a_n$ and previous $n$ terms and $S_n = \sum_{k=1}^n a_k$.
- **Recursion type identification**: First-order linear non-homogeneous recursion, in the form of $a_{n+1} = pa_n + q$, where $p = 2$, $q = 3$, and $p \neq 1$.
- **Domain**: $n \in \mathbb{N}^+$.
- **Uniqueness of solution**: The entire sequence is uniquely determined by the leading term and the recursion relationship.

## Method selection
**Preferred method**: Characteristic equation method (undetermined coefficient method), which converts non-homogeneous recursion into homogeneous recursion solution by constructing a geometric sequence. The core idea: Find a constant $\lambda$ to make $a_{n+1} + \lambda = p(a_n + \lambda)$, then $\{a_n + \lambda\}$ is a geometric sequence.

**Alternative method**: iterative expansion method, from $a_n$ to $a_1$ item by item; generating function method. The characteristic equation method is the most concise and efficient.

## Problem solving process

### Step 1: Find the general term $a_n$

Suppose there is a constant $\lambda$ such that:

 $$a_{n+1} + \lambda = 2(a_n + \lambda)$$

Expand the right side: $a_{n+1} + \lambda = 2a_n + 2\lambda$

Compare with the original recursion $a_{n+1} = 2a_n + 3$:

 $$\lambda = 2\lambda - 3 \quad \Rightarrow \quad \lambda = 3$$

therefore:

 $$a_{n+1} + 3 = 2(a_n + 3)$$

This shows that the sequence $\{a_n + 3\}$ is a geometric sequence whose common ratio is $2$.

Find the first term of $\{a_n + 3\}$:

 $$a_1 + 3 = 1 + 3 = 4$$

so:

 $$a_n + 3 = 4 \cdot 2^{n-1} = 2^{n+1}$$

 $$a_n = 2^{n+1} - 3 \quad (n \in \mathbb{N}^+)$$

### Step 2: Find the first $n$ items and $S_n$

 $$S_n = \sum_{k=1}^n a_k = \sum_{k=1}^n (2^{k+1} - 3) = \sum_{k=1}^n 2^{k+1} - \sum_{k=1}^n 3$$

The first term is the sum of the geometric sequence (first term $2^2 = 4$ , common ratio $2$ , number of terms $n$ ):

 $$\sum_{k=1}^n 2^{k+1} = 4 \cdot \frac{2^n - 1}{2 - 1} = 4(2^n - 1) = 2^{n+2} - 4$$

The second term is a constant series:

 $$\sum_{k=1}^n 3 = 3n$$

therefore:

 $$S_n = (2^{n+2} - 4) - 3n = 2^{n+2} - 3n - 4$$

## Check calculation

### Method 1: Verify item by item

Calculate $a_1, a_2, a_3$ through the general formula, and then cross-validate through the recursive formula.

| $n$ | General term $a_n = 2^{n+1} - 3$ | Recursion $a_{n} = 2a_{n-1} + 3$ |
|-----|---------------------------|------------------------------|
| 1 | $2^2 - 3 = 4 - 3 = 1$ | (known as $a_1 = 1$ ) |
| 2   |  $2^3 - 3 = 8 - 3 = 5$      |  $2 \cdot 1 + 3 = 5$           |
| 3   |  $2^4 - 3 = 16 - 3 = 13$     |  $2 \cdot 5 + 3 = 13$          |

All consistent.

### Method 2: Substitution verification

Substitute $a_n = 2^{n+1} - 3$ into the original recursion:

 $$a_{n+1} = 2^{(n+1)+1} - 3 = 2^{n+2} - 3$$

 $$2a_n + 3 = 2(2^{n+1} - 3) + 3 = 2^{n+2} - 6 + 3 = 2^{n+2} - 3$$

Left side = right side, the recursion holds.

### Method 3: First $n$ items and verification

$n = 1$ : $S_1 = a_1 = 1$ , the formula gives $2^{3} - 3 \cdot 1 - 4 = 8 - 3 - 4 = 1$ . ✓

$n = 2$ : $S_2 = 1 + 5 = 6$ , the formula gives $2^{4} - 3 \cdot 2 - 4 = 16 - 6 - 4 = 6$ . ✓

$n = 3$ : $S_3 = 1 + 5 + 13 = 19$ , the formula gives $2^{5} - 3 \cdot 3 - 4 = 32 - 9 - 4 = 19$ . ✓

## Final answer

 $$\boxed{a_n = 2^{n+1} - 3 \quad (n \in \mathbb{N}^+)}$$

 $$\boxed{S_n = 2^{n+2} - 3n - 4 \quad (n \in \mathbb{N}^+)}$$

## Easy to make mistakes
1. **Undetermined coefficient solution $\lambda$ **: The equation is $\lambda = p\lambda - q$ instead of $\lambda = p\lambda + q$, pay attention to the sign.
2. **Relationship between $\lambda$ and $p\lambda - q$**: When deriving $\lambda = 2\lambda - 3$, $\lambda$ in the $\lambda = a_{n+1} + \lambda$ equation is both an unknown variable and appears on both sides, so don’t get confused.
3. **Sum of geometric sequence**: When finding $\sum 2^{k+1}$, the first term is not $2$ but $2^2 = 4$, the common ratio is $2$, and the number of terms is $n$, not $n-1$.
4. **Special case of $p = 1$**: When $p = 1$ (such as $a_{n+1} = a_n + 3$), this method cannot be used to construct a geometric sequence, and it should be processed directly with an arithmetic sequence.
