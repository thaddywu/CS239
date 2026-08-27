# QuickCheck: A Lightweight Tool for Random Testing of Haskell Programs

## Metadata

ICFP 2000. [DOI](https://doi.org/10.1145/351240.351266).

## One-line idea

State executable properties and automatically generate typed random inputs to
search for counterexamples.

## Technical core

Properties are ordinary Haskell functions; type-directed generators produce
inputs, and combinators customize distributions and conditional domains. The
key abstraction is reusable specification plus generator, not a list of examples.

## Evaluation and limits

The paper demonstrates concise properties and practical bug discovery. Original
QuickCheck lacks the sophisticated shrinking and state-machine features of later
versions, and useful properties/generators require human semantic knowledge.

## Course placement and decision

**Candidate / short Week 4 foundation.** It is included to reveal a major gap:
current repair agents generate tests but rarely create durable properties and
input models.
