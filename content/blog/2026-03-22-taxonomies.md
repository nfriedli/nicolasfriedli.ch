+++
description = "Les taxonomies (tags, mots-clés, keywords, etc.) sont un outil formidable d’architecture d’information. Mais elles sont complexes à maintenir dans la durée. D’où ma proposition d’un référentiel partagé en théologie francophone."
title = "Taxonomies en théologie et sur theologique.ch"
+++

Les taxonomies sont un moyen de classer le contenu sur un site.
Plus précisément, elles permettent de regrouper des contenus du même ordre.
Elles s’appellent catégories, tags, #hashtags ou mots-clés (keywords).

Les systèmes de gestion de contenu (CMS) modernes permettent de les utiliser facilement, d’un point de vue technique.
Mais leur gestion est souvent complexe, du point de vue du sens.
J’essaie de donner quelques pistes pour pratique utile aux internautes et aux  référencement dans les moteurs de recherche (SEO).

## Exemple de WordPress

Comme WordPress est le CMS le plus utilisé sur le web, autant commencer par lui.
Toutefois, sa conception des taxonomies n’est pas triviale.
Notamment parce que certaines sont obligatoires et d’autres sont optionnelles.

Par défaut – ce dont je parle ici –, WordPress propose 2 types de taxonomies:

catégories
: Toute entrée de blog (article) doit appartenir à au moins une catégorie.
Elle peut faire partie de plusieurs catégories.
Il existe une possibilité hiérarchique avec des sous-catégories (récursives).
Les pages ne peuvent pas se voir attribuer de catégories.

mots-clés (tags)
: Des mots clés peuvent être attribués aux articles.
Mais il est aussi possible d’utiliser WordPress sans aucun mot-clé.
Les pages ne peuvent pas se voir attribuer de mots-clés.

En pratique, il existe 2 manières principales de structurer un blog WordPress:

- mettre tous les articles dans une seule catégorie (par exemple «Blog» ou «Actualité»)
- séparer ses publications en quelques catégories (par exemple «Prédications», «Recensions», «Billets d’humeur»)

Dans tous les cas, je conseille:

- de ne pas utiliser de sous-catégories
- d’essayer de placer chaque article dans 1 seule catégorie

Ensuite, il est possible d’attribuer des tags à ses publications.
Ils permettent de:

- regrouper une partie du contenu d’une catégorie (segmentation)
- regrouper des contenus de même ordre qui font partie de plusieurs catégories (navigation transversale)

Un des «problèmes» de WordPress vient de la simplicité de création de nouveaux tags.
Il suffit d’ajouter des mots et, à chaque nouveau mot, un tag (avec sa page dédiée) est créé.
C’est simple, mais rarement efficace.
La confusion est facile et rapide.

Mon conseil, c’est de toujours commencer à bloguer sans utiliser les mots-clés.
Ils peuvent être ajoutés plus tard, simplement, quand on sait vraiment à quoi ils devront servir.

## Autres CMS et outils

Dans la majorité des CMS et outils de publication, les taxonomies sont complètement optionnelles.
Autrement dit, il est possible de proposer un site complet sans taxonomie du tout.

Par exemple, dans un réseau social comme Mastodon ou un outil comme Instagram, les #hashtags ne sont pas nécessaires.
Quand un contenu ne se voit attribuer aucune taxonomie, il entre simplement dans le flux.

Les taxonomies ne sont pas un élément structurel fort comme les catégories de WordPress.
C’est beaucoup plus simple à prendre en main, parce que les taxonomies peuvent être ajoutées avec le temps, quand on est parfaitement à l’aise avec l’outil.

Sachez qu’avec WordPress, si vous avez bien configuré vos permaliens, vous pouvez commencer par tout placer dans une catégorie «Blog».
Puis répartir («dispatcher») les contenus en différentes catégories uniquement quand cela devient nécessaire.
Les adresses (URL) de vos pages ne changeront pas, votre référencement restera bon ou s’améliorera.
La compréhension de votre site par les internautes également.

## Taxonomies utiles et inutiles

