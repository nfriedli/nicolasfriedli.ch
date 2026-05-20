+++
title = "Wander propose des conseils de lecture pour explorer le web"
description = "Facile, ludique et décentralisé, Wander permet de publier une liste aléatoire de recommandations de liens. Et de s'étendre de manière décentralisée avec d'autres propositions."
date = 2026-05-11
+++

Au hasard de mes lectures et livraisons de mon agrégateur de flux, j’ai découvert *Wander* de Susam Pal.
Ce truc est simple et génial pour proposer des sites de manière aléatoire, vivante, collaborative et décentralisée.

## Présentation de Wander

Le dépôt [Wander](https://codeberg.org/susam/wander#readme) propose les fichiers pour l’installation et la documentation de l’outil.
Mais je pense que quelques explications sont plus simples pour commencer.

### Hasard

En se rendant sur un Wander, une page web s’affiche au hasard.
Ce qui me plaît, c’est qu’il n’y a pas à parcourir une longue liste, à réfléchir, à arbitrer.
C’est simple et instantané.

Une fois cette page ouverte:

- je peux la consulter dans Wander (le défilement fonctionne, ce n’est pas une capture d’écran...)
- je peux me rendre sur le site en cliquant sur `Open` (nouvel onglet)
- je peux charger une autre page en cliquant sur `Wander`

C’est tout (pour le moment)!

Comme j’adore et que c’est simple à mettre en œuvre, j’ai rapidement publié mon [Wander sur theologique.ch](https://theologique.ch/wander/).
Il est utilisable sur la plupart des périphériques.
Mais j’ai trouvé un ancien iPad (et un ancien Safari) où cela ne fonctionne pas.

Les pages proposées sont issues d’une liste que j’ai construite pour la démonstration.
Elle est visible dans `Console > Pages` dans un format lisible avec des liens cliquables.

### Pages et sites

Ce que je trouve intéressant, c’est de ne pas publier uniquement des sites, mais aussi des pages précises.
Au fond, renvoyer à l’accueil du site n’est pas toujours pertinent.

C’est à la personne qui crée sa sélection de choisir ce qui semble le plus juste.
Au moment de la rédaction de ce billet, j’ai par exemple choisi de partager des pages d’accueil:

```
https://affordance.framasoft.org/
https://aurelienetz.ch/
https://eliojaillet.ch/
https://marcpernot.net/
https://www.arthurperret.fr/
```

Des pages précises de site:

```
https://jeromeg.ch/2026/04/26/fin-du-blog/
https://olivierbauer.wordpress.com/parcours-decouvrir-le-protestantisme-accueil/
https://write.as/bartux/post-verite-post-realite-post-humanite
https://www.cidoc.ch/nouvelles/selection-du-mois/anciennes-selections
https://www.theologeek.ch/2021/05/26/des-textes-du-seigneur-des-anneaux-pour-accompagner-la-mort/
```

Et une combinaison des 2:

```
https://dianefriedli.ch/
https://dianefriedli.ch/3-reflexions-catechese/
https://dianefriedli.ch/jeunes-alibi/

https://espritdeliberte.leswoody.net/
https://espritdeliberte.leswoody.net/2024/09/15/la-catechese-pour-un-peu-plus-que-la-culture-et-la-doctrine/

https://lauredevaux.ch/
https://lauredevaux.ch/category/meditation-domestique/

https://ploum.net/
https://ploum.net/2023-06-15-merdification.html
https://ploum.net/2025-02-06-decadence-technologique.html
```

Lorsque nous construisons des *blogrolls* et autres pages de liens, je trouve que nous mettons trop l’accent sur les *homepages*.
Il n’y a aucun obstacle à renvoyer à des contenus plus précis, mais nous le faisons peu.

Pour le moment, Wander n’est qu’un partage de liens.
Il est rendu ludique et dynamique par son aspect aléatoire.
Mais il est aussi bien plus!

### Réseau décentralisé

Le truc vraiment génial, c’est que les Wander se mettent en réseau.
Mon Wander va afficher une URL choisie dans ma liste, mais va aussi charger les listes d’autres Wander.

Pour le moment, je ne l’ai pas implémenté sur mon site, mais vous pouvez voir le machin en action dans le [Wander de Susam Pal](https://susam.net/wander/):

- en cliquant sur `Console > Pages`, on voit la liste des pages de ce Wander
- en cliquant sur `Console > Neighbours`, on voit les autres Wander reliés
- et en cliquant sur `Console > Crawl`, on voit comment se construit la liste de liens de Wander en Wander

Vous avez compris!
La navigation s’étend de proche en proche, créant un réseau de conseils, voire un réseau de confiance.

Franchement, avec 10 ou 20 Wander théologiques de 10 ou 20 pages chacun, on aurait un outil de découverte formidable!

### Listes d’exclusion

Je peux consulter la liste d’une autre instance que je souhaite référencer chez moi.
Et là, je vois un lien que je ne souhaite pas voir apparaître sur mon site.

Plutôt que de ne pas référencer cette instance, je peux simplement bloquer ce lien.
Les autres sites apparaîtront (peut-être, aléatoirement) chez moi.
Un lien exclu restera visible dans son Wander initial, mais pas sur mon site.
Simple et élégant.

### Limites du projet

La barrière de la langue est un (petit) problème en ce qui concerne l’interface.
Il faudra voir si une possibilité de traduction existe, à moins que je m’y colle.
C’est mineur.

La vraie barrière de la langue, c’est que si d’autres instances mêlent les langues, je ne les relierai probablement pas.
Il faudrait donc un minimum de «ligne commune» pour créer un Wander théologique francophone.

Dernière limite, il faut placer un fichier sur un serveur et éditer une liste de sites.
C’est le genre de truc manifestement insurmontable pour beaucoup (qui disent que c’est compliqué avant d’avoir essayé).
C’est une limite psychologique plutôt que de compétences...

## Contexte 2026

Il me semble qu’il est nécessaire de construire ou reconstruire des **réseaux de confiance**.
Les intelligences artificielles (IA) et les moteurs de recherche vous balancent n’importe quoi, je vous propose ma liste de confiance.

Mais il peut aussi être intéressant de construire des **réseaux protestants**.
Parce que le *Réseau protestant* (canal historique) était une liste centralisée avant tout.
Un vrai réseau, sans centre, me paraît plus intéressant aujourd’hui.

Enfin, je pense que l’aspect **immédiatement visible et utilisable** de Wander lui offre des chances de réussir.
Au contraire de [human.json](/blog/human-json/) qui est invisible et demande l’installation d’une extension de navigateur.

Reste la question du moment:

> Vais-je supprimer tout ce qui est sur theologique.ch pour ne proposer qu’un Wander en page d’accueil?

En l’attente d’une réponse, je vous propose:

- de me signaler les instances que vous avez installées
- de me demander de l’aide si vous souhaitez en publier une sur votre nom de domaine

Bonnes découvertes!
