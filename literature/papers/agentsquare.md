# AgentSquare: Automatic LLM Agent Search in Modular Design Space

## Decision

**Selected for reading-list v6.** Primary source:
[ICLR 2025 proceedings](https://proceedings.iclr.cc/paper_files/paper/2025/hash/0ae94013da7cd459402fd77874e09ee3-Abstract-Conference.html).

## Mechanism and evidence

AgentSquare normalizes prior agents into four modules with uniform interfaces:
planning, reasoning, tool use, and memory. It searches the resulting design
space through module recombination, module evolution, and an in-context
performance predictor. Across six web, embodied, tool, travel, and planning
benchmarks, the paper reports a 17.2% average gain over the best included
hand-designed agents.

The paper is unusually useful pedagogically because an agent design becomes an
explicit tuple rather than an inseparable prompt stack. Its ablations, however,
mostly isolate search operations rather than the causal value of each of the
four ingredients. The workflow connecting the modules is fixed, the authors
state that the design space is incomplete, and several discovered agents omit
tools or memory entirely. Interface semantics, validators, policies, runtimes,
and durable state are outside the abstraction.

## Course role

Best current overview paper for the question “what are the main cognitive
modules, and how can they be composed?” It should be paired with SWE-agent or
Agentix, which expose system boundaries that its four-module taxonomy omits.

In v6 it replaces CodeAct as the architecture overview; CodeAct remains the
instructor comparison for expressive action languages.
