# 一致连续性的证明与反例构造

## 用户输入
证明函数 $f(x) = x^2$ 在区间 $[0, 1]$ 上一致连续，但在 $[0, \infty)$ 上不一致连续。

## Skill 分类
实分析

## 题意解析
- **函数**：$f(x) = x^2$，定义在实数域。
- **需要证明的两个命题**：
  1. $f$ 在闭区间 $[0, 1]$ 上一致连续。
  2. $f$ 在无界区间 $[0, \infty)$ 上不一致连续。
- **关键区别**：$[0, 1]$ 是紧集（闭且有界），闭区间上的连续函数必然一致连续（Cantor 定理，可用于佐证但不能替代构造性证明）。$[0, \infty)$ 不是紧集。
- **一致连续的定义**：$\forall \varepsilon > 0,\ \exists \delta > 0,\ \forall x, y \in D,\ |x - y| < \delta \implies |f(x) - f(y)| < \varepsilon$。
- **不一致连续的含义**：存在 $\varepsilon_0 > 0$，使得对任意 $\delta > 0$，总存在 $x, y$ 满足 $|x - y| < \delta$ 但 $|f(x) - f(y)| \geq \varepsilon_0$。

## 方法选择
**证明一致连续**：利用恒等式 $|x^2 - y^2| = |x + y| \cdot |x - y|$，在有界区间上放缩 $|x + y|$。这是标准的 $\varepsilon$-$\delta$ 构造方法。

**证明不一致连续**：构造序列反例，选取 $x_n$ 和 $y_n$ 使得 $|x_n - y_n| \to 0$ 但 $|f(x_n) - f(y_n)|$ 保持有下界。常用的构造是 $x_n = n + \frac{1}{n}$，$y_n = n$，利用平方差展开中的 $2n$ 因子发散。

## 解题过程

### 第一部分：$f(x) = x^2$ 在 $[0, 1]$ 上一致连续

对任意 $x, y \in [0, 1]$：

$$|f(x) - f(y)| = |x^2 - y^2| = |x + y| \cdot |x - y|$$

由于 $x, y \in [0, 1]$，所以 $|x + y| \leq 1 + 1 = 2$。因此：

$$|f(x) - f(y)| \leq 2|x - y|$$

给定 $\varepsilon > 0$，取 $\delta = \dfrac{\varepsilon}{2} > 0$。则当 $|x - y| < \delta$ 时：

$$|f(x) - f(y)| \leq 2|x - y| < 2 \cdot \frac{\varepsilon}{2} = \varepsilon$$

这正是一致连续的定义。$\square$

### 第二部分：$f(x) = x^2$ 在 $[0, \infty)$ 上不一致连续

证明思路：设存在一致连续的 $\delta(\varepsilon)$，则对足够大的 $x$，$|f(x+\delta/2) - f(x)|$ 应能被 $\varepsilon$ 控制。但

$$|f(x + h) - f(x)| = |(x+h)^2 - x^2| = |2xh + h^2|$$

对于固定的 $h$，当 $x \to \infty$ 时，这一差值趋于无穷大，矛盾。

正式证明：取 $\varepsilon_0 = 1$。对任意 $\delta > 0$，选取

$$x = \frac{1}{\delta},\quad y = \frac{1}{\delta} + \frac{\delta}{2}$$

则 $|x - y| = \dfrac{\delta}{2} < \delta$，但：

$$|f(x) - f(y)| = \left|\left(\frac{1}{\delta} + \frac{\delta}{2}\right)^2 - \left(\frac{1}{\delta}\right)^2\right|$$

$$= \left|\frac{2}{\delta} \cdot \frac{\delta}{2} + \left(\frac{\delta}{2}\right)^2\right| = 1 + \frac{\delta^2}{4} \geq 1 = \varepsilon_0$$

因此对任意 $\delta > 0$，均存在 $x, y \in [0, \infty)$ 满足 $|x - y| < \delta$ 但 $|f(x) - f(y)| \geq 1$。

这违反了 $f$ 在 $[0, \infty)$ 上一致连续的定义。$\square$

