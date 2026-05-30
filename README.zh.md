# Math.skill

面向 AI 助手的综合数学推理技能。覆盖从基础算术到研究级数学的全部领域——具备严谨的分步推理、系统化验算和透明的不确定性处理。

[English Documentation](./README.md)

## 概述

Math.skill 是一款为 [skills.sh](https://www.skills.sh) / `npx skills` 设计的技能，赋予 AI 代理以下能力：

- **29 个数学领域**：算术、代数、方程、不等式、函数、几何、三角、数列、组合数学、概率、极限、微积分、线性代数、常微分方程、实分析、抽象代数、拓扑学、数论等
- **7 步推理流程**：题意解析 → 数学建模 → 方法选择 → 分步求解 → 验算 → 错误修正 → 最终答案
- **11 种验算方法**（A–K）：代回验算、定义域检查、边界分析、反向推导、数值抽样、量纲分析、极限/特殊情况检查、独立交叉验证、反例搜索、形式化逻辑检查、计算一致性检查
- **8 大高等数学模块**：极限、微分学、积分学、线性代数、常微分方程、实分析、抽象代数、拓扑学基础
- **34 类输入分类**系统
- **18 种交互策略**，覆盖各类 AI–用户数学对话场景
- **难题处理协议**，用于竞赛题、研究题和疑似未解问题
- **8 大类错误防护**机制
- **质量评分与验算评分**标准（各 100 分）

## 安装

```bash
npx skills add Wholiver/Math.Skill
```

## 结构

```
Math.skill/
├── SKILL.md                          # 主技能入口（含 YAML 前置元数据）
├── modules/                          # 9 个详细参考模块
│   ├── classification.md             # 34 类输入分类
│   ├── reasoning_workflow.md         # 7 步推理流程
│   ├── verification_engine.md        # 11 种验算方法（A–K）
│   ├── error_prevention.md           # 8 大类错误防护
│   ├── search_policy.md              # 搜索策略与准则
│   ├── hard_problem_protocol.md      # 难题处理协议
│   ├── higher_math_modules.md        # 8 大高等数学模块
│   ├── interaction_policy.md         # 18 种交互场景
│   └── output_templates.md           # 6 种输出模板
├── examples/                         # 24 个完整示例
│   ├── arithmetic.md, algebra.md, equations.md, inequalities.md
│   ├── functions.md, geometry.md, trigonometry.md, sequences.md
│   ├── probability.md, calculus.md, multivariable_calculus.md
│   ├── linear_algebra.md, ode.md, real_analysis.md
│   ├── abstract_algebra.md, topology.md, proof.md, counterexample.md
│   ├── solution_checking.md, problem_generation.md, hard_problem.md
│   ├── integration_example.md, definite_integral.md, modeling.md
├── tests/                            # 5 套测试用例（120+ 个测试）
│   ├── test_cases.md                 # 30 个标准测试
│   ├── adversarial_cases.md          # 15 个对抗性测试
│   ├── verification_tests.md         # 15 个验算引擎测试
│   ├── higher_math_tests.md          # 15 个高等数学测试
│   └── search_and_uncertainty_tests.md # 12 个搜索/不确定性测试
└── rubrics/                          # 评分标准
    ├── quality_rubric.md             # 100 分质量评分
    └── verification_rubric.md        # 100 分验算评分
```

**共计 41 个文件，约 11,000 行。**

## 核心设计原则

1. **正确性优先** — 每个答案至少通过两种验算方法检验
2. **透明可追溯** — 每一步推理都有解释和依据
3. **诚实面对不确定性** — 明确区分已解决问题与开放问题，不伪造引用或突破性结论
4. **领域感知** — 解题前先分类，选择适当方法和检查
5. **错误恢复** — 验算失败时回溯、修正并重新验算

## 使用场景

安装后，当用户提出数学问题时该技能会自动生效。AI 会：

- 对于简单方程 → 解析 → 求解 → 代回验算 → 确认 → 答案
- 对于证明题 → 分析 → 尝试反例 → 构造证明 → 逻辑检查 → 结论
- 对于研究问题 → 分类 → 搜索 → 从第一原则分析 → 明确已知与未知
- 检查学生解答 → 定位错误 → 修正 → 验算 → 解释

## 兼容平台

- Claude Code
- GitHub Copilot
- Cursor
- Windsurf
- 任何支持 [skills.sh](https://skills.sh) 技能的 AI 编程代理

## 许可证

MIT
