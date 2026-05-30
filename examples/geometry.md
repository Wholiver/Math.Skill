# 等腰三角形的角度计算

## 用户输入
在 $\triangle ABC$ 中，$AB = AC$，点 $D$ 在边 $BC$ 上。已知 $\angle BAD = 30^\circ$，$\angle CAD = 20^\circ$，求 $\angle B$。

## Skill 分类
几何（Geometry）— 三角形角度计算

## 题意解析

**已知条件：**
- $\triangle ABC$ 是等腰三角形，$AB = AC$（两腰相等）
- 点 $D$ 在边 $BC$ 上
- $\angle BAD = 30^\circ$（射线 $AD$ 与 $AB$ 的夹角）
- $\angle CAD = 20^\circ$（射线 $AD$ 与 $AC$ 的夹角）

**图形结构（文字描述）：**

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

射线 $AD$ 从顶点 $A$ 出发，经过 $BC$ 边上的点 $D$，将 $\angle A$ 分成 $\angle BAD = 30^\circ$ 和 $\angle CAD = 20^\circ$。

**求解目标：**
- $\angle B$ 的度数。

**隐式条件：**
- 点 $D$ 在边 $BC$ 上，意味着 $AD$ 是 $\angle A$ 内部的一条线段，将 $\angle A$ 分为两个部分。因此 $\angle A = \angle BAD + \angle CAD = 30^\circ + 20^\circ = 50^\circ$。
- $AB = AC$ 意味着 $\angle B = \angle C$（等腰三角形的两个底角相等）。
- 三角形内角和为 $180^\circ$。

**解的个数：**
- 角度值唯一确定。

## 方法选择

**选择方法：** 等腰三角形性质 + 三角形内角和定理

**理由：**
- 解题关键是利用 $AB = AC$ 得出 $\angle B = \angle C$ 的性质。
- 通过 $D$ 在 $BC$ 上一条件，将 $\angle A$ 表示为两个已知角度之和。
- 然后用内角和定理求 $\angle B$。

**备选方法：**
- 正弦定理法：设定一边长度，用已知角度解三角形——虽然可行，但对纯角度计算来说过于复杂。
- 坐标几何法：建立坐标系计算——适合作为验算手段，不适合作为主解法。

## 解题过程

### 第一步：求 $\angle A$

因为 $D$ 在边 $BC$ 上，射线 $AD$ 在 $\angle A$ 内部，将 $\angle A$ 分为 $\angle BAD$ 和 $\angle CAD$：

$$
\angle A = \angle BAD + \angle CAD = 30^\circ + 20^\circ = 50^\circ
$$

### 第二步：利用等腰三角形性质

因为 $AB = AC$，根据"等边对等角"性质：

$$
\angle B = \angle C
$$

### 第三步：应用三角形内角和定理

三角形三个内角之和为 $180^\circ$：

$$
\angle A + \angle B + \angle C = 180^\circ
$$

代入 $\angle C = \angle B$ 和 $\angle A = 50^\circ$：

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

因此 $\angle B = \angle C = 65^\circ$。

### 第四步：验证几何合理性

检查所有已知条件是否满足：

- $\angle A + \angle B + \angle C = 50^\circ + 65^\circ + 65^\circ = 180^\circ$ ✓
- $\angle BAD + \angle CAD = 30^\circ + 20^\circ = 50^\circ = \angle A$ ✓
- $D$ 在 $BC$ 上：在 $\triangle ABD$ 中，$\angle B = 65^\circ$，$\angle BAD = 30^\circ$，则 $\angle ADB = 180^\circ - 65^\circ - 30^\circ = 85^\circ$。在 $\triangle ADC$ 中，$\angle C = 65^\circ$，$\angle CAD = 20^\circ$，则 $\angle ADC = 180^\circ - 65^\circ - 20^\circ = 95^\circ$。$\angle ADB + \angle ADC = 85^\circ + 95^\circ = 180^\circ$，说明 $B$、$D$、$C$ 三点共线 ✓

## 验算

### 验算方法一：内角和一致性检验

