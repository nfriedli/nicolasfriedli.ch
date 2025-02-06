---
title: Travailler avec un budget de performance web
description: Un budget de performance permet d’anticiper les contraintes, de cadrer les attentes et d’assurer un suivi continu pour obtenir un site rapide, fluide et optimisé.
date: 2025-02-06
categories:
- performance
---

Tester la performance d’un site avec Lighthouse, Web Page Test ou PageSpeed Insights est simple et rapide.
Mais cela ne garantit pas une optimisation durable.
Un budget de performance permet d’anticiper les contraintes, de cadrer les attentes et d’assurer un suivi continu.

## Qu’est-ce qu’un budget de performance?

La première visée d’un budget de performance est le contrôle suivi (monitoring) facilité de ses pages web.
Un budget de performance fixe les contraintes d’affichage d’une page web en équilibrant:

- les ressources consommées (temps de chargement, poids et nombre de fichiers)
- les attentes des internautes (rapidité perçue, fluidité de navigation)
- les limites techniques (bande passante, capacité des appareils)

Il s’agit de bien utiliser ce qui est accordé (voire de «dépenser» moins) pour garantir une expérience optimale.

## Exemple pratique

Concrètement, voici comment appliquer un budget de performance avec [Lighthouse](https://developer.chrome.com/docs/lighthouse/overview/):

```
npx lighthouse https://nicolasfriedli.ch/blog/budget-performance/ \
    --budget-path=budget.json \
    --view \
    --only-categories=performance
```

Avec un budget défini dans un fichier JSON (mise en forme comptacte):

```
[
  {
    "timings": [
      {"metric": "cumulative-layout-shift", "budget": 0},
      {"metric": "first-contentful-paint", "budget": 1800},
      {"metric": "interactive", "budget": 1000},
      {"metric": "largest-contentful-paint", "budget": 2500},
      {"metric": "speed-index", "budget": 1200},
      {"metric": "total-blocking-time", "budget": 0}
    ],
    "resourceSizes": [
      {"resourceType": "total", "budget": 100},
      {"resourceType": "document", "budget": 50},
      {"resourceType": "font", "budget": 0},
      {"resourceType": "image", "budget": 200},
      {"resourceType": "media", "budget": 200},
      {"resourceType": "other", "budget": 200},
      {"resourceType": "script", "budget": 5},
      {"resourceType": "stylesheet", "budget": 5},
      {"resourceType": "third-party", "budget": 5}
    ],
    "resourceCounts": [
      {"resourceType": "total", "budget": 10},
      {"resourceType": "font", "budget": 0},
      {"resourceType": "image", "budget": 10},
      {"resourceType": "media", "budget": 0},
      {"resourceType": "other", "budget": 2},
      {"resourceType": "script", "budget": 1},
      {"resourceType": "stylesheet", "budget": 0}
    ]
  }
]
```

Dans cet exemple, on souhaite par exemple:

- l’affichage complet de la page en 2.5 secondes
- l’absence de mouvements parasites (Cumulative Layout Shift à 0)
- 100ko maximum pour l’ensemble des transferts
- l’absence complètes de polices web (webfonts)

**C’est un budget très strict, adapté à ce site, mais trop restrictif dans bien des cas.**

Comme la sources JSON le montre clairement, il y a 3 catégories de mesures:

- la vitesse pure (timings)
- la taille des ressources (resourceSizes)
- le nombre des ressources (resourceCounts)

Dans chaque catégorie, il est possible de spécifier une ou plusieurs valeurs.

## Budget pour commencer

Il est possible de créer un budget JSON simplifié pour attaquer le sujet et faire ses premiers tests:


```
[
  {
    "timings": [
      {
        "metric": "largest-contentful-paint",
        "budget": 3000
      }
    ],
    "resourceSizes": [
      {
        "resourceType": "total",
        "budget": 1000
      }
    ],
    "resourceCounts": [
      {
        "resourceType": "total",
        "budget": 100
      }
    ]
  }
]
```

Dans ce cas, je vise:

- une page qui se charge en moins de 3 secondes
- qui pèse au maximum 1Mo
- qui n’appelle pas plus de 100 fichiers au total

Commencez par là et essayez de le respecter.
Si c’est le cas, votre site sera déjà très bon.

## La discussion du budget

Je vois d’autres utilités que le monitoring à l’établissement d’un budget de performance.

En premier lieu, les débats dans l’équipe de développement lors de son établissement.

La conférence [The Global Baseline, 2022](https://www.youtube.com/watch?v=BmiVevOUvho) d’Alex Russell, par exemple, donne les résultats moyens que l’on est en droit d’attendre aujourd’hui.
Le conférencier établit ses valeurs en fonction de réalités matérielles (capacité de calcul des téléphones) ou de réseau (bande passante).
En version textuelle, une actualisation est disponible dans [The Performance Inequality Gap, 2024](https://infrequently.org/2024/01/performance-inequality-gap-2024/).

La discussion du budget est une occasion formidable d’instaurer un débat sur ce qui est la «norme» du moment.
Elle permet d’apporter la question de la performance dans les équipes web, de manière concrète et pragmatique.

## Les problématiques internes

En deuxième lieu, un budget de performance est  un outil de dialogue entre les équipes.

Dans la réalité des entreprises et organisations:

- les graphistes veulent des typographies spécifiques
- le marketing a (soi-disant) besoin de trackers analytiques
- la direction souhaite intégrer des widgets sociaux
- les juristes veillent à la protection des données

L’objectif est de trouver un compromis réaliste et accessible.
Un budget trop ambitieux sera ignoré, tandis qu’un budget trop permissif ne servira à rien.

Dans la durée, un fichier établi par consensus évite de devoir se justifier chaque nouvelle contrainte ou ordre venu d’un autre service.
Il légitime les refus des équipes web ou permet de proposer des arbitrages concrets sur des bases solides.

## Rapport aux prestataires externes

Troisièmement, travailler avec un budget de performance facilite la relation avec une agence web. 

Un simple fichier `budget.json` permet:

- de fixer des attentes claires dès le début du projet
- d’évaluer si l’agence maîtrise vraiment les enjeux techniques
- d’arbitrer les demandes pour d’éviter les compromis nuisibles
- de justifier d’éventuelles corrections ou d’exiger une réduction de la facture

Ces dernières années, j’ai vu de nombreux sites institutionnels qui sont entrés en production alors qu’ils n’étaient pas optimisés.
Avec un budget de performance, il aurait été possible de refuser la livraison, d’exiger des améliorations tangibles ou de négocier un rabais.

## Conclusion

Adopter un budget de performance, c’est mettre toutes les chances de son côté pour obtenir un site rapide, fluide et optimisé, tout en facilitant les échanges entre équipes et prestataires.
En définissant un cadre clair, on évite les dérives, on pacifie les choix techniques et on assure une expérience optimale aux internautes sur le long terme.

Celles et ceux qui créent des sites qui militent pour l’écologie devraient aussi s’intéresser aux budgets de performance.
La question du temps de chargement ne sera pas forcément leur priorité.
Mais le nombre de ressources et leur taille sont en lien direct avec la consommation du site.
Et la performance suivra s’il est très léger.
