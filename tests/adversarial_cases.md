# Math.skill 对抗性测试用例

> 本文档包含 15 个专门设计用于"欺骗"系统的对抗性测试用例。
> 每个用例都包含容易被忽视的陷阱，用于测试 Math.skill 的防御能力和严谨性。

---

## 1. 平方引入增根

**Test ID:** ADV-001  
**Input:** "解方程 \(\sqrt{x+3} = x+1\)"  
**Expected Classification:** algebra, radical_equation, extraneous_root_trap  
**Expected Behavior:**
- 平方：x+3 = (x+1)² = x² + 2x + 1
- x² + x - 2 = 0 → x = 1 或 x = -2
- 回代 x=1：√4 = 2, 1+1 = 2 ✓
- 回代 x=-2：√1 = 1, -2+1 = -1 ✗
- x = -2 是增根 → 最终解 x = 1

**Required Verification:**
- 必须回代到原方程
- 必须显式说明 x=-2 是增根以及原因

**Key Checks:**
- 平方两边是不是等价变换？
- 每个解是否都回代了？

**Failure Modes:**
- 直接给两个解，未检查
- 解释增根原因不够清晰

---

## 2. 除以可能为零的表达式

**Test ID:** ADV-002  
**Input:** "解方程 \(\frac{x^2-1}{x-1} = x+1\)，注意 x≠1"  
**Expected Classification:** algebra, rational_equation, removable_singularity_trap  
**Expected Behavior:**
- 注意：即使提示了 x≠1，仍需严谨
- 当 x≠1 时，分子因式分解 (x-1)(x+1)
- 左 = x+1（x≠1 时）
- 方程变为 x+1 = x+1（对所有 x≠1 成立）
- 解为：x ∈ ℝ \ {1}（所有不等于 1 的实数）
- 注意：x=1 时分母为零，原式无定义

**Required Verification:**
- 不能给出 x=1
- 需要理解这不是"无解"，而是"无穷多解（除 1 外）"
- 可能要用极限观点：lim_{x→1} 左 = 2 = 右，但 x=1 处函数无定义

**Key Checks:**
- 是否给出 x 可以是任何实数（除 1 外）？
- 是否说明 x=1 被排除的原因？

**Failure Modes:**
- 说"恒等式，x ∈ ℝ"而遗漏 x≠1（严重）
- 错误地称"无解"
- 直接代入 x=1 认为成立

---

## 3. 有理不等式中的符号表陷阱

**Test ID:** ADV-003  
**Input:** "解不等式 \(\frac{x-1}{x^2-4} \leq 0\)"  
**Expected Classification:** algebra, rational_inequality, sign_chart_trap  
**Expected Behavior:**
- 分子零点：x = 1
- 分母零点（必须排除！）：x = -2, x = 2
- 符号表检验区间：(-∞,-2), (-2,1), (1,2), (2,∞)
- 注意 ≤0：分子为 0 时（x=1）不等式成立（0 ≤ 0 ✓）
- 分母为 0 时必须排除（函数无定义）
- 解集：(-2, 1] ∪ (2, ∞)
  - 验证：x=-3 负数/正数=负<0 → (-∞,-2): 否！
  - 重新算：x=-3: (-4)/(5)=-0.8<0 ✓
  - x=0: (-1)/(-4)=0.25>0 ✗
  - x=1.5: 0.5/(-1.75)<0 ✓
  - x=3: 2/5>0 ✗
- 正确解集：(-∞,-2) ∪ (1, 2) ？需要仔细算
  - x=-3: (-4)/(5) = -0.8 ✓ → (-∞,-2) ✓
  - x=0: (-1)/(-4) = 0.25 ✗ → (-2,1) ✗
  - x=1: 0/(-3) = 0 ✓ → x=1 ✓
  - x=1.5: 0.5/(-1.75) = -0.29 ✓ → (1,2) ✓
  - x=3: 2/5 = 0.4 ✗ → (2,∞) ✗
- 解集：(-∞, -2) ∪ [1, 2)

**Required Verification:**
- 符号表的每个区间是否正确
- 含等于号时分子零点的处理
- 分母零点的正确处理

**Key Checks:**
- 符号表制作是否正确
- x=1 处的不等式方向（含等号）
- x=-2 和 x=2 处的定义域排除

**Failure Modes:**
- 符号表错误
- x=1 处的开闭区间搞混
- 分母零点未正确排除

---

## 4. 隐藏定义域限制的复合函数

