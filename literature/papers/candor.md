# Hallucination to Consensus: Multi-Agent LLMs for End-to-End JUnit Test Generation

## Decision

**Rejected for the reading list after abstract-level inspection.** Primary
source: [ASE 2026 Journal First record](https://conf.researchr.org/details/ase-2026/ase-2026-journal-first/26/Hallucination-to-Consensus-Multi-Agent-LLMs-for-End-to-End-JUnit-Test-Generation).

## Mechanism and limitation

CANDOR assigns models specialized test-generation and oracle-review roles, then
uses a panel discussion and a dual-model summarization pipeline to obtain a
consensus assertion. The official abstract reports coverage, mutation, oracle,
and component-ablation results, but the central coordination mechanism remains
prompted model consensus: no symbolic oracle, independently checked invariant,
or protocol-level correctness boundary is apparent.

It is relevant evidence for multi-agent test generation, but it does not
displace AutoCodeSherpa's executable properties or ImpossibleBench's
unambiguous specification-gaming construction.
