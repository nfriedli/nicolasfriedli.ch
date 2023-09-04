+++
title = "Budget de performance"
description = "Le travail sur un budget de performance permet des négociations en amont, une analyse à la mise en production et un suivi dans la durée."
date = 2023-08-18
+++

Il est facile et rapide d’évaluer la performance d’un site web avec Lighthouse, Web Page Test ou PageSpeed Insights. Mais ce n’est qu’un test ponctuel. Le travail sur un vrai budget de performance permet des *négociations* en amont. Puis une *analyse* à la mise en production. Enfin un *suivi* dans la durée.

## [](https://github.com/nfriedli/nicolasfriedli.ch/blob/4057f881885bf3bfe918acba3342b11a0bf81e96/content/performance/budget.md#quest-ce-quun-budget-de-perfomance)Qu’est-ce qu’un budget de perfomance?

Un budget de performance, ce sont les «coûts» acceptés pour l’affichage d’une page web. **Par coûts, on entend:**

- le *temps* (début de l’affichage, fin de l’affichage, mouvements non souhaités, etc.)
- la *taille* des fichiers (taille totale ou par type de ressources)
- un *nombre* de fichiers (nombre total ou par type de ressource)

**Du côté des «actifs», on a:**

- le *temps* que les internautes accordent pour l’affichage de la page
- la *capacité* des périphériques à gérer la mise en page
- la *bande passante* disponible, la latence, etc.
- ainsi que le *rapport aux sites concurrents*

Il s’agit de trouver **un équilibre pour *bien dépenser* ce qui est accordé**.

## Exemple pratique

Le lancement de l’analyse par Lighthouse (`npm` doit être installé avant):

```
npx lighthouse https://nicolasfriedli.ch \
    --budget-path=budget.json \
    --view \
    --only-categories=performance
```

En utilisant un budget détaille dans un fichier `JSON`:

```
[
  {
    "timings": [
      {
        "metric": "total-blocking-time",
        "budget": 0
      },
      {
        "metric": "largest-contentful-paint",
        "budget": 1000
      },
      {
        "metric": "speed-index",
        "budget": 1000
      },
      {
        "metric": "cumulative-layout-shift",
        "budget": 0
      }
    ],
    "resourceSizes": [
      {
        "resourceType": "total",
        "budget": 500
      },
      {
        "resourceType": "document",
        "budget": 100
      },
      {
        "resourceType": "script",
        "budget": 0
      },
      {
        "resourceType": "font",
        "budget": 200
      },
      {
        "resourceType": "image",
        "budget": 400
      },
      {
        "resourceType": "third-party",
        "budget": 0
      },
      {
        "resourceType": "stylesheet",
        "budget": 50
      }
    ]
  }
]
```

Dans cet exemple précis, on souhaite:

- un affichage complet de la page en 1 seconde
- l’absence de mouvements parasites (*Cumulative Layout Shift* ou CLS nul)
- pas plus de 500ko pour l’ensemble des transferts

Dans le détail

- pas plus de 100ko pour la page HTML
- pas de scripts
- pas de ressources tierces
- pas plus de 200ko pour les polices (qui ne devront donc pas être servies par un autre site)
- pas plus de 50ko de feuilles de style
- pas plus de 400ko d’image

## L’intérêt interne d’un budget de perfomance

Comme pour tout budget, derrière les nombres se cachent des considérations politiques. **L’élaboration d’un budget demande des négociations.** Dans le cas de la performance web, il faudra discuter entre les services:

- les graphistes souhaitent des polices d’écriture bien spécifiques
- les internautes des galeries d’images
- le service marketing veut des données statistiques
- la direction espère des encarts de réseaux sociaux
- les juristes souhaitent ne pas faire fuiter de donner à des tiers

Pour établir le budget, il faut donc se parler et trouver des compromis. Et surtout **établir un schéma de données crédibles**. Il ne sert à rien de proposer une planification trop optimiste, dont on sait qu’elle ne sera pas tenue. Il ne sert à rien non plus de s’accorder des valeurs démesurées uniquement pour la satisfaction de les respecter.

Dans la durée, un fichier établi par consensus permet une évaluation régulière d’un nombre important de pages du *corpus* que constitue le site. Et surtout de ne pas se battre à chaque demande plus ou moins loufoque d’un des services de l’organisation.

## Budget de performance et prestataires externes

Dans un travail avec une agence web, l’idée même de travailler avec un budget de performance annonce la couleur. Elle permet de se poser rapidement **les bonnes questions**:

- L’entreprise est-elle à l’aise avec ce genre d’outil?
- Est-ce qu’elle pose de bonnes questions sur les choix du mandataire?
- Est-ce qu’elle s’estime capable d’atteindre les objectifs? Si ce n’est pas le cas, est-ce qu’elle propose des corrections crédibles au budget?

Dans la relation entre mandant et mandataire, l’utilisation de métriques permet **la clarté**:

- arbitrage des demandes en cours de projet
- accord sur les termes (un site «performant»..., c’est quoi?)
- évaluation à la livraison

Ces derniers mois, j’ai vu plusieurs sites institutionnels entrer en production alors qu’ils ne sont pas au point. Avec un budget de performance, il était possible de refuser la livraison, de demander des améliorations tangibles ou d’exiger un rabais.
