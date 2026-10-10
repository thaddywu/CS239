# Fault-tolerant and transactional stateful serverless workflows

## Decision

**Strong v4 alternative to Sagas; no longer an additional primary.** Primary
metadata and paper: [OSDI 2020 proceedings](https://www.usenix.org/conference/osdi20/presentation/zhang-haoran).

## Problem and mechanism

Serverless platforms may retry a function after a timeout even when an earlier attempt has already changed state or invoked another function. Beldi makes stateful functions fault tolerant through atomic intent logging, re-execution, and an intent collector. Its linked **DAAL** representation stores application data and operation logs without requiring multi-key transactions from the underlying NoSQL store. The programming interface covers reads, writes, conditional writes, and function invocation.

For multi-function workflows, Beldi adds distributed transactions with opacity. Two-phase locking, wait-die deadlock prevention, shadow records, and two-phase commit are adapted to a setting in which each function owns its data; commit or abort is propagated through the invocation graph instead of delegated to a conventional central transaction manager. Invocation identifiers and recorded results make completed calls replayable without duplicating their effects.

## Evidence and limits

The evaluation implements movie-review, travel-reservation, and social-media applications and scales to 1,000 AWS Lambda workers. Transactions prevent consistency failures observed in nontransactional variants. Median overhead is below 2× at low load and roughly 2.4–3.3× at saturation, while reported p99 overhead is lower. The guarantee relies on mediated state operations over a strongly consistent NoSQL substrate. Arbitrary external APIs, irreversible physical effects, and semantic compensation remain outside its transaction boundary.

## Course role

Use instead of Sagas when the class should emphasize implementation: retry,
exactly-once effects, persistent state, and isolation become part of workflow
semantics. Sagas permits visible intermediate commits and repairs them
semantically; Beldi tries to preserve transactional opacity inside a controlled
state boundary.
