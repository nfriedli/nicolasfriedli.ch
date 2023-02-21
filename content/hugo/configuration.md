+++
title = "Fichiers de configuration"
date = 2023-01-29
+++

Hugo a besoin d’un fichier de configuration pour fonctionner.
Par défaut, il s’agit de `hugo.toml` à la racine du projet.
L’ancien fichier par défaut était `config.toml` (qui fonctionne toujours).

## Fichier minimal

Le plus petit fichier suffisant est (pour ce site):

```toml
baseURL = "https://nicolasfriedli.ch/"
title = "Nicolas Friedli"
languageCode = "fr"
```

Il pourrait être écrit en `YAML`:

```yaml
baseURL: https://nicolasfriedli.ch/
title: Nicolas Friedli
languageCode: fr
```
ou en `JSON`:

```json
{
    "baseURL": "https://nicolasfriedli.ch/",
    "title": "Nicolas Friedli",
    "languageCode": "fr"
}
```

Mais je préfère `TOML` pour son excellent équilibre entre sa facilité de rédaction et son absence de problèmes. Voir [The yaml document from hell](https://ruudvanasseldonk.com/2023/01/11/the-yaml-document-from-hell) par Ruud van Asseldonk ou [Yaml, JSON, Toml](https://chriscoyier.net/2023/01/27/yaml-json-toml/) par Chris Coyier pour les questions que pose `TOML`.

## Répertoire de configuration

Pour aller un peu plus loin, je conseille d’utiliser un répertoire dédié à la configuration (`config` à la racine du projet).
Il est alors possible de séparer la configuration entre développement et compilation.

Le fichier de configuration de base prend place à `config/_default/hugo.toml`. Et la configuration de production prend place à `config/production/hugo.toml`.

Lorsque le site est compilé, la configuration de production est «ajoutée» à celle par défaut.
Autrement dit, quand une option est définie 2 fois, c’est celle de production qui fait foi.

Un exemple de `config/production/hugo.toml`:

```toml
cleanDestinationDir = true

[minify]
minifyOutput = true

[minify.tdewolff.html]
keepDefaultAttrVals = false
keepQuotes = true
keepWhitespace = true
```

Le fichier parle de lui même:

- le répertoire final est nettoyé avant la compilation
- les fichier sont minifiés uniquement en production

## Configuration modulaire

Pour aller plus loin, il est possible de séparer sa configuration en de multiples fichiers.
En reprenant l’exemple précédent pour la production.

Un fichier général `config/production/hugo.toml`:

```toml
cleanDestinationDir = true
```

Un fichier spécifique pour la minification `config/production/minify.toml`:

```toml
minifyOutput = true

[tdewolff.html]
keepDefaultAttrVals = false
keepQuotes = true
keepWhitespace = true
```

## Exemple de configuration

Au jour de la rédaction de cette page, voici mon fichier de configuration générale (non modulaire):

```toml
baseURL = "https://nicolasfriedli.ch/"
title = "Nicolas Friedli"

languageCode = "fr"
defaultContentLanguage = "fr"

copyright = "CC BY-SA"

removePathAccents = true
disableKinds = [ "taxonomy", "term", "404" ]
disableFastRender = true

[author]
name = "Nicolas Friedli"
email = "hello+2023@nicolasfriedli.ch"

[build]
writeStats = false

[markup.goldmark.extensions]
typographer = true

[markup.goldmark.parser]
autoHeadingIDType = "github-ascii"

[markup.goldmark.renderer]
unsafe = true

[markup.highlight]
noClasses = false

[params]
footer = """Ce site respecte votre vie privée. Il est généré avec [Hugo](https://gohugo.io/) et hébergé chez Infomaniak. Ses sources sont disponibles chez [GitHub](https://github.com/nfriedli/nicolasfriedli.ch/). Les contenus sont sous licence libre Creative Commons BY-SA."""
```

## En pratique

Pour commencer à développer son site, je conseille le fichier minimal du début.
Je conseille aussi de désactiver par défaut ce qui ne sera pas forcément utilisé:

```toml
baseURL = "https://nicolasfriedli.ch/"
title = "Nicolas Friedli"
languageCode = "fr"

disableKinds = [ "taxonomy", "term", "robotsTXT", "404" ]
```

C’est suffisant pour commencer son site. 
Pour la minification, il suffit de la passer en ligne de commande avec: 

```bash
hugo --minify
```
