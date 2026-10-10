# CodaMOSA: Escaping Coverage Plateaus in Test Generation with Pre-trained LLMs

## Decision

**Selected for the final 20-paper-day list.** Primary source: [ICSE 2023 program](https://conf.researchr.org/details/icse-2023/icse-2023-technical-track/132/CodaMOSA-Escaping-Coverage-Plateaus-in-Test-Generation-with-Pre-trained-Large-Langua).

## Problem and mechanism

Search-based test generation explores executions effectively but stalls on code requiring semantically meaningful constants or call sequences. CodaMOSA runs MOSA-style evolutionary search first. Only when coverage plateaus does it query a pretrained code model for tests targeting under-covered functions; successful model-generated tests seed the evolutionary population, after which ordinary search resumes.

## Evidence and limits

- The evaluation spans 486 Python benchmark modules and compares pure search, pure model generation, and hybrid configurations.
- Timing the model call at an observed plateau is the key ablation-worthy idea: the expensive probabilistic component fills a specific search weakness.
- Coverage is necessary but not an adequacy guarantee, and generated assertions may be weak or absent.
- It is not an autonomous conversational agent. That is a strength for the course: it prevents agent vocabulary from obscuring a more precise hybrid algorithm.

## Course role and comparisons

Use to introduce “LLM-Modulo” engineering in testing. Compare with CoverUp's iterative coverage dialogue and QuickCheck's durable, human-stated properties. A central seminar question is why current coding agents optimize test passage rather than discover reusable properties and generators.

## Reading-list v5 decision

**Strong candidate, no longer primary.** The stagnation-triggered hybrid remains
one of the cleanest search/LLM handoffs. AutoCodeSherpa wins the scarce v5 slot
because its issue-specific conditions are executable validation artifacts, not
only new test seeds.
