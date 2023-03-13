+++
title = "Plan complet récursif du site"
date = 2023-03-13
+++

Proposition de code pour publier un plan complet du site dans une page de son choix.
Dans le cas présent, le menu plan ne liste pas les pages à la racine; elles sont présentes en pied de chaque page.

## L’objectif

Un menu complet en HTML permet de publier:

- la liste complète des pages présentes sur le site
- en listant les sections (type *list*) puis les pages (type *single*)
- en respectant la hiérarchie
- en ne listant pas les pages (type *single*) situées à la racine (par exemple: `/sitemap/` ou `/contact/`)

## Le code

Dans un fichier `/layouts/shortcodes/sitemap.html`:

```go-html-template
{{ define "subpages" }}
{{ if .Pages }}
<ul>
    {{ range .Pages}}
    <li><a href="{{ .Permalink }}">{{ .Title }}</a>
        {{ template "subpages" . }}
    </li>
    {{ end }}
</ul>
{{ end }}
{{ end }}
 
<ul>
{{ range site.Sections }}
    <li><a href="{{ .Permalink }}">{{ .Title }}</a>
        {{ template "subpages" . }}</li>
{{ end }}
</ul>
```

Le code est appelé dans une page (par exemple `sitemap.md`) par un *partial*:

```markdown
{{</* last */>}}
```

## Notes techniques

L’utilisation de la récursivité (la fonction s’apelle elle-même), la taille et la profondeur de la hiérarchie n’ont aucune importance. Il est toutefois nécessaire que chaque répertoire dispose d’une page `_index.md`.

En procédant par *shortcode*, il n’est pas nécessaire de créer un modèle de page. Mais la page de plan du site, si elle ne se trouve pas à la racine, apparaît dans la liste.

L’ordre du menu dépend de l’ordre des pages, par chronologie, par classement (*weight*) ou par ordre alphabétique.

Une utilisation de `.LinkTitle` au lieu de `.Title` permet de choisir un titre spécifique pour le menu (qui n’est pas le titre de la page).

Toutes les pages sont affichées, il n’y a pas de condition de dérogation, sinon celle disponible par défaut par les [Build Options](https://gohugo.io/content-management/build-options/).