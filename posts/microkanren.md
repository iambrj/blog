# microKanren

### Overview

_Goals_ are applied to _states._ Goals are analogous predicates and states to predicate domain values, a goal pursued in a state may either succeed and produce a stream or fail. The result of a $$\mu$$Kanren program is a stream of states satisfying the collection of goals.

### State

Represented as `(alist, fresh counter)` .

### Goal constructors

$$\mu$$Kanren has four goal constructors

1. `==` : this succeeds when both goals unify
2. `call/fresh` : creates fresh variable scoped over its body expression
3. `disj`: succeeds if either goal succeeds
4. `conj`: succeeds if second goal succeeds using first goal's stream



