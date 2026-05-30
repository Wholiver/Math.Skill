# 不定积分：$\int x \sin x \, dx$ 的计算

## 用户输入
计算不定积分 $\displaystyle \int x \sin x \, dx$

## Skill 分类
微积分 / 不定积分

## 题意解析
- **被积函数**：$x \sin x$，是两个函数的乘积
- **目标**：求原函数（不定积分），需包含积分常数 $C$
- **方法选择依据**：被积函数是多项式 $x$ 和三角函数 $\sin x$ 的乘积，这是**分部积分法**的典型适用情境
- **隐含条件**：积分变量为 $x$，积分区间未指定（不定积分）
- **解的唯一性**：原函数不唯一（相差常数），但表示为标准形式即可

## 方法选择

**主方法：分部积分法（Integration by Parts）**

选择理由：分部积分法适用于两类不同函数乘积的积分，特别是当其中一个函数求导后简化（$x \to 1$）、另一个函数容易积分（$\sin x \to -\cos x$）时。

分部积分公式：
$$\int u \, dv = uv - \int v \, du$$

**LIATE 规则**：选取 $u$ 的优先级为 Logarithmic > Inverse trig > Algebraic > Trigonometric > Exponential。此处 $x$ 是代数函数（A），$\sin x$ 是三角函数（T），根据 LIATE 规则应选择 $u = x$，$dv = \sin x \, dx$。

备选方法：不存在——$x \sin x$ 没有简单的变元代换方法，分部积分是唯一的标准方法。

## 解题过程

**Step 1：选定 $u$ 和 $dv$**

令：
$$u = x, \quad dv = \sin x \, dx$$

**Step 2：计算 $du$ 和 $v$**

$$du = dx, \quad v = \int \sin x \, dx = -\cos x$$

**Step 3：代入分部积分公式**

$$\int x \sin x \, dx = uv - \int v \, du$$

$$= x \cdot (-\cos x) - \int (-\cos x) \, dx$$

$$= -x \cos x + \int \cos x \, dx$$

**Step 4：计算剩余积分**

$$\int \cos x \, dx = \sin x$$

**Step 5：得出最终结果**

$$\int x \sin x \, dx = -x \cos x + \sin x + C$$

其中 $C$ 为积分常数。

## 验算

**验算方法 1：对结果求导验证**

对 $F(x) = -x \cos x + \sin x + C$ 求导：

$$\frac{d}{dx}[-x \cos x] = -1 \cdot \cos x + (-x) \cdot (-\sin x) = -\cos x + x \sin x$$
（使用了乘积法则：$(fg)' = f'g + fg'$）

$$\frac{d}{dx}[\sin x] = \cos x$$

$$\frac{d}{dx}[C] = 0$$

求和：
$$F'(x) = (-\cos x + x \sin x) + \cos x + 0 = x \sin x$$

恰好等于被积函数 $x \sin x$ ✓

**验算方法 2：分部积分的反向推导**

从结果出发，分部积分应为：
$$\int x \sin x \, dx = -x \cos x - \int (-\cos x) \cdot 1 \, dx = -x \cos x + \sin x + C$$

与计算过程一致 ✓

**验算方法 3：数值验证（取 $C=0$）**

令 $F(x) = -x \cos x + \sin x$：
- $F(0) = -0 \cdot 1 + 0 = 0$
- $F(\pi/2) = -\frac{\pi}{2} \cdot 0 + 1 = 1$

而 $\int_0^{\pi/2} x \sin x \, dx = [-x \cos x + \sin x]_0^{\pi/2} = 1 - 0 = 1$ ✓

数值 $\int_0^{\pi/2} x \sin x \, dx$ 可近似：在 $[0, \pi/2]$ 上 $x \sin x$ 为正函数，积分 $1$ 合理 ✓

## 最终答案
$$\int x \sin x \, dx = -x \cos x + \sin x + C$$

## 易错点
1. **$u$ 和 $dv$ 的选择错误**：若选 $u = \sin x$，$dv = x \, dx$，则 $du = \cos x \, dx$，$v = x^2/2$，积分变为 $\frac{1}{2}x^2\sin x - \frac{1}{2}\int x^2 \cos x \, dx$，反而更复杂——说明 LIATE 规则的重要性
2. **$v$ 的符号**：$\int \sin x \, dx = -\cos x$（不是 $\cos x$），符号错误会导致验证失败
3. **忘记积分常数 $C$**：不定积分必须包含积分常数，遗漏会扣分
4. **乘积法则方向反了**：求导验证时注意 $(uv)' = u'v + uv'$，不要写错顺序
