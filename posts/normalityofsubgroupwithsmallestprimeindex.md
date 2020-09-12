# Normality of subgroup with smallest prime index

Created: Jul 30, 2020 11:21 PM Tags: Algebra, Mathematics

I've been studying Dummit & Foote and the proof for this given there isn't quite to my taste. So here is my own version

1. Let $G$ be the group whose smallest prime divisor is $p$ and $H$ its subgroup with index $p$.
2. Let $\psi : G\times G/H\rightarrow G/H$ be the action on the left cosets of $G/H$
3. Let the corresponding regular representation be $\phi: G\rightarrow S\_{G/H}$ and its kernel $ker\(\phi\)$
4. Now, by the First Isomorphism theorem,

   $$\frac{|G|}{|ker(\phi)|} = |\phi(G)|\\ \iff |\phi(G)|\mid|G|\\$$

5. Furthermore, by Cauchy's theorem, $\phi\(G\)\leq S\_{G/H}$
6. Therefore, by Lagrange's theorem

   $$|\phi(G)|\mid|S_{G/H}|\\ \iff |\phi(G)|\mid |\;p!$$

7. By 4 and 6,

   $$|\phi(G)|\mid (|G|, p!)\\ \iff|\phi(G)| | p\\ \iff |\phi(G)| = 1\textrm{ or }p$$

8. In both cases, the subgroup is normal.

