---
title: Philosophie d’optimisation raisonnable
description: La meilleure efficacité est souhaitable, mais n’est pas toujours la meilleure solution. L’efficience (efficacité à moindre coût) est l’optimisation la plus raisonnable.
date: 2024-10-26
categories:
- performance
---

À force de consulter des sites de développement, il est facile de se perdre dans des tests numériques et des solutions techniques.
Mais il me paraît utile de formuler aussi les questions d’optimisation, de performance et d’éco-conception en langage naturel.

Cette idée de langage humain m’est venue en consultant la documentation de [minify](https://github.com/tdewolff/minify).
`minify` permet d’optimiser les pages produites par [Hugo]({{< relref "site-statique-generateur-hugo" >}}).

Dans chaque passage, je proposerai des citations qui devraient rendre le contenu de cette page à des internautes non techniques.

## Formuler les résultats de tests en langage naturel

`minify` propose une comparaison de performances (benchmark) pour différents outils.
En première lecture, je peux comparer les résultats de [taille](https://github.com/tdewolff/minify?tab=readme-ov-file#compression-ratio-lower-is-better) et définir un classement.

Mais à y regarder de plus près, il n’est pas certain que ce classement soit toujours identique.
Une moyenne des résultats n’est pas probante, parce qu’il faudrait prendre le meilleur outil *dans un cas précis*.
L’épuisement guette.

Maintenant, je formule la chose en langage humain ou naturel:

> Les 5 outils testés permettent de gagner entre 40% et 70% de taille de fichier de manière automatique.
> Pour un fichier donné, le 5 outils obtiennent des résultats analogues (à 1% près).
> Ils sont tous excellents.

Vue ainsi, le classement n’a plus beaucoup de sens!

Alors on peut ajouter la question du [temps](https://github.com/tdewolff/minify?tab=readme-ov-file#time-lower-is-better) nécessaire à l’optiomisation.

Et là, en langage naturel, il faudrait dire:

> Pour produire des fichiers de taille analogue, certains outils sont plusieurs centaines de fois plus lents que d’autres.

C’est là que `minify` excelle.
Il est certes peut-être moins *efficace* de 1%, mais jusqu’à 500x plus rapide.
Il est alors question d’*efficience*, l’efficacité rapporté au coût (temporel).

## Éviter les erreurs

Il y a quelques semaines, j’ai découvert une image de 70MB(!) sur une page d’accueil d’un site.
C’est un fichier gigantesque qui pose de vrais problèmes.
Elle s’afficherait sans différence sensible en étant 500 fois plus légères.

Quels que soient les efforts sur une telle page, tous est cassé par 1 fichier problématique.
C’est pourquoi il faut toujours [tester régulièrement son site web]({{< relref "tester-site" >}}).
J’ai découvert l’horreur par un contrôle régulier avec [speedlify](https://www.speedlify.dev/) que je conseille.

Donc, en français:

> Avant même de chercher à optimiser, il vaut la peine de détecter des erreurs manifestes qui annihilent tous les efforts

## Se demander ce qui est nécessaire

Des tests montrent [que 70% des fonctionnalités demandées par les utilisateurs ne sont pas essentielles et que 45% ne sont jamais utilisées](https://github.com/cnumr/best-practices/blob/main/chapters/BP_001_fr.md).
Dès lors, il faut se demander sérieusement ce qui est vraiment nécessaire.

Le fichier qui coût le moins du point de vue de la performance est celui qui n’est pas hébergé sur un serveur, qui ne transite pas par le réseau et qui n’est pas interprété par le périphérique final.

Avant d’utiliser une police d’écriture spécifique, je devrais me demander sur une [police disponible]({{< relref "polices-systeme" >}}) n’est pas suffisante.

> Avant de passer à une phase d’optimisation, il vaut la peine de se poser la question de la nécessité des outils proposés.
> Un fichier qui n’est pas envoyé n’a aucun coût écologique ou temporel.

Cette réflexion est valable pour les polices, pour les images, pour les encarts des réseaux sociaux.

## Optimiser avec efficacité

Si j’estime qu’une police spécifique est nécessaire, alors j’essaierai de faire les choses dans les règles de l’art.
J’en parle dans [Police optimisée pour les titres]({{< relref "police-optimisee-titres" >}}).

Dès que l’on entre dans cette phase d’optimisation, on peut se prendre au jeu et essayer d’être le plus efficace possible.
C’est de bonne guerre.

Mais quand les gains entre 2 techniques ou tactiques sont minimes, il faut dire:

> La meilleure efficacité est souhaitable, mais n’est pas toujours la meilleure solution.

## Favoriser l’efficience

C’est pourquoi je cherche à toujours favoriser l’efficience.
C’est ce que me propose `minify`, dont je parle en haut de page.
Je n’ai rien à installer, rien à configurer, c’est rapide et j’obtiens un résultat excellent (mais pas forcément le meilleur possible).
Donc:

> L’efficience (efficacité à moindre coût) est l’optimisation la plus raisonnable.

C’est là que l’on passe de la pure question technique à une question philosophique.
Quand on est dans des questions de rapports entre coût et résultats, on entre dans le domaine de l’appréciation.
Et, finalement, du choix.

## S’amuser du snobisme

Comme la performance web me passionne, je cherche à toujours obtenir le meilleur résultat possible.
C’est pourquoi [ce site est hyper rapide]({{< relref "about" >}}).

Mais, d’une certaine manière, utiliser une mise en page simpliste, renoncer aux images et ne pas utiliser de polices spécifiques est une forme de snobisme.
Au fond, je m’enorgueillis d’obtenir des [résultats parfaits dans PageSpeed Insights](https://pagespeed.web.dev/analysis/https-nicolasfriedli-ch/zdziqsc5vj?form_factor=mobile).
C’est une forme de snobisme.

> La volonté d’obtenir le meilleur résultat à tout prix est un exercice utile pour les développeurs.
> La compétition stimule la recherche.
> Mais c’est rarement un objectif de la pratique réelle.

J’ai effectué des [mandats dans des domaines très différents]({{< relref "bio" >}}).
Mais la constante est que le meilleur résultat à tout prix n’est pas leur première préoccupation.

Ensemble, nous obtenons des produits raisonnablement optimisés parce que nous prenons le temps de discuter des enjeux de fond.
Nous arbitrons entre le souhaitable, l’utile, le nécessaire ou ce qu’il convient d’éviter à tout prix.
Ces tensions et ces négociations nous font discuter de questions sérieuses.
Et parfois philosophiques.
