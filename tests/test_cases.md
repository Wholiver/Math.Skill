# Math.skill 综合测试用例

> 本文档包含 30 个覆盖所有数学类别和技能维度的综合测试用例。
> 每个测试用例用于评估 Math.skill 的正确性、推理透明度、严谨性、验证质量等。

---

## 1. 简单算术：小数乘除混合运算

**Test ID:** TC-ARITH-001  
**Input:** "计算 3.14 × 2.5 ÷ 0.5"  
**Expected Classification:** calculation
**Expected Behavior:** 逐步计算乘法与除法，给出精确结果 15.7  
**Required Verification:**
- 验证 15.7 × 0.5 = 7.85，7.85 ÷ 2.5 = 3.14（逆运算验证）
- 检查中间步骤是否保持足够精度

**Key Checks:**
- 中间步骤不应舍入过早
- 最终结果应精确

**Failure Modes:**
- 中间舍入导致误差累积
- 计算器模式，不展示步骤

---

## 2. 代数化简与定义域限制

**Test ID:** TC-ALG-001  
**Input:** "化简表达式 \(\frac{x^2 - 4}{x^2 + x - 6}\) 并说明定义域限制"  
**Expected Classification:** algebra_simplification
**Expected Behavior:**
- 因式分解分子 \( (x-2)(x+2) \)
- 因式分解分母 \( (x+3)(x-2) \)
- 约去 \( (x-2) \)，得 \( \frac{x+2}{x+3} \)
- 声明 \( x \neq 2, x \neq -3 \)（即使约去后 x=2 处的原函数无定义）

**Required Verification:**
- 代入 x=2 检验原函数无定义
- 代入 x=1 检验化简前后值相等
- 代入 x=0 检验化简前后值相等

**Key Checks:**
- **关键陷阱**：约去 (x-2) 后是否仍然声明 x≠2
- 分母因式分解是否正确

**Failure Modes:**
- 忘记声明 x≠2 的定义域限制（最常见的错误）
- 分母因式分解错误

---

## 3. 二次方程：判别式为零

**Test ID:** TC-ALG-002  
**Input:** "解方程 \(x^2 - 6x + 9 = 0\)"  
**Expected Classification:** equation_solving
**Expected Behavior:**
- 计算判别式 \( \Delta = 36 - 36 = 0 \)
- 指出判别式为零意味着一个重根
- 得到 \( x = 3 \)（二重根）
- 使用求根公式或完全平方：\( (x-3)^2 = 0 \)

**Required Verification:**
- 回代验证：\( 3^2 - 6 \times 3 + 9 = 9 - 18 + 9 = 0 \)
- 显式说明判别式为零 = 一个实数根（而非无根）

**Key Checks:**
- 不应说"无解"
- 应说明是二重根

**Failure Modes:**
- 将 Δ=0 误判为无实数解
- 只说 x=3 而不提二重根的性质

---

## 4. 分式方程与增根

**Test ID:** TC-ALG-003  
**Input:** "解方程 \(\frac{x}{x-2} + \frac{1}{x} = \frac{4}{x(x-2)}\)"  
**Expected Classification:** equation_solving
**Expected Behavior:**
- 乘以公分母 \( x(x-2) \)：\( x^2 + (x-2) = 4 \)
- 得 \( x^2 + x - 6 = 0 \)
- 解得 \( x = 2 \) 或 \( x = -3 \)
- **验证**：x=2 使分母为零，是增根
- 最终解：\( x = -3 \)

**Required Verification:**
- 显式回代 x=2 到原方程，分母 \( x-2 = 0 \) 无定义
- 回代 x=-3：左 = \( \frac{-3}{-5} + \frac{1}{-3} = 0.6 - 0.333... = 0.2666... \) = 右

**Key Checks:**
- **必须**识别增根
- 必须在解题后显式验根
- 不应跳过定义域分析

**Failure Modes:**
- 直接给出两个解，未检查增根（最严重错误）
- 未说明为什么 x=2 不是解

---

## 5. 线性方程组：唯一解

**Test ID:** TC-LIN-001  
**Input:** "解方程组 \begin{cases} 2x + 3y = 8 \\ 4x - y = 2 \end{cases}"  
**Expected Classification:** equation_solving, system_of_equations
**Expected Behavior:**
- 使用消元法或代入法
- 解出 \( x = 1, y = 2 \)
- 指出方程组的秩为 2，有唯一解

**Required Verification:**
- 回代第一条方程：\( 2(1) + 3(2) = 2 + 6 = 8 \) ✓
- 回代第二条方程：\( 4(1) - 2 = 2 \) ✓
- 用矩阵方法交叉验证（可选）

