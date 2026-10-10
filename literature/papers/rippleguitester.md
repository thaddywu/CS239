# RippleGUItester: Change-Aware Exploratory Testing

## Decision

**Candidate, not selected.** Primary metadata: [ISSTA 2026 research track](https://conf.researchr.org/details/issta-2026/issta-2026-research-papers/149/RippleGUItester-Change-Aware-Exploratory-Testing).

## Problem and mechanism

Desktop GUI changes can break interaction paths that ordinary unit tests do not cover, while an unconstrained exploration agent lacks change intent and historical fault knowledge. RippleGUItester combines the current pull request, blame-derived predecessor changes, and a scenario knowledge base mined from historical bugs. The model proposes change-relevant scenarios; retrieval supplies event sequences; a translator maps them into eleven executable GUI action types. The framework builds both pre-change and post-change versions, records a trace on one, replays it verbatim on the other, and combines pixel differences with multimodal intent classification to flag regressions.

## Evidence and limits

Across Firefox, Zettlr, JabRef, and Godot and 111 pull requests, the system reports 119 unique bugs; 26 persisted in current versions, 16 were fixed, and two were confirmed by developers. Its reported precision is 46.4% (148 true positives and 171 false positives), and on the Firefox ground-truth subset it finds 13 of 46 known bugs. GUI nondeterminism, replay mismatch, and multimodal classification remain major error sources; the evaluation covers four desktop applications and averages about $5.99 and 54.8 minutes per pull request.

## Course role

The system is technically richer than a prompt-only test generator, but CodaMOSA retains the primary slot: its explicit stagnation detector and return to algorithmic search isolate the hybrid mechanism more cleanly and rely on a stronger executable oracle.
