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

## Design

### Simplified Roles in the system

Therefore, we can distinguish three kinds of actors, who each play several roles:
* customer: viewer of many addresses, sender (going through facilitator), sometimes receiver (waiting for the consensus), lawyer (defending his interests).
* merchant: viewer of many addresses (accounting), receiver (going through facilitator), sometimes sender (disbursing the funds eventually), lawyer (defending his interests), and entry point (helping customers connect to the very same network rather than a fork).
* notary: facilitator (talking to both sender and receiver), gossiper (accepting data, pre-validating it, storing it, forwarding it), notary (partaking in the many phases of the consensus protocol), detective (watching side-chains for unreported violations, siccing the lawyer at offenders), lawyer (partaking in verification games), judge (maintaining accounts for everyone).

Moreover, all roles share some basic functionality:
connect to the network, validate and handle data, exchange messages, run the judge.


### Common Software

Resource estimates in (man)days for a first working version,
assuming we fork some base coin rather than implement one from scratch.
Properly debugged and documented is probably 3-10x more.


#### Connect to the Network

Short term:
* Inherit functionality from the basic network we fork (0 days).

Long term:
* Users must be able to easily bootstrap their connection to the network
  AND to make sure they use the same fork as the merchant or exchange,
  in case there may be multiple forks.
  We therefore want trusted clients that can connect based on
  dynamic information opportunistically provided by peers-to-be.
  (5 days to figure out how other peer-to-peer networks do it and reproduce whatever is best).
* Handle subscriptions
  (10 days to figure out the economics and implement the accounting).

#### Validate the data

Short term:
* Write a schema for our specific kind of side-chain, together with a validating reader and writer,
  and data accessors and generators
  (3 days).
* Minimally model some indexed "reference id" mechanism so lawsuits can find their data easily
  and are not duplicated.

Long term:
* Design and implement a DSL for describing blockchain formats that is a good sublanguage
  of our logic language for contracts, with which to describe our and other common blockchains
  (20 days).
* Extract `O(N ln N)` code for structural validation and indexing,
  to be run by shared knowledge database, plus access code to be run by the judge
  (10 days).
* Find how to model a representation of the logic in itself, so lawsuits can reflectively
  take into account previous lawsuits as affecting the state of the system
  (20 days).


#### Exchange Messages

Short term:
* Extend the base coin network protocol to exchange data for our side-chains
  (3 days)
* Implement some mechanism based on Lamport clocks (or hashgraph?)
  to manage the state of all the side-chains in the gossip network and/or the consensus
  (3 days)

Long term:
* Generalize the messaging protocol to recognize data describe by the DSL
  and track structural completeness of fragments with a given schema
  as prerequisite for publication as part of the consensus.
  (6 days)


#### Run The Judge

Short term:
* Put as much of the accounting logic directly for the our fast transaction "side-chains"
  directly in the judge for the main chain.
  (3 days).

Long term:
* Develop reconciliation mechanisms that minimize the latency yet preserve security through lawsuits
  (20 days).


### Customer Software (Backend)

#### Accounting

Short term:
* Manage keys to view many addresses
  (1 day).

Long term:
* Let users tag and otherwise categorize their addresses and their transactions, and
  group/coalesce them together according to some DSL for criteria.

#### Sending

Short term:
* Add support for going through facilitator
  (5 days).

#### Receiving

Short term:
* Just wait for Consensus
  (0 days).

#### Lawyer

Short term:
* Make sure a user has a can play his role in all lawsuits
  (3 days).


### Merchant

#### Accounting

Same as above.

#### Sending

Same as above.

#### Receiving

Short term:
* Add support for going through facilitator
  (5 days).

#### Lawyer

Same as above.


### Notary

Short term:
* Be a facilitator: talk to both sender, receiver, and local database
  (10 days).
* Be a gossiper: accept data, pre-validate it, store it, forward it
  (10 days).
* Be a notary: partake in the many phases of the consensus protocol
  (0 days if using Tezos or another Delegated Proof of Stake system,
  20 days if forking Bitcoin or Ethereum).
* Be a detective: watch side-chains for unreported violations, sic lawyer at offenders
  (10 days).
* Be a lawyer: partake in verification games
  (5 days).
* Be a judge: maintain accounts for everyone
  (1 day).
