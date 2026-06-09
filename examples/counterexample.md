# Counterexample construction: Differentiable but the derivative is discontinuous

## User input
Someone asserts: "If function $f$ is differentiable on the open interval $(a, b)$, then its derivative function $f'$ is continuous on $(a, b)$." Please determine whether this assertion is correct.

## Skill Category
Real analysis/counterexample construction

## Question meaning analysis
- **Assertion**: Differentiable $\implies$ derivative is continuous
- **Goal**: Determine authenticity; if false, construct a counterexample
- **Conditions to be checked**:
1. The function is differentiable at every point in the domain
2. The derivative function is discontinuous at a certain point (the limit does not exist or the limit is not equal to the function value)
- **Common cognitive bias**: Many beginners mistakenly believe that the derivative of a differentiable function "should" be continuous, but differentiability only guarantees the continuity of the function itself, not the continuity of the derivative.
- **Multiplicity of Solutions**: Counterexamples are not unique, but classic counterexamples have the most teaching value

## Method selection
Use the **Construction of Counterexample Method** to construct a function that is differentiable everywhere but has a discontinuous derivative at one point. The classic counterexample is:

 $$f(x) = \begin{cases} x^2 \sin(1/x), & x \neq 0 \\ 0, & x = 0 \end{cases}$$

The reason for choosing this example: $x^2$ provides differentiability (the square term is differentiable at the zero point), $\sin(1/x)$ provides derivative oscillation (leading to discontinuity), and the positive multiplication of the two is clever.

## Problem solving process

**Assertion: False. Differentiability does not imply continuity of derivatives. **

### Constructing counterexamples

Define function $f: \mathbb{R} \to \mathbb{R}$:

 $$f(x) = \begin{cases} x^2 \sin\left(\dfrac{1}{x}\right), & x \neq 0 \\[12pt] 0, & x = 0 \end{cases}$$

### Step 1: Prove that $f$ is derivable at $x \neq 0$

When $x \neq 0$, $f(x)$ is the product of differentiable functions $x^2$ and $\sin(1/x)$ (the composite function is differentiable, because $\sin$ is differentiable everywhere and $1/x$ is differentiable at $x \neq 0$), according to the product rule:

 $$f'(x) = 2x \cdot \sin\left(\frac{1}{x}\right) + x^2 \cdot \cos\left(\frac{1}{x}\right) \cdot \left(-\frac{1}{x^2}\right)$$

 $$f'(x) = 2x \sin\left(\frac{1}{x}\right) - \cos\left(\frac{1}{x}\right), \quad x \neq 0$$

### Step 2: Prove that $f$ is derivable at $x = 0$

Defined by the derivative:

 $$f'(0) = \lim_{h \to 0} \frac{f(0 + h) - f(0)}{h} = \lim_{h \to 0} \frac{h^2 \sin(1/h) - 0}{h} = \lim_{h \to 0} h \cdot \sin\left(\frac{1}{h}\right)$$

Since $\left|\sin(1/h)\right| \leq 1$ , there is $0 \leq |h \cdot \sin(1/h)| \leq |h|$ , by squeeze theorem,

 $$\lim_{h \to 0} h \cdot \sin\left(\frac{1}{h}\right) = 0$$

Hence $f'(0) = 0$ . $f$ is derivable at $x = 0$.

### Step 3: Prove that $f'$ is discontinuous at $x = 0$

