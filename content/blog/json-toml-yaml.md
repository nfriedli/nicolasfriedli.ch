---
title: JSON, TOML ou YAML
description: 
date: 2024-04-03
categories:
- hugo
- json
draft: true
---

Avec Hugo, il est possible d’utiliser des fichiers de configuration et des métadonnées de pages (frontmatter) dans 3 formats: JSON, TOML et YAML. Voici quelques pistes pour faire son choix, qui sont aussi valables dans d’autres cas sans utiliser ce générateur de sites statiques.

## JSON

### JSON pour une page

Un entête d’article, défini en JSON car entre `{ }`:

```
{ 
  "title" = "Enseignements du framework Diátaxis" 
  "description" = "Conçu par un spécialiste de documentation technique, le cadre de travail Diátaxis permet d’améliorer la qualité de ses pages web dans d’autres domaines que le code logiciel." 
  "date" = "2024-03-25" 
  "categories" = [
    "documentation" 
  ]
}
```

### JSON pour fichier de configuration

La configuration du site (avec des clés triées par ordre alphabétique), définie en YAML par le nom du fichier `.json`:

```
{
  "baseURL": "https://nicolasfriedli.ch/",
  "cleanDestinationDir": true,
  "copyright": "Creative Commons BY-SA",
  "defaultContentLanguage": "fr",
  "disableFastRender": true,
  "disableKinds": [
    "taxonomy",
    "term",
    "robotsTXT"
  ],
  "enableGitInfo": true,
  "languageCode": "fr",
  "noBuildLock": true,
  "removePathAccents": true,
  "title": "Nicolas Friedli",
  "build": {
    "writeStats": false
  },
  "markup": {
    "goldmark": {
      "parser": {
        "autoHeadingIDType": "github-ascii"
      }
    }
  },
  "minify": {
    "minifyOutput": true,
    "tdewolff": {
      "html": {
        "keepDefaultAttrVals": false,
        "keepQuotes": true,
        "keepWhitespace": true
      }
    }
  },
  "params": {
    "author": {
      "email": "hello+rss@nicolasfriedli.ch",
      "name": "Nicolas Friedli"
    }
  },
  "related": {
    "includeNewer": true,
    "threshold": 50,
    "toLower": true,
    "indices": [
      {
        "name": "categories",
        "weight": 80
      }
    ]
  }
}
```

Le format JSON ne permet pas de commentaires et j’estime que c’est problématique pour un fichier de configuration. Mais la clarté structurelle est évidente.

## TOML

### TOML pour une page

Un entête d’article, défini en TOML car entre `+++`:

```
+++
title = "Enseignements du framework Diátaxis"
description = "Conçu par un spécialiste de documentation technique, le cadre de travail Diátaxis permet d’améliorer la qualité de ses pages web dans d’autres domaines que le code logiciel."
date = 2024-03-25
categories = [ "documentation" ]
+++
```

### TOML pour fichier de configuration

La configuration du site, définie en TOML par le nom du fichier `.toml`:

```
baseURL = "https://nicolasfriedli.ch/"
title = "Nicolas Friedli"

languageCode = "fr"
defaultContentLanguage = "fr"

removePathAccents = true

disableKinds = [ "taxonomy", "term", "robotsTXT"]

cleanDestinationDir = true
disableFastRender = true
enableGitInfo = true
noBuildLock = true

copyright = "Creative Commons BY-SA"

[build]
writeStats = false

[markup.goldmark.parser]
autoHeadingIDType = "github-ascii"

[minify]
minifyOutput = true

[minify.tdewolff.html]
keepDefaultAttrVals = false
keepQuotes = true
keepWhitespace = true

[params.author]
name = "Nicolas Friedli"
email = "hello+rss@nicolasfriedli.ch"

[related]
includeNewer = true
threshold = 50
toLower = true
[[related.indices]]
name = "categories"
weight = 80
```

Grand avantage, le système de tables, entre `[ ]`, qui ne permet pas de revenir ensuite à des valeurs de premier niveau. Impossible, par exemple de définir la langue après le passage `[related]`. C’est très propre.

## YAML

### YAML pour une page

Un entête d’article, défini en YAML car entre `---`:

```
---
title: Enseignements du framework Diátaxis
description: Conçu par un spécialiste de documentation technique, le cadre de travail Diátaxis permet d’améliorer la qualité de ses pages web dans d’autres domaines que le code logiciel.
date: 2024-03-25
categories:
  - documentation
---
```

### YAML pour fichier de configuration

La configuration du site, définie en YAML par le nom du fichier `.yaml`:

```
baseURL: ’https://nicolasfriedli.ch/’
title: Nicolas Friedli

languageCode: fr
defaultContentLanguage: fr

removePathAccents: true

disableKinds:
  - taxonomy
  - term
  - robotsTXT

cleanDestinationDir: true
disableFastRender: true
enableGitInfo: true
noBuildLock: true
copyright: "Creative Commons BY-SA"

build:
  writeStats: false

markup:
  goldmark:
    parser:
      autoHeadingIDType: github-ascii

minify:
  minifyOutput: true
  tdewolff:
    html:
      keepDefaultAttrVals: false
      keepQuotes: true
      keepWhitespace: true

params:
  author:
    name: Nicolas Friedli
    email: hello+rss@nicolasfriedli.ch

related:
  includeNewer: true
  threshold: 50
  toLower: true
  indices:
    - name: categories
      weight: 80

```

Quand une variable est imbriqueé de plusieurs niveaux, tout en étant unique, nous avons quelque chose de peu élégant:

```
markup:
  goldmark:
    parser:
      autoHeadingIDType: github-ascii
```

Comme le système de tableau est moins évident qu’en JSON ou en TOML, ce genre de chose n’est pas limpide pour toutes et tous:

```
indices:
  - name: categories
    weight: 80
```

Sans avoir un minimum de représentation mentale, difficile de comprendre pourquoi il y a un tiret avant `name` mais pas avant `weight`.
