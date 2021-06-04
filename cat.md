---
layout: post
---



Voyant ce concept intervenir de près ou de loin dans à peu près toutes les discussions de mathématiciens - algébristes - auxquelles j'ai pu assister, j'ai profité de ce début de vacances pour enfin l'étudier d'un peu plus près : la théorie des catégories.

Ce billet sera l'occasion pour moi de mettre à plat ces nouvelles idées, et de faire découvrir ce nouveau monde à d'autres néophytes.

Le plan sera calqué sur le premier chapitre du merveilleux livre de M. Kashiwara et P. Schapira [1]. Il est donc fortement probable que cet article soit très long, mais le but ici n'est pas tant de vulgariser que de présenter le vocabulaire de base que tout aspirant catégoricien serait mené à connaître. J'espère néanmoins réussir à reformuler les concepts de façon claire et si possible, donner envie de continuer l'étude par soi-même.

L'étude des catégories ne demande *a priori* aucun prérequis. Ou plutôt, elle en demande autant que de lire un Bourbaki; dans le sens où un lycéen a les connaissances nécessaires pour comprendre les définitions basiques, mais que sans un solide passif en mathématiques, l'étude - en plus d'avoir un intérêt limité - est extrêmement ardue.

Motivation
==

La notion de catégorie est née de l'algèbre, ou plutôt de l'esprit de deux algébristes, Samuel Eilenberg et Saunders MacLane dans les années 1940, puis développé par Grothendieck dans les années 1960 dans son célèbre *Séminaire de Géométrie Algébrique*. Le but est double, d'un côté, on construit un outil important dans le développement des mathématiques et de l'autre, on a là une théorie qui peut prétendre à être un *fondement des mathématiques*.
 Pour les adeptes de l'axiome de Zermelo-Fraenkel, il faut se préparer à un saut conceptuel conséquent. La théorie des ensembles repose sur un formalisme logicien, on part d'un nombre d'axiomes restreint, et on construit tout ce château de carte qu'est les mathématiques à partir de ceux-ci. La base de ce château, ce sont les ensembles. Mais un ensemble, n'en déplaise aux logiciens, ce n'est qu'un gros sac d'objets sans rapport entre-eux, et ça, pour un mathématicien, c'est un comble!


Ce qui donne un sens à ces ensembles, c'est la *structure* qu'on leur donne. Une structure, c'est ce qui permet de manipuler, de relier les objets d'un ensemble entre-eux. Qu'importe qu'un groupe contienne tel ou tel élément, ce qui est fondamental, c'est de savoir comment ils agissent, comment ils se comportent entre-eux. C'est justement le but des catégories : on fait fi des éléments de ces structures, le but est d'établir leurs relations.

NB: Derrière ce paragraphe très caricatural se cache une vraie réflexion sur les différentes conceptions de ce que peut être les fondements mathématiques, mais ne dissertant ni sur l'histoire ou la philosophie, je conseille la lecture du très bon article de Jean-Yves Béziau [2]

En mathématiques, il y a une façon très commode de conceptualiser les relations entre deux objets : les morphismes, et plus particulièrement les isomorphismes. Un morphisme, c'est une application d'une de $$A$$ vers $$B$$ qui conserve la structure de $$A$$ et $$B$$. Quiconque a déjà étudié l'algèbre sait qu'il est souvent plus important de déterminer des morphismes de groupe que d'établir leur table de multiplication; la topologie qu'on préfère savoir si deux espaces sont homéomorphes que ce à quoi ils ressemblent, etc.

Nous allons donc découuvrir ce qu'est formellemment une catégorie, comment ses objets sont reliés entre eux et même comment les catégories sont liées entre-elles.

Univers
==

Partir de la seule théorie des ensembles pour définir une notion unificatrice des structures pose rapidement problème. La première catégorie qu'on voudrait définir serait celle des ensembles. Mais il est bien connu depuis Russell que se confonter à l'ensemble de tous les ensembles est peine perdue. C'est pourquoi nous allons plutôt nous baser sur la notion d'univers, plus spécifiquement d'univers de Grothendieck. L'idée principale est de pouvoir travailler sur un ensemble suffisament gros pour contenir tout ce qu'on attend de lui, sans rencontrer ce genre de paradoxe.

**Définition** : Un univers $$\mathcal{U}$$ est un ensemble tel que:
* \\(\varnothing \in \mathcal{U}\\)
* Si $$u \in \mathcal{U}$$ et $$t \in u$$, alors $$t \in \mathcal{U}$$
* Si $$I \in \mathcal{U}$$, et $$(u_i) \in \mathcal{U}$$ pour tout $$i \in I$$, alors $$\bigcup_{i \in I} U_i \in \mathcal{U} $$

On déduit sans peine de cette définition la stabilité par inclusion, produit, etc.

Il faut néanmoins faire attention à une chose : ainsi défini, un univers ne peut être défini que par un enchevêtrement de symboles du type $$\varnothing, \{ \varnothing \}, \{ \{ \varnothing \}, \varnothing \}$$. Pour résoudre ce problème, Grothendieck a proposé de rajouter un axiome à la théorie ZFC:

\\[ \text{Pour tout ensemble } x \text{ il existe un univers } \mathcal{U} \text{ tel que } x \in \mathcal{U} \\]

Cela permet notamment aux univers de contenir un ensemble de cardinal infini.

*Certains auteurs rajoutent à la définition que $$\mathbf{N} \in \mathcal{U}$$, ou remplacent l'hypothèse que $$\varnothing \in \mathcal{U}$$ par celle-ci. En considérant l'axiome de Grothendieck, ça peut sembler redondant...après discussion avec des camarades et quelques recherches, il semblerait finalement qu'on rajoute cette hypothèse par confort plus que par rigueur logique. Je n'entrerai pas ici dans des les détails concernant l'axiome de l'infini, mais j'ai personnellement trouvé une réponse intéressante [ici](https://ncatlab.org/nlab/show/Grothendieck+universe#axiom_of_universes) et dans l'annexe de Bourbaki [3].*  




Références
--
[1] cat and sheaves
[2] article jean yves beziau
[3] sga 4.1
