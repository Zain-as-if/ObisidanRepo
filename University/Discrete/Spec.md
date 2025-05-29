Combinatorics - Counting Methods
- Product
- Sum 
- etc
Selections
Permutations
Combinations
Binomial Expansion
Binomial Coefficients & Combinatorial Identities
Pigeonhole Principle

Discrete Probability Theory
Finite Probability Spaces
Equiprobable Spaces
Conditional Probability
Independent Events
Bayes' Theorem

Graph Theory
Graph Models
- Directed
- Weighted
- etc
Isomorphic Graphs
Vertex Degree
Paths + Cycles
Bipartite Graphs
Trees

---
Conjunction = AND
Disjunction = OR

Inclusive OR -> Either true then true (Normal OR) 
Exclusive OR -> X or Y but not both
P->Q
- Converse Q->P
- Inverse  ¬P->¬Q
- Contrapositive ¬Q->¬P
$\mathbb{N}$ - Natural Numbers X>0
$\mathbb{Z}$ - Integers $-\infty<X<\infty$ not including decimal/fraction numbers (only whole number)
$\mathbb{Q}$ - Rational (Fractions)
$\mathbb{A}$ - Algebraic (Solution to polynomial w/ rational coefficients)
$\mathbb{R}$ - $-\infty<X<\infty$
$\mathbb{I}$ - Imaginary
$\mathbb{C}$ - Complex

---
<h4>Counting Rules</h4>
Product Rule
Sum Rule
Subtraction Rule - Principle Inclusion-Exclusion
- $|A \lor B|=|A|+|B|-|A \land B|$
Division Rule
- $\frac{n}{d}$ ways to do task if can be done using procedure that can be carried out in n ways, where there are d corresponding outcomes per group
- E.g. How many ways can i sit 6 people around a circular table where two seating are considered the same when each person has the same left and right neighbour
E.g.
How many bit strings of length 6 start with 1 or end with 1
$|A \lor B|=|A|+|B|-|A \land B|$
A = length 6, start with 1
B = length 6, end with 1
A = $2^5$
B = $2^5$
$|A \land B|=2^4$
$|A \lor B|=2^5+2^5-2^4=48$

<h4>Permutation</h4>
**Ordered** arrangement of distinct objects. r-permutation is arrangement of r-elements of a set

E.g.
Let S={A,B,C}. find all 2-permutations
AB BA
AC CA
BC CB
6 Permutations
$$P(n,k)=\frac{n!}{(n-k)!}$$
n=3 and r=2 in this case
$P(3,2)=\frac{3\cdot 2\cdot 1}{(3-2)!}=\frac{6}{1}=6$
<h4>Combinatorics</h4>
**Unordered** arrangement of elements of a set. r-combination is a subset of the set with r elements

E.g.
Let S={A,B,C}. find all 2-combinations, relate to number of 2-permutations

AB BA
AC CA
BC CB

6 Permutations 
3 Combinations (AB, BA same)
$$C(n,r)=\frac{n!}{(n-r)!r!}$$
$C(3,2)=\frac{3!}{(3-2)!2!}=\frac{6}{2}=3$

E.g. 
How many poker hands of 5 cards can be dealt from a standard deck of 52 cards

Don't care about order, just cards, combination rather than permutation
$C(52,5)=\frac{52!}{(52-5)!5!}$

E.g.
In how many ways can 100 marathon runners place in 1st, 2nd and 3rd

Care about order
$P(100,3)=\frac{100!}{(100-3)!}$
---
<h4>Binomial Theorem</h4>
$$(x+y)^n=\sum^n_{j=0}x^{n-j}y^j=\begin{pmatrix}n\\0
\end{pmatrix}x^n+\begin{pmatrix}n\\1\end{pmatrix}x^{n-1}y+\dots+\begin{pmatrix}n\\n-1\end{pmatrix}xy^{n-1}+\begin{pmatrix}n\\n\end{pmatrix}y^n$$
E.g.
What is binomial expansion of $(x+y)^4$
1. $\begin{pmatrix}4\\0\end{pmatrix}=4C_{0}=C(4,0)=\frac{4!}{0!(4-0)!}=\frac{4!}{4!}=1$, $\begin{pmatrix}4\\0\end{pmatrix}x^4=x^4$
2. $\begin{pmatrix}4\\1\end{pmatrix}=4C_{1}=C(4,1)=\frac{4!}{1!(4-1)!}=\frac{4!}{3!}=4$, $\begin{pmatrix}4\\1\end{pmatrix}x^{4-1}y=4x^3y$
3. $\begin{pmatrix}4\\2\end{pmatrix}=4C_{2}=C(4,2)=\frac{4!}{2!(4-2)!}=\frac{4!}{4}=6$, $\begin{pmatrix}4\\2\end{pmatrix}x^{4-2}y^2=6x^2y^2$
4. $\begin{pmatrix}4\\3\end{pmatrix}=4C_{3}=C(4,3)=\frac{4!}{3!(4-3)!}=\frac{4!}{3!}=4$, $\begin{pmatrix}4\\3\end{pmatrix}x^{4-3}y^3=4xy^3$
5. $\begin{pmatrix}4\\4\end{pmatrix}=4C_{4}=C(4,4)=\frac{4!}{4!(4-4)!}=\frac{4!}{4!}=1$, $\begin{pmatrix}4\\4\end{pmatrix}y^4=y^4$
$x^4+4x^3y+6x^2y^2+4xy^3+y^4$

