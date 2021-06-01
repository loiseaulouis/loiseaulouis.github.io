---
layout: post
title:  "Théorème de Wedderburn"
date:   2021-05-31 18:00:00 +0200
categories: articles
usemathjax: true
comments: true
tags: algebre corps-fini theoreme preuve
---

Il est coutume en France de considérer tout corps comme étant commutatif. Dans le cas contraire on parle alors de corps gauche, le plus connu étant le corps $$\mathbf{H}$$ des quaternions.

Dans le cas où un corps est fini, aucune confusion n'est possible : à peine 70 ans après l'introduction de la théorie par Galois, Joseph Wedderburn publie en 1905 un article dans lequel il démontre (même trois fois !) que tout corps fini est commutatif. C'est-à-dire qu'il n'existe pas de corps gauche fini.

Bien que l'on ait appris après que la preuve de Wedderburn était fausse, ou au moins incomplète, ce résultat a été démontré d'une façon très élégante par Ernst Witt en 1931. Celle-çi utilise des notions en fait assez simples que sont l'étude du *centre* d'un corps, la *formule des classes* - résultat fondamental en théorie des groupes - et les *polynômes cyclotomiques*.

La beauté de cette preuve lui a valu d'être publiée dans le livre des *Raisonnements divins* (*Proofs from the Book*), et c'est celle-ci que j'aimerai présenter aujourd'hui.

Racines de l'unité et polynômes cyclotomiques.
==

Rappellons que l'ensemble des *racines primitives de l'unité* est donné par
\\[ \Delta_n = \\{ e^{2i \pi k / n} ~|~ 0 \leqslant k \leqslant n-1, ~ \mathrm{pgcd}(k,n) = 1 \\} \\]

