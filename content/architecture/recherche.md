---
title: 4 manières de rechercher (et trouver) une information sur un site
description: Il n’existe pas une seule manière de rechercher une information sur un site. Il existe 4 types de recherches avec des objectifs différents. J’essaie de vulgariser certains enjeux de l’architecture d’information.
date: 2025-11-22
---

Il n’existe pas une seule manière de rechercher une information sur un site.
Malheureusement, il est souvent considéré qu’une ressource en ligne sera trouvée... parce qu’elle est en ligne.
Cette croyance est problématique car sans rapport avec la réalité des internautes que nous sommes toutes et tous.

Cette page reprend des principes du livre *Information Architecture for the Web and Beyond* de Louis Rosenfeld, Peter Morville et Jorge Arango.
C’est toujours le meilleure référence sur le sujet.

Pour chaque type de recherche, il y aura 2 exemples concrets:

- le premier sur le site web d’un organisation (dans le monde dit «virtuel»)
- le second dans un supermarché (dans le monde dit «réel»)

Ainsi, j’essaie de vulgariser certains enjeux de l’architecture d’information.

## Le modèle trop simple et magique (qui ne fonctionne pas)

Avant de passer aux 4 modèles, voici celui qui ne fonctionne pas, mais qui est très répandu:

- l’internaute pose une question (où? comment? à qui?)
- il se passe quelque chose (recherche? navigation? divination?)
- la réponse est là (la magie a opéré)

Les auteurs du livre cité en référence ont très bien réfléchi au sujet, voici ce qu’ils ont à nous dire.

## Recherche exploratoire (trouver quelque bonnes pistes)

Le premier besoin, c’est de trouver une information utile, dans un contexte défini, sans disposer *a priori* de toutes les données nécessaires.

Dans le cadre d’une organisation, c’est de se renseigner sur les ressources humaines (RH).
Il convient donc de trouver les pages de ce service, puis de naviguer entre ces pages.
Très concrètement, l’internaute pourrait souhaiter contacter les RH sans connaître le nom de la personne responsable.

Dans le cadre d’un supermarché, c’est d’acheter du chocolat pour la très gourmande Madame Michu.
Il convient de trouver le rayon qui présente ce qui est disponible.
Puis de le parcourir pour trouver un cadeau qui fera plaisir.
Il y a plusieurs «réponses» possibles.

Ce qui compte du point de vue de l’architecture d’information, c’est la possibilité de **regroupements thématiques**:

- pages dans la même rubrique pour un site hiérarchique
- catégories ou mots-clés (*tags*) pour un blog
- liens contextuels précis dans le corps du texte pour un wiki

L’important, c’est de pouvoir parcourir simplement plusieurs contenus proches, qu’importe la manière.
 
## Recherche précise (trouver une information exacte)

Le deuxième besoin, c’est de trouver une information exacte le plus simplement et le plus rapidement possible.

Dans le cadre d’une organisation, c’est par exemple de trouver le numéro de téléphone d’une personne dont le nom est connu.
Il y a exactement une réponse à la question posée.

Dans le cadre d’un supermarché, le but est de trouver le chocolat préféré de Madame Michu en quelques secondes.

Ce qui compte du point de vue de l’architecture d’information, c’est la possibilité, c’est la possibilité de trouver un **contenu précis**:

- parce que la navigation dans le menu est univoque
- parce que les unités de contenu sont suffisamment bien définies (1 page = 1 sujet)
- parce que des listes permettent d’accèder exactement à ce qui est souhaité

Ou, évidemment, parce que le moteur de recherche interne est très efficace et classe bien les pages.

## «Re-recherche» (retrouver un contenu)

Le troisième besoin, c’est de retrouver une information qui avait déjà été trouvée à un autre moment.
Ce besoin est réel, mais pas toujours bien compris.

Dans le cadre d’une organisation qui publie son actualité en ligne, il peut s’agir de retrouver le billet de blog du printemps passé.
Il était en page d’accueil il y a quelques mois; il n’y est plus.
Les internautes doivent pouvoir naviguer de manière logique pour le retrouver.
Dans notre cas, en remontant la chronologie par un lien comme «Actualités précédentes».

Dans le cadre d’un supermarché, les clientes et clients doivent retrouver les produits au même endroit que la semaine précédente.
Sinon, les courses risque de durer longtemps.
Et les achats selon la liste, pourtant écrite selon l’ordre connu des rayonnages, pourrait bien être incomplets.

Tant sur un site que dans un magasin, les modifications de classement, d’architecture d’information, ne sont pas anodins.
Elles ne sont pas interdites, mais doivent être réfléchies.

Sur un site, la chronologie n’est pas la seule cause du «déplacement» une information.
Des liens de type «Ceci pourrait vous intéresser» (*related*) font également qu’un contenu accessible en bas d’une page donnée n’y sera plus à un autre moment.
De même que toutes les sélections aléatoires (*random*) de pages.

Ce qui compte du point de vue de l’architecture d’information, c’est d’avoir une certaine **constance dans le classement**.
Le fil d’Ariane (*breadcrumb*) peut être un allié précieux pour dire aux internautes où se trouve une page dans l’arborescence ([Opquast 156](https://checklists.opquast.com/fr/qualite-numerique/chaque-page-affiche-une-information-permettant-de-connaitre-son-emplacement-dans-larborescence-du-site)).
Ainsi, à la prochaine visite, il est possible de naviguer par le menu plutôt que d’arriver par un lien externe ou un moteur de recherche.

## Recherche exhaustive (parcourir toutes les pages)

Finalement, comme quatrième besoin, les internautes peuvent avoir l’envie (ou la nécessité) de parcourir toutes les informations disponibles.

Dans le cadre d’un organisation, c’est exactement le genre de navigation d’une nouvelle personne qui veut se mettre au courant de l’ensemble des prestations et des services.

Dans le cadre d’un supermarché, c’est normalement possible de manière assez facile en parcourant tous les rayons.

Ce qui compte du point de vue de l’architecture d’information, c’est de pouvoir **lister toutes les pages**:

- par un plan complet du site ([Opquast 171](https://checklists.opquast.com/fr/qualite-numerique/un-plan-du-site-est-disponible-depuis-chaque-page))
- par un méga menu (pour un petit site)
- par des menus contextuels (pour un petit ou un grand site)
- par des liens «Suivant» et «Prédécent» (pour un modèle chronologique)

Bien entendu, il existe certaines astuces pour découvrir toutes les pages d’un site.
Par exemple l’utilisation d’un logiciel spécifique (*crawler*) ou d’un fichier [`sitemap.xml`](/sitemap.xml), mais c’est n’est pas prévu pour une utilisation courante par des internautes.

## Note sur les moteurs de recherche

Bien entendu, il est toujours possible d’effectuer une recherche interne, si elle existe, ou externe.

Si votre site est bien référencé, avec un [travail de SEO sérieux](/seo/), ça pourrait fonctionner chez Google (ou un de ses concurrents).
La page [Recherches Google avancées](/pratique/recherche-google-avancee/) donne quelques pistes pour maîtriser des syntaxes comme:

```
site:nicolasfriedli.ch
```

Elle sera peut-être efficace pour l’exploration et une information précise.
Elle sera probablement moyenne pour retrouver un contenu; difficile de trouver un billet passé sans se souvenir exactement de son thème.
Et certainement inopérante pour un parcours exhausdtif, car lister toutes les pages n’est jamais aussi pertinent que les parcourir avec la structure et le contexte.
