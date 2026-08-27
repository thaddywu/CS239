# AgentDojo: Dynamic Evaluation of Prompt Injection Attacks and Defenses

## Decision

**Strong candidate and security evaluation anchor.** Primary source: [NeurIPS 2024 proceedings](https://proceedings.neurips.cc/paper_files/paper/2024/hash/97091a5177d8dc64b1da8bf3e1f6fb54-Abstract-Datasets_and_Benchmarks_Track.html).

## Problem and mechanism

Prompt injection cannot be measured well with static strings because an agent must complete a legitimate task, read adversarial content, and exercise tools with consequential state. AgentDojo provides dynamic tool environments, user tasks, injection goals, attack variants, and defenses. It measures both utility and whether the attacker achieves the injected goal.

The initial release contains 97 realistic tasks and 629 security test cases across multiple application suites. Its extensibility and executable state make it a test harness rather than a prompt collection.

## Evidence and limits

Evaluations show no tested defense achieves both high utility and robust security; seemingly safer behavior can simply refuse useful actions. The benchmark has become a common substrate for later work including CaMeL.

Simulated applications and fixed attack goals cannot cover all web content, side channels, secret lifetimes, or cross-session memory. Benchmark robustness is not a proof, and optimizing against public attacks invites overfitting.

## Course role

Teach before CaMeL. AgentDojo supplies the observable failure and evaluation discipline; CaMeL supplies an architectural security claim. Students should report a two-dimensional utility/security result rather than an attack success number alone.
