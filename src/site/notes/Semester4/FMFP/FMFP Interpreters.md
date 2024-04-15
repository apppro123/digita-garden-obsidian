---
{"dg-publish":true,"permalink":"/semester4/fmfp/fmfp-interpreters/"}
---


- conceptually simple: **read** => **evaluate** => **print**
- **concretisation less trivial**: ![Pasted image 20240329174900.png](/img/user/Semester4/FMFP/attachments/Pasted%20image%2020240329174900.png) 
## Mini-Haskell interpreter
### Parsing
- parser constructs an **abstract syntax tree** ( #short AST) ![Pasted image 20240329175201.png](/img/user/Semester4/FMFP/attachments/Pasted%20image%2020240329175201.png)
	- in Haskell: element of data type
	- further processing depend on application but in general: conversion happens between data types e.g. 
		- Compiler: AST → CODE
		- Calculator: AST → Int 
		- Mini-Haskell: AST → AST
	- in ghci there are additional phases such as dependency analysis, type checking, ...
#### Combinatory parsing
- **Idea**: modular construction and composition of parser functions
	- uses lazy & higher-order programming
	- uses monads to package "higher-order plumbing"
#### Parser type
- parser is a **function taking a string** as input
- result is an element of type `a` (typically a data type like `Expr`)
- parser may process only part of input, leaving a **remainder**
	- support composition: `p`parses first part and `q` continues
- allow **multiple results** from parsing via list of successes
```Haskell
data Parser a = Prs (String -> [(a,String)])

parse::Parser a -> String -> String -> [(a,String)]
parse (Prs p) inp = p inp

-- interested in result of first complete parse
completeParse :: Parser a -> String -> a
completeParse p inp
	| results == [] = error "Parse unsuccessful"
	| otherwise     = head results
	where results   = [res | (res,"") <- parse p inp]
```
- **complete parse** if pair with remainder ""
#### primitive parsers
- serving as basic building blocks
```Haskell
-- Fails trivially ([] signifies ‘unsuccessful parse’):
failure :: Parser a
failure = Prs (\inp -> [])

-- Succeeds trivially without progress:
return :: a -> Parser a
return x = Prs (\inp -> [(x,inp)])

--Succeeds trivially with progress:
item :: Parser Char
item = Prs (\inp -> case inp of
						"" -> []
						(x:xs) -> [(x,xs)])

-- Parse a single character with property p
sat :: (Char -> Bool) -> Parser Char
sat p = Prs (\inp -> case inp of
						"" -> []
						(x:xs) -> if p x then [(x,xs)] else [])

--Chars and Strings (including simpler definition of sat)
sat :: (Char -> Bool) -> Parser Char
sat p = item >>= \x -> if p x then return x else failure

char :: Char -> Parser Char
char x = sat (==x)

string :: String -> Parser String
string ""  = return ""
string (x:xs) = char x >> string xs >> return (x:xs)

-- Repetition
many :: Parser a -> Parser [a] -- 0 or more repetitions of p
many p = many1 p ||| return []

many1 :: Parser a -> Parser [a] -- 1 or more repetitions of p
many1 p = p >>= \t -> many p >>= \ts -> return (t:ts)

-- more readable use of >>-
many1 p = do t <- p
			 ts <- many p
			 return (t:ts)

numPos :: Parser Int
numPos = do ts <- many1 (sat isDigit)
return (read ts)  --- read maps numeric string to number

numNeg :: Parser Int
numNeg = do char ’-’
			t <- numPos
			return (-t)
			
num :: Parser Int
num = numPos ||| numNeg -- or: numPos +++ numNeg
```

#### Gluing parsers together
```Haskell
-- Mutual selection: Apply both first and second parser
(|||) :: Parser a -> Parser a -> Parser a
p ||| q = Prs (\s -> parse p s ++ parse q s)

-- Alternative selection: If first parser fails, apply second parser
(+++) :: Parser a -> Parser a -> Parser a
p +++ q = Prs (\s -> case parse p s of
[] -> parse q s

-- Sequencing: first parser p then parser q to results
(>>) :: Parser a -> Parser b -> Parser b
p >> q = Prs (\s -> [ (u,s’’) | (t,s’) <- parse p s,
								(u,s’’) <- parse q s’ ])
-- but above results of first parser (t above) is lost bc. we just use the remainder further
-- Solution: use as second argument a “parser generator” that takes as input the result of the first parser
(>>=) :: Parser a -> (a -> Parser b) -> Parser b
p >>= g = Prs (\s -> [ (u,s’’) | (t,s’ ) <- parse p s,
								 (u,s’’) <- parse (g t) s’ ])
```
### ambiguous grammars
- **Problem:** How should 2-3+4 be parsed? ![Pasted image 20240329194217.png](/img/user/Semester4/FMFP/attachments/Pasted%20image%2020240329194217.png)
- **Solution**
	- disambiguate grammar using **associativity** and **precedence**
	- give user ability to override defaults using **parentheses**
	- **careful**: left-recursive grammars lead to non-terminating recursion
- **Concrete** ![Pasted image 20240329194547.png](/img/user/Semester4/FMFP/attachments/Pasted%20image%2020240329194547.png)
	- parse repeated operation/atom pairs after initial atom
	- obtain left associativity using **fold-left** over list of these pairs
	- use concrete grammar to  build **abstract syntax tree** of type `data Expr = Lit Int | Add Expr Expr | Sub Expr Expr` 
	- ![Pasted image 20240329194939.png](/img/user/Semester4/FMFP/attachments/Pasted%20image%2020240329194939.png)
## $\lambda$-calculus
- **programs are terms** ![Pasted image 20240329195309.png](/img/user/Semester4/FMFP/attachments/Pasted%20image%2020240329195309.png)
- formalising core ![Pasted image 20240329195326.png](/img/user/Semester4/FMFP/attachments/Pasted%20image%2020240329195326.png)
	- enough to construct all others
### Parsing $\lambda$-terms
- data type for $\lambda$-calculus terms 
```Haskell
data Term = Id String | Ap Term Term | Lam String Term 
			deriving Show

atom = ident ||| lamb ||| paren

ident = do id <- identifier
			return (Id id)

term= do t <- atom   -- t
		ts <- many atom -- [t1 t2 ... tn]
		return (foldl Ap t ts)-- Ap(Ap(Ap(t t1) t2) ... tn)

lamb= do token "%"
		 ids <- many1 identifier -- [x1, x2, ..., xn]
		 token "."
		 t <- term -- t
		 return (foldr Lam t ids) -- Lam x1 (Lam x2 (...(Lam xn t)))

paren = do token "("
		   t <- term
		   token ")"
		   return t

str2term s = completeParse term s
```
- application $t_{1}\;t_{2}$ produces left recursion (prefix-syntax simpler)
- syntax without left-recursion ![Pasted image 20240329195612.png](/img/user/Semester4/FMFP/attachments/Pasted%20image%2020240329195612.png)
	- We use `%` and `.` instead of `\` and `->`, respectively
	- Explicit parentheses
	- Every parsing starts with an identifier, or symbols ‘%’ or ‘(’
- **Examples** ![Pasted image 20240329200008.png](/img/user/Semester4/FMFP/attachments/Pasted%20image%2020240329200008.png)
#### Substitution in Haskell
- must respect free and bound variables ![Pasted image 20240329200154.png](/img/user/Semester4/FMFP/attachments/Pasted%20image%2020240329200154.png)
	- e.g. ![Pasted image 20240329200211.png](/img/user/Semester4/FMFP/attachments/Pasted%20image%2020240329200211.png)
- **Haskell implementation** below (Alternative: use Haskell library `Data.Set` to implement `free`)
```Haskell
free :: Term -> [String]
free (Id v) = sing v -- free (x) = {x}
free (Ap s t) = union (free s) (free t) -- free (M N ) = free(M ) ∪ free(N )
free (Lam v t) = diff (free t) (sing v) -- free (λx. M ) = free(M ) \ { x }

empty = []
sing a = [a]

member [] _ = False
member (x:xs) a
	| x < a = member xs a
	| x == a = True
	| otherwise = False

union [] ys = ys
union xs [] = xs
union (x:xs) (y:ys)
	| x < y = x : union xs (y:ys)
	| x == y = x : union xs ys
	| otherwise = y : union (x:xs) ys

diff [] _ = []
diff xs [] = xs
diff (x:xs) (y:ys)
	| x < y = x : diff xs (y:ys)
	| x == y = diff xs ys
	| otherwise = diff (x:xs) ys

-- subst t v s = t[v -> s]
subst :: Term -> String -> Term -> Term
subst (Id x) v s = if x == v then s else Id x
subst (Ap t1 t2) v s = Ap (subst t1 v s) (subst t2 v s)
subst (Lam x t) v s
	| x == v = Lam x t
	| not (member (free s) x) = Lam x (subst t v s)
	| otherwise = Lam z (subst (subst t x (Id z)) v s)
	where z = fresh (union (free t) (free s))
		fresh m = (foldr max "" m) ++ "’" -- returns id not in m
```

### Substitution ![Pasted image 20240329200819.png](/img/user/Semester4/FMFP/attachments/Pasted%20image%2020240329200819.png)
### $\beta$-reduction
- $\beta$-reduction is rule for **simplifying redexes**: $(\lambda x.M)N\hookrightarrow M[x\mapsto N]$
	- **redex** is a term like $(\lambda x.M)N$
	- **contractrum** is the result i.e. $M[x\mapsto N]$
- e.g. $(\lambda x.f(x\;x))N\hookrightarrow f(N\;N)$
#### Evaluation strategies 
- $t_{1}\;t_{2}$ represents the first application of a function to an argument
	- first evaluate $t_{1}:t_{1}\hookrightarrow r_1$
	  If $r_{1}\neq \lambda x.r$ then throw an exception (or return application)
- strategy 1: **Eager**
	- evaluate $t_{2}$ prior to $\beta$-reduction: $t_{2}\hookrightarrow r_{2}$ meaning $(\lambda x.r)r_{2}\hookrightarrow r[x\mapsto r_{2}]$
	- evaluation carried out under an abstraction $(\lambda x.t)$
- strategy 2: **Lazy**
	- apply $\beta$-reduction to $r_{1}\;t_{2}$ i.e. substitute $t_{2}$ without evaluation meaning $(\lambda x.r)t_{2}\hookrightarrow r[x\mapsto t_{2}]$
	- no evaluation under an abstraction
	- result of $\beta$-reduction is then further evaluated
```Haskell
beta (Lam x t) t’ = subst t x t’
eager :: Term -> Term
eager (Id x) = (Id x)
eager (Ap t t’) = case r of
					(Lam _ _) -> eager (beta r r’)
					_         -> Ap r r’
	where r = eager t
		  r’ = eager t’
eager (Lam x t) = Lam x (eager t)

lazy :: Term -> Term
lazy (Id x) = (Id x)
lazy (Ap t t’) = case r of
					(Lam _ _) -> lazy (beta r t’)
					_         -> Ap r t’
	where r = lazy t
lazy t = t     -- no evaluation under a lambda abstraction
```

- **eager** evaluation in **lazy** language ![Pasted image 20240330090825.png](/img/user/Semester4/FMFP/attachments/Pasted%20image%2020240330090825.png)
	- Haskell is lazy and doesn't fully evaluate omega, since not needed to produce result
	- **solution**: use **strict function application** `f $! x` is like `f x` but forces evaluation of its argument $x$ (up to first constructor)
```Haskell
eager :: Term -> Term
eager (Id x) = (Id x)
eager (Ap t t’) = case r of
					(Lam _ _) -> eager ((beta $! r) $! r’)
					_         -> (Ap $! r) $! r’
	where r = eager t
		  r’ = eager t’
eager (Lam x t) = Lam x $! (eager t)
```

### More on Haskell and interpreters ![Pasted image 20240330091131.png](/img/user/Semester4/FMFP/attachments/Pasted%20image%2020240330091131.png)