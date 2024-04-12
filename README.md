# Code and Erratum for *Asymptotics in infinite monoidal categories*

I collected a bit of Magma and Mathematica code relevant for the paper *Asymptotics in infinite monoidal categories*
<a href="https://arxiv.org/abs/2307.03044">https://arxiv.org/abs/2307.03044</a> on this page.

The code is in a **.odt** file or **.n** file, respectively, that can be downloaded from this site and you can run it with Magma or Mathematica.

An Erratum for the paper *Asymptotics in infinite monoidal categories* can be found at the bottom of the page.

There is also the predecessor of the paper on this page: *Asymptotics in finite monoidal categories*
<a href="https://arxiv.org/abs/2307.03044">https://arxiv.org/abs/2307.03044</a> with relevant 
github page <a "https://github.com/dtubbenhauer/growth-pfdim">https://github.com/dtubbenhauer/growth-pfdim</a>.

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

# The Magma code

Empty so far.

# The Mathematica code

Empty so far.

# Erratum

Empty so far.
