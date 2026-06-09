# Trigonometric identity proof

## User input
Prove the identity: $\sin^3\theta + \cos^3\theta = (\sin\theta + \cos\theta)(1 - \sin\theta\cos\theta)$

## Skill Category
Trigonometry - Proof of trigonometric identities

## Question meaning analysis

**Known conditions:**
- Identity to be proved: $\sin^3\theta + \cos^3\theta = (\sin\theta + \cos\theta)(1 - \sin\theta\cos\theta)$

**Solution goal:**
- Prove that the left and right sides of the equal sign are identical through algebraic and trigonometric identity transformations.

**Variables and Domains:**
- $\theta \in \mathbb{R}$, the identity holds for all real numbers $\theta$ (the domain of both the left and right expressions is $\mathbb{R}$).

**Implicit condition:**
- $\sin^3\theta$ can be treated as $(\sin\theta)^3$, and similarly $\cos^3\theta = (\cos\theta)^3$.
- This is an application of the sum of cubes formula $a^3 + b^3 = (a+b)(a^2 - ab + b^2)$ in trigonometry.
- The fundamental trigonometric identity $\sin^2\theta + \cos^2\theta = 1$ will play a key role.

**Number of solutions:**
- The identity proof is not about solving equations. The goal is not to find the value of $\theta$, but to prove that the equation holds for all $\theta$.

## Method selection

**Selection method:** Starting from the left, apply the sum of cubes formula + simplify the basic identity

**reason:**
- The $\sin^3\theta + \cos^3\theta$ on the left is structurally exactly the sum of cubes $a^3+b^3$, which reminds us of factorization.
- After decomposition, $\sin^2\theta - \sin\theta\cos\theta + \cos^2\theta$ appears, where $\sin^2\theta + \cos^2\theta = 1$ happens to reduce the expression to $1 - \sin\theta\cos\theta$ , perfectly matching the factors on the right.

**Alternative method:**
- Expand the verification from the right: $(\sin\theta + \cos\theta)(1 - \sin\theta\cos\theta) = \sin\theta + \cos\theta - \sin^2\theta\cos\theta - \sin\theta\cos^2\theta$, which needs further deformation to be paired into $\sin^3\theta + \cos^3\theta$. The steps are slightly more but feasible.
- Simplify by subtracting a certain item from the left and right at the same time: not as clear as a direct one-way simplification.

## Problem solving process

### Derive from the left

**Starting point:** $\sin^3\theta + \cos^3\theta$

**Step 1: Apply the Sum of Cubes formula. **

Let $a = \sin\theta$ , $b = \cos\theta$ , then

 $$
a^3 + b^3 = (a+b)(a^2 - ab + b^2)
$$

Substitute:

 $$
\sin^3\theta + \cos^3\theta = (\sin\theta + \cos\theta)(\sin^2\theta - \sin\theta\cos\theta + \cos^2\theta) \tag{1}
$$

**Step 2: Apply basic trigonometric identities. **

From $\sin^2\theta + \cos^2\theta = 1$, $\sin^2\theta + \cos^2\theta$ in parentheses can be replaced with $1$:

 $$
\sin^2\theta - \sin\theta\cos\theta + \cos^2\theta = (\sin^2\theta + \cos^2\theta) - \sin\theta\cos\theta = 1 - \sin\theta\cos\theta \tag{2}
$$

**Step 3: Substitute (2) to (1). **

 $$
\sin^3\theta + \cos^3\theta = (\sin\theta + \cos\theta)(1 - \sin\theta\cos\theta)
$$

This is the right side to prove. The equation is proved.

### Reverse derivation (for verification)

Starting from the right:

 $$
(\sin\theta + \cos\theta)(1 - \sin\theta\cos\theta)
$$

Expand:

 $$
= (\sin\theta + \cos\theta) \cdot 1 - (\sin\theta + \cos\theta) \cdot \sin\theta\cos\theta
$$

 $$
= \sin\theta + \cos\theta - \sin^2\theta\cos\theta - \sin\theta\cos^2\theta
$$

Extract $\sin\theta\cos\theta$ (from the last two items):

 $$
