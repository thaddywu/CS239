# Language Agent Tree Search Unifies Reasoning, Acting, and Planning

## Metadata

ICML 2024. [Primary record](https://icml.cc/virtual/2024/poster/33107).

## One-line idea

Use Monte Carlo tree search to organize model-generated actions, environment
feedback, self-reflections, and model value judgments.

## Technical core

The model serves as policy/proposer and evaluator inside an MCTS loop. Nodes are
interaction states; rollouts explore candidate trajectories; reflections from
failed trials enter later search. This turns linear ReAct into explicit branching
and backtracking.

## Evaluation and limits

Results span reasoning, programming, and embodied/web-style tasks and improve
over linear prompting baselines. Search is expensive, LM value estimates are
correlated with LM generation errors, and benchmark environments offer cleaner
state/feedback than consequential tools.

## Course placement and decision

**Candidate / Week 2 optional.** Technically richer than prompt-only planning,
but LLM-Modulo supplies the sharper controversy about external validators.
