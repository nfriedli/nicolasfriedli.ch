---
title: Amnéliorer la typographie des nombres en CSS
description: Avec quelques lignes de code, il est possible d’améliorer la présentation de sa page de manière discrète mais efficace. Malheureusement, Google Fonts pourrait bien saper vos efforts.
date: 2025-02-08
categories:
- polices
---
 
Avec quelques lignes de code, il est possible d’améliorer la présentation de sa page de manière discrète mais efficace.
La propriété `font-variant-numeric` permet une gestion typographique avancée des nombres.

## Variantes de `font-variant-numeric`

Parmi toutes les propriétés (voir [font-variant-numeric](https://developer.mozilla.org/fr/docs/Web/CSS/font-variant-numeric) chez MDN), 5 sont bigrement utiles:

- 2 agissent sur leur graphie: `lining-nums`et `oldstyle-nums`
- 2 agissent sur la largeur des chiffres: `proportional-nums` et `tabular-nums`
- 1 permet de modifier le zéro: `slashed-zero`

`lining-nums` propose des chiffres alignés sur le ligne de base du texte et de hauteur uniforme.
Presque toutes les polices les utilisent par défaut.

Alors que `oldsyles-nums` propose des chiffres «à l’ancienne», aussi appelés [elzéviriens](https://fr.wikipedia.org/wiki/Chiffres_elz%C3%A9viriens).
La police Georgia a la particularité de ne proposer que de tels chiffres.

`proportional-nums` ne force pas la largeur des chiffres (donc 1 est généralement plus étroit que 0).
C’est ce qui est courant dans le texte.

Alors `tabular-nums` impose une même largeur pour les 10 chiffres (à la manière d’une police à chasse fixe).
C’est un vrai plus dans les tableaux (et dans le code).

`slashed-zero` permet d’afficher un 0 barré ou pointé qui se distingue au mieux de la lettre O.
C’est utile pour des raisons d’accessiblité, mais je ne l’utilise pas ici.

## Mise en application en CSS

On applique un comportement par défaut puis on précise les usages particuliers.

Pour toute la page, par défaut:

```
html {
    font-variant-numeric: oldstyle-nums proportional-nums;
}
```

Pour les liens (et éventuellement pour la titraille):

```
a, h1, h2, h3, h4 {
    font-variant-numeric: lining-nums proportional-nums;
}
```

Pour les tableaux et le code:

```
code, pre, table {
    font-variant-numeric: lining-nums tabular-nums;
}
```

Je ne vois pas de raison d’utiliser la combinaison `oldstyle-nums tabular-nums`.

Si la police utilisée ne dispose pas de ces variations, elle s’affichera quand même parfaitement.
C’est donc sans risque.

## Le problème de Google Fonts

Pour visualiser tous les caractères et les variations d’une police, rien ne vaut [Wakamai Fondue](https://wakamaifondue.com/).
Je préfère sa version ancienne à la version beta disponible en bas de page.

Je télécharge [Roboto](https://fonts.google.com/specimen/Roboto) chez Google Fonts.
Puis je passe le fichier `Roboto-Regular.ttf` dans la moulinette.
922 caractères et 1321 glyphes pour 143Ko.

Mais dans la pratique, on essaie d’utiliser des versions limitées (ici à l’alphabet latin) pour alléger le fichier et dans un format plus optimal (woff2).
J’effecture la transformation sur mon ordinateur:

```
glyphhanger --formats=woff2 --subset=Roboto-Regular.ttf --LATIN
```

Et j’envoie `Roboto-Regular-subset.woff2` chez Wakamai Fondue: 245 caractères, 409 glyphes pour 24Ko.

Dans la pratique, les développeurs et développeuses utilisent très souvent le génial [google-webfonts-helper](https://gwfh.mranftl.com/fonts) pour obtenir des polices déjà optimisées via Google Fonts.

Pour l’exemple présent, `roboto-v47-latin-regular.woff2` que j’envoie aussi en cuisine.
Dans la caquelon, je trouve 229 caractères, 363 glyphes pour 20Ko.

**Google Fonts supprime des options de la police de départ, dont les fameux chiffres elzéviriens.**
On peut considérer que c’est une très bonne optimisation ou que ça revient à dénaturer la typographie.

Le problème, c’est que, selon le [Web Almanac 2024](https://almanac.httparchive.org/en/2024/),  85% des sites font appel à des polices web (webfonts).
Et je parie que, quand elles ne font pas appel à Google Fonts, elles sont obtenues via google-webfonts-helper dans une grande majorité des cas.

Autant dire que vous risquez de ne jamais voir Roboto, Fira Sans et plein d’autres belles polices à leur juste valeur.

---

Si vous utilisez Android, vous devriez voir des chiffres elzéviriens en Roboto (police par défaut).

Si vous utilisez iOS, vous ne verrez logiquement pas de «old style nums» parce que San Francisco n’en propose pas.

Si vous utilisez Windows sans avoir installé Roboto et Inter, vous verrez cette page en police Segoe UI qui propose aussi la variation elzévirienne.