**Test ID:** ADV-004  
**Input:** "求函数 \(f(x) = \frac{\ln(x^2-1)}{\sqrt{x-2}}\) 的定义域。"  
**Expected Classification:** algebra, domain_analysis, composite_function_trap  
**Expected Behavior:**
- 分母 √(x-2) 条件：x-2 > 0 → x > 2（平方根内的必须 > 0 因为还在分母中）
- 等一下：√(x-2) 作为分母 → x-2 > 0 → x > 2
- 对数条件：ln(x²-1) 要求 x²-1 > 0 → x < -1 或 x > 1
- 取交集：x > 2 与 (x < -1 或 x > 1) = x > 2
- 定义域：(2, ∞)

**Required Verification:**
- 每个组成部分的条件
- 交集计算是否考虑了两部分
- 端点检验：x=2 时分母为零

**Key Checks:**
- 平方根内必须是 ≥0 还是 >0（取决于是否在分母）
- 对数的条件
- 正确取交集

**Failure Modes:**
- 忘记分母中平方根的条件
- 交集计算错误

---

## 5. L'Hôpital 法则看起来适用但不行

**Test ID:** ADV-005  
**Input:** "求极限 \(\lim_{x \to 0} \frac{x^2 \sin(1/x)}{x}\)"  
**Expected Classification:** calculus, limit, LHopital_not_applicable  
**Expected Behavior:**
- 尝试 L'Hôpital：分子导数 = 2x sin(1/x) + x² cos(1/x) · (-1/x²) = 2x sin(1/x) - cos(1/x)
- 分母导数 = 1
- 但 lim_{x→0} cos(1/x) 不存在！所以 L'Hôpital 不适用
- 正确方法：约分 x：lim_{x→0} x sin(1/x) = 0（夹逼定理：-x ≤ x sin(1/x) ≤ x）
- **L'Hôpital 的逆命题不成立**：导数之比的极限存在是充分非必要条件

**Required Verification:**
- 必须指出为什么 L'Hôpital 不适用
- 用夹逼定理验证
- 说明 L'Hôpital 法则的条件

**Key Checks:**
- 是否滥用了 L'Hôpital？
- 是否理解了 L'Hôpital 的使用条件？

**Failure Modes:**
- 误用 L'Hôpital 并得出不存在/错误的极限
- 声称极限不存在（实际上存在且为 0）

---

## 6. 误导性几何图：不可能三角形

**Test ID:** ADV-006  
**Input:** "三角形 ABC 中，AB=5, BC=7, CA=13。文字描述，求三角形面积。"  
**Expected Classification:** geometry, triangle_inequality_check, impossible_figure  
**Expected Behavior:**
- 检查三角不等式：5+7 = 12 < 13
- 这不满足三角不等式！
- 这样的三角形不存在
- 不应给出面积，而应指出三角形不可能存在
- 如果强行用海伦公式，s = (5+7+13)/2 = 12.5
- √(12.5·7.5·5.5·(-0.5)) 会有负的被开方数

**Required Verification:**
- 三角不等式检查
- 明确声明三角形不存在
- 解释为何海伦公式会给出虚数

**Key Checks:**
- 关键陷阱：是否会盲目用海伦公式？
- 是否会忽略最基本的几何公理？

**Failure Modes:**
- 不对边长作合理性检查
- 强行用海伦公式
- 给出一个面积值

---

## 7. 微妙的独立性假设

**Test ID:** ADV-007  
**Input:** "事件 A 和 B 满足 P(A)=0.5, P(B)=0.4, P(A∪B)=0.7。问 A 和 B 是否独立？"  
**Expected Classification:** probability, independence_test, common_trap  
**Expected Behavior:**
- 由加法公式：P(A∪B) = P(A) + P(B) - P(A∩B)
- 0.7 = 0.5 + 0.4 - P(A∩B) → P(A∩B) = 0.2
- 检查独立性：P(A)·P(B) = 0.5 × 0.4 = 0.2
- P(A∩B) = 0.2 = P(A)·P(B)
- 所以 A 和 B 是独立的！

**Required Verification:**
- 正确应用加法公式
- 正确的独立性检验
- 数值演算

**Key Checks:**
- 陷阱：许多人会直接代入 P(A∪B)=P(A)+P(B)（互斥假设）
- 必须用加法公式正确推导

**Failure Modes:**
- 误认为不独立（直觉有时误导）
- 计算 P(A∩B) 错误

---

## 8. 换元积分中的定义域陷阱

**Test ID:** ADV-008  
**Input:** "计算定积分 \(\int_{-1}^1 \frac{dx}{1+x^2}\)"  
**Expected Classification:** calculus, definite_integral, substitution_domain  
**Expected Behavior:**
- 反导数：arctan(x)
- ∫_{-1}^{1} dx/(1+x²) = arctan(1) - arctan(-1) = π/4 - (-π/4) = π/2
- 如果换元 x = tan θ，需要注意 θ 的范围
- x ∈ [-1,1] → θ ∈ [-π/4, π/4]
- ∫ dx/(1+x²) = θ|_{θ=-π/4}^{θ=π/4} = π/4 - (-π/4) = π/2

