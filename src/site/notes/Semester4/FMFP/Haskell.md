---
{"dg-publish":true,"permalink":"/semester4/fmfp/haskell/"}
---


### operators 
- have diff. binding strength e.g. 
	- `^` binds stronger than `+` see `? 2 + 3^2` => `11`
	- `not` stronger than `&&` and `||`
- order and equality return `True` or `False` of type Bool
	- same as in other programming languages but 
		- `/=` unequal
## Types
### Int
- `Int` type with at least the range $\{-2^{29},\dots,2^{29}-1\}$
	- support for **unbounded** and **arithmetic**: `Integer`
### bool
- value: `True, False`
### Char
- e.g. `'a','0','\t'`
- `? ord 'a'` => `97` or `? chr 97` => `'a'`
### String
- e.g. `"hello", "123"`
- `? "Hello " ++ "there"` => `"Hello there"`
### Double
`0.3456, -2.85e03`
### Tuple
- used to model composite objects ("records")
- example of a type constructor
	- if $T_{1},\dots,T_{n}$ are types, then $(T_{1},\dots,T_{n})$ is a (tuple) type
	- ![Pasted image 20240220114644.png](/img/user/Semester4/FMFP/Lectures/attachments/Pasted%20image%2020240220114644.png)
### List
- If $T$ is a type then $[T]$ is a type
- empty list: `[]::[T]`
- non-empty list `(x:xs)::[T]` if $x::T$ and $xs::T$
- **abbreviations**
	- `? [3..6] => [3,4,5,6]::Int`
	- `? [6..3] => []::Int
	- `[n, p..m]` means count from $n$ to $m$ in steps of $p − n$
		- `? [7,6..3] => [7, 6, 5, 4, 3] :: [Int]`
		- `? [0.0, 0.3 .. 1.0] => [0.0,0.3,0.6,0.8999999999999999] :: [Double]`
- `x:[y]` appends an element `x` to a list `[y]`
- `[x]++[y]` concatenates two lists
#### Difference lists
- function `[a] -> [a]` that prepends a list to its argument
- e.g. ![Pasted image 20240329105908.png](/img/user/Semester4/FMFP/attachments/Pasted%20image%2020240329105908.png)
- **implementation** ![Pasted image 20240329105948.png](/img/user/Semester4/FMFP/attachments/Pasted%20image%2020240329105948.png)
### Own types
- types always start with a capital letter
- `type Person = String`
- `type Database = [(Person,Book)]`
### Class
- defines a **set of types**
- elements of the class are called **instances**
#### Examples
```Haskell
allEqual :: Eq t => t -> t -> t -> Bool -- where Eq is a class
```
## Functions
- if argument doesn't matter use `_` e.g. `f a _ = a` for `f :: Int -> Int -> Int`
- evaluation by
- generic type definition possible e.g. `ownLength :: [a] -> Int` where `a` is the generic type
- `do` when function has side-effects e.g. in IO
- own e.g.
```Haskell
sumList::[Int] -> Int
sumList []     = 0 -- also handle the empty list case
sumList (x:xs) = x + sumList xs
```
- standard ones: 
	- length
	- append
	- `[2] ++ [3,4,5] => [2,3,4,5]`
	- `? 2 : [3,4,5] => [2,3,4,5]` but `? [2] : [3,4,5] => Error`
### How to use
#### Infix binary 
Infix binary function is also called an "operator" `? 7 'mod' 2`
#### prefix 
Operators can also be written in prefix notation: `? (+) 3 4`
### Examples
- (e.g. for `Int`) +, * , ^, -, div, mod, abs
	- evaluate by `? mod 7 2` => `1`
### branches
- `if test then a else b`
	- `a` and `b` have to be of same type
### multi case
- defined using other **operators**: `f x y = (x || y) && not  (x && y)`
- defined using **guards**
```Haskell
f x y
  | x         = not y
  | otherwise = y
