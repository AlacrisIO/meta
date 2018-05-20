# Task file

## TODO
* [fare] Types for all flow
* [fare] Deepen Types
* [paul] Run local Tezos testnet
* [paul] Write scripts to auto setup development/test environment for gitlab CI
* [paul] Automate test infrastructure
* [paul] Run integration tests in gitlab CI
* [fare] Write stubs
* [?] Write trivial network code
* [?] Write trivial flow for payment
* [fare] Learn the structure of the main chain
* [fare] Keep reading whitepapers and literature -- focus more on (1) contracts and (2) sharding


## DONE
* [fare] document flows (level 0)
* [fare+paul] document best practices
* [paul] Compile Tezos
* [paul] minimal tests
* [paul] link with Tezos



Current contract languages follow a logic that is alien to the logic of the blockchains themselves.
What is a "natural" programming model to write "contracts" on blockchains?

Let's try to describe a logic that is natural to distributed consensus: it's a logic based on a monotonic (append-only) data graph, where immutable information is added, never removed (though it can sometimes be forgotten if it can somehow be proven to be irrelevant forever afterwards). Not just that, but the validity of the data (whether the chain so far is valid, and whether the addition is valid) is supposed to be straightforward to check, wherein mutually exclusive data points ("facts") can easily be detected via suitable indexes, and the later facts rejected. Facts include verifiable information and ownership based on signatures, digests and SNARKs. These are the concepts involved in the consensus, and they should also be those involved in the logic of "smart contracts", at least at its most basic levels of abstractions.

Now, how is non-monotonicity expressed, when it's involved at all? Well, there's already a mechanism for that: a monotonic set for negative information that shouldn't be used twice. That's how systems with UTXO ensure that there is no double-spending. This set can be implicit as in Bitcoin, or explicit (yet obfuscated), as in the Zcash UTXO spending witnesses. That probably should be the model here, too: handling data, but some data can be handled only once, and there's a witness for that. In some easy cases where the correspondence between the capability and the spending witness isn't obfuscated (as in Zcash), I suppose you could optimize the notion of "data that is present once then removed" with the notion of "resource", and keep only the list of active resources or a summary thereof (thus, accounts as in Tezos). The underlying data model thus remains one of classical and linear "facts" — you can check whether a "fact" is or isn't part of the blockchain. The "fact" presumably has a "key" such that it is exclusive of other facts with the same key. Some keys include an expiration policy so the miners know when to forget about it (but former presence can still be checked using merkle proofs).

So much for the data model. What of the execution model? You need to be able to verify any claim. But you don't need to do the hard part of the computations. Actually, doing any hard computation on the blockchain is a huge cost on everyone. So, no Turing-equivalence, just interactive and non-interactive proofs. No need for loops, beside following merkle trees. So, reducing sequences of verifiable accessors, but no building new sequences; duplication, while possible, is costly, though not quite as much as explicit duplication. All the computation happens off-chain: non-trivial recursion, side-effects, non-termination, communication, etc. The contract just verifies them.

Combining the two: an interaction with a contract consists of
1- a set of new facts to be added to the chain
2- evidence, that may notably include signatures, and old facts found in the chain, together with verifiable access paths from the chain state at a given height.
The verifiers validates that
A- the old facts are indeed present in the chain
B- no old fact contradicts the new facts, assigning a different value to the same key.
C- the new facts are indeed explicitly allowed to be added based on the evidence of the old facts, based on the rules of the contract, which is a logical formula that matches the old facts and new facts as parameters.

As special optimizations, it is recognized that
d- some facts are "spending witnesses" (or "antifacts") saying that a fact has been spent
e- implicitly, every fact is implicitly mapped to the path by which its presence can be verified in a transaction.
f- a full node needs to maintain a mapping of the active facts
g- some facts may expire from the active set after a while — but their presence can still be verified with merkle paths.
h- some facts represent messages, activities, actor states, resources, and are systematically spent after first use; verifiers can recognize those facts and just remove them from the active list rather than keep both them and their spending witness (they cancel each other).



More flows: settlement, state update, mass voluntary exit...
Simple Settlement: atomic cross-chain settlement; Lightning Network.
ACIDity: some database with remove replicates.
Pipelining: parallelizing signatures, etc., minimizing contention, types for provably-correct way (ScalaZ?)
Court Registry: types, basic service, pricing, elastic resourcing, gossip
Better Testing: QuickCheck, Integration Tests
Mass Transfers: Mass Force Close, Mass Withdraw
Ethereum support: Talking to full node and/or light client
EVM contract: Bamboo, etc.
Fraud: specification, types, contract, court pricing, argument strategy, claims, resolution, etc.
