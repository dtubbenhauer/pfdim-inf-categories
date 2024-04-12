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

# The Magma code

Empty so far.

# The Mathematica code

Empty so far.

# Erratum

Empty so far.
