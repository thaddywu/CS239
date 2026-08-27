# InjecAgent: Benchmarking Indirect Prompt Injections in Tool-Integrated Agents

## Metadata

Findings of ACL 2024. [Primary record](https://aclanthology.org/2024.findings-acl.624/).

## One-line idea

Embed attacker instructions in data returned by tools and measure whether an
agent executes the attacker's goal while serving a legitimate user task.

## Technical core

The benchmark combines 17 user tools, 62 attacker tools, user tasks, and attack
goals into 1,054 test cases. It targets indirect injection, where hostile content
arrives through external observations rather than the user prompt.

## Evaluation and limits

The reported ReAct GPT-4 setup is vulnerable in about 24% of cases, establishing
that tool data crosses the control boundary. Tool/task templates are mostly
static and evaluation emphasizes attack measurement rather than an enforceable
authorization mechanism.

## Course placement and decision

**Candidate / Week 9 optional.** Useful threat evidence, but AgentDojo and CaMeL
form the stronger benchmark-to-design progression.
