---
layout: post
header-img: "img/cat.jpg"
---



Voyant ce concept intervenir de près ou de loin dans à peu près toutes les discussions de mathématiciens - algébristes - auxquelles j'ai pu assister, j'ai profité de ce début de vacances pour enfin l'étudier d'un peu plus près : la théorie des catégories.

Ce billet sera l'occasion pour moi de réorganiser mentalement ces nouvelles idées, et de faire découvrir ce nouveau monde à d'autres néophytes.

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

**Définition.** Un univers $$\mathcal{U}$$ est un ensemble tel que:
* \\(\varnothing \in \mathcal{U}\\)
* Si $$u \in \mathcal{U}$$ et $$t \in u$$, alors $$t \in \mathcal{U}$$
* Si $$I \in \mathcal{U}$$, et $$(u_i) \in \mathcal{U}$$ pour tout $$i \in I$$, alors $$\bigcup_{i \in I} U_i \in \mathcal{U} $$

On déduit sans peine de cette définition la stabilité par inclusion, produit, etc.

Il faut néanmoins faire attention à une chose : ainsi défini, un univers ne peut être défini que par un enchevêtrement de symboles du type $$\varnothing, \{ \varnothing \}, \{ \{ \varnothing \}, \varnothing \}$$. Pour résoudre ce problème, Grothendieck a proposé de rajouter un axiome à la théorie ZFC:

\\[ \text{Pour tout ensemble } x \text{ il existe un univers } \mathcal{U} \text{ tel que } x \in \mathcal{U} \\]

Cela permet notamment aux univers de contenir un ensemble de cardinal infini.

*Certains auteurs rajoutent à la définition que $$\mathbf{N} \in \mathcal{U}$$, ou remplacent l'hypothèse que $$\varnothing \in \mathcal{U}$$ par celle-ci. En considérant l'axiome de Grothendieck, ça peut sembler redondant...après discussion avec des camarades et quelques recherches, il semblerait finalement qu'on rajoute cette hypothèse par confort plus que par rigueur logique. Je n'entrerai pas ici dans des les détails concernant l'axiome de l'infini, mais j'ai personnellement trouvé une réponse intéressante [ici](https://ncatlab.org/nlab/show/Grothendieck+universe#axiom_of_universes) et dans l'annexe de Bourbaki [3].*  

Pour la suite, si $$\mathcal{U}$$ est univers, on dira qu'un ensemble est un $$\mathcal{U}$$-ensemble s'il appartient à $$\mathcal{U}$$, ou bien qu'il est $$\mathcal{U}$$-petit s'il est isomorphe à un ensemble appartenant à $$\mathcal{U}$$.

Bien, maintenant posé ce petit cadre, il est temps d'enfin entrer dans le sujet.

Catégories, foncteurs
==

Comme présenté dans l'introduction, une catégorie est essentiellement la donné d'un ensemble, et de la structure qu'on souhaite lui donner, caractérisée par ses morphismes. Formellement, on a donc:

**Définition.** - Une catégorie $$\mathcal{C}$$ est la donnée de
* Un ensemble $$\mathrm{Ob}(\mathcal{C})$$, des *objets* de $$\mathcal{C}$$
* Pour deux objets $$X,Y$$, un ensemble Hom$$_\mathcal{C}(X,Y)$$ des *morphismes de $$X$$ vers $$Y$$*,
* Pour trois objets $$X,Y,Z$$, une application $$\mathrm{Hom}_\mathcal{C}(X,Y) \times \mathrm{Hom}_\mathcal{C}(Y,Z) \longrightarrow \mathrm{Hom}_\mathcal{C}(X,Z) $$, appelée *composition*, loi associative notée par $$(f,g) \mapsto g \circ f$$.

Il est aussi naturel d'imposer l'existence d'un (unique) morphisme, dit *morphisme identité*, définit pour chaque objet $$X$$ par $$\mathrm{id}_X \in \mathrm{Hom}_\mathcal{C}(X,X)$$ tel que $$f\circ \mathrm{id}_X = f$$ pour tout morphisme $$f$$ de $$X$$ vers $$Y$$; et symétriquement $$\mathrm{id}_X \circ g = g$$ pour tout morphisme $$g$$ de $$Y$$ dans $$X$$.

Par commodité, on notera souvent $$X \in \mathrm{Ob}(\mathcal{C})$$ et $$f: X \mapsto Y$$ pour $$f \in \mathrm{Hom}_\mathcal{C}(X,Y)$$. Il est aussi courant en théorie des catégories d'appeller ces morphismes des "flèches", ce qui est pratique vu l'importance de la manipulation de *diagrammes*, vu comme des graphes reliant des objets par des flèches. Ainsi défini, un morphisme n'est autre qu'une flèche, de source $$X$$ et de but $$Y$$.

