# RepairAgent: An Autonomous, LLM-Based Agent for Program Repair

## Decision

**Strong candidate, likely optional if the repair week is crowded.** Primary source: [ICSE 2025 program](https://conf.researchr.org/details/icse-2025/icse-2025-research-track/160/RepairAgent-An-Autonomous-LLM-Based-Agent-for-Program-Repair).

## Problem and mechanism

RepairAgent narrows an agent to program repair through repair-specific tools, dynamic prompt/context updates, and a finite-state machine that constrains progress across exploration, patching, testing, and termination. The FSM is important: autonomy is bounded by an explicit protocol rather than an unconstrained shell loop.

## Evidence and limits

- The study uses Defects4J and reports 164 repaired bugs, including 39 not previously repaired by the compared systems.
- Reported average consumption is roughly 270k tokens per bug, making effectiveness/cost tradeoffs visible.
- Defects4J is mature and executable but dominated by Java unit-test repair; general repository issues, build failures, and underspecified requests may behave differently.
- A plausible patch that passes tests may still overfit. The finite states guide process but do not strengthen the oracle.

## Course role and comparisons

RepairAgent is useful if the week focuses on control protocols: contrast its FSM with AutoCodeRover's analysis-guided retrieval and Agentless's completely fixed phases. If limited to two repair readings, AutoCodeRover plus Agentless create the sharper conceptual contrast.
