# Introduction

This is intended as a rough guide/outlines of the concepts to be introduced,
hopefully in a live and interactive manner.





## Hello World

```haskell
putStrLn "Hello world"
```

## Reading a function type signature

```haskell
add :: Int -> Int -> Int
add a b = a + b
```

## Calling a function

```
> add 1 2
3

> add 1 (add 2 3)
6

> add (add 1 2) 3
6

> add "a" 2
<interactive>:8:1:
    Couldn't match expected type ‘Int’ with actual type ‘[Char]’
```

## Type Inference

```haskell
count a b = a + b
```

```
> :t count
count :: Num a => a -> a -> a
```

## Lambda

```haskell
add :: Int -> Int -> Int
add a b = a + b
add a = \b -> a + b
add = \a -> \b -> a + b
add = \a b -> a + b
```









## Lists

```haskell
list :: [Int]
list = [1, 2, 3, 4]
```

## Functions

```haskell
> map (\x -> x + 1) [1, 2, 3, 4]
[2, 3, 4, 5]

> take 2 [1, 2, 3, 4]
[1, 2]
```

## Strings are just Lists

```haskell
helloWorld :: String
helloWorld = "hello world"
```

```haskell
> :i String
type String = [Char]
```

```haskell
helloWorld :: [Char]
helloWorld = "hello world"
```

```haskell
helloWorld :: [Char]
helloWorld = ['h', 'e', 'l', 'l', 'o', ' ', 'w', 'o', 'r', 'l', 'd']
```

```haskell
import Data.Char

> map (\x -> toUpper x) "hello world"
"HELLO WORLD"

> take 1 "hello world"
"he"
```






## Data types

- Similar to an "enum"
- _Must_ start with Upper Case

```haskell
data Fruit = Apple | Banana | Tomato
```

## Data types

- But can contain values

```haskell
data Eat = Yum Fruit | Yuck Fruit String
```

## Pattern Matching

```haskell
eat :: Fruit -> Eat
eat Apple = Yum Apple
eat Banana = Yum Banana
eat Tomato = Yuck Tomato "It's not a real fruit"
```

```haskell
eat :: Fruit -> Eat
eat fruit = case fruit of
  Apple -> Yum Apple
  Banana -> Yum Banana
  Tomato -> Yuck Tomato "It's not a real fruit"
```

## Booleans

- Just a data type

```haskell
data Bool = True | False
```

```haskell
not :: Bool -> Bool
not True = False
not False = True
```

- Special syntax

```haskell
if ... then ... else ...
```

```haskell
not :: Bool -> Bool
not b = if b then False else True
```

## Lists (again)

- Lists are actually linked-lists

```haskell
empty :: [Int]
empty = []

one :: [Int]
one = 1 : []

list :: [Int]
list = 1 : 2 : 3 : 4 : []
```

- Pattern matching

```haskell
startsWith :: Int -> [Int] -> Bool
startsWith i [] = False
startsWith i (h : v) = i == h
```







## Everything is immutable (by default)

```haskell
> ten = ten + 1
Multiple declarations of ‘ten’
```










## "Real world"

- Special `do` syntax
  - Indentation aware (like Python)
  - (Curly brackets and semicolon are available, too.)

```haskell
main :: IO ()
main = do
  putStrLn "Input value"
  v <- input
  putStrLn ("You entered" ++ show v)
```

## Loops?

- Recursion

```haskell
contains :: Int -> [Int] -> Bool
contains v [] =
  False
contains v (h : t) =
  if v == h
    then True
    else contains v t
```

```haskell
main :: IO ()
main = do
  putStrLn "Input value"
  v <- getLine
  putStrLn ("You entered" ++ show v)
  main
```

## Higher Order Function

- Functions that take functions as inputs
  - E.g Have f x and [x1,x2...xN]
  - Want [f x1,f x2,...,f xN]

```haskell
add3 :: Int -> Int
add3 x = x + 3

myMap _ [] = []
myMap f (x:xt) = f x : myMap f xt
```
```haskell
> myMap add3 [1..5] 
[4,5,6,7,8]

>:t myMap
myMap :: (a -> b) -> [a] -> [b]
```
- (a -> b) is "a function that takes an a and outputs a b
- Common ones done for us
  - map "maps" a function over a list
  - filter takes a predicate and a list and outputs the parts of the list which satisfy the predicate
  - There are many more that wont be covered e.g. flip, foldr, zipWith...
```haskell
>:t map
map :: (a -> b) -> [a] -> [b]

> map (+3) [1..5]
[4,5,6,7,8]

>:t filter
filter :: (a -> Bool) -> [a] -> [a]

> let lessThen3 x = x < 3
> filter (lessThen3) [1..5]
[1,2]
```


## Hoogle

- Search the libraries by type
- https://www.haskell.org/hoogle/
