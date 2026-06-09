# Calculation of angles of isosceles triangle

## User input
In     $\triangle ABC$     ,     $AB = AC$     , point     $D$     is on edge     $BC$     . Given     $\angle BAD = 30^\circ$    ,     $\angle CAD = 20^\circ$    , find     $\angle B$    .

## Skill Category
Geometry—triangle angle calculation

## Question meaning analysis

**Known conditions:**
-     $\triangle ABC$     is an isosceles triangle,     $AB = AC$     (both sides are equal)
- point     $D$     on edge     $BC$
-     $\angle BAD = 30^\circ$     (the angle between rays     $AD$     and     $AB$    )
-     $\angle CAD = 20^\circ$     (the angle between rays     $AD$     and     $AC$    )

**Graphic structure (text description):**

     ```
        A
       /|\
      / | \
     /  |  \
    /30°|20°\
   /    |    \
  /     D     \
 /      |      \
B-------+-------C
```

Ray     $AD$     starts from vertex     $A$     and passes through point     $D$     on the edge of     $BC$    , dividing     $\angle A$     into     $\angle BAD = 30^\circ$     and     $\angle CAD = 20^\circ$    .

**Solution goal:**
- Degree of     $\angle B$    .

**Implicit condition:**
- Point     $D$     is on edge     $BC$    , meaning     $AD$     is a line segment inside     $\angle A$    , dividing     $\angle A$     into two parts. Hence     $\angle A = \angle BAD + \angle CAD = 30^\circ + 20^\circ = 50^\circ$     .
-     $AB = AC$     means     $\angle B = \angle C$     (the base angles of an isosceles triangle are equal).
- The sum of the interior angles of a triangle is     $180^\circ$    .

**Number of solutions:**
- The angle value is uniquely determined.

## Method selection

**Selection method:** Isosceles triangle properties + triangle interior angle sum theorem

**reason:**
- The key to solving the problem is to use     $AB = AC$     to get the properties of     $\angle B = \angle C$    .
- Express     $\angle A$     as the sum of two known angles by passing     $D$     on     $BC$     .
- Then use the sum of interior angles theorem to find     $\angle B$    .

**Alternative method:**
- Sine theorem method: set the length of one side and solve the triangle using known angles - although feasible, it is too complex for pure angle calculations.
- Coordinate geometry method: establish coordinate system calculation - suitable as a verification method, not suitable as the main solution method.

## Problem solving process

### Step one: Ask for     $\angle A$

Since     $D$     is on edge     $BC$     and ray     $AD$     is inside     $\angle A$     , split     $\angle A$     into     $\angle BAD$     and     $\angle CAD$     :

     $$
\angle A = \angle BAD + \angle CAD = 30^\circ + 20^\circ = 50^\circ
$$

### Step 2: Use the properties of isosceles triangles

Because     $AB = AC$     , according to the "equilateral opposite angles" property:

     $$
\angle B = \angle C
$$

### Step 3: Apply the triangle interior angle sum theorem

The sum of the three interior angles of a triangle is     $180^\circ$    :

     $$
\angle A + \angle B + \angle C = 180^\circ
$$

Substitute     $\angle C = \angle B$     and     $\angle A = 50^\circ$     :

     $$
50^\circ + \angle B + \angle B = 180^\circ
$$

     $$
50^\circ + 2\angle B = 180^\circ
$$

     $$
2\angle B = 180^\circ - 50^\circ = 130^\circ
$$

     $$
\angle B = 65^\circ
$$

Hence     $\angle B = \angle C = 65^\circ$     .

### Step 4: Verify geometric rationality

Check that all known conditions are met:

-      $\angle A + \angle B + \angle C = 50^\circ + 65^\circ + 65^\circ = 180^\circ$      ✓
-      $\angle BAD + \angle CAD = 30^\circ + 20^\circ = 50^\circ = \angle A$      ✓
-     $D$     on     $BC$     : on     $\triangle ABD$     ,     $\angle B = 65^\circ$     ,     $\angle BAD = 30^\circ$     , then     $\angle ADB = 180^\circ - 65^\circ - 30^\circ = 85^\circ$     . In     $\triangle ADC$     ,     $\angle C = 65^\circ$     ,     $\angle CAD = 20^\circ$     , then     $\angle ADC = 180^\circ - 65^\circ - 20^\circ = 95^\circ$     .     $\angle ADB + \angle ADC = 85^\circ + 95^\circ = 180^\circ$    , indicating that     $B$    ,     $D$    ,     $C$     are three points collinear ✓

## Check calculation

### Calculation method one: interior angle sum consistency test

Divide     $D$     into two small triangles and calculate the interior angle sum respectively:

**In     $\triangle ABD$    :**

     $$
\angle BAD + \angle B + \angle ADB = 30^\circ + 65^\circ + \angle ADB = 180^\circ
$$

     $$
\angle ADB = 180^\circ - 95^\circ = 85^\circ
$$

