# Code and Erratum for *Asymptotics in infinite monoidal categories*

I collected a bit of Magma and Mathematica code relevant for the paper *Asymptotics in infinite monoidal categories*
<a href="https://arxiv.org/abs/2404.09513">https://arxiv.org/abs/2404.09513</a> on this page.

The code is in a **.odt** file or **.n** file, respectively, that can be downloaded from this site and you can run it with Magma or Mathematica.

An Erratum for the paper *Asymptotics in infinite monoidal categories* can be found at the bottom of the page.

There is also the predecessor of the paper on this page: *Asymptotics in finite monoidal categories*
<a href="https://arxiv.org/abs/2307.03044">https://arxiv.org/abs/2307.03044</a> with relevant 
github page <a href="https://github.com/dtubbenhauer/growth-pfdim">https://github.com/dtubbenhauer/growth-pfdim</a>.

# Contact

If you find any errors in the paper *Asymptotics in infinite monoidal categories* **please email me**:

[dtubbenhauer@gmail.com](mailto:dtubbenhauer@gmail.com?subject=[GitHub]%web-reps)

Same goes for any errors related to this page.


# Background

Let us state the results less general than in the paper itself: everything works for so-called based algebras, but we stay with monoidal categories for simplicity.

Let $\mathbf{C}$ be an
additive Krull--Schmidt monoidal category.
Let $\mathtt{X}\in\mathbf{C}$ be an object of $\mathbf{C}$.
We define
$$b_{n}:=\text{number of indecomposable summands in }\mathtt{X}^{\otimes n}\text{ counted with multiplicities}.$$
Let $b\colon\mathbb{N}\to\mathbb{N},b(n)=b_{n}$ denote the associated function.

**Questions**

- What is the **dominating growth** of $b_{n}$?

- Can we get an **asymptotic formula** $a\colon\mathbb{N}\to\mathbb{N}$ expressing $b$, e.g.
$$a(n)\sim b(n),$$
where $a$ is ``nice'', $\sim$ denotes asymptotically equal?

- Say we have found $a$ as in the previous point. Can we bound the **variance** or **mean absolute difference** $|b_{n}-a_{n}|$, or alternatively the convergence 
rate of $\lim_{n\to\infty}b(n)/a(n)=1$?

> In the paper *Asymptotics in infinite monoidal categories* we address these questions for certain categories. The most important examples included in our discussion are all finite (having finitely many simple objects) tensor categories.

**The finite case**

Assume that $\mathbf{C}$ has finitely many indecomposable objects up to isomorphism.
Assume further (only for the sake of this page - the note does not need that assumption) that the **Perron&ndash;Frobenius theorem** holds, that is
the action matrix of $\mathtt{X}$ has a leading eigenvalue $\lambda_{0}=\mathrm{PFdim}\mathtt{X}$ of multiplicity one that we call 
the **Perron&ndash;Frobenius dimension** of $\mathtt{X}$. 
Moreover, the action matrix 
has some period $h\in\mathbb{N}$ such that there are precisely $h-1$ other eigenvalues 
$\lambda_{i}=\zeta^{i}\mathrm{PFdim}\mathtt{X}$, and all of these are of multiplicity one, where 
$\zeta=\exp(2\pi i/h)$.

Take the left and right eigenvectors $v_{i}$ and $w_{i}$, normalized such that the transpose of $w_i$ times $v_i$ is one.

Let $v_{i}w_{i}^{T}[1]$ denote taking the sum of the first column of the matrix 
$v_{i}w_{i}^{T}$. Define

$$a(n)=\big(v_{0}w_{0}^{T}[1]\cdot 1+v_{1}w_{1}^{T}[1]\cdot\zeta^{n}+v_{2}w_{2}^{T}[1]\cdot(\zeta^{2})^{n}+\dots+v_{h-1}w_{h-1}^{T}[1]\cdot(\zeta^{h-1})^{n}\big)
\cdot(\mathrm{PFdim}\mathtt{X})^{n}.$$

Let $\lambda^{sec}$ be the second largest eigenvalue of the action matrix of $\mathtt{X}$.

>We have
$$b(n)\sim a(n)$$
>and the convergence is geometric with ratio $|\lambda^{sec}/\mathrm{PFdim}\mathtt{X}|$ and th varience is $|b_n-a_n|\leq(\lambda^{sec})^n$.

**Example answer in the infinite case**

For a certain type of categories that we call **sustainably positively recurrent** (these categories include all representation, for arbitary gorund field, categories of finite groups) we, roughly speaking,  obtain:

> All questions above can be answered using limits of finite cutoffs where the finite case above applies.

# Computer talk disclaimer

The code we present below is very similar to the one on 
<a href="https://github.com/dtubbenhauer/growth-pfdim">https://github.com/dtubbenhauer/growth-pfdim</a>
so we will be brief.

# The Magma code

The code can, for example, be run in the online calculator of Magma:

<a href="https://magma.maths.usyd.edu.au/calc/">Magma online</a>

