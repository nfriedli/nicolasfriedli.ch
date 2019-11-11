---
title: Et à la fin, c'est Hugo qui gagne!
date: 2019-11-11
description: J'ai choisi d'utiliser le générateur de sites statiques Hugo, voici pourquoi.
---

Voilà des années que je n'ai pas blogué *chez moi* et que ça ma manque.
J'ai besoin d'un site web personnel, pour me sentir bien *à la maison*.
Comme les plateformes centralisatrices et les réseaux sociaux me plaisent de moins en moins, comme j'utilise trop WordPress, j'ai suivi un autre chemin.

L'outil choisi s'appelle [Hugo](https://gohugo.io/).
C'est un générateur de sites statiques rapide, simple, efficace et stable.

L'hésitation avec [Eleventy](https://www.11ty.io/) (11ty) a été longue.
J'essaierai de vous dire pourquoi dans un prochain article.
En attendant, voici pourquoi j'ai choisi Hugo.

## Simplicité d'installation

L'installation d'Hugo, c'est copier un fichier dans un répertoire.
C'est tout!
Pas besoin de droits d'administration, pas besoin de dépendances, pas de configuration.

C'est l'application stricte de la règle de l'emmerdement minimal.
Tant qu'il fonctionne, même pas besoin de le mettre à jour; aucun problème de sécurité.
Ce confort me plaît.

## Structure claire

Bien qu'il soit extrêmement souple, Hugo suppose une structure de site *classique*.
Pour faire court, il y a plusieurs types de pages qui suivent une logique banale.
Une page d'accueil et, éventuellement, d'autres pages à la racine.
Des répertoires constitués de pages dont une, à la racine, liste les autres.

On peut trouver cela simpliste et le déplorer.
Ou s'en réjouir, parce que l'on pense encore et toujours qu'un site est (souvent) constitués d'un certain nombre de pages organisée dans une structure de répertoires.

Toute la structure des fichiers (configurations, fichiers statiques, sources et site généré) me paraît limpide.
Cette organisation que certaines trouvent rigide me convient.

## Performances

La performance, c'est un peu la marque de fabrique d'Hugo.
Il s'est surtout fait connaître par sa capacité à générer des sites de plusieurs milliers de page en quelques secondes.

Aujourd'hui, je suis loin du compte, mais c'est un placement d'avenir.
Le machin tient le rythme même quand le site grandit.
Et surtout, il génère un petit site si rapidement qu'il est possible de le prévisualiser en temps réel sur mon ordinateur.
Site statique, certes, mais développement dynamique!

La performance, c'est aussi le code qui est généré.
Ce site est constitué de pages minifiées (le code est compacté autant que possible), qui appellent une feuille de style elle aussi minifiée.
Pas de javascript, pas de statistiques (autres que celles du serveur), pas de polices d'écriture externes.

La vitesse du site devrait vous être agréable.

## Pages liées

Une des forces d'Hugo, c'est la gestion assez intéressante des *related*. 
Autrement dit, la manière de générer une liste de pages à relier à une autre, par exemple dans une section *Voir aussi*.

Il est possible d'utiliser plusieurs taxonomies, de pondérer chacune, de choisir un seuil de proximité.
À l'avenir, cette possibilité devrait permettre de proposer un maillage interne à la fois simple et pertinent.
(Mais en attendant, il faudra que je rédige du contenu...)

## Multilinguisme

Finalement, Hugo gère nativement le multilinguisme avec simplicité et élégance.
Habitant et travaillant en Suisse, il est courant de travailler sur des sites utilisant deux ou trois langues nationales. 
Et l'anglais.

L'idée de traiter facilement ce que bien des outils très répandus délaissent me plaît.
Les premiers essais de sites multilingues sont concluants, vivement la suite.