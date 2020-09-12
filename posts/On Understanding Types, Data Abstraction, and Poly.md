# On Understanding Types, Data Abstraction, and Polymorphism

Created: Jul 13, 2020 2:05 AM
Tags: Type theory

```
e ::= x
e ::= fun(x) e
e ::= e(e)

```

## Limitations

- Using `value` to introduce a new name bound to a value or function,

    value id = fun(x) x
    value succ = fun(x) (x + 1)

- Correctness of addition requires no assumptions about what happens when the
$\lambda$-expression is applied to $\lambda$-expressions that do not
represent integers; but it is desirable to define such applications as
errors
- Type checking at compile time eliminates the possibility of operations on
objects of an incorrect type - large classes of $\lambda$-expressions legal
in untyped $\lambda$-calculus become illegal (which may depend on a
particular type-checking algorithm, which is undesirable)

## Typed

- Extra restriction - every variable must be explicitly typed when introduced as
a bound variable

    value succ = fun(x:Int) (x + 1)

- Type declarations are introduced by the `type` keyword

    type IntPair = Int X Int
    type IntFun = Int $\rightarrow$ Int

- Type declarations introduce names (abbreviations) for type expressions; they
do not *create* new types in any sense - this is expressed by saying that we
used *structural equivalence*(as opposed to *name equivalence*): two types
are structurally equivalent when they have the same structure, regardless of
the names we use as abbreviations
- Type of a variable can be introduced as part of its initialization using
following notation

    value intPair: IntPair = (3, 4)
    value succ: Int$\rightarrow$Int = fun(x:Int) (x + 1)

- Local variables can be declared using `let ... in ...`

    let (a = 3) in (a + 1)

## Basic Types and Constructors

### Basic Types

### Constructors

## Types as Sets of Values

- There is a universe `V` of all values (a complete partial order) - a large set
of all possible computable values
- A type is a set of values of `V`, but not all subsets of `V` are legal types:
they must obey some technical properties. Subsets of `V` obeying such
properties are called *ideals*
- The set of all types (ideals) over `V`, when ordered by inclusion form a
lattice - the top being `Top` and bottom being the empty set (singleton set
containing the least element of `V`)
- Now *having a type* is same as *membership* in the appropriate set - as ideals
over `V` may overlap, a value can have many types. A particular types system
is then a collection of ideals of `V`, which is usually identified by giving
a language of type expressions and a mapping from type expressions to ideals
- A monomorphic type system is one in which each value belongs to at most one
type

## Universal Quantification

- The typed $\lambda$-calculus can express monomorphic functions, but not
polymorphic functions
- The fact that a given functional form is the same for all types may be
expressed by *Universal Quantification*, for instance

    value id = all[a] fun(x:a) x

- Function parameters of universally quantified types are most useful when they
have to be used on different types in the body of a single function (e.g.
function to find length of a list of any type of element)

## Parametric Types

- Common structure can be factored out in a single *parametric* definition and
that can be used in defining other types

    type Pair[T] = T X T
    type PairOfBool = Pair[Bool]
    type PairOfInt = Pair[Int]

- A type definition simply introduces a new name for a type expression and it is
equivalent to that type expression in any context - it does not introduce a
new type
- A parametric type definition introduces a new *type operator* - `Pair` above
maps any type `T` to a type `T X T`. The following represent two different
things

    type A[T] = T$\rightarrow$T
    type B = $\forall$ T. T$\rightarrow$T

## Existential Quantification

Type specifications for variables of a universally quantified type have the
following from, for any type expression `t(a)`

\begin{align*}
p:\forall a.t(a) (e.g. id:\forall a.a\rightarrow a)
\end{align*}

By analogy with universal quantification, we can try to give meaning to
existentially quantified types

In general, for any type expression t(a), p:$\exists$a.t(a) has the property
"For some type `a`, `p` has the type `t(a)`"

- Existential types are useful only when they are sufficiently structured - they
hide some of the structure of the objects they represent but show enough
structure to allow manipulations of the objects through operations the
objects themselves provide
- For instance, existential types can be used to form heterogeneous lists

    [(3, succ);([1;2;3], length)] : List[$\exists$a.a X (a -> Int)]

## Formalism

- An ordinary object, such as `(3, succ)` may be converted to an abstract object
having type $\exists$`a.a X (a -> Int)` by *packaging* it so that some of
its structure is hidden

    value p = pack[a = Int in a X (a -> Int)] (3, succ) : \exists a . a X (a -> Int)

In general,

```
pack[a = typerep in interface] (contents)
```

- A package must be opened before it can be used

    open p as x in (snd(x))(fst(x))