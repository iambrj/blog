---
description: >-
  Given any two arbitrary expressions in relational algebra, is it possible to
  write a program to check if they are semantically the same without running
  them?
---

# Designing raex

## Syntax

Things between backticks are terminals

```text
identifier ::= [a-z][a-zA-Z0-9]*
type ::= `real` | `string`
predicate ::= predicate `\/` predicate ; disjunction
          ::= predicate `/\` predicate ; conjunction
          ::= `not` predicate
          ::= identifier [`<`|`>`|`=`] [identifier | [0-9]*`.`[0-9]* | `"`[a-zA-Z0-9]*`"`]
expr ::= `select` `[`predicate`]` expr
     ::= `project` `[`(identifier)+`]` expr
     ::= `join` `[`(identifier)*`]` expr1 expr2
     ::= expr `unin` expr
     ::= expr `intr` expr
     ::= expr `diff` expr
     ::= expr `crss` expr
```

## Environment

Tracks `relation_i : [column_1 : type_1,...,column_n : type_n]`

## Type system

The type of an expression is the set of columns \(with their types\) in its relation. For example, the type of of `R(a1 : real, a2 : string)` is `{a1 : real, a2 : string}`. We restrict types of columns to `real` and `string`

## Operational semantics

* The comparison operators for the reals are as usual and lexicographical ordering is followed for strings.
* Loosely speaking, the semantics is in terms of the state tuple

```text
(columns present in an expression, predicates on rows)
```

notation: `--` means "corresponds to the state"

* `project` will just delete some columns from the state

If `R1 -- ({a1 : string, a2: real}, (all r1 in string x real | r1 in R1))`

then `project [a2] R1 -- ({a2 : real}, (all r in real | r in R1.a2))`

* `select` will conjoin more predicates

If `R2 -- ({a1 : real, a2 : string}, (all r2 in real x string | r2 in R2))`

then `select [a1 > 0 /\ a2 = "foo"] -- ({a1 : real, a2 : string}, (all r2 in real x string | r2 in R2 and r2.a1 > 0 and r2.a2 = "foo"))`

* `join` is the composition `select . project . crss` with appropriate parameters
* `unin` requires types to match and works as follows

If `R3 -- ({a1 : real, a2 : real}, (all r3 in real x real | r3 in R3 and r3.a1 > 0 and r2.a2 < 0 ))` and `R4 -- ({a1 : real, a2 : real}, (all r4 in real x real | r4 in R4 and r4.a1 < 0 and r4.a2 > 0))`

then `R3 unin R4 -- ({a1 : real, a2 : real}, (all r in real x real | (r in R3 and r.a1 > 0 and r.a2 < 0) or (r in R4 and r.a1 < 0 and r.a2 > 0)`

* `intr` also requires types to match and works as follows

If `R3 -- ({a1 : real, a2 : real}, (all r3 in real x real | r3 in R3 and r3.a1 > 0 and r2.a2 < 0 ))` and `R4 -- ({a1 : real, a2 : real}, (all r4 in real x real | r4 in R4 and r4.a1 < 0 and r4.a2` What I can't figure out`> 0))`

then `R3 unin R4 -- ({a1 : real, a2 : real}, (all r in real x real | (r in R3 and r.a1 > 0 and r.a2 < 0) and (r in R4 and r.a1 < 0 and r.a2 > 0)` \(the empty set in this case\)

* `diff` also requires types to match and works as follows

If `R3 -- ({a1 : real, a2 : real}, (all r3 in real x real | r3 in R3 and r3.a1 > 0 and r2.a2 < 0 ))` and `R4 -- ({a1 : real, a2 : real}, (all r4 in real x real | r4 in R4 and r4.a1 < 0 and r4.a2 > 0))`

then `R3 diff R4 -- ({a1 : real, a2 : real}, (all r in real x real | (r in R3 and r.a1 > 0 and r.a2 < 0) and !(r in R4 and r.a1 < 0 and r.a2 > 0)`

* `crss` does not require anything about the types

If `R5 -- ({a1 : real, a2 : string}, (all r5 in real x string | r5 in R5 and r5.a1 > 0 and r5.a2 > "foo" ))` and `R6 -- ({a3 : string, a4 : real}, (all r6 in string x real | r6 in R6 and r6.a3 < "bar" and r4.a2 > 5))`

then `R5 crss R6 -- ({a1 : real, a2 : string, a3 : string, a4 : real}, (all r in real x string x string x real | (r.a1 in R5.a1 and r.a2 in R5.a2 and r.a1 > 0 and r.a2 > "foo") and (r.a3 in R6.a3 and r.a4 in R6.a4 and r.a3 < "bar" and r.a4 > 5)`

### Things to think about

* Is what I'm doing decidable? It is well known that first order logic is undecidable, and my predicate calculus for rows is first order complete
* What are my normal forms?

