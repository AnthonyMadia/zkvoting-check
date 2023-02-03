# Voting Check

[From](https://www.youtube.com/watch?v=6XxVeBFmIFs&t=844s&ab_channel=ZeroKnowledge) zk hack - introduction to circom 2.0 - iden3

Idenity of someone is a public key (pk). We want to check that the pk in the consensus is yours (check you have voted) so we need secret key (sk) to prove that I know a secret key from one pk of the list.

Note that there are several pk schemes (ECurves, etc.). With zk, we could use a hash function to build a pk pair. We could use a circuit to implement the hash function (sha256, Posedion, etc.) given in `circomlib`.

`sk` is private input that will get hashed to produce `pk`. Check that `pk` is within the set of `pks` in merkle tree.

A merkle tree is necessary for this proof because if a country votes, there will be millions of public keys. Each of the leaves of the tree are hashes of secret keys.

This circuit proves that a secret key (private input) is in one of the leaves of the Merkle Tree.

Example output of `mkt2cir.js` test using `circom_tester`:

```
 Check Merkle tree Circuit
44444444444
6089164006278979997064988404053639565226149319626268946296635412467235768175
944210591924524960699367252385025357816569597760145946972314960597502103370
44444444444
506952089557660611143169613371890445783724292566211651668393617728459486427
5903205309316973943535550042150768263809469060693271622770717961452492910896
44444444444
9631428795162404395753140309810294961871348072720705774743129922969822967654
8240055649093052352355674146556731727465324548585998462438953390848389993925
    ✔ Should check inclussion in MT
```