Coefficient of term containing $x^{62}$ of $(3x+2)^{100}$
1. $\begin{pmatrix}100\\38\end{pmatrix}=100C_{38}=C(100,38)=\frac{100!}{38!(100-38)!}=\frac{100!}{38!62!}$
2. $\begin{pmatrix}100\\38\end{pmatrix}x^{100-38}y^{38}=\frac{100!}{38!62!}(3x)^{62}2^{38}$
3. Coefficient = $\frac{100!}{38!62!}\cdot 3^{62}\cdot 2^{38}$

Pascal's Identity
$$\begin{pmatrix}n+1\\k\end{pmatrix}=\begin{pmatrix}n\\k-1\end{pmatrix}+\begin{pmatrix}n\\k\end{pmatrix}$$
---
<h4>Probability Rules</h4>
S = Finite sample space, Equally likely outcomes
A = Event where $A \in S$ 
P(A) = $\frac{|A|}{|S|}$ 

Rules:
1. P(S) = 1, probability all events in sample space = 1
2. 0<=P(A)<=1, Individual probability of event between 0-1
3. P(A') = 1-P(A)
4. P(at least 1) = 1 - P(none), One event occurring, more than one outcome E.g.![[Pasted image 20250527120524.png]]
5. $P(A \lor B)=P(A)+P(B)-P(A \land B)$
6. $P(A \land B)=P(A)\cdot P(B|A)$ 

<h4>Conditional Probability</h4>
$P(A|B)=\frac{P(A \land B)}{P(B)}$
E.g.
Bit string length 4 generated at random so each of 16 bit strings of length 4 ($2^4$) is equally likely. What is probability that bit string contains at least 2 consecutive 0's given first bit is a zero
P(at least 2 0's|first bit 0) = $\frac{\text{P(at least 2 0's } \land \text{ first bit 0)}}{\text{P(first bit 0)}}=\frac{\frac{5}{16}}{\frac{1}{2}}$
<h4>Independence</h4>
Events A and B independent if and only if:
$P(A \land B)=P(A)\cdot P(B)$

E.g.
Assume family has 2 children, {BB, BG, GB, GG}. Are having two boys (A) and having at least one boy (B) independent.

$\begin{align}P(A \land B)&=P(A)\cdot P(B) \\ \frac{1}{4}&=\frac{1}{4}\cdot \frac{3}{4} \\ \frac{1}{4}&\neq \frac{3}{16}\end{align}$
Not independent

---
<h4>Random Variables</h4>
![[Pasted image 20250527122103.png]]

<h4>Binomial Distribution</h4>
![[Pasted image 20250527122203.png]]

--- 
<h4>Inclusion-Exclusion</h4>
![[Pasted image 20250527123723.png]]
![[Pasted image 20250527124018.png]]

 ---
 <h4>Graphs</h4>
![[Pasted image 20250527130119.png]]
![[Pasted image 20250527130201.png]]![[Pasted image 20250527130208.png]]

---
<h4>Pigeon Holes</h4>
N Objects are placed into k boxes, there is at least one box containing $\lceil \frac{N}{k} \rceil$ objects

E.g. 
Among 50 people what is numebr of people that must be born on the same month
1. 50 people = N
2. 12 months = k
3. $\lceil \frac{50}{12} \rceil=5$

How many students in class must be there to ensure that 3 students get same grade {A,B,C,D,F}
1. Students = N
2. 5 grades = k
3. $\left\lceil  \frac{N-1}{5}  \right\rceil=3-1$
4. =11
---
<h4>Combination Repetition</h4>
$$nC_{k}=\begin{pmatrix}n+k-1\\k\end{pmatrix}=\frac{(n+k-1)!}{k!(n+k-1-k)!}=\frac{(n+k-1)!}{k!(n-1)!}$$
E.g.
How many ways can choose 4 candies from jar containing 3 types of candies (choc, gummy, mint). Can choose multiple candies of same type
- $\begin{pmatrix}3+4-1\\4\end{pmatrix}=\begin{pmatrix}6\\4\end{pmatrix}=15$
<h4>Permutations Indistinguishable Objects</h4>
$$nP_{k}=\frac{n!}{p_{1}!\cdot p_{2}!\cdot\dots \cdot p_{k}!}$$
E.g.
How many distinct ways can letters of word 'Balloon' be arranged
1. Count total number of letters
	- L - 2
	- O - 2
	- B, A, N = 1
2. Formula
	- n = total number of letters = 7
	- $p_{i}$ = counts of each repeated letter
	- $$\frac{7!}{1!\cdot 1!\cdot 1!\cdot 2! \cdot 2!}=\frac{7!}{2!\cdot 2!}$$
---
 