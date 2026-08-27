# Identifying the Risks of LM Agents with an LM-Emulated Sandbox (ToolEmu)

## Metadata

ICLR 2024. [Primary record](https://proceedings.iclr.cc/paper_files/paper/2024/hash/7274ed909a312d4d869cc328ad1c5f04-Abstract-Conference.html).

## One-line idea

Use a model to emulate tool execution and generate adversarial initial states so
risky agent behavior can be tested cheaply without real-world harm.

## Technical core

Tool interfaces define a simulated sandbox; an emulator returns plausible state
transitions and an adversarial component constructs cases likely to expose harm.
Another evaluation procedure scores helpfulness and safety across high-stakes
toolkits.

## Evaluation and limits

The benchmark covers 36 toolkits and 144 test cases; reported agents exhibit
failures in 68.8% of cases, with human validation of simulated trajectories.
Model-based emulator/evaluator errors can correlate with the tested agent, and
simulated semantics omit real races, permissions, and irreversible side effects.

## Course placement and decision

**Candidate / Week 9 optional.** Strong scalable testing idea; AgentDojo provides
the more concrete dynamic environment and CaMeL the deeper defense mechanism.
