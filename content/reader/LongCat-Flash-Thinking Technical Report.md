---
title: LongCat-Flash-Thinking Technical Report
tags:
  - paper
---
### Overview

- 560B parameter MoE model (only 27B active)
- Open-source reasoning model from Meituan
- Beats most open-source models on math, coding, formal proving

### Training (2 Phases)

#### Phase 1: Cold-Start

**Mid-training**: Add STEM + coding data with curriculum learning to fix lack of reasoning patterns

**SFT** (3 specializations):

1. **General Reasoning**: STEM/code/logic problems with quality filtering
2. **Formal Proving**: Expert iteration to generate verified Lean4 proofs
3. **Agentic**: Dual-path selection to pick queries that NEED tools (64.5% token savings)

#### Phase 2: RL (Large-Scale)

**DORA System**: Asynchronous RL infrastructure

- Split into Standalone Generators + Elastic Roles
- Multiple policy versions, KV-cache reuse
- **Result**: >3x speedup vs synchronous methods

**Domain-Parallel Training**:

- Train separate STEM/Code/Agentic experts
- Merge them into one model (prevents negative transfer)

**Reward Models**:

- Non-verifiable: Discriminative model
- STEM: Generative model with reasoning (98.8% accuracy vs 80.9% rule-based)

### Key Results

**Strong**:

- AIME-25: 90.6% (competitive with o3)
- Formal proving: 67.6% vs DeepSeek 49.6% (+18%)
- Coding: 79.4% (SOTA open-source)
- Safety: Best overall

**Weaker**:

- General knowledge (MMLU-Pro): 82.6%
- Open-ended reasoning (Arena-Hard): 69.9%

### Key Innovations

1. **Domain-Parallel RL + Fusion**: Train experts separately, merge into Pareto-optimal model
2. **DORA System**: >3x RL speedup via asynchronous streaming architecture
3. **Dual-Path Tool Selection**: Select only queries that benefit from tools
4. **Generative Reward Models**: GenRM with reasoning explanations (98.8% accuracy)

### Resources

- ~20% of pre-training compute spent on RL
- 27B active / 560B total (MoE efficiency)

## References

- **Paper**: [LongCat-Flash-Thinking Technical Report](https://arxiv.org/pdf/2509.18883)