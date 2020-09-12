# De Bruijn notation

Problem at hand - how to represent free qnd bound names in lambda calculus unambiguously?

Solution - don't use names, use natural numbers to refer to the lambda abstraction to which a variable is bounded to.

For example, `λx.x` as `λ.0`, `λx.λy.(x (y y))` as `λ.λ.(1 (0 0))` etc

However, there is a catch - we must take care that the numbers aren't messed up when we perform applications. The way this is done is keeping track of free variables in an "environment" - i.e. what we know so far about the lambda expression for sure. For example, if the current environment is `Γ = [x -> 4, y -> 3, z -> 2, a -> 1, b -> 0]` then `x (y z)` would be represented as `4 (3 2)`. One thing to look out for is that new bound variables can have same name as something from the environment - for instance `λw.λa.x` would be `λ.λ.6` and NOT `λ.λ.5`. The trick here is to increment indices - instead of `4` for `x`, we've used `6`. This is because we have introduced two new lambda abstractions \(`w` and a second `a`\) into the environment. In other words, we only increment the free \(unbound\) identifiers. This can be defined succinctly as follows

$$\begin{aligned} \uparrow^{d}_{c} k &= \begin{cases} k & k &lt; c\ k + d & k\ge c \end{cases}\ \uparrow^{d}_{c} \(\lambda .t_1\) &= \lambda . \uparrow^{d}_{c + 1}\(t\_1\)\

\uparrow^{d}_{c} \(t\_1 t\_2\) &= \uparrow^{d}_{c}\(t_1\) \uparrow^{d}_{c}\(t\_1\) \end{aligned}$$

We start with $\uparrow^{d}\_{0} t$, where $t$ is the outermost term.

Now this can be used to define substitution as follows

$\[j \rightarrow s\]k = s$, if $k = j$ and $k$ otherwise

$[j \rightarrow s](https://github.com/iambrj/blog/tree/61a1413c670482c081ce30d6ec550648c5523dc1/lambda%20.t_1) = \lambda .\[j+1 \rightarrow \uparrow^{1}\_{0} s\]t\_1$

$[j \rightarrow s](https://github.com/iambrj/blog/tree/61a1413c670482c081ce30d6ec550648c5523dc1/posts/t_1%20t_2/README.md) = \(\[j\rightarrow s\]t\_1 \[j\rightarrow s\]t\_2\)$

One line explanation: De Bruijn indices count the number of lambdas between the occurrence of a variable and its binding

