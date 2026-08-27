# Improving Factuality and Reasoning through Multiagent Debate

## Metadata

ICML 2024. [Primary record](https://proceedings.mlr.press/v235/du24e.html).

## One-line idea

Multiple instances independently answer, read one another's responses, revise
over rounds, and aggregate a final decision.

## Technical core

The procedure is deliberately simple: repeated cross-conditioning and majority
aggregation, without learned topology or a privileged verifier. It provides the
baseline protocol from which later topology and fault-propagation work departs.

## Evaluation and limits

Reported gains cover factuality and reasoning tasks. However, agents often share
the same model and correlated biases; extra samples and majority voting are
confounded with interaction. The ICLR 2024 self-correction paper finds matched
response-budget debate can be no better than self-consistency.

## Course placement and decision

**Candidate / Week 7 background.** Historically important, but not a primary
reading after stronger causal topology and faulty-agent work.
