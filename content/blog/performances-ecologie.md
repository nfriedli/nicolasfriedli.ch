---
title: Convergences et divergences entre performance et écologie
description: 
date: 2026-07-04
draft: true
---

La performance web et l’écologie ne visent pas les mêmes objectifs.
On pourrait même les imaginer en opposition.
Pourtant, certains choix techniques et tactiques servent les deux.
C’est à mon avis une proximité peu soulignée; je le regrette.

J’essaie de souligner les convergences sans esquiver les divergences.

## Objectifs différents

La performance web cherche à produire des pages et des sites rapides.
Elle souhaite rendre l’expérience des internautes (UX) la plus fluide possible

Alors que l’écologie ou l’éco-conception cherchent à rendre les sites légers.
Il doivent consommer un minimum de ressources tout en restant pertinents et utiles.

## Convergence contre-intuitive

Si la proximité entre écologie et performance est peu mise en valeur, c’est probablement parce qu’elle est contre-intuitive.
À mon avis, l’analogie assez évidente avec l’automobile l’explique.

Une voiture performante est souvent puissante, avec un gros moteur consommateur d’énergie (quelle qu’elle soit).
Alors qu’une voiture plus écologique est petite, roule moins vite, accélère moins fort.

Cette analogie n’est pas applicable telle quelle sur le web.
Il existe pourtant une convegence dans le monde de l’automobile Lotus.
Je reprends une des citations du génial créateur [Colin Chapman sur sa page Wikipédia](https://fr.wikipedia.org/wiki/Colin_Chapman):

> Ajouter de la puissance vous rend plus rapide en ligne droite.
> Enlever du poids vous rend plus rapide partout.

## Exemple des polices d’écriture

J’ai plusieurs fois parlé de polices d’écriture sur ce blog, c’est un excellent exemple où performance et écologie peuvent se rejoindre.

### Polices système

Ce qui est le plus léger (donc écologique) et le plus performant, c’est l’utilisation des [polices système](/blog/polices-systeme/).
En langage naturel, cela donne:

> Utilise une police d’écriture disponible sur le périphérique d’affichage (téléphone, tablette, ordinateur, etc.).
> Ne transfère aucun fichier.
> Ainsi tu ne consomme ni temps (performance), ni bande passante (écologie).

C’est simple et parfaitement effiace.
Convergence absolue.

### Web fonts et convergence

Quand il est «nécessaire» (ou que l’on pense nécessaire) de transférer une écriture, mieux vaut le faire bien.
J’en dis quelques mots techniques dans [Test de web fonts avec Geist et Geist Mono](/blog/geist/).
En langage naturel:

> Utilise le meilleur format de fichiers existant (`woff2`) et uniquement avec les caractères nécesseaires (subset).
> Ainsi, tu prends ni temps ni bande passant pour transférer de l’inutile.

Là encore, convergence complète entre performance et écologie.

### Divergences tactiques

C’est en entrant des les détails que l’on arrive à des divergences entre écologie et performance.
Si je souhaite le site le plus rapide possible:

> Dès que possible, télécharge tous les fichiers `woff2` sans te demander lesquels seront vraiment utilisés.
> Ainsi, tu auras tout en stock dès l’affichage de la page.
> Ce n’est pas grave si tu as chargé trop de fichiers.
> Techniquement, c’est un `preload`.

Si je veux aller encore plus vite, je peux demander:

> Télécharge tous les fichiers comment précédemment.
> Mais s’il y a la moindre lenteur, n’affiche pas du tout ce que tu as téléchargé (pour rien).
> Techniquement, c’est `font-display: optional`.

Alors que si je souhaite ne rien télécharger de trop, je peux dire:

> Ne télécharge que ce qui est vraiment nécessaire à l’affichage.
> Et affiche la page quand le fichier est arrivé, même si c’est plus lent.
> Techniquement, c’est `font-display: swap`.

Il n’y a pas de bon ou de mauvais choix dans ces différentes tactiques.
Il y a des objectifs différents et des résultats divegents.

Ce qui m’importe, c’est que l’utilisation commune de tout ce qui est convergent crée déjà un site écologique et performant.
Le reste est de l’ordre des détails.

## Convergences globales

## Divergences possibles

## Mes arbitrages

----

Les plus performant et le plus écologique, c’est ce qui n’est pas transféré, pas interprété, etc.

Donc pas de Javascript, pas de webfonts (mais des polices système), pas d’images, etc.

## Convergences

Minimisation des contenus

Simplicité du code

## Divergences

Preload des polices

Nombreuses images multitailles ou créées à la volée

## Zones limites

CSS interne ou CSS externe

Selon nombre de visites

Coût réellement plus faible?

(histoire du lave vaisselle de BDP et son mode éco)

## Mon arbitrage

Performance avant écologie