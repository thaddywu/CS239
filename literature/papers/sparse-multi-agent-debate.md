# Improving Multi-Agent Debate with Sparse Communication Topology

## Metadata

Findings of EMNLP 2024. [Primary record](https://aclanthology.org/2024.findings-emnlp.427/).

## One-line idea

Vary which debating agents can communicate and show that sparse graphs can
match or outperform dense all-to-all exchange at lower cost.

## Technical core

The study treats graph connectivity as an independent variable across debate
rounds and tasks. Sparse edges limit repeated/correlated messages and token cost,
challenging the assumption that more communication always improves consensus.

## Evaluation and limits

Experiments compare several topology families and establish the empirical
precursor to later information-propagation models. The explanation is mostly
behavioral; it does not fully separate useful and erroneous diffusion or model
how task-specific graphs should be learned.

## Course placement and decision

**Candidate / Week 7 optional.** Superseded as a primary by the EMNLP 2025 causal
propagation paper, but retained as its direct competing/predecessor approach.
