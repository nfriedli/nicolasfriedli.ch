---
title: Philosophie d’optimisation raisonnable
description: La meilleure efficacité est souhaitable, mais n’est pas toujours la meilleure solution. L’efficience (efficacité à moindre coût) est l’optimisation la plus raisonnable.
aliases:
- /blog/optimisation-raisonnable/
---

À force de consulter des sites de développement, il est facile de se perdre dans des tests numériques et des solutions techniques.
Mais il me paraît utile de formuler aussi les questions d’optimisation, de performance et d’éco-conception en langage naturel.

Cette idée de langage humain m’est venue en consultant la documentation de [minify](https://github.com/tdewolff/minify).
C’est l’outil permet d’optimiser les pages produites par [Hugo](/hugo/).

Dans chaque passage, je proposerai des citations qui devraient rendre le contenu de cette page accessible à des internautes non techniques.

## Formuler les résultats de tests en langage naturel

La page de projet de minify propose une comparaison de performances (benchmark) pour différents outils.
En première approche, je peux comparer les résultats de [taille](https://github.com/tdewolff/minify?tab=readme-ov-file#compression-ratio-lower-is-better) et définir un classement.

Mais à y regarder de plus près, il n’est pas certain que ce classement soit utile.
Une moyenne des résultats n’est pas probante, parce qu’il faudrait prendre le meilleur outil *pour chaque cas précis*.
L’épuisement guette s’il faut tout faire au cas par cas.

Je formule la chose en langage humain ou naturel:

> Les 5 outils testés permettent de gagner entre 40% et 70% de taille de fichier de manière automatique.
> Pour un fichier donné, le 5 outils obtiennent des résultats analogues (à 1% près).
> Ils sont tous excellents.

Vu ainsi, le classement n’a plus beaucoup de sens!

Alors on peut ajouter la question du [temps](https://github.com/tdewolff/minify?tab=readme-ov-file#time-lower-is-better) nécessaire à l’optimisation.

Et là, en langage naturel, il faudrait dire:

> Pour produire des fichiers de taille analogue, certains outils sont plusieurs centaines de fois plus lents que d’autres.

C’est là que minify excelle.
Il est certes peut-être moins *efficace* de 1%, mais jusqu’à 500 fois plus rapide.
Il est alors question d’*efficience*, l’efficacité rapportée au coût (temporel).

## Éviter les erreurs

J’ai une fois découvert une image de 70MB(!) sur une page d’accueil d’un site.
C’est un fichier gigantesque qui pose de vrais problèmes.
Elle s’afficherait sans différence sensible en étant 500 fois plus légère.

Quels que soient les efforts de performance sur une telle page, tout est cassé par un seul fichier problématique.
C’est pourquoi il faut toujours tester régulièrement son site web.
Tout le monde fait une erreur un jour ou l’autre.
J’ai découvert l’horreur par un contrôle régulier avec [speedlify](https://www.speedlify.dev/) que je conseille.

Donc, en français:

> Avant même de chercher à optimiser, il vaut la peine de détecter des erreurs manifestes qui annihileront tous les efforts et les gains de toutes les autres améliorations.

## Se demander ce qui est nécessaire

Des tests montrent [que jusqu’à 45% des fonctionnalités demandées par un utilisateur ne sont jamais utilisées et que jusqu’à 70% peuvent être considérées comme «non essentielles»](https://rweb.greenit.fr/fr/fiches/RWEB_0001-eliminer-les-fonctionnalites-non-essentielles).
Dès lors, il faut s’interroger sur ce qui est vraiment nécessaire.

Le fichier qui coûte le moins du point de vue de la performance est celui qui n’est pas hébergé sur un serveur, qui ne transite pas par le réseau et qui n’est pas interprété par le périphérique final.

> Avant de passer à une phase d’optimisation, il vaut la peine de se poser la question de la nécessité des outils proposés.
> Un fichier qui n’est pas envoyé n’a aucun coût écologique ou temporel.

Cette réflexion est valable pour les polices, pour les images, pour les encarts des réseaux sociaux.

## Optimiser avec efficacité

Si j’estime qu’une police spécifique est nécessaire, alors j’essaierai de faire les choses dans les règles de l’art.
Dès que l’on entre dans cette phase d’optimisation, on peut se prendre au jeu et essayer d’être le plus efficace possible.
C’est de bonne guerre.

Mais quand les gains entre 2 techniques ou tactiques sont minimes, il faut dire:

> Si la meilleure efficacité est souhaitable, elle n’est pas toujours la meilleure solution.

## Favoriser l’efficience

C’est pourquoi je cherche à toujours favoriser l’efficience.
C’est ce que me propose minify, dont je parle en haut de page.
Je n’ai rien à installer, rien à configurer, c’est rapide et j’obtiens un résultat excellent (mais pas forcément le meilleur possible).
Donc:

> L’efficience (efficacité à moindre coût) est l’optimisation la plus raisonnable.

C’est là que l’on passe de la pure question technique à une question philosophique.
Quand on est dans des questions de rapports entre coût et résultats, on entre dans le domaine de l’appréciation.
Et, finalement, du choix.

## S’amuser du snobisme

Comme la performance web me passionne, je cherche à toujours obtenir le meilleur résultat possible.
C’est pourquoi [ce site est hyper rapide](/infos/about/).

Mais, d’une certaine manière, utiliser une mise en page simpliste, renoncer aux images et ne pas utiliser de polices spécifiques est une forme de snobisme.
Au fond, je m’enorgueillis d’obtenir des [résultats parfaits dans PageSpeed Insights](https://pagespeed.web.dev/analysis/https-nicolasfriedli-ch/zdziqsc5vj?form_factor=mobile).
C’est aussi une forme de snobisme.

> La volonté d’obtenir le meilleur résultat à tout prix est un exercice utile pour les développeurs et développeuses.
> La compétition stimule la recherche.
> Mais c’est rarement un objectif de la pratique réelle.

J’ai effectué des [mandats dans des domaines très différents](/infos/bio/).
Mais la constante est que le meilleur résultat à tout prix n’est pas la première préoccupation des entreprises et institutions.

Ensemble, nous obtenons des produits raisonnablement optimisés parce que nous prenons le temps de discuter des enjeux de fond.
Nous arbitrons entre le souhaitable, l’utile, le nécessaire ou ce qu’il convient d’éviter à tout prix.
Ces tensions et ces négociations nous font discuter de questions sérieuses.
Et parfois même philosophiques.
