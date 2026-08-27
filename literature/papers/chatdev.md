# ChatDev: Communicative Agents for Software Development

## Decision

**Rejected as a primary reading; useful comparison artifact.** Primary source: [ACL 2024 / ACL Anthology](https://aclanthology.org/2024.acl-long.810/).

## What it does

ChatDev encodes a waterfall process as sequential design, coding, review, and testing subtasks. Each subtask uses an instructor/assistant dialogue between specialized role prompts. “Communicative dehallucination” asks an agent to request missing detail before proceeding.

## Why it is not central

The chat chain is a hand-authored workflow, and social role labels are not an independently evaluated coordination mechanism. The experiments do not give the matched single-agent, equal-compute comparison needed to attribute gains to collaboration. Generated greenfield applications also avoid the repository state, regression risk, and ambiguous issue specifications that make software maintenance technically revealing.

The paper is not dismissed as useless: natural-language and code-language exchanges are inspectable, and the artifact helped popularize end-to-end workflows. It is rejected because the seminar must prioritize mechanisms that generalize beyond the metaphor of a software company.

## Reconsideration condition

Reconsider for a history or adoption week, or if follow-up work isolates communicative dehallucination under realistic missing-requirement faults.