To prove that $f'$ is discontinuous at $x = 0$, you need to prove that $\lim_{x \to 0} f'(x)$ does not exist (or exists but is not equal to $f'(0) = 0$).

Examine $f'(x) = 2x\sin(1/x) - \cos(1/x)$ ( $x \neq 0$ ):

- The first term $\lim_{x \to 0} 2x\sin(1/x) = 0$ (pinch theorem)
- The second item $\lim_{x \to 0} \cos(1/x)$ **does not exist**

When $x \to 0$, $1/x \to \infty$, $\cos(1/x)$ oscillate infinitely between $[-1, 1]$, the limit does not exist.

For example: take the sequence $x_n = \frac{1}{2n\pi}$, then $\cos(1/x_n) = \cos(2n\pi) = 1$, $f'(x_n) \to -1$.
Take the sequence $x_n = \frac{1}{(2n+1)\pi}$, then $\cos(1/x_n) = \cos((2n+1)\pi) = -1$, $f'(x_n) \to 1$.

The two subsequences tend to different limits, so $\lim_{x \to 0} f'(x)$ does not exist.

**Conclusion**: $f'$ is discontinuous at $x = 0$ (not even the limit exists), but $f$ is differentiable at $x = 0$. The original assertion was falsified.

## Check calculation

**Verification method 1: Verify the calculation of $f'(0)$**

 $$\lim_{h \to 0} \frac{h^2 \sin(1/h)}{h} = \lim_{h \to 0} h \sin\left(\frac{1}{h}\right)$$

Pinch theorem: $-|h| \leq h\sin(1/h) \leq |h|$, when $h \to 0$, both ends tend to $0$, so the limit is $0$ ✓

**Check calculation method 2: Verify the derivation of the derivative formula**

For $x \neq 0$ :
 $$f'(x) = \frac{d}{dx}[x^2] \cdot \sin(1/x) + x^2 \cdot \frac{d}{dx}[\sin(1/x)]$$
 $$= 2x \cdot \sin(1/x) + x^2 \cdot \cos(1/x) \cdot (-1/x^2)$$
 $$= 2x\sin(1/x) - \cos(1/x)$$

The derivation is correct ✓

**Check method 3: Verify the discontinuity of $f'$ - two-point sequence method**

- Sequence $x_n^{(1)} = 1/(2n\pi)$ : $f'(x_n^{(1)}) = \frac{2}{2n\pi}\sin(2n\pi) - \cos(2n\pi) = 0 - 1 = -1$
- Sequence $x_n^{(2)} = 1/((2n+1)\pi)$ : $f'(x_n^{(2)}) = \frac{2}{(2n+1)\pi}\sin((2n+1)\pi) - \cos((2n+1)\pi) = 0 - (-1) = 1$

$\lim_{n \to \infty} f'(x_n^{(1)}) = -1$, $\lim_{n \to \infty} f'(x_n^{(2)}) = 1$, the two limits are not equal, $\lim_{x \to 0} f'(x)$ does not exist ✓

**Check method 4: Complete list to confirm the validity of counterexamples**

| Check items | Results |
|--------|------|
| $f$ is differentiable in $x \neq 0$ | ✓ Product and composition of elementary functions |
| $f$ is differentiable from $x = 0$ | ✓ $f'(0) = 0$ |
| The expression of $f'$ in $x \neq 0$ is correct | ✓ Derivative verified |
| $\lim_{x \to 0} f'(x)$ does not exist | ✓ Sequence method proof |
| Therefore $f'$ is discontinuous at $x=0$ | ✓ |

## Final answer

The original assertion was **wrong**. Counterexample: function

 $$f(x) = \begin{cases} x^2 \sin(1/x), & x \neq 0 \\ 0, & x = 0 \end{cases}$$

It is derivable everywhere, $f'(0) = 0$, but $\lim_{x \to 0} f'(x)$ does not exist, so $f'$ is not continuous in $x=0$.

## Easy to make mistakes
1. **Confusing conditions and conclusions**: Differentiable $\implies$ $f$ is continuous, but the continuity of the derivative requires additional conditions (such as $f$ belongs to the $C^1$ class)
2. **Mistake on the particularity of the counterexample**: This counterexample is not a "pathological" boundary situation, but a classic counterexample in standard textbooks, which profoundly illustrates the gap between "differentiable" and "derivative continuous"
3. **Conditions of the pinch theorem**: When using the pinch theorem to find $f'(0)$, you need to confirm that $\sin(1/h)$ is indeed bounded ($|\sin(\cdot)| \leq 1$). This is the key to correct use.
4. **Determination of the non-existence of the limit**: It cannot be concluded that the limit does not exist based on "oscillation" alone. It is necessary to strictly construct two subsequences tending to different limits.
5. **Don’t overgeneralize**: Although there are counterexamples, Darboux’s theorem guarantees that the derivative has intermediate properties—even if the derivative is discontinuous, it cannot have the first type of discontinuity.
