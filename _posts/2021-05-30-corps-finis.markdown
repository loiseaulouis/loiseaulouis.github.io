---
layout: post
title:  "Introduction à la théorie des corps finis"
date:   2021-05-30 00:00:35 +0200
categories: articles
usemathjax: true
---

J'avais depuis quelques temps en tête l'idée de parler "du" polynôme cyclotomique, qui fait le lien entre les racines de l'unité (c'est-à-dire les \\(n\\) solutions \\(\omega\\) de \\(\omega^n = 1\\)), une notion présentée en général en première année d'études supérieures; et les corps finis, plutôt abordés au bout de 3 à 4 ans.

Mais, encore indécis quant à l'orientation de mes articles, je préfère d'abord (re)présenter les corps finis. Je ne rappellerai pas les notions de groupes et anneaux car, même si elles sont fondamentales, elles n'auraient pas d'intérêt ici si ce n'est alourdir le contenu.

Qu'est-ce qu'un corps ?
==

Les corps sont une des trois grandes structures de base de l'algèbre, avec les groupes et les anneaux. C'est aussi la plus petite et la plus complexe, car un corps vérifie les axiomes d'un anneau (et donc d'un groupe). Cela se traduit par le fait qu'on peut définir une *addition* et une *multiplication*, auxquelles on rajoute une hypothèse plus forte: tout élément est inversible pour la multiplication. Intuitivement, on rajoute la capacité de *diviser* les éléments. En effet, si tout élément \\(a\\) admet un inverse \\(a^{-1}\\), on peut toujours multiplier par \\(a^{-1}\\), et en "choisissant" la notation \\(\frac{1}{a}\\), on peut bien diviser par \\(a\\).

Nous connaissons déjà assez bien trois (souvent quatre!) exemples de corps commutatif, il s'agit de ceux des nombres rationnels, réels et complexes, \\( \mathbf{Q}, \mathbf{R}, \mathbf{C} \\) ou le corps des entiers modulo un premier, \\(\mathbf{Z}/p \mathbf{Z} \\).

Historiquement, cette notion s'est imposée assez naturellement, l'algèbre, de l'Antiquité à la fin du XIXème siècle, était consacrée à l'étude et la résolution des équations polynomiales, et avec le développement des structures algébriques par Galois, des travaux sur une nouvelle structure permettant d'étudier beaucoup plus simplement ces polynômes sont devenus presque essentiels.

Du point de vue de l'étudiant, il est pourtant très compliqué de voir le lien entre cette structure et l'étude des polynômes. Typiquement, quand on cherche à savoir si un polynôme est irréductible, une façon de faire peut être d'étudier sa *réduction modulo un nombre premier \\(p\\)*. Pour se faire, en plus de savoir manipuler les résultats sur les corps, l'étudiant doit au préalable avoir des notions d'arithmétique (et donc de théorie des anneaux), mais aussi être familier des morphismes de réduction et donc de la *propriété universelle*, qu'on rencontre pour la première fois en étudiant les groupes.

Le but ici n'est pas de faire un cours exhaustif de troisième année de licence, aussi je vais présenter les outils généraux
