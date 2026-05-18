+++
description = "Avec Git, GitHub, Markdown et un site statique, tous les outils existent pourtant pour produire des présences pérennes et sûres en ligne. Je «profite» de la chute de reseau-protestant.ch pour en tirer quelques enseignements."
title = "La sécurité de Git et la pérennité des sites statiques"
+++

La chute du site du *Réseau protestant* (réformé de Suisse romande) me fait réfléchir à la pérennité de sites dont le contenu change peu.
Avec Git, GitHub, Markdown et un site statique, tous les outils existent pourtant pour produire des présences pérennes et sûres en ligne.

C’est possible, c’est même assez simple, mais cela demande un minimum d’efforts.
Et surtout d’accepter de changer sa manière de voir.

Pour info, le site se trouvait à l’adresse `reseau-protestant.ch`.
Il peut toujours être vu dans la [Wayback Machine](https://web.archive.org/).

Ce billet n’accuse personne.
J’observe seulement situation concrète et en tire quelques réflexions.

## Site statique

Avec un système de gestion de contenu (CMS) classique , il faut mettre à jour le système, par exemple WordPress.
Mais il faut aussi tenir à flot toutes les extensions (plugins), mêmes celles qui ne sont pas actives.
Et il faut aussi actualiser les thèmes, même ceux qui ne sont pas actifs.
Et, sur le serveur, il faut mettre à jour PHP et la base de données.

Quand il y a une faille dans n’importe laquelle de ces couches, c’est le piratage probable.
C’est ce qui s’est (probablement) passé avec le site *Réseau protestant* en mars 2026.

Le paradoxe, c’est que l’on adopte souvent des CMS par souci de facilité.
Mais, quand un site est mis à jour peu souvent, il faut quand même mettre à jour la pile technique.
Autrement dit, la facilité (discutable) d’utilisation est compensée par la dette technique.

Donc, quand le contenu d’un site évolue peu dans le temps, il y a toujours intérêt à créer un site statique.

Un site statique est pérenne par nature.
Il ne se passe rien sur le serveur d’autre que la livraison de contenus déjà prêts.
J’en dis quelque chose dans [Création & affichage d’une page web](https://nicolasfriedli.ch/blog/creation-affichage-page-web/) et [Site statique, générateur de site & Hugo](https://nicolasfriedli.ch/blog/statique/).

Au début du *Réseau protestant*, il existait un site statique.
On le retrouve dans un commit vieux de 6 ans du [dépôt GitHub reseau-protestant](https://github.com/nfriedli/reseau-protestant/tree/508a402e508c3b2d56f5ece70675e9adad6f8a6b).

J’aurais dû insister, à l’époque, pour qu’il reste statique.
J’aurais dû essayer de convaincre que c’était le meilleur choix.
J’aurais dû...

Ce matin, j’ai remis à jour [Trouver ma paroisse](https://ma-paroisse.ch/).
Je peux le laisser en l’état durant des mois ou des années sans aucun risque de piratage ou de dysfonctionnement soudain.
C’est un immense confort qui est la conséquence directe des choix techniques que j’explique ci-dessous.

## Git

Le site est géré avec [logiciel de gestion de versions](https://fr.wikipedia.org/wiki/Logiciel_de_gestion_de_versions).
Ce qui signifie que chaque étape peut-être retrouvée dans un [historique](https://github.com/nfriedli/reseau-protestant/commits/master/).

Cet historique, j’en dispose sur mon propre ordinateur (et dans les sauvegardes de cet ordinateur).
Si j’utilise un dépôt en ligne, comme GitHub, l’historique y est aussi complet.
Puis, si je le copie sur un autre ordinateur, tout y est aussi.
Etc.

En gros, j’ai 2, 3 ou 4 versions complètes du site, dans des endroits différents.
Difficile de faire plus pérenne.
Si tout n’explose pas simultanément, tout va bien.

De plus, avec chaque modification dans Git, il y a un message d’accompagnement qui explique les changements et la possiblité de faire un `diff` (la [comparaison entre 2 étapes](https://github.com/nfriedli/reseau-protestant/commit/584a61ecfcbbeb35fd96d6b15e6089e0024baec0)).
Pour un site comme *Réseau protestant*, pas besoin d’expliquer chaque modification, toutes sont visibles et explicites.

J’aurais dû insister pour travailler avec Git, pour sa sécurité et pour sa clarté.
J’aurais dû...

## GitHub

Pour collaborer, la solution royale est d’utiliser un service en ligne comme GitHub.
Il en existe d’autres, mais c’est le plus connu.
On peut en changer en tout temps.

Avec GitHub, on peut rendre les sources du site publiques.
Et, surtout, rendre possible de travail collaboratif:

- de manière directe, en accordant les droits de modification à un·e internaute
- de manière indirecte, en permettant de signaler des problèmes (issues) ou de propositions de changements de code (pull requests)

Le vocabulaire est un peu compliqué, parce que nouveau pour beaucoup.
Mais les manipulations sont simples, à condition d’accepter de changer sa «manière de faire».

J’aurais dû profiter du projet *Reseau protestant* pour inciter des personnes éclairées et motivés à essayer Git et GitHub.
J’aurais dû remettre ma documentation sur Git en ligne.
J’aurais dû proposer une mini-formation en ligne.
J’aurais dû...

## Markdown

Au fond, la seule exigence pour utiliser Git dans un contexte techniquement simple comme le *Réseau protestant*, c’est de rédiger en Markdown.
Ce langage de balisage léger a gagné la course, comme le montre Anil Dash dans [How Markdown took over the world](https://www.anildash.com/2026/01/09/how-markdown-took-over-the-world/).

Toute personne qui produit sur le web aujourd’hui a intérêt à parler un minimum le Markdown.
Si c’est ce [langage de balisage léger](https://fr.wikipedia.org/wiki/Langage_de_balisage_l%C3%A9ger) qui a gagné, c’est parce qu’il est très simple.

Franchement, je ne vois aucune complexité dans le [fichier README.md actuellement dans le dépôt GitHub](https://raw.githubusercontent.com/nfriedli/reseau-protestant/refs/heads/master/README.md).
Surtout quand il est affiché dans un éditeur qui propose une [colorisation syntaxique](https://fr.wikipedia.org/wiki/Coloration_syntaxique).

J’aurais dû montrer comment fonctionne Markdown.
J’aurais dû proposer des exemples de `diff`, de `commit`, etc.
J’aurais dû...

## En conclusion

Après avoir donné un coup de main à la première version du *Réseau protestant*, il a existé un certain nombre d’années.
Il a été porté par une petite équipe (donc je ne faisais plus partie) qui a fait un beau travail pour faire connaître le projet.
Je me m’en réjouis; je vois le verre assez plein.

Mais je regrette de ne pas avoir saisi l’occasion de ce petit projet pour parler d’outils modernes et performants.
Je regrette de ne pas avoir parlé de sobriété numérique.
Tout n’est pas perdu, parce que l’histoire du piratage et les [«attaques» incessantes des robots d’indexations des intelligences artificielles (IA)](/blog/robotstxt) vont fatalement remettre la question au goût du jour.
