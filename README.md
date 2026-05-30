# Math.skill

A comprehensive mathematical reasoning skill for AI assistants. Covers everything from basic arithmetic to research-level mathematics — with rigorous step-by-step reasoning, systematic verification, and transparent uncertainty handling.

[中文文档](./README.zh.md)

## Overview

Math.skill is a skill for [skills.sh](https://www.skills.sh) / `npx skills` that equips AI agents with:

- **29 mathematical domains**: arithmetic, algebra, equations, inequalities, functions, geometry, trigonometry, sequences, combinatorics, probability, limits, calculus, linear algebra, ODEs, real analysis, abstract algebra, topology, number theory, and more
- **7-step reasoning workflow**: problem parsing → modeling → method selection → derivation → verification → error correction → final answer
- **11 verification methods** (A–K): back-substitution, domain check, boundary analysis, reverse derivation, numerical sampling, dimensional analysis, limit/special-case checks, independent cross-validation, counterexample search, formal logic verification, computational consistency check
- **8 higher math modules**: limits, differentiation, integration, linear algebra, ODEs, real analysis, abstract algebra, topology basics
- **34-category input classification** system
- **18 interaction strategies** for common AI–user math scenarios
- **Hard problem protocol** for competition, research, and possibly unsolved problems
- **Error prevention** for 8 common mistake categories
- **Quality & verification rubrics** (100-point each)

## Installation

```bash
npx skills add Wholiver/Math.Skill
```

## Structure

```
Math.skill/
├── SKILL.md                          # Main skill entry (with YAML frontmatter)
├── modules/                          # 9 detailed reference modules
│   ├── classification.md             # 34-category input classification
│   ├── reasoning_workflow.md         # 7-step workflow
│   ├── verification_engine.md        # 11 verification methods (A–K)
│   ├── error_prevention.md           # Error prevention for 8 domains
│   ├── search_policy.md              # Search strategy & ethics
│   ├── hard_problem_protocol.md      # Hard problem handling
│   ├── higher_math_modules.md        # 8 advanced math modules
│   ├── interaction_policy.md         # 18 interaction scenarios
│   └── output_templates.md           # 6 output format templates
├── examples/                         # 24 worked examples
│   ├── arithmetic.md, algebra.md, equations.md, inequalities.md
│   ├── functions.md, geometry.md, trigonometry.md, sequences.md
│   ├── probability.md, calculus.md, multivariable_calculus.md
│   ├── linear_algebra.md, ode.md, real_analysis.md
│   ├── abstract_algebra.md, topology.md, proof.md, counterexample.md
│   ├── solution_checking.md, problem_generation.md, hard_problem.md
│   ├── integration_example.md, definite_integral.md, modeling.md
├── tests/                            # 5 test suites (120+ test cases)
│   ├── test_cases.md                 # 30 standard tests
│   ├── adversarial_cases.md          # 15 adversarial tests
│   ├── verification_tests.md         # 15 verification engine tests
│   ├── higher_math_tests.md          # 15 higher math tests
│   └── search_and_uncertainty_tests.md # 12 search/uncertainty tests
└── rubrics/                          # Scoring rubrics
    ├── quality_rubric.md             # 100-point quality rubric
    └── verification_rubric.md        # 100-point verification rubric
```

**41 files, ~11,000 lines total.**

## Key Design Principles

1. **Correctness first** — Every answer goes through at least two verification methods
2. **Transparency** — Every reasoning step is explained and justified
3. **Honesty with uncertainty** — Open problems are clearly distinguished from solved ones; no fabricated citations or breakthroughs
4. **Domain awareness** — The skill classifies problems before solving, using appropriate methods and checks
5. **Error recovery** — If verification fails, the skill backtracks, fixes, and re-verifies

## Usage Examples

After installation, the skill is available when a user asks a math question. The AI will:

- For a simple equation: parse → solve → back-substitute → verify → answer
- For a proof: analyze → attempt counterexample → formulate proof → logic-check → conclude
- For a research problem: classify → search → analyze from first principles → state what's known and what's not
- For student solution checking: identify errors → correct → verify → explain

## Compatible With

- Claude Code
- GitHub Copilot
- Cursor
- Windsurf
- Any AI coding agent that supports [skills.sh](https://skills.sh) skills

## License

MIT
