# Schröder–Bernstein theorem

# Theorem

If the sets $A$ and $B$ are such that there exist injections $f:A\rightarrow B$ and $g:B\rightarrow A$, then $|A| = |B|$

# Proof

Consider the following series

$$\dots,f^{-1}(g^{-1}(x)),g^{-1}(x),x,f(x),g(f(x)),\dots$$

1. If two series have at least one equal element, all elements are equal
2. The set of all possible series partitions $A\cup B$, thus it is enough to show that for disjoint $A$ and $B$ there is a bijection between elements of $A$ and $B$ in every series
3. Since $f$ and $g$ are functions, the series never terminates on the right, but may terminate on the left due to non existence of inverses

    3.1 If it never terminates, both $f$ and $g$ are bijections

    3.2 If it terminates due to non existence of $f^{-1}$, then $g$ is a bijection

    3.3 If it terminates due to non existence of $g^{-1}$, then $f$ is a bijection