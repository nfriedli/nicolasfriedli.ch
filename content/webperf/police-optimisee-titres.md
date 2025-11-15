---
title: Police optimisée pour les titres
description: Proposer une police particulière sans prétériter la performance de son site. Fichier optimisé en woff2 latin, stratégie de chargement efficace et gestion du cache pour minimiser les ressource.
---

Voici une stratégie facile à mettre en œuvre pour disposer d’une belle police pour les titres et les intertitres sans prétériter la performance.

Il est possible que je l’utilise, par moments, sur ce site.
Mais les tactiques et techniques de cette page restent valable dans la durée et applicable à d’autres polices.
Ce qui est documenté plus bas est disponible dans le [dépôt GitHub au commit 74a8e8d](https://github.com/nfriedli/nicolasfriedli.ch/blob/efb6694df25c11b22e0397124a88b7d7926dffdc/assets/css/all.css).

## Optimisation de la police

J’ai choisi de tester [Literata](https://fonts.google.com/specimen/Literata) pour les titres (`h1`, `h2`, etc.) de mon site.
C’est une police variable, ce qui signifie qu’elle dispose de beaucoup de variantes, mais qu’elle est aussi assez lourde.
Elle peut varier de taille optique et de poids (`opsz` et `wght`).

Pour me simplifier la vie, j’ai téléchargé la police sur le site [Google Webfonfs Helper](https://gwfh.mranftl.com/fonts/literata?subsets=latin).
Je l’ai choisie en graisse normale (400), en version droite et italique (alphabet latin).

Ainsi, je dispose de fichiers `woff2` légers (environ 40Ko pour les 2) sans nécessité de passer par [glyphhanger](https://github.com/zachleat/glyphhanger).
Ils sont légers car non variables; ils sont «nettoyés» des options que je n’utiliserai pas.
C’est suffisant et parfait pour ma titraille.

## Affichage par la feuille de style CSS

Désormais, il faut utiliser ce fichier dans les règles de l’art pour que tout se passe bien.

Dans ma feuille de style, j’ai des règles de ce type:

```
:root {
    --sans-serif: ui-sans-serif, "Roboto", system-ui, sans-serif;
}

html {
    font-family: var(--sans-serif);
}
```

J’ajoute ceci pour les premiers niveaux de titres:

```
:root {
    --titles: "Literata", var(--sans-serif);
}

h1, h2, h3, h4 {
    font-family: var(--titles);
    font-weight: 400;
}
```

Ce qui signifie que, si Literata n’est pas disponible, c’est la police du texte qui sera utilisée.
On évite ainsi de mauvaises surprises.

Et maintenant, on appelle la police Literata que j’ai placée dans `/fonts/`:

```
@font-face {
  font-display: optional; 
  font-family: "Literata";
  font-style: normal;
  font-weight: 400;
  src: url("/fonts/literata-v40-latin-regular.woff2") format("woff2"); 
}

@font-face {
  font-display: optional; 
  font-family: "Literata";
  font-style: italic;
  font-weight: 400;
  src: url("/fonts/literata-v40-latin-italic.woff2") format("woff2"); 
}
```

## Stratégie de chargement et de cache

Je veux être certain que le **site ne soit jamais ralenti** par le chargement de police.
Donc, je mise sur un affichage optionnel avec:

```
font-display: optional;
```

Si je voulais être certain que cette police s’affiche (même avec un délai), j’opterais pour:

```
font-display: swap;
```

Sur ce site, les CSS sont dans la page HTML, donc immédiatement disponibles.
Mais si ma feuille de style était dans un fichier externe, je pourrais lancer le chargement avant même la disponibilité du CSS.

```
<link 
    rel="preload" 
    href="/fonts/literata-v40-latin-regular.woff2" 
    as="font" 
    type="font/woff2" 
    crossorigin>

<link 
    rel="preload" 
    href="/fonts/literata-v40-latin-italic.woff2" 
    as="font" 
    type="font/woff2" 
    crossorigin>
```

Et dans tous les cas, j’ajoute une règle de cache dans le fichier `.htaccess`, pour tous les fichiers de type `woff2`:

```
<filesMatch ".(woff2)$">
    Header set Cache-Control "max-age=63072000,immutable"
</filesMatch>
```

Ou, quand j’utilise Netlify, une règle dans `_headers` appliquée pour un répertoire plutôt qu’un type de fichiers:

```
/fonts/*
    Cache-Control: max-age=63072000,immutable
```

Ces règles de cache signifient que **les fichiers resteront en mémoire durant une année et ne seront pas rechargés**.
Pour des informations très précises sur la gestion du cache, je conseille [Cache Rules Everything](https://www.youtube.com/watch?v=qVQjGwm_mmw) par Harry Roberts.

## Améliorer votre site

**La même politique peut s’appliquer pour toutes les polices de votre site.**
Vous pouvez entreprendre une même démarche en vous inspirant des travaux de Zach Leatherman:

- [The Scoville Scale of Web Font Loading Opinions](https://beyondtellerrand.com/events/dusseldorf-2019/speakers/zach-leatherman)
- [A Comprehensive Guide to Font Loading Strategies](https://www.zachleat.com/web/comprehensive-webfonts/)

Mais quand plusieurs polices entrent en jeu, d’autres questions se posent.
Par exemple:

- quels fichiers précharger (`preload`) pour ne pas faire de transferts inutiles?
- quelle police afficher de quelle manière (`optional` ou `swap`)?
- quelle pertinence d’une feuille de style dédiée uniquement au chargements des polices?

Dans tous les cas, il vaut mieux **éviter les services tiers comme Google Fonts**.
Ils posent des problèmes de confidentialité, de fiabilité et de performance.
Et comme ils proposent un cache très court, ils gaspillent pas mal de ressources en transferts inutiles.
