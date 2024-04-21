---
title: Police optimisée pour les titres
description: Proposer une police particulière sans prétériter la performance de son site. Optimisation du fichier, stratégie de chargement et gestion du cache.
date: 2024-03-30
categories:
- performance
---

Voici la stratégie j’applique sur mon site pour disposer d’une belle police pour les titres et les intertitres sans prétériter la performance.

**Remarque:** cette solution n'est plus utilisée actuellement sur ce site, mais toutes les considérations techniques de la démarche restent valables. 

## Optimisation de la police

J’ai choisi d’utiliser [Bricolage Grotesque](https://ateliertriay.github.io/bricolage/) pour les titres (`h1`, `h2`, etc.) de mon blog. C’est une police variable, ce qui signifie qu’elle dispose de beaucoup de variantes, mais qu’elle est aussi assez lourde. Elle peut varier de taille optique, de largeur et de poids (`opsz`, `wdth` et `wght`). 

Le téléchargement du fichier de départ se passe dans le [dépôt GitHub](https://github.com/ateliertriay/bricolage/tree/main) ou chez [Google Fonts](https://fonts.google.com/specimen/Bricolage+Grotesque). 

Pour être certain d’avoir un fichier léger, je vais convertir un fichier `ttf` en format `woff2`. Ce format est accepté par tous les navigateurs. Je ne souhaite pas de version variable sur mon site pour une question de poids. Comme tous mes titres sont en gras, je choisis la version statique `bold` (pour éviter la variation `wght`) et je prends celle en 48px (pour éviter la variation `opsz`). Je limiter la gamme de caractères à l’alphabet latin.

Avec le génial [Glyphhanger](https://github.com/zachleat/glyphhanger) de l’excellent Zach Leatherman:

```
glyphhanger 
    --formats=woff2
    --subset=BricolageGrotesque_48pt-Bold.ttf 
    --LATIN
```

La taille du fichier passe de 79kB à 25kB. Je le renomme en `bricolage.woff2` pour la suite.

Si le truc de Glyphanger semble trop compliqué, [Google Webfonfs Helper](https://gwfh.mranftl.com/fonts/bricolage-grotesque?subsets=latin) ou le [Webfont Generator de Font Squirrel](https://www.fontsquirrel.com/tools/webfont-generator) permettent de simplifier le travail.

## Affichage par la feuille de style CSS

Désormais, il faut utiliser ce fichier dans les règles de l’art pour que tout se passe bien.

Dans ma feuille de style, j’ai les règles suivantes ([feuille de style complète dans GitHub](https://github.com/nfriedli/nicolasfriedli.ch/blob/main/assets/css/screen.css)):

```
:root {
    --font-main: ui-sans-serif, Roboto, system-ui, sans-serif;
}

html {
    font-family: var(--font-main);
}
```

J’ajoute ces règles pour les 3 premiers niveaux de titres:

```
:root {
    --font-title: BricolageGrotesque, var(--font-main);
}

h1,
h2,
h3 {
    font-family: var(--font-title);
}
```

Ce qui signifie que si Bricolage Grotesque n’est pas disponible ce sera la même police que celle du texte qui sera utilisée. On évite ainsi de mauvaises suprises.

Et maintenant, on appelle la police que j’ai placée dans `/fonts/`:

```
@font-face {
    font-display: swap;
    font-family: BricolageGrotesque;
    font-style: normal;
    font-weight: 700;
    src: url("/fonts/bricolage.woff2") format("woff2");
}
```

Avec un site généré par Hugo, on placera le fichier source dans `/static/fonts/`.

## Stratégie de chargement et de cache

Si je dois être certain que le site ne soit jamais ralenti par le chargement de police, je peux choisir un affichage optionnel avec:

```
font-display: optional;
```

Si ma feuille de style était dans un fichier externe, je pourrais lancer le chargement avant même la disponibilité du CSS:

```
<link 
    rel="preload" 
    href="/fonts/bricolage.woff2" 
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

Ces règles de cache signifient que le fichier restera en mémoire durant une année et ne sera pas rechargé. Pour des informations très précises sur la gestion du cache, je conseille [Cache Rules Everything](https://www.youtube.com/watch?v=qVQjGwm_mmw) par Harry Roberts.

## Améliorer votre site

La même politique peut s’appliquer pour toutes les polices du de votre site. Vous pouvez entreprendre une même démarche en vous inspirant des travaux de Zach Leatherman:

- [The Scoville Scale of Web Font Loading Opinions](https://beyondtellerrand.com/events/dusseldorf-2019/speakers/zach-leatherman)
- [A Comprehensive Guide to Font Loading Strategies](https://www.zachleat.com/web/comprehensive-webfonts/)

Mais quand plusieurs polices entrent en jeu, d’autres questions se posent. Par exemple:

- quels fichiers précharger (`preload`) pour ne pas faire de transferts inutiles?
- quelle police afficher de quelle manière (`optional` ou `swap`)?
- quelle pertinence d’une feuille de style externe uniquement pour les chargement de polices?

Dans tous les cas, essayez d’éviter les services tiers comme Google Fonts. Ils posent des problèmes de confidentialité, de fiabilité et de perfomance. Et comme ils proposent un cache très court, ils gaspillent pas mal de ressources en transferts inutiles.
