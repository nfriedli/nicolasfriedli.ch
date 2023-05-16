+++
title = "Fichier de configuration"
description = ""
date = 2023-05-18
draft = true
+++

## Fichier minimal

Hugo a besoin d’un fichier de configuration pour fonctionner.
Par défaut, il s’agit de `hugo.toml` à la racine du projet.
L’ancien fichier par défaut était `config.toml` (qui fonctionne toujours).

Le plus petit fichier suffisanten [TOML](https://toml.io/en/) (Tom's Obvious Minimal Language):

```
baseURL = "https://nicolasfriedli.ch/"
title = "Nicolas Friedli"
languageCode = "fr"
```

Il pourrait être écrit en [YAML](https://yaml.org/) (YAML Ain't Markup Language):

```
baseURL: https://nicolasfriedli.ch/
title: Nicolas Friedli
languageCode: fr
```

Ou en [JSON](https://www.json.org/) (JavaScript Object Notation):

```
{
    "baseURL": "https://nicolasfriedli.ch/",
    "title": "Nicolas Friedli",
    "languageCode": "fr"
}
```

Je préfère TOML pour son excellent équilibre entre sa facilité de rédaction et son absence de problèmes. Voir [The yaml document from hell](https://ruudvanasseldonk.com/2023/01/11/the-yaml-document-from-hell) par Ruud van Asseldonk ou [Yaml, JSON, Toml](https://chriscoyier.net/2023/01/27/yaml-json-toml/) par Chris Coyier pour les questions que pose YAML. JSON est peu agréable à rédiger.

## Ma configuration pour ce site

```
baseURL = "https://nicolasfriedli.ch/"
title = "Nicolas Friedli"
```

```
languageCode = "fr"
defaultContentLanguage = "fr"
```

```
copyright = "CC BY-SA"
```

```
removePathAccents = true
```

```
disableKinds = [ "taxonomy", "term", "robotsTXT", "404" ]
```

```
cleanDestinationDir = true
disableFastRender = true
enableGitInfo = true
```

```
[build]
writeStats = false
```

```
[markup.goldmark.extensions]
typographer = true
```

```
[markup.goldmark.parser]
autoHeadingIDType = "github-ascii"
```

```
[minify]
minifyOutput = true

[minify.tdewolff.html]
keepDefaultAttrVals = false
keepQuotes = true
```

```
[outputs]
home = ["HTML", "RSS"]
section = ["HTML"]
```

```
[params]
footer = """Abonnement par [flux RSS](/index.xml). 
Ce site ne vous traque pas. Généré avec [Hugo](https://gohugo.io/). 
Hébergé chez Infomaniak. Sources chez [GitHub](https://github.com/nfriedli/nicolasfriedli.ch/). 
Contenus sous licence Creative Commons BY-SA. """
```

La [version courante](https://github.com/nfriedli/nicolasfriedli.ch/blob/main/hugo.toml) est toujours disponible chez GitHub.