**Required Verification:**
- 如果换元，定义域变换是否正确
- 答案 π/2
- 直接方法和换元方法一致

**Key Checks:**
- 换元时区间变换是否正确
- 积分值是否正确

**Failure Modes:**
- 换元时区间映射错误
- 忘记改变积分限

---

## 9. 比率检验法失效的级数

**Test ID:** ADV-009  
**Input:** "判断级数 \(\sum_{n=1}^\infty \frac{n!}{n^n}\) 的敛散性。"  
**Expected Classification:** calculus, series_convergence, ratio_test_edge  
**Expected Behavior:**
- 比率检验：a_n/a_{n+1} = ... 
- 实际上：lim_{n→∞} a_{n+1}/a_n = lim_{n→∞} (n+1)!/(n+1)^(n+1) · n^n/n!
  = lim n^n/(n+1)^n = lim (n/(n+1))^n = lim (1 - 1/(n+1))^n = 1/e
- 1/e < 1，由比率检验知级数收敛
- 这和直觉不同（一些人会觉得 n! 增长很快所以发散）

**Required Verification:**
- 比率检验的极限是否正确
- 结果 < 1 的含义
- 其他检验方法（如斯特林公式）

**Key Checks:**
- 陷阱：直觉判断可能出错
- 比率检验极限计算的代数是否正确

**Failure Modes:**
- 凭直觉判断发散
- 比率检验极限计算错误

---

## 10. 矩阵维度不匹配

**Test ID:** ADV-010  
**Input:** "设 A 是 2×3 矩阵，B 是 3×2 矩阵。求证 AB 和 BA 都有意义但不经历相同。计算 tr(AB) 和 tr(BA) 的关系。"  
**Expected Classification:** linear_algebra, matrix_multiplication, trace_properties  
**Expected Behavior:**
- AB 是 2×2，BA 是 3×3
- tr(AB) = tr(BA) = Σ_i Σ_j a_{ij} b_{ji}（迹的循环性质，即使维度不同也成立）
- 但 AB ≠ BA，因为它们维度不同

**Required Verification:**
- 维度推理
- 迹的循环性质的应用
- 不能错误地说 AB = BA

**Key Checks:**
- 陷阱：可能错误地认为 AB = BA
- 迹的性质
- 维度理解

**Failure Modes:**
- 说 AB = BA
- 不理解迹的循环性质
- 维度混乱

---

## 11. 隐藏除以零的"证明"

**Test ID:** ADV-011  
**Input:** "以下证明有什么问题？设 a=b，则 a²=ab, a²-b²=ab-b², (a-b)(a+b)=b(a-b), a+b=b, 2b=b, 2=1。"  
**Expected Classification:** algebra, error_detection, division_by_zero  
**Expected Behavior:**
- 从 (a-b)(a+b) = b(a-b) 到 a+b = b 这一步除以了 (a-b)
- 但已知 a=b，所以 a-b = 0
- 除以零的步骤是非法的
- 这解释了为什么得到了矛盾的结果

**Required Verification:**
- 精确定位除以零的步骤
- 说明为什么非法
- 展示正确的推导（不能消去零因子）

**Key Checks:**
- 是否能找到错误的精确位置？
- 是否解释了错误的原理？

**Failure Modes:**
- 找不到隐藏的除以零
- 认为"证明显然有问题"但不精确指出

---

## 12. 贝叶斯定理的误解

**Test ID:** ADV-012  
**Input:** "某种疾病在人群中的患病率是 0.1%。检测方法的灵敏度是 99%（有病被检出阳性的概率），特异度也是 99%（没病被检出阴性的概率）。某人检测结果为阳性，问他实际患病的概率是多少？"  
**Expected Classification:** probability, Bayes_theorem, base_rate_fallacy  
**Expected Behavior:**
- 这不是 99%！
- P(患病|阳性) = P(阳性|患病)P(患病) / P(阳性)
  = 0.99 × 0.001 / (0.99×0.001 + 0.01×0.999)
  = 0.00099 / (0.00099 + 0.00999)
  = 0.00099 / 0.01098
  ≈ 0.0902 ≈ 9%
- 尽管检测很准，但因为基础患病率极低，阳性结果中只有约 9% 真正患病

**Required Verification:**
- 贝叶斯公式应用
- 全概率公式计算 P(阳性)
- 数值计算

**Key Checks:**
- 陷阱：很多人直接说 99%
- 基础概率谬误
- 贝叶斯推理

