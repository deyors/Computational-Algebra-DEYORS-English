# Computational-Algebra-TheYorsh (English)
Below are exposed several algorithms of Computational Algebra related with
factorization, primality, logarithms and other properties of polynomial and
elements of finite fields, all of it programed in Maple.
This algorithms corresponds with the Computational Algebra subject
imparted in the fourth year of the Degree of Mathematics in the Complutense 
University of Madrid.

Bibliography:

- Modern Computer Algebra (Joachim von zur Gathen)
- A Computational Introduction to Number Theory and Algebra (Victor Shoup)

The algorithms are in .txt to see the codes. To apply them you need to open
an .mw file with Maple and add them line by line. Most of the algorithms 
need other algorithms to be executed, so be sure to execute them in order.

This repository was created with the desire of extending the knowledge of the 
Computational Algebra and the techniques that you can do to reach the results
of the books. The literal copy of the codes to approve a subject related 
with this programs is discouraged.

This material is 100% free, buy you can help me to upload more programs 
with the donation of any amount that you see convenient to my Pay-Pal: 
paypal.me/theyorsh

If you want to download the codes, is advised to open it with Notepad++
to see the separation between lines, and then write the codes in Maple. 

In order to execute the codes without problems, all of the examples 
and the auxiliary functions must be in different environment executions. 
For example, this execution is not correct:

*"> FiniteInverse:=proc(K,e)*

   *local inverse, oc, r, s, t, K1, K2;*
   
   *oc:=K[Size];*
   
   *#the function ends..*
   
   *p := 13;*
   
   *Zp := Zmod(p);*
   
   *FiniteInverse(Zp, 5);* #THIS HAS TO BE OUT OF THE MAIN EXECUTION
   
   *#The instruction above is the example*
   

Nevertheless, this is correct:

*"> FiniteInverse:=proc(K,e)*

   *local inverse, oc, r, s, t, K1, K2;*
   
   *oc:=K[Size];*
   
   *#the function ends..*
   
   *#the main execution ends and I create another environment execution:*

*"> p := 13;*

   *Zp := Zmod(p);*
   
   *InversoFinito(Zp, 5);*
   
   *#The instruction above is the example*
   
The algorithms are listed below:

**1. Euclidean Algorithm for Euclidean Domains.**

Given an Euclidean Domain and two elements, executes the Euclidean Algorithm
and returns the g.c.d. of these elements.

**2. Extended Euclidean Algorithm.**

Given K an Euclidean Domain and two elements a,b of K, executes the 
Euclidean Algorithm listed above and returns the g.c.d (let's say "d") of these 
elements. Then, finds using the Bézout's identity, the two elements x e y that
verify:

a*x + b*y = d

**3. Chinese Remainder Algorithm.**

Let R be an Euclidean Algorithm.
Let m[0], m[1], ... ,m[r-1] of R be coprime.
Let v[0], v[1], ... , v[r-1] of R.
Let m = m[0]*m[1]*...*m[r-1].

Then we've got m = lcm(m[0],m[1],... m[r-1])

The Chinese Remainder theorem says that exists an element f od R such that:

f ≡v[i] mod m[i], para 0 <= i < r

The following algorithm takes the m[i] and v[i] elements and returns the 
mentioned f element, using the demonstration of the theorem listed before.


**4. G.C.D. in a U.F.D.**

Let K be an Unique Factorization Domain (U.F.D.).
Let f,g be two elements of K.

The following algorithm returns the Greatest Common Divisor of f and g (normalized)


**5. Inverse of an element in a Finite Field.**

Let K be a finite field.
Let e be an element of K

The following algorithm returns the inverse of "e" in K.


**6. Irreducibility test for a polynomial in Fq[x]**

Let f be a polynomial in a field with dimension q^k. The algorithm returns
"Reducible" if the polynomial is reducible in K, and "Irreducible" if not.

**7. Discrete logarithm in fields Fq[x] quotiented with f(x):**

Given a polynomial f in a field with dimension "q" prime and two numbers a,b,
the algorithm calculate log_b(a).

**8. Factorization algorithms for a polynomial in a finite field (SFD, DDF, EDF):**

Showing up next there are three different algorithms that factorizes a polynomial 
in different ways. The structure of the file is:

- 0. Auxiliary functions:

Let F be a field with |F| = q = p^w, w != 1, the function PolynomialToFx transforms
a polynomial f with alpha, x variables to a polynomial with coefficients in F.

To build F, it's posible for q to be not prime, so we need to apply the action
of a polynomial "pol" irreducible with degree w to express F as Zp/(pol).

In the case w=1 you'll have to enter pol=1 (it's not neccesary the action of 
a polynomial becouse F can be represented as Zp). 

The second auxiliary function calculates the G.C.D. in a finite field of two 
primitive polynomials with coefficients in F, where F,p and pol are described 
before.

- 1. SFD (Square-free descomposition)

Let F be a field with |F| = q = p^w and "pol" be an irreducible polynomial with
degree w with which we can express F as Zp/(pol), this algorithm returns a list
of pairs [(g[i], s[i])], where f is the multiplication of (g[i])^(s[i]), and 
every g[i] is monic and square-free.


- 2. DDF (Distinct Degree Factorization)

Let F be a field with |F| = q = p^w and "pol" be an irreducible polynomial with
degree w with which we can express F as Zp/(pol), this algorithm returns a list
of pairs [(g[i]),k[i])], where f is the multiplication of g[i], and every g[i]
can be factorized in irreducible polynomials of degree k[i].

- 3. EDF (Equal Degree Factorization)

Let F be a field with |F| = q = p^w and "pol" be an irreducible polynomial with
degree w with which we can express F as Zp/(pol), this algorithm returns a list 
with the irreducible factors of a polynomial f if we know that f can be 
factorized in k irreducible polynomials.

**9. Berlekamp's algorithm in a finite field:**

The structure of the algorithm is based in:

- 0. Auxiliary functions: 

Let Q be a matrix. The function insertRow inserts to a vector "r" the first n-elements
of a row "i".

Let f be a polynomial and p be the cardinal of Zp with which we want to express f 
apllying this algorithm, the function matrixQ provides the Berkelamp matrix of 
that polynomial. 

Let "a" be a number. The function inverseModulus returns its inverse modulus "b".

Let M be a matrix of dimension n, the function permuteRow swap the row i with the row j.

Let M be a matrix of dimension n and p the cardinal of Zp, the function berlekampVectors
returns the Berlekamp vectors v(1), ... , v(n).


- 1. Final algorithm:

Let f be a square-free polynomial and p the cardinal of Zp, this algorithm completely 
factorizes f in factors contained in Zp[x].

**10. Factorization algorithm in Z[x] (Hensel):**

Let f be a polynomial, p the cardinal of Zp and g,h two polynomial that fulfill the conditions
of Hensel's propositions, the algorithm returns a factorization of f.

**11. AKS primality test:**

Given an integer number, the algorithm gives the information about the irreducibility of that
number using the AKS technique.
