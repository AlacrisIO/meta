# Plan

Identify the Skills & Time required for each part of the project...
to reach technological demo

## To Reach Technological Demo

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
* Discipline in maintaining good code quality and writing all the tests.
* Can use lower-level abstractions in non-leaky ways
  to provide good abstractions to higher-level abstractions.
* Possesses or can quickly acquire domain knowledge about cryptocurrency payments.
* Can use OCaml (assuming Tezos), or to learn it, fast.

#### Resources

* Full-time application back-end programmer

### Front-end Design

#### Description

* Client interface for casual users
* Management interface for the miners, underwriters, etc.

#### Skills

* Understand usability for end-users.
* Understands web and/or mobile front-end technology (might require two people?)
* Can talk with back-end guys, logicians, security experts
* Can use OCaml (assuming Tezos), or learn fast. (Using Ocaml to Javascript?)

#### Resources

* Full-time front-end expert

### Release Engineering

#### Description

* Building and maintaining the software infrastructure.
* Continuously build, test, deploy software.
* Watch each step, detect failures, identify them, address them.
* Ensure developers get timely feedback on failures, bugs are filed.
* Use containers for deployment.
* Keep software dependencies up-to-date, particularly watch security updates.
* Work in interaction with all the rest of the team.

#### Skills Required

* Software plumbing: building great piping on good days, scrubbing them on bad days
* High quality standards, yet ability to deal with bad software (decisively if needed).

#### Resources

* Part-time in the beginning, full-time as the team grows, one release engineer

### Red Team

#### Description

* Break the system until it can't be broken.

* Penetration testing, fudge testing, trying known attack vectors, designing new attacks,
  reviewing code for errors, etc.

* Work with the developers so they fix the problem and with the release engineer
  so the problems remain fixed forever.

* Teach discipline to developers, constraints to architects.

#### Skills

* Probably best done by alternating security consultants each addressing a variety of aspects
  of security.

#### Resources

* Full-time senior network expert.
* Full-time junior network expert.
* Part-time logic expert.
* Part-time compilation expert (little languages and their performance)
* Part-time application expert.
* Part-time network expert.

## All in all

### To Reach Technological Demo

* Full-time senior logic expert.
* Full-time junior logic expert.
* Part-time release engineer.
* Part-time OCaml user expert.
* Full-time application back-end expert.
* Part-time domain expert.
* Part-time compilation expert.
* Full-time interface front-end expert.
* Full-time network expert.
* Part-time security expert.

### Beyond

* Full-time language design.
* Compilation expert full-time.