将 $D$ 分割成的两个小三角形分别计算内角和：

**在 $\triangle ABD$ 中：**

$$
\angle BAD + \angle B + \angle ADB = 30^\circ + 65^\circ + \angle ADB = 180^\circ
$$

$$
\angle ADB = 180^\circ - 95^\circ = 85^\circ
$$

**在 $\triangle ADC$ 中：**

$$
\angle CAD + \angle C + \angle ADC = 20^\circ + 65^\circ + \angle ADC = 180^\circ
$$

$$
\angle ADC = 180^\circ - 85^\circ = 95^\circ
$$

**验证三点共线：** $\angle ADB$ 和 $\angle ADC$ 是 $AD$ 两侧的邻补角。

$$
\angle ADB + \angle ADC = 85^\circ + 95^\circ = 180^\circ
$$

$B$、$D$、$C$ 共线，满足题设 $D$ 在 $BC$ 上的条件。✓

### 验算方法二：坐标几何法

建立坐标系，用坐标数值验证。

以 $A$ 为原点 $(0, 0)$，设 $AB = AC = 1$（不失一般性，因为相似三角形角度相同）。将射线 $AB$ 放在 $x$ 轴正向上：

- $B$：$(1, 0)$
- $A$：$(0, 0)$

由于 $\angle A = 50^\circ$ 且 $AC = 1$，点 $C$ 的坐标为：

$$
C = (\cos 50^\circ,\ \sin 50^\circ) \approx (0.6428,\ 0.7660)
$$

点 $D$ 在 $BC$ 上，且 $\angle BAD = 30^\circ$。射线 $AD$ 的方向角为 $30^\circ$：

$$
AD \text{ 方向向量：}(\cos 30^\circ,\ \sin 30^\circ) = \left(\frac{\sqrt{3}}{2},\ \frac{1}{2}\right) \approx (0.8660,\ 0.5000)
$$

$D$ 是 $AD$ 与 $BC$ 的交点。

直线 $BC$ 过 $B(1,0)$ 和 $C(0.6428, 0.7660)$，参数方程：

$$
BC: (1, 0) + t[(0.6428, 0.7660) - (1, 0)] = (1 - 0.3572t,\ 0.7660t),\quad 0 \leq t \leq 1
$$

直线 $AD$ 方程：$(s \cos 30^\circ,\ s \sin 30^\circ) = (0.8660s,\ 0.5000s),\ s \geq 0$

令两点重合求交点：

$$
\begin{cases}
0.8660s = 1 - 0.3572t \\
0.5000s = 0.7660t
\end{cases}
$$

由此可解出 $D$ 点位置（数值验证可得到在 $BC$ 上）。

计算 $\angle B$：向量 $\overrightarrow{BA}$ 与 $\overrightarrow{BC}$ 的夹角。

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

坐标几何计算与解析结果一致 ✓

## 最终答案

$$
\boxed{\angle B = 65^\circ}
$$

## 易错点
1. **忽略 $D$ 在 $BC$ 上的作用：** $D$ 的作用是将 $\angle A$ 表示为 $\angle BAD + \angle CAD$，这是求 $\angle A$ 的关键。有人会试图用 $D$ 做其他复杂构造而舍近求远。
2. **等腰三角形性质记反：** 等腰三角形中"等边对等角"，不要误记为"等边对大角"。$AB = AC$ 得出 $\angle B = \angle C$（两个底角相等），而非 $\angle A = \angle B$。
3. **内角和公式记错：** 三角形的内角和是 $180^\circ$，不要误记为 $360^\circ$（那是四边形的内角和）或 $90^\circ$。
4. **角度单位混淆：** 解题使用度数制（$^\circ$），不要与弧度制混淆。最终的 $65^\circ$ 如果写成 $\frac{65\pi}{180}$ 就错了——除非特意要求弧度。
5. **只列方程不解到底：** 得出 $2\angle B = 130^\circ$ 后忘记除以 $2$，直接写 $\angle B = 130^\circ$。$130^\circ$ 是 $2\angle B$，不是 $\angle B$。