**Key Checks:**
- 两个解都应满足两个方程
- 如果有唯一解，显式说明

**Failure Modes:**
- 消元过程中算术错误
- 忘记验证

---

## 6. 不等式与符号表

**Test ID:** TC-INEQ-001  
**Input:** "解不等式 \(x^3 - 3x^2 - 4x + 12 > 0\)"  
**Expected Classification:** equation_solving, inequality_solving
**Expected Behavior:**
- 因式分解：尝试 x=2 是根，得 \( (x-2)(x^2-x-6) = (x-2)(x-3)(x+2) \)
- 关键点：x = -2, 2, 3
- 制作符号表，检验四个区间
- 给出解集 \( (-2, 2) \cup (3, +\infty) \)

**Required Verification:**
- 在每个区间取代表值检验（如 x=-3, 0, 2.5, 4）
- 端点检验：x=-2, 2, 3 处函数值为 0
- 符号表逻辑是否完整

**Key Checks:**
- 符号表是否正确
- 区间端点是否正确处理（开区间/闭区间）
- 因式分解是否正确

**Failure Modes:**
- 因式分解错误导致符号表错误
- 漏掉某个区间
- 端点的开闭搞混

---

## 7. 函数定义域与值域

**Test ID:** TC-FUNC-001  
**Input:** "求函数 \(f(x) = \sqrt{4 - x^2} + \ln(x-1)\) 的定义域"  
**Expected Classification:** equation_solving, function_analysis
**Expected Behavior:**
- 对 \( \sqrt{4-x^2} \)：\( 4-x^2 \geq 0 \) → \( x \in [-2, 2] \)
- 对 \( \ln(x-1) \)：\( x-1 > 0 \) → \( x > 1 \)
- 取交集：\( x \in (1, 2] \)

**Required Verification:**
- 端点 x=1：验证 ln(0) 无定义
- 端点 x=2：验证 √(4-4)=0 和 ln(1)=0，f(2)=0
- 区间内取 x=1.5 检验

**Key Checks:**
- 平方根条件是 ≥0 而不是 >0
- 对数条件是 >0 而不是 ≥0
- 交集是否正确

**Failure Modes:**
- 平方根条件写成 >0，遗漏 x=2
- 对数条件写成 ≥0
- 不懂取交集

---

## 8. 几何证明：三角形全等

**Test ID:** TC-GEOM-001  
**Input:** "如图，在 △ABC 中，AB=AC，D 是 BC 中点。求证 AD⊥BC。文字描述，无图。"  
**Expected Classification:** geometry, proof
**Expected Behavior:**
- 利用等腰三角形性质
- 已知 AB=AC，D 是 BC 中点
- 在 △ABD 和 △ACD 中：AB=AC, BD=CD, AD=AD
- 由 SSS 得 △ABD ≅ △ACD
- 故 ∠ADB = ∠ADC
- 又 ∠ADB + ∠ADC = 180°
- 所以 ∠ADB = ∠ADC = 90°，即 AD⊥BC

**Required Verification:**
- 全等的 SSS 条件是否完整（三条边对应相等）
- 逻辑链是否完整：全等 → 对应角相等 → 邻补角 → 直角
- 是否有跳步

**Key Checks:**
- SSS 全等条件正确应用
- 等腰三角形性质的推理是否正确
- 最终结论的逻辑完备性

**Failure Modes:**
- 直接声称"等腰三角形底边中线即高"而无证明（循环论证）
- SSS 条件陈述不全

---

## 9. 三角恒等式

**Test ID:** TC-TRIG-001  
**Input:** "证明 \(\frac{\sin 2x}{1 + \cos 2x} = \tan x\)"  
**Expected Classification:** trigonometry, proof
**Expected Behavior:**
- 使用倍角公式：\( \sin 2x = 2\sin x \cos x \)
- \( \cos 2x = 2\cos^2 x - 1 \)
- 左 = \( \frac{2\sin x \cos x}{1 + (2\cos^2 x - 1)} = \frac{2\sin x \cos x}{2\cos^2 x} \)
- 约分：\( \frac{\sin x}{\cos x} = \tan x \) = 右
- 定义域说明：\( \cos 2x \neq -1 \) 即 \( x \neq \frac{\pi}{2} + k\pi \) 且 \( \cos x \neq 0 \)

**Required Verification:**
- 从右到左倒推验证
- 代入特殊值检验：x=π/4 时左=1，右=1
- 定义域说明

**Key Checks:**
- 倍角公式是否正确
- 化简过程代数错误概率
- 是否说明定义域

