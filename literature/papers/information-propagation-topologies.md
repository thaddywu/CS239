# Understanding Information Propagation Effects of Communication Topologies

## Decision

**Selected for the final 20-paper-day list.** Primary source: [EMNLP 2025 / ACL Anthology](https://aclanthology.org/2025.emnlp-main.623/).

## Problem and mechanism

Multi-agent communication graphs transmit both useful insights and errors. The paper introduces Counterfactual Agent Propagation Effect (CAPE): intervene on one agent's output and measure whether the collective prediction changes under a fixed graph. It analyzes how graph sparsity changes error and insight diffusion.

EIB-Learner then combines views learned from dense and sparse graphs with a GNN-based topology optimizer. The objective is not maximal connectivity; it is sufficient access to complementary insights without letting every bad output contaminate every node.

## Evidence and limits

- Experiments cover six datasets and compare predefined and learned graph structures on effectiveness, communication cost, and robustness.
- Moderately sparse structures repeatedly provide the best balance, motivating task-specific graph construction.
- The intervention is a useful causal probe but still operates inside synthetic benchmark episodes. Agents often share base models and prompts, so real organizational diversity is limited.
- A learned graph can overfit task distributions and does not by itself authenticate messages or contain malicious authority.

## Course role and comparisons

This is the preferred topology reading. Pair with the earlier sparse-debate paper for the empirical precursor and Multi-Agent Resilience for explicit faulty-node injection. It displaces “different personas talk in a room” as the center of the multi-agent week.
