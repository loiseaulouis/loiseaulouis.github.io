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

Les corps sont une des trois grandes structures de base de l'algèbre, avec les groupes et les anneaux. C'est aussi la plus petite et la plus complexe, car un corps vérifie les axiomes d'un anneau (et donc d'un groupe). Cela se traduit par le fait qu'on peut définir une *addition* et une *multiplication*, auxquelles on rajoute une hypothèse plus forte: tout élément est inversible pour la multiplication. Intuitivement, on rajoute la capacité de *diviser* les éléments. En effet, si tout élément \\(a\\) admet un inverse \\(a^{-1}\\), on peut toujours multiplier par \\(a^{-1}\\), et en "choisissant" la notation \\(\frac{1}{a}\\), on voit bien cet aspect.
