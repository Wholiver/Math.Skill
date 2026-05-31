<div align="center">

# Math.skill

> *"One question. A verified answer."*

[![License](https://img.shields.io/badge/License-MIT-blue.svg)](./LICENSE)
[![Agent-Agnostic](https://img.shields.io/badge/Agent-Agnostic-blueviolet)](https://skills.sh)
[![Skills](https://img.shields.io/badge/skills.sh-Compatible-green)](https://skills.sh)
[![11,007 Lines](https://img.shields.io/badge/11,007-Lines-orange)]()
[![41 Files](https://img.shields.io/badge/41-Files-8A2BE2)]()

[![English](https://img.shields.io/badge/English-blue?style=flat-square)](./README.md)
[![中文](https://img.shields.io/badge/中文-red?style=flat-square)](./README.zh.md)

</div>

**Type a math problem in your agent. Get back a rigorous, step-by-step, verified solution.**

From arithmetic to abstract algebra — Math.skill gives AI agents a disciplined mathematical workflow: every problem is parsed, modeled, solved with justifications, verified through multiple independent checks, and only then delivered as a final answer.

The verification engine is the core differentiator — no answer is output without passing at least two verification methods. And if the problem is a known open question (Goldbach, Riemann Hypothesis, etc.), the skill will tell you honestly rather than fabricating a breakthrough.

## Install & Go

```bash
npx skills add Wholiver/Math.Skill
```

## What Can It Do

| Capability | Deliverable | Typical Output |
|---|---|---|
| Standard Problem Solving | Full step-by-step solution · Back-substitution verification · Domain & boundary check | 5–15 steps |
| Proof & Reasoning | Logical structure · Counterexample search · Formal quantifier check | 10–20 steps |
| Solution Checking | Error pinpointing · Corrected derivation · Re-verification | 5–10 steps |
| Problem Generation | Well-posed problems · Full solutions · Grading rubric | 3–5 problems |
| Higher Math | Limit/calculus/linear algebra/ODE analysis · Theorem condition verification | 10–25 steps |
| Research-Level Problems | Honest uncertainty · Partial results · Failure path documentation | 10–30 steps |

## Core Mechanisms

### 7-Step Reasoning Workflow

Every problem goes through this pipeline:

| Step | Name | What Happens |
|---|---|---|
| 1 | Problem Parsing | Extract conditions, goals, variables, domains. Detect ambiguity, missing conditions, or errors |
| 2 | Mathematical Modeling | Build the formal representation: equation, function, set, matrix, probability space, etc. |
| 3 | Method Selection | Choose optimal strategy from 30+ methods (factorization, substitution, induction, L'Hôpital, etc.) |
| 4 | Step-by-Step Solution | Every transformation justified. No division by zero. Domain checked at each operation |
| 5 | Verification (see below) | 11 verification methods applied — multiple independent checks |
| 6 | Error Correction | If verification fails: locate, backtrack, fix, recalculate, re-verify |
| 7 | Final Answer | Clear conclusion with conditions, exact form, verification summary |

### 11 Verification Methods (A–K)

This is the heart of the skill. Each solution must pass at least 2 methods:

| ID | Method | What It Catches |
|---|---|---|
| A | **Back-substitution** | Substitute answer into original equation — catches extraneous roots |
| B | **Domain Check** | Denominator zero, radicand negative, log argument ≤ 0, etc. |
| C | **Boundary Analysis** | Missed endpoints, critical points, parameter boundary values |
| D | **Reverse Derivation** | Work backward to original — catches irreversible step errors |
| E | **Numerical Sampling** | Test specific values — catches sign errors, off-by-factor mistakes |
| F | **Dimensional Analysis** | Units mismatch, probability > 1, variance < 0 |
| G | **Limit & Special Cases** | Parameter → 0/∞, degenerate case consistency |
| H | **Independent Cross-Validation** | Solve with second method — algebraic + graphical, analytical + numerical |
| I | **Counterexample Search** | For universal claims, proof attempts — search low-dim, boundary, zero cases |
| J | **Formal Logic Check** | Quantifier order (∀∃ vs ∃∀), necessary vs sufficient, circular reasoning |
| K | **Computational Consistency** | Recompute, check matrix dimensions, verify det(A-λI)=0, total probability = 1 |

### 34-Category Input Classification

Before solving, the skill classifies the problem:

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

Each category has its own: recognition features, recommended strategies, must-check conditions, common errors, verification protocol, output format.

### Error Prevention Engine

8 categories of safeguards prevent the most common mathematical mistakes:

| Domain | Key Safeguards |
|---|---|
| **Algebra** | Re-expand after factoring · Check division by zero · Verify roots after squaring |
| **Inequality** | Sign reversal on multiply by negative · Case analysis for variable expressions |
| **Function** | Find domain first · Check non-differentiable points · Distinguish critical vs extremum |
| **Geometry** | Don't rely on visual intuition · State theorem conditions · Explain auxiliary lines |
| **Probability** | Define sample space · Check P∈[0,1] · Total probability = 1 · Variance ≥ 0 |
| **Calculus** | Check L'Hôpital conditions · State Taylor remainder · Add +C · Check convergence |
| **Linear Algebra** | Check matrix dimensions · Verify Av=λv · Auth A=PDP⁻¹ |
| **Abstract Math** | Check definition completeness · Quantifier order · Well-definedness |

### Hard Problem Protocol

When facing competition problems, research-level questions, or suspected open problems:

1. **Classify** — Standard textbook? Competition? Known open problem? Missing conditions?
2. **Search** — Known theorems, similar problems, open problem status
3. **If similar found** — Reference approach, re-derive independently, verify each step
4. **If nothing found** — From first principles: write definitions, decompose, try simple cases, construct counterexamples, induce, transform, establish lemmas
5. **If possibly unsolved** — Clearly state: verified facts vs conjectures vs numerical evidence vs failed approaches. Do NOT claim a breakthrough without a complete, gap-free, publicly verifiable proof.

## File Structure

```
Math.skill/
├── SKILL.md                           ← Core definition (693 lines)
├── modules/                           ← 9 detailed reference modules
│   ├── classification.md              ← 34-category input classification (1,567 lines)
│   ├── reasoning_workflow.md          ← 7-step workflow
│   ├── verification_engine.md         ← 11 verification methods A–K (598 lines)
│   ├── error_prevention.md            ← Error prevention for 8 domains
│   ├── search_policy.md               ← Search strategy & ethics
│   ├── hard_problem_protocol.md       ← Hard problem protocol
│   ├── higher_math_modules.md         ← 8 advanced math modules
│   ├── interaction_policy.md          ← 18 interaction scenarios (611 lines)
│   └── output_templates.md            ← 6 output format templates
├── examples/                          ← 24 worked examples (3,388 lines)
├── tests/                             ← 5 test suites, 120+ cases
│   ├── test_cases.md                  ← 30 standard tests
│   ├── adversarial_cases.md           ← 15 adversarial tests
│   ├── verification_tests.md          ← 15 verification engine tests
│   ├── higher_math_tests.md           ← 15 higher math tests
│   └── search_and_uncertainty_tests.md ← 12 search/uncertainty tests
└── rubrics/                           ← Scoring rubrics
    ├── quality_rubric.md              ← 100-point quality rubric
    └── verification_rubric.md         ← 100-point verification rubric
```

**41 files · 11,007 lines total.**

## Compatible With

- Claude Code · GitHub Copilot · Cursor · Windsurf · Codex · OpenCode
- Any AI coding agent that supports [skills.sh](https://skills.sh) skills

## License

MIT — use freely, attribution appreciated.
