# RepoProbe: Benchmarking Architecture-Aware Repository Comprehension with Checklists

## Decision

**Strong v4 alternative, not a primary architecture-recovery mechanism.** The
paper has an ASE 2026 proceedings DOI but the conference is after the review
date, so the index records it as `accepted_in_press`: [DOI](https://doi.org/10.1145/3832783.3837452).

## Mechanism and evidence

RepoProbe derives 500 open-ended architectural questions from real GitHub
Discussions across 50 repositories and 15 languages. Its verification protocol
decomposes maintainer answers into atomic binary checklist items with file-level
evidence. Across 20 models, the best overall score remains in the low 60% range;
checklist evaluation is substantially more stable than holistic scalar judging.
The paper also identifies **edit bias**: agents propose plausible modifications
before recovering the system constraint that motivated the request.

This is excellent negative evidence and a stronger architecture-understanding
evaluation than another repair benchmark. It does not construct, update, or
check a recovered architecture model, so it cannot fill the mechanism slot
vacated by Software Reflexion Models.

