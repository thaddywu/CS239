# RefineAct: Automatic Runtime Verification of LLM Agent Actions

## Metadata

Accepted to ASE 2026; proceedings pending as of 2026-08-26.
[Author publication page](https://lab-design.github.io/papers/ASE-26/).

## One-line idea

Translate an instruction into formal goals and refine a plan with
pre/postconditions so a runtime can allow, confirm, or block individual actions.

## Technical core

RefineAct expresses task goals and safety properties in first-order Prolog,
generates a refinement plan, and checks intercepted calls against expected
state transitions and risky patterns. Monitor feedback can trigger replanning.

## Evaluation and limits

On 144 ToolEmu tasks, the paper reports reducing failure from 77% to 39% and
raising average task quality from 1.0 to 1.9. Natural-language-to-formal
translation is itself fallible, ToolEmu is simulated, and final artifact review
is pending.

## Course placement and decision

**Candidate / Week 9 watch reading.** Recheck final ASE proceedings, artifacts,
and policy-translation ablations before promotion.
