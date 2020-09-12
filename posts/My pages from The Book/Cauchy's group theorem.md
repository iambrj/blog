# Cauchy's group theorem

# Theorem

If a prime $p$ divides $|G|$ for some group $G$, then $G$ has an element of order $p$.

# Proof

Consider the set

$$S = \{(g_1,\dots, g_p) | g_1\dots g_p = e\}$$

Then

1. $|S| = |G|^{p-1}$, since the last element is determined by first $p-1$ elements
2. $|S|$ can be partitioned into equivalence classes based on cyclic permutations
3. Each equivalence class has either $1$ or $p$ elements, since otherwise

$$(g_1,\dots,g_p)>>k = (g_1,\dots,g_p)\\(g_1,\dots,g_p)>>p = (g_1,\dots,g_p)$$

which would together imply $k|p$ which is impossible since $p$ is a prime

4. $|G|^{p-1} = s+kp$ where 

1. $s$ = number of single element classes
2. $k$ = number of $p$ element classes

since $p$ divides both $|G|^{p-1}$ and $kp$, it must also divide $s$ meaning there is a non identity $x\in G, x^p = e$