# 三角恒等式证明

## 用户输入
证明恒等式：$\sin^3\theta + \cos^3\theta = (\sin\theta + \cos\theta)(1 - \sin\theta\cos\theta)$

## Skill 分类
三角学（Trigonometry）— 三角恒等式证明

## 题意解析

**已知条件：**
- 需证明的恒等式：$\sin^3\theta + \cos^3\theta = (\sin\theta + \cos\theta)(1 - \sin\theta\cos\theta)$

**求解目标：**
- 通过代数与三角恒等变换证明等号左右两边恒等。

**变量与定义域：**
- $\theta \in \mathbb{R}$，恒等式对一切实数 $\theta$ 成立（左式和右式的定义域均为 $\mathbb{R}$）。

**隐式条件：**
- $\sin^3\theta$ 可视为 $(\sin\theta)^3$，同理 $\cos^3\theta = (\cos\theta)^3$。
- 这是立方和公式 $a^3 + b^3 = (a+b)(a^2 - ab + b^2)$ 在三角学中的应用。
- 三角基本恒等式 $\sin^2\theta + \cos^2\theta = 1$ 将发挥关键作用。

**解的个数：**
- 恒等式证明不是解方程，目标不是求 $\theta$ 的值，而是证明对一切 $\theta$ 等式成立。

## 方法选择

**选择方法：** 从左边出发，应用立方和公式 + 基本恒等式化简

**理由：**
- 左边的 $\sin^3\theta + \cos^3\theta$ 结构上正是立方和 $a^3+b^3$，联想到因式分解。
- 分解后出现 $\sin^2\theta - \sin\theta\cos\theta + \cos^2\theta$，其中 $\sin^2\theta + \cos^2\theta = 1$ 恰好将表达式化简为 $1 - \sin\theta\cos\theta$，完美匹配右边的因子。

**备选方法：**
- 从右边展开验证：$(\sin\theta + \cos\theta)(1 - \sin\theta\cos\theta) = \sin\theta + \cos\theta - \sin^2\theta\cos\theta - \sin\theta\cos^2\theta$，需要进一步变形才能配对成 $\sin^3\theta + \cos^3\theta$，步骤稍多但也可行。
- 左右同时减去某项化简：不如直接单向化简清晰。

## 解题过程

### 从左边出发推导

**起点：** $\sin^3\theta + \cos^3\theta$

**第一步：应用立方和公式。**

令 $a = \sin\theta$，$b = \cos\theta$，则

$$
a^3 + b^3 = (a+b)(a^2 - ab + b^2)
$$

代入：

$$
\sin^3\theta + \cos^3\theta = (\sin\theta + \cos\theta)(\sin^2\theta - \sin\theta\cos\theta + \cos^2\theta) \tag{1}
$$

**第二步：应用基本三角恒等式。**

由 $\sin^2\theta + \cos^2\theta = 1$，可将括号内的 $\sin^2\theta + \cos^2\theta$ 替换为 $1$：

$$
\sin^2\theta - \sin\theta\cos\theta + \cos^2\theta = (\sin^2\theta + \cos^2\theta) - \sin\theta\cos\theta = 1 - \sin\theta\cos\theta \tag{2}
$$

**第三步：代入 (2) 到 (1)。**

$$
\sin^3\theta + \cos^3\theta = (\sin\theta + \cos\theta)(1 - \sin\theta\cos\theta)
$$

这就是要证明的右边。等式得证。

### 反向推导（验算用）

从右边出发：

$$
(\sin\theta + \cos\theta)(1 - \sin\theta\cos\theta)
$$

展开：

$$
= (\sin\theta + \cos\theta) \cdot 1 - (\sin\theta + \cos\theta) \cdot \sin\theta\cos\theta
$$

$$
= \sin\theta + \cos\theta - \sin^2\theta\cos\theta - \sin\theta\cos^2\theta
$$

提取 $\sin\theta\cos\theta$（从后两项）：

$$
= \sin\theta + \cos\theta - \sin\theta\cos\theta(\sin\theta + \cos\theta)
$$

