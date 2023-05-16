+++
title = "Configuration d’Hugo"
description = "Quelques commentaires la configuration d’Hugo avec un fichier hugo.toml aussi simple que possible."
date = 2023-05-18
draft = true
+++

Quelques commentaires sur mon fichier de configuration d’Hugo, que je souhaite aussi simple et lisible que possible.

## Fichier minimal

Hugo a besoin d’un fichier de configuration pour fonctionner.
Par défaut, il s’agit de `hugo.toml` à la racine du projet.
L’ancien fichier par défaut était `config.toml` (qui fonctionne toujours).

Le plus petit fichier suffisanten [TOML](https://toml.io/en/) (Tom’s Obvious Minimal Language):

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

Une sécurité si un nom de fichier source comprenant un caractère problématique. Ou si j’utilises des taxonomies qui génèrent automatiquement des URLs.

```
removePathAccents = true
```

Je désactive ce que je n’utilise pas. Notamment les taxonomies pour éviter de créer des pages de catégories ou de tags sans l’avoir choisi. Il est ainsi possible de renseigner (déjà) des catégories et tags dans les sources, mais de ne pas les afficher (pour le moment). Le fichier `robots.txt` est écrit à la main, dans `/static/`. Donc:
```
disableKinds = [ "taxonomy", "term", "robotsTXT", "404" ]
```

Le répertoire final est vidé avant compilation. La compilation est toujours complète. Et j’utilise les date de Git (par exemple pour la dernière modification dans `sitemap.xml`):

```
cleanDestinationDir = true
disableFastRender = true
enableGitInfo = true
```

Pas besoin de statistiques des balises HTML et des attributs `class` et `id` utilisés:

```
[build]
writeStats = false
```

Les `id` des titres `h2`, `h3`, etc. sont propres: 

```
[markup.goldmark.parser]
autoHeadingIDType = "github-ascii"
```

Les fichiers de sorties sont minifiés. Je supprime les attributs par défaut qui ne sont plus utiles en HTML5. Mais je conserve les guillemets par souci de lisibilité. Voici la configuration:

```
[minify]
minifyOutput = true

[minify.tdewolff.html]
keepDefaultAttrVals = false
keepQuotes = true
```

Je décide de générer un RSS global, pour tout le site. Je l’active donc pour la racine, mais pas pour les sections:

```
[outputs]
home = ["HTML", "RSS"]
section = ["HTML"]
```

Enfin, dans les paramètres optionnels, je saisis le texte du pied de page. J’évite ainsi de le publier dans les *layouts*:

```
[params]
footer = """Abonnement par [flux RSS](/index.xml). 
Ce site ne vous traque pas. Généré avec [Hugo](https://gohugo.io/). 
Hébergé chez Infomaniak. Sources chez [GitHub](https://github.com/nfriedli/nicolasfriedli.ch/). 
Contenus sous licence Creative Commons BY-SA. """
```

La [version courante](https://github.com/nfriedli/nicolasfriedli.ch/blob/main/hugo.toml) est toujours disponible chez GitHub.

## Modularisation et environnements

