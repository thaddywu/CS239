# Solving Olympiad Geometry without Human Demonstrations (AlphaGeometry)

## Decision

**Strong candidate; use if room permits a neuro-symbolic case.** Primary source: [Nature 2024](https://www.nature.com/articles/s41586-023-06747-5).

## Problem and mechanism

Symbolic geometry engines can exhaustively derive consequences but often need auxiliary constructions that expand the problem. A neural model proposes those constructions; a symbolic deduction engine closes the consequences and either solves the theorem or gives the next state for further proposals. Training uses roughly 100 million synthetically generated theorem/proof examples rather than human olympiad demonstrations.

This is not a generic conversational agent. It is a tightly coupled search system in which learned generation supplies exogenous terms and the symbolic component supplies exact deductive closure.

## Evidence and limits

AlphaGeometry solves 25 of 30 geometry problems from the selected IMO benchmark period, approaching the reported human-gold-medalist level and far exceeding the prior symbolic baseline. Solutions can be checked by the domain engine.

The domain has a clean formal language, strong synthetic generator, and exact checker—conditions absent from much of software engineering. Diagram interpretation and informal-to-formal translation are not the main evaluated bottleneck. Compute and data generation are substantial.

## Course role

Use to ask which software tasks admit the same division: learned proposal of invariants, summaries, or edit obligations followed by sound analysis. Pair with IRIS rather than presenting it as evidence that general LLM agents reason formally.
