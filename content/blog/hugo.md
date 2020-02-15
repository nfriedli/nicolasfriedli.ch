---
title: Et à la fin, c'est Hugo qui gagne!
date: 2020-01-28
description: J'ai choisi d'utiliser le générateur de sites statiques Hugo pour mon site personnel, voici pourquoi.
---

Voilà des années que je n'ai pas blogué *chez moi* et que ça me manque.
J'ai besoin d'un site web personnel, pour me sentir bien *à la maison*.
Les plateformes centralisatrices et les réseaux sociaux me plaisent de moins en moins.
Comme j'utilise trop WordPress, j'ai suivi un autre chemin.

L'outil choisi s'appelle [Hugo](https://gohugo.io/).
C'est un générateur de sites statiques rapide, simple, efficace et stable.

J'ai hésité longtemps avec [Eleventy](https://www.11ty.dev/) (11ty), un autre générateur de sites statiques.
J'essaierai de vous parler de 11ty, une fois.
En attendant, voici pourquoi j'ai choisi Hugo.

## Simplicité d'installation

L'installation d'Hugo, c'est copier un fichier dans un répertoire.
C'est tout!
Pas besoin de droits d'administration, pas besoin de dépendances, pas de configuration.

C'est l'application stricte de la *règle de l'emmerdement minimal*.
Tant qu'il fonctionne, même pas besoin de le mettre à jour; aucun problème de sécurité.
Ce confort me plaît.

## Structure claire

Bien qu'il soit extrêmement souple, Hugo est pensé pour une structure de site *classique*.
Plusieurs types de pages qui suivent une logique banale: une page d'accueil, quelques autres pages à la racine, des répertoires constitués de pages dont une liste les autres.

On peut trouver cela simpliste et le déplorer.
Ou s'en réjouir, parce que l'on pense encore et toujours qu'un site est (souvent) constitués d'un certain nombre de pages organisée dans une arborescence.

Toute la structure des fichiers (configuration, fichiers statiques, sources et site généré) me paraît limpide.
Cette organisation, que certains trouvent rigide, me convient.

## Performances

La performance, c'est un peu la marque de fabrique d'Hugo.
Il s'est surtout fait connaître par sa capacité à générer des sites de plusieurs milliers de page en quelques secondes.

Aujourd'hui, je suis loin du compte, mais c'est un placement d'avenir.
Le machin tient le rythme même quand le site grandit.
Et surtout, il génère un petit site si rapidement qu'il est possible de le prévisualiser en temps réel sur son ordinateur.
Site statique, certes, mais développement dynamique!

La performance, c'est aussi le code qui est généré.
Ce site est constitué de pages minifiées (le code est compacté autant que possible), qui appellent une feuille de style elle aussi minifiée.
Pas de javascript (en attendant un éventuel `service worker`), ~~Google Analytics le temps de démarrer~~ pas de statistiques (autres que celles du serveur), ~~un chargement efficace des polices d'écriture~~ pas de polices d'écriture externes.

La vitesse du site devrait vous être agréable.

## Pages liées

Une des forces d'Hugo, c'est la gestion assez intéressante des *related*. 
Ou la manière de générer une liste de pages à relier à une autre, par exemple pour créer une section *Voir aussi*.

Utilisation plusieurs taxonomies, pondérations, seuil de proximité, etc. permettent d'affiner les choix.
À l'avenir, je devrais être à même de vous proposer un maillage interne à la fois simple et pertinent.
(Mais en attendant, il faudra que je rédige du contenu...)

## Multilinguisme

Finalement, Hugo gère nativement le multilinguisme avec simplicité et élégance.
Habitant et travaillant en Suisse, il est courant de concevoir et gérer des sites utilisant deux ou trois langues nationales. 
Et l'anglais.

La question des langues et traductions me semble bien plus simple à gérer qu'avec la grande majorité des outils de gestion de contenu.
Dans ce domaine (comme dans d'autres), les plus populaires ne sont pas forcément les meilleurs.