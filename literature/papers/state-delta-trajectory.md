# Augmenting Multi-Agent Communication with State Delta Trajectory

## Decision

**Candidate; background for multi-agent communication.** Primary source:
[EMNLP 2025 / ACL Anthology](https://aclanthology.org/2025.emnlp-main.518/).

## Mechanism and evidence

State Delta Encoding augments natural-language messages with token-wise changes
in selected transformer hidden states. The receiving agent injects those deltas
while retaining its own profile and local context. Experiments cover private-
information QA, multi-agent debate, and sequential workflows; deltas outperform
natural language and a hidden-state baseline most clearly on harder reasoning
tasks. Layer-selection and original-state-versus-delta ablations support the
specific representation choice.

The method requires white-box access and sufficiently compatible models, adds
high-dimensional communication bandwidth, and primarily transfers latent
reasoning rather than shared world state. CARD and information-propagation
topologies better fit the course's systems-design question.

