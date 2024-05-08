---
title: Configuration d’Hugo
description: Quelques commentaires la configuration d’Hugo avec un fichier hugo.toml simple. Notes sur la modularisation et les environnements.
date: 2024-04-05
categories:
- hugo
---

La configuration d’Hugo est simple quand on part de zéro, mais souvent complexe lorsqu’un thème existant est repris. Il est bon de connaître certains concepts de base pour se débrouiller ensuite.

## Fichier minimal

Hugo a besoin d’un fichier de configuration pour fonctionner. Par défaut, il s’agit de `hugo.toml` à la racine du projet. L’ancien fichier par défaut était `config.toml` (qui fonctionne toujours).

Le plus petit fichier suffisant en [TOML](https://toml.io/en/) (Tom’s Obvious Minimal Language):

```
baseURL = "https://nicolasfriedli.ch/"
title = "Nicolas Friedli"
languageCode = "fr"
```

Il pourrait être écrit en [YAML](https://yaml.org/) (YAML Ain’t Markup Language):

```
baseURL: https://nicolasfriedli.ch/
title: Nicolas Friedli
languageCode: fr
```

Ou en [JSON](http://www.json.org/json-en.html) (JavaScript Object Notation):

```
{
    "baseURL": "https://nicolasfriedli.ch/",
    "title": "Nicolas Friedli",
    "languageCode": "fr"
}
```

## Préférence personnelle pour TOML

J’utilise TOML dans les fichiers de configuration, pour son excellent équilibre entre sa facilité de rédaction et sa fiabilité.

YAML pose parfois des problèmes comme le soulignent Ruud van Asseldonk dans [The yaml document from hell](https://ruudvanasseldonk.com/2023/01/11/the-yaml-document-from-hell) ou Chris Coyier dans [Yaml, JSON, Toml](https://chriscoyier.net/2023/01/27/yaml-json-toml/).

JSON n’est pas un format très agréable à rédiger. Mais il n’est pas prévu pour cela.

## Configuration spécifique pour mon site

L’adresse et le titre du site:

```
baseURL = "https://nicolasfriedli.ch/"
title = "Nicolas Friedli"
```

Le code de langue et la langue par défaut (que je configure même sur un site monolingue):

```
languageCode = "fr"
defaultContentLanguage = "fr"
```

Une sécurité si un nom de fichier source comprend un caractère problématique. Ou si j’utilise des taxonomies qui génèrent automatiquement des URL.

```
removePathAccents = true
```

Je désactive ce que je n’utilise pas. J’ai désactivé les taxonomies, pour éviter de créer des pages de catégories ou de tags sans l’avoir choisi. Il est ainsi possible de renseigner (déjà) des catégories et tags dans les sources, mais de ne pas les afficher (pour le moment). Le fichier robots.txt est écrit à la main, dans `/static/`. Donc:

```
disableKinds = [ "taxonomy", "term", "robotsTXT"]
```

Le répertoire final est vidé avant compilation. La compilation est toujours complète. Et j’utilise les dates de Git (par exemple pour la dernière modification dans `sitemap.xml`). Finalement, je ne génère pas de fichier `lock`.

```
cleanDestinationDir = true
disableFastRender = true
enableGitInfo = true
noBuildLock = true
```

Je configure un copyright, mon nom et mon mail qui seront repris dans le flux RSS:

```
copyright = "Creative Commons BY-SA"

[params.author]
name = "Nicolas Friedli"
email = "hello+rss@nicolasfriedli.ch"
```

Pas besoin de statistiques des balises HTML et des attributs `class` et `id` utilisés:

```
[build]
writeStats = false
```

Les `id` des titres `h2`, `h3`, etc., sont propres. C’est surtout important quand on génère une table des matières interne à la page:

```
[markup.goldmark.parser]
autoHeadingIDType = "github-ascii"
```

Les fichiers de sortie sont minifiés. Je supprime les attributs par défaut qui ne sont plus utiles en HTML5. Mais je conserve les guillemets et les sauts de lignes par souci de lisibilité. Voici la configuration:

```
[minify]
minifyOutput = true

[minify.tdewolff.html]
keepDefaultAttrVals = false
keepQuotes = true
keepWhitespace = true
```

Je décide de générer un RSS global, pour tout le site. Je l’active donc pour la racine, mais pas pour les sections:

```
[outputs]
home = ["HTML", "RSS"]
section = ["HTML"]
```

Finalement, je gère les relations entre billets par taxonomie:

```
[related]
includeNewer = true
threshold = 50
toLower = true
[[related.indices]]
name = "categories"
weight = 80
```

La [version courante](https://github.com/nfriedli/nicolasfriedli.ch/blob/main/hugo.toml), qui peut différer des exemples de cette page, est toujours disponible chez GitHub.

## Pas de thème!

Celles et ceux qui connaissent un peu Hugo remarqueront que mon fichier de configuration n’utilise pas de thème:

```
theme = "monthemehugo"
```

Je n’utilise que le répertoire `/layouts/` pour mes modèles de pages, mes shortcodes, etc. Aucun thème existant n’est utilisé pour mon site.

Si les *layouts* permettent de surcharger les fichiers d’un thème activé. Ils peuvent aussi être utilisés seuls. Ils ne surchargent rien, mais sont suffisants.

Au passage, je trouve que l’apprentissage des logiques d’Hugo est meilleur si un thème n’est pas activé dès le début. C’est un conseil que je donne aux personnes qui débutent: commencez par créer vos *layouts*, puis activez un thème si nécessaire.

## Modularisation de la configuration

Le fichier de configuration peut être séparé en plusieurs petits fichiers. Je vois peu d’intérêt à le faire avec le mien qui fait quelques dizaines de lignes. Mais ce peut être intéressant si `hugo.toml` devient trop long ou trop complexe.

Pour modulariser la configuration, il faut placer les différents fichiers dans `/config/`. Le nom de fichier est alors la section de configuration. Par exemple, la minification dans mon fichier unique est:

```
[minify]
minifyOutput = true

[minify.tdewolff.html]
keepDefaultAttrVals = false
keepQuotes = true
keepWhitespace = true
```

Déplacée dans /config/minify.toml/, elle devient:

```
minifyOutput = true

[tdewolff.html]
keepDefaultAttrVals = false
keepQuotes = true
keepWhitespace = true
```

La séparation en différents fichiers me paraît très utile dans certains cas:

- quand un site est multilingue, la [configuration des langues](https://gohugo.io/content-management/multilingual/#configure-languages) dans un fichier dédié me semble pertinente (surtout s’il y a des paramètres par langue, etc.)
- quand un site a un grand menu de navigation, un fichier dédié est une bonne idée
- et bien entendu quand certaines parties de configuration sont réutilisées telles quelles dans différents projets

Surtout, la séparation en fichier permet de proposer des portions de configurations plus simples à des personnes qui interviennent sur le site. Les responsables de la partie rédactionnelle éditeront plus facilement un fichier de menu qu’une configuration monolithique.

## Configuration par environnement

Finalement, différentes versions de configuration sont applicables selon l’environnement. Un exemple simple, pour la minification:

- dans `/config/_default/hugo.toml`: aucune option de minification mentionnée
- dans `/config/production/hugo.toml`: les quelques lignes sur la minification de mon fichier

Ainsi, durant le développement, les fichiers ne sont jamais minifiés. Alors que lors de la compilation ils le sont. Par défaut, hugo server est en environnement de développement et hugo en environnement de production.

D’autres environnements sont utilisables et les variables peuvent être passées à la compilation. Ce sont des finesses inutiles pour un site aussi léger que le mien.
