# ZeroTIR: Tool‑Integrated Reinforcement Learning From a General Base Model

Welcome to the official repository for **ZeroTIR**, a reproducible framework that trains a general‑purpose language model to discover and exploit code execution tools using only outcome‑level rewards. This repository provides:

* full training curves and checkpoints (ZTRL‑0727‑7B),
* statistical analyses of tool‑usage dynamics,
* benchmark comparisons against larger closed‑ and open‑source systems,
* and references to recent work on Tool‑Integrated Reasoning (TIR).

---

## 1 Statistical Test Summary

| Item                                | Value |
|------------------------------------|-------|
| Aligned data points                | 500   |
| Step range                         | 1 – 500 |

### Spearman Correlation Analysis

| Variable | Description | Mean | Std Dev |
|----------|-------------|------|---------|
| `train/rule_rewards` | training accuracy | 0.3759 | 0.0677 |
| `train/code_rewards` | code ratio        | 0.6629 | 0.3678 |

* Spearman ρ = 0.6863  
* p‑value = 7.06 × 10⁻⁷¹  
* Pearson r = 0.6637 (for reference)  
* n = 500  

Interpretation: strong, positive, highly significant (p < 0.001).

Visualization saved to  
`/mnt/data/maixinji/spearman_correlation_analysis.png`.

#### Research Question  
Does training accuracy monotonically correlate with code ratio during RL?

#### Result  
Spearman analysis indicates a strong positive relationship  
(ρ = 0.686, p = 7.06 × 10⁻⁷¹, n = 500).

#### Conclusion  
Higher training accuracy is associated with higher code usage.

---

## 2 Checkpoints and Curves

All checkpoints and raw curves are provided in the `checkpoints/` and `logs/` directories.  
Performance numbers for Qwen‑3 and Claude baselines are available at  
<https://huggingface.co/Qwen/Qwen3-235B-A22B-Instruct-2507>.

---

## 3 Benchmark Results

### Closed‑ vs Open‑Source Comparison (avg@32)

| Dataset | ZTRL‑0727‑7B | Qwen3‑238B‑A22B | Claude Optus4 |
|---------|--------------|-----------------|---------------|
| AIME25  | 29.99 % | 24.7 % | 33.9 % |
| HMMT25  | 22.08 % | 10.0 % | 15.9 % |

### Validation Trajectory

| Steps |100|200|300|400|500|600|700|800|900|
|-------|---|---|---|---|---|---|---|---|---|
|AIME25 |12.18|25.00|28.22|28.12|28.02|28.12|29.79|32.81|29.99|
|HMMT25 | 8.54|18.95|21.14|20.83|20.62|22.08|24.16|21.25|22.08|

### TORL vs ZeroTIR (Greedy)

| Dataset | Ours | TORL |
|---------|------|------|
| AIME25  | 32.81 % | 30 % |
| AMC23   | 80 %   | 75 % |
| MATH500 | 84.6 % | 82.2 % |

---

## 4 Related TIR Work

1. SimpleRL‑Zoo: Investigating and Taming Zero Reinforcement Learning for Open Base Models in the Wild  
2. DAPO: An Open‑Source LLM Reinforcement Learning System at Scale  
3. ToRL: Scaling Tool‑Integrated RL  
4. Qwen2.5‑Math Technical Report: Toward a Mathematical Expert Model via Self‑Improvement  
5. When2Call: When (not) to Call Tools  
6. T‑Eval: Evaluating the Tool Utilization Capability of Large Language Models Step by Step  
7. Behavior Injection: Preparing Language Models for Reinforcement Learning  
8. OctoThinker: Mid‑training Incentivizes Reinforcement Learning Scaling  

---

## 5 Our Contribution

* Earliest exploration of a scaling law for spontaneous code use in math‑oriented RL.
* First empirical Agent‑RL scaling study in the math domain, including environment masking and asynchronous scheduling.
* Quantified link between compute investment and emergence of effective tool‑augmented reasoning.
* Reproducible benchmark framework usable with standard RL algorithms across domains.

These contributions were highlighted by reviewers MhKq, cNww, and 96Y3, and have received strong interest within the TIR community.

---
