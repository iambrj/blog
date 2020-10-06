# Normality of subgroup with smallest prime index

Created: Jul 30, 2020 11:21 PM Tags: Algebra, Mathematics

I've been studying Dummit & Foote and the proof for this given there isn't quite to my taste. So here is my own version

1. Let $$G$$ be the group whose smallest prime divisor is $$p$$ and $$H$$ its subgroup with index $$p$$.
2. Let $$\psi : G\times G/H\rightarrow G/H$$ be the action on the left cosets of $$G/H$$
3. Let the corresponding regular representation be $$\phi: G\rightarrow S_{G/H}$$ and its kernel $$ker(\phi)$$
4. Now, 

   $$|G/ker(\phi)| \mid |G|$$

5. Furthermore, by Lagrange's theorem

   $$|G/\ker(\phi)| \mid |S_{G/H}| = |S_{p}|$$

6. By 4 and 6,

   $$|\phi(G)|\mid (|G|, p!)\\ \iff|\phi(G)| | p\\ \iff |\phi(G)| = 1\textrm{ or }p$$

7. In both cases, the subgroup is normal.

