+++
title = "Minification"
date = 2023-02-03
+++

La minification des fichiers permet de réduire leur taille tout en restant «identiques». Avec Hugo, les fichiers `HTML`, `CSS`, `JSON` et `XML` sont minifiés. Hugo utilise `minify` de Taco de Wolff.

## Minification en ligne de commande

La version la plus simple pour minifier ses fichiers, c’est de l’appeler en ligne de commande. Soit à la compilation:

```bash
hugo --minify
```

soit en développement:

```bash
hugo server --minify
```

Sans configuration explicite, ce sont les options par défaut qui sont utilisées. Elles fonctionnent très bien.

## Minification par configuration

Dans le fichier général de configuration `hugo.toml`, il est possible d’activer la minification par défaut, tant en production qu’en développement.

```toml
[minify]
minifyOutput = true
```
Bien entendu, la séparation des fichiers de configuration est toujours possible, comme je l’explique sur la [page dédiée aux fichiers de configuration](/hugo/configuration/). Il en va de même pour les autres formats de fichiers de configuration (`JSON` ou `YAML`). La meilleure solution, c’est de minifier en production, mais pas en développement.

## En pratique

Sur ce site, la configuration de la minification se présente de manière suivante:

```toml
[minify]
minifyOutput = true

[minify.tdewolff.html]
keepDefaultAttrVals = false
keepQuotes = true
keepWhitespace = true
```

L’ensemble des options disponibles et des valeurs par défaut est disponible dans la section [Configure Minify](https://gohugo.io/getting-started/configuration/#configure-minify) de la documentation officielle. Les options sont discutées en détail sur la [page de référence de `minify`](https://github.com/tdewolff/minify).

La feuille de style de colorisation syntaxique est générée par:

```bash
hugo gen chromastyles --style=dracula > assets/css/chroma.css
```

Puis optimisée par [CSS Minifier](https://www.toptal.com/developers/cssminifier) avant de passer par Hugo. J’évite ainsi les répétitions inutiles et les balises vides.

## Minification efficiente

L’outil `minify` est extrêmement rapide. Mais il ne fait pas d’optimisation structurelles. En d’autres termes, il ne *réécrit* pas complètement la feuille de style, mais la *minifie* seulement. Pourtant, c’est **efficient**: raisonnablement efficace par rapport au coût quasi nul (en temps, en énergie ou en complexité).

S’il fallait être plus efficace, dans l’absolu, il serait possible d’utiliser des outils tiers. Mais ils demandent l’installation de logiciels comme `node` et font perdre à Hugo sa simplicité (et sa rapidité). C’est pourquoi j’ai préféré optimiser la feuille de style de colorisation une fois (elle ne changera pas) dans un outil en ligne.

Pour une optimisation maximale, voir par exemple:

- [A high-performance blog template for 11ty](https://www.industrialempathy.com/posts/eleventy-high-performance-blog/) de Malte Ubl
- [The Emergency Website Kit](https://mxb.dev/blog/emergency-website-kit/) de Max Böck

Une optimisation moins forte, mais plus simple, peut-être obtenue par Hugo. Elle requiert quand même `node`, mais est simple à mettre en œuvre: [How to Use PurgeCSS With Hugo](https://zwbetz.com/how-to-use-purgecss-with-hugo/) par Zachary Wade Betz.

Le gain est trop faible par rapport à la complexité supplémentaire. J’en reste donc à l’outil par défaut de Hugo qui me paraît le plus efficient.