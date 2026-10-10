# Revisable by Design: A Theory of Streaming LLM Agent Execution

## Decision

**Rejected as a primary reading in this round; reconsider after peer review and broader evaluation.** Primary record: [arXiv 2604.23283](https://arxiv.org/abs/2604.23283).

## Problem and mechanism

Streaming execution lets a user revise a goal while an agent is already acting. The paper models an execution as thought, action, observation, and injection events; separates rollbackable epistemic state from world state; and classifies actions as idempotent/read-only, reversible, compensable, or irreversible. A Revision Absorber locates the earliest event conflicting with a new instruction, rolls back the suffix when semantics allow it, and replans. The formal result makes achievable revision flexibility depend on the reversibility of prior actions.

## Evidence and limits

StreamBench injects revisions into three synthetic workflows—event planning, travel, and report publication. Experiments use DeepSeek-V3 for the main 1,008 cases, smaller cross-model checks, and a mock model for scaling; an LLM judge assesses quality. The absorber approaches full-restart quality while reducing wasted steps by up to 14.6×. The theorem rests on deliberately simplified action semantics, the workflows are synthetic, and evaluation depends heavily on model judging. The current record is a 2026 preprint from Fudan University and Guangming Laboratory rather than a peer-reviewed publication.

## Course role

Its reversibility taxonomy is useful vocabulary for the correctness audit, but Sagas supplies a mature compensation semantics and Beldi supplies implemented transactional replay under stronger evidence.