**Failure Modes:**
- 直接回答 99%（最常见的贝叶斯错误）
- 公式使用错误

---

## 13. 看似不活跃的约束条件

**Test ID:** ADV-013  
**Input:** "在约束 x² + y² ≤ 1 下，求 f(x,y) = x + y 的最大值和最小值。"  
**Expected Classification:** optimization, constrained_optimization, boundary_check  
**Expected Behavior:**
- 无约束临界点：∇f = (1,1) ≠ (0,0) → 无内部临界点
- 约束在边界 x²+y²=1 上达到极值
- Lagrange 乘子法或直接解：x=cos θ, y=sin θ → f(θ)=cos θ + sin θ = √2 sin(θ+π/4)
- 最大值 √2（θ=π/4），最小值 -√2（θ=5π/4）

**Required Verification:**
- 检查内部是否有临界点
- 边界上求极值
- 约束是否活跃

**Key Checks:**
- 陷阱：可能误以为约束不活跃
- 边界分析

**Failure Modes:**
- 忽略约束条件
- 不用 Lagrange 乘子法或参数化

---

## 14. 参数方程中不完整的分类讨论

**Test ID:** ADV-014  
**Input:** "解关于 x 的方程 \(ax^2 + (a-1)x - 1 = 0\)（a 为参数）。"  
**Expected Classification:** algebra, parametric_equation, case_analysis  
**Expected Behavior:**
- 情况 1：a = 0 → 方程变为 -x - 1 = 0 → x = -1
- 情况 2：a ≠ 0 → 二次方程
  - 判别式：Δ = (a-1)² + 4a = a² - 2a + 1 + 4a = a² + 2a + 1 = (a+1)² ≥ 0
  - x = [-(a-1) ± |a+1|] / (2a)
  - 子情况 2a：a+1 ≥ 0（a ≥ -1 且 a≠0）
    - x₁ = -(a-1+a+1)/(2a) = -1
    - x₂ = -(a-1-a-1)/(2a) = 2/(2a) = 1/a
  - 子情况 2b：a+1 < 0（a < -1）
    - x₁ = 1/a
    - x₂ = -1

**Required Verification:**
- a=0 的处理
- a≠0 的情况覆盖
- 判别式的含参分析
- 讨论的完整性

**Key Checks:**
- 陷阱：忘记 a=0 时方程退化
- 判别式中的 a 的处理
- 分类的完整性

**Failure Modes:**
- 忘记 a=0 的情况
- 判别式开方时忘记绝对值
- 分类讨论不完整

---

## 15. 答案正确但理由错误

**Test ID:** ADV-015  
**Input:** "学生回答：因为 \(\sqrt{16} = \pm 4\)。这个说法对吗？"  
**Expected Classification:** arithmetic, notation, conceptual_error  
**Expected Behavior:**
- 不对！
- 符号 √(16) 在实数范围内**定义为**非负平方根，即 4
- 方程 x² = 16 的解是 x = ±4，但这和 √16 = ±4 不同
- √ 符号是函数，定义为主平方根（非负的那个）
- 如果学生说 √16 = ±4，这是符号的误用

**Required Verification:**
- 区分 √ 符号和"平方根"概念的区别
- 指出学生的概念混淆

**Key Checks:**
- 是否理解 √ 符号的准确定义？
- 是否能区分开方运算和方程求解？

**Failure Modes:**
- 同意学生说法
- 未能清晰区分两个概念

---

## 对抗性测试用例汇总

| Test ID | 陷阱类型 | 风险等级 | 核心防御 |
|---------|----------|----------|----------|
| ADV-001 | 平方引入增根 | 高 | 回代检验 |
| ADV-002 | 除以零 | 高 | 定义域检查 |
| ADV-003 | 符号表陷阱 | 高 | 逐区间检验 |
| ADV-004 | 隐藏定义域 | 中 | 逐条件分析 |
| ADV-005 | L'Hôpital 滥用 | 高 | 条件验证 |
| ADV-006 | 不可能图形 | 高 | 三角不等式 |
| ADV-007 | 独立性直觉陷阱 | 中 | 公式计算 |
| ADV-008 | 换元定义域 | 中 | 区间变换 |
| ADV-009 | 直觉与公式矛盾 | 中 | 严格计算 |
| ADV-010 | 矩阵维度陷阱 | 中 | 维度检查 |
| ADV-011 | 隐藏除以零 | 高 | 代数审查 |
| ADV-012 | 贝叶斯谬误 | 高 | 基础概率 |
| ADV-013 | 约束活跃性 | 中 | 边界分析 |
| ADV-014 | 参变量分类不完 | 高 | 完整讨论 |
| ADV-015 | 概念混淆 | 中 | 定义准确性 |
