# Abstract-Algebras
Mathematica notebooks about abstract algebra: what kinds, how many for each size, etc.

What is abstract algebra? First note that mathematicians love abstractions, taking properties and generalizing them. Abstract algebra uses a generalization of the features of operations on numbers that many of us had learned about. Properties like being commutative and associative, being independent of order and grouping, true of addition and multiplication though not of subtraction or division.

The functions or operators are from some set (the domain set) to the same set, usually a finite set in most of the examples that I will consider here. Every one will be over all the elements in that set, while they need not return every element in that set. Much of these notebooks' content is for counting every possible function with some properties for some size of set.

A major resource used for the numbers and formulas in many of these notebooks is [The On-Line Encyclopedia of Integer Sequences® (OEIS®)](https://oeis.org/)

## Unary functions
Functions of one variable - Notebook: `Unary Functions.nb`

For a finite domain set, repeated application of such a function will converge onto a limit cycle of an endlessly repeating sequence, a cycle which can have one member, the fixed point.

## Binary functions
Functions of two variables - Notebook: `Groupoids.nb`

Called groupoids or magmas.

They have a variety of possible algebraic properties. For operation *:
* Commutative: b * a = a * b
* Associative: (a * b) * c = a * (b * c)
* Left, right, two-sided (plain) identity e: e * a = a, a * e = a, both
* Left, right, two-sided (plain) zero, absorber, annihilator z: z * a = z, a * z = z, both
* Ideals generalize zeros to sets
* Division: for every a, b, there exists a unique x, y satisfying a * x = y * a = b. x and y can be either equal or distnct.

Here are groupoids with some of these features:
* Semigroup: associative
* Monoid: associative, identity
* Group: associative, identity, division (gives inverses)
* Quasigroup: division
* Loop: division, identity

## Ternary functions
Functions of three variables - Notebook: `Pure Ternary Operators.nb`

That notebook finds all pure ternary functions f(a,b,c), pure meaning not some combination of binary functions, like f1(f2(a,b),c). It only finds them for a set with size 2, because the number of them grows large **very** fast. For domain size n and number of arguments (input values) m,

number (labeled) = n<sup>n<sup>m</sup></sup>

| Size | 1 | 2 | 3 | 4 | 5 | 6 |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | 1 | 1 | 1 | 1 | 1 | 1 |
| 2 | 4 | 16 | 256 | 65536 | 4294967296 |
| 3 | 27 | 19683 | 7625597484987 |
| 4 | 256 | 4294967296 |
| 5 | 3125 |

I find this table of results
| What | Lbld | Unlb |
| --- | --- | --- |
| Unary | 4 | 3 |
| Binary | 16 | 10 |
| Ternary | 256 | 136 |
| From Binary | 152 | 80 |
| Pure Ternary | 104 | 56 |

Lbld = labeled, Unlb = unlabeled (isomorphic sets)

## Partition transform
Notebook: `Partition Transform.nb`

Many abstract-algebra entities can be decomposed into direct products of smaller ones; those ones are "reducible". Those that cannot are "irreducible". To find total counts from counts of irreducible ones, it is necessary to use a partition transform, one of Euler's transforms. For irreducible numbers n1, n2, n3, n4, ... and total numbers nt1, nt2, nt3, nt4, ...
* nt1 = n1
* nt2 = n2 + n1<sup>{2}</sup>
* nt3 = n3 + n2 * n1 + n1<sup>{3}</sup>
* nt4 = n4 + n3 * n1 + n2<sup>{2}</sup> + n2 * n1<sup>{2}</sup> + n1<sup>{4}</sup> 
* ...

The powers are symmetrized: n<sup>{m}</sup> = n * (n+1) * ... * (n+m-1) / m!

This transform is the partition transform, one of Euler's transforms. It can be inverted to find the irreducible counts from the total counts.

The algorithm uses Möbius (Moebius) inversion, also implemented in this notebook:
* a(n) = sum over d evenly dividing n of b(d)
* b(n) = sum over d evenly dividing n of mu(n/d)*a(d)
where mu(n) is 1 if n = 1, (-1)<sup>m</sup> for n having m distinct prime factors, and 0 for n having a repeated prime factor.