**Failure Modes:**
- 倍角公式符号错误（sin2x 或 cos2x）
- 忘记说明定义域
- 代数化简错误

---

## 10. 等差数列：求通项与求和

**Test ID:** TC-SEQ-001  
**Input:** "等差数列的前 5 项和为 30，第 10 项为 25。求通项公式和前 n 项和公式。"  
**Expected Classification:** equation_solving, sequence, system_of_equations
**Expected Behavior:**
- 设首项 a，公差 d
- S₅ = \( \frac{5}{2}(2a + 4d) = 30 \) → \( 2a + 4d = 12 \)
- a₁₀ = a + 9d = 25
- 解方程组：得 a = -4, d = 3.222...? 
  - 等一下，验证：2(-4) + 4d = 12 → -8 + 4d = 12 → d = 5
  - a + 9d = -4 + 45 = 41 ≠ 25
  - 看来不一致。重新：S₅ = 5a + 10d = 30 → a + 2d = 6
  - a + 9d = 25
  - 相减：7d = 19 → d = 19/7 ≈ 2.714...
  - a = 6 - 2(19/7) = 6 - 38/7 = 4/7
  - 验证：S₅ = 5(4/7) + 10(19/7) = 20/7 + 190/7 = 210/7 = 30 ✓

**Required Verification:**
- 验证 a₁₀：4/7 + 9(19/7) = 4/7 + 171/7 = 175/7 = 25 ✓
- 通项：\( a_n = \frac{4}{7} + (n-1)\frac{19}{7} \)
- 前 n 项和：\( S_n = \frac{n}{2}(2 \cdot \frac{4}{7} + (n-1)\frac{19}{7}) \)

**Key Checks:**
- 方程组列写是否正确
- 解出的 a 和 d 是否正确
- 验证步骤完整性

**Failure Modes:**
- 等差数列公式错误
- 方程组求解错误

---

## 11. 组合数学：排列限制

**Test ID:** TC-COMB-001  
**Input:** "从 5 个男生和 4 个女生中选 4 人组成委员会，要求至少包含 1 名女生。有多少种不同的选法？"  
**Expected Classification:** combinatorics
**Expected Behavior:**
- 方法一（补集法）：总数 C(9,4) - 全男生 C(5,4)
  - C(9,4) = 126, C(5,4) = 5 → 121
- 方法二（分情况）：1女3男 + 2女2男 + 3女1男 + 4女0男
  - C(4,1)C(5,3) + C(4,2)C(5,2) + C(4,3)C(5,1) + C(4,4)C(5,0)
  - 4×10 + 6×10 + 4×5 + 1×1 = 40+60+20+1 = 121

**Required Verification:**
- 两种方法结果一致（121）
- 逐个验证各分情况的计算
- 确保无遗漏或重复

**Key Checks:**
- 补集法的应用是否正确
- C(n,k) 计算是否正确
- 是否考虑了所有情况

**Failure Modes:**
- 直接加而不考虑组合
- 补集法中总数减去的方式有误
- 分情况讨论遗漏

---

## 12. 概率：条件概率

**Test ID:** TC-PROB-001  
**Input:** "袋中有 3 个红球和 2 个蓝球。不放回地摸两次。已知第一次摸到红球，求第二次也摸到红球的概率。"  
**Expected Classification:** probability_statistics
**Expected Behavior:**
- 第一次摸到红球后，剩余 2 红 2 蓝共 4 球
- P(第二次红 | 第一次红) = 2/4 = 1/2
- 也可用定义：P(A∩B)/P(A) = (3/5 × 2/4) / (3/5) = (6/20)/(3/5) = 6/20 × 5/3 = 1/2

**Required Verification:**
- 两种方法结果一致
- 说明条件概率的直观意义
- 不放回抽样的影响

**Key Checks:**
- 条件概率定义的正确应用
- 不放回的影响是否正确体现
- 结果 1/2 是否合理（直观检验）

**Failure Modes:**
- 误用放回抽样公式
- 条件概率定义混淆 P(A|B) 和 P(B|A)

---

## 13. 微积分：L'Hôpital 法则求极限

**Test ID:** TC-CALC-001  
**Input:** "求极限 \(\lim_{x \to 0} \frac{e^x - 1 - x}{x^2}\)"  
**Expected Classification:** limit
**Expected Behavior:**
- 代入 x→0：分子 1-1-0=0，分母 0，0/0 型
- 第一次 L'Hôpital：\( \lim \frac{e^x - 1}{2x} \)，仍是 0/0
- 第二次 L'Hôpital：\( \lim \frac{e^x}{2} = \frac{1}{2} \)
- 或者展开 \( e^x = 1 + x + x^2/2 + x^3/6 + ... \)

