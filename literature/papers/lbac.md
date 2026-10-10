# Language-Based Agent Control

## Decision

**Strong preprint frontier; not a published primary.** Current source is
[arXiv 2605.12863](https://arxiv.org/abs/2605.12863).

## Mechanism

LBAC embeds both agent-generated programs and application scaffolding in one
pure typed host language. Policies become types/effects: abstract values enforce
data provenance, unforgeable path capabilities confine filesystem access, and
LIO labels enforce information flow. Recursive subagents inherit the same or a
strictly narrower effect type, so delegation cannot relax a parent's policy.

## Evidence

TYPE GUARD implements the model in Haskell through three case studies. On the
AgentDojo Slack suite its information-flow configuration has task utility
statistically comparable to CaMeL and resists all evaluated direct and
"important instructions" injections, while allowing confined subagents to keep
tool access.

## Limits

The guarantee inherits the soundness and complete mediation of the host
language and policy library; foreign calls or unsafe scaffolding would enlarge
the trusted base. The quantitative comparison covers only 21 benign Slack tasks
and 105 injection combinations, and restrictive IFC policies reduce utility for
flows that cannot be proven safe.

## Course role

LBAC is the most conceptually distinct unpublished challenger to CaMeL: it asks
students to treat an agent application, including recursive subagents and
scaffolding, as one typed program rather than a prompt loop plus filters.
