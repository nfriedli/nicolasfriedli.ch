+++
title = "Menu récursif contextuel"
date = 2023-03-13
+++

Pour un site de documentation, un menu  particulier a été construit. 
Il utilise la récursivité et des notions de hiérachie propres à Hugo.

## L’objectif

Pour n’importe quelle page du site, le menu propose:

- toutes les pages situées à la racine du site
- toutes les pages ancêtres de la page courante
- les pages sœurs de la page courante
- les pages filles de la page courante

Le menu est donc **contextuel**, il est différent pour (presque) chaque page.

## Le code

Dans un fichier `/layouts/partials/nav.html`:

```go-html-template
{{ define "subpages" }}
    {{ $thePage := .currentPage }}
    <ul>
        {{ range .context.Pages }}
            <li>
                <a href="{{ .RelPermalink }}">{{ .Title }} </a>
                {{ if or (.IsAncestor $thePage) (eq . $thePage) }}
                    {{ template "subpages" (dict "context" . "currentPage" $thePage ) }} 
                {{ end }}
            </li>
        {{ end }}
    </ul>
{{ end }}


{{ $thePage := .Page }}
{{ $context := .GetPage "/"}}
{{ template "subpages" (dict "context" $context "currentPage" $thePage ) }}
```

## Technique

Ce menu reprend l’idée de la récursivité du [plan complet du site](/hugo/plan-complet/).
Avec les mêmes contraintes ou limitations:

- existence d’une page `_index.md` dans chaque répertoire
- classement des pages selon la logique générale
- pas de suppression ou d’ajout de page

Toutefois, la récursion est moins triviale, puis qu’une faut tester à chaque fois où l’on se trouve dans la hiérarchie.
Pour disposer de toutes les information, il est nécessaire de *passer des variables* dans l’appel de la fonction. 
La magie opère ici:

```go-html-template
{{ template "subpages" (dict "context" . "currentPage" $thePage ) }} 
```

Ce *template* utilise le notion d’*ancêtres* (avec `.IsAncestor`) qui est apparue avec la version 0.109.0.
Il ne fonctionnera pas avec des versions antérieures d’Hugo.

----

Merci à l’excellent développeur Hugo [Régis Philibert](https://www.regisphilibert.com/fr/) qui m’avait expliqué la question du *passage de variables*.