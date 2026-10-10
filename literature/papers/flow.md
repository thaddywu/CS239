# Flow: Modularized Agentic Workflow Automation

## Decision

**Rejected as a primary.** Primary source: [ICLR 2025 proceedings](https://proceedings.iclr.cc/paper_files/paper/2025/hash/ba84da6921f3040b74ee163aa7451f53-Abstract-Conference.html).

## Mechanism and evidence

Flow encodes subtasks, dependencies, status, outputs, and assigned roles in an
activity-on-vertex DAG. It selects LLM-generated graphs for parallelism and low
dependency complexity, executes ready nodes concurrently, and uses a global LLM
inspector to add, delete, rerun, or reassign subtasks after failure.

The graph vocabulary is direct and teachable, but the evidence consists of
three coding-oriented tasks against framework baselines. Correctness checks,
graph generation, and workflow repair remain model judgments; cloning an agent
sidesteps resource contention; the stated modularity theorem follows from a
simple independent-failure assumption. It does not establish consistency,
transactionality, or reliable allocation under real shared state.

## Course role

Illustrative workflow-engine example, not a stronger primary than Evolving
Orchestration, Information Propagation, or TraceFix.

