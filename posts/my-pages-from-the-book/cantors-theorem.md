# Cantor's theorem



I like to break down the proof into two parts

1. $$P(A)$$does not have the same cardinality as $$A$$
2. Not only is its cardinality different from $A$ but, in fact, it is greater than $$A$$'s cardinality

For 1. we go by _reductio ad absurdum_ - proof by contradiction.

* Assume on the contrary that they indeed have the same cardinality.
* This means that it should be possible to define a bijection, a one-to-one correspondence, from $$A$$ to $$\mathcal{P}(A)$$, call this $$f:A\rightarrow\mathcal{P}(A)$$.
* Now consider the set $$X = {a\in A | a\not\in f(a)}$$.
* Since $$X$$ is a subset, it must be in $$\mathcal{P}(A)$$, and have a preimage under $$f$$. Call this preimage $$\alpha$$.
* Now arguing whether or not $$\alpha$$ is in $$X$$ leads to a contradiction. Thus they cannot have the same cardinality by modus tollens.

To see 2 observe that there are only two possibilities since 1 is already proved

1. $$\mathcal{P}(A)$$ has the larger cardinality
2. $$A$$ has the larger cardinality

Observe that the latter is impossible since every element of$$A$$ is contained in $$\mathcal{P}(A)$$ as $${x}, \forall x\in A$$

### Edit : 23-08-2020

* [A formalization of the above in Coq](https://cstheory.stackexchange.com/a/40146/54872)

