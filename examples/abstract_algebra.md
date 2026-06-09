# Group theory - Proof of commutativity of second-order elements

## User input
Let     $G$     be a group. Proof: If for any     $g \in G$     there is     $g^2 = e$     (where     $e$     is the identity element), then     $G$     is an Abelian group (that is, a commutative group).

## Skill Category
abstract algebra

## Question meaning analysis
- **Known conditions**:     $G$     is a group, and     $\forall g \in G$     ,     $g^2 = e$     . This means that the order of each non-identical element is     $2$     (or     $1$     , only the identity element is     $1$     ).
- **Lemma**:     $g = g^{-1}$     can be obtained from     $g^2 = e$     (each element is its own inverse).
- **Solution Objective**: Prove that     $G$     is a commutative group, that is,     $\forall a, b \in G$    ,     $ab = ba$    .
- **Structural Implication**: A finite group that satisfies this condition must be the direct product of several     $\mathbb{Z}_2$     (or elementary Abel     $2$     -group).
- **Implicit condition**:     $G$     is a group, so it satisfies the associative law, the existence of identity elements, and the existence of inverse elements.

## Method selection
**Preferred method**: direct algebraic deduction. Starting from     $(ab)^2 = e$    , use the associative law and the properties of     $g = g^{-1}$     to expand and derive     $ab = ba$    .

**Alternative**: Use     $g = g^{-1}$     to relate     $ab$     to its inverse     $b^{-1}a^{-1}$    .

**Key Insight**:     $g^2 = e \iff g = g^{-1}$     . For any     $a, b \in G$     , consider     $(ab)^{-1}$     . Because     $(ab)^{-1} = b^{-1}a^{-1}$     (the inverse product rule of the group), and     $a = a^{-1}$     ,     $b = b^{-1}$     , so     $(ab)^{-1} = b^{-1}a^{-1} = ba$     . On the other hand,     $(ab)^2 = e$     means     $(ab)^{-1} = ab$     . Lianli got     $ab = ba$    .

## Problem solving process

### Official certification

**Step 1**: Based on the condition     $g^2 = e$    , for any     $g \in G$    , there is:

     $$g^{-1} = g$$

Because     $g \cdot g = e$     means     $g$     has itself as its inverse.

**Step 2**: Take any     $a, b \in G$     and consider their product     $ab$     .

    $(ab)^2 = e$     (the question condition applies to all group elements, including the product     $ab$    ), so according to step 1:

     $$(ab)^{-1} = ab \quad \cdots \quad (1)$$

**Step 3**: On the other hand, the inverse of the product in the group satisfies:

     $$(ab)^{-1} = b^{-1}a^{-1}$$

Using step 1,     $a^{-1} = a$     and     $b^{-1} = b$     are therefore:

     $$(ab)^{-1} = ba \quad \cdots \quad (2)$$

**Step 4**: From (1) and (2):

     $$ab = (ab)^{-1} = ba$$

That is, any     $a, b \in G$     satisfies the commutative law.     $\square$

### Alternative proof (expansion method)

From     $(ab)^2 = e$    :

     $$(ab)(ab) = e$$

Multiply both sides by     $a$     on the left and     $b$     on the right:

     $$a(abab)b = aeb = ab$$

     $$(aa)ba(bb) = ab$$

    $aa = e$     is obtained from     $a^2 = e$    , and     $bb = e$     is obtained from     $b^2 = e$    :

     $$e \cdot ba \cdot e = ab$$

     $$ba = ab$$

     $\square$

The two proof methods are essentially the same, but the expansion method more intuitively displays the group axioms used in each step.

## Check calculation

### Method 1: Group axiom review of proof steps

Check the group axioms used at each step line by line:

| Steps | Properties used in the operation |
|------|---------------|
|     $g^2 = e \Rightarrow g = g^{-1}$     | Definition of inverse element (if     $ab = e$    , then     $b = a^{-1}$    ) |
|     $(ab)^2 = e$     (conditional application) | Precondition: for all     $g \in G$     is true, take     $g = ab$     |
|     $(ab)^{-1} = b^{-1}a^{-1}$     | The product inverse rule of the group (can be deduced from the associative law) |
|     $a^{-1} = a$    ,     $b^{-1} = b$     | Conclusion of step 1 |
|     $(ab)^{-1} = ba$     | Substitute into step 3 |
|     $ab = ba$     | Passed by (1) and (2) equal sign |

Each step is based on group axioms or proven conclusions, and the logical chain is complete. ✓

### Method 2: Verification with specific examples

**Example 1**:     $G = \mathbb{Z}_2 = \{0, 1\}$     (modulo 2 additive group).

    $0 + 0 = 0$    ,     $1 + 1 = 0 \pmod{2}$    , satisfy     $g + g = 0$    . And     $\mathbb{Z}_2$     is a swap group. ✓

**Example 2**:     $G = \mathbb{Z}_2 \times \mathbb{Z}_2 = \{(0,0), (0,1), (1,0), (1,1)\}$     (Klein Quaternary Group).

Each element plus itself gets     $(0,0)$     (unit yuan), which satisfies the condition. verify:

     $$(0,1) + (1,0) = (1,1),\quad (1,0) + (0,1) = (1,1)$$

Commutativity is established. ✓

**Example 3**:     $G = S_3$     (cubic symmetry group).     $(12)^2 = e$     is established but     $(123)^2  = (132) \neq e$     , does not satisfy the condition and commutativity is not established. ✓

### Method 3: Check whether commutativity is implicitly assumed

Key checkpoint: In the expansion proof, steps

     $$a(abab)b = (aa)ba(bb)$$

Use **associative law** to rearrange the brackets:     $a((ab)(ab))b = (a(ab))((ab)b) = ((aa)b)(a(bb))$     . This is perfectly legal and does not involve commutativity.

No assumptions like     $ab = ba$     are used in the proof earlier. ✓

## Final answer

$$\boxed{\forall a, b \in G: ab = ba \quad \text{(i.e. $G$ is an Abelian group)}}$$

## Easy to make mistakes
1. **Two representations of     $(ab)^{-1}$    **: The key equation     $(ab)^{-1} = ab$     comes from the condition     $g^2 = e$    , while     $(ab)^{-1} = b^{-1}a^{-1}$     comes from the general properties of the group. Connecting the two is the core skill of this question.
2. **Reverse element order**:     $(ab)^{-1} = b^{-1}a^{-1}$    , not     $a^{-1}b^{-1}$     (unless the group is already a commutative group). Beginners often reverse the order.
3. **     $g^2 = e$     does not mean     $g = e$     **:     $g^2 = e$     only indicates that the order of     $g$     is     $1$     or     $2$    , and does not mean     $g = e$    . For example, in addition to the identity element, there are three non-trivial elements satisfying     $g^2 = e$     in the Klein quaternion group.
4. **Inference of finiteness**: It can be deduced from the condition that if     $G$     is finite, then     $|G|$     is a power of 2. But the proof of commutativity does not require     $G$     to be finite - the result holds for any group, including infinite groups.