The code we collected is about $G=\mathrm{PSL}(2,7)$ and representations in characteristic $2$ and can be adjusted to 
other groups easily. In this case there are two three dimensional simple
representations, and let $\mathtt{X}$ be any of these two. We want to compute the first numbers $b(n)$ -- **the numbers we what to approximate** -- 
and display its fusion graph.

The code in full is:

```
G:=PSL(2,7);
Irr:=IrreducibleModules(G,GF(2));
M:=Irr[2];
X:=[Irr[1],Irr[2]];
nn:=0;
max:=10;

while nn lt #X and nn lt max do
nn+:=1;
M2:=TensorProduct(X[nn],M);
XM2:=IndecomposableSummands(M2);
for j in [1..#XM2] do
new:=1;
for i in [1..#X] do
if(IsIsomorphic(XM2[j],X[i])) then
new:=0;
end if;
end for;
if(new eq 1) then X:=Append(X,XM2[j]); 
end if;
end for;
end while;

fus:=[[0 : i in [1..#X]] : j in [1..#X]];

for i in [1..#X] do
for j in [1..#X] do
Z:=IndecomposableSummands(TensorProduct(X[i],M));
z:=0;
for k in [1..#Z] do
if(IsIsomorphic(X[j],Z[k])) then z:=z+1; end if;
end for;
fus[j][i]:=z;
end for;
end for;

fus
```

Let us go through the code.

```
G:=PSL(2,7); //The group
Irr:=IrreducibleModules(G,GF(2)); //Simple modules over the field with two elements
M:=Irr[2]; //We take the second, which is of dimension three
X:=[Irr[1],Irr[2]]; //Starting set (will be filled with all indecomposables that appear in X^(otimes n) below)
nn:=0; //Start value
max:=10; //Maximal value (the problem is infinite so we cut it after the 10th step)
```

This is the basic setup as described above.

```
while nn lt #X and nn lt max do
nn+:=1;
M2:=TensorProduct(X[nn],M); //Take the tensor product
XM2:=IndecomposableSummands(M2); //Get its summands
for j in [1..#XM2] do
new:=1;
for i in [1..#X] do
if(IsIsomorphic(XM2[j],X[i])) then //Get rid of isomorphic copies to keep the calculation short
new:=0;
end if;
end for;
if(new eq 1) then X:=Append(X,XM2[j]); //Append new copies
end if;
end for;
end while; //Repeat ;-)
```

This part of the code computes the indecomposable summands in X^(otimes n) up to isomorphism. For example, the above returns:

```
X;
```
```
[
    GModule of dimension 1 over GF(2),
    GModule M of dimension 3 over GF(2),
    GModule of dimension 9 over GF(2),
    GModule of dimension 8 over GF(2),
    GModule of dimension 11 over GF(2),
    GModule of dimension 16 over GF(2),
    GModule of dimension 17 over GF(2),
    GModule of dimension 16 over GF(2),
    GModule of dimension 35 over GF(2),
    GModule of dimension 8 over GF(2),
    GModule of dimension 25 over GF(2)
]
```

The final part of the code returns the fusion graph on the vertex set given by X:

```
fus:=[[0 : i in [1..#X]] : j in [1..#X]]; //Set up a zero matrix

for i in [1..#X] do
for j in [1..#X] do
Z:=IndecomposableSummands(TensorProduct(X[i],M)); //Get the summands under the action
z:=0;
for k in [1..#Z] do
if(IsIsomorphic(X[j],Z[k])) then z:=z+1; end if; //Count isomorphic summands
end for;
fus[j][i]:=z; //Set the matrix values
end for;
end for;

fus
```
```
[
    [ 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 ],
    [ 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 ],
    [ 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0 ],
    [ 0, 0, 2, 1, 2, 2, 2, 3, 6, 1, 4 ],
    [ 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0 ],
    [ 0, 0, 0, 1, 0, 0, 0, 0, 0, 1, 0 ],
    [ 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0 ],
    [ 0, 0, 0, 0, 0, 2, 0, 1, 2, 0, 0 ],
    [ 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0 ],
    [ 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0 ],
    [ 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0 ]
]
```
The appearing matrix can for example then be copied into <a href="https://graphonline.ru/en/">Graph online</a> which displays it nicely:

![Cutoff of the fusion graph](https://github.com/dtubbenhauer/pfdim-inf-categories/blob/main/graph.png)

The online calculator uses the opposite convention as in the paper. Precisely, you need to transpose the matrix to get the same 
drawing conventions for the fusion graph as in the paper. This can be done by using

```
fus[i][j]:=z; //Set the matrix values
```

instead of the above.

# The Mathematica code

The code is hopefully pretty straightforward. All that is happening is that 
the data created with the Magma code is plotted.

For example:

![The dimension 3 case](https://github.com/dtubbenhauer/pfdim-inf-categories/blob/main/psl2.png)

Let me know if there are any questions!

# Erratum

Empty so far.
