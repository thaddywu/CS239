# How Memory Management Impacts LLM Agents

## Decision

**Selected for the final 20-paper-day list.** Primary source: [ACL 2026 proceedings](https://aclanthology.org/2026.acl-long.27/).

## One-line idea

Controlled memory addition and deletion experiments show that agents imitate
retrieved experiences strongly enough to propagate old errors and replay
successful but misaligned behavior.

## Technical core

The paper varies unfiltered, automatic-evaluator, and strict additions plus
periodic, history-based, and combined deletion across four agent setups. Its
central construct—experience-following—connects input similarity to output
similarity and makes memory quality a state-management problem rather than a
larger-vector-store problem. Later task outcomes can become delayed quality
signals for stored records.

## Evidence and limits

- Noisy additions can compound errors; strict selection helps, while deletion
  helps only when its utility evaluator is reliable.
- History-based deletion can sharply reduce memory size, but a coarse evaluator
  can delete useful experience and hurt performance.
- The operation set is deliberately limited to addition/deletion, with no merge,
  summarization, schema evolution, or consistency theory.

## Course role

Primary negative/diagnostic reading. It supports discussion of provenance,
invalidation, evaluator trust, and why persistent memory creates failure modes
that stateless context selection does not.
