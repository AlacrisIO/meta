# Plan

Identify the Skills & Time required for each part of the project

## Tasks

### Logical Specification

#### Description

* Write a logical specification of each chain in a logic language,
  say Coq (but it could also be K, or any suitable logic system).
  [Who: logic expert, finance expert, security expert]

* Prove essential properties of the specification.
  [Who: logic expert, finance expert, security expert]

* Extract operator (client/server) software from the logical specification.
  [Who: logic expert, finance expert, application expert, network expert, a bit security expert.]

* Extract contract/law (Game arbiter) from the logical specification.
  [Who: logic expert, a bit application expert, a bit security expert.]

* Extract lawyer (winning strategy) software from the logical specification.
  [Who: logic expert, application expert, a bit security expert.]

* Extract third party litigation from the logical specification.
  [Who: logic expert, application expert, security expert.]

#### Skills

* [Logic expert] Theoretical understanding of proof systems, their capabilities and their limits
* [Logic expert] Practical knowledge of Coq (or K, etc.), using it, developing proofs, tactics, etc.
* [Logic expert] Experience with program extraction
* [Finance expert] Domain-specific understanding of the blockchain structure and its invariants
* [Security expert] Adversarial thinking
* [Security expert] Knowledge of existing attack models

#### Resources

* Full-time senior logic expert.
* Full-time junior logic expert.
* Part-time application expert.
* Part-time security expert.
* Part-time network expert.

### Network Engineering

#### Description

* Enhance the Gossip network for the main chain so it can include all data of all side-chains.

* Design the Gossip network so maximum assurance of non-double-spend can be achieved
  with minimum latency while maximizing throughput.

* Design the Gossip network so Consensus can be achieved as fast as possible.
  Understand the performance tradeoffs AND the good and bad incentives.

* Actually implement the algorithms.

#### Skills

* Can read whitepapers and protocol specifications.
* Can write protocol specifications.
* Can think about the performance of network protocols, bottlenecks, congestions, attacks, etc.
* Can actually write the code that implements the protocols, correctly and securely.
* Can think adversarially; understands LangSec, understands good/bad incentives, etc.
* Can work with abstract logicians, application programmers, concrete bitgangers, security guys, etc.
* Can use OCaml (assuming Tezos), or to learn it, fast.
* Can maintain high standards of code quality
  (from syntactic conventions to continuously running unit testing to writing correctness proofs)

#### Resources

* Full-time senior network expert.
* Full-time junior network expert.
* Part-time logic expert.
* Part-time compilation expert (little languages and their performance)
* Part-time application expert.
* Part-time network expert.

### Back End Development

#### Description

* Write daemons, their application logic, etc., in collaboration with
  logic expert (who extracts as much as possible),
  network expert (who provides communication primitives),
  front-end expert (who provides human interface),
  security expert (who prevents corners from being cut).
* Can orchestrate the many underlying components to implement the overarching protocol.

#### Skills

* Good aesthetics in application development to keep complexity in check.
* Discipline in writing all the tests.

#### Resources

* Full-time application back-end programmer

### Front-end Design

#### Description

* Client interface for casual users
* Management interface for the miners, payment processors, etc.

#### Skills

* Understand usability for end-users
* Can talk with back-end guys, logicians, security experts
* Can use OCaml (assuming Tezos), or learn fast.

#### Resources

* Full-time front-end expert

## All in all

* Full-time senior logic expert.
* Full-time junior logic expert.
* Full-time release engineer.
* Part-time OCaml user expert.
* Full-time application back-end expert.
* Part-time domain expert.
* Part-time compilation expert.
* Full-time interface front-end expert.
* Full-time network expert.
* Part-time security expert.
