---
title: Test de web fonts avec Geist et Geist Mono
description: Retour d’expérience sur l’intégration des polices variables Geist et Geist Mono sur un site statique, de l’implémentation aux choix d’optimisation.
date: 2026-06-21
lastMod: 2026-06-25
images:
- https://cdn.pixabay.com/photo/2018/03/26/11/36/equipment-3262336_1280.jpg
- https://cdn.pixabay.com/photo/2016/11/19/15/06/alphabets-1839737_1280.jpg
---

Pour faire quelques tests actuels sur les polices web (web fonts), j’ai décidé d’utiliser Geist et `Geist Mono` sur ce site.
Ce sont des familles de caractères modernes et disponibles en format variable.
Elles permettent de combiner élégamment sans-serif et `chasse fixe`.

**Je rappelle que dans la majorité des cas, les polices web ne sont pas nécessaires.**
L’utilisation de polices locales (system font stack) est plus performante, plus simple et pas forcément moins élégante.
J’en parle dans [Polices système en 2026](/blog/polices-systeme/).

## Geist et `Geist Mono`

Pour en savoir un peu plus sur ces polices, je vous conseille [Geist chez Vercel](https://vercel.com/font), l’entreprise les a commandées et les diffuse gratuitement.

Ou alors le faire-part de naissance par l’agence qui les a créées: [The Birth of Geist: A Typeface Crafted for the Web](https://basement.studio/post/the-birth-of-geist-a-typeface-crafted-for-the-web).

Ou encore l’analyse de l’excellent Oliver Schöndorfer: [Geist chez Pimp my Type](https://pimpmytype.com/font/geist/).

## Implémentation classique

Dans un premier temps (commit [a536d60](https://github.com/nfriedli/nicolasfriedli.ch/commit/a536d6037670c62d0027c6ff0e1c5e1d1fe6ba89)), j’ai fait ce qu’il y a de plus classique:

- utilisation des fichiers woff2 variables fournis par Vercel (plutôt légers)
- fichiers renommés (`g` et `gi` pour Geist et son italique; `gm` et `gmi` pour `Geist Mono` et son italique)
- préchargement des 4 polices dans l’entête de la page
- `font-display: swap`

**C’est très simple, ça fonctionne bien.**
On pourrait s’arrêter là, mais on peut faire mieux en 2 minutes.

## Optimisation par subset

Pour le commit [5ab173e](https://github.com/nfriedli/nicolasfriedli.ch/commit/5ab173e1a2c2e3737cf736ce7ce65b6241435659), j’ai simplement allégé les fichiers avec [Glyphhanger](https://github.com/zachleat/glyphhanger):

```
glyphhanger --formats=woff2 --subset=* --LATIN
```

Il n’y a donc plus que les caractères latins dans les fontes et **on économise en gros 50% de taille**.
Comme je publie du français (en tout cas j’essaie) et du code (j’essaie aussi), c’est très bien ainsi.

## Feuilles de style (CSS) externes

Je suis allé un peu plus loin avec le commit [14ea4f4](https://github.com/nfriedli/nicolasfriedli.ch/commit/14ea4f4ea27ef84294c340fdd206f5dd5942e870):

- les feuilles de style sont externes
- les 4 fichiers sont préchargés
- un entête CSP (Content Security Policy) plus strict est envoyé

**C’est probablement la meilleure solution pour un site organisationnel standard sur lequel les internautes reviennent régulièrement.**
Les CSS et les polices sont en cache pour 2 ans et tout va bien.

Je parle de la gestion du cache dans [htaccess pour site statique chez Infomaniak](/blog/htaccess/).

## Choix pragmatique

Il est visible dans le commit [f880215](https://github.com/nfriedli/nicolasfriedli.ch/commit/f880215aeff2ba765c3b649c83a7a5a5028d1b3f):

- les polices sont reprises de Google Fonts (mais installées localement)
- les CSS sont internes
- il n’y a pas de préchargement (`preload`)
- chargement de type `swap`

Quand la police n’est pas variable, le meilleur outil pour les télécharger est [google-webfonts-helper](https://gwfh.mranftl.com/fonts).
Mais quand la police est variable, il faut ruser.

Google Fonts fournit un [fichier CSS](https://fonts.googleapis.com/css2?family=Geist+Mono:ital,wght@0,100..900;1,100..900&family=Geist:ital,wght@0,100..900;1,100..900&display=swap) qui se charge de tous les `@font-face` utiles.
L’extrait qui m’intéresse ressemble à:

```
/* latin */
@font-face {
  font-family: "Geist";
  font-style: normal;
  font-weight: 100 900;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/geist/v5/gyByhwUxId8gMEwcGFU.woff2) format("woff2");
  unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA, U+02DC, U+0304, U+0308, U+0329, U+2000-206F, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215, U+FEFF, U+FFFD;
}
```

Je le reprends sans le `unicode-range`, je télécharge la police et je la renomme `g.woff2` dans `/fonts/`.
Ainsi je profite des optimisations de Google Fonts qui allège les polices (en leur faisant perdre quelques fonctions que je n’utilise pas).
Avec environ 100ko, j’ai mes 4 fichiers avec toutes les graisses disponibles et de vrais italiques, en sans-serif et en `mono`.

**Je conserve les CSS internes, parce que c’est la solution la plus légère.**
Mes feuilles de styles sont tellement petites que je soupçonne que cela coûte moins de temps et d’énergie de les charger à chaque fois plutôt que de vérifier le cache.
(Je suis preneur de données scientifiques sur le sujet.)
Avantage, les pages sont toujours cohérentes entre contenu (HTML) et forme (CSS), notamment quand elles sont sauvegardées dans la [Wayback Machine](https://web.archive.org/) de l’Internet Archive.

Je ne précharge rien, parce qu’il y a un grand risque de transférer entre 1 et 3 fichiers pour rien.
Seule `g.woff2`, utilisée sur toutes les pages, pourrait être préchargée.
Je décide de laisser faire le navigateur.
**Mon choix, c’est de minimiser la bande passante avant d’optimiser la vitesse pure.**

J’active `swap` pour l’affichage, qui peut me faire perdre quelques pourcents de performances chez PageSpeed Insights.
Mais je m’assure d’avoir Geist et `Geist Mono` à l’écran.

Avec `optional`, je pourrais assurer un résultat de 100%.
Mais avec un risque de ne pas voir les polices choisies dans quelques cas.

Si je voulais des performances maximales, je ne chargerais tout simplement pas de fichiers externes, même légers.



## Solution actuelle

Sur le site que vous visitez, dans l’idée de garder un site ultra performant, j’ai [testé](https://github.com/nfriedli/nicolasfriedli.ch/commit/4cdd314be116a1eac9000d1a96a7250441041eba):

- des CSS embarqués
- les fichiers de Geist et `Geist Mono` téléchargés de Google Fonts (les plus légers disponibles sans optimisation manuelle)
- le préchargement des 4 polices
- un affichage `font-display: optional`

C’est le dernier point qui change tout:

- les polices sont affichées seulement si elles sont disponibles assez rapidement
- mais ce sont des polices locales qui sont affichées dans le cas contraire (jamais de ralentissement pour les internautes)
- les fichiers `woff2` sont mis en cache durant 2 ans (c’est pourquoi je me permets de les précharger)

Au final, le seul cas défavorable, c’est:

- quand vous ne visitez qu’une page du site
- que les 4 fichiers ont été transférés
- mais que votre connexion était trop lente pour les afficher

Dans tous les autres cas (transfert rapide, plusieurs pages dans la visite ou retour sur le site dans les 2 ans), c’est la meilleure solution.

Pour plus d’explications sur `optional`, je vous conseille la lecture de [More than you ever wanted to know about font loading on the web](https://www.industrialempathy.com/posts/high-performance-web-font-loading/).

## Après les tests

En fait, je souhaite des performances 🚀 maximales 🏆.

Suite à ce billet de tests, j’en reviens à des polices locales.
Le commit [77d0ac0](https://github.com/nfriedli/nicolasfriedli.ch/commit/77d0ac0b591dc7186a326f3ec191a2f25ed15de5) documente le retour.

Si vous installez Geist et `Geist Mono` sur votre périphérique, ce sont elles qui s’afficheront en priorité, selon la logique du «font stack».
Les [versions officielles sur GitHub](https://github.com/vercel/geist-font/releases/tag/v1.7.2) sont plus à jour que celles disponibles sur Google Fonts.

Sinon, j’espère avoir bien fait les choses pour vous proposer un site lisible sans le moindre chargement de police, quelles que soient les fichiers disponibles sur votre propre périphérique.

<!--
## Foire aux questions (FAQ)

1re visite

connexion lente

visite de plusieurs pages

retour sur le site dans les 2 ans

pages avec code

pages sans code
-->