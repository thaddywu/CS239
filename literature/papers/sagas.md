# Sagas

## Decision

**Selected for the final 20.** Primary metadata: [ACM SIGMOD 1987 DOI](https://doi.org/10.1145/38713.38742).

## Problem and mechanism

A long-lived transaction cannot hold every lock for hours or days without blocking shorter work and increasing abort cost. A saga decomposes it into an ordered sequence of independently committed, consistency-preserving transactions `T1 … Tn`. Each step may have a semantic compensating transaction `Ci`. If execution stops after `Tj`, backward recovery runs `Cj … C1`; when completion is mandatory and remaining steps are retryable, forward recovery continues `Tj+1 … Tn`. Savepoints, persistent code and compensation metadata, and a saga execution component make recovery survive crashes.

Compensation is not byte-for-byte rollback. Other transactions may observe a step before it is compensated, and a compensator must respect intervening state—for example, cancelling a reservation rather than restoring an old seat count. The paper also treats failed compensators, recovery blocks, implementation above an existing DBMS, and ordering constraints for parallel sagas.

## Evidence and limits

This is an abstraction and implementation-design paper, not a modern benchmark study. Its value is the precise semantic distinction among atomic rollback, backward compensation, and forward recovery. The application must supply correct compensators, some effects cannot be undone, and observers are not automatically notified that a previously visible result was compensated. Parallel execution introduces cascading-rollback and savepoint-consistency concerns.

## Course role

Sagas provides the vocabulary that most agent retry loops omit. It supports direct analysis of multi-step tool use after partial external effects and creates a productive contrast with Beldi's stronger but narrower transactional boundary.

## Reading-list v5 decision

**Strong candidate and instructor background, no longer primary.** The mechanism
remains essential, but the 1987 original does not consume a full assignment
under the v5 recency rule. No modern peer-reviewed agent-native replacement was
found; that absence is taught as a design gap.
