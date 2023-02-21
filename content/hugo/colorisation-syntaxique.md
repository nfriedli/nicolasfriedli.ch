+++
title = "Colorisation syntaxique"
date = 2023-02-07
lastMod = 2023-02-21
+++

Sur un site qui présente beaucoup de code, comme celui-ci, il est intéressant de coloriser les sources pour en faciliter la lecture et la compréhension. J’utilise `Chroma`, qui est inclus par défaut dans Hugo.

## Sur ce site

La charte couleur utilisée est celle de [Dracula](https://draculatheme.com/), tant pour le code que pour l’ensemble du contenu.

Hugo peut, à choix, insérer le code `CSS` dans le pages `HTML` ou utiliser une feuille de style séparée. J’ai choisi la seconde option. La feuille de style `chroma.css` est générée par:

```bash
hugo gen chromastyles --style=dracula > assets/css/dracula.css
```

Elle est ensuite appelée dans les pages par le code disponible sur la [page consacrée aux feuilles de style](/hugo/css/).

Dans la configuration, il faut veiller à désactiver le code embarqué dans le fichier `HTML` par:

```toml
[markup.highlight]
noClasses = false
```

## Colorisation sans CSS

Pour une colorisation sans feuille de style externe, tout passe par le fichier de configuration.

```toml
[markup.highlight]
# noClasses = true      # par défaut (donc pas nécessaire)
# style = "monokai"     # par défaut (donc pas nécessaire)
style = "dracula"       # le style de ce site
```

Double avantage de la colorisation sans CSS:

1. Il est possible de changer de style pour chaque extrait de code. Voir, par exemple: 
[Two different Chroma styles in one post?](https://discourse.gohugo.io/t/two-different-chroma-styles-in-one-post/41332/1)
2. Pas besoin de charger une feuille de style, ce qui se justifie s’il y a du code sur peu de pages. 

Comme je propose du code sur beaucoup de pages, il m’a paru pertinent de charger le fichier `CSS` un fois pour toutes.

## Avec ou sans colorisation

Si j’avais utilisé les balises *markdown* de code sans colorisation, j’aurais obtenu:

```
<a href="https://nicolasfriedli.ch>le site de Nicolas Friedli</a>
```

Avec la colorisation, j’obtiens:

```html
<a href="https://nicolasfriedli.ch>le site de Nicolas Friedli</a>
```

## Note sur l’accessibilité

En première approche, c’est le thème par défaut (Monokai) qui a été utilisé. Ses couleurs sont plaisantes. Toutefois, il manque de contrastes dans certains cas (par exemple les commentaires) et ne permet pas de passer les tests d’accessibilité.

C’est hélas aussi le cas avec Dracula par défaut. Il me reste à modifier la feuille de style par défaut pour corriger cela.

L’ensemble des styles disponibles se trouve en ligne sur la [Chroma Style Gallery](https://xyproto.github.io/splash/docs/all.html).
