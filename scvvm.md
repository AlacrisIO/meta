# scvvm: Legicash Smart Contract Verification Virtual Machine

## General Principles

The Legicash's Virtual Machine is designed for the *verification* of arbitrary contract clauses,
and not for the *evaluation* of arbitrary code.
It can be compiled to EVM and other targets.
It is hopefully an extension to the Bitcoin script language,
or will have a future variant that is.

If possible, we should extract the design of the verification VM from the design of the specification VM,
as its derivative or something similar: for every primitive in the specification VM,
come according primitives of the verification VM to check that a computation went according to spec.

## Evaluation

### Primitives

The SCVVM will sport all the required primitives to verify
equations involving cryptographic functions:
digests, signatures, merkle proofs, zk-SNARKs, encryption, etc.

It will also have primitives to verify the usual arithmetic operations,
either with bounds-checking and computation abortion,
or in modular arithmetic modulo some specified basis.

It will *not* feature functions that introduce objects "larger" than their arguments,
but *will* feature functions that introduce objects strictly smaller than their arguments.
For instance, it will not feature addition of integers,
but may feature subtraction of natural integers;
it will not feature creating new list objects,
but may feature taking sublists of an existing list object.


### Combinators

The SCVVM will have no unbounded recursion and no nested loops.
It will be able to deconstruct existing data structures;
but it will not be able to build new ones
(beyond initial constants, including toplevel invocation parameters).
It will have subtraction or division of natural numbers;
but it will not have addition or multiplication.
Evaluation is in $O(n)$ where $n$ is the size of the input.

TODO: We will try to identify a way to (semi-)automatically deduce
and/or otherwise co-specify the combinators for computation and verification.
Is there a generalization of the Curry-Howard isomorphism
that gives us verification as well as computation?

### BLOH


Ordre du Jour
* Qui fait quoi pour la TF: Fare fait un nouveau draft.
   Decouper en deux:
     * une demande industrielle court terme
     * un projet de recherche scientifique plus standard
* Discuter un plan pour la logique des contrats:
  * Logiquement non seulement décidable (quantification sur structures de données finies),
    mais avec preuves en temps borné
    * Nombre d'allers-retours sur le tribunal: nombre d'alternations de somme et produit (dépendants).
  * Déveloper en Coq une logique du premier ordre pour ecrire des contrats pour Tezos, avec
    * extraction vers Coq pour les preuves de correction (réflexion) pour les invariants des side-chains.
    * extraction vers ML pour de code client et serveur qui respecte les invariants de chaque joueur.
    * extraction vers arbitre et stratégie de preuve interactive (en sémantique des jeux).
    * extraction vers exemples de jeux à jouer pour assurer la couverture du code
      pour ML *et* les stratégies de preuve (tests).
  * Donner exemples de formules et de structures
    * exemple de formule:
       * partie classique
       * partie linéaire
       * partie épistémique
       * partie temporelle
    * exemple de structure de side-chain
       * définie inductivement
       * simple: chacun un compte (layer 2)
         invariant: conservation de l'argent (vis-à-vis des dépôts, retraits, transferts)
       * plus compliqué: avec un vérificateur de contrats dans la side-chain elle-même! (layer 3)
         [Pour autre demande de fonds]:

               manager: forall i . correct_transition(entry(i), entry(i+1))
               challenger: exist i . x=entry(i), y=entry(i+1), not correct_transition(x,y)

  * NB: Court Registry: promet que la structure est (1) bien formée, et (2) publique.
    * Attaque à 50%: http://www.crypto51.app/ (Quid avec la Proof-of-Stake de Tezos?)
    * Pour les travaux logiques, on suppose que le registre légal est honnête.



* f(x) = header_block_bitcoin(hauteur=x) interprete comme Merkle Patricia Tree.
etat_license(Trent, valide, bond)
etat_license(Trent, invalid, 0)



## BLAH

I am looking for a systematic way to have a pair of related calculi,
large and small, that can express arbitrary computations and their
arbitrary desired properties, wherein "players" use the "large"
calculus with unbounded recursion and growth, whereas the "judge" use
the "small" calculus with very limited recursion (logarithmic only?)
and no growth, and can *verify* the properties hold based on the
witnesses interactively provided by the players' "lawyers" as part of
verification games.

A friend told me about your work on self-justifying systems. I admit I
only took a superficial look at your work, and it goes deeper that
I've ever gone even when studying logic in college. Yet, its general
approach of building correspondences between a larger unbounded
axiomatic system such as traditionally used for logic and computation,
and a smaller axiomatic system that can verify both statements of the
previous logic and its own consistency, strikes me as relevant to my
endeavor.

Be a computer scientist and a functional programmer, I have worked
mainly in the domain of higher-order languages, with logic being
expressed through dependent types and the Curry-Howard isomorphism
between types and propositions (e.g. Coq). I'm wondering:

1- How do your first-order constructions apply in that setting?
2- Can I systematically deduce both "large" and "small" calculi from a
common logical description?
3- Can this logical description be embedded in Coq (using what Coq
calls "reflection"), such that propositions in the logic have a direct
and obvious meaning in Coq, and that provability in the logic implies
provability in Coq?
4- Given a single specification in this logical system, can I extract
programs and interactive verification engines, judges and lawyer
strategies, that fulfill the specified behavior?
5- Can I further prove that the extraction process is indeed
semantic-preserving, and that the logical properties proven in the
logic apply to the extracted entities?
6- What are the underlying "virtual machines" for the large and small calculi?
7- Is the correspondence between the two calculi as simple as "the
small calculus only allows growth using constants, not variables"?
8- What happens to recursion schemes? Under what systematic principle
may the judge verify a Merkle tree in O(log N) time but not otherwise
do unbounded recursion?
9- To virtualize computations and have a hierarchical court system of
judges, my verification calculus must be able to describe its own
verification algorithm such that a higher judge can verify that a
lower judge did its verifications correctly. How does this constraint
help or hinder the design of such systems?
10- Is there some generalization of the Curry-Howard isomorphism at
stake when extracting those two calculi? Can this generalization
reconcile the Curry-Howard point of view of propositions-as-types,
proofs-as-programs with the Russell-Whitehead point of view of
propositions-as-programs, proofs-as-traces? How does game semantics
fit in this picture?
