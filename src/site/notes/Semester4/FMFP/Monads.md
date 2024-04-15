---
{"dg-publish":true,"permalink":"/semester4/fmfp/monads/"}
---


- #Idea separate values from computation producing the values
	- `f :: a -> b` ordinary function, returns value of type `b`
	- `f :: a -> M b` **monadic** function, returns computation `M b`
		- `M` is a **type constructor** satisfying certain properties (monad laws)
		- by varying `M`, we can model different notions of computation
- Monad is a **type constructor** in the monad type class
- **imagine** a monad as a container which "wraps" a value 
- explains side-effects in a functional context and helps designing controlled side-effects
	- fine-grained control of side effects possible
	- can model computational effects that are not present in imperative languages
## Properties
- every monad supports 2 **basic operations**
	- **embedding a value** into a computation
	- **composing computations**
```Haskell
class Monad m where
	-- return and bind are mathematical core
	return :: a -> m a
	(>>=) :: m a -> (a -> m b) -> m b -- bind
	
	-- shortcut for convenience, when second computatin
	-- doesn't depend on result of first
	(>>) :: m a -> m b -> m b
	m1 >> m2 = m1 >>= (\_ -> m2)
	
	-- not partof mathematical concept of a monad
	-- called on pattern matching error in do-notation
	fail :: String -> m a

-- instances
instance Monad Maybe where
	return x       = Just x
	Nothing >>= _  = Nothing
	(Just x) >>= f = f x
```
### Monad laws
Monad operations must satisfy
- (1) `return x >>= f = f x` **left unit**
- (2) `m >>= return = m` **right unit**
- (3) `(m >>= f) >>= g = m >>= (\x -> (f x >>= g))` **associativity**
## Examples
### monad
```Haskell
data Maybe a = Nothing | Just a

-- e.g. for making a safe division
safeDiv::Int -> Int -> Maybe Int
safeDiv n d
	| d /= 0 = Just (n `div`d)
	| otherwise = Nothing
```
### Computation with monads
```Haskell
-- idea: computation takes a state of type s and transforms it into
-- a result of type a and a successor state of type s
data State s a = State (s -> (a,s)) -- here s is just a type, not an argument so in reality s on left hand side doesn't have to be s on right hand side, but they just have to be the same type!

-- state access: read current value of state without changing it
get :: State s s
get = State (\s -> (s,s))

-- state update: write a new state value ignoring the current state
put :: s -> State s ()
put t = State (\s -> ((), t))

-- auxiliary function that opens monad and 
-- runs computation from initial state s0
runState :: (State s a) -> (s -> (a, s))
runState (State m) s0 = m s0 -- bc. `(State m)` returns a function (see data State s a) which takes s0 as an argument; I just don't know yet, why this is not reflected in the data type of runState (why there is not another input)

-- return embeds a value into a stateful computation
return :: a -> State s a
return x = State (\s -> (x,s))

-- Bind composes two stateful computations with value binding
(>>=) :: State s a -> (a -> State s b) -> State s b
m >>= k = State (\s -> let (x, t) = runState m s 
						in runState (k x) t)
```
- application of state monad in **counter** ![Pasted image 20240410104944.png](/img/user/Semester4/FMFP/attachments/Pasted%20image%2020240410104944.png)
	- state monad **encapsulate program composition**
	- **run program**: invoke `runState tick s0` where `s0` is some initial state
- application of state monad in **tree renaming**
	- as reference: **without** state monad => ugly plumbing needed to thread `state` through two recursive calls ![Pasted image 20240410105359.png](/img/user/Semester4/FMFP/attachments/Pasted%20image%2020240410105359.png)
	- **state monad** takes care of all the plumbing ![Pasted image 20240410105143.png](/img/user/Semester4/FMFP/attachments/Pasted%20image%2020240410105143.png)
	- or with more **abstraction** ![Pasted image 20240410105239.png](/img/user/Semester4/FMFP/attachments/Pasted%20image%2020240410105239.png)
## Input/Ouput
- **problematic** bc. we don't know what we get as an input from user => reasoning would no longer be sound ![Pasted image 20240410110528.png](/img/user/Semester4/FMFP/attachments/Pasted%20image%2020240410110528.png)
	- bc. result depends on order in which the argument are evaluated
	- I/O-functions have side effects => state of world ( #disclaimerN nice name^^) changes
	- e.g. `IO Int` not same as `Int` e.g. you cannot subtract bc. `IO Int` is monadic
```Haskell
inputInt :: IO Int
inputString :: IO String
outputInt :: Int -> IO ()
```
- `()` is the unit type in Haskell [[Semester4/FMFP/Atoms/Unit type#Haskell\|Unit type#Haskell]]
### Basic Actions 
- ![Pasted image 20240410112144.png](/img/user/Semester4/FMFP/attachments/Pasted%20image%2020240410112144.png)
### Sequencing
- ![Pasted image 20240410112308.png](/img/user/Semester4/FMFP/attachments/Pasted%20image%2020240410112308.png)
### Examples
```Haskell
-- printing string on screen
putString :: String -> IO ()
putString ""     = return ()
putString (x:xs) = do putChar x; putString xs

-- reading string from keyboard
getString :: IO String
getString = do c <- getChar
				if c == ’\n’
				then return ""
				else do cs <- getString
					return (c:cs)
					
-- hello world (what else)
main :: IO ()
main = do putString "Hi, I am HAL. Who are you?\n"
name <- getString
putString ("Hello " ++ name ++ "!\n")
```
## Functors
- when you instantiate `Monad`, you must instantiate `Functor` and `Applicative` too
```Haskell
class Functor f where
fmap :: (a -> b) -> f a -> f b
```
### Laws
- Functor instances must satisfy two functor laws
	1. **Identity**: `fmap id v = v`
	2. **Composition**: `fmap f (fmap g v) = fmap (f . g) v`
### operations
- in applicative functor ![Pasted image 20240411181101.png](/img/user/Semester4/FMFP/attachments/Pasted%20image%2020240411181101.png) mimicks function application #ToDo find symbols for LaTex
```Haskell
class Functor f => Applicative f where
pure :: a -> f a
(<*>) :: f (a -> b) -> f a -> f b -- associates to the left

instance Applicative Maybe where
pure x = Just x
Just f <*> Just x = Just (f x)
_      <*> _      = Nothing
```
#### Applicative functor laws
1. **Identity** `pure id <*> v = v`
2. **Homomorphism** `pure f <*> pure x = pure (f x)`
3. **Composition** `pure (.) <*> u <*> v <*> w = u <*> (v <*> w)`
4. **Interchange** `v <*> pure x = pure (\f -> f x) <*> v`
5. **fmap** `fmap f v = pure f <*> v`
- canonical implementation for monads
```Haskell
pure x = return x
u <*> v = u >>= \f -> v >>= \x -> return (f x)
```
- applicative functor laws can be derived from monad laws
### Examples
- `map` function transforms all elements in a structure: type class `Functor` can capture this functionality
```Haskell
instance Functor Tree where
fmap _ Leaf         = Leaf
fmap f (Node x l r) = Node (f x) (fmap f l) (fmap f r)

-- in console
> fmap (*2) [0,1,2] = [0,2,4]
> fmap (*2) (Node 5 Leaf Leaf) = Node 10 Leaf Leaf
```
- applicative functor examples ![Pasted image 20240411181433.png](/img/user/Semester4/FMFP/attachments/Pasted%20image%2020240411181433.png)
## Resources
- [recommended monad tutorials](http://www.haskell.org/haskellwiki/Tutorials#Using_monads)