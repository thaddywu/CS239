# Agentic Memory: Learning Unified Long-Term and Short-Term Memory Management for Large Language Model Agents

## Decision

**Strong candidate and architecture background; not in the v3 primary 20.** Primary source: [ACL 2026 proceedings](https://aclanthology.org/2026.acl-long.981/).

## One-line idea

AgeMem turns storing, retrieving, updating, summarizing, and discarding memory
into first-class agent actions, then learns a joint long-/short-term memory
policy with progressive reinforcement learning.

## Technical core

The same policy manages persistent records and the active context through tool
calls. A three-stage rollout separates memory construction, future-task use,
and context management; step-wise GRPO supplies denser credit than answer-only
training. This is more than retrieval augmentation because deletion and
compression are actions whose timing changes future state.

## Evidence and limits

- Across five long-horizon benchmarks, the reported average rises from 28.05 to
  41.96 on Qwen2.5-7B and from 43.97 to 54.31 on Qwen3-4B versus no memory.
- Component ablations support distinct contributions from long-term memory,
  short-term context control, and reinforcement learning.
- The study covers only 4B/7B open models; learned behavior depends on designed
  rewards, and benchmark answers provide supervision unavailable in many real
  deployments.

## Course role

Primary constructive memory reading. Pair with the empirical failure study on
experience-following and use MemGPT as architectural history rather than the
best current evidence.
