# ChipNeMo: Domain-Adapted LLMs for Chip Design

## Decision

**Rejected as an agentic primary reading; retained as a boundary case.** Primary source: [NVIDIA Research record](https://research.nvidia.com/publication/2023-10_chipnemo-domain-adapted-llms-chip-design).

## Contribution

ChipNeMo develops a domain tokenizer, continued pretraining, instruction tuning, and retrieval for chip-design assistance. The applications—engineering chat, bug summaries, and script generation—are industrially meaningful and the adaptation study is substantive.

## Why it is rejected here

The core technical question is domain adaptation of an LM, not an agent architecture. There is no central stateful action/observation loop, tool authority model, recovery mechanism, or runtime validation contribution. Calling these applications “agents” would erase the course boundary between a specialized model and an autonomous software actor.

## Reconsideration condition

Reconsider as prerequisite/domain context for a hardware week, or if integrated follow-up work evaluates a closed EDA loop with explicit intermediate representations, tool failures, verification, rollback, and PPA tradeoffs. ChatEDA is closer to that loop but still mechanism-light compared with the main corpus.
