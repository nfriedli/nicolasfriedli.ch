+++
title = "Pourquoi un site statique"
description = "Le choix d’un site statique peut paraître incongru dans les années 2020. Pourtant, ce type de site offre des avantages considérables que j’essaie de lister ici."
date = 2023-09-05
draft = true
+++

Le choix d’un site statique peut paraître incongru dans les années 2020. Pourtant, ce type de site offre des avantages considérables que j’essaie de lister ici.

Cette page est complémentaire à [Pourquoi choisir Hugo](/hugo/pourquoi-hugo/).

## Cohérence

## Sauvegarde implicite

Un site statique dispose presque toujours d’au moins une sauvegarde. Lorsque les sources sont gérées sur GitHub, comme c’est le cas pour mon blog, il existe:

- les sources sur plusieurs ordinateurs
- les sources sur GitHub
- le site compilé en ligne

À moins de stocker les sources (gérées avec Git ou non) uniquement sur son serveur de production, le site est donc toujours automatiquement sauvegardé.

Cela signifie aussi qu’en cas de problème, un déploiement sur un autre serveur est simple et rapide. Il est aussi possible de déployer automatiquement le site à des adresses de secours, par exemple chez Netlify, GitHub Pages, CloudFlare ou Vercel.

## Sécurité

Un système de gestion de contenu classique (WordPress, Drupal, Typo3, etc.) est par définition le moyen de donner un accès distant à son serveur.

Avec un site statique, les accès sont beaucoup plus restreints. Il n’existe aucun système de s’authentifier et de se loguer sur le un site en production. Il faut accéder au serveur (par FTP, rsync, etc.) ou au dépôt GitHub pour toute modification.

De plus, comme aucun logiciel ne tourne sur le serveur, il n’y a pas besoin de mise à jour. Les mêmes fichiers peuvent rester indéfiniment en ligne sans créer de failles de sécurité.

## Optimisation & vitesse

## Écoconception

## Édition en Markdown