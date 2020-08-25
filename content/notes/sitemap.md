---
title: Plan de site récursif avec Hugo
date: 2020-08-25
description: Proposer l'ensemble des pages du site sous forme de plan.
images:
    - https://cdn.pixabay.com/photo/2017/08/25/06/54/street-map-2679271_960_720.jpg
---

Comme pour les [fils d'Ariane](/notes/breadcrumb/), il est très simple de faire appel à la récursivité.

## Extrait récursif

À un endroit quelconque du site:

- on regarde s'il existe des sous-pages (*single* ou *list*, qu'importe) de la page courante
- si oui, on commence une liste (`<ul>`)
- puis on parcourt les sous-pages et on les affiche chaque item (`<li>`) en lien (`<a>`)
- et à chaque page, on recommence (on regarde s'il existe des sous-pages, etc.)
- à la fin, on ferme la liste

Le bout de code qui s'appelle lui-même -- c'est le principe d'un algorithme récursif -- est donc:

```go-html-template
{{ define "souspages" }}
{{ if .Pages }}
<ul>
    {{ range .Pages}}
    <li><a href="{{ .Permalink }}">{{ .Title }}</a>
        {{ template "souspages" . }}
    </li>
    {{ end }}
</ul>
{{ end }}
{{ end }}
```

## Plan complet

Maintenant que le code récursif est prêt, il reste à «amorcer» le plan en partant des pages de la racine du site.
Chez Hugo, une section est un répertoire à la racine.
Ma préférence: commencer par lister les sections du site.

```go-html-template
<ul>
{{ range .Site.Sections }}
    <li><a href="{{ .Permalink }}">{{ .Title }}</a></li>
{{ end }}
</ul>
```

Sans oublier d'ajouter l'appel récursif préparé précédemment:

```go-html-template
<ul>
{{ range .Site.Sections }}
    <li><a href="{{ .Permalink }}">{{ .Title }}</a>
        {{ template "souspages" . }}</li>
{{ end }}
</ul>
```
Par choix, je ne liste pas les pages situées à la racine dans le plan du site.

## Mise en pratique

Un plan récursif dans un fichier du répertoire `layouts` serait donc:

```go-html-template
{{ define "souspages" }}
{{ if .Pages }}
<ul>
    {{ range .Pages}}
    <li><a href="{{ .Permalink }}">{{ .Title }}</a>
        {{ template "souspages" . }}
    </li>
    {{ end }}
</ul>
{{ end }}
{{ end }}

<ul>
{{ range .Site.Sections }}
    <li><a href="{{ .Permalink }}">{{ .Title }}</a>
        {{ template "souspages" . }}</li>
{{ end }}
</ul>
```

Comme pour les fils d'Ariane, il est possible de procéder par un appel à des fichiers partiels (*partials*) plutôt qu'en passant par la fonction `define`. 
Pour un usage unique, je préfère tout mettre dans le même fichier et ne pas m'embarasser d'un fichier partiel.