```
- defined using multiple **cases** (new)
	- priority from above down
	- exception, if one case is not covered but it's used
```Haskell
f True True = False
f True False = True
f False True = True
f False False = False
```
- cases can contain variables
```Haskell
f True  y = not y
f False y = y
```
```Haskell
f 0 = 1
f 1 = 2
f x = x*x
```
### Advice on recursion
> Defining recursive functions is like riding a bicycle: it looks easy when someone else is doing it; it may seem impossible when you first try to
> do it yourself, but becomes simple and natural with practice.”
> \- G. Hutton, Programming in Haskell

 ![Pasted image 20240308133744.png](/img/user/Semester4/FMFP/attachments/Pasted%20image%2020240308133744.png)
### Higher-order functions
- just higher order, if function takes function(s) as input ![Pasted image 20240308203127.png](/img/user/Semester4/FMFP/attachments/Pasted%20image%2020240308203127.png)
### $\lambda$-expression
- for writing functions in-line
	- good for when functions are just used once and rather short
- ![Pasted image 20240308210034.png](/img/user/Semester4/FMFP/attachments/Pasted%20image%2020240308210034.png)
## Input-Output
```Haskell
-- putStrin :: String -> IO()

-- getLine :: IO String

-- read String :: t, where t is a type and it tries to convet String to this type 

-- show a => String of a

func1 = do
  putStrLn "Test"
  n <- getLine
  putStrLn ("Text: " ++ show (func2 (read n :: Int)))
```
- [[Semester4/FMFP/Monads#Input/Ouput\|Monads#Input/Ouput]]
## Other
### Shell
- `ghci`: open
- `:load name-of-file.hs` load modules from file
- `reload` loads last file again (e.g. after changing functions)

### Lazy Evaluation
- Haskell uses **Lazy evaluation** ![Pasted image 20240220112718.png](/img/user/Semester4/FMFP/Lectures/attachments/Pasted%20image%2020240220112718.png)
- possible problem of lazy evaluation is **duplicated computation**: avoided by simultaneously reducing both occurrences
- **Summary**: function arguments are evaluated only when needed and at most once
#### Cool applications
- compute with **infinite data** in **finite time** ![Pasted image 20240329151246.png](/img/user/Semester4/FMFP/attachments/Pasted%20image%2020240329151246.png)
- implementation of **sieve of Eratosthenes**  ![Pasted image 20240329151339.png](/img/user/Semester4/FMFP/attachments/Pasted%20image%2020240329151339.png)
### 2D layout
- **spaces** are important don't use TABs (in modern IDEs it should be okay, but this maybe a reason for an erroneous program)
- **indentation** determines separation of definitions
	- all function definitions must start at same indentation level
	- if a definition requires n > 1 lines, indent lines 2 to n further
	- recommended layout![Pasted image 20240220123243.png](/img/user/Semester4/FMFP/Lectures/attachments/Pasted%20image%2020240220123243.png)
## Patterns
- **purposes**
	- checks if argument has proper form
	- binds values to variables
### Rules
- patterns are **inductively** defined
- pattern required to be **linear** i.e. each variable can occur at most once
- Examples: `[(x,foo),_] , ((x,y),_) , 1:(2:(x,y))`
- Counterexamples: `(x ++ y, z) , [x,y,z,x]`
### List comprehension
Notation for sequential processing of list elements
- analogous to set comprehension in set theory $\{2\cdot x|x\in X\}$
- Haskell notation `[2*x| x <- xs]`
- can be augmented with guards: `[2*x | x <- xs, pred1(x), ...]`
### Examples
- `(x:xs)` matches with `[2,3,4]` as $x=2$ and $xs=[3,4]$
- `? let ([x,y,z],t) = ([1,2,3],(20,30)) in x + y => 3 :: Int`
- `? [2*x | x <- [1,2,3,4,5]] => [2,4,6, 8, 10]`
- `? [n ‘mod‘ 2 == 0 | n <- [2,4,7]] => [True,True,False]`
- `? [2*x | x <- [0,1,2,3,4,5,6], x ‘mod‘ 2 == 0, x > 3] => [8,12]`
- easy quick sort^^
```Haskell
q []     = []
q (p:xs) = q [x | x<-xs, x <= p] ++ [p] ++ q [x | x<-xs, x > p]
```