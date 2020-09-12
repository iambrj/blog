# Alternative's some and many

Consider the parser type and a simple `Char` parser

```text
import Control.Applicative
import Data.Char

-- char string parser
newtype P a = P { runP :: String -> [(a,String)] }

-- runP (P p) s = p s

instance Functor P where
  -- fmap :: (a -> b) -> f a -> f b
  fmap f (P q) = P (\\s -> [ (f y,ys) | (y,ys) <- q s])

instance Applicative P where
  -- pure :: a -> f a
  pure x = P (\\s -> [(x,s)])
  -- (<*>) :: f (a -> b) -> f a -> f b
  P f <*> P a = P (\\s -> [(x y, ys) | (x,xs) <- f s, (y,ys) <- a xs])

letter = P p where      -- sample parser
  p (x:xs) | isAlpha x = [(x,xs)]
  p _ = []
```

this can now be used as follows

```text
> runP letter "123"
[]
> runP letter "a123"
[('a', "123")]
```

Now, consider the following line

```text
> foo = runP ((:) <$> letter) "asdf"
> :t foo
foo :: [([Char] -> [Char], String)]
```

i.e. it returns a list of tuples where the first element is a function that concatenates parsed results. For example

```text
> fst (head foo) "bcd"
"abcd"
```

The second element is the remaining unparsed string.

```text
> snd (head foo)
"sdf"
```

Now we can use `<*>` to chain parsing operations as follows, starting with `pure []`

```text
> runP ((:) <$> letter <*> pure []) "asdf"
[("a", "sdf")]
> runP ((:) <$> letter <*> ((:) <$> letter <*> pure [])) "asdf"
[("as", "df")]
```

As can be seen, this quickly gets out of hand. The solution? Define an instance of `Alterantive` and use `some` and `many`

```text
instance Alternative P where
  -- (<|>) :: f a -> f a -> f a
  P p <|> P q = P (\\s-> p s ++ q s)
  -- empty :: f a   -- the identity of <|>
  empty = P (\\s-> [])

some f = (:) <$> f <*> many f
many f = some f <|> pure []
```

i.e. `some` runs `f` once, then `many` times and returns by consing the results. `many` runs `f` `some` times and alteratively returns the empty list.

Now, we can write the following instead

```text
> runP (many letter) "ab123"
[("ab","123"),("a","b123"),("","ab123")]
> runP (some letter) "ab123"
[("ab","123"),("a","b123")]
```

## References

* [https://stackoverflow.com/a/18110679/12158779](https://stackoverflow.com/a/18110679/12158779)
* [https://stackoverflow.com/a/7681283/12158779](https://stackoverflow.com/a/7681283/12158779)