Depuis 20+ ans, bourrer une page de mots-clés (keywords) ne fonctionne plus.
C’était une technique qui marchait avant l’arrivée de Google, dont l’algorithme a tué cette pratique.
Tant mieux!
Et pourtant, il subsiste une confusion entre les mots-clés (qui sont des requêtes cibles) et les mots-clés (qui sont des taxonomies).
Pour mieux comprendre ce qu’est une requête cible, je vous conseille [Keyword research for SEO: the ultimate guide](https://yoast.com/keyword-research-ultimate-guide/).

Donc, dans le cas des taxonomies, [ajouter des dizaines de tags à une page](https://gillesbourquin.ch/predication-savoir-oser-dire-les-choses-evangile-jean/) est contre-productif.
Pour les internautes, ça ne sert à rien; personne ne va s’amuser à cliquer sur une liste trop longue.
Pour les moteurs de recherche, c’est tout simplement néfaste; il y a tant de liens qu’aucun n’a d’importance.

Pour que les taxonomies aient du sens, il faut qu’elles soient choisies, pas trop nombreuses, précises.
Pour détecter les taxonomies inutiles, il existe 2 indices efficaces:

- quand le nombre d’articles dans une taxonomie de segmentation (tous les articles sont dans 1 rubrique) est proche du nombre d’articles de la rubrique, c’est qu’elle ne segmente plus grand chose
- quand le nombre d’article(s) lié(s) à une taxonomie vaut 1 ou 2, c’est que ce n’est pas vraiment une taxonomie

En conséquence, quand on clique sur un mot-clé, on devrait arriver sur une page intéressante.
Le nombre d’article devrait être raisonnable (s’il n’y en a que 1, j’ai cliqué pour rien).
Et, surtout, la raison de regrouper ces articles devrait être évidente.
Sans évidence, il n’y a pas de sens.

Je pense que la taxonomie du [blog de Diane Friedli](https://dianefriedli.ch/) est intéressante.
La taxonomie [Noël](https://dianefriedli.ch/tag/noel/) compte à ce jour 23 articles qui sont répartis entre 3 catégories (navigation transversale).
Tous les [Contes et récits de Noël](https://dianefriedli.ch/category/contes/) se voient attribuer ce tag.
Ce pourrait être absurde si ce tag ne débordait sur d’autres catégories ([Prédications](https://dianefriedli.ch/category/predication/) et [Catéchèse](https://dianefriedli.ch/category/catechese/)).
Il est possible, en décembre, de retrouver tout ce qui concerne Noël sans difficulté.
Exactement ce que l’on souhaite d’une taxonomie.
C’est simple, ça fonctionne, ça se gère bien dans la durée.

## Gérer des vocabulaires

L’article [Fans Are Better Than Tech at Organizing Information Online](https://www.wired.com/story/archive-of-our-own-fans-better-than-tech-organizing-information/) publié par Wired m’avait impressionné.
Le travail effectué sur les taxonomies par les bénévoles de [Archive of Our Own](https://archiveofourown.org/) (Ao3) est incroyable.

Le système qui vise à ajouter un maximum de tags est néfaste, on vient de le voir.
En théologie, ce pourrait être quelque chose comme: `#exegese` `#NouveauTestament` `#Evangile` `#Matthieu` `#pericope` `#Mt12`.

Mais l’autre péril taxonomique, c’est l’accumulation d’un «même» tag.
En théologie, ce pourrait être `#Nouveau Testament` `#NouveauTestament` `#NT`. 
Si les 3 tags regroupent les mêmes articles, c’est «bienvenue en enfer» pour les internautes comme pour Google et compagnie.

Le truc génial de Ao3, c’est de laisser les rédactrices et rédacteurs choisir leurs mots-clés, dans des listes existantes.
Tout en leur laissant la possiblité d’en ajouter.
Quand il n’y a pas de liste de départ, c’est le chaos assuré.
Quand la liste est complètement fermée, ce n’est pas très incitatif.

Puis, des centaines de bénévoles trient les nouveaux tags, les gèrent, choisissent les meilleurs.
Il y a «modération des tags».
Et cela fonctionne très bien.

D’après les responsables du site, c’est beaucoup plus efficace que tous les systèmes automatisés.
Parce que les bénévoles connaissent le contexte et les finesses des contenus classés.
Je les crois volontiers.

## Proposer des taxonomies théologiques

Je suis convaincu que nous aurions intérêt, par exemple entre blogueuses et blogueurs, à choisir quelques taxonomies ensemble:

- principe général: `#Nouveau Testament`, `#NT`, `#Nouveau-Testament`, `#NouveauTestament` ?
- vocabulaire: `#prédications`, `#sermons` ou `#messages`?
- majuscules ou minuscules: `#ancientestament`, `#ancienTestament` ou `#AncienTestament`?
- accents ou non: `#priere` ou `#prière`?
- singulier ou pluriel: `#méditation` ou `#méditations`?
- abréviation ou canton: `#EREN` ou `#Neuchâtel`?
- croisillon ou non: `éthique` ou `#éthique`?

Je ne développe pas pour le moment.
Il me paraît évident que ce serait utile, mais j’ai peur d’être le seul à le penser.
Si cette réflexion suscite l’intérêt, je suis prêt à lancer une liste de référence sur GitHub (ou ailleurs).

## Sur theologique.ch

Pour le moment, ce site n’utilise pas du tout de taxonomies.
Tous les billets sont dans la rubrique «Blog».
Avec Hugo que j’utilise, c’est simplement un [répertoire](https://github.com/nfriedli/theologique.ch/tree/main/content/blog).

Par défaut, Hugo propose 3 taxonomies, que j’imagine utiliser bientôt:

- les catégories, qui devraient segmenter les articles en grandes sections et qui pourraient être affichées sur la page d’accueil ou dans le menu
- les tags, qui devraient segmenter les catégories ou proposer une navigation transversales mais qui ne seraient pas affichés sur la page d’accueil ou dans le menu
- les keywords qui seraient invisibles aux internautes mais permettraient de regrouper des contenus «par magie»

C’est un chantier prochain.
`#OuPas`

----

J’ajoute qu’il est important, quand une page de taxonomie existe, qu’elle propose une vrai contenu comme un titre bien choisit, un texte introductif, une description, etc.
L’idée est de faire des pages de mots-clés ou des catégories des *landing pages* solides.
Plus d’informations dans [Taxonomy SEO: How to optimize your categories and tags](https://yoast.com/taxonomy-seo-categories-tags/).

----

Je reste à disposition pour vous aider à sauver votre WordPress personnel de l’explosion taxonomique dans laquelle vous pataugez.
