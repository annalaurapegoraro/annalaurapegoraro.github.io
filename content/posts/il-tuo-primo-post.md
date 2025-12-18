---
title: "Plateau's Problem: the Douglas–Radó Theorem"
# author: "Annalaura"
# authorAvatarPath: "/avatar.jpeg"
date: "2025-12-17"
draft: false
summary: "A brief presentation of my Bachelor's thesis."
description: false
toc: true # stands for Table Of Contents, summarizes sections and subsections
readTime: true
autonumber: true # true gives numbered sections/subsections, similarly to latex
math: true
tags: ["math"]
showTags: false
hideBackToTop: false # command to go back to the top in long pages
# fediverse: "@username@instance.url"
---
I recently earned my Bachelor's degree from the University of Padua with a thesis titled "Plateau's Problem: the Douglas--Radó Theorem". \
Here is an overview of my thesis defense, accompanied by a photo from the day:

![Discussione](/images/discussione.jpg)

If you are interested in more details and references, you can find the full thesis in the [University archive](https://thesis.unipd.it/handle/20.500.12608/102023).

## Plateau's problem

### Introduction
Plateau's problem concerns the existence of a minimal surface whose boundary is a given curve in space. Before getting into the math, I would like to introduce the intuitive concept of a minimal surface. Let's think of "soap films" obtained by dipping a wire frame into soapy water and then pulling it out. 

{{< youtube jReQUm9EB9k >}}

The film obtained in this way arranges itself such that any local deformation would increase its area, which is proportional to the "elastic energy" of the surface. In other words, it arranges itself so that the area is minimized: in this sense, we speak of a *minimal surface*.

Now, if we fix a closed curve $\Gamma$ in space, Plateau's problem consists of answering the question: **does there exist a surface of minimal area that has $\Gamma$ as its boundary?**

In the 1930s, Jesse Douglas and Tibor Radó proved, independently, that for sufficiently regular curves, such a surface always exists.

### Parametric formulation 
Let us now proceed with the parametric formulation of Plateau's problem.\
Consider the unit disk $D$ in the complex plane, and a parametrization $$\gamma:\partial D\to\mathbb{R}^n$$which is of class $C^1$, regular, and injective: it is a *Jordan curve*. Let$$\Gamma=\gamma(\partial D)$$ be its support. This is our "wire frame".

![Parametric](/images/disegno.png)

Let $F$ be such that
$$F\in C^2(D)\cap C(\overline{D}), \quad F(\partial D)=\Gamma, \quad \Sigma=F(D)$$
We say that the image of the disk $$\Sigma=F(D)$$ is a *parametric 2-surface*. This parametric surface formalizes the idea of the "soap film".\
Plateau's problem consists of minimizing the area functional

$$\mathscr{A}(F)=\int_D \sqrt{|F_u|^2|F_v|^2-\langle F_u,F_v\rangle^2} \ dudv,$$

with $F$ varying among the class of maps

$$\mathscr{C}(\Gamma)=\\{F:\partial D\to\mathbb{R}^n \text{ is a homeomorphism}\\}.$$

Having arrived at this formulation, the natural idea is to search for a minimizing sequence of functions in $\mathscr{C}(\Gamma)$ and hope that this "converges" (in some unspecified topology) to the sought-after minimal surface. The problem is that $\mathscr{C}(\Gamma)$ is not "compact" (in some unspecified topology) and the area functional $\mathscr{A}$ is invariant under any diffeomorphism of the disk.

## The Douglas–Radó theorem

### From the area functional to the Dirichlet energy
Douglas's idea was to replace the area functional with the Dirichlet energy:

$$\mathscr{E}(F)=\frac{1}{2}\int_D \left(|F_u|^2+|F_v|^2\right) \ dudv$$

In fact, the following properties hold:
* $\mathscr{A}(F)\leq\mathscr{E}(F)$ and equality holds if $F$ is weakly conformal;
* $\displaystyle \inf_{F\in\mathscr{C}(\Gamma)}\mathscr{A}(F)=\inf_{F\in\mathscr{C}(\Gamma)}\mathscr{E}(F)\quad$ (Morrey)

Plateau's problem thus becomes finding an $F$ that realizes the infimum of the energy.\
We are in a more advantageous situation than before because the Dirichlet energy is invariant only under **conformal transformations** of the disk.

### Statement of the theorem

We are now ready to state the Douglas--Radó theorem:

> **Theorem (Douglas--Radó)**
>
> $\exists F\in\mathscr{C}(\Gamma)$ that minimizes $\mathscr{A}$ such that:
> 1.  $F\in C^\infty(D)$, $\Delta F=0$ (i.e. each coordinate is harmonic);
> 2.  $F\mid_{\partial D}$ is a homeomorphism;
> 3.  $F$ is weakly conformal, with isolated singularities.

Where does Laplace's equation come from? The second fundamental step, after replacing the area functional with the Dirichlet energy, is the transition from minimal surfaces to harmonic functions. From the theory of partial differential equations, we know that the Dirichlet problem

$$
\begin{cases}
    \Delta F=0 & \text{ in } D\\\\
    F\rvert_{\partial D}=\gamma &
\end{cases}
$$

admits a unique solution $F^\gamma \in C^{\infty}(D)\cap C(\overline{D})$ and, since $\gamma$ is of class $C^1$, $\mathscr{E}(F)<\infty$ (this will be useful later).
In particular, Laplace's equation is the Euler--Lagrange equation associated to the Dirichlet energy, and Dirichlet energy is a convex functional: this means that by finding a solution to Dirichlet's problem we find a global minimizer of the energy $\mathscr{E}$.

## Proof of the theorem

### Eliminating parametrization dependence
Finally, we should notice that the solution to Dirichlet's problem $F^\gamma$ depends on the specific parametrization $\gamma$ we choose for $\Gamma$. We want to remove this dependence.
Pick a sequence of parametrizations $\gamma_j$ that is minimizing for the energy, i.e. $$\lim_{j\to\infty} \mathscr{E}(F^{\gamma_j})=\overline{\mathscr{E}}:=\inf_{F\in\mathscr{C}(\Gamma)}\mathscr{E}(F) ,$$ and **assume** that it converges uniformly to another parametrization, i.e.$$\gamma_j\underset{j\to\infty}{\rightrightarrows} \gamma .$$
Then, it can be proved that $$F^{\gamma_j}\underset{j\to\infty}{\rightrightarrows} F,$$where $F$ has harmonic coordinates and satisfies$$\mathscr{E}(F)\leq \liminf_{j\to\infty}\mathscr{E}(F^{\gamma_j})=\overline{\mathscr{E}}.$$ Hence, once we prove that the remaining properties in the theorem hold, we can conclude that $F$ gives our minimal surface and the proof is concluded.

### Three-points normalization
It now remains to show that we can actually find a minimizing sequence that converges uniformly. To do this, we first remove the conformal invariance of the energy by doing a *three-points normalization*, i.e. fixing the image of three points on the boundary of the unit disk: $$\gamma(e^{i\frac{2k\pi}{3}})=p_k,\quad k=1,2,3.$$
Why exactly three points? Because conformal transformations are Möbius maps, which are determined by the image of three points. This prevents "sliding" along the boundary via conformal transformations, which could otherwise disrupt convergence.

![Normalization](/images/disegno1.png)

### Courant–Lebesgue lemma
Secondly, we use the following lemma:

> **Lemma (Courant--Lebesgue)**
>
> Let $z\in\partial D$, $G(r,\theta)=F(z+re^{i\theta})$. Then $\forall \delta\in(0,1)$, $\exists r\in[\delta,\sqrt{\delta}]$ such that:
>
> $$\textnormal{Length}(G(r,\cdot))\leq\sqrt{\frac{4\pi\mathscr{E}(F)}{-\log(\delta)}}$$

Recalling that $\mathscr{E}(F)<\infty$ because $\gamma$ is of class $C^1$, we know that the quantity on the right is finite. This lemma states that the length of the image of a small arc is bounded. This prevents points near each other on the boundary of the domain from being "stretched" and sent to distant points on the curve $\Gamma$, guaranteeing the equicontinuity of the boundary parametrizations. Finally, by the Ascoli-Arzelà theorem we can extract a uniformly converging subsequence.

As already observed, at this point it is sufficient to prove the remaining properties to conclude the proof of the theorem.

## Conclusion

In conclusion, the Douglas-Radó Theorem was the first rigorous answer to Plateau's problem. 

The physical limits of this solution are evident: in reality, non-orientable soap films exist (e.g., Möbius Strip), whereas the solution is restricted to the disk topology. Moreover, real films may exhibit self-intersections that interact with each other, while this solution does not account for such interactions.

However, this theorem is a fundamental result that paved the way for many other formulations and for the calculus of variations.