---
title: Recherche statique performante avec PageFind
description: Ajoutez un moteur de recherche performant à votre site statique avec PageFind. Facile à intégrer, léger et sans services tiers, il est idéal pour Hugo et d’autres générateurs statiques.
date: 2025-02-10
---

Un moteur de recherche peut améliorer l’expérience des internautes (UX) en offrant un accès rapide aux contenus d’un site.
Pour les sites statiques, il faut soit coder une recherche côté client à la main, soit utiliser un service tiers comme Algolia.
Ou alors on peut utiliser PageFind qui se distingue par sa facilité d’intégration et ses performances.

## Qualité web

La règle [Opquast 163](https://checklists.opquast.com/fr/assurance-qualite-web/le-site-propose-un-moteur-de-recherche-interne) est sans équivoque:

> **Le site propose un moteur de recherche interne.**
> Le moteur de recherche est, avec le plan du site, les menus et le lien de retour à l’accueil, un des moyens fondamentaux de réorientation et d’accès à l’information. Rendez-le présent et facile d’accès.

Je signale que la règle [Opquast 164](https://checklists.opquast.com/fr/assurance-qualite-web/chaque-page-de-resultats-de-recherche-peut-etre-atteint-via-une-adresse-web) ne sera pas respectée:

> Chaque page de résultats de recherche peut être atteinte via une adresse Web.

Alors que la règle [Opquast 165](https://checklists.opquast.com/fr/assurance-qualite-web/il-est-possible-de-relancer-une-recherche-depuis-sa-page-de-resultats) le sera:

> Il est possible de relancer une recherche depuis sa page de résultats.

## Présentation de PageFind

[PageFind](https://pagefind.app/) est conçu pour ajouter une recherche interne aux sites statiques: 

- il analyse toutes les pages générées (en local) pour créer un index
- il génère le code nécessaire pour l’affichage et la recherche côté client
- il est rapide à la compilation et léger à l’usage
- il est utilisable sans configuration (et il est configurable)
- il est très bien documenté

Je viens de parcourir l’ensemble de la documentation pour imaginer les possibles cet outil.
Elle est très claire, bien structuré, ni trop longue, ni trop succincte.

Si le sujet vous intéresse, je vous conseille ces vidéos:

- [Static Search on Hugo: The Journey to Pagefind v1.0](https://www.youtube.com/watch?v=WgoBoX4qTk8)
- [Workshop and Interview with Pagefind engineer Liam Bigelow](https://www.youtube.com/watch?v=wb6tD2gDv2c)

Je conseille de toujours se renseigner sur les objectifs d’un projet avant de l’adopter ou non.
PageFind vise à être **performant sur de grands sites**, en utilisant **le moins de bande passante possible** et **sans infrastructure particulière** ou de service tiers.
Je suis impressionné du resultat, avec des réponses souvent meilleures que la recherche de ~~WordPress~~ des CMS classique.

## Inclure la recherche dans Hugo

Comme je ne souhaite pas la recherche sur toutes les pages, j’ai créé un shortcode Hugo que je peux placer où je le veux.
Je pourrais très bien l’appeler ici avec un simple `{{</* search */>}}`.
 Sur ce site, j’ai choisi de l’intégrer dans une page dédiée à la recherche.

Le code de `layout/shortcodes/search.html` est une reprise la proposition de [Getting Started with Pagefind](https://pagefind.app/docs/) avec quelques [options de configuration](https://pagefind.app/docs/ui/):

```
<link href="/pagefind/pagefind-ui.css" rel="stylesheet">
<script src="/pagefind/pagefind-ui.js"></script>
<div id="search"></div>
<script>
    window.addEventListener("DOMContentLoaded", (event) => {
        new PagefindUI({
            element: "#search",
            pageSize: 10,
            showSubResults: true,
            showImages: false,
            autofocus: true
        });
    });
</script>
```

Bien entendu, je lance PageFind entre la compilation avec Hugo et le déploiement sur le serveur.

## Conclusion

La promesse de PageFind est tenue.
Il est très simple d’intégrer une bonne recherche à un site statique en quelques minutes.
Le lien se trouve dans le menu principal.

Désormais, j’attends 2 informations pour faire un vrai bilan.

**Est-ce que la recherche est bonne?**
La pertinence des résultats, la rapidité de recherche et la qualité de l’affichage sont essentielles.
Vos retours tant positifs que négatifs sont précieux.

**Est-ce qu’elle est utilisée?**
Les statistiques Plausible vont me donner quelques indices sur l’utilisation réelle de la page de recherche.
Si elle n’est pas utilisée, je me poserai aussi la question d’inclure la recherche sur toutes les pages du site.

J’en profite pour créer un [mail prérempli]({{% relref "linkmail" %}}) pour les résultats: [Envoyer mes tests de recherche dans TestFind](mailto:hello+2025@nicolasfriedli.ch?subject=Test%20de%20PageFind&body=Hello%2C%0D%0A%0D%0AJe%20viens%20de%20tester%20un%20peu%20PageFind%20sur%20ton%20site%20et%20voici%20ce%20que%20je%20peux%20en%20dire.%0D%0A%0D%0AC’est%20globalement%3A%20excellent%20%2F%20bon%20%2F%20moyen%20%2F%20mauvais%20%2F%20non%20fonctionnel%0D%0A%0D%0AExemples%20de%20recherche%20qui%20fournissent%20de%20bons%20r%C3%A9sultats%3A%0D%0A%0D%0AExemples%20de%20recherche%20qui%20fournissent%20de%20mauvais%20r%C3%A9sultats%3A). Merci!