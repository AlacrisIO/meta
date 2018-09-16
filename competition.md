The Competitive Landscape
=========================


Algorand
--------


Augur
-----

[Augur](https://www.augur.net/) XXX


Blockstream's Liquid
--------------------

[Liquid](https://blockstream.com/liquid/) is an early side-chain project,
with a two-way peg to Bitcoin, with a fixed set of notaries who handle all the logic.



ChainLink
---------

[ChainLink](https://www.smartcontract.com/) provides a great approach for smart contracts on a blockchain (currently, Ethereum) to refer to data from the outside world. For instance, simple crop insurance contracts might refer to weather reports. Key entities, or oracles, sign and publish data anchored in the outside world. The challenge is to build oracles that can be reasonably trusted by participants in a contract. ChainLink offers many mitigation strategies and services to build more trustworthy oracles out of a collection of existing oracles. In the end, this kind of technology allows smart contracts in a decentralized consensus to query data from centralized information sources.

ChainLink, or a clone thereof, would work well as a complement to our proposal Legicash. Our Legicash protocol can help enforce internal and mutual structural properties of blockchains, but cannot make up the data values for external events; ChainLink or similar technologies provide usef


Dragonchain
-----------

[Dragonchain](https://dragonchain.com/) has the notion of using side-chains for scaling
and notaries for synchronizing with the main chain, but its whitepaper looks like it is
yet another in the category of "business idea without technical backing".


Ethereum
--------

[Ethereum](https://www.ethereum.org/) is an established cryptocurrency that pioneered the use of smart contracts. There is now a formal model of its blockchain and contract virtual machine. Although Ethereum currently does not have anything that overlaps with Legicash FaCTS, their upcoming development, Plasma, will be very similar (see more on Plasma below). Ethereum is a potential platform on which to eventually deploy our smart contract technology once it’s mature (see our second proposal Legicash), given that we have a good relationship with members of the core Ethereum team. However, Ethereum is not the best option for our initial deployment of Legicash FaCTS since Legicash FaCTS would require too many backward-incompatible changes to their very large existing network.


Factom
------

[Factom](https://www.factom.com/) is a blockchain
with its own consensus (non-transferable PoS) and token ("Factoid").
It requires the current leader of every tenth one-minute consensus round
to publish the summary of an update to Bitcoin.
It is thus a Bitcoin side-chain, but with no pegging between BTC and Factoids.
The value of it being a side-chain at all is only to ride on Bitcoin's POW
to prevent false histories.

Otherwise, it purports to store data ("facts") in a DHT,
though it is unclear what are the incentives for publication and against non-publication -
which makes it worse than SIA or FileCoin.
On the other hand, it has this interesting idea of cleanly separating
the collation of transactions which happens in the consensus servers,
from the interpretation of the transactions as having a meaning in terms of tokens,
which can happen in any full client.
Clean from a design point of view, but the overall economic benefits and costs are not clear.

There are no obviously published data on how well it scales.
They advertise recursive side-chains, but if it's also without pegging,
the economic value is recursively dubious.


FileCoin
--------

[FileCoin](https://filecoin.io/) offers an innovative way of paying people to verifiably store data online. Payment is accomplished through a bitcoin-style ledger where the classic Proof-of-Work is replaced by Proof-of-Replication of data and Proof-of-Space-time availability of data. FileCoin otherwise has a contract system similar to Ethereum, and will probably be built as an extension to Ethereum.

While Filecoin is only distantly relevant to Legicash FaCTS, it is a very interesting potential partner for our more general proposal, Legicash. Legicash crucially depends on users being able to post the state of their arbitrary side-chains as shared knowledge and FileCoin offers a substrate to post large amounts of data as part of their protocol. This would be another reason to potentially build Legicash on top of Ethereum.


Hedera Hashgraph
----------------

[Hashgraph](https://hashgraph.com/) is a remarkable new consensus algorithm based on gossip-about-gossip. Unlike other protocols that relegate gossip to lower layers of the protocol, hashgraph makes gossip an essential part of its protocol, and very elegantly builds the consensus as a property that emerges from gossip about gossip: the directed acyclic graph (DAG) of gossip contains a trace of all relevant communications; making this DAG explicit allows for optimal use of the information therein, making hashgraph as fast as any consensus algorithm can be; on top of the gossip graph, arbitrary old school byzantine voting algorithms can be run “virtually”, which works very well in a Proof-of-Stake setting. A cryptocurrency, Hedera, is being launched on top of Hashgraph. Design details are not available yet. On the other hand, announced performance from simulations is impressive: the platform will scale to over 100,000 transaction per seconds with a consensus latency of about 3 seconds. Even if the latency were twice as high, that would still be a notable improvement over debit card systems as well as a dramatic improvement over existing cryptocurrencies.

In the context of Legicash FaCTS, gossip-about-gossip provides a way to measure progress from local knowledge to shared knowledge to common knowledge. It is a great tool to detect double spending attempts early, and to identify malicious miners who would partake in block withholding attacks and eventually punish them by forking. If Legicash FaCTS has to build its own blockchain from scratch, hashgraph is a great inspiration (though hashgraph itself is patented).

If the performance projections for Hedera are correct, achieving consensus in a few seconds is so fast that Legicash FaCTS’s sub-second confirmation isn’t a huge improvement anymore. Legicash FaCTS could still accelerate transactions on networks that use older consensus algorithms, but these networks would soon be displaced by newer networks based on Hedera or other post-hashgraph technologies. If and when these new networks replace the old ones, the market for Legicash FaCTS would be restricted to secure facilitation services to non-technical people, people who live in places where internet bandwidth is at a premium, people using embedded devices, etc.

On the other hand, our more general Legicash system proposal is positively, not negatively, affected by any performance improvement of the consensus, and will welcome any speedup from using hashgraph.
Hashgraph seems to be the most “one to watch” technology at the moment. We believe it is more promising than all the other projects cited in this appendix.

IOHK
----

[IOHK](https://iohk.io/research/library/#tag-smartcontract).
[IOHK research library on smart contracts](https://iohk.io/research/library/#tag-smartcontract).


IOTA
----

[IOTA](https://iota.org/) (originally DagCoin) is another ledger based on DAGs with a novel statistical approach that works well with Proof-of-Work. While the basic approach is quite interesting, the IOTA team seemingly tends to vastly oversell what IOTA is capable of: it is not at all suitable for use in the “Internet of Things”; its transactions are not anymore “instantaneous” than in any other system and they may take hours to confirm; the current implementation isn’t decentralized and depends on a closed source snapshot server controlled by the authors. What more, the authors do not look like they are interested either in taking criticism constructively and addressing the many issues with their platform nor in making significant improvements to it.
In the context of Legicash FaCTS, IOTA is neither a strong rival nor a strong potential partner.


Kava
----

[Kava](http://kava.io/wp-content/uploads/2018/04/Kava_Blockchain_Overview-White-Paper.pdf)
correctly separates clearance from settlement.
However, Kava also assumes it can build a consensus that provides simultaneously
"fast, low-cost finality; strong decentralization; and
payment channels with fast settlement in the case of non-cooperative closure".
It's dubious that they can actually do that without sacrificing security.
And if they could, that blockchain would win easily over existing ones,
removing the need for interoperability with them.


Lightning Network
-----------------

Bitcoin Core’s [Lightning Network](https://lightning.network/) is the most significant competitor on the market for both fast and secure cryptocurrency transactions. However, the basic construct, channels, is a specialized peer-to-peer connection with limited direct utility. Lightning Network proponents claim that networks of such channels allow for paths of transactions, in the style of Ripple. They might also be inspired by Nick Szabo’s writings about how such medieval bills of exchange or the Islamic hawala networks successfully allowed for continental and intercontinental commerce over many centuries.

However, there are many seemingly unresolved challenges in offloading transactions from the consensus to peer channels and networks of peer channels. First, the Lightning Network requires transactions on the consensus to setup and close channels, but also to rebalance accounts between multiple channels when the liquidity is missing in a particular channel. This is much more onerous than the working models that the Lightning Network purports to emulate, and one extra such transaction defeats the entire purpose of the construction as far as making the network scale (which is admittedly not the only potential purpose of payment channels).

The Lightning Network also requires all channel participants to remain online at all times, unless all they ever do with their channels is pay (which can only apply to half the participant accounts at most). Participants who receive funds are also particularly vulnerable to denial-of-service attacks that would prevent them from defending against dishonest channel peers. Those who partake in onion transactions may be victims of incomplete-transaction attacks that freeze their liquidities unless they pay the consensus for transactions that close their channels. Even with these challenges addressed, it looks like the implicit network topology that would make this network work is to have centralized “hubs” that act like facilitators or banks, despite the marketing about decentralization. This is the same centralized but repudiable model we are proposing, just achieved in a backhanded way. Even then, it is unclear how much floating liquidity a facilitator would want to leave in each channel before it has to claim it at the cost of an expensive main chain transaction.

Last but not least, the Lightning Network brings a great deal complexity for all participants to master, and it may take months or years to suitably remove the kinks to the point that the public-at-large may safely use it. All in all, for all the excitement surrounding it, the Lightning Network is more a technological feat looking for an economic problem to solve, than a design that actually solves the problem of fast and secure payments.

It is unclear at this point if and when the Lightning Network will be fully functional and ready for public consumption.


Liquidity Network
-----------------

The Liquidity Network, from reading its [whitepaper](https://liquidity.network/whitepaper_Liquidity_Network.pdf),
looks very much like Legicash FaCTS.
However, it is not very clear from the how they defend against bad transitions or block withholding.


Loom
----

[Loom](https://loomx.io/) is a platform to write dApps, with the broken paradigm of dApps as computing on the blockchain. Now, they do use side-chains; but their side-chains have their own consensus and only partially linked to the main-chain via contracts. Better as a platform to learn and play than one to actually develop with.


Nano
----

[Nano](https://www.nano.org/) originally known as [RaiBlocks](https://raiblocks.net/) is a project whose authors understood the right way to distribute payment processing from a computational point of view. Nano gets a lot of details right in this respect, and from the point of view of computing architecture, Legicash FaCTS is very similar to Nano.

Where Nano and Legicash FaCTS diverge is that the Nano authors did not emphasize security or incentive structures to keep users honest over time. Whether or not Nano addresses these issues may decide whether it will be widely successful or not.

If our plans to build on Tezos change for political reasons, Nano may or may not be a good alternative for Legicash to start with, depending on whether we Legicash teams and the Nano team can get our complementary approaches to work together.


Nebulas
-------


Neon Exchange (NEX)
-------------------

[White paper](https://neonexchange.org/pdfs/whitepaper_v2.pdf)


Nervos
------

[Nervos](nervos.org)
They might actually provide data ingestion, *validation* and republication at scale,
making them a viable court registry.

[Review](https://cryptobriefing.com/nervos-ico-review-token-analysis/)

Code: since 2012, now 10 Rust developers.


OmniLedger
----------

Reacting to their whitepaper started me (Faré) on the journey to Legicash.
Technically interesting (though falling far behind e.g. Algorand),
it completely misses the point with respect to how the economics of proof of work
(that it only mentions in passing) affect what it means for there being a "thousand computers"
involved in each shard, when e.g. for Bitcoin their would be 95% the same 3 to 10 computers.


Ontology
--------

Currently a token ONT on top of NEO, defined NEP-5, using VRF + BFT (à la Algorand?),
Ontology claims to solve plenty of issues.
https://medium.com/@LindaCrypto/ontology-announces-the-triones-membership-system-a-high-performance-governance-model-with-3a009cfe68a4


Plasma
------

[Plasma](https://plasma.io/) is a proposal for using contracts to build fast payment side-chains on top of Ethereum and more. The proposal is explicitly based on the principle of recognizing the consensus as a court system — the same principle that underlies Legicash. Plasma even features lower courts, i.e. nested side-chains, beyond what Legicash proposes. In many ways, the Legicash FaCTS proposal is a special application of the main ideas in Plasma, and our second proposal, Legicash, is an extension of these ideas. We recommend reading the Plasma whitepaper, even cursorily, to those who want to more deeply understand Legicash FaCTS.

Despite the parallels between Legicash FaCTS and Plasma, a notable difference is Plasma’s defense against block withholding attack — the case where a side-chain manager fraudulently refrains from publishing the details of data they register. Plasma requires users to withdraw en masse from the side-chain because the manager may use a fraudulent block to withdraw their money. But this approach cannot work as is, because:
An exit by millions of individual account holders will swamp the court system.

Since the court system alone cannot distinguish between honest and dishonest claims, malicious actors have the advantage in the race (the current “earliest transaction wins” heuristic of Plasma can be gamed).

If the smart legal procedure is too short, if the victims are too slow, or can be further slowed down by a denial-of-service attack, etc., the attacker can get away with robbing those UTXOs because the consensus cannot distinguish between bogus claims based on withheld blocks vs. verifiable claims based on published blocks.
Last but not least, a mass exit supposes a reliable way to honestly coordinate mass withdrawals, which may be a bigger coordination problem than the one solved through said mass withdrawal.

More generally, interactive proofs are not possible, much less in predictably finite time, when lawyers cannot see the evidence. For instance, a facilitator that manages more funds than their posted bond could become dishonest (e.g. being hacked) and create a bad block with lots of tiny valid transactions from sybil accounts and one huge invalid transaction from vulnerable UTXOs they don’t own to multiple puppet accounts. Because the data is withheld, lawyers for the victims cannot directly go to the bad transaction, and they will lose the argument if there is a time limit on legal procedures. If there is no time limit and the court allows interactive discovery through a long series of expensive challenges, the discovery may take an arbitrarily long time during which the victims’ assets are held hostage and the victims bleed legal fees. Ultimately, the problem is that Plasma attempts to solve this issue in the context of the unmodified Ethereum network. But the exercise is inevitably futile; any working solution necessarily involves a capability that Ethereum does not currently possess, which is that the main chain's gossip network must maintain shared knowledge of the direct side-chains' data. This shared knowledge is a prerequisite to preventing fraud via verification games.

A second issue with Plasma is that it dedicates a large section to verifiable computations on a blockchain, seemingly with the implicit assumption that this can be a substitute for cloud computing in a trusted data center (e.g. Amazon EC2, Google Cloud, Microsoft Azure, etc.). While such computations can conceivably be useful as part of financial products and other smart contracts, they are not conceivable substitutes to cloud computing because the deterministic verifiability adds significant complexity, runtime overhead, development costs, etc. All these costs are necessarily in excess to directly renting the same machines and electricity directly from the very same provider, just without the expensive middleware, etc. Computing on the chain inherently sacrifices both trust and privacy, and they can only be regained at very large expenses. All in all, it is inadvisable to compute in the Consensus unless you need the results to be publicly visible and used as part of ledger operations — e.g. as part of financial products expressed as smart contracts. A few narrow applications may therefore exist, but this is not at all a substitute to Cloud Computing.

A third issue with Plasma is that they seem to neglect formal methods in their approach. To develop complex contracts that can securely manage billions of dollars-worth of tokens without making the same catastrophic mistakes witnessed in the past with the DAO, Parity Wallet and others, we assert that formal methods cannot be an afterthought. Having a good understanding of the problem at the level of formal logic must come first.

Plasma is a great predecessor to Legicash FaCTS, but Legicash includes many key advances without which Plasma will probably fail.


PolkaDot
--------

[Polka Dot](https://polkadot.network/) provides a vision for binding multiple chains together using accountability through bonds, and has many worthwhile economic ideas, such as trying to identify the many roles of participants in the network.

However, Polka Dot does not address attacks on the all-important interchain transactions. How can a chain trust availability of data on another one, and thus host verification contracts? The whitepaper leaves too many technical questions open.


Pumapay
-------

[Pumapay](https://pumapay.io/docs/pumapay_whitepaper.pdf) has a lot of hype around one idea:
making "pull" contracts where suppliers can automatically charge the customer's account.
Beside the dubious security model, the idea is of no help with scaling or simplification.
As described it actually makes for double the number of transactions:
one where the customer creates or authorizes the contract,
then one where the merchant invokes the contract to get money.
The job is much better done on the wallet side, without doing anything special on-chain.
Technically, it seems to be yet another useless shitcoin.
Marketing-wise, they look like they got their shit together.


Raiden Network
--------------

[Raiden](https://raiden.network/) is an Ethereum adaptation of the Bitcoin Lightning Network,
with the same advantages and the same limitations,
though it doesn't interoperate directly with the LN.


Ripple
------

[Ripple](https://ripple.com/) is a blockchain that openly embraces centralized responsibilities to achieve great performance. Because it doesn’t even claim or try to achieve trustless security, it is radically simpler and vastly superior to the many blockchain projects that try it and fail at it. For the same reason, though, Ripple is not a direct competitor of Bitcoin in terms of  trustless network security. Some might even argue that it is not a “cryptocurrency” sensu stricto, though it is based on blockchain technology.

Legicash FaCTS aims at being as fast as Ripple while providing the same trustless security as Bitcoin.


RSK
---

[RSK](https://www.rsk.co/) is doing two-way pegs between a main chain and a side-chain,
where all the logic and security is moved to the notaries who handle the side-chain
and/or miners for the main chain who do merged mining.

Similar to Liquid, but also adds contracts on the side-chain, and combines notaries and miners.


Skale
-----

[Skale](https://www.skalelabs.com/) no whitepaper yet, but it looks like
they will be offering a Plasma solution.
[https://medium.com/@megadeth20/skale-labs-overview-115e75ba48d6](Medium) introduction.
TODO: see the CTO's posts on Ethresear.ch.


Stellar
-------

Michael Horowitz says they have a great scripting language...


Tezos
-----

[Tezos](http://www.tezos.ch/), the self-amending cryptographic ledger, might be an ideal partner to implement Legicash FaCTS. Tezos is pre-launch and therefore does not pose backward compatibility challenges, yet is very advanced and almost ready to launch. Furthermore, the structure of its “delegates” that post bonds to mine (or “bake”) blocks using Proof-of-Stake can be easily leveraged into our repudiable facilitators. Finally, the codebase was written in OCaml with the explicit notion that it would integrate well with verified code extracted from proofs using formal methods — which is exactly what we need.

Tezos has experienced turmoil due to disputes regarding control of the money raised in 2017 to fund its development. In light of these disputes, several class-action lawsuits were initiated. These disputes seem to be resolved as of February 22nd, 2018, and it appears that they will not impact the release of Tezos. Even the worst scenario would not be a showstopper for building Legicash FaCTS on top of the Tezos codebase since Legicash FaCTS has the option of forking the Tezos code base without associating with its brand or community. However, we see value in sticking with the brand and community, and are looking forward to working with them. Tezos users could see Legicash FaCTS as a way to revive a community currently in disarray.


TrueBit
-------

[TrueBit](https://truebit.io/) uses Ethereum smart contracts to implement a Verification Game. It can thus verify logical invariants of structures published on the blockchain with a variety of applications.

However, TrueBit fails to draw a link to Computability Logic, which would offer a formal framework to systematize the design of those games. Furthermore, it is written, like its successor Plasma, with the assumption that “smart contracts” are about computations that are supposed to happen in a decentralized trustless way. By contrast, Legicash is based on the understanding that “smart contracts” are about computations that are not supposed to happen; Court should always be a last resort, never a default option.


Truthcoin
---------

[Truthcoin](http://truthcoin.info/) (2014-2018) by Paul Sztorc,
once renamed [Hivemind](http://bitcoinhivemind.com/) (2015-2016).
It has ideas both weird and great about smart contracts, oracles, etc.
Warning: Sztorc seems to have the "takes pro-IP arguments seriously problem",
as in "if anyone can copy the data, no useful data will be published",
which is obviously false.
