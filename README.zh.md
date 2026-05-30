# Math.skill

> *"一道题。一个经过验算的答案。"*

[![License](https://img.shields.io/badge/License-MIT-blue.svg)](./LICENSE)
[![Agent-Agnostic](https://img.shields.io/badge/Agent-Agnostic-blueviolet)](https://skills.sh)
[![Skills](https://img.shields.io/badge/skills.sh-Compatible-green)](https://skills.sh)
[![11,007 Lines](https://img.shields.io/badge/11,007-行-orange)]()
[![41 Files](https://img.shields.io/badge/41-文件-8A2BE2)]()

[![English](https://img.shields.io/badge/English-blue?style=flat-square)](./README.md)
[![中文](https://img.shields.io/badge/中文-red?style=flat-square)](./README.zh.md)

**在 AI 代理中输入一道数学题。返回严谨的分步推导、系统化验算后的可靠答案。**

从小学算术到抽象代数——Math.skill 赋予 AI 代理一套规范的数学工作流：每道题都经过题意解析、数学建模、方法选择、分步求解、多轮验算，最后才能给出答案。

验算引擎是核心差异——没有通过至少两种验算方法的答案不会被输出。如果问题是哥德巴赫猜想这样的已知未解问题，技能会诚实地告诉你，而不是编造一个突破性结论。

## 安装即用

```bash
npx skills add Wholiver/Math.Skill
```

## 能力一览

| 能力 | 交付物 | 典型输出量 |
|---|---|---|
| 标准解题 | 完整分步推导 · 代回验算 · 定义域及边界检查 | 5–15 步 |
| 证明与推理 | 逻辑结构 · 反例搜索 · 形式化量词检查 | 10–20 步 |
| 解答检查 | 定位错误 · 修正推导 · 重新验算 | 5–10 步 |
| 题目生成 | 设计良好的题目 · 完整解答 · 评分标准 | 3–5 题 |
| 高等数学 | 极限/微积分/线性代数/ODE 分析 · 定理条件验证 | 10–25 步 |
| 研究级问题 | 诚实面对不确定性 · 部分结果 · 失败路径记录 | 10–30 步 |

## 核心机制

### 7 步推理流程

每道题都经过以下流水线：

| 步骤 | 名称 | 内容 |
|---|---|---|
| 1 | 题意解析 | 提取条件、目标、变量、定义域。检测歧义、缺失条件或题目错误 |
| 2 | 数学建模 | 建立形式化表达：方程、函数、集合、矩阵、概率空间等 |
| 3 | 方法选择 | 从 30+ 种方法中选取最优策略（因式分解、换元、归纳、洛必达等） |
| 4 | 分步求解 | 每步变换都有数学依据。不除以零。每一步检查定义域 |
| 5 | 验算（见下文） | 应用 11 种验算方法——至少两种独立检查 |
| 6 | 错误修正 | 验算失败时：定位 → 回溯 → 修正 → 重算 → 重验 |
| 7 | 最终答案 | 清晰结论，附带条件范围、精确形式、验算摘要 |

### 11 种验算方法（A–K）

这是技能的核心。每道题至少通过 2 种方法验算：

| 编号 | 方法 | 能发现的问题 |
|---|---|---|
| A | **代回验算** | 代入原式检查相等性——发现增根、漏解 |
| B | **定义域检查** | 分母为零、根号为负、对数为负、反三角函数范围越界等 |
| C | **边界分析** | 漏掉端点、临界点、参数分界值 |
| D | **反向推导** | 从答案反推回原式——发现不可逆变换引入的增根 |
| E | **数值抽样** | 选取特值代入——发现符号错误、系数偏差 |
| F | **量纲分析** | 单位不匹配、概率大于 1、方差为负等 |
| G | **极限与特例** | 参数趋于 0/∞ 时的退化情形一致性 |
| H | **独立交叉验证** | 用第二种方法重解——代数法＋图像法、解析法＋数值法 |
| I | **反例搜索** | 对全称命题、证明尝试——搜索低维、边界、零元等情形 |
| J | **逻辑量词检查** | ∀∃ 顺序、充分必要条件、循环论证、未证明前提 |
| K | **计算一致性** | 复算关键计算、检查矩阵维度、验证 det(A-λI)=0、总概率=1 |

### 34 类输入分类

解题前先分类，每类有独立的验算策略：

```
calculation | algebra_simplification | equation_solving | system_of_equations
inequality_solving | function_analysis | geometry | analytic_geometry
trigonometry | sequence | combinatorics | probability_statistics | limit
differentiation | integration | multivariable_calculus | linear_algebra
ordinary_differential_equation | complex_analysis | real_analysis
abstract_algebra | topology | number_theory | discrete_math | optimization
mathematical_modeling | proof | counterexample | solution_checking
problem_generation | research_level_problem | ambiguous_or_incomplete
out_of_scope
```

每个类别定义了：识别特征、推荐策略、必须检查的条件、常见错误、验算协议、输出格式。

### 错误防护引擎

8 大类防护机制预防常见数学错误：

| 领域 | 关键防护 |
|---|---|
| **代数** | 展开后反向因式分解 · 检查除以零 · 平方后验根 |
| **不等式** | 乘除负数变号 · 含变量表达式分类讨论符号 |
| **函数** | 先求定义域 · 检查不可导点 · 极值≠最值 |
| **几何** | 不依赖图形直觉 · 说明定理条件 · 解释辅助线目的 |
| **概率** | 定义样本空间 · 检查 P∈[0,1] · 总概率=1 · 方差≥0 |
| **微积分** | 检查洛必达条件 · 说明泰勒余项 · 加 +C · 检查反常积分收敛性 |
| **线性代数** | 检查矩阵维度 · 验证 Av=λv · 验证 A=PDP⁻¹ |
| **抽象数学** | 检查定义完整性 · 量词顺序 · 良定义性 |

### 难题处理协议

面对竞赛题、研究级问题或疑似开放问题时的流程：

1. **分类** — 标准教材？竞赛？已知未解问题？条件缺失？
2. **搜索** — 相关定理、相似题目、开放问题状态
3. **找到相似题** — 参考思路、独立重推、逐步骤验算
4. **没有相似题** — 从定义出发：写出定义、分解目标、尝试简单情形、构造反例、归纳、变换、建立引理
5. **可能是未解问题** — 明确区分：已验证事实 vs 猜想 vs 数值证据 vs 失败路径。未经完整可验证证明，不得宣称突破性结论。

## 文件结构

```
Math.skill/
├── SKILL.md                           ← 核心定义（693 行）
├── modules/                           ← 9 个详细参考模块
│   ├── classification.md              ← 34 类输入分类（1,567 行）
│   ├── reasoning_workflow.md          ← 7 步推理流程
│   ├── verification_engine.md         ← 11 种验算方法 A–K（598 行）
│   ├── error_prevention.md            ← 8 大类错误防护
│   ├── search_policy.md               ← 搜索策略与准则
│   ├── hard_problem_protocol.md       ← 难题处理协议
│   ├── higher_math_modules.md         ← 8 大高等数学模块
│   ├── interaction_policy.md          ← 18 种交互场景（611 行）
│   └── output_templates.md            ← 6 种输出模板
├── examples/                          ← 24 个完整示例（3,388 行）
├── tests/                             ← 5 套测试，120+ 用例
│   ├── test_cases.md                  ← 30 个标准测试
│   ├── adversarial_cases.md           ← 15 个对抗性测试
│   ├── verification_tests.md          ← 15 个验算引擎测试
│   ├── higher_math_tests.md           ← 15 个高等数学测试
│   └── search_and_uncertainty_tests.md ← 12 个搜索/不确定性测试
└── rubrics/                           ← 评分标准
    ├── quality_rubric.md              ← 100 分质量评分
    └── verification_rubric.md         ← 100 分验算评分
```

**41 个文件 · 11,007 行代码。**

## 兼容平台

- Claude Code · GitHub Copilot · Cursor · Windsurf · Codex · OpenCode
- 任何支持 [skills.sh](https://skills.sh) 技能的 AI 编程代理

## 许可证

MIT — 自由使用，保留原作者署名。
