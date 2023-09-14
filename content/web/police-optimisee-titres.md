+++
title = "Police optimisée pour les titres"
description = "Comment proposer une police particulière pour les titres sans prétériter la performance?"
date = 2023-05-14
lastMod = 2023-09-14
+++

Comment proposer une police particulière pour les titres sans prétériter la performance? Voici la stratégie j’applique sur mon site.

## Optimisation de la police

J’ai choisi d’utiliser l’excellente [Fraunces](https://fraunces.undercase.xyz/) d’Undercase Type pour les titres (`h1`, `h2`, etc.) de mon blog. C’est une police variable, ce qui signifie qu’elle dispose de beaucoup de variantes, mais qu’elle est aussi assez lourde.

Le téléchargement du fichier de départ se passe chez [Google Fonts](https://fonts.google.com/specimen/Fraunces) (download family). J’ai choisi: `Fraunces_72pt-Bold.ttf`.

La polices est ensuite tranformée au format `woff2`, le plus léger actuellement disponible. Ce format est [accepté par tous les navigateurs décents](https://caniuse.com/woff2). Seules les lettres nécessaires au français sont conservées. Le tout se fait avec [Glyphhanger](https://github.com/zachleat/glyphhanger) du génial Zach Leatherman.

La commande magique:

```
glyphhanger --formats=woff2 --subset=Fraunces_72pt-Bold.ttf --LATIN
```

La taille du fichier passe de 70kB à 18kB. Je la renomme en `fraunces.woff2` pour la suite.

Il est aussi possible d’utiliser [google-webfonts-helper](https://gwfh.mranftl.com/fonts) ou le [Webfont Generator de Font Squirrel](https://www.fontsquirrel.com/tools/webfont-generator) pour obtenir un fichier léger, sans nécessiter l’installation de Glyphhanger.

## Affichage par la feuille de style CSS

Désormais, il faut utiliser ce fichier dans les règles de l’art pour que tout se passe bien.

Dans ma feuille de style principale, j’ai les règles suivantes ([feuille de style complète dans GitHub](https://github.com/nfriedli/nicolasfriedli.ch/blob/main/assets/css/screen.css)):

```
:root {
    --font-main: Inter, Roboto, system-ui, Arial, sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol", "Noto Color Emoji";
}

html {
    font-family: var(--font-main);
}
```

Les nouvelles règles pour les 3 premiers niveaux de titres:

```
:root {
    --font-titling: Fraunces, var(--font-main);
}

h1,
h2,
h3 {
    font-family: var(--font-titling);
}
```

Ce qui signifie que si Fraunces n’est pas disponible ce sera la même police que celle du texte qui sera utilisée. Pas de mauvaise surprise.

Et maintenant, on appelle la police que j’ai placée dans `/fonts/`:

```
@font-face {
    font-family: Fraunces;
    font-style: normal;
    font-weight: 700;
    src: url("/fonts/fraunces.woff2");
}
```

Avec un site généré par Hugo, on placera le fichier source dans `/static/fonts/’.

Tout fonctionne bien, mais on peut faire mieux pour aller vite.

## Stratégie de chargement et de cache

Comme le site ne doit souffrir d’aucun ralentissement, je choisis un affichage optionnel. Fraunces ne s’affiche que si elle est disponible assez tôt:

```
@font-face {
    font-display: optional;
    font-family: Fraunces;
    font-style: normal;
    font-weight: 700;
    src: url("/fonts/fraunces.woff2");
}
```

Et dans le `head` de ma page, je lance le chargement dès que possible, avant même la disponibilité de la feuille de style:

```
<link 
    rel="preload" 
    href="/fonts/fraunces.woff2" 
    as="font" 
    type="font/woff2" 
    crossorigin>
```

Finalement, j’ajoute une règle de cache dans le fichier `.htaccess`:

```
<filesMatch ".(woff2)$">
Header set Cache-Control "max-age=63072000,immutable"
</filesMatch>
```

Une action similaire chez Netlify, dans `_headers`:

```
/fonts/*
    Cache-Control: max-age=63072000,immutable
```

Ces règles de cache signifient que le fichier restera en mémoire durant une année et ne sera pas rechargé.

## Cas défavorable

Il existe un cas rare qui est défavorable. Il ne se produit que si la connexion est très lente. Je n’ai réussi à tomber dans cette situation qu’en simulant un (très) mauvais réseau.

Si le chargement de Fraunces est trop lent, comme elle est `optional`, elle ne sera pas affichée. Mais l’appel `preload` a quand même demandé son chargement.

Dans ce cas, il y a eu un tranfert de fichier (de 18kB...) pour rien.

Pas tout à fait pour rien, parce que comme le fichier est en cache, il sera déjà là pour les autres pages visitées ou une prochaine visite. Le cas est donc défavorable si et seulement si l’internaute ne visite qu’une seule page et ne revient pas sur le site durant une année.

## Variations

Il est possible d’afficher une police particulière pour les titres sans choisir la police de texte s’il y a un souci de chargement. Par exemple:

```
:root {
    --font-titling: Fraunces, Georgia, sans-serif;
}

h1,
h2,
h3 {
    font-family: var(--font-titling);
}
```

Et il est possible d’afficher la police chargée, même si elle arrive lentement, avec `swap`:

```
@font-face {
    font-display: swap;
    font-family: Fraunces;
    font-style: normal;
    font-weight: 700;
    src: url("/fonts/fraunces.woff2");
}
```

## Améliorer votre site

La même politique peut s’appliquer pour toutes les polices du de votre site. Vous pouvez entreprendre une même démarche en vous inspirant des travaux de Zach Leatherman:

- [The Scoville Scale of Web Font Loading Opinions](https://beyondtellerrand.com/events/dusseldorf-2019/speakers/zach-leatherman)
- [A Comprehensive Guide to Font Loading Strategies](https://www.zachleat.com/web/comprehensive-webfonts/)

Si le travail vous semble trop complexe, je suis disponible pour des mandats de performance web afin d’optimiser votre stratégie d’affichage des polices sur votre site.