将 $(\sin\theta + \cos\theta)$ 视为公因子：

$$
= (\sin\theta + \cos\theta)\left[1 - \sin\theta\cos\theta\left(\frac{\sin\theta + \cos\theta}{\sin\theta + \cos\theta}\right)\right]
$$

这里出错了。让我重新做。

实际上从右边展开回去也很直接。让我用另一种方式：

$(\sin\theta + \cos\theta)(1 - \sin\theta\cos\theta)$

$= \sin\theta \cdot 1 - \sin\theta \cdot \sin\theta\cos\theta + \cos\theta \cdot 1 - \cos\theta \cdot \sin\theta\cos\theta$

$= \sin\theta + \cos\theta - \sin^2\theta\cos\theta - \sin\theta\cos^2\theta$

$= \sin\theta(1 - \sin\theta\cos\theta) + \cos\theta(1 - \sin\theta\cos\theta)$  -- no that's just re-writing the original.

Let me try: $= \sin\theta + \cos\theta - \cos\theta\sin^2\theta - \sin\theta\cos^2\theta$

Replace $\sin^2\theta = 1 - \cos^2\theta$ and $\cos^2\theta = 1 - \sin^2\theta$:

Actually, this approach is getting messy. Let me reformulate.

Better: Group terms differently:

$= \sin\theta - \sin\theta\cos^2\theta + \cos\theta - \sin^2\theta\cos\theta$

$= \sin\theta(1 - \cos^2\theta) + \cos\theta(1 - \sin^2\theta)$

$= \sin\theta \cdot \sin^2\theta + \cos\theta \cdot \cos^2\theta$

$= \sin^3\theta + \cos^3\theta$, ✓

This is clean.

## 验算

### 验算方法一：数值抽样检验

选取五个代表性的 $\theta$ 值，分别计算左右两边。

**① $\theta = 0$：**

$$
\sin 0 = 0,\ \cos 0 = 1
$$

左式：$0^3 + 1^3 = 1$

右式：$(0 + 1)(1 - 0 \times 1) = 1 \times 1 = 1$ ✓

**② $\theta = \frac{\pi}{6}$（$30^\circ$）：**

$$
\sin\frac{\pi}{6} = \frac{1}{2},\ \cos\frac{\pi}{6} = \frac{\sqrt{3}}{2}
$$

左式：

$$
\left(\frac{1}{2}\right)^3 + \left(\frac{\sqrt{3}}{2}\right)^3 = \frac{1}{8} + \frac{3\sqrt{3}}{8} = \frac{1 + 3\sqrt{3}}{8}
$$

右式：

$$
\left(\frac{1}{2} + \frac{\sqrt{3}}{2}\right)\left(1 - \frac{1}{2} \times \frac{\sqrt{3}}{2}\right) = \frac{1+\sqrt{3}}{2} \times \left(1 - \frac{\sqrt{3}}{4}\right)
$$

$$
= \frac{1+\sqrt{3}}{2} \times \frac{4-\sqrt{3}}{4} = \frac{(1+\sqrt{3})(4-\sqrt{3})}{8}
$$

展开分子：$(1+\sqrt{3})(4-\sqrt{3}) = 4 - \sqrt{3} + 4\sqrt{3} - 3 = 1 + 3\sqrt{3}$

因此右式 $= \dfrac{1 + 3\sqrt{3}}{8}$，与左式相等。✓

**③ $\theta = \frac{\pi}{4}$（$45^\circ$）：**

$$
\sin\frac{\pi}{4} = \cos\frac{\pi}{4} = \frac{\sqrt{2}}{2}
$$

左式：

$$
\left(\frac{\sqrt{2}}{2}\right)^3 + \left(\frac{\sqrt{2}}{2}\right)^3 = 2 \times \frac{2\sqrt{2}}{8} = \frac{4\sqrt{2}}{8} = \frac{\sqrt{2}}{2}
$$

右式：

