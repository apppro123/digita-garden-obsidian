---
{"dg-publish":true,"permalink":"/semester4/fmfp/lectures/fmfp-l9/"}
---

## Type classes
- **morphism** ![Pasted image 20240319185409.png](/img/user/Semester4/FMFP/Lectures/attachments/Pasted%20image%2020240319185409.png)
	- monomorphism: just one primitive type
	- polymorphism: can take multiple primitive types
- type classes **restrict polymorphism** ![Pasted image 20240319185749.png](/img/user/Semester4/FMFP/Lectures/attachments/Pasted%20image%2020240319185749.png)
```Haskell
-- from prelude.hs
class Eq a where
	(==) :: a -> a -> Bool
	(/=) :: a -> a -> Bool

	x /= y = not (x==y) -- thus in the end, a has just to be == comparable
	-- example with Eq
	allEqual :: Eq t => t -> t -> t -> Bool

-- instance example
instance Eq Bool where
	True == True = True
	False == False = True
	_     == _     = False
```
- elements of class are called **instances**
	- `instance` builds instances by "interpreting signature functions"
	- instances of primitive types like `Int` use built-in (primitive) qualities
```Haskell
class Visible t where
	stringOf :: t -> String
	size :: t -> Int
	
instance Visible Char where
	stringOf ch = [ch]
	size _ = 1

instance Visible Bool where
	stringOf True = "Wahr"
	stringOf False = "Falsch"
	size b = 1

? (stringOf ’e’) ++ "ine " ++ (stringOf True) ++ "e Aussage"
"eine Wahre Aussage" :: [Char]

instance Visible t => Visible [t] where
	stringOf xs = concat (map stringOf xs)
	size xs = foldr (+) 0 (map size xs)
	-- stringOf xs ... is not a recursive definition bc. on of them is over `[t]` and the other just over `t`

? size [True,False]
2 :: Int

? stringOf [True,False]
"WahrFalsch" :: [Char]
```
- if `t` is visible then a list of type `[t]` is also visible => class **membership** can depend on membership for other types
### Derived classes
```Haskell
class Eq a => Ord a where
	(<), (>), (<=), (>=) :: a -> a -> Bool
	max, min :: a -> a -> a
	-- implement all operators except (<=)
	x < y = x <= y && x /= y
	x >= y = y <= x
	x > y = y <= x && x /= y

max x y | x <= y = y
		| otherwise = x
min x y | x <= y = x
		| otherwise = y
```
- if `a` belong to `Ord`, then `a` must also belong to `Eq`
- functions for `Eq` are inherited and some new ones must be given
### Some type classes
- `Show` and `Read` ![Pasted image 20240319190848.png](/img/user/Semester4/FMFP/Lectures/attachments/Pasted%20image%2020240319190848.png)
- `Foldable` ![Pasted image 20240319190912.png](/img/user/Semester4/FMFP/Lectures/attachments/Pasted%20image%2020240319190912.png)
### Enumeration types (disjoint unions)
```Haskell
data Season = Spring | Summer | Fall | Winter
data Month = January | February | March | April | May | June | July | August |September | October | November | December

-- functions can be written using pattern matching
whichSeason :: Month -> Season
whichSeason January = Winter
...
```
- Syntax
	- start with keyword `data`
	- names different (uniquely named) constructors
	- first letter of each constructor must be upper-case
- Defines a set: `Season = {Spring, Summer, Fall, Winter}`
### Product types
```Haskell
data People = Person Name Age
type Name = String
type Age = Int

-- Constructors are functions 
? :type Person
Person :: Name -> Age -> Peopled

showPerson :: People -> String
showPerson (Person n a) = n ++ " who is " ++ show a ++ " years old"

? showPerson (Person "Uncle George" 85)
"Uncle George who is 85 years old" :: [Char]
```
- an element of type `People` consists of a name `n` and an age `a` e.g. `Person "Uncle George" 85`
#### Product types versus tuples ![Pasted image 20240319191854.png](/img/user/Semester4/FMFP/Lectures/attachments/Pasted%20image%2020240319191854.png)
#### Enumeration and product types ![Pasted image 20240319191929.png](/img/user/Semester4/FMFP/Lectures/attachments/Pasted%20image%2020240319191929.png)
- general case ![Pasted image 20240319192137.png](/img/user/Semester4/FMFP/Lectures/attachments/Pasted%20image%2020240319192137.png)
#### Integration with classes ![Pasted image 20240319192008.png](/img/user/Semester4/FMFP/Lectures/attachments/Pasted%20image%2020240319192008.png)
- or in some cases, class instances can be automatically **derived** ![Pasted image 20240319192047.png](/img/user/Semester4/FMFP/Lectures/attachments/Pasted%20image%2020240319192047.png)
### Recursive types ![Pasted image 20240319192218.png](/img/user/Semester4/FMFP/Lectures/attachments/Pasted%20image%2020240319192218.png)
- recursive functions over data types ![Pasted image 20240319192256.png](/img/user/Semester4/FMFP/Lectures/attachments/Pasted%20image%2020240319192256.png) ![Pasted image 20240319192332.png](/img/user/Semester4/FMFP/Lectures/attachments/Pasted%20image%2020240319192332.png)