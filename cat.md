---
layout: post
header-img: "img/cat.jpg"
---



Voyant ce concept intervenir de près ou de loin dans à peu près toutes les discussions de mathématiciens - algébristes - auxquelles j'ai pu assister, j'ai profité de ce début de vacances pour enfin l'étudier d'un peu plus près : la théorie des catégories.

Ce billet sera l'occasion pour moi de réorganiser mentalement ces nouvelles idées, et de faire découvrir ce nouveau monde à d'autres néophytes.

Le plan sera calqué sur le premier chapitre du merveilleux livre de M. Kashiwara et P. Schapira [1]. Il est donc fortement probable que cet article soit très long, mais le but ici n'est pas tant de vulgariser que de présenter le vocabulaire de base que tout aspirant catégoricien serait mené à connaître. Le format sera donc plus proche de notes de lectures que d'un condensat de résultats ou idées générales; j'espère néanmoins réussir à reformuler les concepts de façon claire et si possible, donner envie de continuer l'étude par soi-même.

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

*On peut à ce stade définir les notions d'objet initial, terminal et nul, mais malgré l'intérêt de la chose, je laisse aux soins du lecteur de regarder dans [1]*

Par commodité, on notera souvent $$X \in \mathrm{Ob}(\mathcal{C})$$ et $$f: X \mapsto Y$$ pour $$f \in \mathrm{Hom}_\mathcal{C}(X,Y)$$. Il est aussi courant en théorie des catégories d'appeller ces morphismes des "flèches", ce qui est pratique vu l'importance de la manipulation de *diagrammes*, vu comme des graphes reliant des objets par des flèches. Ainsi défini, un morphisme n'est autre qu'une flèche, de source $$X$$ et de but $$Y$$.

En lien avec la définition donnée au dernier paragraphe, notons qu'une catégorie $$\mathcal{C}$$ est appelé une $$\mathcal{U}$$-catégorie (ou localement petite) si $$\mathrm{Hom}_\mathcal{C}(X,Y)$$ est $$\mathcal{U}$$-petit pour n'importe quels objets $$X,Y$$. De la même façon, une $$\mathcal{U}$$-petite (ou juste petite) catégorie est une $$\mathcal{U}$$-catégorie telle que $$\mathrm{Ob}(\mathcal{C})$$ est $$\mathcal{U}$$-petite.

La plupart du temps, on travaillera sur des catégories (localement) petite. En fait, dans la définition d'une catégorie, $$\mathrm{Ob}$$ et $$\mathrm{Hom}$$ ne sont pas *a priori* des ensembles, mais des collections dites "classes propres". Pour rester sur des choses plus ou moins intuitives et connues, considérer des petites catégories règle ce problème.

Donnons déjà quelques exemples de catégories usuelles, que tout mathématicien peut (ou doit !) avoir rencontré dans sa vie.

* $$\mathrm{Set}$$ est la catégorie des $$\mathcal{U}$$-ensembles et des applications.
* $$\mathrm{Rel}$$ est la catégorie des *relations binaires*, dont les objets sont $$\mathrm{Ob(Rel)} = \mathrm{Ob(Set)}$$ et les morphismes $$ \mathrm{Hom}_{\mathrm{Rel}}(X,Y) = \mathcal{P}(X \times Y)$$
* $$\mathrm{Top}$$ est la catégorie est *espaces topologiques*, dont les morphismes sont les applications continues.
* $$\mathrm{Grp}$$ est la catégorie des *groupes* et ses morphismes sont évidemment les morphismes de groupes.
* Pour $$K$$ un corps, $$\mathrm{Vect}_K$$ la catégorie des espaces vectoriels et des applications linéaires.

On peut bien sûr compléter cette liste à volonté en y ajoutant les anneaux, mais aussi les anneaux unitaires ou unitaires commutatifs, les groupes abéliens ou encore les espaces métriques et même les ensembles ordonnés (de morphisme les applications croissantes)...toute la boîte à outils mathématique.

