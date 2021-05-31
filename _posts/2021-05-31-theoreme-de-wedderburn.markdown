---
layout: post
title:  "Théorème de Wedderburn"
date:   2021-05-31 18:00:00 +0200
categories: articles
usemathjax: true
comments: true
tags: algebre corps-fini theoreme preuve
---

Il est coutume en France de considérer tout corps comme étant commutatif. Dans le cas contraire on parle alors de corps gauche, le plus connu étant le corps $$\mathbf{H} des quaternions.

Dans le cas où un corps est fini, aucune confusion n'est possible : à peine 70 ans après l'introduction de la théorie par Galois, Joseph Wedderburn publie en 1905 un article dans lequel il démontre (même trois fois !) que tout corps fini est commutatif. C'est-à-dire qu'il n'existe pas de corps gauche fini.

Bien que l'on ait appris après que la preuve de Wedderburn était fausse, ou au moins incomplète, ce résultat a été démontré d'une façon très élégante par Ernst Witt en 1931. Celle-çi utilise des notions en fait assez simples que sont l'étude du *centre* d'un corps, la *formule des classes* - résultat fondamental en théorie des groupes - et les *polynômes cyclotomiques*.

La beauté de cette preuve lui a valu d'être publiée dans le livre des *Raisonnements divins* (*Proofs from the Book*), et c'est celle-çi que j'aimerai présenter aujourd'hui.

Racines de l'unité et polynômes cyclotomiques
--

Rappellons que l'ensemble des *racines primitives de l'unité* est donné par
\\[ \Delta_n = \\{ e^{2i \pi k / n} ~|~ 0 \leqslant k \leqslant n-1, ~ \mathrm{pgcd}(k,n) = 1 \\} \\]

Cette notion de base de l'analyse complexe est fortement liée à l'arithmétique (a extensio à l'étude des anneaux et des corps finis), plus particulièrement à la fonction *indicatrice d'Euler* par la relation $$ \varphi(n) = | \Delta_n | $$.

On définit alors le *polynôme cyclotomique d'ordre $$n$$* comme étant le polynôme de $$\mathbf{C}[X]$$ dont les racines sont exactement les éléments de $$\Delta_n$$. En particulier, il est de degré $$\varphi(n)$$.

\\[ \phi_n (X) = \prod_{z \in \Delta_n} (X-z) \\]

Notons qu'étant définit par rapport aux racines primitives de l'unité, on obtient directement la factorisation suivante

\\[ X^n - 1 = \prod_{z \in \mathbf{U_n}} (X-z) = \prod_{d \mid n} \prod_{z \in \Delta_d} (X-z) =  \prod_{d \mid n} \phi_d(X)\\]

Fait remarquable supplémentaire, bien que $$\phi_n$$ soit *a priori* à coefficients complexes, on peut montrer qu'il est *a fortiori* à valeurs entières ! En effet, par récurrence, il suffit de remarquer que $$\phi_1(X) =  X-1$$, puis utiliser la factorisation précédente pour montrer que si $$\phi_n$$ est à coefficients dans $$\mathbf{Z}$$, alors $$\phi_{n+1}$$ aussi.

Ces deux remarques servent en fait à montrer un résultat plus puissant, qui sera ensuite un point clef de notre démonstration.

Soient $$1 \leqslant m \leqslant n$$ deux entiers. On définit la fraction rationnelle

\\[ T(X) = \frac{X^n - 1}{X^m -1} \\]

Alors dans ce cas,

* Si $$m$$ divise $$n$$, alors $$T$$ est à coefficients entiers.
* Si de plus, $$m<n$$, alors $$T$$ est divisible par $$\phi_n$$. (dans $$\mathbf{Z}[X] !)

Pour le voir, il faut d'abord noter que si $$m$$ divise $$n$$, alors les diviseurs de $$n$$ sont le résultat de l'union des diviseurs de $$m$$ et des diviseurs de  $$n$$ qui ne divisent pas $$n$$.

Notons alors $$Q$$ l'ensemble des diviseurs de $$n$$ ne divisant pas $$m$$, on obtient alors, par union disjointe,

\\[ X^n - 1 = (X^m - 1) \cdot \prod_{q \in Q} \phi_q(X) \\]

C'est-à-dire que $$T(X) = \prod_{q \in Q} \phi_q(X)$$, qui est donc un polynôme de $$\mathbf{Z}[X]$$ par la remarque précédente.

Si maintenant on suppose que $$m<n$$
