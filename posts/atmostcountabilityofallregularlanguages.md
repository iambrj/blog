# At-most countability of all regular languages

## At-most countability of all regular languages

## Question

Given an at-most countable set of alphabet, how many regular languages can be made using these alphabet?

## Answer

At most countable.

## Proof

Consider the CFG

$$X\rightarrow X\cup X\mid X.X\mid X^*\mid \{a\}\mid \phi$$

where $$a\in\Sigma$$, the alphabet.

Since the CFG can only generate countably infinite strings and the union of countably infinite sets is countably infinite we are done.

