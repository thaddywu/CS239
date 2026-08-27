# G-Designer: Architecting Multi-agent Communication Topologies via Graph Neural Networks

## Decision

**Candidate.** Primary source: [ICML 2025 proceedings](https://proceedings.mlr.press/v267/zhang25cu.html).

## One-line idea

Learn a sparse, task-dependent communication graph rather than choose chain,
star, tree, or fully connected coordination by hand.

## Technical core

A variational graph autoencoder represents agents plus a virtual task node and
decodes a communication topology. Sparsity, performance, and robustness enter
the objective, turning graph choice into a learned systems-design problem.

## Evidence and limits

- Six reasoning/code benchmarks show competitive performance with lower token
  use; HumanEval token reduction reaches 95.33% in the reported comparison.
- Virtual-node and graph-encoder ablations support the task-adaptive mechanism;
  the reported adversarial test loses only 0.3% accuracy.
- Agents mostly share one strong model and tasks lack durable shared state,
  concurrent tool effects, or distributed consistency requirements.

## Course role

Optional learned-topology competitor. The information-propagation paper remains
the better primary because it explains how errors and insights move, while
G-Designer optimizes a graph without supplying protocol semantics.
