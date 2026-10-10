# AutoCodeSherpa: Symbolic Explanations in AI Coding Agents

## Decision

**Selected for reading-list v5; accepted in press at ISSTA 2026.** Primary
source: [ISSTA 2026 research program](https://conf.researchr.org/details/issta-2026/issta-2026-research-papers/70/AutoCodeSherpa-Symbolic-Explanations-in-AI-Coding-Agents).

## Mechanism and evidence

AutoCodeSherpa generates a symbolic explanation of an issue as input,
infection, and output conditions, then turns it into property-based tests and
program-internal formulas. Generation and refinement are separate stages, and
the executable artifacts are used for localization and patch rejection. With
GPT-5-mini, reported property generation succeeds on 86.6% of issues and 73.4%
of generated properties are correct; validation rejects 105 of 245 incorrect
patches, 123% more than the strongest compared baseline. Added to Agentless, it
improves top-1 file localization by 19%, element localization by 55.7%, and
plausible patches by 60.7%.

The study includes cross-model and refinement ablations, but is confined to
Python SWE-bench Verified and relies on manual semantic labels. A generated
explanation can still faithfully test an incomplete interpretation of the issue.

## Course role

This is a stronger modern testing reading than a second repair controller: it
asks whether an independently executable explanation can validate a patch.