En lien avec la définition donnée au dernier paragraphe, notons qu'une catégorie $$\mathcal{C}$$ est appelé une $$\mathcal{U}$$-catégorie (ou localement petite) si $$\mathrm{Hom}_\mathcal{C}(X,Y)$$ est $$\mathcal{U}$$-petit pour n'importe quels objets $$X,Y$$. De la même façon, une $$\mathcal{U}$$-petite (ou juste petite) catégorie est une $$\mathcal{U}$$-catégorie telle que $$\mathrm{Ob}(\mathcal{C})$$ est $$\mathcal{U}$$-petite.

La plupart du temps, on travaillera sur des catégories (localement) petite. En fait, dans la définition d'une catégorie, $$\mathrm{Ob}$$ et $$\mathrm{Hom}$$ ne sont pas *a priori* des ensembles, mais des collections dites "classes propres". Pour rester sur des choses plus ou moins intuitives et connues, considérer des petites catégories règle ce problème.

Donnons déjà quelques exemples de catégories usuelles, que tout mathématicien peut (ou doit !) avoir rencontré dans sa vie.

* $$\mathrm{Set}$$ est la catégorie des $$\mathcal{U}$$-ensembles et des applications.
* $$\mathrm{Rel}$$ est la catégorie des *relations binaires*, dont les objets sont $$\mathrm{Ob(Rel)} = \mathrm{Ob(Set)}$$ et les morphismes $$ \mathrm{Hom}_{\mathrm{Rel}}(X,Y) = \mathcal{P}(X \times Y}$$
* $$\mathrm{Top}$$ est la catégorie est *espaces topologiques*, dont les morphismes sont les applications continues.
* $$\mathrm{Grp}$$ est la catégorie des *groupes* et ses morphismes sont évidemment les morphismes de groupes.

On peut bien sûr compléter cette liste à volonté en y ajoutant les anneaux, mais aussi les anneaux unitaires ou unitaires commutatifs, les groupes abéliens ou encore les espaces métriques et même les ensembles ordonnés (de morphisme les applications croissantes)...toute la boîte à outils mathématique.