$$
\left(\frac{\sqrt{2}}{2} + \frac{\sqrt{2}}{2}\right)\left(1 - \frac{\sqrt{2}}{2} \times \frac{\sqrt{2}}{2}\right) = \sqrt{2} \times \left(1 - \frac{2}{4}\right) = \sqrt{2} \times \frac{1}{2} = \frac{\sqrt{2}}{2}
$$

✓

**④ $\theta = \frac{\pi}{3}$（$60^\circ$）：**

$$
\sin\frac{\pi}{3} = \frac{\sqrt{3}}{2},\ \cos\frac{\pi}{3} = \frac{1}{2}
$$

左式：

$$
\left(\frac{\sqrt{3}}{2}\right)^3 + \left(\frac{1}{2}\right)^3 = \frac{3\sqrt{3}}{8} + \frac{1}{8} = \frac{3\sqrt{3}+1}{8}
$$

右式：

$$
\left(\frac{\sqrt{3}}{2} + \frac{1}{2}\right)\left(1 - \frac{\sqrt{3}}{2} \times \frac{1}{2}\right) = \frac{\sqrt{3}+1}{2} \times \frac{4-\sqrt{3}}{4} = \frac{(\sqrt{3}+1)(4-\sqrt{3})}{8}
$$

展开：$(4\sqrt{3} - 3 + 4 - \sqrt{3}) = 3\sqrt{3} + 1$

右式 $= \dfrac{3\sqrt{3}+1}{8}$ = 左式 ✓

**⑤ $\theta = \frac{\pi}{2}$（$90^\circ$）：**

$$
\sin\frac{\pi}{2} = 1,\ \cos\frac{\pi}{2} = 0
$$

左式：$1^3 + 0^3 = 1$

右式：$(1 + 0)(1 - 1 \times 0) = 1$ ✓

五个特殊角全部验证通过。

### 验算方法二：反向推导（从右边到左边）

$$
\begin{aligned}
(\sin\theta + \cos\theta)(1 - \sin\theta\cos\theta)
&= \sin\theta - \sin^2\theta\cos\theta + \cos\theta - \sin\theta\cos^2\theta \\[6pt]
&= \sin\theta(1 - \cos^2\theta) + \cos\theta(1 - \sin^2\theta) \\[6pt]
&= \sin\theta \cdot \sin^2\theta + \cos\theta \cdot \cos^2\theta \\[6pt]
&= \sin^3\theta + \cos^3\theta
\end{aligned}
$$

其中第二步使用了 $\sin^2\theta = 1 - \cos^2\theta$ 和 $\cos^2\theta = 1 - \sin^2\theta$。✓

## 最终答案

$$
\boxed{\sin^3\theta + \cos^3\theta = (\sin\theta + \cos\theta)(1 - \sin\theta\cos\theta)}
$$

对一切 $\theta \in \mathbb{R}$ 成立。

## 易错点
1. **立方和公式记错：** $a^3 + b^3 = (a+b)(a^2 - ab + b^2)$，注意中间是 $-ab$ 而非 $+ab$。如果与立方差公式 $a^3-b^3 = (a-b)(a^2+ab+b^2)$ 混淆会导致错误。
2. **忘记基本恒等式：** $\sin^2\theta + \cos^2\theta = 1$ 是三角学最基本的恒等式，本题中在因式分解的后一步即需要这个替换。
3. **展开右边时符号错误：** 从右边展开 $(\sin\theta + \cos\theta)(1 - \sin\theta\cos\theta)$ 时，负号要在每项都体现。
4. **混淆 $\sin^3\theta$ 与 $\sin\theta^3$：** $\sin^3\theta$ 表示 $(\sin\theta)^3$，而 $\sin\theta^3$ 通常表示 $\sin(\theta^3)$，两者完全不同。在等式中始终使用 $\sin^3\theta$ 的写法。
5. **误以为需要解方程：** 恒等式证明不是解方程——不需要求出具体的 $\theta$ 值。证明的目标是展示等式对一切 $\theta$ 都成立。