**Required Verification:**
- 验证每次 L'Hôpital 前确实是 0/0 或 ∞/∞ 不定式
- 用泰勒展开交叉验证：\( e^x - 1 - x = x^2/2 + x^3/6 + ... \)，除以 x^2 → 1/2
- 用数值验证：x=0.001 时近似值为 0.500000167...

**Key Checks:**
- 两次 L'Hôpital 的条件是否满足
- 最终答案 1/2
- 交叉验证方法

**Failure Modes:**
- 不检查 L'Hôpital 条件就应用
- 只做一次 L'Hôpital 就停止

---

## 14. 导数应用：最优化

**Test ID:** TC-CALC-002  
**Input:** "用一块边长为 12cm 的正方形铁皮，在四个角各剪去一个相同的小正方形，然后折成一个无盖长方体盒子。问剪去的小正方形边长为多少时，盒子的容积最大？"  
**Expected Classification:** limit, optimization, differentiation
**Expected Behavior:**
- 设剪去小正方形边长为 x (0 < x < 6)
- 盒子底面边长 12-2x，高 x
- 体积 V(x) = x(12-2x)² = 4x(6-x)²
- V'(x) = 4(6-x)² - 8x(6-x) = 4(6-x)[(6-x) - 2x] = 4(6-x)(6-3x)
- 令 V'(x) = 0：x=6 或 x=2
- x=6 对应体积 0（最小值），x=2 对应最大值
- 验证：V''(2) < 0
- 最大体积 V(2) = 2 × 8² = 128 cm³

**Required Verification:**
- 给出 V'(x) 的详细推导
- 临界点的二阶导数检验
- 端点检验：x→0 时 V→0，x→6 时 V→0
- 答案的合理性检验

**Key Checks:**
- 导数计算是否正确
- 极值判断是正确的最大值而非最小值
- 实际意义：边长不能超过 6

**Failure Modes:**
- 忘记检查二阶导数
- 乘积求导错误
- 不懂最优化的基本步骤

---

## 15. 换元积分法

**Test ID:** TC-CALC-003  
**Input:** "计算不定积分 \(\int x\sqrt{2x+1}\,dx\)"  
**Expected Classification:** limit, integration
**Expected Behavior:**
- 换元：令 u = 2x+1，则 x = (u-1)/2, dx = du/2
- \( \int \frac{u-1}{2} \cdot \sqrt{u} \cdot \frac{du}{2} = \frac{1}{4} \int (u-1)u^{1/2} du \)
- = \( \frac{1}{4} \int (u^{3/2} - u^{1/2}) du \)
- = \( \frac{1}{4} \left( \frac{2}{5}u^{5/2} - \frac{2}{3}u^{3/2} \right) + C \)
- = \( \frac{1}{10}(2x+1)^{5/2} - \frac{1}{6}(2x+1)^{3/2} + C \)
- 可进一步化简为 \( \frac{(2x+1)^{3/2}(3x-1)}{15} + C \)

**Required Verification:**
- 求导验证：对结果求导，检验是否等于原被积函数
- 代入特殊值数值验算

**Key Checks:**
- 换元步骤中 dx 的转换
- 积分后的代数化简
- 不要忘记 +C

**Failure Modes:**
- 换元时 dx 转换错误
- 积分公式应用错误
- 代数化简中的错误

---

## 16. 反常积分收敛性

**Test ID:** TC-CALC-004  
**Input:** "判断反常积分 \(\int_1^\infty \frac{\ln x}{x^2}\,dx\) 的敛散性，若收敛求其值。"  
**Expected Classification:** limit, integration
**Expected Behavior:**
- 先判断收敛性：\( \frac{\ln x}{x^2} \) 的增长阶
  - 对任意 ε>0，ln x = o(x^ε)
  - \( \frac{\ln x}{x^2} = \frac{\ln x}{x^{1/2}} \cdot \frac{1}{x^{3/2}} \leq \frac{C}{x^{3/2}} \)（对充分大的 x）
  - 由 p-积分，\( \int_1^\infty \frac{1}{x^{3/2}} dx \) 收敛（p=3/2 > 1）
  - 由比较判别法，原积分收敛
- 计算积分值：分部积分法
  - 令 u = ln x, dv = dx/x²
  - du = dx/x, v = -1/x
  - \( \int \frac{\ln x}{x^2} dx = -\frac{\ln x}{x} + \int \frac{1}{x^2} dx = -\frac{\ln x}{x} - \frac{1}{x} + C \)
  - \( \lim_{t \to \infty} [-\frac{\ln x}{x} - \frac{1}{x}]_1^t = 0 - 0 - (-0 - (-1)) = 1 \)

