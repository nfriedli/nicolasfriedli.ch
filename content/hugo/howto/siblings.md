---
title: Comment lister les pages sœurs, filles et mère?
date: 2021-04-28
description: Des extraits de code pour proposer différentes navigations contextuelles sur un site créé avec Hugo.
images:
    - https://cdn.pixabay.com/photo/2020/05/23/16/16/genealogy-5210251_960_720.jpg
---

La navigation sur un site web ressemble parfois à de la généalogie.
Si un site créé avec Hugo est correctement structuré, le parcours de l'arbre est facile.

Je suppose donc que les pages (de type *single*) sont correctement placées dans des répertoires.
Et que chaque répertoire contient une page `_index.md` (de type *list*).

## La page mère

Les pages disposent d'une variable `.Parent`, ce qui rend recherche de la page mère triviale.
Si la page courante a un page mère, on affiche le lien:

```go-html-template
{{ with .Parent }}
    <a href="{{ .Permalink }}">{{ .Title }}</a>
{{ end }}
```
En version un peu plus développée, on pourrait par exemple afficher:

```go-html-template
{{ with .Parent }}
    {{ if not .IsHome }}
        <aside>Publié dans <a href="{{ .Permalink }}">{{ .Title | markdownify }}</a></aside>
    {{ end }}
{{ end }}
```

Ce lien n'est pas affiché sur les sections et les pages de premier niveau du site.

## Les pages filles

La variable `.Pages` renvoie précisément les pages et sous-sections de la page de liste courante.
C'est donc simple:

```go-html-template
{{ range .Pages }}
    <a href="{{ .Permalink }}">{{ .Title }}</a>
{{ end }}
```
Un détour par la documentation [Page Variables](https://gohugo.io/variables/page/ "Les variables de pages") (en anglais) peut être utile pour mieux comprendre ce que renvoient exactement les variables disponibles. 

Ensuite, il y a possiblité d'affiner un peu les choses, par exemple en listant séparément les sections et les pages:

```go-html-template
{{ range .Sections }}
    <h2><a href="{{ .Permalink }}">{{ .Title }}</a></h2>
    {{ .Description }}
{{ end }}

{{ range .RegularPages }}
    <a href="{{ .Permalink }}">{{ .Title }}</a>
{{ end }}
```

## Les pages sœurs

Finalement, les pages sœurs ne sont rien d'autres que des pages dont la mère est commune.
En version simple:

```go-html-template
{{ with .Parent }}
    {{ range .Pages }}
        <a href="{{ .Permalink }}">{{ .Title }}</a>
    {{ end }}
{{ end }}
```
Un exemple un peu plus développé dans lequel la page courante n'est pas affichée, mais seulement ses sœurs:

```go-html-template
{{ $current := . }}
{{ with .Parent }}
Voir aussi:
<ul>
    {{ range .Pages }}
        {{ if ne $current .}}
            <li>
                <a href="{{ .Permalink }}">{{ .Title }}</a>
            </li>
        {{ end }}
    {{ end }}
</ul>
{{ end }}
```

Cela semble assez lisible:

1. On mémorise la page courante dans une variable.
2. Si la page a une mère, on affiche *Voir aussi:* et on commence une liste.
3. On parcourt les sous-pages et on les affiches si la page listée n'est pas la page courante.

Autre possibilité, mettre en valeur la page courante par l'attribution d'une classe CSS.
Ou encore de l'afficher mais sans en faire un lien actif.

## Remarque

Il est possible de proposer des listes pages mère, sœurs ou filles uniquement en utilisant les URL finales.
Mais cela signifie alors que le site produit doit respecter scrupuleusement la structure des source.

Cette méthode n'est pas suffisamment robuste.
Je pense qu'elle est en plus assez lente (pas mal de conditions à utiliser alors que la variable `.Parent` existe déjà).