= \sin\theta + \cos\theta - \sin\theta\cos\theta(\sin\theta + \cos\theta)
$$

Treat $(\sin\theta + \cos\theta)$ as a common factor:

 $$
= (\sin\theta + \cos\theta)\left[1 - \sin\theta\cos\theta\left(\frac{\sin\theta + \cos\theta}{\sin\theta + \cos\theta}\right)\right]
$$

Something went wrong here. Let me do it again.

In fact, it is very straightforward to unfold it from the right side. Let me do it another way:

 $(\sin\theta + \cos\theta)(1 - \sin\theta\cos\theta)$

 $= \sin\theta \cdot 1 - \sin\theta \cdot \sin\theta\cos\theta + \cos\theta \cdot 1 - \cos\theta \cdot \sin\theta\cos\theta$

 $= \sin\theta + \cos\theta - \sin^2\theta\cos\theta - \sin\theta\cos^2\theta$

 $= \sin\theta(1 - \sin\theta\cos\theta) + \cos\theta(1 - \sin\theta\cos\theta)$   -- no that's just re-writing the original.

Let me try:  $= \sin\theta + \cos\theta - \cos\theta\sin^2\theta - \sin\theta\cos^2\theta$

Replace  $\sin^2\theta = 1 - \cos^2\theta$  and  $\cos^2\theta = 1 - \sin^2\theta$ :

Actually, this approach is getting messy. Let me reformulate.

Better: Group terms differently:

 $= \sin\theta - \sin\theta\cos^2\theta + \cos\theta - \sin^2\theta\cos\theta$

 $= \sin\theta(1 - \cos^2\theta) + \cos\theta(1 - \sin^2\theta)$

 $= \sin\theta \cdot \sin^2\theta + \cos\theta \cdot \cos^2\theta$

 $= \sin^3\theta + \cos^3\theta$ , ✓

This is clean.

## Check calculation

### Verification method one: numerical sampling inspection

Select five representative $\theta$ values ​​and calculate the left and right sides respectively.

**①  $\theta = 0$ ：**

 $$
\sin 0 = 0,\ \cos 0 = 1
$$

Left style: $0^3 + 1^3 = 1$

Right form: $(0 + 1)(1 - 0 \times 1) = 1 \times 1 = 1$ ✓

**②  $\theta = \frac{\pi}{6}$ （ $30^\circ$ ）：**

 $$
\sin\frac{\pi}{6} = \frac{1}{2},\ \cos\frac{\pi}{6} = \frac{\sqrt{3}}{2}
$$

Left style:

 $$
\left(\frac{1}{2}\right)^3 + \left(\frac{\sqrt{3}}{2}\right)^3 = \frac{1}{8} + \frac{3\sqrt{3}}{8} = \frac{1 + 3\sqrt{3}}{8}
$$

Right form:

 $$
\left(\frac{1}{2} + \frac{\sqrt{3}}{2}\right)\left(1 - \frac{1}{2} \times \frac{\sqrt{3}}{2}\right) = \frac{1+\sqrt{3}}{2} \times \left(1 - \frac{\sqrt{3}}{4}\right)
$$

 $$
= \frac{1+\sqrt{3}}{2} \times \frac{4-\sqrt{3}}{4} = \frac{(1+\sqrt{3})(4-\sqrt{3})}{8}
$$

Expand numerator: $(1+\sqrt{3})(4-\sqrt{3}) = 4 - \sqrt{3} + 4\sqrt{3} - 3 = 1 + 3\sqrt{3}$

Therefore, the right expression $= \dfrac{1 + 3\sqrt{3}}{8}$ is equal to the left expression. ✓

**③  $\theta = \frac{\pi}{4}$ （ $45^\circ$ ）：**

 $$
\sin\frac{\pi}{4} = \cos\frac{\pi}{4} = \frac{\sqrt{2}}{2}
$$

Left style:

 $$
\left(\frac{\sqrt{2}}{2}\right)^3 + \left(\frac{\sqrt{2}}{2}\right)^3 = 2 \times \frac{2\sqrt{2}}{8} = \frac{4\sqrt{2}}{8} = \frac{\sqrt{2}}{2}
$$