Cette notion de base de l'analyse complexe est fortement liée à l'arithmétique (a extensio à l'étude des anneaux et des corps finis), plus particulièrement à la fonction *indicatrice d'Euler* par la relation $$ \varphi(n) = \mid \Delta_n \mid $$.

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
* Si de plus, $$m<n$$, alors $$T$$ est divisible par $$\phi_n$$. (dans $$\mathbf{Z}[X]$$ !)

Pour le voir, il faut d'abord noter que si $$m$$ divise $$n$$, alors les diviseurs de $$n$$ sont le résultat de l'union des diviseurs de $$m$$ et des diviseurs de  $$n$$ qui ne divisent pas $$n$$.

Notons alors $$Q$$ l'ensemble des diviseurs de $$n$$ ne divisant pas $$m$$, on obtient alors, par union disjointe,

\\[ X^n - 1 = (X^m - 1) \cdot \prod_{q \in Q} \phi_q(X) \\]

C'est-à-dire que $$T(X) = \prod_{q \in Q} \phi_q(X)$$, qui est donc un polynôme de $$\mathbf{Z}[X]$$ par la remarque précédente.

Si maintenant on suppose que $$m<n$$, alors $$n \in Q$$, et donc $$T(X) = \phi_n \cdot \prod_{q \in Q \setminus \\{n\\} } \phi_q(X) $$, ce qui est le résultat voulu.

Démonstration du théorème.
==

Entrons enfin dans le vif du sujet. Au programme comme promis: extensions de corps, actions de groupes et polynômes cyclotomiques. On pourra notamment se référer au *Cours d'Algèbre* de Perrin, ou aux *Raisonnements Divins* de Aigner et Ziegler.

Soit $$K$$ un corps fini. On notera $$Z$$ son centre (ie: l'ensemble des éléments de $$K$$ qui commutent avec tous les autres). C'est en particulier un sous-corps de $$K$$, et si on note son cardinal $$q$$, alors par propriétés des corps finis, le cardinal de $$K$$ s'écrit $$q^n$$.

Raisonnons par l'absurde en supposant que $$K$$ n'est pas commutatif. Par définition du centre, on a forcément $$K \neq Z$$, et donc $$n>1$$. On considère l'extension de $$Z$$ suivante:

\\[ Z_x = \\{ a \in K ~\mid~ ax = xa \\} \\]

On a donc défini une tour d'extension $$ Z \subset Z_x \subset K$$. Il existe alors deux entiers $$m(x)$$ et $$n(x)$$ de sorte que

\\[ q^n = \mid Z_x \mid^{m(x)} = q^{d(x) m(x)}\\]

D'où $$n = d(x) m(x)$$. En particlier, $$d(x)$$ divise $$n$$ pour tout $$x \in K$$.

On va maintenant considérer l'action de $$K^\times$$ (le groupe multiplicatif) sur lui-même par *conjuguaison*. Cette action possède des orbites $$\omega_x$$ et un stabilisateur $$\mathrm{Stab}(x)$$. On a

\\[ Z_y = \mathrm{Stab}(x) \cup \\{0\\} \\]

De là, on tire que $$\mid \mathrm{Stab}(x) \mid = \mid Z_y \mid - 1 = q^{d(y)} - 1$$.

On a de plus

\\[ \mid \omega_x \mid = 1 \iff \omega_x = \\{x\\} \iff \mathrm{Stab}(x) = K^\times \iff x \in Z^\times \\]

Soient $$(z_i)_{0\leqslant i \leqslant q-1}$$ les éléments de $$Z$$. On a $$z_0 = 0$$. Ces éléments ont une orbite réduite à un point.
 Celles qui s'intersectent avec $$Z^\times$$ sont $$ \omega_{z_1}, \cdots, \omega_{z_{q-1}} $$. On note $$\omega_{y_1}, \cdots, \omega_{y_r}$$ les autres.

 C'est ici qu'intervient la formule des classes, induite par l'action. Elle nous donne:

 \\[ \mid K^\times \mid = \mid Z^\times \mid + \sum_{i=1}^r \frac{\mid K^\times \mid}{\mid \mathrm{Stab}(y_i) \mid} \\]

Ce qui s'écrit, d'après les considérations précédentes,

\\[ q^n - 1 = (q-1) + \sum_{i=1}^r \frac{q^n - 1}{q^{d(y_i)} - 1} \\]

Il est alors (plus ou moins) naturel de considérer la fraction rationnelle

\\[ F(X) = (X^n - 1) -  \sum_{i=1}^r \frac{X^n - 1}{X^{d(y_i) - 1}} \\]

Qui est en fait un polynôme de $$\mathbf{Z}[X]$$ car car $$d(y_i) \mid n$$. On peut même aller plus loin, et constater que  $$ d(y_i) < n $$, et par conséquent $$ \frac{X^n-1}{X^{d(y_i)} - 1} $$ est divisible par $$\phi_n(X)$$. (toujours dans $$\mathbf{Z}! $$). Comme il divise de plus $$X^n - 1$$, il divise $$F$$. On peut donc l'écrire $$F = Q \phi$$ pour un certain polynôme $$Q$$. Évalué en $$q$$, on doit avoir:

\\[   F(q) = Q(p)\phi_n(Q) = q-1  \\]

Si $$q=1$$, c'est fini. Sinon, on a $$\mid Q(q) \mid \geqslant 1$$, et donc (et c'est le point le plus important)

\\[ \mid \phi_n(q) \mid = \prod_{z \in \Delta_n} \mid q-z \mid  \leqslant q-1 \\]

Un argument géométrique va maintenant nous permettre de conclure.

S'il existe $$z_0 \in \Delta_n$$ tel que $$\mid z_0 - q \mid \leqslant q-1$$, alors $$z_0 \neq 1$$ (car $$n \geqslant 2$$ par les premières considérations sur le centre). Mais $$\mid q-z_0 \mid > q-1$$, donc $$\mid \phi_n(q) \mid > q-1$$, ce qui est absurde.

On a ainsi démontré que tout corps fini est commutatif.
