# ReAct: Synergizing Reasoning and Acting in Language Models

## Metadata

ICLR 2023. [Primary record](https://openreview.net/forum?id=WE_vluYUL-X).

## One-line idea

Interleave model-generated reasoning traces with environment actions and feed
observations back into the next reasoning step.

## Technical core and architecture

The model emits a repeated thought–action–observation sequence. Tools or an
interactive environment execute actions; the growing transcript is working
memory. The paper combines prompting demonstrations with external Wikipedia and
embodied task interfaces rather than training a new controller.

## Evaluation, insight, and limits

Question answering and decision-making tasks show that reasoning helps plans
while action supplies current evidence and reduces hallucination. The loop is a
foundational abstraction, but its state is untyped text, tools are trusted, and
reflection/authorization/recovery are not provided.

## Course placement and decision

**Candidate / short Week 1 background.** It supplies vocabulary used by later
papers; CodeAct and SWE-agent offer deeper interface mechanisms.