**Required Verification:**
- 比较判别法的基准 p-积分选择是否合理
- 分部积分步骤是否正确
- 极限计算：lim(t→∞) ln(t)/t = 0
- 数值验证：部分和近似

**Key Checks:**
- 先证明收敛再计算（对反常积分的关键步骤）
- 比较判别法的应用
- 分部积分的正确性

**Failure Modes:**
- 不验证收敛性直接计算（最常见的错误）
- 发散但给出有限值

---

## 17. 多元函数：临界点与分类

**Test ID:** TC-MULTI-001  
**Input:** "求函数 \(f(x,y) = x^3 + 3xy^2 - 15x - 12y\) 的所有临界点，并分类（极大值、极小值或鞍点）。"  
**Expected Classification:** multivariable_calculus
**Expected Behavior:**
- 求偏导数：
  - \( f_x = 3x^2 + 3y^2 - 15 = 3(x^2 + y^2 - 5) \)
  - \( f_y = 6xy - 12 = 6(xy - 2) \)
- 解 f_x = 0: \( x^2 + y^2 = 5 \)
- 解 f_y = 0: \( xy = 2 \)
- 解方程组：x² + y² = 5, xy = 2
  - (x+y)² = x² + y² + 2xy = 5 + 4 = 9 → x+y = ±3
  - (x-y)² = x² + y² - 2xy = 5 - 4 = 1 → x-y = ±1
  - 四组合：4 个临界点
  - (2,1), (1,2), (-1,-2), (-2,-1)
- Hessian 矩阵：H = [[6x, 6y], [6y, 6x]], det(H) = 36(x² - y²)
  - (2,1): det(H)=108>0, f_{xx}=12>0 → 局部极小值
  - (1,2): det(H)=-108<0 → 鞍点
  - (-1,-2): det(H)=-108<0 → 鞍点
  - (-2,-1): det(H)=108>0, f_{xx}=-12<0 → 局部极大值

**Required Verification:**
- 方程组求解是否完整
- Hessian 行列式分类是否正确
- 每个临界点的 f_{xx} 符号检查

**Key Checks:**
- 不能漏解
- Hessian 判别法的应用
- 区分鞍点与极值点

**Failure Modes:**
- 方程组求解漏解
- Hessian 计算错误
- 分类弄反（极大/极小）

---

## 18. 矩阵特征值问题

**Test ID:** TC-LINALG-001  
**Input:** "求矩阵 \(A = \begin{pmatrix} 2 & 1 & 1 \\ 1 & 2 & 1 \\ 1 & 1 & 2 \end{pmatrix}\) 的特征值和特征向量。"  
**Expected Classification:** linear_algebra
**Expected Behavior:**
- 特征方程：det(A - λI) = 0
  - \( \begin{vmatrix} 2-λ & 1 & 1 \\ 1 & 2-λ & 1 \\ 1 & 1 & 2-λ \end{vmatrix} = 0 \)
  - 计算行列式：\( (2-λ)^3 + 1 + 1 - (2-λ) - (2-λ) - (2-λ) \)
  - = \( (2-λ)^3 - 3(2-λ) + 2 \)
  - 令 t = 2-λ：t³ - 3t + 2 = (t-1)²(t+2) = 0
  - t = 1 (二重) 或 t = -2
  - λ = 1 (二重) 或 λ = 4
- 验证迹：tr(A) = 6, 特征值和 = 1+1+4 = 6 ✓
- λ=1 的特征向量（解 (A-I)x=0）
- λ=4 的特征向量（解 (A-4I)x=0）

**Required Verification:**
- 迹等于特征值之和
- 行列式等于特征值之积
- 代入检验 Av=λv

**Key Checks:**
- 行列式计算正确
- 特征多项式因式分解
- 特征向量的基础解系

**Failure Modes:**
- 行列式计算错误
- 特征值漏解（三重根 vs 二重根+单根）
- 忘记特征向量

---

## 19. 一阶线性常微分方程

