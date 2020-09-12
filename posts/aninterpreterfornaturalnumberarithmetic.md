# An interpreter for natural number arithmetic

I implemented the first \(untyped\) system descried in [TaPL](https://www.cis.upenn.edu/~bcpierce/tapl/) in [haskell](https://github.com/iambrj/haskground/blob/master/tapl/arith.hs). This post describes the same.

Firstly, we have an inductive datatype for various terms

```text
data Term = MyTrue
          | MyFalse
          | IfThenElse Term Term Term
          | MyZero
          | MySucc Term
          | MyPred Term
          | MyIsZero Term
        deriving (Show)
```

this means a term in our language can either be a `MyTrue` \(i.e. the boolean true\) etc.

Next we have an auxiliary function to check if a given expression evaluates to a number.

```text
isNumeric :: Term -> Bool
isNumeric e = case e of
                MyZero -> True
                MySucc t -> isNumeric t
                MyPred t -> isNumeric t
                _        -> False
```

this is useful to catch nonsensical expressions \(and this where the need for types arises from\).

Finally, we have an evaluator for expressions in our language

```text
evaluate :: Term -> Term
evaluate e = case e of
               MyTrue   -> MyTrue
               MyFalse  -> MyFalse
               IfThenElse cond texp fexp -> case (evaluate cond) of
                                              MyTrue  -> evaluate (texp)
                                              MyFalse -> evaluate (fexp)
                                              _       -> error "Non-boolean value used in if-then-else"
               MyZero   -> MyZero
               MySucc term -> if (isNumeric term) then (MySucc term) else (error "MySucc applied to non numeric expression")
               MyPred term -> if (isNumeric term)
                                 then case (evaluate term) of
                                        MyZero -> MyZero
                                        MySucc p -> p
                                 else error ("MyPred applied to non numeric expression")
               MyIsZero term -> if (isNumeric term)
                                   then case (evaluate term) of
                                        MyZero -> MyTrue
                                        _      -> MyFalse
                                   else (error "MyIsZero applied to non numeric expression")
```

Now we can evaluate expressions in our language using GHCi. For example,

```text
*Main> show (evaluate (IfThenElse (MyTrue) (MySucc MyZero) (MyZero)))
"MySucc MyZero"
```