Il n'est pas rare que, partant de morphismes $$X \longrightarrow Y$$, on souhaite en étudier d'autres de $$Y \longrightarrow X$$ (penser à la réciproque d'une application). Cette notion aura un rôle central et sera représentée par la catégorie *opposée*, ou *duale*, $$ \mathcal{C}^{op}$$ définie par

 * Les objets sont les mêmes: $$\mathrm{Ob} (\mathcal{C}^{op}) = \mathrm{Ob}(\mathcal{C})$$
 * Les flèches sont inversées: $$\mathrm{Hom}_{\mathcal{C}^{op}} (X,Y) = \mathrm{Hom}_{\mathcal{C}} (Y,X) $$

Pour des objets $$X$$ et morphismes $$f$$ dans $$\mathcal{C}$$, on pourra noter $$X^{op}$$ ou $$f^{op}$$ son image dans $$\mathcal{C}^{op}$$.

Avant de passer à la suite, j'aimerai passer un peu de temps sur le concept d'isomorphisme. Quand on parle d'isomorphisme, il y a  en général deux définitions (équivalentes) possibles. Prenons l'exemples des isomorphismes d'ensemble $$f : E \mapsto F$$; c'est-à-dire, d'une façon moins pédante, des bijections.

Une application $$f : E \mapsto F $$ est bijective si, pour tout $$y \in F$$, il existe un *unique* antécédent $$x \in E$$ tel que $$f(x) = y$$

Cette définition est très pratique pour présenter les bijections aux jeunes étudiants : il suffit de leur faire dessiner deux patates, les remplir de points et relier les points d'une patate vers ceux de l'autre. Si chaque couple de point est relié par une et une seule flèche, c'est une bijection.

Mais il faut se rappeller de l'intérêt de notre étude : on ne s'intéresse pas ici à proprement parler des éléments de tels ensembles, mais uniquement des flèches. On préférera alors cette autre définition:

Une application $$f : E \mapsto F $$ est bijective si $$g \circ f = \mathrm{id}_E$$ et $$f \circ g = \mathrm{id}_F$$

Ici, jamais on ne considère les éléments de $$E$$ et de $$F$$, il se peut même qu'il n'y en ait aucun (ce qui je l'avoue, ne serait pas très pratique mais soit.), mais seulement à la composition de flèches.

**Définition.** Un morphisme $$X \mapsto Y$$ est un isomorphisme si il existe $$g : Y \mapsto X$$ telle que $$f \circ g = \mathrm{id}_Y, ~ g \circ f = \mathrm{id}_X$$.
Un tel morphisme $$g$$ est appelé *inverse de $$f$$* et noté $$f^{-1}$$. S'il existe, on dit que $$X$$ et $$Y$$ sont isomorphes, ce qu'on note $$X \simeq Y$$.

Duale à celle des isomorphismes, présentons maintenant deux autres classe de morphismes, analogues - en un sens - aux notions d'injectivité et de surjectivité.

**Définitions.**
* Un morphisme $$f : X \mapsto Y$$ est un *monomorphisme* si pour toute paire de morphismes paralèlles $$g_1, g_2: Z \rightrightarrows X$$, si $$f \circ g_1 = f \circ g_2$$, alors $$g_1 = g_2$$. On note $$f : X \hookrightarrow Y$$.
* Un morphisme $$f : X \mapsto Y$$ est un *épimorphisme* si $$f^{op} : X^{op} \mapsto Y^{op}$$ est un monomorphisme dans $$\mathcal{C^{op}}$$. On note $$f : X \twoheadrightarrow Y$$.

En voyant ces notations, j'ai repensé à cet enseignant d'algèbre en L3 qui notait toujours les morphismes injectifs et surjectifs de la sorte, et laissait de temps en temps échapper le mot "épimorphisme" au détour d'une démonstration, avant de se reprendre devant nos airs étonné.

Il se trouve que cet enseignant est un géomètre algébristre, et que sa notation est parfaitement cohérente, en effet on peut remarquer que $$f$$ est un monomorphisme si et seulement si l'application $$ f \circ : \mathrm{Hom}_{\mathcal{C}}(Z,X) \mapsto \mathrm{Hom}_{\mathcal{C}}(Z,Y)$$ est injective pour tout $$Z$$, et de la même façon que $$f$$ est un épimorphisme si et seulement si $$\circ f : \mathrm{Hom}_{\mathcal{C}}(Y,Z) \mapsto \mathrm{Hom}_{\mathcal{C}}(X,Z)$$ est injective pour tout $$Z$$. (ie: injective dans la catégorie duale, en inversant les flèches on peut retrouver cette idée de surjection). Encore une fois, il faut faire attention aux définitions, et considérer des compositions à gauche et à droite et non pas raisonner en termes ensemblistes.

En particulier, en théorie des ensembles, les mono/épimorphismes sont exactements les fonctions inj/surjectives.

Nous allons revenir à nos exemples de catégories pour développer notre connaissance à leur sujet. Pour celà, partons pour une nouvelle vague de vocabulaire. C'est un peu long, mais c'est le prix à payer pour donner des exemples enrichis.

La première de la liste s'impose dans l'étude de chaque structure mathématique, et est donc assez naturelle, les suivantes donnent un peu de contexte et permettront des études plus détaillées.

**Définitions.**
* Une catégorie $$\mathcal(C)^\prime$$ est une *sous-catégorie* de $$\mathcal{C}$$, $$\mathcal{C}^\prime \subset \mathcal{C}$$ si les objets de $$\mathcal{C}^\prime$$ sont déjà des objets de $$\mathcal{C}$$, de même pour les morphismes, que la composition dans $$\mathcal{C}^\prime$$ est induite par celle de $$\mathcal{C}$$ et que le morphisme identité est le même.
* Une sous-catégorie $$\mathcal{C}^\prime \subset \mathcal{C}$$ est dite *pleine* si les morphismes sont les mêmes. $$\mathrm{Hom}_{\mathcal{C}}(X,Y) = \mathrm{Hom}_{\mathcal{C}^\prime}(X,Y)  $$
* Une sous-catégorie pleine est dite *saturée*, si, dès que $$X \in \mathcal{C}$$ est isomorphe à un quelconque objet de $$\mathcal{C}^\prime$$, alors $$X$$ est déjà dans $$\mathcal{C}^\prime$$.
* Une catégorie est *discrète* si les seuls morphismes sont les morphismes identité.
* Une catégorie est dite non-vide si sa classe d'objet est non-vide.
* Une catégorie est un *groupoïde* si tout morphisme est isomorphisme.
* Une catégorie est *finie* si l'ensemble de tous ses morphismes est fini. (et donc *a fortiori*, celui de ses objets également)
* Une catégorie est *connectée* si elle est non-vide et, pour tout $$X,Y \in \mathcal{C}$$, il existe une suite finite d'objets $$X_0,\dots,X_n$$, avec $$X_0 = X$$ et $$X_n = Y$$, tel qu'au moins l'un des ensembles $$ \mathrm{Hom}(X_j,X_{j+1})$$ ou $$\mathrm{Hom} (X_{j+1}, X_j) $$ est non-vide pour $$0 \leqslant j \leqslant n-1$$

Revenons maintenant sur nos exemples.


Références
--
[1] cat and sheaves
[2] article jean yves beziau
[3] sga 4.1