Right form:

 $$
\left(\frac{\sqrt{2}}{2} + \frac{\sqrt{2}}{2}\right)\left(1 - \frac{\sqrt{2}}{2} \times \frac{\sqrt{2}}{2}\right) = \sqrt{2} \times \left(1 - \frac{2}{4}\right) = \sqrt{2} \times \frac{1}{2} = \frac{\sqrt{2}}{2}
$$

✓

**④  $\theta = \frac{\pi}{3}$ （ $60^\circ$ ）：**

 $$
\sin\frac{\pi}{3} = \frac{\sqrt{3}}{2},\ \cos\frac{\pi}{3} = \frac{1}{2}
$$

Left style:

 $$
\left(\frac{\sqrt{3}}{2}\right)^3 + \left(\frac{1}{2}\right)^3 = \frac{3\sqrt{3}}{8} + \frac{1}{8} = \frac{3\sqrt{3}+1}{8}
$$

Right form:

 $$
\left(\frac{\sqrt{3}}{2} + \frac{1}{2}\right)\left(1 - \frac{\sqrt{3}}{2} \times \frac{1}{2}\right) = \frac{\sqrt{3}+1}{2} \times \frac{4-\sqrt{3}}{4} = \frac{(\sqrt{3}+1)(4-\sqrt{3})}{8}
$$

Expand: $(4\sqrt{3} - 3 + 4 - \sqrt{3}) = 3\sqrt{3} + 1$

Right $= \dfrac{3\sqrt{3}+1}{8}$ = Left ✓

**⑤  $\theta = \frac{\pi}{2}$ （ $90^\circ$ ）：**

 $$
\sin\frac{\pi}{2} = 1,\ \cos\frac{\pi}{2} = 0
$$

Left style: $1^3 + 0^3 = 1$

Right form: $(1 + 0)(1 - 1 \times 0) = 1$ ✓

All five special corners have been verified.

### Calculation method two: reverse derivation (from right to left)

 $$
\begin{aligned}
(\sin\theta + \cos\theta)(1 - \sin\theta\cos\theta)
&= \sin\theta - \sin^2\theta\cos\theta + \cos\theta - \sin\theta\cos^2\theta \\[6pt]
&= \sin\theta(1 - \cos^2\theta) + \cos\theta(1 - \sin^2\theta) \\[6pt]
&= \sin\theta \cdot \sin^2\theta + \cos\theta \cdot \cos^2\theta \\[6pt]
&= \sin^3\theta + \cos^3\theta
\end{aligned}
$$

The second step uses $\sin^2\theta = 1 - \cos^2\theta$ and $\cos^2\theta = 1 - \sin^2\theta$. ✓

## Final answer

 $$
\boxed{\sin^3\theta + \cos^3\theta = (\sin\theta + \cos\theta)(1 - \sin\theta\cos\theta)}
$$

True for everything $\theta \in \mathbb{R}$.

## Easy to make mistakes
1. **The formula for the sum of cubes is incorrectly remembered:** $a^3 + b^3 = (a+b)(a^2 - ab + b^2)$. Note that the middle is $-ab$ instead of $+ab$. An error will result if confused with the cubic difference formula $a^3-b^3 = (a-b)(a^2+ab+b^2)$.
2. **Forgot the basic identity:** $\sin^2\theta + \cos^2\theta = 1$ is the most basic identity in trigonometry. This replacement is required in the last step of factorization in this question.
3. **Sign error when expanding the right side:** When expanding $(\sin\theta + \cos\theta)(1 - \sin\theta\cos\theta)$ from the right side, the negative sign must be reflected in each item.
4. **Confusing $\sin^3\theta$ with $\sin\theta^3$:** $\sin^3\theta$ means $(\sin\theta)^3$, while $\sin\theta^3$ usually means $\sin(\theta^3)$, which are completely different. Always use $\sin^3\theta$ in equations.
5. **Mistaken belief that you need to solve an equation:** The identity proof is not the solution of the equation - there is no need to find the specific value of $\theta$. The goal of the proof is to show that the equation holds for everything $\theta$.