**备选构造**（更优雅）：取 $x_n = n$，$y_n = n + \frac{1}{n}$。则 $|x_n - y_n| = \frac{1}{n} \to 0$，但：

$$|f(x_n) - f(y_n)| = \left|n^2 - \left(n + \frac{1}{n}\right)^2\right| = \left|n^2 - n^2 - 2 - \frac{1}{n^2}\right| = 2 + \frac{1}{n^2} > 2$$

与一致连续矛盾（一致连续要求 $|x_n - y_n| \to 0 \implies |f(x_n) - f(y_n)| \to 0$）。

## 验算

### 方法一：$\varepsilon$-$\delta$ 结构检查

**一致连续证明的结构验证**：
1. 从不等式放缩出发：$|f(x) - f(y)| \leq L|x - y|$（Lipschitz 条件）。
2. 找到 Lipschitz 常数 $L = 2$，不依赖于 $x, y$ 的选取。
3. 给定 $\varepsilon$，$\delta = \varepsilon/2$ 中的 $\delta$ 仅依赖于 $\varepsilon$，不依赖于具体的 $x$ 或 $y$。这正是"一致"的含义。✓

**不一致连续证明的结构验证**：
1. 选取 $\varepsilon_0 = 1$ 是具体的正数。
2. 对"任意"$\delta$ 构造了 $x, y$ 使得 $|x - y| < \delta$ 但 $|f(x) - f(y)| \geq \varepsilon_0$。$x$ 和 $y$ 的构造依赖于 $\delta$（即 $x = 1/\delta$），这是正确的——反例当然可以依赖于给定的 $\delta$。✓

### 方法二：边界情况的验证

**$[0, 1]$ 上**：当 $x = 1$，$y = 0.999$（$|x-y| = 0.001$）：
$$|f(1) - f(0.999)| = |1 - 0.998001| = 0.001999 \approx 2 \times 0.001$$
符合 Lipschitz 界。✓

**$[0, \infty)$ 上**：当 $n = 100$ 时，$x_n = 100$，$y_n = 100.01$：
$$|f(100) - f(100.01)| = |10000 - 10002.0001| = 2.0001 > 2$$
即使两点间距仅 $0.01$，函数值差已超过 $2$。✓

### 方法三：定理对照

Cantor 定理：紧集上的连续函数一致连续。$[0, 1]$ 是 $\mathbb{R}$ 中的紧集，$f(x) = x^2$ 连续，因此一致连续。这与第一部分构造性证明的结论一致。✓

$[0, \infty)$ 不是紧集（无界），Cantor 定理不适用，因此一致连续性不能直接从连续性推出——反例确证了这一点。✓

## 最终答案

$$\boxed{f(x) = x^2 \text{ 在 } [0, 1] \text{ 上一致连续}}$$

$$\boxed{f(x) = x^2 \text{ 在 } [0, \infty) \text{ 上不一致连续}}$$

## 易错点
1. **Lipschitz 常数对有界区间的作用**：放缩 $|x + y| \leq 2$ 的关键是利用了区间的有界性。如果区间无界（如 $[0, \infty)$），$|x + y|$ 没有统一的上界，因此无法导出全局的 Lipschitz 估计。
2. **反例的构造**：$|x_n - y_n| \to 0$ 但 $|f(x_n) - f(y_n)| \not\to 0$ 是不一致连续的**等价刻画**，不是充分条件。这个条件等价于"存在 $\varepsilon_0$ 使得 $\forall \delta, \exists x, y: |x-y|<\delta \land |f(x)-f(y)|\geq\varepsilon_0$"。构造时确保差额至少为常数（不趋于零）。
3. **$\delta$ 与 $\varepsilon$ 的依赖**：一致连续要求 $\delta$ 仅依赖于 $\varepsilon$ 而不依赖于 $x$。在 $[0,1]$ 的证明中 $\delta = \varepsilon/2$ 正是如此。不要把逐点连续与一致连续混淆。
4. **$x = 1/\delta$ 的讨论**：当 $\delta \to 0$ 时 $x \to \infty$，说明反例确实需要跑到无穷远处。这揭示了不一致连续的根源在于函数在远处的斜率无限增长。