**Test ID:** TC-ODE-001  
**Input:** "解微分方程 \(y' + 2xy = x\)，满足 y(0) = 1。"  
**Expected Classification:** ordinary_differential_equation
**Expected Behavior:**
- 识别为一阶线性 ODE：\( y' + P(x)y = Q(x) \)，P(x) = 2x, Q(x) = x
- 积分因子：\( \mu(x) = e^{\int 2x dx} = e^{x^2} \)
- 两边同乘：\( e^{x^2}y' + 2xe^{x^2}y = xe^{x^2} \)
- 左边 = \( \frac{d}{dx}(e^{x^2}y) \)
- 积分：\( e^{x^2}y = \int xe^{x^2} dx = \frac{1}{2}e^{x^2} + C \)
- \( y = \frac{1}{2} + Ce^{-x^2} \)
- 用 y(0) = 1：1 = 1/2 + C → C = 1/2
- 特解：\( y = \frac{1}{2}(1 + e^{-x^2}) \)

**Required Verification:**
- 代入 ODE 验证：y' = -xe^{-x^2}, y' + 2xy = -xe^{-x^2} + x(1+e^{-x^2}) = x ✓
- 检验初始条件

**Key Checks:**
- 积分因子计算正确
- 积分步骤
- 初始条件代入

**Failure Modes:**
- 积分因子公式记忆错误
- 右边积分错误
- 忘记用初始条件求 C

---

## 20. 实分析：证明一致连续性

**Test ID:** TC-ANALYSIS-001  
**Input:** "证明函数 \(f(x) = \sqrt{x}\) 在 \([0, \infty)\) 上一致连续吗？给出证明或反例。"  
**Expected Classification:** real_analysis
**Expected Behavior:**
- 结论：是，√x 在 [0,∞) 一致连续
- 证明：对任意 ε>0，取 δ = ε²
- 若 |x-y| < δ，则 |√x - √y| = |x-y|/(√x+√y) ≤ |x-y|/√|x-y|（利用 √x+√y ≥ √|x-y|）
  - 且当 x,y≥0 时，|√x-√y|² = |x-y| - 2√xy(1 - sgn(xy)...) ≤ |x-y|
  - 更简洁：|√x - √y| ≤ √|x-y|（√是 1/2-Hölder 连续的）
- 所以当 |x-y| < δ = ε² 时，|√x - √y| ≤ √δ = ε

**Required Verification:**
- δ 是否仅依赖于 ε 而不依赖于 x（一致连续的核心）
- 不等式的推导是否正确
- 另一种证明：在 [0,1] 用紧致性，在 [1,∞) 用导数有界

**Key Checks:**
- 一致连续 vs 普通连续的理解
- δ 的选择
- 不等式的使用

**Failure Modes:**
- 混淆一致连续和普通连续
- 错误地判定为不一致连续
- 证明中的不等式不严密

---

## 21. 抽象代数：群的性质

**Test ID:** TC-ALGEBRA-001  
**Input:** "设 G 是一个群，证明：若对任意 g∈G 有 g² = e，则 G 是交换群。"  
**Expected Classification:** abstract_algebra
**Expected Behavior:**
- 对于任意 a,b∈G，需要证明 ab = ba
- 已知：(ab)² = e → abab = e
- 两边左乘 a，右乘 b：a(abab)b = aeb → a²bab² = ab
- 因 a² = b² = e：ebab = ab → ab = ab（这不对，重新推导）
- 正确推导：(ab)² = e → abab = e
- 左乘 a：a(abab) = a → (a²)bab = a → bab = a
- 右乘 b：bab·b = ab → ba·b² = ab → ba = ab
- 得证 G 是交换群

**Required Verification:**
- 每一步的逻辑依据
- 检查群运算的结合律是否被正确使用
- 结论：ba = ab

**Key Checks:**
- 结合律的运用
- 每一步的合理性

**Failure Modes:**
- 跳过中间步骤，"显然"的推理
- 运算顺序搞反

---

## 22. 拓扑学：开集与闭集

**Test ID:** TC-TOPOL-001  
**Input:** "在实数集 R（配备标准拓扑）中，集合 A = [0,1) 是开集吗？是闭集吗？请解释。"  
**Expected Classification:** topology
**Expected Behavior:**
- 不是开集：0 ∈ A 但 0 的任何邻域 (-ε,ε) 不完全包含于 A（包含负数不在 A 中）
- 不是闭集：极限点 1 ∉ A（1 的每个邻域与 A 相交），但 A 不包含 1
- A = [0,1) 既不开也不闭
- 但若在子空间拓扑 [0,1] 中，则是开的……

**Required Verification:**
- 开集定义的逐点否定
- 闭集定义：补集 (-∞,0)∪[1,∞) 不是开集（1 的邻域不完全在补集中）

**Key Checks:**
- 区分"非开"和"闭"
- 区分"非闭"和"开"
- 准确应用定义

**Failure Modes:**
- 误判为开集
- 误判为闭集
- 混淆开闭的定义

---

## 23. 数论：模运算

**Test ID:** TC-NUMTH-001  
**Input:** "求 3^100 mod 7 的值。"  
**Expected Classification:** number_theory
**Expected Behavior:**
- 利用费马小定理：3⁶ ≡ 1 (mod 7)（因为 3 和 7 互素）
- 100 = 6×16 + 4
- 3¹⁰⁰ = 3⁶·¹⁶⁺⁴ ≡ (3⁶)¹⁶ · 3⁴ ≡ 1¹⁶ · 3⁴ ≡ 3⁴ (mod 7)
- 3⁴ = 81 ≡ 81 - 7×11 = 81 - 77 = 4 (mod 7)
- 答案：4

**Required Verification:**
- 费马小定理的适用性：3 和 7 互素 ✓
- 直接计算验证：3²=9≡2, 3³=6≡-1, 3⁴=18≡4 ✓
- 3¹⁰⁰ ≡ 4 (mod 7)

**Key Checks:**
- 费马小定理的引用
- 指数分解
- 模运算步骤

**Failure Modes:**
- 忘记验证互素条件
- 指数计算错误

---

## 24. 条件不足问题

**Test ID:** TC-INSUFF-001  
**Input:** "三角形的一条边长为 5，求面积。"  
**Expected Classification:** ambiguous_or_incomplete, geometry
**Expected Behavior:**
- **不应直接给出答案**
- 应指出：仅知一条边长无法确定三角形面积
- 说明需要什么额外信息（如高、角度、其他边长等）
- 可能给出面积的取值范围（>0 且 ≤ 通过不等式的上界）

**Required Verification:**
- 是否识别出条件不足
- 是否请求更多信息
- 是否说明原因

**Key Checks:**
- 绝对不要猜测或编造条件
- 诚实面对不确定性和不足条件

**Failure Modes:**
- 直接给出"答案"（最严重错误）
- 未意识到条件不足

---

## 25. 超出范围问题

**Test ID:** TC-OUTOFSCOPE-001  
**Input:** "What is the meaning of life?"  
**Expected Classification:** out_of_scope
**Expected Behavior:**
- 识别出这不是数学问题
- 礼貌地说明 Math.skill 的范围是数学问题
- 不尝试回答（即使回答 42 也是不恰当的）

**Required Verification:**
- 是否正确识别为非数学问题
- 回复是否专业

**Key Checks:**
- 不能当作数学问题处理
- 不能强行找数学角度回答

**Failure Modes:**
- 尝试用数学方式回答（"从概率角度看..."）
- 没有边界意识

---

## 26. 用户要求"仅给答案"

**Test ID:** TC-META-001  
**Input:** "解 x²-5x+6=0，只给答案就行。"  
**Expected Classification:** equation_solving
**Expected Behavior:**
- 理解用户要求"仅答案"
- 但在给出答案 (x=2, 3) 后，可以简洁地建议验证步骤
- 或者直接给出 x=2 或 x=3

**Required Verification:**
- 答案是否正确
- 是否尊重了用户的格式偏好
- 是否仍提供最小必要信息
- 是否可以回溯验证

**Key Checks:**
- 用户要求仅答案时，是否需要提供最小验证
- 权衡简洁性与正确性

**Failure Modes:**
- 忽略用户要求，输出冗长的完整解答
- 完全不给验证线索，用户无法确认

---

## 27. 用户要求"用初中方法"

**Test ID:** TC-META-002  
**Input:** "求函数 f(x)=x²-4x+3 在 [0,3] 上的最大值和最小值。用初中方法，不要用微积分。"  
**Expected Classification:** equation_solving, function_analysis
**Expected Behavior:**
- 用配方法：f(x) = (x-2)² - 1
- 对称轴 x=2 在区间 [0,3] 内
- 最小值在顶点：f(2) = -1
- 最大值在端点（离对称轴最远）：f(0) = 3, f(3) = 0 → 最大值为 3
- **不使用导数**

**Required Verification:**
- 是否使用了导数？（检查组）
- 二次函数顶点法和端点比较是否正确
- 端点比较是否完整

**Key Checks:**
- 遵守了方法限制（不用微积分）
- 用配方法/顶点法正确求解

**Failure Modes:**
- 使用了导数（违反方法限制）
- 忘记比较端点

---

## 28. 错误命题需要反例

**Test ID:** TC-PROOF-001  
**Input:** "判断真假：若数列 {a_n} 和 {b_n} 都发散，则 {a_n + b_n} 一定发散。证明或举反例。"  
**Expected Classification:** real_analysis, counterexample, sequence
**Expected Behavior:**
- 判断：假
- 反例：a_n = n, b_n = -n，则 a_n + b_n = 0（收敛）
- 说明：发散数列的和可能收敛

**Required Verification:**
- 反例是否正确
- 解释为什么是反例

**Key Checks:**
- 必须给出具体反例
- 不能说"显然为真"

**Failure Modes:**
- 错误地判断为真并"证明"
- 反例不合理

---

## 29. 学生解答中的细微错误

**Test ID:** TC-STUDENT-001  
**Input:** "学生解方程 √(x+5) = x-1 得到 x=4 和 x=-1，认为两个都是解。请检查学生的解答。"  
**Expected Classification:** equation_solving, solution_checking
**Expected Behavior:**
- 平方：x+5 = (x-1)² = x² - 2x + 1
- x² - 3x - 4 = 0 → (x-4)(x+1) = 0 → x=4 或 x=-1
- 检验 x=4：√9 = 3，4-1 = 3 ✓
- 检验 x=-1：√4 = 2，-1-1 = -2 ✗
- x=-1 是增根
- 最终解只有 x=4

**Required Verification:**
- 回代 x=-1 到原方程
- 说明为什么会出现增根（平方运算不是等价的）

**Key Checks:**
- 必须识别增根
- 必须解释增根产生的原因

**Failure Modes:**
- 认为学生完全正确
- 未发现增根

---

## 30. 生成概率问题

**Test ID:** TC-GEN-001  
**Input:** "给我出一道中等难度的概率题，并给出完整解答。"  
**Expected Classification:** problem_generation, probability_statistics
**Expected Behavior:**
- 生成一道完整的、自洽的概率题目
- 题目应包含所有必要信息
- 提供完整解答，包括步骤和最终答案
- 解答应包含验证

**Required Verification:**
- 题目是否有解
- 解答是否正确
- 难度是否确实是"中等"
- 题目是否自洽

**Key Checks:**
- 不能生成有歧义的题目
- 不能生成无解的题目
- 解答步骤是否完整

**Failure Modes:**
- 生成题目与解答不一致
- 题目有内在矛盾
- 难度不匹配

---

## 测试用例汇总

| Test ID | 类别 | 难度 | 关键风险 |
|---------|------|------|----------|
| TC-ARITH-001 | 算术 | 易 | 精度、舍入 |
| TC-ALG-001 | 代数 | 中 | 定义域遗漏 |
| TC-ALG-002 | 代数 | 易 | 判别式解读 |
| TC-ALG-003 | 代数 | 中 | 增根 |
| TC-LIN-001 | 代数 | 易 | 算术错误 |
| TC-INEQ-001 | 代数 | 中 | 符号表 |
| TC-FUNC-001 | 代数 | 中 | 交集 |
| TC-GEOM-001 | 几何 | 中 | 逻辑跳跃 |
| TC-TRIG-001 | 三角 | 中 | 公式错误 |
| TC-SEQ-001 | 数列 | 中 | 公式误用 |
| TC-COMB-001 | 组合 | 中 | 重复/遗漏 |
| TC-PROB-001 | 概率 | 中 | 条件混淆 |
| TC-CALC-001 | 微积分 | 中 | L'Hôpital 滥用 |
| TC-CALC-002 | 微积分 | 中 | 极值判断 |
| TC-CALC-003 | 微积分 | 中 | 换元错误 |
| TC-CALC-004 | 微积分 | 难 | 收敛性未验证 |
| TC-MULTI-001 | 多元 | 难 | 漏解 |
| TC-LINALG-001 | 线代 | 中 | 多项式因式分解 |
| TC-ODE-001 | 微分方程 | 中 | 积分因子 |
| TC-ANALYSIS-001 | 分析 | 难 | 一致连续理解 |
| TC-ALGEBRA-001 | 抽象代数 | 难 | 运算序 |
| TC-TOPOL-001 | 拓扑 | 中 | 开闭混淆 |
| TC-NUMTH-001 | 数论 | 中 | 费马小定理 |
| TC-INSUFF-001 | 边界 | 中 | 强行编造 |
| TC-OUTOFSCOPE-001 | 边界 | 易 | 边界意识 |
| TC-META-001 | 交互 | 易 | 格式偏好 |
| TC-META-002 | 交互 | 中 | 方法限制 |
| TC-PROOF-001 | 证明 | 中 | 反例意识 |
| TC-STUDENT-001 | 纠错 | 中 | 增根识别 |
| TC-GEN-001 | 生成 | 中 | 自洽性 |
