# Augmenting Large Language Models with Chemistry Tools (ChemCrow)

## Metadata

Nature Machine Intelligence 2024. [Primary record](https://www.nature.com/articles/s42256-024-00832-8).

## One-line idea

Give a ReAct-style model 18 chemistry-specific expert tools and connect selected
plans to robotic synthesis.

## Technical core

Tools cover literature search, molecular properties, reaction prediction, and
synthesis planning/execution. The model selects/composes tools and revises from
their observations; expert and model evaluations compare chemistry task quality.

## Evaluation and limits

The study includes diverse chemistry questions and physical synthesis examples,
showing that expert tools can compensate for base-model knowledge limits. The
general architecture largely inherits ReAct, evaluation includes subjective
judgments, and physical safety/generalization depend on extensive domain
scaffolding.

## Course placement and decision

**Candidate / Week 10 case.** Interesting closed-loop application, not yet a
general mechanism-rich primary reading.
