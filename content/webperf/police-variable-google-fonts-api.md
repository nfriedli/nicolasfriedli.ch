---
title: Polices variables sur son serveur via l’API de Google Fonts
description: Les polices variables fournies par Google Fonts limitent les possibilités mais sont relativement légères. En utilisant l’API, il est possible de les installer facilement sur son propre serveur.
date: 2025-12-07
---

Les polices variables sont parfois annoncées comme révolutionnaires et légères (par rapport aux possiblités offertes).
Mais les fichiers réellement transférés sont parfois assez lourds malgré les discours.
L’utilisation de Google Fonts API permet de concilier légèreté (relative) et possibilités (un peu réduites).

Pour l’exemple, je choisis de travailler avec la magnifique police [Literata](https://fonts.google.com/specimen/Literata).

La police droite Literata variable avec les paramètres de taille optique (`opsz`) et de graisse (`wght`) pèse presque 900Ko en format `ttf`.
Le poids est proche pour la version italique.

Il convient d’alléger la police en passant au format `woff2` et en la limitant (*subset*) aux caractères que j’utilise (`latin`).

On peut travailler:

- avec [glyphhanger](https://github.com/zachleat/glyphhanger) qui est simple et efficace mais demande **une installation et l’utilisation de la ligne de commande**
- avec [Google Webfonfs Helper](https://gwfh.mranftl.com/fonts/literata?subsets=latin) mais qui **ne permet pas d’obtenir des polices variables**
- avec [Webfonts Generator](https://www.fontsquirrel.com/tools/webfont-generator) de Font Squirrel **auquel je ne comprends pas grand chose**...

Je vous propose donc une **solution simple avec l’API de Google Fonts**.
Je ne prétends pas explorer l’API en profondeur (pas plus que les possibilités de glyphhanger).

## Solution optimisée avec Google Fonts API

Plutôt que de télécharger la police sur son ordinateur, on passe par «Get embed code», comme pour l’inclusion de Google Fonts dans un site.

Il est important d’éviter Google Fonts comme service tiers pour des questions de performance, de fiabilité et de respect de la vie privée.
**L’utilisation de Google Fonts API proposée ici permet d’installer les polices sur votre propre site.**

Puis tout se passe avec l’URL de la feuille de style.
Pour Literata:

```
https://fonts.googleapis.com/css2?family=Literata:ital,opsz,wght@0,7..72,200..900;1,7..72,200..900
```

Ici, on a trois variations:

- italique ou non
- taille optique entre 7 et 72 pixels
- graisses entre 200 et 900

C’est assez simple à comprendre car l’[API Google Fonts est bien documentée](https://developers.google.com/fonts/docs/css2?hl=fr).
Mais, comme toujours avec du code, une seule faute de frappe et plus rien ne fonctionne.

Quand on ouvre la feuille de style, on reçoit un truc à rallonge qui traite toutes les langues.
Pour Literata en version droite et latine, ce qui nous intéresse est:

```
@font-face {
  font-family: "Literata";
  font-style: normal;
  font-weight: 200 900;
  src: url(https://fonts.gstatic.com/s/literata/v40/or3hQ6P12-iJxAIgLYTwJrU.woff2) format("woff2");
  unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA, U+02DC, U+0304, U+0308, U+0329, U+2000-206F, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215, U+FEFF, U+FFFD;
}
```

On va désormais charger le fichier `woff2`, dont le nom a peut-être changé depuis.
Le fichier, qui pèse un peu plus de 100Ko, est donc **beaucoup plus léger** que le `ttf` initial.
Il pourra être placé, par exemple, dans:

```
/fonts/literata.woff2
```

Et dans la feuille des style locale, on pourra utiliser:

```
@font-face {
  font-family: "Literata";
  font-style: normal;
  font-weight: 200 900;
  src: url(/fonts/literata.woff2) format("woff2");
}
```

Il suffit de faire la même manœuvre pour la version italique.
Puis reste à ajouter une [gestion du cache](/webperf/htaccess/) correcte et une [politique d’affichage](/webperf/police-optimisee-titres/#strategie-de-chargement-et-de-cache) (`font-display`) adaptée.
J’en parle ailleurs dans cette rubrique.

Vous pouvez vous arrêter là.
Vous disposez désormais d’un `woff2` variable de taille raisonnable
Ou satisfaire votre curiosité en lisant la suite.

## Utilisation de glyphhanger

La manipulation est simple en ligne de commande avec `glyphhanger`.
C’est l’outil que j’utilise habituellement, parce qu’il est déjà installé sur mon ordinateur.
La manipulation:


```
glyphhanger --formats=woff2 --subset=Literata-VariableFont_opsz,wght.ttf --LATIN
```

J’obtiens un fichier `woff2` d’à peine plus de 150Ko, donc 300Ko avec l’italique.
C’est donc **significativement plus lourd** que le fichier qui sortait précédemment.
Il n’est pas moins bon que le service de Google, mais cela mérite une explication.

## Différences entre glyphhanger et Google Fonts API

Pour comparer les 2 fichiers produits, on peut passer par l’excellent [Wakamai Fondue](https://wakamaifondue.com/) (dont la version classique est meilleure que la beta en lien en bas de page):

- Le premier, téléchargé chez Google Fonts, pèse 108KB, comporte 230 caractères et 300 glyphes, avec 11 *layout features*.

- Le second, produit par glyphhanger, pèse 156KB, comporte 233 caractères et 457 glyphes, avec 24 *layout features*.

Les deux sont variables en graisse et en taille, comme souhaité.

Autrement dit, **Google Fonts diminue les possibilités de la police de départ**, par exemple en supprimant les ligatures discretionnaires (`dlig`) ou les [chiffres elzéviriens](https://fr.wikipedia.org/wiki/Chiffres_elz%C3%A9viriens) (`onum`).

Je n’ai pas d’avis tranché sur la meilleure politique, mais une alternative:

- si vous souhaitez disposer de **toutes les possibilités** d’une police aussi riche que Literata, vous devrez passer par `glyphhanger` (c’est par exemple le cas du site [Clagnut](https://clagnut.com/) de Richard Rutter)
- si vous souhaitez disposer d’une **police variable plus légère**, je vous conseille Google Fonts API

Et si la performance est très importante dans votre projet, il vaut peut-être la peine de renoncer à certaines variations.

## Le choix «performance» de Google Fonts Helper

Comme déjà dit, Google Fonts Helper **ne permet pas de télécharger des polices en format variable**.

La solution de repli, c’est de choisir 4 fichiers statiques (normal, italique, gras et gras italique) qui pèsent à peine plus de 20Ko chacun.
C’est très optimisé, moins de 100Ko pour l’ensemble, mais on perd les avantages du variable.

Si la variation continue de la graisse n’est pas indispensable, parce que vous n’utilisez que normal (400) et bold (700), c’est excellent.
Et si la variation de taille optique apporte peu, c’est parfait.

Des polices comme Literata et [Inter](https://rsms.me/inter/) apportent beaucoup par `opsz`.
Mais ce n’est pas toujours le cas.
À vous de trouver le meilleur compromis entre esthétique, écoconception et performance.

----

N’oubliez jamais que les polices système sont très bonnes (quand elles ne sont pas simplement meilleurs que des choix «baroques» vus ça et là) et ne coûtent ni temps ni bande passante.