**In     $\triangle ADC$    :**

     $$
\angle CAD + \angle C + \angle ADC = 20^\circ + 65^\circ + \angle ADC = 180^\circ
$$

     $$
\angle ADC = 180^\circ - 85^\circ = 95^\circ
$$

**Verify that the three points are collinear:**     $\angle ADB$     and     $\angle ADC$     are adjacent supplementary angles on both sides of     $AD$    .

     $$
\angle ADB + \angle ADC = 85^\circ + 95^\circ = 180^\circ
$$

    $B$    ,     $D$    ,     $C$     are collinear, satisfying the condition that     $D$     is on     $BC$    . ✓

### Calculation method two: coordinate geometry method

Establish a coordinate system and verify it numerically.

Taking     $A$     as the origin     $(0, 0)$     , let     $AB = AC = 1$     (without loss of generality, since similar triangles have the same angles). Place ray     $AB$     on the positive axis of     $x$    :

-      $B$     ：     $(1, 0)$
-      $A$     ：     $(0, 0)$

Since     $\angle A = 50^\circ$     and     $AC = 1$     , the coordinates of point     $C$     are:

     $$
C = (\cos 50^\circ,\ \sin 50^\circ) \approx (0.6428,\ 0.7660)
$$

Point     $D$     is on     $BC$     and     $\angle BAD = 30^\circ$     . The direction angle of ray     $AD$     is     $30^\circ$     :

     $$
AD \text{ Direction vector: }(\cos 30^\circ,\ \sin 30^\circ) = \left(\frac{\sqrt{3}}{2},\ \frac{1}{2}\right) \approx (0.8660,\ 0.5000)
$$

    $D$     is the intersection of     $AD$     and     $BC$    .

Straight line     $BC$     passes through     $B(1,0)$     and     $C(0.6428, 0.7660)$    , parametric equation:

     $$
BC: (1, 0) + t[(0.6428, 0.7660) - (1, 0)] = (1 - 0.3572t,\ 0.7660t),\quad 0 \leq t \leq 1
$$

Line     $AD$     Equation:     $(s \cos 30^\circ,\ s \sin 30^\circ) = (0.8660s,\ 0.5000s),\ s \geq 0$

Let two points coincide and find the intersection point:

     $$
\begin{cases}
0.8660s = 1 - 0.3572t \\
0.5000s = 0.7660t
\end{cases}
$$

From this, the     $D$     point position can be solved (numerical verification can be obtained on     $BC$    ).

Calculate     $\angle B$    : the angle between vectors     $\overrightarrow{BA}$     and     $\overrightarrow{BC}$    .

     $$
\overrightarrow{BA} = (0-1,\ 0-0) = (-1,\ 0)
$$
     $$
\overrightarrow{BC} = (0.6428-1,\ 0.7660-0) = (-0.3572,\ 0.7660)
$$

     $$
\cos \angle B = \frac{\overrightarrow{BA} \cdot \overrightarrow{BC}}{|\overrightarrow{BA}| \cdot |\overrightarrow{BC}|} = \frac{(-1)(-0.3572) + 0 \times 0.7660}{1 \times \sqrt{0.3572^2 + 0.7660^2}}
$$

     $$
= \frac{0.3572}{\sqrt{0.1276 + 0.5868}} = \frac{0.3572}{\sqrt{0.7144}} \approx \frac{0.3572}{0.8452} \approx 0.4226
$$

     $$
\angle B = \arccos(0.4226) \approx 65^\circ
$$

Coordinate geometry calculations are consistent with analytical results ✓

## Final answer

     $$
\boxed{\angle B = 65^\circ}
$$

## Easy to make mistakes
1. **Ignore the role of     $D$     on     $BC$    :** The role of     $D$     is to represent     $\angle A$     as     $\angle BAD + \angle CAD$    , which is the key to finding     $\angle A$    . Some people will try to use     $D$     to do other complex structures and sacrifice the near and far.
2. **Reverse the properties of an isosceles triangle:** In an isosceles triangle, "equilateral sides correspond to equal angles". Do not mistakenly write "equilateral sides correspond to large angles".     $AB = AC$     gives     $\angle B = \angle C$     (two base angles are equal), not     $\angle A = \angle B$     .
3. **Incorrect memory of the formula for the sum of interior angles:** The sum of the interior angles of a triangle is     $180^\circ$    . Do not mistakenly remember it as     $360^\circ$     (that is the sum of the interior angles of a quadrilateral) or     $90^\circ$    .
4. **Angle unit confusion:** Use the degree system (    $^\circ$    ) to solve the problem, do not confuse it with the radian system. The final     $65^\circ$     would be wrong if written as     $\frac{65\pi}{180}$     - unless radians were specifically requested.
5. **Only list the equations without solving them:** After getting     $2\angle B = 130^\circ$    , forget to divide by     $2$     and directly write     $\angle B = 130^\circ$    .     $130^\circ$     is     $2\angle B$     , not     $\angle B$     .