Fait remarquable, l'ensemble des morphismes d'une catégorie $$\mathcal{C}$$, $$\mathrm{Mor}(\mathcal{C})$$ (ie: tous les morphismes, en opposition à $$\mathrm{Hom}$$ des morphismes d'un certain $$X$$ vers un certain $$Y$$) peut lui-même être muni d'une structure de catégorie. Les morphismes de cette catégorie sont définies de façons pas trop déconnantes (promis) par $$ \mathrm{Hom}_{\mathrm{Mor}(\mathcal{C})}(f,g) = \{ u:X\mapsto X^\prime, ~ v : Y \mapsto Y^\prime, ~ g \circ u = v \circ f \} $$

Ce morphisme peut être visualisé par le diagramme (enfin !) commutatif suivant.

$$
\require{AMScd}
\begin{CD}
X @>{f}>> Y\\
@V{u}VV @VV{v}V\\
X^\prime @>{g}>> Y^\prime
\end{CD} $$


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
* Une catégorie est *discrète* si les seuls morphismes sont les morphismes identité.
* Une catégorie est dite non-vide si sa classe d'objet est non-vide.
* Une catégorie est un *groupoïde* si tout morphisme est isomorphisme.
* Une catégorie est *finie* si l'ensemble de tous ses morphismes est fini. (et donc *a fortiori*, celui de ses objets également)
* Une catégorie est *connectée* si elle est non-vide et, pour tout $$X,Y \in \mathcal{C}$$, il existe une suite finite d'objets $$X_0,\dots,X_n$$, avec $$X_0 = X$$ et $$X_n = Y$$, tel qu'au moins l'un des ensembles $$ \mathrm{Hom}(X_j,X_{j+1})$$ ou $$\mathrm{Hom} (X_{j+1}, X_j) $$ est non-vide pour $$0 \leqslant j \leqslant n-1$$

*Mea culpa, j'aurai pu donner la définition de sous-catégorie saturée, mais je n'ai pour ainsi dire trouvé aucun exemple pour l'illustrer. Quant aux sous-catégories connectées, je l'ai bien vu une ou deux fois, mais j'ai peur que ces notions me soient encore trop obscures.*

Revenons maintenant sur nos exemples.

* $$\mathrm{Set} \subset \mathrm{Rel}$$, mais elle n'est pas pleine.
* La catégorie des groupes abéliens $$\mathrm{Ab}$$ est une sous-catégorie pleine de la catégorie groupes, elle-même sous-catégorie pleine des monoïdes. $$\mathrm{Mon}$$.
* Si $$A$$ est un anneau, on peut définir $$\mathrm{Mod}(A)$$ la catégorie des $$A$$-modules. Ainsi la sous-catégorie des $$A$$-modules de type fini en est une sous-catégorie pleine.
* Si $$X$$ est un ensemble et $$x \in X$$, le couple $$(X,x)$$ est un ensemblé pointé. On appelle $$\mathrm{pSet}$$ la catégorie de ces ensembles et on le munit d'une structure en définissant les morphismes $$f: (X,x) \mapsto (Y,y)$$ par $$f(x)=y$$

*Remarque: Je ne connaissais pas les ensembles pointés jusqu'ici. J'ai trouvé un exemple à première vue assez innatendu: le premier groupe de cohomologie $$H^1(G,A)$$ est un ensemble pointé. Mais c'est tout de suite moins drôle quand on sait que tout groupe est pointé en son neutre [4]*

Il est maintenant l'heure de faire un pas de plus dans l'abstraction. Nous avons jusqu'ici donner les grandes idées pour définir une catégorie. Composée d'objets de flèches, nous avons remarqué que les flèches formaient elles aussi une catégorie. Pour aller plus loin, nous allons maintenant voir qu'il est possible de relier les catégories entres elles, c'est précisement la notion de foncteur.

Dans un cursus scolaire "normal", il est assez rare de voir des applications qui partent d'une structure dans une autre, il peut donc être difficile de s'imaginer directement un exemple. On pourrait bien penser aux structures algébriques de base, et imaginer par exemple un morphisme (par un grotesque abus de language) d'un anneau vers un corps, mais je n'en connais personnellement aucun qui pourrait être intéressant. En revanche, il y a un exemple simple et assez courant qui est le *foncteur d'oubli*. Le foncteur d'oubli, fait "oublier" à sa source sa structure. Partons par exemple d'un espace topologique. C'est la donnée d'un ensemble, disons $$T$$, et d'une topologie: c'est elle qui donne sa structure à $$T$$. Le foncteur d'oublie va alors renvoyer uniquement $$T$$, l'ensemble sous-jacent de l'espace topologique. De la même façon, on peut considérer un groupe $$(G, \dot)$$ et ne renvoyer que $$G$$. Ce sont là deux foncteurs des catégories $$\mathrm{Top}$$ et $$\mathrm{Grp}$$ vers $$\mathrm{Set}$$. Ce sont là des exemples où les objets perdent "toute" leur structure, mais on peut aussi partir d'un groupe abélien $$G$$, *ie* un objet de $$\mathrm{Ab}$$ et le plonger dans $$\mathrm{Grp}$$, dans ce cas $$G$$ "oublie juste" qu'il est abélien.

**Définition.**
Soit $$\mathcal{C}, \mathcal{C}^\prime$$ deux catégories. Un *foncteur* $$F : \mathcal{C} \mapsto \mathcal{C}^\prime$$ est la donnée d'une application $$F: \mathrm{Ob} (\mathcal{C}) \mapsto \mathrm{Ob} (\mathcal{C}^\prime)$$ et $$F: \mathrm{Hom}_{\mathcal{C}}(X,Y) \mapsto \mathrm{Hom}_{\mathcal{C}^\prime}(F(X),F(Y))$$ pour tout $$X,Y \in \mathcal{C}$$, qui préserve l'identité et la composition.
Plus clairement, un foncteur est une application qui envoie chaque objet $$X$$ d'une catégorie $$\mathcal{C}$$ vers un objet $$F(X)$$ d'une catégorie $$\mathcal{C}^\prime$$, et chaque morphisme $$f : X \mapsto Y$$ vers un morphisme $$F(f):F(X) \mapsto F(Y)$$.
Sous de bonnes hypothèses, la composition de deux foncteurs $$G \circ F$$ est donnée par $$(G\circ F)(X) = G(F(X))$$ et $$(G\circ F)(f) = G(F(f))$$.

On appelle *foncteur contravariant* de $$\mathcal{C}$$ vers $$\mathcal{C}^\prime$$ un foncteur de $$\mathcal{C}^{op}$$ vers $$\mathcal{C}$$. C'est-à-dire que $$F(g \circ f) = F(f) \circ F(g)$$.


Il pourra être utile par la suite de noter le foncteur contravariant "trivial" $$\mathrm{op}: \mathcal{C} \mapsto \mathcal{C}^{op}$$ défini par l'identité. Notons que tout foncteur $$F:\mathcal{C} \mapsto \mathcal{C}^\prime$$ induit naturellement un foncteur dans le dual $$F^{op} : \mathcal{C}^{op} \mapsto \mathcal{C}^{\prime op}$$

Après un nouveau point vocabulaire, nous serons en mesure de (enfin !) montrer notre premier résultat.

**Définition.**

* Un foncteur $$F : \mathcal{C} \mapsto \mathcal{C}^\prime$$ est dit *fidèle* (resp. *plein*, *pleinement fidèle*) si

 $$ \mathrm{Hom}_{\mathcal{C}}(X,Y) \mapsto \mathrm{Hom}_{\mathcal{C}^\prime}(F(X),F(Y))  $$

 est injective (resp. surjective, bijective) pour tout $$X,Y \in \mathcal{C}$$.

* On dit que $$F$$ est *essentiellement surjectif* si pour chaque $$Y \in \mathcal{C}^\prime$$, il existe un objet $$X$$ de $$\mathcal{C}$$ et un isomorphisme $$F(X) \simeq Y$$.

* On dit que $$F$$ est *conservatif* si le fait que $$F(f)$$ est un isomorphisme dans $$\mathcal{C}^\prime$$ implique que $$f$$ est déjà un isomorphisme dans $$\mathcal{C}$$.

Par exemple, la foncteur d'oubli défini plus haut est fidèle. (mais pas pleinement)

On peut alors énoncer notre premier résultat, qui s'agit essentiellement d'une sorte de caractérisation des mono/épimorphismes.

**Résultat.** Soit $$F : \mathcal{C} \mapsto \mathcal{C}^\prime$$ un foncteur fidèle et soit $$f: X \mapsto Y$$ un morphisme de $$\mathcal{C}$$. Si $$F(f)$$ est un épimorphisme, (resp. monomorphisme), alors $$f$$ est déjà un épimorphisme. (resp monomorphisme)

La preuve de ce résultat peut être qualifiée de triviale, dans le sens où on ne fait qu'appliquer deux définitions, en fait tout le travail a été d'introduire ces concepts, mais le résultat n'en est pas moins intéressant. Nous ne traiterons que le cas d'un épimorphisme, l'autre étant similaire.

*Démonstration. Supposons que $$F(f)$$ est un épimorphisme et considérons deux flèches parallèles $$f,g: Y \rightrightarrows Z$$ telles que $$g \circ f = h \circ f$$. Alors, par préservation de la composition, $$F(g) \circ F(f) = F(h) \circ F(f)$$. On en déduit alors que $$F(g)=F(h)$$, et comme $$F$$ est fidèle, $$g=h$$.*

J'ai jusqu'ici passé sous silence les notions de catégorie produit et de réunion disjointe de catégories, mais les foncteurs s'appliquent évidemment à ces cas. En particulier, un foncteur $$F: \mathcal{C} \times \mathcal{C} \mapsto \mathcal{C}^{\prime \prime}$$ et appelé un *bifoncteur*. Détaillons.

Pour $$X \in \mathcal{C}, ~ X^$\prime \in \mathcal{C}^\prime$$, les applications $$F(X, \cdot): \mathcal{C}^\prime \mapsto \mathcal{C}^{\prime \prime}$$ et  $$F(\cdot, X): \mathcal{C} \mapsto \mathcal{C}^{\prime \prime}$$ sont des foncteurs. De plus, pour tout morphisme $$f : X \mapsto Y$$ dans $$\mathcal{C}$$, $$g : X^\prime \mapsto Y^\prime$$ de $$\mathcal{C}^\prime$$, le diagramme suivant commute:

$$
\require{AMScd}
\begin{CD}
F(X,X^\prime) @>{F(X,g)}>> F(X,Y^\prime)\\
@V{F(f,X^\prime)}VV @VV{F(f,Y^\prime)}V\\
F(Y,X^\prime) @>{F(Y,g)}>> F(Y,Y^\prime)^\prime
\end{CD} $$

On peut citer l'exemple, pour une $$\mathcal{U}$$-catégorie $$\mathcal{C}$$, le bifoncteur $$\mathrm{Hom}_{\mathcal{C}}(\cdot,\cdot) : \mathcal{C}^{op} \times \mathcal{C} \mapsto \mathrm{Set}$$.

Morphismes de foncteur, lemme de Yoneda
==

Je concluerai cet article par un dernier saut abstractif. Celui-ci consiste en une rapide présentation des morphismes de foncteurs (car après tout, des morphismes entre des images de morphismes entre des catégories, rien de plus simple ?) puis par l'énoncé du lemme de Yoneda. En dehors de l'aspect conceptuel, cette partie aura surtout pour intérêt de présenter des résultats et, a extenso, des démonstrations utilisant les outils présentés jusqu'ici.

**Définition.** Soit $$\mathcal{C}, \mathcal{C}^\prime$$ deux catégories et $$F_1,F_2$$ deux foncteurs de $$\mathcal{C}$$ vers $$\mathcal{C}^\prime$$
Un *morphisme de foncteurs* $$\theta: F_1 \mapsto F_2$$ consiste en un morphisme $$\theta_X : F_1(X) \mapsto F_2(X)$$ pour tout $$x$$, tel que, pour tout morphisme $$f: X \mapsto Y$$, le diagramme commute:

$$
\require{AMScd}
\begin{CD}
F_1(X) @>{\theta_X}>> F_2(X)\\
@V{F_1(f)}VV @VV{F_2(f) }V\\
F_1(Y) @>{F(Y,g)}>> F_2(Y)
\end{CD} $$

L'application $$\theta$$ est appelé *transformation naturelle*. Les transformations naturelles sont un sujet passionnant et riche d'exemple, qui mériterait un article plus court, pédagogue, et illustré. Par chance, il semblerait que quelqu'un l'ait [déjà fait...](https://www.math3ma.com/blog/what-is-a-natural-transformation)

Bien. Nous avons désormais des flèches entre nos catégories. On rajoute une idendité $$\mathrm{id}_\mathcal{C}$$ et on a tout le package. On serait tenté de travailler comme d'habitude, et *techniquement* on le pourrait, mais il semblerait qu'il y ait un hic: les isomorphismes de catégories - qui de fait, existent - sont bien trop restrictifs pour notre étude, on préférera  l'affaiblir et parler d'*équivalence de catégorie*.

**Définition.** Un foncteur $$F : \mathcal{C} \mapsto \mathcal{C}^\prime$$ est une *équivalence de catégories* si il existe $$G: \mathcal{C}^\prime \mapsto \mathcal{C}$$ et des isomorphismes de foncteurs $$\alpha : G \circ F \simeq \mathrm{id}_\mathcal{C}, \beta: F \circ G \simeq \mathrm{id}_{\mathcal{C}^prime}$$.
Dans une telle situation, on écrit $$F: \mathcal{C} \simeq \mathcal{C}^\prime$$, et on dit que $$F$$ et $$G$$ sont quasi inverse l'un de l'autre.

Présentons maintenant deux résultats, découlant tout deux du lemme de Zorn (qui, il faut le rappeller "n'est pas un lemme, et n'est pas de moi")

**Premier lemme.**  Soit $$F: \mathcal{C} \mapsto \mathcal{C}^\prime$$ un foncteur et une sous-catégorie pleine $$\mathcal{C}_0^\prime \subset \mathcal{C}^\prime$$ telle que pour tout $$X \in \mathcal{C}$$ il existe un $$Y \in \mathcal{C}_0^\prime$$ et un isomorphisme $$F(X) \simeq Y$$.
On note $$i^\prime$$ le plongement naturel de $$\mathcal{C}_0^\prime \mapsto \mathcal{C}_0$$.
Alors il existe un foncteur $$F_0 : \mathcal{C} \mapsto \mathcal{C}_0^\prime$$ et une transformation naturelle $$\theta_0: F \mapsto i^\prime \circ F_0$$. De plus, $$F_0$$ est unique à (un unique) isomorphisme près.

*Démonstration: Par le lemme de Zorn, pour chaque $$X$$, on peut choisir un $$Y$$ dans $$\mathcal{C}_0^\prime$$, un isomorphisme $$\varphi_X : Y \mapsto F(X)$$ et poser $$F_0(X) = Y$$. Si $$f : X \mapsto X^\prime$$ est un morphisme dans $$\mathcal{C}$$, on définit $$F_0(f) : F_0(X) \mapsto F_0(X^\prime)$$ comme étant la composition de $$F_0(X) \longrightarrow F(X) \longrightarrow F(X^\prime) \longleftarrow F_0(X^\prime)$$. *

**Second lemme.** Soit $$\mathcal{C}$$ une catégorie. Alors il existe une sous-catégorie $$\mathcal(C)_0$$ tel que le plongement naturel $$i$$ soit une équivalence de catégories.
De plus, si deux objets de $$\mathcal{C}_0$$ sont isomorphes, alors ils sont égaux.

Références
--
[1] cat and sheaves
[2] article jean yves beziau
[3] sga 4.1
[4] AN INTRODUCTION TO GALOIS COHOMOLOGY
AND ITS APPLICATIONS
