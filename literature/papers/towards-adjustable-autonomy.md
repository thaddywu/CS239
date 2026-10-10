# Towards Adjustable Autonomy for the Real World

## Decision

**Strong v4 alternative; replaced as primary by Plan-Then-Execute.** Primary
metadata: [JAIR 17 (2002), 171–228](https://doi.org/10.1613/JAIR.1037).

## Problem and mechanism

One-shot rules—always ask the user, or always act autonomously—ignore response uncertainty and the coordination cost imposed on a team while a decision is pending. The paper defines a **transfer-of-control strategy** as a conditional sequence of control-transfer actions among agents and people plus `D` actions that deliberately change coordination constraints to buy time. A mathematical expected-utility model accounts for decision quality, response probability, wait cost, and miscoordination. A Markov decision process operationalizes the model, and user-specified constraints can require or forbid actions in parts of the policy.

## Evidence and limits

The Electric Elves system ran continuously for roughly seven months with ten research-group users, monitored nearly 700 meetings, and made thousands of autonomy decisions. Strategy analysis shows multi-step transfers are common; in randomly generated configurations, optimal strategies use multiple transfer actions in about 70% of cases. Parameter sweeps over 2,800-state policies test whether policy behavior changes sensibly and reveal sensitivity regions. Evidence is from a single organizational domain, utilities and response models must be estimated, and the formulation handles one isolated decision rather than interacting simultaneous decisions. The paper also reports privacy, security, and user-adaptation concerns.

## Course role

This is the formal alternative to the modern CHI reading. It turns “ask a human
when uncertain” into a costed sequential policy and shows that escalation itself
can create correctness failures through delay and miscoordination.
