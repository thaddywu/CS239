# SagaLLM: Context Management, Validation, and Transaction Guarantees for Multi-Agent LLM Planning

## Decision

**Rejected as a primary despite PVLDB 2025 publication.** It is relevant, but
the evidence does not support the strength implied by "transaction guarantees."

## Mechanism

SagaLLM stores application, operation, and dependency state; generates workflow
and compensation agents; uses a global LLM validation agent before commits; and
invokes compensations in reverse dependency order after failures.

## Evidence and limits

The experiments study four REALM planning problems and mostly illustrate where
standalone models miss constraints or reactive replanning fails. They do not
provide a convincing comparison of durable logs, idempotent replay, isolation,
crash recovery, or real external-effect compensation against transactional
baselines. Many validation properties are delegated to another LLM, and the
paper explicitly relaxes ACID.

## Course role

Use only as a provocative comparison with Atomix or classical Sagas: adopting
transaction vocabulary is not equivalent to defining an enforceable settlement
boundary.
