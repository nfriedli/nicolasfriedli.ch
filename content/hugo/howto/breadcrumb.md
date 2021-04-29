---
title: Comment créer un fil d'Ariane (breadcrumb)?
date: 2021-04-28
description: Pour tout site structuré hiérarchiquement, le fil d'Ariane apporte une vraie plus-value aux utilisateurs.
images:
    - https://cdn.pixabay.com/photo/2017/07/26/16/48/bread-2542308_960_720.jpg
---

La question du fil d'Ariane (ou *breadcrumb*) est courant sur les différents forum consacrés à Hugo.
Les réponses ne sont pas toujours fonctionnelles et pas vraiment simples.

Si votre site est correctement structuré, que chaque répertoire comporte une page de liste (`_index.md`), voici la solution:

## Solution avec «partial»

Dans le répertoire `/layout/partials/`, un fichier `breadcrumb.html`:

```go-html-template
{{ with .Parent }}
    {{ partial "breadcrumb.html" . }}
    <a href="{{ .Permalink }}">{{ .Title }}</a> >
{{ end }}
```

À vous d'ajouter le séparateur qui vous convient (ici: `>`).

Le fil d'Ariane est appelé dans les pages de templates par:

```go-html-template
{{ partial "breadcrumb" . }} {{ .Title }}
```

## Solution  interne

Il est aussi possible d'intégrer le fil d'Ariane directement dans le *template*.
Ce peut être utile s'il n'est pas utilisé plusieurs fois:

```go-html-template
{{ define "breadcrumb" }}
    {{ with .Parent }}
        {{ template "breadcrumb" . }}
        <a href="{{ .Permalink }}">{{ .Title }}</a> >
    {{ end }}
{{ end }}

{{ template "breadcrumb" . }} {{.Title}}
``` 

Comme dans l'exemple précédent, il faut changer si nécessaire le séparateur (aussi: `>`).

## Améliorations

Ce sont des exemples complets fonctionnels, mais certainement insuffisants.
De manière récursive, ces fils d'Ariane remontent jusqu'à la page d'accueil du site.
On pourrai ajouter une condition à la place du titre, par exemple:

```go-html-template
{{ if .IsHome }}Accueil{{ else }}{{.Title}}{{ end }}
```
ou

```go-html-template
{{ if .IsHome }}🏠{{ else }}{{.Title}}{{ end }}
```

Pour le formater, il est serait bien d'encadrer le fil d'Ariane par un `div` avec un classe `breadcrumb`.
Ou, mieux encore, proposer une liste (`ol` voir `ul`) qui a plus de sens d'un point de vue sémantique.